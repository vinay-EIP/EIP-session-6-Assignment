# EIP-session-6-Assignment
EIP Session 6 Assignment (Session 2 of phase 2 )

# EIP Session 6 Assignment  (Phase-2 Session 2)


   1. Go through this Post: https://machinelearningmastery.com/text-generation-lstm-recurrent-neural-networks-python-keras/ (Links to an external site.)
   
   2. Add these improvements to the final code described in the post:
    
        a. Predict 500 characters only
        
        b. Remove all the punctuation from the source text
        
        c. Train the model on padded sequences (Links to an external site.) rather than random sequences of characters. 
        
        d. Train the model for 100 epochs
        
        e. Add dropout to the input layer, remove it from the layer before dense layer. Use Dropout value of 0.1 everywhere
        
        f.Submit!

## The data is downloaded from the official website using curl.

## About dataset:

Download Link : https://www.gutenberg.org/ebooks/11

Alice's Adventures in Wonderland (commonly shortened to Alice in Wonderland) is an 1865 novel written by English author Charles Lutwidge Dodgson under the pseudonym Lewis Carroll. It tells of a young girl named Alice falling through a rabbit hole into a fantasy world populated by peculiar, anthropomorphic creatures.

We have used the plain text UTF-8 format.

## The solution achieved in this repository is mainly influenced by https://machinelearningmastery.com/text-generation-lstm-recurrent-neural-networks-python-keras/ by Jason Brownlee

# Text preprocessing:
  1.  Convert entire text to lower cases (To reduce the number of unuqie characters)
  2. Remove the unwanted new lines so that its a one single string where sentences are split by fullstops
  3. All punctuations apart from comma and fullstops are removed
  4. Individual characters are converted into integers based on a mapping
  5. Prepadding is done while generating sequential information in each sentences influenced by https://machinelearningmastery.com/develop-character-based-neural-language-model-keras/
  6. The target "y" is defined as the very first letter after the input "X" sequence in the sentence
 
 
 # Example of padding:
 
 Sentence: "You are beautiful"
 
 All patterns:
 X = "Y"            y = "o"
 
 X = "Yo"           y = "u"
 
 X = "You"          y = " "
 
 X = "You "         y = "a"
 
 and so on.... 
 And each X sentence is converted into character list, mapped to integers and pre padded to 100 characters with value = 0
 
 ## Adding drop out to the visible input layer of the first LSTM

Ref: https://keras.io/layers/recurrent/

The LSTM api from keras as 2 paramets namely dropout and recurrent_dropout.
1. dropout: Float between 0 and 1. Fraction of the units to drop for the linear transformation of the inputs.
2. recurrent_dropout: Float between 0 and 1. Fraction of the units to drop for the linear transformation of the recurrent state.

To achive the desired dropout at the input layer, the first parameter is used.

# Conclutions:

1. When the punctuation like " ' " and " " " and still retained in the data, the model was able to predict direct speech sentences as well. SO work can be done on this as well

2. Character level text generation will require larger network and more epochs to learn well. So the idea of iteration through the sentence was helpful and verified




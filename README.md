# Next_word_predictor_LSTM
This is an natural language processing (NLP) project aimed at predicting the next words in an email sentence given a partial input. Leveraging LSTM (Long Short-Term Memory) neural networks with embeddings, this project assists users in composing emails more efficiently by suggesting probable continuations based on common sentence structures found in email communication. This type of model is useful for applications like autocomplete or text suggestion.

# DataSet
The dataset used for training the Email Sentence Predictor consists of a collection of common sentences found in email communication. Each sentence is preprocessed and tokenized to prepare it for training the LSTM model.

# Data Preprocessing
Tokenization: The text data, containing sentences, is split into individual lines. Each line represents a single sentence. These sentences are then tokenized

Sequence Generation: For each tokenized sentence, sequences of increasing lengths are generated. Starting from the first word, additional words are incrementally added to form longer sequences. This creates a series of input-output pairs, where the input sequence consists of a subset of words from the sentence, and the output is the next word in the sequence.

Padding: Pre-Padding is applied to ensure all sequences have the same length.

Input-Output Split: Finally, the input sequences (excluding the last word) and corresponding labels (the last word) are separated into x and y respectively. This prepares the data for training the LSTM model, where the goal is to predict the next word in a sequence given the preceding words.(Multiclass classification)


# Architecture
1. Input Layer: The input layer accepts sequences of words represented as integers. Each word is mapped to an integer index, and the input sequence is of variable length.
The input length is set to the maximum length of the sentence minus 1. This is because the last word of each sequence is used as the target prediction, so it's not part of the input sequence itself.

2. Embedding Layer: The dimensionality of the embeddings is set to 'max_word_index + 1', which indicates the total number of unique words in your dataset plus one for out-of-vocabulary (OOV) words.
Each word in the input sequence is represented by a dense vector in a continuous vector space, allowing the model to learn semantic relationships between words.

3. LSTM Layer: Model consists of 636 memory cells (nodes). Each LSTM cell maintains a hidden state and a cell state, which are updated recurrently as the model processes the input sequence.
The output dimensionality of the LSTM layer is set to 336. This means that each LSTM cell in the layer produces an output vector of length 336 at each time step.

4. Output Layer:The output layer takes the output of the LSTM layer and produces predictions for the next word in the sequence. Uses a softmax activation function to output a probability distribution over the vocabulary (all possible words).

The model is trained to minimize the categorical cross-entropy loss.




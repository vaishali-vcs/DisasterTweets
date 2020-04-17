# DisasterTweets
Real or Not? NLP with Disaster Tweets
| Experiment # | Feature Engineering | Input Embedding | Model Chosen | Hyperparameters |Leaderboard Score |
| :---:         |     :---      |          ---: | :---         |     :---:      |          ---: |
| 1   | Removed Emoji, urls and non-ASCII characters, punctuations. 16 Targets that were misclassified were corrected. | BERT Pre-trained word embeddings|BERT| Maximum character sequence considered=128|  0.8353  |
| 2     | Abbreviations such as ppl, nyc, etc were replaced. None of targets corrected.| BERT Pre-trained word embeddings  | BERT  | Maximum character sequence considered=160 |  0.8404 |
| 3   | Converted text to lowercase. Removed hashtags, usernames, links and usernames. Added features- number of hashtags, usernames, links, mentions. | BERT Pre-trained word embeddings Universal Sentence Encoder Pre-trained word embeddings | "Ensemble of following models: BERT pretrained word embeddings fed to a Dense Layer + pretrained smaller dimensional word embeddings by Universal Sentence Encoder fed to SVM + pretrained hisher dimensional word embeddings by  Universal Sentence Encoder fed to a MultiLayerPerceptron + pretrained higher dimensional word embeddings by  Universal Sentence Encoder fed to SVM | Maximum character sequence considered=512 SVM: kernel='rbf',gamma='auto', MLP: Dense and Sigmoid with two Conv1D & MaxPool layers, Number of epochs = 5, batch_size=16,Learning Rate=2e-6 | 0.8312 |
| 4     | None | GloVe, Pre-trained word vectors from Twitter | A Neural Network with Embedding Layer, BiLSTM Layer, GlobalMaxPooling1D, BatchNormalization, Drop out of 0.5, Dense Layer with relu activation, Drop out of 0.5, Dense with with relu activation, Dropout of 0.5, Dense with sigmoid activation  | 27B tokens of 200 Dimensional vectors, batch_size=32,epochs=15, default Learning rate |  0.7678  |
| 5   | Removed URLs, HTML Tags, emoji, punctuations, non aplphabet characters. Converted text to lowercase | Word2Vec from Gensim library and TfidfVectorizer | XGB Classifier with RandomizedGridSearch | 'subsample': 0.99, 'n_estimators': 200, 'min_child_weight': 16, 'max_depth': 7, 'learning_rate': 0.1, 'gamma': 0.05, 'alpha': 7 | 0.4314 |

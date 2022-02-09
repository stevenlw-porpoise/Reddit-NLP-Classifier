# Reddit-NLP-Classifier
The goal of this project is to use NLP to classify Reddit posts from 2 subreddits: [OCPoetry](https://www.reddit.com/r/OCPoetry) and [shortscarystories](https://www.reddit.com/r/shortscarystories/). This is the third project I did as part of the General Assembly [Data Science Immersive Bootcamp](https://generalassemb.ly/education/data-science-immersive-remote).

### Executive Summary
Data for the project was collected using the [Pushshift Reddit API](https://github.com/pushshift/api). After removing duplicated and short posts, a total of 56550 posts remain, evenly split between the two subreddits. The posts from r/OCPoetry date from April 2020 to January 2022 while the posts from r/shortscarystories are from June 2018 to January 2022. Additional data cleaning steps consisted of filling empty strings, removing URLs, and removing additional markdown non text codes such as "&amp;#x200B;" (a zero width space). 

I was able to use several NLP feature engineering steps that performed well on their own and in addition to bag of words features. These were 
* word count
* white space (including new line characters, tab characters, and zero width space characters)
* Part of speech tagging with the NLTK library using the [Penn Treebank Tagset](https://ericthornton.net/NLP-3/ref_nlp_penn_treebank2_pos_tags_list.php) and punctuation.
* Polarity and subjectivity sentiment scores from the textblob library.

In the modelling phase I built classifiers using different feature sets (bag of words, individual feature sets listed above with and without bag of words, and all features) and classification algorithms (logistic regression, multinomial Naive Bayes, random forests, and boosting models).
The best bag of words model was a logistic regression using 5,000 unigrams with a Tf-idf vectorization and score 92.3% accuracy.
A logistic regression model trained on white space alone did nearly as well scoring 91.0% accuracy.
The best model on all features was a Light GBM classifier with all the features and 5,000 unigrams and bigrams with Tf-idf vectorization, scoring 96.0%.
For tables with the accuracy of all trained models see the presentation slides in this repo.

### Files
* README.md - this document
* pushshift.ipynb - pulling data from reddit. Outputs data/OCPoetry.csv and data/shortscarystories.csv files.
* EDA.ipynb - cleans data, performs feature engineering, and does basic EDA. Outputs data/data_cleaned.parquet file
* model.ipynb - Builds several classifiers and evaluates their accuracy.
* presentation.pdf - Presentation slides delivered on February 4, 2022 as part of the General Assembly Data Science Immersive course.

### Folders
* data - Contains data files generated from this project. 
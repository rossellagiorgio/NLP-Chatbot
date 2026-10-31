# Mental Health FAQ — NLP Chatbot

A retrieval-based chatbot built on the [Mental Health FAQ for Chatbot](https://www.kaggle.com/datasets/narendrageek/mental-health-faq-for-chatbot) dataset from Kaggle.

## Project Overview and Approach

This project explores a dataset of 98 mental health question-answer pairs and builds a retrieval-based chatbot using modern NLP techniques. Given a user question, the chatbot finds the most semantically similar FAQ question and returns the associated answer.

## Structure

- **EDA** — exploratory data analysis (and world cloud)
- **Clustering** — unsupervised topic discovery with K-Means and Sentence-BERT embeddings
- **Chatbot** — retrieval-based chatbot with cosine similarity and similarity threshold


- `sentence-transformers` — Sentence-BERT for semantic embeddings
- `scikit-learn` — K-Means clustering, cosine similarity, normalization, PCA
- `umap-learn` — dimensionality reduction for visualization
- `matplotlib` — data visualization
- `wordcloud` — word cloud generation

## How It Works

1. All FAQ questions are encoded into 384-dimensional vectors using Sentence-BERT (`all-MiniLM-L6-v2`)
2. At query time, the user input is encoded and compared to all FAQ embeddings via cosine similarity
3. The most similar question is retrieved and its answer is returned
4. If the similarity score is below the threshold (0.55), a fallback message is shown

## Limitations

- Small dataset (98 questions) limits chatbot coverage and cluster quality
- Clusters overlap significantly due to the inherently related nature of mental health topics and the dataset size
- The similarity threshold is a trade-off (a higher value filters irrelevant questions but may reject legitimate ones)

## Possible future Improvements

- Use a larger mental health dataset
- Add a generative component to handle out-of-domain questions
- Formal evaluation with Hit Rate and MRR metrics

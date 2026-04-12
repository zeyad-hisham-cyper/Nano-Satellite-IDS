# Nano-Satellite Intrusion Detection System

This repository contains the implementation of an Intrusion Detection System (IDS) for nano-satellites, developed and evaluated using the NSL-KDD dataset.

## Overview

The project includes two primary Jupyter notebooks that explore different dataset partitioning and evaluation strategies. Both notebooks utilize a common pipeline consisting of data preprocessing, feature selection (Variance Threshold, Pearson Correlation, ANOVA F-Score, and PCA), and model training (Random Forest, SVM, XGBoost, and MLP) with hyperparameter tuning via GridSearchCV.

### 1. Train+ Evaluation (ids_Train+.ipynb)
This notebook focuses on training and validating the models exclusively on the `KDDTrain+` dataset. The data is partitioned using a standard 80/20 stratified train-test split. This approach measures the performance of the models on known attack signatures that follow the training dataset's distribution.

### 2. Train+ and Test+ Evaluation (ids_Train+_Test+.ipynb)
This notebook trains the models on the full `KDDTrain+` dataset and evaluates them against the official, separate `KDDTest+` dataset. The `KDDTest+` dataset contains novel attack types that are entirely unseen during the training phase. This provides a significantly harder, more realistic evaluation of the models' ability to generalize and detect zero-day intrusions in a real-world scenario.

## Results Summary

* **Train+ Evaluation**: Models achieved near-perfect performance (up to 99.9% accuracy with XGBoost), demonstrating that the algorithms can effectively detect known attack patterns when tested on the same distribution as the training data.
* **Train+ and Test+ Evaluation**: When exposed to the challenging, novel attacks in the `KDDTest+` dataset, performance dropped to a more realistic level (peaking at ~83.4% accuracy with SVM and PCA). This highlights the inherent difficulty of zero-day attack detection and the importance of using a distinct test dataset for real-world reliability metrics.

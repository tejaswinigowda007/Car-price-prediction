# 🚗 Car Price Category Prediction using Machine Learning

## 📌 Project Overview

This project uses Machine Learning to classify cars into **Low, Medium, and High price categories** based on different vehicle specifications.

The project follows a complete machine learning workflow including:

- Data loading and inspection
- Data cleaning
- Exploratory Data Analysis (EDA)
- Feature engineering
- Data preprocessing
- Multiple machine learning models
- Model evaluation and comparison
- Feature importance analysis
- Model saving

The main objective is to understand which vehicle characteristics are useful for predicting the price category of a car.

---

## 🎯 Objective

To build and compare multiple classification models that can predict whether a car belongs to the:

- **Low Price Category**
- **Medium Price Category**
- **High Price Category**

The price categories are created based on the car's **MSRP (Manufacturer's Suggested Retail Price)** using percentile-based thresholds.

---

## 📊 Dataset

The project uses a car dataset containing information about different vehicles.

Important features include:

- `Make`
- `Model`
- `Year`
- `Engine HP`
- `Engine Cylinders`
- `Transmission Type`
- `Driven_Wheels`
- `Number of Doors`
- `Vehicle Size`
- `Vehicle Style`
- `highway MPG`
- `city mpg`
- `Popularity`
- `MSRP`

### Target Variable

The original `MSRP` value is transformed into three categories:

| Category | Description |
|---|---|
| Low | Lower-priced vehicles |
| Medium | Mid-priced vehicles |
| High | Higher-priced vehicles |

The thresholds are determined using the **33rd and 67th percentiles** of MSRP.

---

## 🔍 Exploratory Data Analysis

The project performs several EDA steps to understand the dataset.

### Data Inspection

- First few rows
- Dataset dimensions
- Data types
- Descriptive statistics
- Missing values
- Duplicate records

### Data Cleaning

The following preprocessing steps were performed:

- Removed unnecessary whitespace from column names
- Removed duplicate rows
- Removed records with missing MSRP
- Removed records where MSRP was zero or negative

### Visualizations

The notebook includes:

- Price category distribution
- MSRP histogram
- MSRP boxplot
- Correlation heatmap
- Engine HP vs MSRP scatter plot
- Vehicle Size vs Price Category analysis

Outliers in MSRP were also investigated using the **Interquartile Range (IQR)** method.

---

## ⚙️ Feature Engineering

A new feature called `Price_Category` was created from the `MSRP` column.

The dataset was divided using:

```text
MSRP ≤ 33rd percentile → Low
33rd percentile < MSRP ≤ 67th percentile → Medium
MSRP > 67th percentile → High
```

The original `MSRP` and `Model` columns were excluded from the model input.

---

## 🧹 Data Preprocessing

The dataset contains both numerical and categorical features.

### Numerical Features

Numerical features are processed using:

- Median imputation for missing values
- StandardScaler for feature scaling

### Categorical Features

Categorical features are processed using:

- Most-frequent value imputation
- One-Hot Encoding
- `handle_unknown='ignore'`

A Scikit-learn `ColumnTransformer` and `Pipeline` were used to combine the preprocessing and machine learning steps.

---

## 🤖 Machine Learning Models

Multiple classification algorithms were trained and compared:

1. **Logistic Regression**
2. **Decision Tree**
3. **K-Nearest Neighbors (KNN)**
4. **Support Vector Machine (SVM)**
5. **Random Forest**

The dataset was split into:

- **80% Training Data**
- **20% Testing Data**

Stratified splitting was used to maintain the distribution of the target classes.

---

## 📈 Model Evaluation

The models were evaluated using multiple classification metrics:

- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC

Additional evaluation included:

- Classification reports
- Confusion matrices
- ROC curves
- Model performance comparison

A comparison table is also generated as:

```text
classification_model_comparison.csv
```

---

## 🌳 Feature Importance

Feature importance was analyzed using the **Random Forest** model.

The project extracts the importance of the processed features and identifies the most influential features for predicting car price categories.

---

## 💾 Model Saving

The trained models are saved using `joblib`.

The saved model files follow the naming format:

```text
logistic_regression.pkl
decision_tree.pkl

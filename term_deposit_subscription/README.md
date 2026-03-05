# Term Deposit Subscription Prediction using Machine Learning

## Project Overview
This project develops a machine learning–based solution to help a Portuguese bank improve the effectiveness of its marketing campaigns for term deposit subscriptions.

Historically, the bank relied on repeated phone calls to identify customers likely to subscribe, resulting in high operational costs and low conversion rates. By applying predictive analytics to historic campaign data, this project identifies behavioral, demographic, and economic factors that influence customer decisions.

Using the Bank Marketing Dataset (41,188 observations collected between 2008–2010), we built and compared multiple machine learning models to predict whether a client will subscribe to a term deposit. The resulting models allow the bank to target high-value customers more effectively, reduce unnecessary contact attempts, and optimize campaign strategies.


## Dataset
The dataset used in this project is the **Bank Marketing Dataset**, containing **41,188 records** and **20 input variables**.

Each record represents a client interaction during a marketing campaign.


### Key Feature Categories

**Demographic & Financial Attributes**
- Age
- Job
- Marital Status
- Education Level
- Credit Default Status
- Housing Loan
- Personal Loan

**Campaign Interaction Features**
- Contact Type (cellular or telephone)
- Month and Day of Contact
- Call Duration
- Number of Campaign Contacts
- Previous Campaign Contacts
- Outcome of Previous Campaign

**Macroeconomic Indicators**
- Consumer Price Index
- Consumer Confidence Index
- Euribor 3-month interest rate
- Number of Employees

### Target Variable
`y` → Indicates whether the client subscribed to the term deposit (`yes` or `no`).

### Sampling Strategy

During the initial modeling phase, multiple sampling approaches were tested to evaluate computational efficiency and model stability. When experimenting with larger subsets of the dataset (e.g., 100,000 records) or randomized samples of 10,000 observations, we observed inconsistencies in the temporal distribution of the data. Because the dataset spans multiple years (2008–2010), random sampling produced uneven representation across months and economic periods, which could introduce bias in model training.

To maintain a consistent temporal structure and ensure that macroeconomic indicators and seasonal patterns were preserved, the analysis was conducted using the **first 10,000 sequential observations** from the dataset. This approach retained the chronological integrity of the data while still providing a sufficiently large sample for reliable model training and evaluation.

## Methodology

The project follows a full end-to-end machine learning workflow:

1. **Data Cleaning**
   - Standardized schema
   - Corrected data types
   - Handled missing values using median and mode imputation

2. **Feature Engineering**
   - One-hot encoding for categorical variables
   - Consolidation of "unknown" categories
   - Preparation of machine-learning-ready dataset

3. **Class Imbalance Handling**
   - Class-weighted models to address the imbalance between subscribers and non-subscribers

4. **Exploratory Data Analysis**
   - Descriptive statistics
   - Distribution analysis
   - Correlation heatmaps
   - Behavioral and seasonal trend visualization

5. **Model Development**
   Four supervised learning models were trained:
   - Logistic Regression
   - Random Forest
   - Gradient Boosting
   - XGBoost

6. **Evaluation Metrics**
   - Accuracy
   - Precision
   - Recall
   - F1 Score
   - ROC-AUC


## Key Insights from Exploratory Data Analysis

### Customer Engagement
- Call **duration** is the strongest predictor of subscription.
- Longer calls indicate stronger customer engagement.

### Campaign Strategy
- Most clients are contacted **1–3 times**.
- Excessive contacts reduce conversion rates due to **customer fatigue**.

### Demographic Trends
- **Students and retirees** show higher subscription likelihood.
- **Higher education levels** correlate with higher conversion rates.

### Seasonal Patterns
Higher subscription rates were observed in:
- March
- September
- October
- December

Lower performance months include:
- May
- June
- July

### Communication Channel
- **Cellular contact** performs significantly better than landline communication.



## Model Performance Summary

| Model | Strength |
|------|------|
| Logistic Regression | Highest Recall |
| Random Forest | Highest Precision |
| Gradient Boosting | Best Overall Performance |
| XGBoost | Best Precision-Recall Balance |

### Logistic Regression
- Accuracy: **0.862**
- ROC-AUC: **0.94**
- Recall: **0.898**

Best for identifying the **largest number of potential subscribers**.

### Random Forest
- Precision: **0.672**
- ROC-AUC: **0.946**

Effective for **high-confidence predictions**, but lower recall.

### Gradient Boosting
- Accuracy: **0.919**
- ROC-AUC: **0.949**

Best **overall model performance**.

### XGBoost
- Highest **F1-Score: 0.632**
- Recall: **0.883**
- ROC-AUC: **0.947**

Provides the best **balanced classification performance**.

---

## Business Implications

The results suggest that machine learning can significantly improve marketing efficiency by:

- Targeting **high-probability customers**
- Reducing **unnecessary contact attempts**
- Optimizing **campaign timing and communication channels**
- Improving overall **subscription conversion rates**

A data-driven marketing strategy can reduce operational costs while increasing campaign success.

---

## Limitations

- The dataset is **highly imbalanced**, which affects classification precision.
- The data reflects economic conditions between **2008–2010**, which may differ from modern market conditions.
- Some variables (e.g., `pdays`) contain limited predictive information.

---

## Future Improvements

Future work could include:

- Testing additional algorithms such as **LightGBM** or **CatBoost**
- Applying **SMOTE** or advanced resampling techniques
- Incorporating **temporal features**
- Model calibration for improved probability estimation

---



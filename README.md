# Credit Card Fraud Detection  
**CIS 545: Big Data Analytics (Spring 2024) – Final Project**

---

## 1. Project Overview
This repository focuses on identifying fraudulent credit card transactions using machine learning models. Given the highly imbalanced nature of fraud data, the primary goal is to maximize recall (i.e., capturing the majority of fraud cases) while maintaining acceptable precision and overall accuracy.

---

## 2. Dataset
- **Rows:** ~24.3 million  
- **Columns:** 15  
- **Target Column:** `Is_Fraud` (binary: 1 = Fraud, 0 = Non-Fraud)  
- **Class Distribution:**
  - ~99.88% non-fraudulent transactions
  - ~0.12% fraudulent transactions  

- **Key Features:**
  - Transaction timestamps (split into hours/minutes)
  - Transaction amount
  - Merchant info (city, state/country, category code)
  - Transaction type (online, swipe, chip)
  - User and card identifiers

---

## 3. Exploratory Data Analysis (EDA)
- **Data Cleaning:**
  - Null handling: replaced or encoded certain columns (e.g., `Errors?` with `no_error`).
  - Generated new features (e.g., cyclical transformations for month/day/time).
- **Class Imbalance:** ~0.12% fraud leads to significant skew; standard models risk ignoring minority class.
- **Key Insights:**
  - Fraud tends to peak mid-day (10:00–14:00).
  - Higher transaction amounts often correlate with fraud.
  - Online transactions are most susceptible; swipe/chip are more common for legitimate use.

---

## 4. Modeling
**Models Explored**  
1. **Logistic Regression**  
2. **Random Forest**  
3. **XGBoost**  
4. **Neural Network**

**Data Sampling Approaches**  
1. **Full (Imbalanced) Dataset**  
2. **Under-Sampling**  
3. **SMOTE Over-Sampling**  

> We ultimately chose **under-sampling** due to better recall in testing.

---

## 5. Performance Summary (Under-Sampled Data)

- **Logistic Regression:**  
  - **Recall:** ~0.83  
  - **ROC AUC:** ~0.86  

- **Random Forest:**  
  - **Recall:** ~0.86  
  - **ROC AUC:** ~0.96  

- **XGBoost (Tuned):**  
  - **Recall:** ~0.86  
  - **ROC AUC:** ~0.96  
  - *Best overall recall with balanced performance.*

- **Neural Network:**  
  - **Recall:** ~0.84  
  - **ROC AUC:** ~0.95  

**Key Observations:**  
- XGBoost provided the best recall and high ROC AUC, making it ideal for fraud detection where missing a fraudulent case is extremely costly.  
- Precision was relatively low across all models due to severe class imbalance.

---

## 6. Conclusion
- **High Recall** is essential to catch the majority of fraudulent transactions.  
- **XGBoost** emerged as the top model, excelling in separating fraud vs. non-fraud under under-sampling.  
- **Real-Time Detection** can be facilitated using these models, but further optimization and robust data pipelines are crucial for large-scale deployment.

---

## 7. Future Work
- **Wider Data Diversity:** Incorporate more varied transaction types and newer fraud patterns to improve model generalization.  
- **Adaptive Learning:** Continuously retrain or update models to keep pace with evolving fraud tactics.  
- **Real-Time Systems:** Deploy streaming solutions to detect fraudulent transactions as they happen.  
- **Mitigate Bias:** Ensure balanced performance across different merchant categories, geographical locations, and transaction types.

---


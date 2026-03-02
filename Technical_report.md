# Technical Report
# Advanced End-to-End Customer Churn Prediction & Segmentation System

## 1. Introduction

Customer churn is a critical challenge for subscription-based businesses, directly affecting revenue, profitability, and long-term growth. Retaining existing customers is significantly more cost-effective than acquiring new ones. Therefore, identifying high-risk customers early and understanding churn drivers is essential for strategic decision-making.

This project presents a comprehensive end-to-end data science workflow that includes:

- Data preprocessing and cleaning
- Exploratory data analysis (EDA)
- Feature engineering
- Machine learning modeling
- Hyperparameter tuning
- Model evaluation
- Customer segmentation
- Business interpretation

The objective is to build an accurate churn prediction system while generating actionable business insights.

## 2. Dataset Description

The primary dataset used in this project is:
- customer_churn.csv

The dataset contains customer-level information including demographic details, service usage, billing data, contract type, and churn status.

**Key Variables**

- Tenure – Duration of customer relationship (in months)
- MonthlyCharges – Monthly subscription fee
- TotalCharges – Total amount billed
- Contract – Contract type (Month-to-month, One year, Two year)
- PaymentMethod – Payment mode
- PaperlessBilling – Billing preference
- Churn – Target variable (Yes/No)

The dataset includes both numerical and categorical variables, requiring preprocessing before model development.

## 3. Data Preprocessing

Data preprocessing was performed to ensure model reliability and consistency.

**3.1 Data Cleaning** 

- Duplicate records were removed.
- Missing values were handled using forward filling or imputation where necessary.
- Inconsistent data types were corrected.

**3.2 Outlier Detection**
Outliers in numerical features (e.g., MonthlyCharges) were detected using the Interquartile Range (IQR) method.

Formula used:
- Lower Bound = Q1 - 1.5 × IQR  
- Upper Bound = Q3 + 1.5 × IQR

Observations outside this range were removed to reduce model distortion.

## 4. Feature Engineering

Feature engineering was conducted to enhance predictive capability.

**4.1 Customer Lifetime Value (CLV)**
- CLV = MonthlyCharges × Tenure

Represents total revenue contribution of each customer.

**4.2 Average Charge Per Tenure**
- Avg_Charge_Per_Tenure = TotalCharges / (Tenure + 1)

Captures billing consistency and customer payment behavior.

**4.3 Tenure Grouping**

Customers were categorized into lifecycle groups:

- 0–1 Year
- 1–2 Years
- 2–4 Years
- 4–6 Years

This captures lifecycle-based churn behavior. 

These engineered features improved model interpretability and performance.

## 5. Preprocessing Pipeline

An industry-standard preprocessing pipeline was implemented using:
- ColumnTransformer
- StandardScaler
- OneHotEncoder

This ensured:
- Numerical features were standardized.
- Categorical variables were properly encoded.
- The pipeline remained reproducible and scalable.

Pipeline-based preprocessing prevents data leakage and supports production deployment.

## 6. Machine Learning Models

Two supervised learning models were implemented:

**6.1 Decision Tree Classifier**

- Simple interpretable model
- Baseline comparison model

**6.2 Random Forest Classifier**

- Ensemble-based model
- Higher predictive accuracy
- Better generalization

Random Forest demonstrated superior performance compared to Decision Tree.

## 7. Hyperparameter Tuning

GridSearchCV was applied to optimize:

- Number of estimators
- Maximum tree depth

Cross-validation (5-fold) ensured stable model performance across different data splits.
This reduced overfitting and improved generalization.

## 8. Model Evaluation

Models were evaluated using multiple metrics:
- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC Score

**8.1 Confusion Matrix**

A confusion matrix heatmap was generated to visualize:

- True Positives
- True Negatives
- False Positives
- False Negatives

**8.2 ROC Curve**

The ROC curve demonstrated the trade-off between sensitivity and specificity.

The Random Forest model achieved strong ROC-AUC performance, indicating effective churn classification capability.

9. Cross-Validation

Cross-validation was applied to validate model stability.

The mean cross-validation accuracy confirmed consistent predictive performance and minimized variance across folds.

10. Feature Importance Analysis

Random Forest feature importance analysis identified key churn drivers:

- Monthly Charges
- Tenure
- Contract Type
- Customer Lifetime Value

These features significantly influenced churn prediction.

Feature importance analysis enhances explainability and supports business interpretation.

11. Customer Segmentation

Unsupervised learning using K-Means clustering was applied to identify customer segments.

Three distinct clusters were identified:

- High-risk / Price-sensitive customers
- Loyal long-term customers
- Medium-risk customers

**PCA Visualization**

Principal Component Analysis (PCA) reduced dimensionality to 2 components for cluster visualization.

Segmentation supports targeted retention strategies.

## 12. Model Comparison

|Model	| Performance|
|--------|------------|
|Decision Tree |	Moderate accuracy|
|Random Forest|	Higher accuracy and stability|

Random Forest outperformed Decision Tree and was selected as the final predictive model.

## 13. Limitations

- Dataset limited to historical customer data
- No external demographic enrichment
- Model performance may vary in real-time deployment
- Advanced ensemble methods (e.g., XGBoost) not implemented

## 14. Conclusion

This project successfully implemented a complete end-to-end machine learning workflow for churn prediction and customer segmentation.

**Key achievements:**

- Robust preprocessing pipeline
- Advanced feature engineering
- Hyperparameter optimization
- Comprehensive evaluation
- Segment-based business insights

The Random Forest model demonstrated strong predictive performance, while segmentation provided strategic customer insights.

This system enables businesses to proactively reduce churn, optimize retention strategies, and enhance customer lifetime value.

## 15. Future Improvements

- Implement Gradient Boosting / XGBoost
- Deploy real-time prediction API
- Integrate with CRM systems
- Implement automated model monitoring

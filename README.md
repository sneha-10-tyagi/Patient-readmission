# Predicting Diabetic Patient Readmission

This project aims to predict early hospital readmission (within 30 days) for diabetic patients using machine learning techniques on the **"Diabetes 130-US Hospitals"** dataset. The primary goal is to identify high-risk patients and understand the key factors driving readmissions, enabling hospitals to improve patient outcomes and reduce costs.

---

## 📌 Project Phases

### 📁 Phase 1: Project Definition and Planning

- **Objective**: Predict early readmission (within 30 days) of diabetic patients.
- **Tools Used**:
  - Python (Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn)
  - Tableau (for final interactive visualizations)

---

### 🧹 Phase 2: Data Exploration and Cleaning (EDA)

- **Dataset Size**: ~100,000 patient records, 50 features
- **Key Findings**:
  - **High-Risk Age Groups**: [70–80), [80–90) had highest readmission rates.
  - **Missing Data**: Columns like `weight`, `payer_code`, and `medical_specialty` had large gaps.
  - **Low-Variance Columns**: Medication columns such as `glimepiride-pioglitazone` were mostly static.
  
---

### ⚙️ Phase 3: Data Preprocessing and Feature Engineering

- **Dropped Columns**:
  - High missing values: `weight`, `payer_code`, `medical_specialty`
  - Complex diagnostics: `diag_1`, `diag_2`, `diag_3`
  - Identifiers: `encounter_id`, `patient_nbr`
  - Low-variance medications

- **Transformations**:
  - Mapped numeric categorical IDs to readable labels
  - Created binary target variable `readmitted_target` (1 = readmitted <30 days, 0 = otherwise)
  - One-hot encoded all categorical variables
  - Converted booleans to integers

- **Result**: Final dataset with ~456 numerical feature columns

---

### 🤖 Phase 4: Model Training

- **Model Used**: Logistic Regression (for simplicity and interpretability)
- **Train-Test Split**: 80% train / 20% test (stratified on target variable)
- **Class Imbalance Handling**: Used `class_weight='balanced'` to account for 11.16% positive class
- **Output**: Trained model capable of predicting readmission probabilities

---

### 📊 Phase 5: Model Evaluation and Interpretation

- **Test Set Predictions**: Evaluated on 20,354 records
- **Performance Metrics**:
  - **AUC-ROC**: 0.6729 (good separability between classes)
  - **Recall (Readmitted)**: 0.57
  - **Precision (Readmitted)**: 0.18

- **Key Predictors Identified**:
  - `discharge_disposition_id` (e.g., transfer to another care facility)
  - `number_inpatient` (inpatient history)
  - `num_medications` (complex care requirement)

- **Output File**: Final predictions and probabilities stored in `patient_readmission_predictions.csv`

---

## 📈 Interactive Tableau Dashboard

The final dataset has been visualized using **Tableau** to make the results interpretable and actionable for healthcare stakeholders. The interactive dashboard allows for a deep dive into the factors affecting patient readmission.

**[View the Live Interactive Dashboard Here](https://public.tableau.com/views/Book1_17529997470360/Dashboard1?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)**

### Visual Components:

* **KPI Overview:** High-level metrics including **Total Patients**, overall **Readmission Rate**, and **Average Length of Stay**.
* **Demographic Analysis:** Bar charts showing the readmission rate broken down by **Age** and **Race**.
* **Key Predictors of Readmission:** A feature importance chart highlighting the most influential factors in predicting readmission, such as `discharge_disposition_id`.
* **Clinical Analysis Scatter Plot:** An interactive scatter plot visualizing the relationship between a patient's **Duration of Stay** and the **Number of Lab Procedures**, color-coded by readmission status.
* **Interactive Filtering:** The entire dashboard can be filtered by clicking on specific demographic groups, allowing for a detailed exploration of high-risk patient profiles and potential intervention points.
  
---

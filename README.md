# 🏥 PH COVID-19 Hospital Forecasting  
**AI-Driven Forecasting of ICU Occupancy in Philippine Hospitals Using Time-Series Modeling**

---

## 📘 Overview  

This repository contains the complete data science workflow for analyzing and forecasting hospital utilization during the COVID-19 pandemic in the Philippines.  
Using **Facebook Prophet**, an AI-based time-series forecasting model, the project predicts ICU occupancy trends from open **Department of Health (DOH)** datasets.  

You can view the rendered analysis **without running any code** via GitHub Pages:

🔗 **Live HTML Report:**
[https://willardcsoriano.github.io/ph-covid19-hospital-forecasting/](https://willardcsoriano.github.io/ph-covid19-hospital-forecasting/)

This page is generated from the Jupyter notebook export and contains:

* All charts and visualizations
* Forecast outputs
* Written interpretations and conclusions

> 💡 Recommended for reviewers, policymakers, or readers who only need results.

The notebook performs:  
- Data cleaning and feature engineering  
- Descriptive and regional analysis of hospital capacity  
- Predictive modeling using AI (Prophet)  
- Visualization and interpretation for policy insights  

This project demonstrates how **AI can support healthcare capacity management** and pandemic preparedness through open data and reproducible analysis.

## 📂 Repository Structure  
```
ph-covid19-hospital-forecasting/
│
├── ph-covid19-hospital-forecasting.ipynb     # Main Jupyter Notebook
├── ph-covid19-hospital-forecasting.html       # Exported HTML report (viewable in browser)
├── ph-covid19-hospital-forecasting.pdf        # Printable report version
│
├── requirements.txt                           # Python dependencies
├── .gitignore                                 # Git ignore rules
└── .venv/                                     # Local virtual environment (excluded from repo)
```
> 💡 The main notebook (`ph-covid19-hospital-forecasting.ipynb`) is your entry point.  
> It contains **seven structured sections**, from data preprocessing to AI forecasting and policy recommendations.

## 📦 Dataset Access  

To reproduce this project, download the dataset directly from the official **DOH Open Data Portal**:

> **Dataset Name:**  
> *DOH COVID Data Drop: 20221119 – 05 DOH Data Collect – Daily Report*  
>
> **Source:**  
> [Philippine Government Open Data Portal (data.gov.ph)](https://data.gov.ph/index/public/dataset/COVID-19%20DOH%20Data%20Drop%20%28November%2019,%202022%29/zkn3dj3a-8q8j-3tn8-ybwc-wycq0elukpzp)  
>
> **Publisher:** Department of Health (Philippines)  
>
> **File Format:** CSV  
>
> After downloading, rename or place the file in your project root directory:
> ```
> /ph-covid19-hospital-forecasting/
> ├── ph-covid19-hospital-forecasting.ipynb
> ├── DOH COVID Data Drop_20221119 - 05 DOH Data Collect - Daily Report.csv
> ```
> The notebook automatically loads it during the **Data Overview** step.

> ⚠️ **Note:**  
> The raw dataset is approximately **340 MB** and may take several minutes to load.  
> Due to GitHub’s file size limit (100 MB), this dataset is **not stored in this repository**.  
> Please ensure the file is available locally before running the notebook.

---

## 🧠 Project Workflow Summary  

| Section | Title | Description |
|:--------:|:------|:------------|
| **1** | Introduction | Defines objectives and healthcare context |
| **2** | Methodology | Data preprocessing and AI model setup |
| **3–4** | Data Analysis | Exploratory statistics and visualization |
| **5** | AI Forecasting | Prophet-based ICU occupancy prediction |
| **6** | Visualization & Reporting | Summary plots and interpretation |
| **7** | Documentation | Findings, recommendations, and limitations |
| **Appendix A** | AI Explanation | Describes the machine-learning component |

---

## 📊 Dataset Description  

**Key Fields:**  
- `reportdate` – Date of hospital report  
- `icu_o`, `icu_v` – ICU occupied and vacant beds  
- `nonicu_o`, `nonicu_v` – Non-ICU occupied and vacant beds  
- `mechvent_o`, `mechvent_v` – Ventilator usage  
- `region`, `province`, `city_mun` – Geographic identifiers  

**Derived Columns:**  
- `icu_occupancy_rate = icu_o / (icu_o + icu_v)`  
- `nonicu_occupancy_rate = nonicu_o / (nonicu_o + nonicu_v)`  
- `ventilator_usage_rate = mechvent_o / (mechvent_o + mechvent_v)`

---

## ⚙️ Installation and Setup  

### 1️⃣ Clone the Repository  
```bash
git clone https://github.com/<your-username>/ph-covid19-hospital-forecasting.git
cd ph-covid19-hospital-forecasting
````

### 2️⃣ Create and Activate a Virtual Environment

```bash
python -m venv .venv
# For Linux/Mac:
source .venv/bin/activate
# For Windows:
.venv\Scripts\activate
```

### 3️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 🚀 Running the Notebook

### Option 1 – Jupyter Notebook

```bash
jupyter notebook ph-covid19-hospital-forecasting.ipynb
```

### Option 2 – VS Code / JupyterLab

Open the `.ipynb` file and **Run All Cells**.

---

## 🤖 AI / Machine Learning Component

The **Prophet model** is the AI core of this project.
It uses additive regression to capture **trend**, **seasonality**, and **holiday effects** in ICU occupancy data.

```python
from prophet import Prophet

model = Prophet(
    daily_seasonality=True,
    yearly_seasonality=True,
    weekly_seasonality=True,
    seasonality_mode='additive'
)
model.fit(train)
future = model.make_future_dataframe(periods=30)
forecast = model.predict(future)
```

Outputs include predicted ICU occupancy (`yhat`) and 95 % confidence intervals (`yhat_lower`, `yhat_upper`).

---

## 📈 Key Results

* **Peak ICU Occupancy:** Mid-2021 (Delta Wave)
* **Highest Sustained Utilization:** NCR and CALABARZON
* **Model Performance:**

  * MAE = **0.0301**
  * RMSE = **0.0828**
  * MAPE = **17.07 %**
* **Forecast Insight:** Stabilizing occupancy post-Omicron with moderate uncertainty

---

## 🧩 Recommended Use Cases

* Public health forecasting dashboards
* DOH / LGU surge preparedness systems
* Academic reference for AI-based epidemiological modeling
* Policy visualization for healthcare capacity planning

---

## 🧾 Citation

If you reference this work:

> Willard Soriano, Claire Mendoza. *AI-Based Forecasting of COVID-19 Hospital Capacity in the Philippines.* 2025.
> Repository: [GitHub – ph-covid19-hospital-forecasting](https://github.com/<your-username>/ph-covid19-hospital-forecasting)

---

## ⚠️ Limitations

* Missing or inconsistent hospital records in source data
* Incomplete vaccination and severity information
* Forecast reliability decreases for long-term horizons (> 30 days)

---

## 📚 License

This project is licensed under the **MIT License** — free for use, modification, and distribution with proper credit.

---

## 🙌 Acknowledgments

* **Department of Health (Philippines)** for the open COVID-19 dataset
* **Facebook Prophet** team for the forecasting library
* **AI2 Course and Instructors** for academic guidance
* **Claire Mendoza** for collaboration and contributions to the project
* Frontline healthcare workers who inspired this research

---

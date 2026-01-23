# Mental Health Indicators During COVID-19 (Household Pulse Survey)

This repository contains a statistical analysis of U.S. Census Bureau **Household Pulse Survey** weekly estimates for **symptoms of anxiety** and **symptoms of depressive disorder** reported during the last 7 days.

Dataset (Kaggle): https://www.kaggle.com/datasets/melissamonfared/indicators-of-anxiety-or-depression

---

## Notebook

- `notebooks/mental_health_pulse_analysis.ipynb`

The notebook covers:

1. National time-series trends (United States, National Estimate)
2. Anxiety vs. Depression comparison over time
3. Statistical significance of time trends
4. Demographic comparison (Age groups)

---

## Statistical tests used

The notebook runs the following tests (with results printed in-cell):

- **Paired t-test** (weekly paired observations) comparing Anxiety vs Depression  
- **OLS linear regression** (statsmodels) of value on time index to test trend slope  
- **Spearman rank correlation** between time index and value (robust trend test)  
- **One-way ANOVA** across **age subgroups** (using all available weeks)  
- **Kruskal–Wallis** across **age subgroups** (non-parametric alternative)

---

## Key results (from the notebook output)

National series uses **72 matched weeks** (Anxiety and Depression available for the same week).

### National averages
- Mean Anxiety: **28.39%**
- Mean Depression: **22.70%**

### Anxiety vs Depression (paired over weeks)
- Mean weekly difference (Anxiety − Depression): **5.68 percentage points**
- Paired t-test p-value: **7.82e-49**
- Effect size (Cohen’s d, paired): **4.46**

### Trend significance (national)
Linear trend slopes are in **percentage points per week**.

- Anxiety slope: **-0.179** (p = **1.07e-12**); Spearman ρ = **-0.672** (p = **9.92e-11**)
- Depression slope: **-0.155** (p = **3.42e-15**); Spearman ρ = **-0.759** (p = **1.15e-14**)

Interpretation: both indicators show a statistically significant **downward** trend over the available national time window.

### Age-group comparison
Latest week available for age breakdown: **2024-08-20**  
Highest levels in the latest week:
- Anxiety: **18 - 29 years** at **30.2%**
- Depression: **18 - 29 years** at **24.1%**

Across *all weeks*, age-group differences are statistically significant:
- ANOVA p-value (Anxiety): **8.5e-159**
- ANOVA p-value (Depression): **2.95e-154**

---

## How to run

1. Put the CSV in `data/` (recommended structure):
   - `data/Indicators_of_Anxiety_or_Depression_Based_on_Reported_Frequency_of_Symptoms_During_Last_7_Days.csv`

2. Install dependencies:
```bash
pip install pandas numpy matplotlib scipy statsmodels jupyter
```

3. Open the notebook:
```bash
jupyter notebook notebooks/mental_health_pulse_analysis.ipynb
```

---

## Notes

The Household Pulse Survey estimates are weighted and intended to represent population-level trends. This repo focuses on reproducible exploratory analysis and statistical testing.

## **Predictive Maintenance Analysis using Machine Sensor Data**


Exploratory data analysis of industrial machine sensor data to identify the conditions most strongly associated with equipment failure — laying the groundwork for a predictive maintenance strategy.

## **Overview**


In manufacturing, unplanned machine downtime is one of the most costly problems a factory can face — halting production, delaying orders, and driving up repair costs. Most plants still rely on **reactive maintenance** (fixing machines after they break) or **scheduled maintenance** (servicing machines at fixed intervals, regardless of actual condition), both of which are inefficient.


**Predictive Maintenance** uses real-time sensor data — temperature, torque, rotational speed, tool wear — to catch early warning signs of failure before a breakdown occurs. This project explores sensor and operational data from industrial machines to uncover the patterns and conditions most linked to failure, using Python for the full workflow: data cleaning, feature engineering, exploratory data analysis, and visualization.


## **Objective**


To perform exploratory data analysis (EDA) on machine sensor data in order to identify which conditions and sensor readings are most strongly associated with machine failure, and to derive insights that could support a predictive maintenance approach in a manufacturing environment.


## **Dataset**


-Source: AI4I Predictive Maintenance Dataset — UCI Machine Learning Repository
-Records: 10,000 machine instances
-Features: 14 (mix of numerical and categorical)
-Key columns: Air/Process Temperature, Rotational Speed, Torque, Tool Wear, Product Quality Type (L/M/H), Machine Failure, and 5 specific failure-type flags (TWF, HDF, PWF, OSF, RNF)


## **Tools & Libraries**


-Python — core language
-Pandas / NumPy — data cleaning, manipulation, numerical computation
-Matplotlib / Seaborn — data visualization
-Jupyter Notebook — analysis environment


## **Project Workflow**


1. Data Loading & Initial Overview — import and inspect the raw dataset
2. Data Cleaning & Pre-processing — quality checks, column standardization, feature engineering
3. Exploratory Data Analysis — univariate, bivariate, and multivariate analysis
4. Visualization — 13+ charts across histograms, bar charts, pie charts, box plots, scatter plots, and a correlation heatmap
5. Key Insights & Recommendations — translating patterns into actionable conclusions


## **Feature Engineering**


Two features were engineered from raw sensor data, grounded in mechanical engineering principles:

| Feature | Formula | Purpose |
|---|---|---|
| `Temp_Diff_K` | Process Temp − Air Temp | Indicator of heat dissipation efficiency — a shrinking gap signals cooling issues |
| `Power_W` | Torque × Angular Velocity (P = τω) | True mechanical power output, combining torque and rotational speed into one measure |

Both features proved to be meaningful predictors of failure during analysis, rather than arbitrary additions.


## **Key Findings**


-Class imbalance: Only 3.39% of machines (339 of 10,000) experienced failure — consistent with real-world industrial reliability data.
-Quality grade matters: Low-quality (Type L) machines failed at nearly double the rate of High-quality (Type H) machines — 3.92% vs. 2.09%.
-Torque & Power are leading predictors: Both showed the strongest individual correlation with machine failure among all numerical features.
-Heat dissipation is the top failure mode: Heat Dissipation Failure (HDF) occurred most frequently (115 cases), and machines that failed consistently showed a smaller `Temp_Diff_K` — validating the engineered feature.
-Failure is combinatorial: A scatter plot of Torque vs. Rotational Speed revealed two distinct failure clusters — high torque at low/moderate speed, and high speed at low torque — showing failure results from specific combinations of conditions, not any single variable.


## **Recommendations**


-Prioritize monitoring and maintenance around heat dissipation systems, the leading failure cause.
-Implement torque and power threshold alerts, given their strong correlation with failure.
-Apply quality-grade-specific maintenance schedules, since Type L machines fail nearly twice as often as Type H.
-Extend this analysis into a predictive classification model (e.g., Random Forest) using the engineered features, to move from reactive to predictive maintenance.


## **Project Structure**


```
├── ai4i2020.csv                     # Original raw dataset
├── ai4i2020_cleaned.csv             # Cleaned dataset (post feature engineering)
├── Final_Project.ipynb              # Full analysis notebook
└── README.md
```

Author
Vyshakh
Data Analytics|Mechanical Engineering
---
This project was completed as a final data analytics assignment, combining a mechanical engineering background with Python-based data analysis to explore predictive maintenance in industrial manufacturing.

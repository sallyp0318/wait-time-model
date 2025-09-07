# Event Wait Time Prediction at Barclays Center

This repository showcases my work on **predictive modeling of ingress wait times** for large-scale events (NBA, WNBA, concerts, family shows) at Barclays Center, home of the Brooklyn Nets and New York Liberty.  
The project was developed during my **Data Analytics Internship at BSE Global**, where I built and evaluated machine learning pipelines to optimize event-day operations and enhance the fan experience.  

---

## 📌 Project Overview

### Problem
Managing large crowds at live events requires anticipating **queue congestion** at entry gates. Traditional staffing decisions relied heavily on historical averages and manual adjustments, often failing to capture event-specific dynamics (e.g., weather, genre, arrival patterns).

### Objective
- Predict **95th percentile wait times** per minute relative to event start.  
- Enable operations teams to adjust staffing and messaging **proactively**.  
- Reduce fan complaints and improve **Net Promoter Score (NPS)**.

---

## Methodology

### Data Sources
- **Ingress scans** from turnstiles (line length, arrival time, throughput) stored in Snowflake from S3.
- **Event metadata**: genre, performer/team, property (Nets vs Liberty vs Barclays events) stored in Dbeaver.
- **Weather API**: temperature, precipitation, severe weather flags.
- **External factors**: MTA delays, day of week, weekend flags, holidays.

### Feature Engineering
- Queue statistics: historical rolling averages (`queue_mean_3`, `queue_slope_5`).  
- Event patterns: genre congestion factors, early-arrival risk scores.  
- Cyclical encoding for time (hour_sin, day_sin, minute_sin).  
- Weather-driven modifiers (temperature bins, precipitation intensity).  
- Attendance scaling and **expected crowd intensity** multipliers.  

### Models
- **Quantile Regression** for 95th percentile prediction.  
- **Tree-based methods** (LightGBM, CatBoost) with group-based cross-validation.  
- **Baselines**: Historical averages and regression benchmarks.  

---

## Results

- Achieved **~2-3 minutes MAE** on 95th percentile wait time predictions.  
- Improved accuracy by incorporating **weather and genre-specific features**.  
- Delivered real-time **Tableau dashboards** with congestion “red zones” to guide staffing.  
- Ops teams used forecasts to reduce **peak-line complaints** and enhance fan flow.  

---

## Tech Stack

- **Languages**: Python (pandas, numpy, scikit-learn, LightGBM, CatBoost)  
- **Visualization**: Tableau, matplotlib, seaborn  
- **Data Infrastructure**: AWS S3 → Snowflake ETL pipelines  
- **Collaboration**: Jupyter, Git, Slack, stakeholder presentations  

---

## Next Steps

- **Model Refinement**: Incorporate real-time ingress feeds + live weather API for minute-level updating.  
- **Hybrid Models**: Blend quantile regression + gradient boosting for sharper tail predictions.  
- **Operational Integration**: Automate dashboard refreshes for day-of-event playbooks.  
- **Exploration**: Use simulation techniques to model “what-if” staffing and gate allocation scenarios.  

---

## Key Takeaways

- Showcased **end-to-end data science**: ETL → Feature Engineering → Modeling → Deployment.  
- Balanced **technical rigor** with **stakeholder communication** by translating complex models into **intuitive dashboards**.  
- Delivered measurable operational impact at a **world-class sports & entertainment venue**.  


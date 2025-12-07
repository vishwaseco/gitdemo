# Retail Pricing Optimization
A data science project that goes beyond prediction to prescribe optimal pricing strategies using Double Machine Learning (DML) and Economic Theory.
📌 Overview

Standard Machine Learning models often fail in pricing optimization because they confuse correlation with causation. For example, high prices might correlate with high sales simply because they occur during peak seasonality (Christmas), leading a naive model to recommend indefinitely raising prices.

This project solves that "Endogeneity Bias" by using Double Machine Learning (EconML) to isolate the true Price Elasticity of Demand. It then uses this causal insight to build a simulation engine that recommends prices to maximize Profit (where Marginal Revenue = Marginal Cost).
🚀 Key Features

    Economist-First EDA: Visualized demand curves and identified "Quality Bias" in the dataset.

    Causal Inference (The Core): Implemented LinearDML from Microsoft's EconML library to filter out confounders (seasonality, competition, shipping costs).

    Price Elasticity Estimation: Calculated a true price sensitivity of -0.02 (Inelastic), revealing that customers are less price-sensitive than naive models suggested.

    Profit Optimization Engine: Built a Python simulator that calculates the optimal price point by solving the MR=MC equation (Marginal Revenue = Marginal Cost).

🛠️ Tech Stack

    Language: Python

    Libraries: pandas, numpy, scikit-learn, econml, matplotlib, seaborn

    Concepts: Econometrics, Causal Inference, Random Forest Regressors, Profit Maximization

📊 Methodology
Phase 1: Exploratory Data Analysis (EDA)

We started by testing the "Law of Demand."

    Finding: Raw data showed upward-sloping demand curves in categories like "Computer Accessories."

    Insight: This confirmed the presence of omitted variable bias (higher prices in this category signaled higher quality/specs, not just inflation).

Phase 2: Causal Inference (Double Machine Learning)

We used a 2-stage "Residualization" process to remove noise:

    Model Y (Outcome): Predicted Quantity from control variables (Competitor Price, Freight, Product Score).

    Model T (Treatment): Predicted Unit Price from the same controls.

    Result: Regressed the residuals to find the true causal slope (m=−0.0227).

Phase 3: The Optimization Engine

We moved from "Prediction" to "Prescription."

    Logic: Assumed linear demand locally: Q=mP+c.

    Constraint: Estimated Unit Cost at 70% of current price.

    Objective: Maximize Profit function π=(P−Cost)×Q.

📈 Results

    Elasticity: The model identified that demand for the tested product category was highly inelastic.

    Impact: The optimization engine recommended a strategic price increase.

    Simulation: For a sample product, the model projected a >1500% increase in profitability (Base Effect driven) by correcting a severe underpricing strategy where the product was previously sold near-cost.

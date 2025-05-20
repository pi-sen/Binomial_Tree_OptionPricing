
Contingent Coupon Auto-Callable Note Valuation using Binomial Tree
===================================================================

📈 Overview
-----------
This project presents a robust implementation of a **Binomial Tree model** to price a **Contingent Coupon Auto-Callable Note** linked to the common stock of **Applied Materials, Inc.** The product pays conditional coupons and may be called early if certain stock price thresholds are met on predefined observation dates. The goal is to replicate the term sheet’s payout logic using backward induction on a recombining binomial lattice.

The final model estimates a note value of **$9.7446**, closely matching the term sheet’s value of **$9.76**, confirming high accuracy.

💡 Key Features
---------------
- Constructed a **CRR-based binomial tree** with 251 time steps (daily granularity)
- Integrated **auto-call and coupon barrier logic** in backward induction
- Incorporated **forward rate regime shifts** and market-implied **dividend yield**
- Used Bloomberg for real-time **discount factors, implied volatilities**, and **dividend yield**
- Conducted detailed **sensitivity analyses**:
  - Volatility impact
  - Coupon barrier variations
  - Convergence behavior across different time steps

🧮 Financial Specifications
---------------------------
- **Underlying:** Applied Materials Inc. (Ticker: AMAT)
- **Contingent Coupon Rate:** 11.35%
- **Initial Value:** $190.70
- **Coupon Barrier & Downside Threshold:** $123.96 (65% of initial value)
- **Maturity:** 01/28/2026
- **Observation Dates:** Quarterly (Apr, Jul, Oct, Jan)
- **Note Value Estimated:** $9.7446 (vs Term Sheet: $9.76)

🧠 Methodology
--------------
1. **Stock Tree Generation**:
   - Used Cox-Ross-Rubinstein (CRR) method to calculate up/down factors.
   - Used daily steps to create a recombining lattice.

2. **Valuation Tree**:
   - Backward induction incorporating:
     - Auto-call condition
     - Coupon eligibility check
     - Downside payoff logic
   - Used forward rates per regime to compute discounting and risk-neutral probabilities.

3. **Data Inputs**:
   - SOFR rates interpolated from Bloomberg swap discount factors
   - AMAT dividend yield = 2.071%
   - Implied volatility (σ) = 37.797% (approximated for numerical tractability)

📊 Sensitivity Analysis
------------------------
- Volatility has **nonlinear** effects on pricing due to discrete barrier interaction
- Coupon barrier above initial value shows **valuation ceiling** due to auto-call dominance
- Convergence analysis reveals **oscillatory error patterns**—accuracy depends on step alignment with observation dates


📌 Authors
----------
- Piyush Sen
- Srikari Rallabandi
- Aastha Shah

📄 License
----------
MIT License (or your preferred open-source license)

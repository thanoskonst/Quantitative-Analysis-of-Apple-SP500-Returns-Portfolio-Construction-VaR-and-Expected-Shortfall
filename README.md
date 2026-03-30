# Quantitative-Analysis-of-Apple-SP500-Returns-Portfolio-Construction-VaR-and-Expected-Shortfall
Quantitative analysis of Apple and S&amp;P 500 using R. Includes log returns, volatility clustering, CAPM regression (beta estimation), inverse-volatility portfolio construction, and risk metrics such as Value at Risk (VaR) and Expected Shortfall (ES).


1) Price Dynamics & Log Returns  
Plotted Apple prices over 250 days -> clear volatility clustering and fat tails, which are typical characteristics of financial time series.  
Log returns are used as they stabilize variance, allow additive compounding over time, and approximate normality better than raw price differences.  

Focusing on the last 150 days:  
mean = 0.00395, SD = 0.02437, t-test p = 0.049 -> Significant at 2% level.  
This suggests that even in more recent and relatively stable periods, returns may still exhibit non-zero behavior, although economically small.  

---

2) Market Sensitivity (Regression)  
Regression: Y ~ X (Apple vs S&P500)  

β = 1.126 -> Apple is a high-beta stock, moving approximately 1.13x the market, indicating amplified reactions to market movements.  

Example:  
SP500: -5% (crisis) -> AAPL: -5.63% (-5% × 1.126)  

R² = 0.715 -> 71.5% of Apple’s variance is explained by market movements, showing strong dependence on systematic risk factors.  

The regression is not used for prediction, but to estimate market exposure (systematic risk) and understand how sensitive Apple is to overall market conditions.  

---

3) Portfolio Construction (Inverse Volatility)  
Weights are assigned as the inverse of each asset’s standard deviation, giving lower weight to more volatile assets and higher weight to more stable ones.  
This approach aims to reduce overall portfolio risk without relying on return forecasts.  

Portfolio mean: 0.00131, SD: 0.02401 -> lower volatility compared to a simple equal-weight (50/50) portfolio, indicating improved risk efficiency.  

The histogram of portfolio returns shows fat tails and is roughly centered around the mean, suggesting the presence of extreme events despite diversification.  

Although the distribution of portfolio returns deviates from normality (Shapiro-Wilk and KS tests), the sample size allows inference on the mean via the Central Limit Theorem.  

Portfolio returns are centered around zero (t-test with p-value = 0.3884), indicating no statistically significant average return.  

---

4) Value at Risk (VaR)  
Historical VaR (98%): 5.481% (more robust due to non-normality)  
Parametric VaR (98%): 4.799%  

There is a 2% probability of daily losses exceeding approximately 5.58%.  
This provides a clear threshold for downside risk under normal market conditions.  

KS test p = 0.0002 -> returns are not normally distributed, confirming the presence of fat tails.  
However, the parametric VaR remains relatively close to the historical estimate, suggesting reasonable approximation in this case.  

---

5) Expected Shortfall (ES / Conditional VaR)  
ES (98%): 6.118%  

In the worst 2% of cases, average losses exceed 6.1%, highlighting the severity of extreme downside risk beyond the VaR threshold.  

ES > VaR, capturing fat-tail risk more effectively and providing a more conservative and informative risk measure.  
This makes ES an essential metric in modern risk management frameworks.  

---

6) Key Insights  
Sub-period analysis (last 150 days) confirms a more stable behavior, with reduced volatility compared to earlier periods.  

Apple shows high market sensitivity (high beta), implying that portfolio risk is strongly influenced by overall market movements and requires careful risk management.  

The inverse volatility portfolio successfully reduces total risk without sacrificing return potential, demonstrating the benefits of simple risk-based allocation strategies.  

Historical and parametric VaR estimates are relatively close, but Expected Shortfall reveals deeper tail risk, emphasizing the importance of going beyond VaR when assessing extreme scenarios.  

Overall, diversification reduces volatility, but significant tail risk remains, reinforcing the need for robust risk measures.

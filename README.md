# Tennis Match Outcome Prediction: Aces and Double Fault Analysis

## Project Overview

This project aims to classify whether an ATP tennis player wins a match based on their serving performance, specifically the points won from first and second serves, as well as the occurrence of aces and double faults. Tennis is a sport rich in statistical data, making it a fascinating subject for predictive modeling. Through this analysis, we explore the extent to which certain serve statistics correlate with match outcomes and evaluate the predictive power of these metrics.

## Objectives

The main objectives of this project are:
1. **Classify Tennis Match Outcomes:** Develop a machine learning model to predict match winners based on serve statistics, focusing on first and second serve points won.
2. **Data Analysis and Visualization:** Analyze serve data, visualize correlations, and explore model performance at various parameter settings.
3. **Model Optimization:** Tune model parameters to improve prediction accuracy and determine the best-performing model configuration.

## Data Description

- **Source:** Data was obtained from the top 500 ATP players from 2017 to 2019.
- **Format:** The dataset is available as a CSV file.
- **Content:** Match statistics, including aces, double faults, points won on first and second serves, player rankings, tournament dates, and match difficulty levels.

## Dependencies

The project requires the following R libraries:
- **tidyverse** for data manipulation and visualization.
- **tidymodels** for model building and tuning.
- **ggplot2** for creating plots and visualizations.
- **repr** for adjusting plot sizes in Jupyter Notebook.

To install these libraries, run:
```R
install.packages(c("tidyverse", "tidymodels", "ggplot2", "repr"))
```

## Data Preparation

The dataset originally represents matches, with separate columns for the winner and loser. To make it suitable for individual player analysis:
1. **Select Columns of Interest:** We created two datasets, one for winners and one for losers, focusing on first and second serve points won.
2. **Win Status Indicator:** A column was added to each dataset indicating the win status ("win" or "lose").
3. **Data Merging and Cleaning:** The winner and loser datasets were merged, and missing values were removed.

## Methodology

1. **Data Splitting:** The data was split into training (75%) and testing (25%) sets, stratified by win status to maintain class balance.
2. **Visualization:** We created scatter plots to visualize the relationship between first and second serve points won and match outcomes.
3. **Model Selection:** A k-Nearest Neighbors (k-NN) classifier was chosen for its simplicity and interpretability in binary classification.
4. **Cross-Validation:** A 5-fold cross-validation with tuning for different k-values (neighbors) was used to find the optimal number of neighbors.
5. **Evaluation:** Model accuracy was evaluated to determine the k-value that provided the best predictive accuracy.

## Results

The k-NN model achieved the highest accuracy of approximately 54.5% at k = 41, which indicates only a marginal improvement over random guessing (50% accuracy). This suggests that serve statistics alone may not be sufficient predictors of match outcomes, potentially due to the lack of other influential metrics (e.g., break points won or points won on the opponent’s serve).

## Visualization

Two primary visualizations were created:
1. **Scatter Plot:** Showing the relationship between first and second serves won by win status.
2. **Accuracy vs. k Plot:** Demonstrating model accuracy across different values of k in the k-NN classifier, with accuracy peaking at k = 41.

## Discussion

The low predictive accuracy implies that:
- Serve points alone may not be highly indicative of match outcomes.
- Further model improvements could involve using additional predictors (e.g., aces, double faults, break points).
- Higher k-values, not tested here due to computational constraints, may yield marginal improvements.
- Exploring alternative models (e.g., decision trees, support vector machines) may offer better accuracy.

### Future Directions

Potential areas for improvement include:
1. **Using Serve Percentages:** Converting absolute serve points won to percentages to account for match length variability.
2. **Incorporating Additional Features:** Adding metrics like aces, double faults, and break points could enhance predictive power.
3. **Testing Alternative Models:** Trying more complex models may uncover nonlinear relationships missed by k-NN.
4. **Increasing k-Values:** Testing k-values in the 100s might provide better insights into model performance.

## Files

- **main_analysis.Rmd**: Contains the full R code for data wrangling, visualization, model building, and evaluation.
- **README.md**: Overview of the project and instructions.
- **data/**: Folder with the dataset file (`tennis_data.csv`).

## References

- Barnett, T., & Clarke, S. R. (2005). Combining player statistics to predict outcomes of tennis matches. IMA Journal of Management Mathematics. [Link](https://academic.oup.com/imaman/article-abstract/16/2/113/704903?redirectedFrom=fulltext)
- Gu, W., & Saaty, T. L. (n.d.). Predicting the outcome of a tennis tournament: Based on both data and judgments. ResearchGate. [Link](https://www.researchgate.net/publication/330883807_Predicting_the_Outcome_of_a_Tennis_Tournament_Based_on_Both_Data_and_Judgments)
- Sackmann, J. (n.d.). tennis_atp_matches (2017-2019). GitHub Repository.

## License

This project is for educational and research purposes. Data sources and third-party content are credited to their respective owners.

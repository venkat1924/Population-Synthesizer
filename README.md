## Objective:
The objective of this project is to read data from a CSV file, perform grouping and sampling operations based on specified attributes, and create a new DataFrame with the sampled data.

## Pseudocode:

1. Read data from `Data.csv` into DataFrame `df0`.
2. Group `df0` by the attributes ["Sex", "Age_category", "Highest_education_level"] to obtain the frequency of each combination, storing the result in a dictionary `freq_of_all_combos`.
3. Initialise an empty DataFrame `df` with 50,000 rows and columns ["Sex", "Age_category", "Highest_education_level"].
4. For each unique combination `combo` in `freq_of_all_combos`:
   - Calculate the proportion of `combo` in the seed sample as `proportion = (frequency of the combination / total sample size)`.
   - Determine the number of agents `n` in `df` corresponding to `combo` using the formula `n = proportion * 50000`.
   - Identify the indices in `df` where the "Sex" column is NaN and store them in `sample_indices`.
   - If the number of `sample_indices` is greater than or equal to `n`:
     - Randomly select `n` indices from `sample_indices` without replacement.
     - Assign the values of `combo` to the selected indices in `df`.
5. Return the `df` DataFrame.

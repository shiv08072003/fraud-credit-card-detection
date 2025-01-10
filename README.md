Credit Card Fraud Detection
This project is a credit card fraud detection system that utilizes a dataset of credit card transactions to classify transactions as either legitimate or fraudulent using logistic regression.
Logistic regression is a binary classification algorithm that predicts the probability of an event belonging to one of two classes. Instead of fitting a straight line (as in linear regression), it fits a sigmoid function, which maps any real-valued input to a value between 0 and 1.
In this project:
Input Features (x): The dataset has 30 features (Time, V1-V28, Amount) used to predict the class of the transaction.
Target Variable (y): The Class column represents whether a transaction is legitimate (0) or fraudulent (1).

Steps Explained
Import Libraries
pandas: For data manipulation and analysis.
numpy: For numerical operations.
sklearn: For splitting the dataset, building the logistic regression model, and evaluating accuracy.
Load Dataset
The dataset is read using pd.read_csv from a CSV file containing 284,807 transactions and 31 features:
Features: Time, V1 to V28, Amount.
Target: Class (0: Legitimate, 1: Fraudulent).
Explore Dataset
df.head(): Displays the first few rows.
df.shape: Shows the dataset dimensions (284,807 rows and 31 columns).
df.info(): Provides data types and counts of non-null values for each column.
df.isnull().sum(): Checks for missing values (none in this dataset).
df["Class"].value_counts(): Shows the distribution of legitimate (0) and fraudulent (1) transactions. The dataset is highly imbalanced with only 492 fraudulent cases out of 284,807 total transactions.
Separate Legitimate and Fraudulent Transactions
legit: Contains only legitimate transactions.
fraud: Contains only fraudulent transactions.
Analyze Transaction Amounts
Statistical summaries of the Amount feature for legitimate and fraudulent transactions are compared.
Downsample Legitimate Transactions
To handle the class imbalance, a random sample of 492 legitimate transactions is taken using legit.sample(n=492). This creates a balanced dataset when combined with the 492 fraudulent transactions.
Combine Balanced Dataset
Concatenates the legitimate sample with fraudulent transactions to create a new balanced dataset (new_df).
Split Dataset
The features (x) and target (y) are separated:
x: All columns except Class.
y: The Class column.
The dataset is split into training (80%) and testing (20%) sets using train_test_split, with stratification to preserve the class distribution.
Model Training
A logistic regression model (LogisticRegression) is instantiated and trained using the x_train and y_train datasets.
Model Evaluation
Predictions are made on both training and testing datasets.
Accuracy is computed using accuracy_score:
Training accuracy: 94.16%
Testing accuracy: 95.43%

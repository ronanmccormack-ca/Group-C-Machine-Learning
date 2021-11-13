# Group-C-Machine-Learning
Group C machine learning project for Machine Learning module - IT Sligo

Comparison of Classification Algorithms
Anonymous Submission
Institute of Technology Sligo

Abstract
The performance and effectiveness of two classification algorithms are tested across several datasets for comparison. Sufficient variations of data are covered, and a few classifier methods are considered and investigated for use within this data to ensure the best operating classifier methods will be identified for use in the project. Categorizing data for it to be used at its highest level of effectiveness and efficiency is called data classification and it is used to perform complex and varied actions (Raluca-Marian, 2012). Clean data is essential to optimise the accuracy of classifier models.

Keywords: Classification, Data, Machine Learning,

1 Introduction 
Many classifier models exist to perform data classification, examples of these include Logistic regression, K-Nearest Neighbours, Decision Tree, Support Vector Machines (SVM) and Random Forest. The amount of data being produced is constantly increasing and the size of these datasets make it extremely hard for manual data analysis, which is where the classifier models are used, it is necessary to find patterns concealed in large datasets using automated pattern recognition performed by these algorithms (Amancio DR, 2014). There has been tremendous progress in data mining and machine learning with BIG DATA driving the need for effective use of data and classification algorithms to find hidden patterns in data to increase its value (Osisanwo F.Y., 2017) and uses.

2 Methodology
The data presented was compiled from two separate vehicles, a Peugeot 207 and an Opel Corsa. Each car took two journeys respectively and the results were recorded using 17 different variables.

The total number of rows for each journey are as follows:
Peugeot Journey 1	8199
Peugeot Journey 2	4446
Corsa Journey 1	7038
Corsa Journey 2	7038

Two classifier methods were trained on a selected dataset and a full comparison and analysis of the results was carried out. A few steps needed to be carried out before the data was used in the chosen classifier models. These steps ensured the quality of the data being used.

Data cleaning: The sample data needs to be cleaned to ensure it is free of inconsistent data and errors. There are several steps which need to be carried out to clean the data, these include Data Scaling, variables measured at different scales will not contribute equally to model fitting and may create a bias.

2.1 Data Pre-processing
As mentioned, the data needs to be cleaned to produce the best results from the classifier models. This can be done in several ways, data labelling and data scaling being the main topics of this paper.

The data for each car was merged as the two datasets for each car contained the same number of columns and information for each column and the subsequent datasets were depending on their car model.

The datasets were queried to find missing data and mismatching column types. The datapoints that returned a NaN were removed from the dataset. No mismatching column types were found within the data.

The expected y value columns were queried to ensure the unique values within the data matched the expected outcome. Within the Peugeot data, the road surface conditions classes were mistakenly identified and the mislabelled ‘FullOfHolesCondition’ data was changed to ‘UnevenCondition’. The datapoints resulting in the output ‘FullOfHolesCondition’ represented almost 25% (3247 entries) of the data in this dataset and therefore must remain to ensure accurate outcomes.

2.1.1 Data Labelling 
Data labelling is used when the outputted y value contains text value or categorical values. The aim of label encoding is to transform the non-numerical output y into a numerical output. This can be done using Sklearn’s Label Encoding function. While Decision-Tree classifiers can handle non-numerical values very well, to get the best results, many algorithms prefer to use numerical values.

For our different y outputs, the following non-numerical data was converted to the below:

Non-Numerical	Numerical
UnevenCondition	1
SmoothCondition	0
LowCongestionCondition	1
HighCongestionCondition	0
NormalCongestionCondition	2
EvenPaceStyle	1
AggressiveStyle	0

2.1.2 Data Scaling
Data Scaling provides a way to Standardize the data used in this dataset. The data is largely distributed across many columns and ranges provides difficulty when trying to standardise the data. There are many studies which show scaling techniques have a significant effect on data analysis. Types of data scaling used in this project included:

1.	Standard Scaling: This involves transforming data, so it fits within a specific scale e.g., 1-1000. By scaling variables, you can compare different variables on equal footing.

2.	Min-Max Scaling: This method normalises the input features/variables using the Min-Max scaler. All the features are transformed into the range [0,1]. This allocates 0 and 1 as the only Min-Max values for a variable.

Each scaled dataset was assigned to a different DataFrame for further analysis. This gives the count of datasets for each vehicle equal to 3, the original, Standard Scaled and Min-Max Scaled. In the next section, the datasets are analysed further and visualised.

2.2 Data Analysis and Visualisation
The cleaned data is ready to be analysed further and visualised. For this project the following data analysis techniques were used to produce the optimal datasets for the classifier models.

2.2.1 Multicollinearity
Using a combination of a correlation matrix and Variance Inflation Factor (VIF) analysis, the features are analysed to determine how highly correlated they are too each other. The two main problems we may find with highly correlated data are overfitting of the model and the stability of the model. To minimize this issue, the features were first visually analysed and then analysed using VIF. Any feature that presented a VIF percentage over 10% were removed from the dataset.

2.2.2 Principal Component Analysis
After the data was cleaned of highly correlated features, it was then analysed using Principal Component Analysis. A combination of 2D and 3D analysis were used to present data that is on dimensionality which can be presented using 2D and 3D plotting techniques.

2D PCA: Based on 2d image matrices rather than 1d vectors. 2D PCA can yield higher recognition rates on data than PCA alone as demonstrated in (Yang, 2004). This method creates a 2D scatter plot. The data is plotted with the 2 most descriptive principal components. 3D PCA: Like the 2D method but uses a 3D scatter plot with the 3 most descriptive principal components. 

3 Experiments and results

3.1 Datasets
After the Principal Component Analysis (PCA) was completed, the results for each y output were recorded with their 3 corresponding PCA values also recorded in separate datasets. This allows the model to be trained on 3 features and classify the y value based off these features. Each model was trained on each vehicle’s training dataset and scored based on the test set for each vehicle. The smaller subsets with outputs, roadSurface, traffic and drivingStlye, were also scored individually within each vehicles analysis. This method allows the models to score each y output based on their 3 PCA features identified in part 2. 

Datasets
Peugeot	Corsa
Peugeot Min-Max	Corsa Min-Max
Peugeot Standard	Corsa Standard

Outputs
roadSurface
traffic
drivingStyle


3.2 Classifier models
For this project, a Logistical Regression model was compared against a Random Forest classifier. 
3.2.1 Logistical Regression
The Logistical Regression model was chosen as the model is used to predict the probability of a certain event existing, e.g., Pass/Fail. As the outcomes were largely binary outcomes, this model appeals to the data presented in this project. For this project, the model was imported from the Sklearn library and trained using its default parameters. 

3.2.2 Random Forest
Like the Logistical Regression model, the Random Forest model uses a similar approach to its classification. The Random Forest is composed of many decision trees which can work on a binary classification method. The Random Forest classifier was also imported from the Sklearn library, using the parameters (n_estimaros=1000, max_depth=3, min_samples_leaf=10).

3.3 Results
Dataset	Logistic Regression	Random Forest
roadSurface	traffic	drivingStyle	roadSurface	traffic	drivingStyle
Peugeot Not Scaled	0.73	0.61	0.94	0.79	0.65	0.94
Peugeot Min Max	0.82	0.67	0.94	0.84	0.68	0.94
Peugeot Standard	0.90	0.67	0.94	0.90	0.69	0.94
Corsa Not Scaled	0.96	0.90	0.82	0.96	0.90	0.82
Corsa Min Max	0.96	0.89	0.82	0.96	0.90	0.82
Corsa Standard	0.96	0.89	0.82	0.96	0.90	0.82

4 Conclusion
Based on the findings in part 3.3, we can conclude the optimal output for each dataset. A common high scoring output for the Peugeot dataset was ‘drivingStyle’ with an average score of 0.94 from both models. For the Corsa dataset, we can conclude that the high scoring output across both models was ‘roadSurface’, with an average score of 0.96. For further research, the parameters of each model could be altered to see if higher scores can be produced. The dataset outputs were also highly in-balanced, which may cause bias in the models. Another area of improvement may be the sample size of the training data. The dataset’s size may have been a contributing factor to the in-balance in the data outputs. Further tests with smaller dataset sizes and more balanced outputs could produce higher scores for each model across both datasets.

References
Amancio DR, C. C. C. D. T. G. B. O. R. F. e. a., 2014. A systematic comparison of supervised classifiers.. Plos ONE, 9(4).
Osisanwo F.Y., A. J. A. O. H. J. O. O. O. A. J., 2017. Supervised Machine Learning Algorithms:. International Journal of Computer Trends and Technology (IJCTT) , 48(3), pp. 1-11.
Raluca-Marian, S., 2012. A Comparison of data classification methods.. Procedia economics and finance,, Volume 3, pp. 420-425.
Yang, J. Z. D. F. A. &. Y. J., 2004. Two-dimensional PCA: a new approach to appearance based face representation and recognition.. IEEE transactions on pattern analysis and machine intelligence, 26(1), pp. 131-137.



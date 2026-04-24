Aim
To study and implement Association Rule Mining using Python and understand how relationships among items in transactional data are discovered. The objective of this experiment is to generate frequent itemsets, apply association rules, and analyze measures such as support, confidence, and lift using Python libraries.

Theory
Introduction to Association Rule Mining
Association Rule Mining is a data mining technique used to identify interesting relationships or patterns between variables in large datasets. It is commonly used in market basket analysis to determine which items are purchased together.
It helps answer questions such as:

Association rules are represented as:
X→YX \rightarrow YX→Y
Where:
X = Antecedent (If part)
Y = Consequent (Then part)

Libraries Used in Experiment
import pandas as pdimport numpy as npimport matplotlib.pyplot as plt
Theory of Libraries:
pandas
Used for loading and handling transactional datasets.
numpy
Used for numerical operations.
matplotlib.pyplot
Used for graph plotting and visualization.

Functions Used in Detail
1. Reading Dataset
df = pd.read_csv("transactions.csv")
Function Used: pd.read_csv()
Loads CSV file into DataFrame format.

2. Display First Rows
df.head()
Function Used: head()
Displays first five rows of dataset.

3. Shape of Dataset
df.shape
Function Used: shape
Returns number of rows and columns.

4. Dataset Information
df.info()
Function Used: info()

Displays:
Column names
Data types
Non-null values
Memory usage

5. Convert Data into Basket Format
basket = df.groupby(['Transaction','Item'])['Item'].count().unstack().fillna(0)
Functions Used:
groupby()
Groups data based on transaction and item.
count()
Counts frequency.
unstack()
Converts grouped table into matrix format.
fillna(0)
Replaces missing values with 0.

6. Binary Conversion
basket = basket.applymap(lambda x: 1 if x > 0 else 0)
Functions Used:
applymap()
Applies function to each DataFrame element.
lambda
Anonymous function.

Converts counts into:
1 = Item present
0 = Item absent

Generating Association Rules
from mlxtend.frequent_patterns import association_rulesrules = association_rules(frequent_items, metric="confidence", min_threshold=0.5)
Function Used: association_rules()
Creates rules from frequent itemsets.

Parameters:
metric="confidence" → Rule evaluation metric
min_threshold=0.5 → Minimum confidence value

Confidence Formula
Confidence(X→Y)=Support(X∪Y)Support(X)Confidence(X\rightarrow Y)=\frac{Support(X\cup Y)}{Support(X)}Confidence(X→Y)=Support(X)Support(X∪Y)​
Confidence measures probability of buying Y when X is bought.

Lift Formula
Lift(X→Y)=Confidence(X→Y)Support(Y)Lift(X\rightarrow Y)=\frac{Confidence(X\rightarrow Y)}{Support(Y)}Lift(X→Y)=Support(Y)Confidence(X→Y)​
Lift shows strength of relationship.

Lift > 1 → Positive relation
Lift = 1 → Independent
Lift < 1 → Negative relation

Display Rules
rules.head()
Function Used: head()
Displays top generated rules.

Sorting Rules
rules.sort_values(by='confidence', ascending=False)
Functions Used:
sort_values()
Sorts rows based on selected column.
ascending=False
Descending order.

Visualization
plt.scatter(rules['support'], rules['confidence'])plt.xlabel("Support")plt.ylabel("Confidence")plt.title("Association Rules")plt.show()

Functions Used:
scatter() → Scatter plot
xlabel() → X-axis label
ylabel() → Y-axis label
title() → Graph title
show() → Display graph

Applications of Association Rule Mining
Market basket analysis
Product recommendation systems
Cross-selling strategies
Website click analysis
Medical diagnosis patterns
Fraud detection

Plotly: A Python library used to create interactive and dynamic visualizations with zooming, hovering, and animation features.
Treemap: A visualization used to represent hierarchical data using nested rectangles where size indicates value.
px.treemap(): A Plotly Express function used to generate treemap charts by specifying hierarchy and values.
path: Defines the hierarchical structure of data in a treemap using column names.
values: Determines the size of each rectangle based on numerical data.
Dendrogram: A tree-like diagram used to represent hierarchical clustering and relationships between data points.
Hierarchical Clustering: A method of grouping data based on similarity, forming clusters step by step.
linkage(): A function used to compute distances between clusters and form hierarchical relationships.
method='ward': A clustering method that minimizes variance within clusters during grouping.
dendrogram(): A function used to visualize hierarchical clustering in a tree structure.
Venn Diagram: A diagram used to show relationships and common elements between two or more sets.
matplotlib_venn: A Python library specifically used to create Venn diagrams.
venn2(): A function used to create a Venn diagram for two sets showing their intersection.
Sankey Diagram: A flow diagram used to represent movement of data or resources between different stages.
node: Represents individual entities or stages in a Sankey diagram.
link: Represents connections or flow between nodes in a Sankey diagram.
source & target: Define the starting and ending points of flow between nodes.
value: Indicates the quantity or magnitude of flow between nodes.
3D Plot: A graph used to visualize data in three dimensions using x, y, and z axes.
px.scatter_3d(): A Plotly function used to create 3D scatter plots for multi-variable visualization.
Radar Chart: A circular chart used to compare multiple variables on different axes.
Scatterpolar: A plot type used to create radar charts in polar coordinates.
r: Represents the magnitude or values plotted on the radial axis in radar chart.
theta: Represents categories or variables arranged around the circular axis.
fill='toself': Used to fill the area inside the radar chart for better visualization.

Conclusion
Thus, the experiment on Association Rule Mining using Python was successfully performed.
Transactional data was loaded and converted into basket format.
Frequent itemsets were generated using the Apriori algorithm, and strong association rules were created using confidence and lift measures.
Functions such as read_csv(), head(), shape, info(), groupby(), count(), unstack(), fillna(), applymap(), apriori(), association_rules(), sort_values(), scatter(), show() were studied in detail
. This experiment helped in understanding how hidden relationships in large datasets can be discovered effectively.

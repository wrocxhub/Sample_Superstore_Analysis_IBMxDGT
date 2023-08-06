# Superstore Sales Analysis_IBMxDGT
Data and Business Analysis Research on Superstore Datset
Project Overview:
The project "Superstore Sales Analysis" aims to gain insights into sales trends, customer behavior, and operational efficiency of a fictional supermarket.

The main objectives are to:

• Identify sales trends and patterns to optimize inventory management and sales forecasting.

• Understand customer demographics, preferences and purchase patterns to develop targeted marketing strategies.

• Improve operational efficiency by identifying bottlenecks and optimizing resource allocation.

• Provide data-driven recommendations to optimize store performance and profitability.

Tools and Technologies used:

• Data Cleaning and Preparation: Python (Pandas, NumPy).

• Exploratory Data Analysis: Python (Matplotlib, Seaborn).

• Sales Forecasting: Time series analysis.

• Data Visualization: Plotly & Matplotlib.

Future Methodologies:

• Customer Segmentation: Clustering algorithms (K-means, Hierarchical clustering).

• Geospatial Analysis: Python (Geopandas, Folium).

• Data Visualization: Tableau, Power BI, Python visualization Plotly libraries.


Analytical Study of a Superstore Dataset based in United States : The Data Science Approach
Exploratory Data Analysis on Retail Superstore

Dataset : US based Sample Superstore

Task category: Data Science and Business Analytics

Dataset Volume : 9994 rows × 12 columns

Important steps involved in this Study:
Defining the problem
Importing all necessary Libraries
Loading and exploring data
Cleaning and Pre-Processing of the Data
Exploratory Data analysis (EDA) to understand patterns, trends & insights
Visualization of findings
Statistical Analysis
Conclusion
1. Defining the Problem Statement:
The business is growing down and the stakeholders are seeking for an analysis to support the business managers to work upon the delicate areas to make necessary improvements for making more profits.

2. Importing the necessary libraries:
# To load all necessary libraries
import pandas as pd; print ("Pandas version:",pd.__version__)
import numpy as np; print ("NumPy version:", np.__version__)
import matplotlib.pyplot as plt
import seaborn as sns; print ("SeaBorn version:", sns.__version__)
import plotly.express as px
import plotly.graph_objects as go
import plotly.io as pio
import plotly.colors as colors
from plotly.subplots import make_subplots
pio.templates.default = "plotly_white" 
import scipy.stats as stats
import warnings
warnings.filterwarnings("ignore")
Pandas version: 1.5.3
NumPy version: 1.23.5
SeaBorn version: 0.12.2
3. Loading the CSV file into a pandas DataFrame:
# To load Dataset / Data Sourcing
df = pd.read_csv("SampleSuperstore.csv")
print(df.shape)
(9994, 13)
3(b). Exploring the Data
# Display the first few rows of the DataFrame
print(df.head())

# Check the summary statistics of numerical columns
print(df.describe())

# Check the data types of each column
print(df.dtypes)

# Check the number of rows and columns in the DataFrame
print(df.shape)
        Ship Mode    Segment        Country             City       State  \
0    Second Class   Consumer  United States        Henderson    Kentucky   
1    Second Class   Consumer  United States        Henderson    Kentucky   
2    Second Class  Corporate  United States      Los Angeles  California   
3  Standard Class   Consumer  United States  Fort Lauderdale     Florida   
4  Standard Class   Consumer  United States  Fort Lauderdale     Florida   

   Postal Code Region         Category Sub-Category     Sales  Quantity  \
0        42420  South        Furniture    Bookcases  261.9600         2   
1        42420  South        Furniture       Chairs  731.9400         3   
2        90036   West  Office Supplies       Labels   14.6200         2   
3        33311  South        Furniture       Tables  957.5775         5   
4        33311  South  Office Supplies      Storage   22.3680         2   

   Discount  Profit  
0      0.00   41.91  
1      0.00  219.58  
2      0.00    6.87  
3      0.45 -383.03  
4      0.20    2.52  
        Postal Code         Sales     Quantity     Discount       Profit
count   9994.000000   9994.000000  9994.000000  9994.000000  9994.000000
mean   55190.379428    229.858001     3.789574     0.156203    28.656973
std    32063.693350    623.245101     2.225110     0.206452   234.260203
min     1040.000000      0.444000     1.000000     0.000000 -6599.980000
25%    23223.000000     17.280000     2.000000     0.000000     1.730000
50%    56430.500000     54.490000     3.000000     0.200000     8.665000
75%    90008.000000    209.940000     5.000000     0.200000    29.360000
max    99301.000000  22638.480000    14.000000     0.800000  8399.980000
Ship Mode        object
Segment          object
Country          object
City             object
State            object
Postal Code       int64
Region           object
Category         object
Sub-Category     object
Sales           float64
Quantity          int64
Discount        float64
Profit          float64
dtype: object
(9994, 13)
df.head()
Ship Mode	Segment	Country	City	State	Postal Code	Region	Category	Sub-Category	Sales	Quantity	Discount	Profit
0	Second Class	Consumer	United States	Henderson	Kentucky	42420	South	Furniture	Bookcases	261.9600	2	0.00	41.91
1	Second Class	Consumer	United States	Henderson	Kentucky	42420	South	Furniture	Chairs	731.9400	3	0.00	219.58
2	Second Class	Corporate	United States	Los Angeles	California	90036	West	Office Supplies	Labels	14.6200	2	0.00	6.87
3	Standard Class	Consumer	United States	Fort Lauderdale	Florida	33311	South	Furniture	Tables	957.5775	5	0.45	-383.03
4	Standard Class	Consumer	United States	Fort Lauderdale	Florida	33311	South	Office Supplies	Storage	22.3680	2	0.20	2.52
# To know the Unique Values present in specifc individual Column using Pandas
print(df["Ship Mode"].unique())
print(df["Segment"].unique())
print(df["Country"].unique())
print(df["City"].unique())
print(df["Category"].unique())
print(df["Sub-Category"].unique())
['Second Class' 'Standard Class' 'First Class' 'Same Day']
['Consumer' 'Corporate' 'Home Office']
['United States']
['Henderson' 'Los Angeles' 'Fort Lauderdale' 'Concord' 'Seattle'
 'Fort Worth' 'Madison' 'West Jordan' 'San Francisco' 'Fremont'
 'Philadelphia' 'Orem' 'Houston' 'Richardson' 'Naperville' 'Melbourne'
 'Eagan' 'Westland' 'Dover' 'New Albany' 'New York City' 'Troy' 'Chicago'
 'Gilbert' 'Springfield' 'Jackson' 'Memphis' 'Decatur' 'Durham' 'Columbia'
 'Rochester' 'Minneapolis' 'Portland' 'Saint Paul' 'Aurora' 'Charlotte'
 'Orland Park' 'Urbandale' 'Columbus' 'Bristol' 'Wilmington' 'Bloomington'
 'Phoenix' 'Roseville' 'Independence' 'Pasadena' 'Newark' 'Franklin'
 'Scottsdale' 'San Jose' 'Edmond' 'Carlsbad' 'San Antonio' 'Monroe'
 'Fairfield' 'Grand Prairie' 'Redlands' 'Hamilton' 'Westfield' 'Akron'
 'Denver' 'Dallas' 'Whittier' 'Saginaw' 'Medina' 'Dublin' 'Detroit'
 'Tampa' 'Santa Clara' 'Lakeville' 'San Diego' 'Brentwood' 'Chapel Hill'
 'Morristown' 'Cincinnati' 'Inglewood' 'Tamarac' 'Colorado Springs'
 'Belleville' 'Taylor' 'Lakewood' 'Arlington' 'Arvada' 'Hackensack'
 'Saint Petersburg' 'Long Beach' 'Hesperia' 'Murfreesboro' 'Layton'
 'Austin' 'Lowell' 'Manchester' 'Harlingen' 'Tucson' 'Quincy'
 'Pembroke Pines' 'Des Moines' 'Peoria' 'Las Vegas' 'Warwick' 'Miami'
 'Huntington Beach' 'Richmond' 'Louisville' 'Lawrence' 'Canton'
 'New Rochelle' 'Gastonia' 'Jacksonville' 'Auburn' 'Norman' 'Park Ridge'
 'Amarillo' 'Lindenhurst' 'Huntsville' 'Fayetteville' 'Costa Mesa'
 'Parker' 'Atlanta' 'Gladstone' 'Great Falls' 'Lakeland' 'Montgomery'
 'Mesa' 'Green Bay' 'Anaheim' 'Marysville' 'Salem' 'Laredo' 'Grove City'
 'Dearborn' 'Warner Robins' 'Vallejo' 'Mission Viejo' 'Rochester Hills'
 'Plainfield' 'Sierra Vista' 'Vancouver' 'Cleveland' 'Tyler' 'Burlington'
 'Waynesboro' 'Chester' 'Cary' 'Palm Coast' 'Mount Vernon' 'Hialeah'
 'Oceanside' 'Evanston' 'Trenton' 'Cottage Grove' 'Bossier City'
 'Lancaster' 'Asheville' 'Lake Elsinore' 'Omaha' 'Edmonds' 'Santa Ana'
 'Milwaukee' 'Florence' 'Lorain' 'Linden' 'Salinas' 'New Brunswick'
 'Garland' 'Norwich' 'Alexandria' 'Toledo' 'Farmington' 'Riverside'
 'Torrance' 'Round Rock' 'Boca Raton' 'Virginia Beach' 'Murrieta'
 'Olympia' 'Washington' 'Jefferson City' 'Saint Peters' 'Rockford'
 'Brownsville' 'Yonkers' 'Oakland' 'Clinton' 'Encinitas' 'Roswell'
 'Jonesboro' 'Antioch' 'Homestead' 'La Porte' 'Lansing' 'Cuyahoga Falls'
 'Reno' 'Harrisonburg' 'Escondido' 'Royal Oak' 'Rockville' 'Coral Springs'
 'Buffalo' 'Boynton Beach' 'Gulfport' 'Fresno' 'Greenville' 'Macon'
 'Cedar Rapids' 'Providence' 'Pueblo' 'Deltona' 'Murray' 'Middletown'
 'Freeport' 'Pico Rivera' 'Provo' 'Pleasant Grove' 'Smyrna' 'Parma'
 'Mobile' 'New Bedford' 'Irving' 'Vineland' 'Glendale' 'Niagara Falls'
 'Thomasville' 'Westminster' 'Coppell' 'Pomona' 'North Las Vegas'
 'Allentown' 'Tempe' 'Laguna Niguel' 'Bridgeton' 'Everett' 'Watertown'
 'Appleton' 'Bellevue' 'Allen' 'El Paso' 'Grapevine' 'Carrollton' 'Kent'
 'Lafayette' 'Tigard' 'Skokie' 'Plano' 'Suffolk' 'Indianapolis' 'Bayonne'
 'Greensboro' 'Baltimore' 'Kenosha' 'Olathe' 'Tulsa' 'Redmond' 'Raleigh'
 'Muskogee' 'Meriden' 'Bowling Green' 'South Bend' 'Spokane' 'Keller'
 'Port Orange' 'Medford' 'Charlottesville' 'Missoula' 'Apopka' 'Reading'
 'Broomfield' 'Paterson' 'Oklahoma City' 'Chesapeake' 'Lubbock'
 'Johnson City' 'San Bernardino' 'Leominster' 'Bozeman' 'Perth Amboy'
 'Ontario' 'Rancho Cucamonga' 'Moorhead' 'Mesquite' 'Stockton'
 'Ormond Beach' 'Sunnyvale' 'York' 'College Station' 'Saint Louis'
 'Manteca' 'San Angelo' 'Salt Lake City' 'Knoxville' 'Little Rock'
 'Lincoln Park' 'Marion' 'Littleton' 'Bangor' 'Southaven' 'New Castle'
 'Midland' 'Sioux Falls' 'Fort Collins' 'Clarksville' 'Sacramento'
 'Thousand Oaks' 'Malden' 'Holyoke' 'Albuquerque' 'Sparks' 'Coachella'
 'Elmhurst' 'Passaic' 'North Charleston' 'Newport News' 'Jamestown'
 'Mishawaka' 'La Quinta' 'Tallahassee' 'Nashville' 'Bellingham'
 'Woodstock' 'Haltom City' 'Wheeling' 'Summerville' 'Hot Springs'
 'Englewood' 'Las Cruces' 'Hoover' 'Frisco' 'Vacaville' 'Waukesha'
 'Bakersfield' 'Pompano Beach' 'Corpus Christi' 'Redondo Beach' 'Orlando'
 'Orange' 'Lake Charles' 'Highland Park' 'Hempstead' 'Noblesville'
 'Apple Valley' 'Mount Pleasant' 'Sterling Heights' 'Eau Claire' 'Pharr'
 'Billings' 'Gresham' 'Chattanooga' 'Meridian' 'Bolingbrook' 'Maple Grove'
 'Woodland' 'Missouri City' 'Pearland' 'San Mateo' 'Grand Rapids'
 'Visalia' 'Overland Park' 'Temecula' 'Yucaipa' 'Revere' 'Conroe'
 'Tinley Park' 'Dubuque' 'Dearborn Heights' 'Santa Fe' 'Hickory'
 'Carol Stream' 'Saint Cloud' 'North Miami' 'Plantation'
 'Port Saint Lucie' 'Rock Hill' 'Odessa' 'West Allis' 'Chula Vista'
 'Manhattan' 'Altoona' 'Thornton' 'Champaign' 'Texarkana' 'Edinburg'
 'Baytown' 'Greenwood' 'Woonsocket' 'Superior' 'Bedford' 'Covington'
 'Broken Arrow' 'Miramar' 'Hollywood' 'Deer Park' 'Wichita' 'Mcallen'
 'Iowa City' 'Boise' 'Cranston' 'Port Arthur' 'Citrus Heights'
 'The Colony' 'Daytona Beach' 'Bullhead City' 'Portage' 'Fargo' 'Elkhart'
 'San Gabriel' 'Margate' 'Sandy Springs' 'Mentor' 'Lawton' 'Hampton'
 'Rome' 'La Crosse' 'Lewiston' 'Hattiesburg' 'Danville' 'Logan'
 'Waterbury' 'Athens' 'Avondale' 'Marietta' 'Yuma' 'Wausau' 'Pasco'
 'Oak Park' 'Pensacola' 'League City' 'Gaithersburg' 'Lehi' 'Tuscaloosa'
 'Moreno Valley' 'Georgetown' 'Loveland' 'Chandler' 'Helena' 'Kirkwood'
 'Waco' 'Frankfort' 'Bethlehem' 'Grand Island' 'Woodbury' 'Rogers'
 'Clovis' 'Jupiter' 'Santa Barbara' 'Cedar Hill' 'Norfolk' 'Draper'
 'Ann Arbor' 'La Mesa' 'Pocatello' 'Holland' 'Milford' 'Buffalo Grove'
 'Lake Forest' 'Redding' 'Chico' 'Utica' 'Conway' 'Cheyenne' 'Owensboro'
 'Caldwell' 'Kenner' 'Nashua' 'Bartlett' 'Redwood City' 'Lebanon'
 'Santa Maria' 'Des Plaines' 'Longview' 'Hendersonville' 'Waterloo'
 'Cambridge' 'Palatine' 'Beverly' 'Eugene' 'Oxnard' 'Renton' 'Glenview'
 'Delray Beach' 'Commerce City' 'Texas City' 'Wilson' 'Rio Rancho'
 'Goldsboro' 'Montebello' 'El Cajon' 'Beaumont' 'West Palm Beach'
 'Abilene' 'Normal' 'Saint Charles' 'Camarillo' 'Hillsboro' 'Burbank'
 'Modesto' 'Garden City' 'Atlantic City' 'Longmont' 'Davis' 'Morgan Hill'
 'Clifton' 'Sheboygan' 'East Point' 'Rapid City' 'Andover' 'Kissimmee'
 'Shelton' 'Danbury' 'Sanford' 'San Marcos' 'Greeley' 'Mansfield' 'Elyria'
 'Twin Falls' 'Coral Gables' 'Romeoville' 'Marlborough' 'Laurel' 'Bryan'
 'Pine Bluff' 'Aberdeen' 'Hagerstown' 'East Orange' 'Arlington Heights'
 'Oswego' 'Coon Rapids' 'San Clemente' 'San Luis Obispo' 'Springdale'
 'Lodi' 'Mason']
['Furniture' 'Office Supplies' 'Technology']
['Bookcases' 'Chairs' 'Labels' 'Tables' 'Storage' 'Furnishings' 'Art'
 'Phones' 'Binders' 'Appliances' 'Paper' 'Accessories' 'Envelopes'
 'Fasteners' 'Supplies' 'Machines' 'Copiers']
4. Cleaning Data / Removing Unnecessary Data Columns and Outliers
# To drop unnecessary columns - Data Cleaning
df.drop(columns="Postal Code", inplace=True)
# Verifying the absense of the removed  unnecessary Column 
df.head()
Ship Mode	Segment	Country	City	State	Region	Category	Sub-Category	Sales	Quantity	Discount	Profit
0	Second Class	Consumer	United States	Henderson	Kentucky	South	Furniture	Bookcases	261.9600	2	0.00	41.91
1	Second Class	Consumer	United States	Henderson	Kentucky	South	Furniture	Chairs	731.9400	3	0.00	219.58
2	Second Class	Corporate	United States	Los Angeles	California	West	Office Supplies	Labels	14.6200	2	0.00	6.87
3	Standard Class	Consumer	United States	Fort Lauderdale	Florida	South	Furniture	Tables	957.5775	5	0.45	-383.03
4	Standard Class	Consumer	United States	Fort Lauderdale	Florida	South	Office Supplies	Storage	22.3680	2	0.20	2.52
df.info() # To know the Info (null values and Data Type) of the Data
sns.heatmap(df.isna(),yticklabels=False,cbar=False,cmap="viridis")
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 9994 entries, 0 to 9993
Data columns (total 12 columns):
 #   Column        Non-Null Count  Dtype  
---  ------        --------------  -----  
 0   Ship Mode     9994 non-null   object 
 1   Segment       9994 non-null   object 
 2   Country       9994 non-null   object 
 3   City          9994 non-null   object 
 4   State         9994 non-null   object 
 5   Region        9994 non-null   object 
 6   Category      9994 non-null   object 
 7   Sub-Category  9994 non-null   object 
 8   Sales         9994 non-null   float64
 9   Quantity      9994 non-null   int64  
 10  Discount      9994 non-null   float64
 11  Profit        9994 non-null   float64
dtypes: float64(3), int64(1), object(8)
memory usage: 937.1+ KB
<Axes: >

df.isna() # Another method To know if there is null value in any fields 
Ship Mode	Segment	Country	City	State	Region	Category	Sub-Category	Sales	Quantity	Discount	Profit
0	False	False	False	False	False	False	False	False	False	False	False	False
1	False	False	False	False	False	False	False	False	False	False	False	False
2	False	False	False	False	False	False	False	False	False	False	False	False
3	False	False	False	False	False	False	False	False	False	False	False	False
4	False	False	False	False	False	False	False	False	False	False	False	False
...	...	...	...	...	...	...	...	...	...	...	...	...
9989	False	False	False	False	False	False	False	False	False	False	False	False
9990	False	False	False	False	False	False	False	False	False	False	False	False
9991	False	False	False	False	False	False	False	False	False	False	False	False
9992	False	False	False	False	False	False	False	False	False	False	False	False
9993	False	False	False	False	False	False	False	False	False	False	False	False
9994 rows × 12 columns

df.isna().sum() # Different method  To know if there is any Null values in any of the column
Ship Mode       0
Segment         0
Country         0
City            0
State           0
Region          0
Category        0
Sub-Category    0
Sales           0
Quantity        0
Discount        0
Profit          0
dtype: int64
# To describe or summarise the data Statistacaly
df.describe()
Sales	Quantity	Discount	Profit
count	9994.000000	9994.000000	9994.000000	9994.000000
mean	229.858001	3.789574	0.156203	28.656973
std	623.245101	2.225110	0.206452	234.260203
min	0.444000	1.000000	0.000000	-6599.980000
25%	17.280000	2.000000	0.000000	1.730000
50%	54.490000	3.000000	0.200000	8.665000
75%	209.940000	5.000000	0.200000	29.360000
max	22638.480000	14.000000	0.800000	8399.980000
# To check for duplicates in the data
df.duplicated().sum()
50
df.drop_duplicates()
Ship Mode	Segment	Country	City	State	Region	Category	Sub-Category	Sales	Quantity	Discount	Profit
0	Second Class	Consumer	United States	Henderson	Kentucky	South	Furniture	Bookcases	261.9600	2	0.00	41.91
1	Second Class	Consumer	United States	Henderson	Kentucky	South	Furniture	Chairs	731.9400	3	0.00	219.58
2	Second Class	Corporate	United States	Los Angeles	California	West	Office Supplies	Labels	14.6200	2	0.00	6.87
3	Standard Class	Consumer	United States	Fort Lauderdale	Florida	South	Furniture	Tables	957.5775	5	0.45	-383.03
4	Standard Class	Consumer	United States	Fort Lauderdale	Florida	South	Office Supplies	Storage	22.3680	2	0.20	2.52
...	...	...	...	...	...	...	...	...	...	...	...	...
9989	Second Class	Consumer	United States	Miami	Florida	South	Furniture	Furnishings	25.2480	3	0.20	4.10
9990	Standard Class	Consumer	United States	Costa Mesa	California	West	Furniture	Furnishings	91.9600	2	0.00	15.63
9991	Standard Class	Consumer	United States	Costa Mesa	California	West	Technology	Phones	258.5760	2	0.20	19.39
9992	Standard Class	Consumer	United States	Costa Mesa	California	West	Office Supplies	Paper	29.6000	4	0.00	13.32
9993	Second Class	Consumer	United States	Westminster	California	West	Office Supplies	Appliances	243.1600	2	0.00	72.95
9944 rows × 12 columns

5. Exploratory Data analysis (EDA) to understand patterns, trends & insights
df.corr() # To know the corelation b/w the columns ex: Sales v/s Profit or Quantity vs Profit .. Note: Only numerical values are considered
Sales	Quantity	Discount	Profit
Sales	1.000000	0.200795	-0.028190	0.479065
Quantity	0.200795	1.000000	0.008623	0.066253
Discount	-0.028190	0.008623	1.000000	-0.219488
Profit	0.479065	0.066253	-0.219488	1.000000
df.cov() # Covariance is used to measure the corelation b/w the columns. Covariance represents the rate at which the columns are corelated to eachother
Sales	Quantity	Discount	Profit
Sales	388434.455308	278.459923	-3.627228	69944.147979
Quantity	278.459923	4.951113	0.003961	34.534806
Discount	-3.627228	0.003961	0.042622	-10.615189
Profit	69944.147979	34.534806	-10.615189	54877.842658
Covariance between "Sales" and "Sales":

Cov(Sales, Sales) = 388434.455308 This value represents the variance of the "Sales" variable. Since covariance measures the relationship between two instances of the same variable, the covariance of a variable with itself is its variance. Covariance between "Sales" and "Quantity":

Cov(Sales, Quantity) = 278.459923 This value indicates the covariance between "Sales" and "Quantity." It shows how the sales and quantity vary together. A positive covariance suggests that as sales increase, the quantity sold also tends to increase. Covariance between "Sales" and "Discount":

# Create a pivot table to calculate the average sales and profit by category and region
pivot_table = pd.pivot_table(df, values=['Sales', 'Profit'],
                             index='Category', columns='Region',
                             aggfunc={'Sales': 'mean', 'Profit': 'mean'})

print(pivot_table)
                    Profit                                        Sales  \
Region             Central       East      South       West     Central   
Category                                                                  
Furniture        -5.969023   5.068552  20.395271  16.272871  340.534644   
Office Supplies   6.244691  23.957079  20.086955  27.733205  117.458801   
Technology       80.232381  88.714243  68.231945  73.963239  405.753124   

                                                     
Region                 East       South        West  
Category                                             
Furniture        346.574383  353.309289  357.302325  
Office Supplies  120.044425  126.282727  116.422377  
Technology       495.278469  507.753952  420.687533  
# To group the data by customer segment and calculate total sales and profit
grouped_data = df.groupby('Segment').agg({'Sales': 'sum', 'Profit': 'sum'}).reset_index()

# Sort the data by sales in descending order
grouped_data = grouped_data.sort_values('Sales', ascending=False)

# Calculate average sales and profit per segment
grouped_data['Average Sales'] = grouped_data['Sales'] / df.groupby('Segment')['Sales'].count()
grouped_data['Average Profit'] = grouped_data['Profit'] / df.groupby('Segment')['Profit'].count()

# Display the results
print(grouped_data)
       Segment         Sales     Profit  Average Sales  Average Profit
0     Consumer  1.161401e+06  134119.33            NaN             NaN
1    Corporate  7.061464e+05   91979.45            NaN             NaN
2  Home Office  4.296531e+05   60299.01            NaN             NaN
# Perform the Pearson correlation test
result = stats.pearsonr(df['Discount'], df['Profit'])

# Print the result
print("Pearson correlation coefficient:", result[0])
print("Correlation p-value:", result[1])
Pearson correlation coefficient: -0.21948771072704854
Correlation p-value: 2.7007080625903815e-109
# Calculate the frequency of each shipping mode
shipping_mode_counts = df['Ship Mode'].value_counts()

# Display the frequency of each shipping mode
print(shipping_mode_counts)

# Group the data by shipping mode and calculate the average profit
grouped_data = df.groupby('Ship Mode')['Profit'].mean().reset_index()

# Perform a correlation test between shipping mode and profit
result = stats.pointbiserialr(df['Ship Mode'].map(grouped_data.set_index('Ship Mode')['Profit']), df['Profit'])

# Print the correlation coefficient and p-value
print("Correlation coefficient:", result.correlation)
print("Correlation p-value:", result.pvalue)
Standard Class    5968
Second Class      1945
First Class       1538
Same Day           543
Name: Ship Mode, dtype: int64
Correlation coefficient: 0.006798324290901532
Correlation p-value: 0.49678862028435117
The above chart denotes as the business is not performing Satisfactory Profits

6. Visualization of Data and The Findings
# Filter out non-numeric columns
numeric_columns = df.select_dtypes(include=[int, float]).columns


# Create histograms for all numeric columns
plt.figure(figsize=(10, 10))
df[numeric_columns].hist(bins=30, figsize=(15, 5))
plt.tight_layout()  # To improve the spacing between subplots
plt.show()
<Figure size 1000x1000 with 0 Axes>

The above charts Displays

The Histogram of Sales, Quantity, Discount, Profit.
Findings:

The above visual explains:

There are only few highly discounted products which can be Good or bad which the further analysis can reveal.

2 and 3 is the minimum quantity ordered Maximum

# To Create the pair plot
fig = px.scatter_matrix(df, dimensions=df.select_dtypes(include=[int, float]).columns,
                        color='Sub-Category', title='Pair Plot', height=500)

# To Update the layout and show the plot
fig.update_layout(width=2000, height=1000)
fig.show()
The above charts Displays

The Pair Plot of sub-Category
# Calculate the total overall sales and profit
total_sales = df['Sales'].sum()
total_profit = df['Profit'].sum()

# Calculate the percentage of total sales and profit
profit_percentage = (total_profit / (total_sales + total_profit)) * 100

# Create a bar graph
fig = go.Figure()
fig.add_trace(go.Bar(x=['Total Sales'], y=[total_sales], name='Total Sales'))

fig.add_trace(go.Bar(x=['Total Profit'], y=[total_profit], name='Total Profit'))

fig.update_layout(title='Total Overall Sales and Profit',
                  xaxis_title='Category', yaxis_title='Amount')

# Add text annotations to display the percentage on the bars
fig.add_annotation(x='Total Profit', y=total_profit, text=f'{profit_percentage:.2f}%', showarrow=False)

fig.show()
The above charts Displays

The Difference between Sales and Profit
Findings: The Total profit after the Sales of Scale 2.29M the profit is ronding to 287k which is 11% of total Sales

# Group the data by country and year, calculate sales and profit, and reset the index
grouped_data = df.groupby(['Country', 'City']).agg({'Sales': 'sum', 'Profit': 'sum'}).reset_index()

# Create line charts to visualize trends in sales and profit over time for each country
fig_sales = px.line(grouped_data, x='City', y='Sales', color='Country',
                    title='Sales Trends by Country Over Time')

fig_profit = px.line(grouped_data, x='City', y='Profit', color='Country',
                     title='Profit Trends by Country Over Time')

# Display the line charts
fig_sales.show()
fig_profit.show()
The above charts Display

Sale Trends by Country
Profit Trends by Country
Findings:

Top 5 Cities by Sales and Profit:
City -------- Sales -------- Profit

New York City , 256368.1610 , 62037.08

Los Angeles , 175851.3410 , 30440.94

Seattle , 119540.7420 , 29156.13

San Francisco , 112669.0920, 17507.39

Detroit , 42446.9440 , 13181.79

Bottom 5 Cities Sales and Loss :
City ------ Sales -----Loss

Chicago 48539.5410 -6654.55

Lancaster 9891.4640 -7239.08

San Antonio 21843.5280 -7299.06

Houston 64504.7604 -10153.48

Philadelphia 109077.0130 -13837.83

# Group the data by country and calculate sales and profit
grouped_data = df.groupby('City').agg({'Sales': 'sum', 'Profit': 'sum'}).reset_index()

# Sort the data by profit in descending order
grouped_data = grouped_data.sort_values('Profit', ascending=False)

# Display the grouped data
print(grouped_data)
              City        Sales    Profit
329  New York City  256368.1610  62037.08
266    Los Angeles  175851.3410  30440.94
452        Seattle  119540.7420  29156.13
438  San Francisco  112669.0920  17507.39
123        Detroit   42446.9440  13181.79
..             ...          ...       ...
80         Chicago   48539.5410  -6654.55
241      Lancaster    9891.4640  -7239.08
434    San Antonio   21843.5280  -7299.06
207        Houston   64504.7604 -10153.48
374   Philadelphia  109077.0130 -13837.83

[531 rows x 3 columns]
# Calculate the frequency of each shipping mode
shipping_mode_counts = df['Ship Mode'].value_counts().reset_index()
shipping_mode_counts.columns = ['Ship Mode', 'Count']

# Calculate the average profit by shipping mode
average_profit_by_mode = df.groupby('Ship Mode')['Profit'].mean().reset_index()

# Create a subplots grid with two rows and one column
fig = make_subplots(rows=2, cols=1, shared_xaxes=True, vertical_spacing=0.1)

# Add the bar chart for shipping mode popularity to the top row
fig.add_trace(go.Bar(x=shipping_mode_counts['Ship Mode'], y=shipping_mode_counts['Count']),
              row=1, col=1)

# Add the scatter plot for correlation between shipping mode and profit to the bottom row
fig.add_trace(go.Scatter(x=average_profit_by_mode['Ship Mode'], y=average_profit_by_mode['Profit'],
                         mode='markers', marker=dict(size=10)),
              row=2, col=1)

# Update the layout and labels
fig.update_layout(height=600, width=800, title='Shipping Mode v/s Profit Analysis')
fig.update_xaxes(title_text='Shipping Mode', row=2, col=1)
fig.update_yaxes(title_text='Count', row=1, col=1)
fig.update_yaxes(title_text='Profit', row=2, col=1)

# Display the stacked visualizations
fig.show()
The above charts Display

Shipping mode v/s Profit analysis
Findings:

The above visual explains that the shipping mode Standard is relatively High in number of counts when compared to other shipping classes but relatively giving less profits when compared to other classes

# Group the data by customer segments and calculate metrics
grouped_data = df.groupby('Segment').agg({
    'Sales': 'sum',
    'Profit': 'sum',
    'Quantity': 'sum',
    'Discount': 'mean'
}).reset_index()

# Display the grouped data
print(grouped_data)
       Segment         Sales     Profit  Quantity  Discount
0     Consumer  1.161401e+06  134119.33     19521  0.158141
1    Corporate  7.061464e+05   91979.45     11608  0.158228
2  Home Office  4.296531e+05   60299.01      6744  0.147128
# Bar chart for sales by customer segment
fig_sales = px.bar(grouped_data, x='Segment', y='Sales',
                   title='Total Sales by Customer Segment')

# Bar chart for profit by customer segment
fig_profit = px.bar(grouped_data, x='Segment', y='Profit',
                    title='Total Profit by Customer Segment')

# Scatter plot for quantity by customer segment
fig_quantity = px.scatter(grouped_data, x='Segment', y='Quantity',
                          title='Total Quantity by Customer Segment')

# Box plot for discount by customer segment
fig_discount = px.box(grouped_data, x='Segment', y='Discount',
                      title='Discount Distribution by Customer Segment')

# Display the visualizations
fig_sales.show()
fig_profit.show()
fig_quantity.show()
fig_discount.show()
The above charts Display

Total Sales by Customer Segment
Total Profit by Customer Segment
Total Quantity by Customer Segment
Discount Distribution by Customer Segment
Findings:

The above visual explains that

The Total Quantity, Sales and Profit in Consumer Segment is Comparitively Better followed by Corporate and Home

Customers who gave high sales and profit are mostly from the Consumer segment

Customers who gave less sales and high profit ratio are mostly from the Corporate segment

plt.figure(figsize=(20, 4))
sns.lineplot(x='Discount', y='Profit', data=df, color='r', label='Discount')
plt.legend()
plt.title('Discount vs. Profit')
plt.xlabel('Discount (%)')
plt.ylabel('Profit')
plt.show()

The above charts Display

Average Profit by Discount
Findings:

The above visual explains that

The products with 0.5% is making Huge losses when compared to others and follwed by 0.3% & 0.4%

The products with .1% or no Discounts are considered to make profits for the company

# To Create an interactive scatter plot using Plotly
fig = px.scatter(df, x='Discount', y='Profit', color='Category', symbol='Segment',
                 size='Sales', hover_name='Sub-Category', hover_data=['Sales', 'Quantity'],
                 labels={'Discount': 'Discount (%)', 'Profit': 'Profit', 'Category': 'Product Category',
                         'Segment': 'Customer Segment', 'Sales': 'Sales', 'Sub-Category': 'Sub-Category'},
                 title='Relationship between Discount and Profit by Product Category and Customer Segment',
                 template='plotly_white')

# To Customize legend and marker size
fig.update_traces(marker=dict(size=10))

fig.show()
# Group the data by category and calculate the average discount
grouped_category = df.groupby('Category').agg({'Discount': 'mean'}).reset_index()

# Create a bar chart to visualize the average discount by category
fig_category_discount = px.bar(grouped_category, x='Category', y='Discount',
                                title='Average Discount by Category')

# Display the bar chart
fig_category_discount.show()

# Group the data by sub-category and calculate the average discount
grouped_subcategory = df.groupby('Sub-Category').agg({'Discount': 'mean'}).reset_index()

# Create a bar chart to visualize the average discount by sub-category
fig_subcategory_discount = px.bar(grouped_subcategory, x='Sub-Category', y='Discount',
                                   title='Average Discount by Sub-Category')

# Display the bar chart
fig_subcategory_discount.show()
The above charts Display

Average Discount by Category
Average Discount by Sub-Category
Findings:

The above visual explains that

Overall, Furnitures category is given the highest number of discounted sales follwed by office supplies and Technology category to be least discounted.

within the sub-category Binders has the Highest Dicounts received which approx .37% followed by Machines at .30% and Tables at .26%.

segment = df['Segment'].value_counts()
# Plot the distribution of segments
fig = px.pie(segment, values=segment.values, names=segment.index, title='Customer Segment Distribution')
fig.show()
The above charts Display

Customer Segmentation by Segments ( Consumer/Corporate/Home Office )
Findings:

The above visual explains that

the customers of this company are mostly Consumer and Corporate, with a small percentage being for Home Office
# Create the interactive scatter plot using Plotly
fig = px.scatter(df, x='Quantity', y='Profit', color='Segment', symbol='Ship Mode', size='Discount',
                 size_max=10, hover_name='Sub-Category', hover_data=['Sales'],
                 labels={'Quantity': 'Quantity', 'Profit': 'Profit', 'Segment': 'Segment', 'Ship Mode': 'Ship Mode'},
                 title='Scatter Plot: Quantity vs. Profit by Segment and Ship Mode',
                 template='plotly_white')

# Customize legend
fig.update_layout(legend_title_text='Segment')

# Show the plot
fig.show()
# Create the bar graph using Plotly
fig = px.bar(df, x='Category', y='Sales', color='Segment', barmode='group',
             labels={'Category': 'Category', 'Sales': 'Sales', 'Segment': 'Segment'},
             title='Category vs. Sales with respect to Segment',
             template='plotly_white')

# Show the plot
fig.show()
grouped_data = df.groupby('Region').agg({'Sales': 'sum', 'Profit': 'sum'}).reset_index()

# Create a bar chart using Plotly
fig = px.bar(grouped_data, x='Region', y=['Sales', 'Profit'], barmode='group',
             title='Total Sales and Profit by Region')

# Set x-axis and y-axis labels
fig.update_xaxes(title_text='Region')
fig.update_yaxes(title_text='Amount')

# Display the plot
fig.show()
The above charts Display

Bar graph representation of Total Sales vs Profit based on Region
# Group by State and calculate the total sales and profit
state_sales_profit = df.groupby('State').agg({'Sales': 'sum', 'Profit': 'sum'}).reset_index()

# Create the bar graph using Plotly
fig = px.bar(state_sales_profit, x='State', y=['Sales', 'Profit'], barmode='group',
             labels={'State': 'State', 'value': 'Amount'},
             title='Total Sales and Profit by State')

# Show the plot
fig.show()
The above charts Display

Bar graph representation of Total Sales and Profit by State
# Calculate sales and profit by city
city_performance = df.groupby('City').agg({'Sales': 'sum', 'Profit': 'sum'}).reset_index()

# Sort cities by sales in descending order
city_performance = city_performance.sort_values(by='Sales', ascending=False)

# Plot sales and profit by city
fig = px.bar(city_performance, x='City', y=['Sales', 'Profit'], title='Performance Comparison by City')
fig.update_layout(barmode='group')
fig.show()
The above charts Display

Performance comparison ( Sales vs Profit ) by City
Findings:

The above visual explains that

The Top 3 performing cities in sales and prfit are New york , Los angeles and Seattle.
The Bottom 3 Non-Performing cities are San louis obi, Billings , New Brunswick.
# Calculate overall sales and profit
overall_sales = df['Sales'].sum()
overall_profit = df['Profit'].sum()

# Group by 'City', 'State', and 'Region' and calculate individual sales and profit for each group
grouped_data = df.groupby(['City', 'State', 'Region']).agg({'Sales': 'sum', 'Profit': 'sum'}).reset_index()

# Calculate individual sales percentage
grouped_data['Sales Percentage'] = (grouped_data['Sales'] / overall_sales) * 100

# Calculate individual profit percentage
grouped_data['Profit Percentage'] = (grouped_data['Profit'] / overall_profit) * 100

# Sort the data by profit in descending order
grouped_data = grouped_data.sort_values(by='Profit', ascending=False)

# Display the results
print("Overall Sales: ${:,.2f}".format(overall_sales))
print("Overall Profit: ${:,.2f}".format(overall_profit))
print("\nIndividual Sales and Profit Percentage by City, State, and Region (Sorted by Profit Descending):")
print(grouped_data)
Overall Sales: $2,297,200.86
Overall Profit: $286,397.79

Individual Sales and Profit Percentage by City, State, and Region (Sorted by Profit Descending):
              City         State   Region        Sales    Profit  \
380  New York City      New York     East  256368.1610  62037.08   
312    Los Angeles    California     West  175851.3410  30440.94   
517        Seattle    Washington     West  119540.7420  29156.13   
503  San Francisco    California     West  112669.0920  17507.39   
143        Detroit      Michigan  Central   42446.9440  13181.79   
..             ...           ...      ...          ...       ...   
90         Chicago      Illinois  Central   48539.5410  -6654.55   
283      Lancaster          Ohio     East    8202.6250  -7149.63   
499    San Antonio         Texas  Central   21843.5280  -7299.06   
239        Houston         Texas  Central   64504.7604 -10153.48   
430   Philadelphia  Pennsylvania     East  109077.0130 -13837.83   

     Sales Percentage  Profit Percentage  
380         11.160024          21.661159  
312          7.655027          10.628902  
517          5.203757          10.180292  
503          4.904625           6.112963  
143          1.847768           4.602616  
..                ...                ...  
90           2.112986          -2.323534  
283          0.357070          -2.496398  
499          0.950876          -2.548574  
239          2.807972          -3.545237  
430          4.748258          -4.831682  

[604 rows x 7 columns]
#plotting Heatmap distribution for category and region
sns.heatmap(pd.crosstab(df['Category'],df['Region']))
<Axes: xlabel='Region', ylabel='Category'>

# Select the numerical columns for correlation analysis
numerical_cols = ['Sales', 'Profit', 'Quantity', 'Discount']

# Calculate the correlation matrix
correlation_matrix = df[numerical_cols].corr()

# Create a correlation heatmap using Plotly
fig = px.imshow(correlation_matrix,
                labels=dict(x="Variables", y="Variables", color="Correlation"),
                x=numerical_cols,
                y=numerical_cols,
                color_continuous_scale='RdBu',
                title="Correlation Heatmap")

# Display the plot
fig.show()
The above charts Display

Graphical representation of co-relation b/w columns
Findings:

The above visual explains that

there is no Co-Relation b/w Sales,Profit,Quantity.

Negative co-relation b/w profit and discount

sales_profit_by_segment = df.groupby('Segment').agg({'Sales': 'sum', 'Profit': 'sum'}).reset_index()

color_palette = colors.qualitative.Pastel

fig = go.Figure()
fig.add_trace(go.Bar(x=sales_profit_by_segment['Segment'], 
                     y=sales_profit_by_segment['Sales'], 
                     name='Sales',
                     marker_color=color_palette[0]))
fig.add_trace(go.Bar(x=sales_profit_by_segment['Segment'], 
                     y=sales_profit_by_segment['Profit'], 
                     name='Profit',
                     marker_color=color_palette[1]))

fig.update_layout(title='Sales and Profit Analysis by Customer Segment',
                  xaxis_title='Customer Segment', yaxis_title='Amount')

fig.show()
The above charts Display

Bar graph representation of Total Sales vs Profit by Customer Segment
sales_profit_by_segment = df.groupby('Category').agg({'Sales': 'sum', 'Profit': 'sum'}).reset_index()

color_palette = colors.qualitative.Pastel

fig = go.Figure()
fig.add_trace(go.Bar(x=sales_profit_by_segment['Category'], 
                     y=sales_profit_by_segment['Sales'], 
                     name='Sales',
                     marker_color=color_palette[0]))
fig.add_trace(go.Bar(x=sales_profit_by_segment['Category'], 
                     y=sales_profit_by_segment['Profit'], 
                     name='Profit',
                     marker_color=color_palette[1]))

fig.update_layout(title='Sales and Profit Analysis by Category',
                  xaxis_title='Category', yaxis_title='Amount')

fig.show()
The above charts Display

Bar graph representation of Total Sales vs Profit by Category
sales_profit_by_segment = df.groupby('Sub-Category').agg({'Sales': 'sum', 'Profit': 'sum'}).reset_index()

color_palette = colors.qualitative.Pastel

fig = go.Figure()
fig.add_trace(go.Bar(x=sales_profit_by_segment['Sub-Category'], 
                     y=sales_profit_by_segment['Sales'], 
                     name='Sales',
                     marker_color=color_palette[0]))
fig.add_trace(go.Bar(x=sales_profit_by_segment['Sub-Category'], 
                     y=sales_profit_by_segment['Profit'], 
                     name='Profit',
                     marker_color=color_palette[1]))

fig.update_layout(title='Sales v/s Profit Analysis by Sub-Category',
                  xaxis_title='Sub-Category', yaxis_title='Amount')

fig.show()
The above charts Display

Bar graph representation of Total Sales vs Profit by Sub-Category
# Group by 'Region', 'Category', and calculate total sales and profit for each region-category combination
region_category_performance = df.groupby(['Region', 'Category'])[['Sales', 'Profit']].sum().reset_index()

# Get unique regions and categories
regions = df['Region'].unique()
categories = df['Category'].unique()

# Create empty matrices to store sales and profit data
sales_data = np.zeros((len(regions), len(categories)))
profit_data = np.zeros((len(regions), len(categories)))

# Fill the matrices with sales and profit data based on region and category
for idx, region in enumerate(regions):
    for jdx, category in enumerate(categories):
        sales = region_category_performance.loc[(region_category_performance['Region'] == region) & 
                                                (region_category_performance['Category'] == category), 'Sales'].values
        profit = region_category_performance.loc[(region_category_performance['Region'] == region) & 
                                                 (region_category_performance['Category'] == category), 'Profit'].values
        sales_data[idx, jdx] = sales[0] if sales else 0
        profit_data[idx, jdx] = profit[0] if profit else 0

# Create the heatmap using Matplotlib
fig, axes = plt.subplots(1, 2, figsize=(15, 6))

# Sales Heatmap
sales_heatmap = axes[0].imshow(sales_data, cmap='YlGnBu', interpolation='nearest', aspect='auto')
axes[0].set_xticks(np.arange(len(categories)))
axes[0].set_yticks(np.arange(len(regions)))
axes[0].set_xticklabels(categories, rotation=45, ha='right')
axes[0].set_yticklabels(regions)
axes[0].set_xlabel('Category')
axes[0].set_ylabel('Region')
axes[0].set_title('Sales Heatmap by Region and Category')
for i in range(len(regions)):
    for j in range(len(categories)):
        axes[0].text(j, i, f"{int(sales_data[i, j]):,}", ha='center', va='center', color='w')

# Add colorbar for sales heatmap
cbar_sales = plt.colorbar(sales_heatmap, ax=axes[0], shrink=0.6)
cbar_sales.ax.set_ylabel('Sales')

# Profit Heatmap
profit_heatmap = axes[1].imshow(profit_data, cmap='YlGnBu', interpolation='nearest', aspect='auto')
axes[1].set_xticks(np.arange(len(categories)))
axes[1].set_yticks(np.arange(len(regions)))
axes[1].set_xticklabels(categories, rotation=45, ha='right')
axes[1].set_yticklabels([])
axes[1].set_xlabel('Category')
axes[1].set_title('Profit Heatmap by Region and Category')
for i in range(len(regions)):
    for j in range(len(categories)):
        axes[1].text(j, i, f"{int(profit_data[i, j]):,}", ha='center', va='center', color='w')

# Add colorbar for profit heatmap
cbar_profit = plt.colorbar(profit_heatmap, ax=axes[1], shrink=0.6)
cbar_profit.ax.set_ylabel('Profit')

plt.tight_layout()
plt.show()

# Group by Region, Category, and Sub-Category, and calculate the total sales and profit
region_category_subcategory_performance = df.groupby(['Region', 'Category', 'Sub-Category']).agg({'Sales': 'sum', 'Profit': 'sum'}).reset_index()

# An Interactive sun burst chart to look at Sales and Profit by Region, Category & Sub-Category
fig = px.sunburst(region_category_subcategory_performance, path=['Region', 'Category', 'Sub-Category'],
                  values='Sales', color='Profit', title='Sales and Profit by Region, Category, and Sub-Category')
fig.show()
The above charts Displays

An Interactive sun burst chart to look at Sales and Profit by Region > Category > Sub-Category
import pandas as pd
import plotly.express as px

# Assuming you have your dataset loaded into a pandas DataFrame called 'df'

# Group by Category and Sub-Category, and calculate the total sales or profit
category_subcategory_performance = df.groupby(['Category', 'Sub-Category']).agg({'Sales': 'sum', 'Profit': 'sum'}).reset_index()

# Treemap
fig = px.treemap(category_subcategory_performance, path=['Category', 'Sub-Category'],
                 values='Sales', color='Profit', title='Sales and Profit by Category and Sub-Category')
fig.show()
The above charts Displays

An Interactive Tree Map to explore Sales and Profit by only Category & Sub-Category in detail
7. Statistical analysis
# Descriptive statistics
statistics = df[['Sales', 'Quantity', 'Discount', 'Profit']].describe()
print(statistics)

# Box plots
sns.boxplot(data=df[['Sales', 'Quantity', 'Discount', 'Profit']])
              Sales     Quantity     Discount       Profit
count   9994.000000  9994.000000  9994.000000  9994.000000
mean     229.858001     3.789574     0.156203    28.656973
std      623.245101     2.225110     0.206452   234.260203
min        0.444000     1.000000     0.000000 -6599.980000
25%       17.280000     2.000000     0.000000     1.730000
50%       54.490000     3.000000     0.200000     8.665000
75%      209.940000     5.000000     0.200000    29.360000
max    22638.480000    14.000000     0.800000  8399.980000
<Axes: >

8. Conclusions
Profit in South and Central region is Less when compared to East and West Regions.

Highest Profit Contribution is from Copiers

Tables has negative profits

Supplies has very less profits

Technology Segment has more Profitability

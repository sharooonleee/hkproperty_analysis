# Exploratory Data Analysis of Hong Kong Private Housing Market (2020.04-2023.02)

## Project Objective
As a HK property market newbie, this project is aimed at having a brief understanding of the Hong Kong property market and getting insightful investment recommendations. 

## Dataset Description
We use the dataset on Kaggle which is scraped from Centaline Property Hong Kong, one of the largest local real estate agencies. It has 159,676 property transaction records during 10/03/2020 to 11/03/2023, showing the detailed information on the date of the transaction, the property address, floor, saleable area etc. The dataset covers a period of time spanning several years, allowing for analysis of trends and changes in the Hong Kong housing market.

## Data Cleaning and Preprocessing
After identifying the data type of variable, we then match it with the current dataset. We found column “date” and “seleable_area(ft^2)” are stored as incorrect type - “Object”. Besides correcting “selable_area(ft^2) to numeric and “date” to datetime, we also added 2 more columns of “month_year” and “quarter_year” for higher level analysis.  We then check the null of each column. It is found that “Tower”, “Flat”, “Phase” and “Block” have more then 50% null, and the column “change” have 60% value equal 0. As those columns are not the key elements for the analysis, we decided to drop them off from our dataframe. Considering the data of 2020 Mar and 2023 March are not complete, we excluded it  from our analysis. Also, the size of public houses is too little, 1,554 out of 159,676, so we decided to focus on private property only and exclude public housing.Too many distinct values of a variable sometimes is hard for delivering insight. We regroup 18 districts to 4 regions and “seable_are(ft^2)” to 3 flat sizes. For the details, please refer to the coding file.
![image](https://github.com/user-attachments/assets/6b66357b-1543-4b8e-9613-2d456011593a)
![image](https://github.com/user-attachments/assets/bfe84b32-0acf-40a0-ad1e-2740e1b1f393)

## Analysis and Findings
### Current Market Trend and Unit Rate Distribution
In the HK private property market, it experienced a downturn during 2020 due to the lockdown of COVID-19. It was gradually recovering from January 2021. Then, the US interest rate hike gave a big hit to the market which shows a significant drop in the 1st quarter of 2022. However, a significant spike in May 2022 indicates a potential market recovery or impact of policy changes. Another point worth noting is the fast growing rental property, it might be related to the policy impact.
![image](https://github.com/user-attachments/assets/eb93d379-6cb6-4cbb-9472-f50f1976ff20)

For the unit rate distribution, we separately analyze rental property and sold property. The unit rate distribution of the rental property market shows a bell shaped, most transactions occur between approximately 30 and 50 HKD per square foot. But in the sold market, the right-skewed shape indicates that there are few transactions at extremely high prices when the mean of unit rate is at 16,449.64.
![image](https://github.com/user-attachments/assets/8c5cf7cc-e5cf-4b07-82f9-5e1150e83e36)

### Trend and unit rate distribution of different Property Size

To better understand the market trend and unit rate distribution on different aspects, we deep dive it to flat size level and location level. 

Since flat size has too many distinct variables, we divided property sizes into 3 categories for easy understanding: Less than 500 sq. ft. is “Small Property”, between  500 and 1000 sq. ft. is “Medium Property”, and greater than 1000 sq. ft.. The stacked bar plots below are showing their variation of transaction number  over time. Both rental and sold markets had a significant increase in transactions during Q1 of 2022. For sold properties, small properties have largest transactions, whereas for rental properties,both small and medium properties have high demand. Small properties have highest demand in both the selling and rental market. Medium properties are more popular in the rental market than the selling market.
![image](https://github.com/user-attachments/assets/601e3eb7-23d0-4306-b6ec-1449069f1975)
![image](https://github.com/user-attachments/assets/62d57f10-3d0e-4408-aa7c-7c968aa8a38c)
Box plots below help in investigating the spreading of unit rate in different flat sizes. For the sold property market, the unit rate shows a heavy-tailed distribution, indicating that the unit rate has a lot of extreme value, especially in large property. The box width of Both small and medium properties are narrower than large properties, they have less variability and more focus. Small property has a slightly higher selling price per sq. ft. than medium property. The same situation also happens on the rental market, but the outlier in the rental market is far lesser than the sold property market, suggesting that the rental market is relatively more controlled or less volatile compared to the sold market. 

Insights:
Small property unit rates are stable for sold properties, but have a large variance in rental market, more probable to gain high rental yield , which is good for investors who buy properties for rental profit.
Medium properties unit rate are stable for both sold and rental properties, which is good for conservative investors.
![image](https://github.com/user-attachments/assets/3db344d7-448e-405f-ab28-9da0a534d62b)
![image](https://github.com/user-attachments/assets/4b9b3313-46ce-4441-9eb8-c3bca42f3e38)

### Trend and unit rate distribution on location level
It is hard to understand the trend of unit rate in different locations if we only use distinct to show on the chart, so we group them to 4 bigger regions: Hong Kong, Kowloon, New Territories East, and New Territories West.

It is observed that the unit rate of both rental and sold property markets are gradually going down. Although there is a slight rise from Dec 2022 to Feb 2023, the overall unit rate could not go back to the same level of 2020, showing that the price of property is relatively cheaper. The rental market is more stable, while the sold market experienced more fluctuation. NT West’s properties are the cheapest and comparatively stable then the others. NT East’s properties are rising while HK’s and KLN’s properties are declining. 

![image](https://github.com/user-attachments/assets/76f3ffb1-89ac-4fdb-87da-565306dc8819)
![image](https://github.com/user-attachments/assets/bc446ced-8a2c-4dfb-bf6f-aedd2a797a9e)

After knowing the higher level of the trend of unit rate changing in different locations, we would like to look into the details of the district. Stacked bar plot is plotted to see variation of transaction volume of properties in different districts against time. For both sold properties and rental properties, a consistent demand is observed in Central and western, HK island southern, eastern districts and Wan Chai district. Higher transaction volumes are observed in districts like Kowloon city, Kwun Tong, Sham Shui Po, Wong Tai Sin and East North District. This may be due to the supply of new properties for selling and renting.

![image](https://github.com/user-attachments/assets/872bc8ff-c40a-44be-adba-edfd586e6a12)
![image](https://github.com/user-attachments/assets/0870e655-3c99-430a-aa91-e0b1b0d2b375)

### Challenges and Limitations

The dataset spans from April 2020 to February 2023, which is only three years, with 2020 and 2023 not being complete years. This time frame is not long enough to provide accurate predictions. Additionally, the dataset lacks breadth, as it does not include enough detailed property information beyond the address. For more accurate predictions, it would be beneficial to add GPS coordinates and more detailed property data, such as estate names, building years, and property types like houses or apartments.

Another issue is data accuracy. There are some inaccuracies in the district column, with errors such as properties being listed in incorrect districts. For example, the same property name “Overbays” appears in different districts. Correcting these inaccuracies is essential for reliable analysis and predictions.

### Conclusion

Despite the overall property market facing challenges such as declining property prices and transaction volumes, the rental market has remained robust. This indicates a strong underlying demand for rental housing. From 2020 to early 2023, the rental volume has shown a significant upward trend, suggesting a growing demand for rental properties in Hong Kong during this period. Smaller properties, particularly those less than 500 square feet, have demonstrated high rental yields, making them attractive to investors looking for rental income. For those seeking high returns from short-term investments, considering properties in the Central and Western Districts may be beneficial. On the other hand, for long-term investments, properties in the Yau Tsim Mong District or the New Territories could provide relatively stable income.

### Reference
https://www.kaggle.com/datasets/cyrusttf/hong-kong-housing-price-2020-2023/data





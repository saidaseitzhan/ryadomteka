#  Ryadomteka
Ryadomteka - your health is most valuable!
- Front-end: Vue.js
- Backend: Django(DRF) without ORM
- DB: Oracle (18c)

## Introduction 
The whole world is now in the state of a global pandemic. People were afraid of the opportunity to freely move and independently  decide their actions. Not a single sick person will go out individually to get the pharmacy and purchase his own medicine, without help. It is possible to save energy and health if there will be a system that helps in choosing medicines and not only in choosing, but also in ordering and on delivery to home. Tragically, there's no such framework in Kazakhstan to illuminate this issue. In addition, even if they do exist, they do not give you complete control with information.

For this situation we provide a web site that will make life easier for almost everyone, regardless of age and we believe that this system will have a huge weighty role in the life of every citizen of Kazakhstan. The system is based on pharmacy and medicine data in Kazakhstan.

**The whole functionality is of our site:**

1) *To provide the necessary information about medicine.*
2) *To deliver medicines at home.*
3) *To find the nearest pharmacy.*
4) *To give full statistics about Covid-19 state.*
5) *Daily news about the situation in the whole world.*


## Data mining
We used different libraries in advanced Python programming languages to collect data. The requests and BeautifulSoup libraries were used to obtain information, and we used the pandas, also numpy libraries to filter and classify our data. And so is the software for filtering "Jupyter Lab". It should be mentioned that we needed all the pharmacy data (location, name, phone number) as well as all the drug data (name, expiration date, category, description, etc.) 
Sites where we found our data are: 
- https://i-teka.kz/
- https://darihana.com/
- https://data.egov.kz/datasets/view?index=gosudarstvenniy_reestr_lekarst
- https://informburo.kz/tags/meditsina
- https://www.kaggle.com/antgoldbloom/covid19-data-from-john-hopkins-university

These sites did not have the necessary information. Therefore, it was decided to generate the missing part based on the parsed data.
## Tables structures
1. Drugs (5273)      
	- ID 
	- DESCRIPTION 
	- IMAGE 
	- QUANTITY 
	- PRICE 
	- CLASSIFICATION 
	- PRODUCER 
	- ATC_CLASSIFICATION 
	- REG_ID 
	- RECIPE 
	- FORM_DRUG 
	- COUNTRY_ID 
	- NAME 
	- CATEGORY_ID
	-  STORE_ID

2. Pharmacy (5887)        
	- ID 
	- NAME 
	- ADDRESS
	-  LONGITUDE 
	- LATITUDE 
	- PHONE 
	- WORK_TIME_WEEKDAYS 
	- WORK_TIME_SAT 
	- WORK_TIME_SUN 
	- CITY_ID

3. Cities (30)          
	- ID 
	- NAME
	-  LONGITUDE
	-  LATITUDE
4. DRUG_CATEGORIES (237)      
	- ID 
	- NAME 
5. USERS (6667)             
	- ID 
	- NAME 
	- SURNAME 
	- PASSWORD 
	- EMAIL 
	- USERNAME 
	- DATE_JOINED 
	- PHONE_NUMBER 
	- CITY_ID 
6. BOUGHT_DRUGS
	-  ID 
	- USER_ID 
	- DRUG_ID 	
	- BUY_DATE 
	- QUANTITY

7. NEWS (every day updating)              
	- ID 
	- TITLE
	- VIEWS_COUNT 
	- HTML_TEXT 
	- PREVIEW_IMAGE 
8. COUNTRY(274)            
	-  ID 
	- NAME 
	- LAT 
	- LONG
9. COVID_STATISTICS(109 000)    
	- ID 
	- COUNTRY_ID
	- DATE 
	- CASES 


## Database constraints

Foreign keys:
- DRUGS.COUNTRY_ID ==> COUNTRY.ID
- STORES.city_id ==> CITIES.id
-  USERS.city_id ==> CITIES.id
- DRUGS.store_id ==> STORES.id
- BOUGHT_DRUGS.DRUG_ID ==> DRUGS.ID
- BOUGHT_DRUGS.USER_ID ==> USERS.ID

Primary keys:
- All id fields in tables


## Questions related project

1. Show users who can buy medicine N in city X.
2. Show total number of drugs in category X available in pharmacy N.
3. Price of medicine X which is located in city N.
4. Time Schedule on Sunday of all pharmacies that have the medicine X.
5. Print all descriptions of drugs in the city N in the pharmacy X.
6. Print the number of new cases of infection on day X in country N.
7. Display information about recovered people in country X in the days between A and B.
8. Display users who bought a medicine according to description X in city Y and pharmacy Z.
9. Display the number of medicines produced in country X that can be bought at a pharmacy Y in city Z.
10. Withdraw cities in which there are more than 5 drugs, the cost of which is not more than 4000tg in the X pharmacy from category Y that were not purchased at all.
11. Find pharmacies in city X that have medicines over 1000 and available without a prescription from category Y and have been purchased more than 10 times.
12. The number of medicines purchased on X day, with a total amount of more than 10,000 tenge in the city of Y and the category in which the most medicines were purchased, the price of which is less than 1,000, whose name began with A.
13. Withdraw pharmacies with the highest amount of income that users who registered no more than 7 days ago, in category Y in city X, where the form of release of drugs is "Таблетки, покрытые оболочкой". 
14. Display the most profitable day of a pharmacy located in city X, in which there are fewer drugs than in the rest. 
15. Find a pharmacy that sells medicines produced in country X and which are open until 20:00 in city Y.

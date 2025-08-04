# British_Airline_Sentiment_Analysis

### Description 
Analyze customer sentiment and satisfaction patterns in airline reviews through automated data collection and sentiment analysis techniques.

### Business Introduction
British Airways plc (BA) is the flag carrier of the United Kingdom, headquartered in London near its main hub at Heathrow Airport, formed in April 1974 through the merger of British Overseas Airways Corporation (BOAC) and British European Airways (BEA). The company primarily operates international and domestic air travel services, offering passenger and cargo transportation, aircraft maintenance, ground handling services, and holiday packages, while being associated with the oneworld alliance to enhance its worldwide reach. As a global airline with over 100 years of heritage, British Airways connects people, places and diverse cultures across an extensive network spanning Europe, the Americas, Africa, Asia and Australia

### Business Problem Statement
British Airways, as the UK's flag carrier operating extensive international and domestic routes through its Heathrow hub, faces the challenge of monitoring customer satisfaction across its vast network while competing in an increasingly demanding aviation market. With thousands of passenger reviews generated daily across multiple platforms, BA lacks the systematic capability to analyze this critical feedback at scale, missing opportunities to identify service gaps, route-specific issues, and emerging customer concerns that could impact its premium brand reputation and market position. This inability to harness customer sentiment data effectively puts the airline at a competitive disadvantage, preventing proactive service improvements and limiting its ability to maintain the high service standards expected from a global flag carrier with over 100 years of aviation heritage.

### Data Acquisition
Reviews were scraped from https://www.airlinequality.com/airline-reviews/turkish-airlines/ using requests and BeautifulSoup:

- Fetched HTML with requests.get.
- Parsed content with BeautifulSoup.
- Extracted 100 reviews, including Message (from div.text_content) and metadata (from div.review-stats).
- Saved data as {British_airlines_reviews_data.csv} using pandas.

### Why Only 100 Reviews?
- Testing purposes, as proceed = False stops after one page.
- Website limitations (e.g., rate limits, pagination restrictions).
- Time or computational constraints for initial analysis.

### Dataset Description
The dataset contains:
    Message: Review text, often with verification prefix (e.g., ``Trip Verified'').
    Type of Traveller: Family Leisure, Couple Leisure, Solo Leisure, or Business.
    Seat Type: Economy, Business, or Premium Economy.
    Route: Flight origin, destination, and layovers (e.g., ``Istanbul to South Africa via Kayseri'').
    Date Flown: Month and year (e.g., ``September 2024'').
    Recommended: ``Yes'' or ``no'' recommendation.
    Aircraft: Aircraft model (71\% missing).

### Data Quality
    Missing values: 1 in Route, 71 in Aircraft.
    No duplicates.
    Message required cleaning to remove emojis, special characters, and standardize case.

### Methodology
Analysis was performed in a Jupyter Notebook using Python.

### Data Loading
- Loaded with {pandas.read_csv}.
- Inspected using head() and info().
- Verified missing values isnull().sum() and duplicates duplicated().sum().

### Text Cleaning
A clean_text function using re:
- Removed emojis (e.g., ✅), pipes (``|''), and special characters.
- Retained alphabetic characters and spaces.
- Converted to lowercase and trimmed whitespace.
Stored in cleaned_message.

### Sentiment Analysis
Assumed steps:
Applied VADER to compute sentiment scores for cleaned_message,extracted Year-Month from Date Flown.Generated compound scores (-1 to 1).

#### Reasons for choosing VADER
VADER is specifically designed to handle social media text, including slang, acronyms and emotions, making it well suited for analyzing sentiment.

### Findings
#### Worst Sentiment:

- Routes: All routes have predominantly negative reviews (90% "no"). Specific routes like Istanbul to South Africa via Kayseri, London to Lahore via Istanbul, and Istanbul to Toronto show consistent complaints (e.g., delays, cancellations).
- Seat Types: Economy Class (24/30 reviews, 22 "no") has the worst sentiment, followed by Business Class (3/30, 2 "no") and Premium Economy (1/30, 1 "no").
- Traveler Types: Family Leisure (13/30, all "no") and Couple Leisure (5/30, all "no") show the worst sentiment. Solo Leisure (7/30, 2 "yes") has slightly better sentiment.

#### Best Sentiment:

- Routes: Detroit to Bangkok (1 review, "yes") and Guangzhou to Nuremberg via Istanbul (1 review, "yes") are positive outliers.
- Seat Types: Business Class has one positive review (Geneva to Kuala Lumpur via Istanbul).
- Traveler Types: Solo Leisure has 2/7 positive reviews, the highest proportion.

### Business Impact Analysis
- Improve Service Reliability: Address frequent complaints about delays and cancellations (e.g., Kuala Lumpur to Düsseldorf, Istanbul to Toronto) by optimizing scheduling and communication.
- Enhance Family/Couple Experience: Family Leisure (13/13 negative) and Couple Leisure (5/5 negative) show poor sentiment. Offer family-friendly amenities or couple packages.
- Business Class Focus: One positive Business Class review suggests potential; invest in consistent premium service.
- Customer Service Training: Complaints about staff (e.g., check-in issues in Guangzhou) indicate a need for better training.

### Why British_Airline Should Considerations

- Cost Savings: Reducing delays/cancellations lowers compensation costs (e.g., EU261 claims).
- Revenue Improvement: Positive sentiment in Solo Leisure and Business Class could attract high-value customers, increasing ticket sales.
- Brand Reputation: Proactive issue resolution enhances Turkish Airlines' global image, potentially boosting market share.

### N.B
This project only required that i use a power point slides to report my findings.

### Conclusion
The project provides a framework for sentiment analysis via web scraping, text cleaning, and visualization. Future work
- Implement explicit VADER analysis.
- Analyze by Type of Traveller or Seat Type.
- Handle missing Aircraft data.
- Apply topic modeling for themes.

### Dependencies
- pandas: Data manipulation.
- numpy: Numerical operations.
- seaborn, matplotlib: Visualization.
- re: Text cleaning.
- requests ,BeautifulSoup: Web scraping.


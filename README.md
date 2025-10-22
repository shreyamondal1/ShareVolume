# ShareVolume

## Overview
ShareVolume is a single-page web application that analyzes and displays Common Stock Shares Outstanding data from SEC EDGAR filings. The application fetches data from the SEC's XBRL API, processes it to find maximum and minimum share values for fiscal years after 2020, and presents the information in a visually appealing dashboard.

## Features
- **Real-time SEC Data Fetching**: Retrieves live data from SEC EDGAR API
- **Dynamic Company Lookup**: Search any company by CIK number
- **Query Parameter Support**: Load different companies via URL parameters (e.g., `?CIK=0001018724`)
- **Responsive Design**: Beautiful, mobile-friendly interface with gradient backgrounds
- **Data Visualization**: Clear presentation of maximum and minimum share values
- **Error Handling**: Robust error handling with user-friendly messages
- **No Server Required**: Fully client-side application that works on GitHub Pages

## Setup Instructions
1. Clone the repository
2. Open `index.html` in a web browser
3. The application runs entirely client-side - no build process or server required

## Usage

### Default View
Simply open `index.html` to view Cigna's shares outstanding data (loaded from `data.json`).

### Search by CIK
1. Enter a 10-digit CIK number in the search box
2. Click "Fetch Data" or press Enter
3. The page will update with the new company's data without reloading

### Query Parameter
Access any company directly via URL:

index.html?CIK=0001018724


## Code Explanation

### Data Processing
The application fetches data from the SEC API endpoint:

https://data.sec.gov/api/xbrl/companyconcept/CIK{number}/dei/EntityCommonStockSharesOutstanding.json


It then:
1. Filters entries where `fy > "2020"` and `val` is numeric
2. Finds the maximum and minimum values
3. Updates the DOM with formatted results

### CORS Handling
To avoid CORS issues with the SEC API, the application uses the AllOrigins proxy service for dynamic lookups while maintaining a fallback to the local `data.json` file.

### Dynamic Updates
All content updates happen via JavaScript DOM manipulation:
- Entity name in title and H1
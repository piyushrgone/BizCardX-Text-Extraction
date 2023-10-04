# BizCardX-Text-Extraction

### BizCardX - Text Extraction Using Easy OCR

BizCardX is a Streamlit web application designed to effortlessly extract data from business cards using Optical Character Recognition (OCR) technology. With BizCardX, users can easily upload images of business cards, and the application leverages the powerful easyOCR library to extract pertinent information from the cards. The extracted data is then presented in a user-friendly format and can be stored in a SQL database for future reference and management.

**Features:**

* Extract essential information from business cards, including:
    * Company name
    * Card holder's name
    * Designation
    * Mobile number
    * Email address
    * Website URL
    * Area
    * City
    * State
    * Pin code
    * Image of the card
* Store the extracted data in a SQL database
* Alter/delete the data stored in the database at any time

**Pre-requisites:**

* Python environment (Python 3.x recommended)
* Necessary libraries installed: Streamlit, Pandas, easyOCR, PIL, cv2, matplotlib, re, sqlite3

**Usage:**

1. Clone the BizCardX repository from GitHub:

```
git clone https://github.com/piyushrgone/BizCardX-Text-Extraction.git
```

2. Install the required Python libraries:

```
pip install -r requirements.txt
```

3. Run the BizCardX web application:

```
streamlit run app.py
```

4. Upload an image of a business card to the application.

5. The application will extract the relevant information from the business card and present it in a user-friendly format.

6. You can then choose to store the extracted data in a SQL database.

**Example:**

The following example shows how to extract the information from a business card image:

```python
import easyocr

# Initialize the easyOCR library
reader = easyocr.Reader(['en'])

# Read the business card image
image = cv2.imread('business_card.jpg')

# Extract the text from the image
result = reader.readtext(image)

# Print the extracted text
for (bbox, text, prob) in result:
    print(text)
```

**Database:**

To store the extracted data in a SQL database, you can use the following steps:

1. Create a new database file:

```
sqlite3 business_cards.db
```

2. Create a new table in the database to store the business card information:

```sql
CREATE TABLE business_cards (
    company_name TEXT,
    card_holder_name TEXT,
    designation TEXT,
    mobile_number TEXT,
    email TEXT,
    website_url TEXT,
    area TEXT,
    city TEXT,
    state TEXT,
    pin_code TEXT,
    image BLOB
);
```

3. Insert the extracted data into the database:

```python
import sqlite3

# Connect to the database
conn = sqlite3.connect('business_cards.db')

# Create a cursor
cursor = conn.cursor()

# Insert the extracted data into the database
for row in result:
    cursor.execute('INSERT INTO business_cards (company_name, card_holder_name, designation, mobile_number, email, website_url, area, city, state, pin_code, image) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?)', row)

# Commit the changes
conn.commit()

# Close the database connection
conn.close()
```

You can then retrieve the data from the database using the following query:

```sql
SELECT * FROM business_cards;
```

**Conclusion:**

BizCardX is a powerful and easy-to-use tool for extracting text from business cards. With BizCardX, you can easily store the extracted data in a SQL database for future reference and management.
# Web Scraping - Task 05 (Prodigy Infotech Internship)
# Scrape data from books.toscrape.com and store it in a CSV

import requests
from bs4 import BeautifulSoup
import csv

def scrape_books(pages=5):
    # CSV file to store data
    with open("books.csv", mode="w", newline='', encoding="utf-8") as file:
        writer = csv.writer(file)
        writer.writerow(["Title", "Price", "Rating"])  # CSV Header

        # Loop through pages
        for page in range(1, pages + 1):
            print(f"Scraping page {page}...")
            url = f"https://books.toscrape.com/catalogue/page-{page}.html"
            response = requests.get(url)
            soup = BeautifulSoup(response.text, "html.parser")

            books = soup.find_all("article", class_="product_pod")

            for book in books:
                # Extract title
                title = book.h3.a["title"]

                # Extract price
                price = book.find("p", class_="price_color").text

                # Extract rating from class attribute
                rating_class = book.p["class"]
                rating = rating_class[1] if len(rating_class) > 1 else "Not Rated"

                # Write to CSV
                writer.writerow([title, price, rating])

    print("✅ Scraping completed! Data saved to 'books.csv'")

# Call the function
if __name__ == "__main__":
    scrape_books()

# Image Scraping Web Application with Flask

This project involves creating a web application using Flask to scrape images from a Google Image search and store the image data in a MongoDB database. The web application provides a simple user interface for entering search queries and fetching corresponding images.

## Getting Started

To run this project, you'll need to have Python and Flask installed on your system. Additionally, you need to install the required libraries. You can install them using the following command:
```bash
pip install Flask flask-cors requests beautifulsoup4 pymongo
```
## Project Structure

The project consists of the following components:

- app.py: The main Flask application script containing the web app code.
- templates/: A directory containing HTML templates for rendering the web pages.
- images/: A directory to store the downloaded images.
- scrapper.log: A log file to store logging information.
- README.md: This README file to provide project documentation.

## How it Works
1. Import the necessary libraries and modules:
```sh
from flask import Flask, render_template, request, jsonify
from flask_cors import CORS, cross_origin
import requests
from bs4 import BeautifulSoup
import pymongo
import os
import logging
```

2. Set up the Flask application:
```sh
app = Flask(__name__)
```
3. Create routes for the web application:

* '/': Render the homepage template.
```sh
@app.route("/", methods=['GET'])
def homepage():
    return render_template("index.html")
```
* '/review': Handle POST requests, scrape images, and store in MongoDB.
```sh
@app.route("/review", methods=['POST', 'GET'])
def index():
    if request.method == 'POST':
        try:
            # Code for scraping images, downloading, and storing in MongoDB
            # ...
            return "Images loaded and stored in MongoDB"
        except Exception as e:
            logging.info(e)
            return 'Something went wrong'
    else:
        return render_template('index.html')
```
4. Create the necessary directories and set up user agent and other parameters for the scraping process.
5. Send a request to Google Image search, parse the response using BeautifulSoup, and extract image URLs.
6. Download each image, save it to the specified directory, and create a list of image data dictionaries.
7. Connect to the MongoDB database, insert the image data, and store it in the image_scrap_data collection.
8. Run the Flask app:
```sh
if __name__ == "__main__":
    app.run(host='0.0.0.0', port=8000)
```

## Usage
1. Clone the repository:
```bash
git clone https://github.com/your-username/image-scraping-webapp.git
cd image-scraping-webapp
```
2. Run the Flask app:
```bash
python app.py
```
3. Access the web application by opening a web browser and navigating to http://localhost:8000.
4. Enter a search query in the input field, submit the form, and the app will scrape and store the images in MongoDB.

## Note

- Modify the headers dictionary to use an appropriate user agent to avoid getting blocked by Google.
- Be cautious while scraping websites and follow their terms of use and scraping policies.

## Contributing

Contributions are welcome! If you have improvements or suggestions, feel free to submit a pull request.

## License
This project is licensed under the MIT License - see the LICENSE file for details.


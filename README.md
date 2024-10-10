 # Twitter API Interaction in Go

## Introduction
This Go application demonstrates how to interact with the Twitter API using OAuth1 authentication. The program allows users to post a tweet and subsequently delete it after a specified time. This project aims to provide practical experience with making RESTful API calls, handling JSON data, and using environment variables for sensitive credentials.

## Setup Instructions

### 1. Create a Twitter Developer Account
To begin, you need a Twitter Developer account. Follow these steps:
1. Go to the [Twitter Developer Platform](https://developer.twitter.com/en).
2. Click on "Apply" to create a new developer account.
3. Fill in the required details about your intended use of the Twitter API.
4. Wait for approval (usually takes a few hours to a few days).

### 2. Generate API Keys
After your developer account is approved, you can generate the necessary API keys:
1. Navigate to the **Projects & Apps** section.
2. Click on **Create App**.
3. Fill out the required fields (app name, description, website URL).
4. go to the **Keys and tokens** tab once the app is created.
5. Note down your **API Key**, **API Secret Key**, **Access Token**, and **Access Token Secret**.

### 3. Prepare Your Environment
1. Clone this repository to your local machine:
   ```bash
   git clone <repository-url>
   cd <repository-folder>

2. Create a .env file in the root of your project and add your Twitter API credentials:

TWITTER_API_KEY=your_api_key_here
TWITTER_API_SECRET_KEY=your_api_secret_key_here
TWITTER_ACCESS_TOKEN=your_access_token_here
TWITTER_ACCESS_TOKEN_SECRET=your_access_token_secret_here

3. Install the required Go packages:
   go get github.com/dghubble/oauth1
   go get github.com/joho/godotenv

4. Run the Program
   go run main.go

### 1. Posting a Program Details
New Tweet
The application posts a new tweet by sending a JSON payload containing the tweet text to the Twitter API's /2/tweets endpoint.

Example Request:

POST https://api.twitter.com/2/tweets
Content-Type: application/json

{
  "text": "Hello from Twitter API!"
}

Example Response:

{
  "data": {
    "id": "1234567890123456789",
    "text": "Hello from Twitter API!"
  }
}

### 2. Deleting an Existing Tweet
After posting the tweet, the application waits for 30 seconds and then sends a DELETE request to the /2/tweets/:id endpoint to delete the tweet.

Example Request:

DELETE https://api.twitter.com/2/tweets/1234567890123456789

Example Response:

204 No Content

###3. Error Handling
The application checks for various error conditions during API requests. If any errors occur, appropriate messages are logged.

Common Errors:
401 Unauthorized: This indicates invalid or expired credentials.
403 Forbidden: This signifies insufficient permissions to perform the requested action.
404 Not Found: This indicates that the requested tweet does not exist.

The application will log an error message similar to:

Error posting tweet: twitter: 453 You currently have access to a subset of Twitter API v2 endpoints.

### Conclusion
This project provides a practical understanding of how to interact with the Twitter API using Go, focusing on posting and deleting tweets. It demonstrates the importance of proper authentication and error handling when working with web APIs.
 



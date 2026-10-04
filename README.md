# AI-Powered Business Assistant

An AI-powered business assistant prototype built for **SS Production** to help a small-business owner record business updates and ask questions using natural language.

## Overview

Small-business information such as sales, quantities, payment status, customers, and other events can be difficult to maintain when updates are entered manually.

This project explores how AI and workflow automation can convert natural-language messages into structured business records and provide useful answers from those records.

The system is designed around a simple interface: the business owner communicates through **Telegram**, while the automation handles classification, data extraction, storage, and responses in the background.

## Architecture
```
Telegram Bot
     ↓
Make.com — Watch Updates
     ↓
Gemini — Request Classification
     ↓
    Router
   ↙      ↓      ↘
Update  Question  Unknown
  ↓        ↓        ↓
Gemini   Read      Reply
Extract  Records   to User
  ↓        ↓
JSON     Gemini
Parse    Summary
  ↓        ↓
Iterator  Owner Request
  ↓        ↓
Google Sheets
  ↓
Telegram Confirmation / Answer
```
Main Workflows

1. Business Update
The owner can send a natural-language business update through Telegram.
The workflow:
1. Receives the Telegram message.
2. Uses Gemini to classify the request.
3. Extracts structured business information.
4. Parses the JSON response.
5. Stores the extracted event in Google Sheets.
6. Sends a confirmation back through Telegram.

2. Business Question
The owner can also ask questions about the recorded business information.
The workflow:
1. Receives the question through Telegram.
2. Retrieves business records from Google Sheets.
3. Aggregates the records.
4. Sends the relevant data to Gemini.
5. Generates a response.
6. Stores the request and response.
7. Sends the answer back through Telegram.

3. Unknown Request
If the system cannot classify the message as a business update or business question, it asks the owner to provide a clearer request.
Data Structure
The system uses Google Sheets as the current data store.
Business Events
Field	Purpose
Event ID	Identifies the event
Timestamp	Records when the event occurred
Event Type	Type of business event
Customer	Customer information
Product	Product involved
Quantity	Quantity involved
Unit	Unit of measurement
Amount	Transaction amount
Payment Status	Payment state
Due Date	Payment due date
Notes	Additional information


4. Owner Requests
Stores owner questions and the generated responses.
Technology Stack
- Make.com — workflow automation and orchestration
- Google Gemini — request classification, information extraction and business-question processing
- Telegram Bot — natural-language user interface
- Google Sheets — structured business data storage
- JSON — structured data exchange
- APIs / Webhooks — system integration

5. Project Screenshots

 # Workflow Architecture
 The complete automation workflow connecting Telegram, Gemini, Make.com, and Google Sheets.
 ![Workflow](Screenshots/Workflow)

 # Owner Update
 The business owner can send a natural-language business update to the assistant.
 ![Owner Update](Screenshots/OwnerUpdate)

 # Automated Response
 The assistant confirms that the business update has been received and recorded.
 ![Response](Screenshots/Response)

 # Google Sheets Update
 The extracted business information is stored as structured data in Google Sheets.
 ![Google Sheets Update](Screenshots/GooglesheetUpdate)

 # Business Question
 The owner can ask questions about the recorded business information.
 ![Owner Request](Screenshots/OwnerRequest)

 # Business Data Retrieval
 The workflow retrieves the stored business data before generating the response.
 ![Database Scan](Screenshots/DatabaseScan)

5. What This Project Demonstrates
- Multi-step workflow automation
- LLM-based classification
- Structured information extraction
- JSON-based data processing
- API and webhook integration
- Routing different types of requests
- Connecting AI processing with business data
- Designing an automation around a real business use case

6. Project Context
This project was built around SS Production, a small paper-plate manufacturing business, as a practical environment for experimenting with business process automation.
The goal was not simply to build an AI chatbot, but to connect an AI interface with structured business records and automate a real operational workflow.

7. Future Improvements
Potential future improvements include:
- Additional business event types
- More robust validation of extracted data
- Better handling of incorrect or incomplete inputs
- Error handling and retry mechanisms
- Additional business reporting
- Integration with other business systems
- More advanced access and permission controls

8. Status
Prototype / Personal Project
Built and tested as a practical AI automation project.

# Smart Tourism & Travel Planning Platform

## Project Overview

The **Smart Tourism & Travel Planning Platform** is an automation-based travel planning system built using **n8n**.

The project reduces manual work in travel planning by connecting customer registration, AI-based recommendations, booking and itinerary management, travel alerts, and post-trip feedback analysis into five independent workflows.

The platform uses **n8n, OpenAI, Google Sheets, Gmail, Google Calendar, and a Weather API**.

---

## Problem Statement

Travel agencies often spend considerable time understanding customer preferences, comparing travel options, preparing itineraries, coordinating bookings, and communicating travel updates.

Handling these activities manually becomes difficult when multiple customers are managed at the same time.

This project aims to automate the travel planning process using n8n, AI, APIs, and communication tools so that customers can receive more personalized and timely travel services.

---

## Objectives

- Collect customer information and travel preferences.
- Generate personalized destination recommendations using AI.
- Manage booking and itinerary information.
- Send weather-based travel alerts and notifications.
- Create travel events in Google Calendar.
- Collect customer feedback after travel.
- Analyze feedback using AI.
- Store travel-related information in Google Sheets.
- Automate customer communication through Gmail.

---

# System Architecture

The platform consists of five independent workflows:

```text
Customer
   |
   v
01. Customer Registration & Preferences
   |
   v
02. AI Destination Recommendation
   |
   v
03. Booking & Itinerary Management
   |
   v
04. Travel Alerts & Notifications
   |
   v
05. Feedback Collection & Travel Analytics
```

The five workflows are implemented independently in n8n. Together, they represent the main stages of the travel planning journey.

---

# Workflows

## 1. Customer Registration & Preferences

### Purpose

Collects customer details and travel preferences and stores the information for further processing.

### Main Flow

```text
Webhook
   |
   v
Prepare Customer Data
   |
   v
AI Customer Profile
   |
   v
Google Sheets
   |
   v
Gmail
```

### Main Information

- Name
- Email
- Phone
- Destination
- Travel dates
- Interests
- Hotel type
- Transport preference
- Budget
- Number of travelers

The customer data is processed, stored in Google Sheets, and a registration confirmation is sent through Gmail.

---

## 2. AI Destination Recommendation

### Purpose

Generates personalized travel recommendations based on customer requirements.

### Main Flow

```text
Webhook
   |
   v
AI Agent
   |
   +---- OpenAI Chat Model
   |
   v
Google Sheets
   |
   v
Gmail
```

### AI Processing

The AI considers:

- Budget
- Number of travelers
- Destination
- Travel dates
- Interests
- Hotel type
- Transport preference

The generated recommendation can include:

- Recommended destination
- Reason for recommendation
- Estimated hotel cost
- Estimated transport cost
- Estimated food cost
- Estimated activity cost
- Total estimated cost
- Top activities
- Day-by-day itinerary
- Budget suitability

---

## 3. Booking & Itinerary Management

### Purpose

Handles booking-related information and itinerary generation.

### Main Flow

```text
Webhook
   |
   v
Switch
 |      |      |
 v      v      v
Manali Shimla Goa
 |      |      |
 +------+------+ 
        |
        v
     AI Agent
        |
        v
  Google Sheets
        |
        v
      Gmail
```

The Switch node provides conditional branching based on the selected destination.

### Booking Information

- Customer name
- Email
- Destination
- Number of travelers
- Start date
- End date
- Booking type
- Hotel
- Room type
- Transport
- Budget

The processed booking and itinerary information is stored in Google Sheets and communicated through Gmail.

---

## 4. Travel Alerts & Notifications

### Purpose

Retrieves weather information and sends an appropriate travel notification.

### Main Flow

```text
Webhook
   |
   v
HTTP Request / Weather API
   |
   v
IF Condition
  /  /   Rain  No Rain
 |      |
 v      v
Alert  Update
Email  Email
  \     /
   \   /
    v v
Google Calendar
```

The workflow uses weather information such as temperature, precipitation, rain, and weather code.

The IF node checks the weather condition and selects the appropriate notification path. The workflow also creates a Google Calendar event for the travel schedule.

---

## 5. Feedback Collection & Travel Analytics

### Purpose

Collects post-trip customer feedback and uses AI to analyze it.

### Main Flow

```text
Webhook
   |
   v
AI Agent
   |
   +---- OpenAI Chat Model
   |
   v
Google Sheets
   |
   v
Gmail
```

### Feedback Analysis

The AI generates structured information including:

- Sentiment
- Satisfaction level
- Key positive points
- Key issues
- Suggested improvements
- Summary

The analyzed feedback is stored in Google Sheets and a thank-you message is sent to the customer.

---

# Integrations

| Integration | Purpose |
|---|---|
| **n8n** | Workflow automation and orchestration |
| **OpenAI** | AI recommendations, itinerary processing and feedback analysis |
| **Google Sheets** | Storage of customer, booking and feedback information |
| **Gmail** | Automated customer communication |
| **Google Calendar** | Travel event and schedule management |
| **Weather API** | Weather information for travel alerts |

---

# AI Features

### Customer Profiling
Customer information is processed to create a useful customer profile.

### Destination Recommendation
Travel requirements are analyzed to generate personalized destination recommendations.

### Itinerary Processing
The AI Agent helps generate travel and itinerary information based on booking requirements.

### Feedback Analysis
Customer feedback is analyzed to identify sentiment, satisfaction, positive points, issues, improvements, and a summary.

---

# Data Storage

Google Sheets is used for storing information generated by the workflows, including:

- Customer registration
- Travel preferences
- Destination recommendations
- Booking information
- Itinerary information
- Feedback
- Feedback analysis

---

# Testing

The workflows were tested using their n8n webhook test URLs.

Testing was performed by sending JSON requests through Windows CMD using `curl`.

The following were tested:

- Webhook input
- AI processing
- Google Sheets updates
- Gmail notifications
- Conditional branching
- Weather API response
- Google Calendar event creation
- Feedback analysis

### Example

```cmd
curl -X POST "YOUR_N8N_TEST_WEBHOOK_URL" -H "Content-Type: application/json" -d "{"name":"Priyank Sharma","email":"priyanksharma7426@gmail.com","destination":"Manali","budget":40000,"travelers":2}"
```

Replace `YOUR_N8N_TEST_WEBHOOK_URL` with the Test URL shown in the corresponding n8n Webhook node.

---

# Project Structure

```text
Smart-Tourism-Travel-Planning/
|-- Screenshots
|-- 01 - Customer Registration & Preferences.json
|-- 02 - AI Destination Recommendation.json
|-- 03 - Booking & Itinerary Management.json
|-- 04 - Travel Alerts & Notifications.json
|-- 05 - Feedback Collection & Travel Analytics.json
|-- Demo Video
|-- Presentation
|-- Workflow Documentation
`-- README.md
```

---

# How to Run

1. Open the n8n instance.
2. Import the required workflow JSON file.
3. Configure the required credentials.
4. Connect the required Google Sheets and Gmail accounts.
5. Configure the OpenAI credential.
6. Configure the Weather API workflow.
7. Open the required Webhook node.
8. Click **Listen for Test Event**.
9. Send the required JSON request using CMD or another API client.
10. Check the workflow execution.
11. Verify the generated output in Google Sheets, Gmail, or Google Calendar.

---

# Screenshots

# 📸 Screenshots

## 1. Customer Registration & Preferences

![Customer Registration Workflow](Screenshots%20-%20n8n/workflow-1.png)

## 2. AI Destination Recommendation

![AI Destination Recommendation](Screenshots%20-%20n8n/workflow-2.png)

## 3. Booking & Itinerary Management

![Booking & Itinerary Management](Screenshots%20-%20n8n/workflow-3.png)

## 4. Travel Alerts & Notifications

![Travel Alerts & Notifications](Screenshots%20-%20n8n/workflow-4.png)

## 5. Feedback Collection & Travel Analytics

![Feedback & Analytics](Screenshots%20-%20n8n/workflow-5.png)
  

---

# Demo

The project demonstration covers:

1. Customer registration
2. AI destination recommendation
3. Booking and itinerary management
4. Weather-based travel alerts
5. Feedback collection and AI analysis
6. Google Sheets data storage
7. Gmail notifications
8. Google Calendar integration

---

# Future Scope

The project can be extended by adding:

- Real flight and hotel booking APIs
- Google Maps and location services
- Attraction and activity APIs
- Currency conversion
- Visa and travel-document information
- Travel analytics dashboard
- Advanced error handling and retry mechanisms
- Human approval before final booking
- More destinations and languages
- Additional personalization features

---

# Deliverables

- Exported n8n workflow JSON files
- Workflow architecture
- Project README
- Workflow screenshots
- Demonstration video
- Presentation

---

# Project Information

**Project:** Smart Tourism & Travel Planning Platform  
**Domain:** Travel & Tourism  
**Platform:** n8n  
**Project Type:** AI & Workflow Automation  
**Course:** Summer School'26 – N8N Capstone Project

---

## Conclusion

The Smart Tourism & Travel Planning Platform demonstrates how AI and workflow automation can be combined to simplify different stages of travel planning.

By using independent n8n workflows and integrations such as OpenAI, Google Sheets, Gmail, Google Calendar, and Weather API, the system automates customer interaction, recommendations, itinerary processing, travel alerts, and feedback analysis.

# AI-Buyer-Agent-commerce-Project
An AI-powered buyer agent for conversational e-commerce that understands customer intent, searches products, recommends relevant products, manages checkout, processes payments, and sends payment-status notifications.

## Overview

Track01 connects an AI-powered conversational interface with a merchant's commerce backend.

A customer can interact with the system through Telegram, describe what they want to buy, and receive product recommendations based on their intent.

The system can then:

* Understand buyer intent
* Search the merchant catalog
* Recommend suitable products
* Ask the user to accept or reject recommended products
* Build the checkout
* Generate a Razorpay payment link
* Track payment status through webhooks
* Send payment notifications through Telegram
* Maintain an audit log of all commerce events

 # Architecture
Customer
   │
   ▼
Telegram Bot
   │
   ▼
n8n AI Buyer Agent
   │
   ├── Understand Intent
   │
   ├── Search Product Catalog
   │
   ├── Recommend Products
   │
   ├── User accepts/rejects products
   │
   └── Checkout
          │
          ▼
     FastAPI Backend(audit_log.jsonl)
          │
          ▼
       Razorpay
          │
          ▼
     Payment Webhook
          │
          ▼
    Update Audit Log
          │
          ▼
   Payment Notification
          │
          ▼
      Telegram

## 🛠️ Tech Stack

| Technology       | Purpose                                    |
| ---------------- | ------------------------------------------ |
|                  |                                            |
| FastAPI          | Merchant backend API                       |
| n8n              | AI workflow orchestration                  |
|                  |                                            |
| Telegram Bot API | Conversational buyer interface             |
| Razorpay         | Payment processing                         |
| Webhooks         | Payment event handling                     |
| Google Gemini    | AI-powered intent and recommendation logic |

##  Key Features

### 1. Conversational Product Discovery

Users can describe their requirements naturally instead of searching using exact product names.

Example:

> "I need affordable wireless earbuds for daily use."

The AI agent interprets the request and searches the merchant catalog.

### 2. Catalog-Based Recommendations

Products are recommended only from the merchant's catalog.

The agent uses product information such as:

* Product ID
* Product name
* Price
* Stock status
* Product relationships

### 3. User Product Confirmation

The agent presents suitable products and allows the user to accept or reject the recommendations.

The user's confirmation determines which products proceed to checkout.

### 4. Checkout and Payment

After the customer confirms the products, the system creates the checkout/payment flow and generates a Razorpay payment link.

### 5. Payment Status Tracking

Razorpay webhook events are processed by the backend.

Supported payment states include:

order.paid
payment.captured
payment.failed

The system can then notify the customer about the payment result.

### 6. Audit Logging

All important commerce events are recorded in an audit log for traceability and debugging.

The audit log records details such as:

* User/customer information
* Order details
* Selected products
* Payment status
* Payment/order IDs
* Event timestamps
* Important workflow events

## Setup

### 1. Clone the repository

### 2. Create a Python virtual environment

### 3. Install dependencies

### 4. Configure environment variables

### 5. Start the FastAPI backend

## 🔄 n8n Workflows

The repository contains exported n8n workflows:

### AI Buyer Agent

Responsible for the buyer conversation, product discovery, recommendations, user confirmation, checkout logic, audit logging, and commerce orchestration.

### Payment Notifications

Handles payment events and sends appropriate notifications to the customer.

Import the workflow JSON files into your n8n instance and configure the required credentials.

##  Payment Flow
Customer confirms order
        ↓
Checkout created
        ↓
Razorpay Payment Link
        ↓
Customer completes payment
        ↓
Razorpay generates payment event
        ↓
Webhook received
        ↓
Payment status processed
        ↓
Event details entered into audit_log
        ↓
Telegram notification

##  Security
This repository contains configuration templates only.

API keys, webhook secrets, bot tokens, and database credentials must be stored in environment variables .

##  Demo

A demonstration of the complete buyer-agent flow is available in:
https://www.loom.com/share/ff9d830c57974513a610f9fa553b7c9c

The demo covers:

1. Customer request
2. AI intent understanding
3. Product recommendation
4. User acceptance/rejection of products
5. Checkout
6. Audit log
7. Razorpay payment
8. Payment notification

# Project Status

 Active development




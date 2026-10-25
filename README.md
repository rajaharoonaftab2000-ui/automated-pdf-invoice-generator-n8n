# Automated PDF Invoice Generator

An invoice automation built with n8n, Google Calendar, JavaScript, html2pdf.app, and Gmail.

## Overview

This automation retrieves appointment information from Google Calendar, prepares an invoice, converts it into a PDF, and sends it through Gmail.

The demo uses salon appointments and a predefined service price list to demonstrate how businesses can reduce repetitive invoice preparation and email work.

## Workflow

Schedule Trigger → Get Calendar Events → Process Appointment Details → Build Invoice HTML → Generate PDF → Send Invoice through Gmail

## How It Works

1. ⏰ **Start the scheduled workflow**  
   The Schedule Trigger starts the automation at the configured time.

2. 📅 **Retrieve calendar events**  
   The workflow fetches Google Calendar events within the configured date range.

3. 📋 **Process appointment details**  
   JavaScript extracts the customer name from the event description and reads the service from the event title.

4. 💰 **Determine the service price**  
   The service title is matched against a predefined salon price list.

5. 🧾 **Prepare the invoice**  
   An HTML template displays the invoice number, customer name, appointment date, service, and amount.

6. 📄 **Generate a PDF**  
   An HTTP request sends the HTML to html2pdf.app for PDF generation.

7. 📧 **Email the invoice**  
   Gmail sends the invoice to the configured recipient with the PDF attached.

## Features

- ⏰ Scheduled workflow execution
- 📅 Google Calendar integration
- 📋 Customer name extraction from event descriptions
- 💰 Service pricing based on a customizable price list
- 🧾 HTML invoice template
- 📄 PDF invoice generation
- 📧 Gmail delivery with a PDF attachment
- ⚙️ Customizable schedule, invoice wording, and service prices

## Technologies Used

- **n8n** — Workflow automation
- **Google Calendar** — Appointment information
- **JavaScript** — Data processing, pricing, and HTML generation
- **html2pdf.app** — HTML-to-PDF conversion
- **Gmail** — Invoice email delivery

## Use Case

This workflow demonstrates invoice automation for salons and other appointment-based businesses.

Instead of preparing each invoice manually, the business can use calendar appointment information to generate a PDF and email it through a scheduled workflow.

The service list, prices, currency label, and invoice design can be adapted to the business.

## Setup Requirements

- A running n8n instance
- Google Calendar OAuth credentials
- Gmail OAuth credentials
- An html2pdf.app account and API key
- A calendar containing appointment details
- A recipient email address for testing

## Configuration

1. Import `automated-invoice-generator.sanitized.json` into n8n.
2. Connect your Google Calendar and Gmail credentials.
3. Replace `YOUR_CALENDAR_ID` with your calendar ID.
4. Configure your PDF API authentication securely in n8n.
5. Update the JavaScript service price list.
6. Customize the invoice HTML and currency label.
7. Replace `recipient@example.com` with your test recipient.
8. Verify that Gmail attaches the binary PDF returned by the HTTP Request node.
9. Configure the schedule, time zone, and event date range.
10. Test manually before activating the workflow.

The imported workflow is inactive by default.

## Sample Appointment

**Event title:**
```text
Haircut appointment
```

**Event description:**
```text
Customer Name: Demo Customer
```

Set a valid appointment start date and time.

The workflow also supports extracting an optional `Chat ID:` field, but this value is not used for invoice delivery.

## Important Notes

- The current demo sends invoices to one configured email address. It does not automatically extract each customer's email.
- The calendar query currently includes events from seven days before today to seven days after the current time.
- The workflow does not check whether appointments are completed or paid.
- Duplicate prevention is not included. Repeated runs may send another invoice for the same appointment.
- Invoice numbers are randomly generated and are not guaranteed unique.
- Services that do not match the price list receive an amount of zero.
- Validate appointment fields and escape event text before using it in invoice HTML.
- Payment collection, tax calculation, invoice logging, and dedicated error alerts are not included.
- Scheduled execution requires n8n to remain online.
- Hosting and PDF API charges depend on the services used.
- The public workflow contains placeholders for private settings. Do not upload credentials or customer data.

## Demo Video

[Watch the Invoice Generator Demo](./2_invoice_workflow_captions_voiceover.mp4)

Upload the demo video to the repository using the filename above for this link to work.

## Project Status

Completed portfolio demo demonstrating calendar event retrieval, invoice preparation, PDF generation, and Gmail delivery.

Additional validation and duplicate prevention are needed before live business use.

## Created By

**Haroon AI Automation**

NexusCloud Enterprise B2B SaaS Modernization
Business Analysis & Systems Architecture Portfolio

Author: Saad Elboukhali
Role: IT Business Analyst
Domain: Enterprise B2B SaaS | Software License Marketplace | FinTech Payments | CRM | Cloud ERP

1. Project Overview

NexusCloud is a fictional enterprise B2B software license marketplace that provides corporate customers with subscription licenses for 20 enterprise software products, including Microsoft 365, CrowdStrike, Salesforce, Palo Alto Networks, Okta, and ServiceNow.

The platform serves business customers across Europe, the Middle East, and North Africa (EMEA).

This portfolio project demonstrates how Business Analysis and Systems Architecture can transform a fragmented, manual business operation into a more automated, secure, and scalable enterprise platform.

The project covers the complete business analysis lifecycle, including:

Business requirements gathering and documentation.
Business Process Reengineering (BPR).
BPMN 2.0 and UML process modeling.
Agile backlog management and requirements prioritization.
SQL data profiling and business performance analysis.
Database design and legacy data migration.
Financial risk identification and KPI reporting.
Enterprise system integration architecture.

The main objective: Identify operational problems using real SQL analysis, translate them into measurable business requirements, and design a practical solution supported by process models, database structures, and technical specifications.

2. Business Problem & Initial Assessment (As-Is)

Before modernization, NexusCloud relied heavily on manual spreadsheets, disconnected systems, and inconsistent business rules.

This created significant problems across order processing, payments, inventory management, sales discounting, and data quality.

To understand the scale of these problems, I analyzed:

700 raw legacy CSV records.
650 production database orders.
20 enterprise software SKUs.

The SQL analysis identified five major business challenges.

Key Findings
Business Problem	Findings	Business Impact
Unauthorized CPQ Discounts (BR-08)	51 deals exceeded the 25% discount limit without manager approval.	$23,378.66 in unauthorized margin reductions.
ERP Synchronization Delays (BR-04)	73 out of 650 orders exceeded the 3-second SLA.	SLA compliance dropped to 88.77%.
Payment Processing Failures (BR-02)	523 successful, 56 pending retries, 51 card declines, and 20 manual refunds.	Payment delays and increased operational workload.
Critical Inventory Levels (BR-05)	7 out of 20 SKUs fell below their minimum stock thresholds.	$12,296.66 estimated restocking budget required.
Legacy Data Corruption (BR-10)	37 production orders contained duplicate license keys.	Risk of duplicate license allocation and data integrity failures.
Business Impact at a Glance
KPI	Result
Total production orders analyzed	650
Legacy CSV records analyzed	700
Software products monitored	20
ERP SLA compliance	88.77%
Unauthorized discount deals	51
Unauthorized margin reductions	$23,378.66
Critical inventory SKUs	7
Estimated restocking budget	$12,296.66
Orders requiring payment retry	56
Orders with duplicate license keys	37

These findings established the business justification for modernization and helped define the project's functional and non-functional requirements.

3. Proposed Solution (To-Be Architecture)

The proposed solution introduces an integrated enterprise architecture designed to automate critical business operations, reduce financial risks, and improve system reliability.

Core Solution Components

1. Secure Identity & Access Management

Enterprise Single Sign-On (SSO).
Multi-Factor Authentication (MFA).
Role-Based Access Control (RBAC).
OAuth 2.0 / Azure AD integration.

2. Automated Payment Processing

Stripe payment gateway integration.
PCI-DSS-aligned payment tokenization.
Webhook idempotency to prevent duplicate transactions.
Automated payment retry and refund workflows.

3. Automated Order & ERP Synchronization

Real-time inventory verification.
Temporary 10-minute inventory soft-lock during checkout.
Automatic rollback when payment fails or expires.
ERP synchronization within a 3-second target SLA.

4. CRM Integration

Salesforce lead and customer synchronization.
Asynchronous RabbitMQ processing.
Automatic retry mechanisms.
Dead-Letter Queue (DLQ) for failed messages.

5. CPQ Pricing & Discount Governance

Automated tiered enterprise pricing.
Preventive controls for discounts exceeding 25%.
Mandatory manager approval.
Four-hour manager escalation process.

6. License Security & Customer Portal

AES-256 encryption at rest.
Masked license keys in the user interface.
Digital License Vault.
Seat assignment and CSV export.
Security audit trail for license access.

7. Business Intelligence & Reporting

Nightly ETL processing.
Cloud data warehouse integration.
Power BI executive dashboards.
Automated low-stock and operational alerts.
4. Business Requirements Documentation

The Business Requirements Document (BRD) defines 10 business requirements, each supported by functional requirements, non-functional requirements, measurable targets, and implementation priorities.

Requirements Overview
ID	Business Requirement	Priority	Target Release
BR-01	Secure Identity & Access Management	Must Have	Sprint 1
BR-02	Payment Gateway Integration & Automated Billing	Must Have	Sprint 1
BR-03	Salesforce CRM Integration	Could Have	Sprint 3
BR-04	Automated Order & ERP Inventory Synchronization	Must Have	Sprint 1
BR-05	Analytics Dashboard & Alerting Engine	Should Have	Sprint 2
BR-06	Customer Support Ticketing & SLA Management	Could Have	Sprint 3
BR-07	Self-Service B2B License & Seat Management	Should Have	Sprint 2
BR-08	Automated Tiered Pricing & CPQ Engine	Should Have	Sprint 2
BR-09	Cryptographic License Protection & Audit Trail	Must Have	Sprint 1
BR-10	Legacy Spreadsheet Migration & Bulk Ingestion	Must Have	Sprint 1

Prioritization follows the MoSCoW and Kano frameworks to balance business value, customer expectations, and implementation complexity.

5. Business Analysis Deliverables

This project includes a collection of practical Business Analysis and Systems Architecture deliverables.

A. Business Requirements Document (BRD)

File: NexusCloud_BRD_v2.0_Final.docx

The document includes:

Business objectives and project scope.
Stakeholder requirements.
Functional Requirements (FRs).
Non-Functional Requirements (NFRs).
Business rules and acceptance criteria.
SQL-derived operational baselines.
System integration requirements.
Risks, assumptions, and constraints.

An initial BRD version is also included to demonstrate requirements evolution and document version control.

B. Master Business Analysis Workbook

File: NexusCloud_Master_BA_Workbook_v2.0.xlsx

The Excel workbook contains eight integrated worksheets:

Tab	Deliverable	Purpose
01	Stakeholder Analysis	Power/Interest matrix, stakeholder mapping, and RACI assignments.
02	Feasibility & Impact	Strategic prioritization, feasibility assessment, and risk scoring.
03	MoSCoW & Kano	Requirements prioritization and FR/NFR classification.
04	Elicitation Guide	Interview questions, JAD workshops, surveys, and observation logs.
05	Agile Backlog	10 user stories with Gherkin acceptance criteria and story points.
06	BPR & Process Specifications	As-Is/To-Be analysis, UML specifications, ERD keys, and DFD data stores.
07	Requirements Traceability Matrix	End-to-end traceability from business requirements to UAT test cases.
08	SQL KPI Dashboard	Business performance metrics, financial analysis, and Excel charts.

The Agile backlog contains 10 user stories totaling 73 Fibonacci story points across three planned sprints.

6. Business Process Modeling (BPMN 2.0 & UML)

The process architecture illustrates how NexusCloud transitions from manual business operations to automated enterprise workflows.

BPMN Deliverables

Directory: 02_Process_Modeling_BPMN_UML/

Diagram 01: Order-to-Fulfillment Process

BPMN_01_Order_to_Fulfillment_3s_SLA.png

A high-level BPMN 2.0 swimlane diagram illustrating:

Customer order submission.
Inventory verification.
Payment authorization.
ERP synchronization.
License allocation.
Order completion.

Diagram 02: End-to-End Exception & CPQ Process

BPMN_02_End_to_End_Exception_and_CPQ_Flow.jpg

A detailed five-swimlane process covering:

Corporate Buyer.
Sales Representative & Manager.
NexusCloud Front-End & API.
Stripe Payment Gateway.
SQL Server ERP & RabbitMQ Queue.
Key Architectural Decisions

Two-Phase Inventory Locking

When checkout begins, the system temporarily reserves available inventory for 10 minutes.

Successful payment: inventory is committed.
Failed payment: inventory is released.
Expired checkout: the temporary reservation is automatically rolled back.

Webhook Idempotency

Duplicate Stripe webhook events are identified and ignored to prevent duplicate order processing or payment actions.

Asynchronous Processing

Non-critical operations, such as Salesforce CRM updates and PDF invoice generation, are transferred to RabbitMQ workers.

This prevents background processes from delaying the customer checkout experience.

License Delivery SLA

The architecture targets license synchronization and delivery within 3 seconds, with a 99.9% availability/compliance objective for the defined ERP synchronization requirement.

7. Database Design & SQL Data Analysis

Directory: 03_Database_and_Legacy_Migration/

The database deliverable demonstrates relational database design, data validation, legacy migration analysis, and business KPI extraction.

Database Components

File: NexusCloud_Enterprise_Database_650Rows.sql

Includes:

SQL Server relational database schema.
erp_inventory inventory table.
nexus_orders production orders table.
Primary and foreign key relationships.
SQL audit and validation queries.
Business KPI calculations.

The database model follows Third Normal Form (3NF) principles to reduce redundancy and improve data integrity.

SQL Business Intelligence & Audit Queries

Four core SQL analyses reproduce the project's main business findings.

1. Inventory & Restocking Analysis (BR-05)

Identifies products below their minimum stock threshold and calculates the estimated restocking budget.

2. ERP Synchronization SLA Analysis (BR-04)

Measures order synchronization compliance against the 3-second target and identifies the categories with the highest latency.

3. Unauthorized CPQ Discount Analysis (BR-08)

Identifies deals exceeding the 25% discount limit without manager approval and calculates associated financial exposure.

4. Duplicate License Key Detection (BR-10)

Identifies duplicate license keys using SQL aggregation and the HAVING COUNT() > 1 condition.

These queries connect technical database analysis directly to business risks and management decisions.

Legacy Data Migration Testing

File: NexusCloud_Legacy_Raw_Dirty_Orders_700Rows.csv

The raw CSV dataset contains 700 legacy records used to demonstrate data quality assessment and migration validation.

The migration requirements include:

Duplicate license key detection.
SHA-256-based duplicate quarantine.
Data validation before import.
Prevention of corrupted records entering production.
Bulk ingestion performance target of 10,000 rows in under 15 seconds.
8. Repository Structure
text
nexuscloud-ba-portfolio/
│
├── README.md
│
├── 01_Requirements_Documentation/
│   ├── NexusCloud_BRD_v2.0_Final.docx
│   ├── NexusCloud_BRD_v1.0_Initial_Draft.docx
│   └── NexusCloud_Master_BA_Workbook_v2.0.xlsx
│
├── 02_Process_Modeling_BPMN_UML/
│   ├── BPMN_01_Order_to_Fulfillment_3s_SLA.png
│   └── BPMN_02_End_to_End_Exception_and_CPQ_Flow.jpg
│
└── 03_Database_and_Legacy_Migration/
    ├── NexusCloud_Enterprise_Database_650Rows.sql
    └── NexusCloud_Legacy_Raw_Dirty_Orders_700Rows.csv

9. Methodologies, Technologies & Tools
Business Analysis Methodologies
Agile Scrum.
Business Process Reengineering (BPR).
BPMN 2.0.
UML 2.5.
MoSCoW Prioritization.
Kano Model.
Requirements Elicitation.
Requirements Traceability.
User Story Mapping.
Gherkin Acceptance Criteria.
Technical Skills & Tools
Category	Technologies & Tools
Business Analysis	BRD, FR/NFR, RTM, User Stories, RACI
Process Modeling	Microsoft Visio, Lucidchart, BPMN 2.0, UML
Database	Microsoft SQL Server, T-SQL, 3NF, ERD, DFD
Data Analysis	Microsoft Excel, SQL Data Profiling
Business Intelligence	Microsoft Power BI
Payments	Stripe API, Webhooks, PCI-DSS concepts
CRM	Salesforce
Messaging	RabbitMQ
Cloud & Identity	Azure AD, OAuth 2.0, Cloud ERP
10. Business Value & Expected Outcomes

The modernization initiative is designed to address the operational and financial weaknesses identified during the initial SQL assessment.

Business Area	Expected Improvement
Revenue Protection	Prevent unauthorized discounts through automated approval controls.
Order Fulfillment	Reduce ERP synchronization delays and improve SLA compliance.
Payment Reliability	Automate retries, reduce manual intervention, and prevent duplicate webhook processing.
Inventory Management	Improve stock visibility and prevent overselling through temporary inventory reservations.
Data Integrity	Detect and quarantine duplicate license keys before production ingestion.
Customer Experience	Provide secure self-service access to licenses and subscription management.
Operational Efficiency	Move non-critical integrations to asynchronous background processing.
Management Reporting	Provide measurable operational and financial KPIs through Power BI.

Important: The figures in the business case represent findings from the analyzed datasets. The proposed improvements are architectural targets and expected outcomes, not claims of an already deployed production system.

11. Author & Contact

Saad Elboukhali
Junior Business Analyst

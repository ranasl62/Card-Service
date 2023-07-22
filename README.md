# Simple Order Carts Deployment on AWS

This project demonstrates the deployment of a simple order carts application on AWS using various services to achieve scalability, reliability, and event-driven functionalities. The architecture utilizes AWS services such as Auto Scaling, Load Balancer, Lambda, SQS, SNS, SES, S3 Static Website Hosting, and Step Functions. The system allows users to place orders for items, handles the order processing, sends email notifications, and logs events in an S3 bucket.

## Architecture Overview

The application's architecture is designed to be scalable, fault-tolerant, and event-driven, ensuring smooth handling of order carts and enabling real-time communication with users.

### Components and Services

- Frontend Application (S3 Static Website Hosting):
  - The frontend application is hosted in an S3 bucket, providing a user-friendly interface for customers to interact with the order carts system.

- Auto Scaling and Load Balancer:
  - The backend components, such as EC2 instances running the API server, are set up with Auto Scaling and behind a Load Balancer.
  - Auto Scaling dynamically adjusts the number of instances based on traffic demand, ensuring high availability and performance.

- Lambda Functions:
  - Several Lambda functions are utilized for event-driven tasks, such as processing order data, sending email notifications, and handling background operations.
  - Order Lambda: Triggered by DynamoDB streams when new orders are placed, it sends email notifications to users using SES and SNS.
  - Event Service Lambda: Triggered by SQS when events are received, it stores logs in an S3 bucket using Step Functions.

- SQS (Simple Queue Service):
  - SQS is used to decouple components and manage event-driven communication between services.
  - Order Lambda pushes messages to SQS for the Event Service Lambda to process.

- SNS (Simple Notification Service):
  - SNS is responsible for delivering email notifications to users.
  - The Order Lambda publishes email payloads to SNS, which sends emails using SES.

- SES (Simple Email Service):
  - SES is used for sending email notifications to users when new orders are placed or for other communication purposes.

- Step Functions:
  - Step Functions are used to orchestrate the storing of logs in an S3 bucket from the Event Service Lambda.
  - The logs are saved in a structured format in the designated S3 bucket.

## Deployment and Setup

To deploy the application, follow these steps:

1. Deploy the frontend application to an S3 bucket for static website hosting.
2. Set up an Auto Scaling group and attach a Load Balancer to it to handle backend traffic.
3. Create the required Lambda functions for order processing and event handling, ensuring they have the necessary IAM roles and permissions.
4. Configure SQS to handle communication between services.
5. Set up SNS to deliver email notifications using SES for sending emails.
6. Implement Step Functions for logging event data in the S3 bucket.
7. Test the system thoroughly to ensure all components work as expected.

Remember to adjust configurations, IAM roles, and permissions to match your specific requirements.

## Contact

https://www.linkedin.com/in/ranasl62/.

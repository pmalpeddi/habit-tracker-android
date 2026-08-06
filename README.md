# Habit Tracker (Android)

A native Android habit tracker built to track two kinds of consistency: **good habits you consistently follow through on**, and **bad habits you consistently avoid**. Minimalist design with light and dark modes plus customizable accent colors.

## Overview

Most habit trackers only measure "did I do the good thing." This app tracks both directions:

- **Good habits** build a completion streak (did the habit today)
- **Bad habits** build an avoidance streak (successfully avoided the habit today)

The two streak types break and reset differently, since a missed good habit and a slipped bad habit are not the same kind of failure.

## Status

In Progress - early development

## Tech Stack

**Android app**
- Kotlin
- Jetpack Compose (Material 3 theming, light/dark mode, accent color picker)
- Retrofit or Ktor client for networking (TBD)
- AWS Amplify Android SDK or Cognito SDK for auth

**Backend (AWS, provisioned via Terraform)**
- API Gateway
- Lambda
- DynamoDB
- Cognito (user auth)
- EventBridge (scheduled reminders, planned)

**Infrastructure as Code**
- Terraform

## Architecture

```
Android App (Kotlin + Compose)
        |
        v
   API Gateway
        |
        v
      Lambda  --------> DynamoDB
        |
        v
     Cognito (auth)
```

## Repository Structure

```
/android      Native Android app (Kotlin, Jetpack Compose)
/terraform    Infrastructure as Code for the AWS backend
```

## Data Model (planned)

**Habits table**
- habit_id
- user_id
- type (good / bad)
- name
- target_frequency
- streak_count
- created_at

**Logs table**
- habit_id
- date
- status (done / avoided / broken)

## Build Plan

- [ ] Phase 1: Repo setup, Android Studio project init, Terraform directory scaffold
- [ ] Phase 2: Backend - DynamoDB tables, Lambda CRUD + streak logic, API Gateway, Cognito
- [ ] Phase 3: Core Android app - habit list, add/edit habit, log entry, networking layer
- [ ] Phase 4: Streak logic (good vs. bad habit break/reset rules) + Material 3 theming
- [ ] Phase 5: Notifications, polish, screenshots

## Getting Started

Setup instructions will be added once the Android project and Terraform backend are initialized.

## License

All rights reserved. This source code is shared publicly for portfolio purposes only. No permission is granted to copy, modify, distribute, or use this code without explicit written permission from the copyright holder.

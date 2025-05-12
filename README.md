# 🌐 Circular Calendar App – Specification Document

## 📌 Overview

**App Concept:**  
A personal calendar app that represents time as a circular, clockwise-flowing spiral, designed for users who perceive time as cyclical. Unlike linear calendars, it uses zoomable spiral views of time (hour, day, week, month, year) to organize events and plans.

**Primary Use Case:**  
Event planning, time visualization, and scheduling with a focus on cyclical time perception.

---

## 🧩 Core Features

### 📅 Calendar Spiral Views

- Time flows clockwise in an infinite spiral

**Views:**
- **Hour view**: Time slots arranged in a radial layout
- **Day view**: 24-hour spiral
- **Week/Month/Year views**: Expanding concentric layers of spiral
- Smooth animated zooming between dimensions (e.g., pinch or swipe to zoom in/out)
- Highlight current unit (e.g., current hour, day, month, etc.)

---

### 📍 Event Representation

**Visual indicators:**
- **Size**: Duration
- **Color**: Category
- **Shape/Icon**: Type or priority
- Interactive markers placed along the spiral

---

### ✏️ Event Creation & Editing

- Accessed through a modal window

**Fields:**
- Title  
- Start time  
- End time  
- Category (color-coded)  
- Description  
- Reminders (set time before event)  
- Recurrence (daily, weekly, monthly, yearly, custom)  
- Attachments: text notes, file uploads, external links  
- Support for editing individual occurrences of recurring events

---

### 🔔 Notifications

- Scheduled reminders (e.g., 10 min, 1 hour, 1 day before event)

---

### 🔄 Calendar Sync

Two-way sync with:
- Google Calendar  
- Apple Calendar  
- Outlook Calendar

**Details:**
- OAuth-based authentication  
- Periodic sync and conflict resolution  
  - Preference set for "last write wins" or user prompts on conflicts

---

### 🔐 User Authentication

- Login, account creation, password recovery  
- Email/password authentication  
- Optional OAuth (Google, Apple)

---

### 🎨 Theme Support

- Light/dark mode based on system settings

---

### 📶 Platforms

Available on:
- iOS  
- Android  
- Web

---

## ⚙️ Architecture & Tech Stack

### Frontend
- **Framework**: React (web), React Native (mobile)  
- **Visualization**: D3.js or PixiJS (for performant spiral rendering)  
- **State Management**: Zustand, Redux, or React Context API  
- **Animations**: Framer Motion or Reanimated  
- **Design**: Tailwind CSS (web), NativeBase (mobile)  

### Backend
- **Framework**: Node.js with Express  
- **Auth**: Firebase Auth or Auth0  
- **Calendar Sync**: Google Calendar API, Apple EventKit, Microsoft Graph API  
- **Database**: PostgreSQL or Firestore  
- **Storage**: Firebase Storage / AWS S3 (for attachments)  
- **Push Notifications**: Firebase Cloud Messaging (FCM), APNs  

---

## 🧱 Data Model

### **User**
```json
{
  "id": "uuid",
  "email": "string",
  "password_hash": "string",
  "preferences": {
    "theme": "system|dark|light"
  },
  "external_calendars": {
    "google": { "token": "...", "sync_enabled": true },
    "apple": { "token": "...", "sync_enabled": false },
    "outlook": { "token": "...", "sync_enabled": true }
  }
}

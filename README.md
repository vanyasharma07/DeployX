# 🚀 DeployX – Automated Web Deployment Platform

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js](https://img.shields.io/badge/Node.js-v16+-green.svg)](https://nodejs.org/)
[![Docker](https://img.shields.io/badge/Docker-Ready-blue.svg)](https://www.docker.com/)
[![AWS](https://img.shields.io/badge/AWS-Powered-orange.svg)](https://aws.amazon.com/)

DeployX is an automated deployment platform that allows developers to deploy web applications simply by pushing code to GitHub.
Built using AWS, Docker, Node.js, and a custom reverse proxy layer, DeployX automates the entire process of building, containerizing, and hosting applications — all while providing a clean dashboard for logs, deployment status, and URLs.

---

## 🧾 Introduction

DeployX is a cloud-based automated deployment platform that lets users deploy apps instantly through GitHub integration.
When a user pushes code, DeployX automatically:

- Builds the project
- Creates a Docker container
- Deploys it on AWS infrastructure
- Generates a deployment URL
- Tracks status & logs in a dashboard

This makes DeployX ideal for:

- Student projects
- Hackathon submissions
- Small developer teams
- Full-stack web applications

---

## ⭐ Features

### 🔐 User Authentication
- JWT-based login
- Optional GitHub OAuth (for repo access)

### 🔗 GitHub Integration
- Connect a repository
- Auto-create a webhook
- Trigger deployments on every push

### 🔧 Automated Deployment
- Automated build and dockerization on every push
- Seamless deployment pipeline

### 🐳 Dockerized Isolation
Each project runs in its own container for security & scalability.

### 📊 Deployment Dashboard
- View deployments
- Check live status
- Access real-time logs
- Open deployed URL

### ☁️ AWS Cloud Hosting
- EC2 for Docker runtime
- Route 53 for subdomains
- S3 for logs & artifacts
- Custom reverse proxy for deployment URLs

---

## 🏗 Architecture

```
              ┌───────────────┐
              │     User       │
              └──────┬────────┘
                     │ Login / Create Project
              ┌──────▼────────┐
              │  DeployX UI    │
              └──────┬────────┘
                     │ API Calls
              ┌──────▼────────┐
              │ DeployX Backend│
              └──────┬────────┘
          Create webhook │
                     ┌──▼───────────────────────────────┐
                     │          GitHub Repo              │
                     └──┬───────────────────────────────┘
                        │ Push Event Triggers Webhook
              ┌─────────▼──────────┐
              │ DeployX Webhook API │
              └─────────┬──────────┘
                        │ Build → Dockerize → Run
              ┌─────────▼──────────────┐
              │   AWS EC2 (Docker Host) │
              └─────────┬──────────────┘
                        │ Expose via Reverse Proxy
              ┌─────────▼──────────┐
              │  Subdomain / URL   │
              └─────────────────────┘
```

---

## 🧰 Tech Stack

### Frontend
- React.js
- Axios
- TailwindCSS (optional)

### Backend
- Node.js
- Express.js
- MongoDB / PostgreSQL
- JWT Auth

### Cloud Infrastructure
- AWS EC2
- Custom reverse proxy
- Docker & Docker Compose
- Route 53
- S3 (optional)

---

## 🔄 System Workflow

1. User logs in to DeployX dashboard
2. User adds GitHub repo + config
3. DeployX automatically creates a GitHub webhook
4. User pushes code → GitHub triggers webhook
5. Build server:
   - Clones repo
   - Installs dependencies
   - Builds app
   - Builds Docker image
   - Runs container on EC2
6. Backend stores deployment info
7. Frontend shows updated deployment logs & URL

---

## 📁 Project Structure

```
deployx/
│
├── backend/
│   ├── src/
│   │   ├── routes/
│   │   ├── controllers/
│   │   ├── models/
│   │   ├── services/
│   │   └── index.js
│   └── package.json
│
├── frontend/
│   ├── src/
│   ├── public/
│   └── package.json
│
└── services/
    └── build-server/
```

---

## 🚀 Getting Started

### Prerequisites
- Node.js v16+
- Docker & Docker Compose
- MongoDB or PostgreSQL
- AWS Account
- GitHub Account

### 1. Clone Repository

```bash
git clone https://github.com/vanyasharma07/DeployX.git
cd DeployX
```

### 🛠 Backend Setup

```bash
cd backend
npm install
cp .env.example .env
npm start
```

**Environment Variables:**

```env
PORT=3000
MONGO_URI=your-db-uri
```

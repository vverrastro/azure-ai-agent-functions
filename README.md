# Azure AI Agent with function

This project demonstrates how to build a simple technical support AI Agent using the **Azure AI Foundry Agent Service** in Python.
The agent collects user input about technical issues and automatically generates support tickets using custom function tools.

---

## ✅ Features

* Interactive command-line AI agent.
* Uses **custom functions** to generate support tickets.
* Stateful conversation with full history tracking.
* Automatic cleanup of agents and threads.
* Saves support tickets as text files in the project folder.

---

## 🔧 Requirements

* Python 3.9+
* An **Azure subscription** with access to Azure AI Foundry
* A deployed **GPT-4o** model in your Azure AI Foundry project
* Azure CLI installed for authentication (`az login`)

---

## 📁 Project Structure

```
.
├── agent.py              # Main application file
├── user_functions.py     # Custom functions for the agent (submit support tickets)
├── requirements.txt      # Python dependencies
├── .env                  # Configuration file with project settings
```

---

## Setup

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd <project-folder>
```

### 2. Create and activate a virtual environment

```bash
python -m venv labenv
```

**Windows PowerShell**

```bash
./labenv/Scripts/Activate.ps1
```

**macOS/Linux**

```bash
source labenv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure environment variables

Create or edit the `.env` file with the following:

```
PROJECT_ENDPOINT="your_project_endpoint_here"
MODEL_DEPLOYMENT_NAME="your_model_deployment_name_here"
```

Replace the placeholder values with your Azure AI Foundry project details.

---

## Run the Application

1. Sign in to Azure:

```bash
az login
```

2. Start the agent:

```bash
python agent.py
```

3. When prompted, enter a text describing your technical issue.
   Example:

```
I have a technical problem with my laptop
```

4. The agent may ask for your email address and a description of the issue.
   Example:

```
Email: alex@contoso.com
Issue: My computer won't start
```

5. The agent will generate a support ticket and display the file name.
   Tickets are saved as `ticket-<ticket_number>.txt` in the project folder.

6. Continue the conversation or type `quit` to end the session.

---

## 🗂️ Conversation Log

At the end of the session, the application prints the **full conversation history** in chronological order.

---

## 📂 Example Support Ticket

A generated ticket will look like this:

```
Support ticket: 1a2b3c
Submitted by: alex@contoso.com
Description:
My computer won't start
```

---

## Cleanup

To avoid unnecessary Azure resource usage:

1. Open the Azure portal: [https://portal.azure.com](https://portal.azure.com)
2. Navigate to the resource group containing your AI Foundry resources.
3. Delete the resource group to remove all associated resources.
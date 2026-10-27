# Banking Customer Resolution System

A multi-agent AI workflow that analyzes a banking customer query, considers relevant policy guidance, drafts a customer-facing response, and determines whether the case should be escalated.

The workflow uses four specialized agents coordinated in sequence with CrewAI and a locally hosted Mistral model through Ollama.

## Features

- **Intent classification:** Categorizes the customer's issue and identifies urgency, fraud indicators, and risk level.
- **Policy reasoning:** Applies the policy rules supplied in the workflow to recommend verification and resolution steps.
- **Response generation:** Drafts a professional response with an explanation and next steps.
- **Risk and escalation assessment:** Determines whether the issue should be escalated and provides justification.
- **Sequential orchestration:** Passes relevant context between agents so later steps can use earlier results.

## Technology stack

- Python
- [CrewAI](https://www.crewai.com/) for multi-agent orchestration
- [Ollama](https://ollama.com/) for local model serving
- Mistral model (`mistral`)
- `langchain-ollama` integration

## Repository contents

- `banking_customer_resolution_system.ipynb` — notebook containing the workflow implementation.
- `README.md` — project overview and setup instructions.
- `requirements.txt` — Python dependencies.
- `.gitignore` — ignores common local development files.

## Prerequisites

1. Install Python in a version supported by the CrewAI release you install.
2. Install Ollama from [ollama.com](https://ollama.com/).
3. Download the Mistral model:

   ```bash
   ollama pull mistral
   ```

4. Ensure Ollama is running and available at `http://localhost:11434`.

## Setup

Create a virtual environment from the project directory.

### Windows PowerShell

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
jupyter notebook
```

Open `banking_customer_resolution_system.ipynb` and run the cells in order.

## Workflow

```text
Customer query
      |
      v
Intent Classification Agent
      |
      v
Banking Policy Agent
      |
      v
Response Generation Agent
      |
      v
Risk & Escalation Agent
      |
      v
Resolution response + escalation decision
```

## Important limitations

- This is a demonstration workflow, not a real banking service or source of authoritative financial advice.
- The policy rules are illustrative and hard-coded in the notebook; they are not a substitute for a bank's approved procedures or regulatory review.
- Model output can be incorrect or inconsistent. Human review is required before any real customer communication or account action.
- Do not submit real customer information, account numbers, credentials, or other sensitive financial data to the workflow.
- The notebook currently uses a fixed example customer query. Modify the query in the notebook to experiment with other non-sensitive scenarios.

## Possible future improvements

- Add structured output validation and error handling.
- Add test cases for different issue categories and escalation scenarios.
- Separate agent configuration from workflow code.
- Add audit logging that avoids storing sensitive customer data.
- Add a human-review step before a response is considered final.

# AI-Driven Structured Data Retrieval Agent
Agentic AI workflow using n8n and Gemini Pro to query structured student data via natural language.

🎯 Objective:

To engineer an Agentic AI Workflow that translates Natural Language (NL) queries into precise data retrieval operations. The system interprets user intent to filter and extract specific records from a structured student dataset.

🏗️ Technical Architecture:

The project follows a Modular Parent-Child Design for enhanced scalability and debugging:
Primary Agent (Main): Orchestrates the Reasoning Loop. It utilizes Gemini Pro to parse incoming queries from Chat or Webhook triggers.
Data Controller (Sub-workflow): Acts as the Integration Layer. It fetches raw data from the source, allowing the Main Agent to remain data-agnostic.
Tool Calling: The AI Agent is configured to dynamically trigger the sub-workflow only when data retrieval is required to answer a prompt.

🛠️ Key Features & Keywords
Natural Language Understanding (NLU): Maps conversational queries (e.g., "Who topped NLP?") to logical data filters.
Agentic Reasoning: Uses Chain-of-Thought to determine which subject columns and score thresholds to analyze.
Modular Design (DRY): Decoupled logic ensures the database connector can be updated without modifying the AI brain.
Zero-Shot Extraction: No hard-coded SQL/Regex; the LLM generates the filtering logic on-the-fly.

⚙️ Setup & Deployment
Import: Load Main_Workflow.json and Sub_Workflow.json into n8n.
Linking: Set the Execute Workflow node in the Main canvas to reference the Sub-workflow's unique ID.

API Configuration: Connect the Google Gemini Chat Model using a valid API Key.

Dataset: Ensure the Sub-workflow's HTTP/File node points to the provided student_records CSV/Excel file.

📊 Performance Demonstration
The following execution trace confirms a successful end-to-end cycle: Trigger → Intent Parsing → Sub-workflow Execution → Natural Language Synthesis.

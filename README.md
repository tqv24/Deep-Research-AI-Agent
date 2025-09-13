# Deep Research Assistant

An intelligent AI-powered research tool that automatically conducts comprehensive research on any topic and generates detailed reports. Built with a multi-agent architecture using OpenAI's models and featuring a sleek Gradio web interface.

![alt text](<image.png>)

## Features

- **Multi-Agent Architecture**: Utilizes specialized AI agents working together to deliver comprehensive research
- **Automated Research Pipeline**: From planning to execution to reporting - fully automated
- **Web Search Integration**: Performs intelligent web searches with strategic query planning
- **Detailed Report Generation**: Creates comprehensive markdown reports (1000+ words, 5-10 pages)
- **Email Integration**: Automatically sends formatted HTML reports via SendGrid
- **Real-time Progress Tracking**: Live updates during the research process
- **Modern Web Interface**: Clean, responsive Gradio interface with sky theme

## Architecture

The application uses a sophisticated multi-agent system:

1. **Planner Agent** (`planner_agent.py`): Analyzes the research query and generates strategic web search plans
2. **Search Agent** (`search_agent.py`): Executes web searches and produces concise summaries of findings
3. **Writer Agent** (`writer_agent.py`): Synthesizes research into comprehensive, well-structured reports
4. **Email Agent** (`email_agent.py`): Formats and sends professional HTML email reports
5. **Research Manager** (`research_manager.py`): Orchestrates the entire research workflow

## How It Works

1. **Input**: User provides a research topic through the web interface
2. **Planning**: The Planner Agent creates a strategic search plan with 5 targeted queries
3. **Research**: The Search Agent performs parallel web searches and summarizes findings
4. **Writing**: The Writer Agent synthesizes all research into a detailed markdown report
5. **Delivery**: The Email Agent formats and sends the report via email
6. **Output**: Final report is displayed in the web interface

## Prerequisites

- Python 3.8+
- OpenAI API key
- SendGrid API key (for email functionality)
- Required Python packages (see installation)

## Installation

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd llm-deep_research
   ```

2. **Install dependencies**:
   ```bash
   pip install gradio python-dotenv sendgrid agents
   ```

3. **Set up environment variables**:
   Create a `.env` file in the root directory:
   ```env
   OPENAI_API_KEY=your_openai_api_key_here
   SENDGRID_API_KEY=your_sendgrid_api_key_here
   ```

4. **Configure email settings**:
   Edit `src/email_agent.py` to update sender and recipient email addresses:
   ```python
   from_email = Email("your-verified-sender@example.com")
   to_email = To("recipient@example.com")
   ```

## Usage

1. **Start the application**:
   ```bash
   python main.py
   ```

2. **Access the web interface**:
   - The application will automatically open in your default browser
   - Alternatively, navigate to the provided local URL (usually `http://127.0.0.1:7860`)

3. **Conduct research**:
   - Enter your research topic in the text field
   - Click "Run" or press Enter
   - Watch real-time progress updates
   - View the comprehensive report when complete

## Example Output

The system generates:
- **Comprehensive Reports**: 1000+ word markdown reports with proper structure
- **Executive Summary**: 2-3 sentence key findings summary
- **Follow-up Questions**: Suggested areas for further research
- **Email Delivery**: Professional HTML-formatted email reports

## Configuration

### Model Settings
- Default model: `gpt-4o-mini` (configurable in agent files)
- Search context: Low (optimized for efficiency)
- Tool choice: Required for search agent

### Search Configuration
- Number of searches: 5 (configurable in `planner_agent.py`)
- Parallel search execution for faster results
- Graceful error handling for failed searches

## Project Structure

```
llm-deep_research/
├── main.py                 # Gradio web interface and entry point
├── README.md              # Project documentation
├── .env                   # Environment variables (create this)
└── src/
    ├── research_manager.py    # Main orchestration logic
    ├── planner_agent.py      # Search planning agent
    ├── search_agent.py       # Web search and summarization
    ├── writer_agent.py       # Report generation
    └── email_agent.py        # Email delivery
```

## Tracing and Debugging

The application includes OpenAI trace integration for debugging:
- Each research session generates a unique trace ID
- Trace URL is displayed in the interface for detailed execution analysis
- Access traces at: `https://platform.openai.com/traces/trace?trace_id=<trace_id>`

🎓 EduMind AI Tutor
An intelligent, multi-modal AI tutoring system powered by Groq's Llama 4 that helps students learn across all subjects through interactive chat, document analysis, and image understanding.

Python Streamlit Groq

📋 Table of Contents
Features
Demo
Installation
Usage
Project Structure
API Configuration
Technologies Used
Group Members
Troubleshooting
License
✨ Features
🎯 Core Capabilities
📄 PDF Processing: Upload and analyze PDF documents with automatic text extraction
🖼️ Image Analysis: Visual understanding through multi-modal AI capabilities
💬 Intelligent Chat: Contextual conversations with study material awareness
📚 Multi-Subject Support: Expert tutoring across science, math, history, law, engineering, arts, and more
✏️ Manual Text Input: Paste your own notes and study materials
🧠 Context Management: Maintains conversation history and uploaded content context
🎨 User Experience
Beautiful gradient-based dark UI with smooth animations
Real-time chat interface with user/AI message distinction
Active context tracking with visual badges
Mobile-responsive design
Progress indicators and status updates
🎬 Demo
The application provides:

Upload Interface: Drag-and-drop or browse for PDFs and images
Chat Interface: Ask questions about uploaded materials or general topics
Context Display: See all active study materials at a glance
Real-time Responses: Fast AI-powered answers using Groq's infrastructure
🚀 Installation
Prerequisites
Python 3.8 or higher
Google Colab account (for notebook execution)
Groq API Key (Get one here)
Step-by-Step Setup
Option 1: Google Colab (Recommended)
Open the edumind_ai_tutor.py file in Google Colab
Execute the cells in order:
Cell 1 - Install Dependencies

# Installs all required libraries
!pip install -q streamlit pyngrok pymupdf Pillow google-generativeai langchain...
Cell 2 - Configure Groq API

# Enter your Groq API key securely
!pip install -q groq
import getpass, os
GROQ_API_KEY = getpass.getpass('Groq API Key: ')
Cell 3 - Generate Application

# Creates the Streamlit app.py file
# Also sets up Cloudflare tunnel for public access
Cell 3b - Save API Key

# Saves API key to file for Streamlit access
Cell 4 - Start Tunnel

# Launches Cloudflare tunnel
# Displays public URL for accessing the app
Cell 5 - Launch App

# Starts the Streamlit server
!streamlit run app.py --server.port 8501
Option 2: Local Installation
# Clone or download the project
git clone <your-repo-url>
cd edumind-ai-tutor

# Install dependencies
pip install streamlit groq pymupdf Pillow langchain langchain-community faiss-cpu sentence-transformers pypdf

# Set environment variable
export GROQ_API_KEY="your-api-key-here"

# Run the app
streamlit run app.py
💡 Usage
Basic Workflow
Launch the Application

Execute all cells in order in Google Colab
Access the public URL provided by Cloudflare tunnel
Upload Study Materials

Click "📄 Upload PDF(s)" to add documents
Click "🖼️ Upload Image(s)" to add visual content
Or paste text directly in the text area
Ask Questions

Type your question in the chat input
Reference uploaded materials: "Summarize this PDF"
Ask general questions: "Explain Newton's laws"
Request explanations: "How does photosynthesis work?"
Review Responses

AI responses appear with 🎓 icon
Your questions show with 🧑‍🎓 icon
Context badges show active materials
Manage Context

View active materials in the sidebar
Click "🗑️ Clear All Context" to reset
Example Questions
📚 Subject-Specific:
- "Explain the Pythagorean theorem with examples"
- "What are the main causes of World War II?"
- "How do I solve quadratic equations?"

📄 Document-Based:
- "Summarize the key points from this PDF"
- "What is the main argument in this text?"
- "Extract the important formulas from the document"

🖼️ Image-Based:
- "Explain this diagram"
- "What equation is shown in this image?"
- "Describe this scientific illustration"
📁 Project Structure
edumind-ai-tutor/
│
├── edumind_ai_tutor.py     # Main Colab notebook (5 cells)
├── app.py                   # Generated Streamlit application
├── api_key.txt              # Groq API key storage (auto-generated)
├── cloudflared              # Tunnel binary (auto-downloaded)
└── README.md                # This file
Key Components
edumind_ai_tutor.py

Cell 1: Dependency installation
Cell 2: API key configuration
Cell 3: App generation + tunnel setup
Cell 3b: API key persistence
Cell 4: Tunnel launch (displays URL)
Cell 5: Streamlit server launch
app.py (Auto-generated)

Streamlit UI configuration
Groq client initialization
File upload handlers (PDF, images)
Chat interface and message management
Context tracking and display
AI response generation
🔑 API Configuration
Getting a Groq API Key
Visit Groq Console
Sign up or log in
Navigate to API Keys section
Create a new API key
Copy the key (starts with gsk_...)
Setting the API Key
In Colab:

# Cell 2 prompts for secure input
GROQ_API_KEY = getpass.getpass('Groq API Key: ')
In Local Environment:

# Linux/Mac
export GROQ_API_KEY="gsk_your_key_here"

# Windows (CMD)
set GROQ_API_KEY=gsk_your_key_here

# Windows (PowerShell)
$env:GROQ_API_KEY="gsk_your_key_here"
🛠️ Technologies Used
Core Framework
Streamlit - Web application framework
Groq - Ultra-fast LLM inference platform
Llama 4 Scout 17B - Groq's flagship language model
Document Processing
PyMuPDF (fitz) - PDF text extraction
Pillow - Image processing
pypdf - PDF utilities
AI & ML
LangChain - LLM application framework
FAISS - Vector similarity search
Sentence Transformers - Text embeddings
Infrastructure
Cloudflare Tunnel - Secure public URL tunneling
Base64 - Image encoding for API transmission
👥 Group Members
Group 1 - AI Tutor Project

Vishav Bhan Singh Parmar (Lead Developer)
Adarsh Sharma
Mayank Singh Pathania
Dinesh Mandela
Saksham Neb
🐛 Troubleshooting
Common Issues
Problem: "Groq API key not found"

Solution: Ensure Cell 2 was executed and API key was entered correctly
Check that api_key.txt file exists with the key
Problem: "Module not found" errors

Solution: Re-run Cell 1 to install all dependencies
Restart runtime if needed: Runtime → Restart runtime
Problem: Tunnel URL not appearing

Solution: Wait 10-15 seconds after Cell 4
Check Cell 4 output for the Cloudflare URL
Problem: Slow responses

Solution: Groq is generally very fast (< 2 seconds)
Check your internet connection
Verify API key has sufficient quota
Problem: PDF not loading

Solution: Ensure PDF is not password-protected
Try smaller PDFs (< 10MB recommended)
Check file is valid PDF format
Problem: Images not analyzing

Solution: Llama 4 Scout supports image analysis
Ensure images are PNG/JPG/JPEG/WEBP format
Try smaller images if timeout occurs
📝 How It Works
Architecture Overview
User Input (Question + Context)
         ↓
Streamlit Interface
         ↓
Context Assembly:
  - PDF text extraction
  - Image base64 encoding
  - Manual text addition
         ↓
Groq API Call
  - Model: Llama 4 Scout 17B
  - System prompt: Expert tutor
  - Context: Study materials
  - History: Previous messages
         ↓
AI Response Generation
         ↓
Display in Chat UI
Context Management
PDFs are converted to text and stored in session state
Images are base64-encoded and sent with each request
Chat history maintains last 6 messages for continuity
Context is truncated to 12,000 characters for performance
🎨 UI Features
Design Elements
Gradient backgrounds with smooth animations
Floating cards for feature display
Shimmer effects on hero title
Pulse animations on buttons
Slide-in transitions for messages
Custom badges for active context
Color Scheme
Primary: Indigo/Purple gradient (#6366f1 → #8b5cf6)
Secondary: Cyan accent (#06b6d4)
Background: Deep purple/navy (#0f0c29 → #1a1040)
Text: Slate shades for readability
🚦 Future Enhancements
Potential improvements:

 Add voice input/output
 Support for more file formats (DOCX, PPTX)
 Advanced RAG with vector database
 Multi-language support
 Export chat history
 Custom tutor personalities
 Quiz generation from materials
 Progress tracking dashboard
📄 License
This project was created as an academic assignment. Contact group members for usage permissions.

🙏 Acknowledgments
Groq for providing ultra-fast LLM inference
Meta for the Llama 4 model
Streamlit for the amazing web framework
Cloudflare for secure tunneling
📞 Support
For issues, questions, or contributions:

Open an issue on the repository
Contact group members directly
Check Groq documentation: https://console.groq.com/docs
Made with ❤️ by Group 1 | Powered by Groq + Llama 4

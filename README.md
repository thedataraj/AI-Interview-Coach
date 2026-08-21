# AI Interview Coach

An AI-powered mock interview application built with Python and Streamlit that helps candidates practice technical and behavioral interviews in an interactive environment.

The project combines Generative AI, voice interaction, role-specific interview questions, and structured performance feedback to create a realistic interview preparation experience. Instead of simply displaying a list of interview questions, the application guides the candidate through a complete interview session and provides AI-generated coaching based on the candidate's responses.

The application was designed and developed by Raj Singh as a practical project focused on applying Generative AI to interview preparation and career development.

---
## Live Demo

Try the deployed application:

[Launch AI Interview Coach](https://interviewcoachpro.streamlit.app/)

Note: The Streamlit Community Cloud app may temporarily go to sleep after a period of inactivity. If the app is sleeping, click "Yes, get this app back up!" to start it again.

You can use the application to select a target role, practice HR and domain-specific interview questions, listen to questions using text-to-speech, record responses, receive AI-powered coaching feedback, and generate a final interview performance report.

## Project Overview

Preparing for interviews is often difficult because candidates can study technical concepts but still struggle with answering questions clearly, handling pressure, organizing their thoughts, or communicating their experience effectively.

This project attempts to address that problem by creating an interactive AI interview environment.

The application allows a candidate to select a target role and start a structured mock interview. The system combines a set of core HR questions with questions specific to the selected professional domain.

During the session, the application:

1. Selects a set of interview questions.
2. Presents the questions one by one.
3. Reads the question using text-to-speech.
4. Allows the candidate to record an answer using the microphone.
5. Sends the interview context to a Generative AI model.
6. Generates coaching feedback.
7. Maintains a session transcript.
8. Moves the candidate through the interview automatically.
9. Generates a final performance report at the end of the session.

The goal is to make interview practice more interactive and closer to an actual interview rather than relying only on static question-and-answer preparation.

---

## Key Features

### 1. Role-Based Interview Practice

The application supports multiple professional domains.

Current question banks include roles such as:

* Data Analyst
* Business Analyst
* MIS Analyst / MIS Executive
* Power BI / BI Analyst
* SQL / Database Analyst
* Financial Analyst
* Marketing Analyst
* Operations Analyst
* Product Analyst
* HR / People Analyst
* GEN-AI Developer

Each role has its own domain-specific question pool.

This makes the interview experience more relevant to the position the candidate is preparing for.

---

### 2. Core HR Interview Questions

Every interview session includes a dedicated HR section.

The application contains standard behavioral questions covering topics such as:

* Introduction and background
* Strengths and weaknesses
* Career goals
* Conflict management
* Stress management
* Teamwork
* Leadership
* Time management
* Handling criticism
* Stakeholder management
* Problem solving
* Adaptability
* Workplace communication
* Professional development
* Handling difficult situations

The project also randomly selects additional HR questions so that repeated interview sessions do not necessarily follow exactly the same sequence.

---

### 3. Randomized Interview Sessions

The application does not use the same fixed set of questions for every session.

A predefined group of core HR questions is combined with randomly selected HR questions and randomly selected domain-specific questions.

For each session, the application selects:

* 5 fixed HR questions
* 10 additional HR questions
* Up to 15 domain-specific questions

This gives the candidate a different interview experience each time they start or shuffle a session.

The application also provides a "Shuffle & Start New Session" option that resets the session and creates a new question set.

---

## Voice-Based Interview Experience

One of the main objectives of this project was to move beyond a traditional text-based interview interface.

The application uses text-to-speech to read interview questions aloud. The question is converted into audio using the `gTTS` library and played directly inside the Streamlit application.

Candidates can then use the microphone interface provided by Streamlit to record their response.

This creates a more realistic interview flow:

```text
AI asks question
       |
       v
Candidate listens
       |
       v
Candidate speaks answer
       |
       v
Answer submitted
       |
       v
AI evaluates response
       |
       v
Coaching feedback
       |
       v
Next question
```

The voice interaction makes the project particularly useful for candidates who want to practice speaking rather than simply typing answers.

---

## Generative AI Integration

The project uses the Groq API to generate interview coaching and post-session analysis.

The configured model in the current implementation is:

```text
openai/gpt-oss-20b
```

The application initializes the Groq client using the `GROQ_API_KEY` environment variable or Streamlit secrets.

For each interview response, the application sends contextual information including:

* Target role
* Interview question
* Candidate answer

The AI then generates direct coaching feedback based on the response.

This approach allows the same application structure to support different professional roles without requiring a separate application for each role.

---

## Interview Session Structure

A typical session follows this structure:

### Step 1: Select a Target Role

The candidate selects the role they are preparing for from the sidebar.

For example:

```text
Data Analyst
Business Analyst
MIS Analyst / MIS Executive
Power BI / BI Analyst
SQL / Database Analyst
Financial Analyst
Marketing Analyst
Operations Analyst
Product Analyst
HR / People Analyst
GEN-AI Developer
```

### Step 2: Generate the Question Set

The application creates a session-specific question set using the selected role.

The question bank combines HR questions with domain-specific questions.

### Step 3: Start the Interview

The first question is displayed on the main interface.

The application also displays session progress so the candidate can see how far they are through the interview.

### Step 4: Listen to the Question

The question is converted to audio using gTTS and played within the application.

### Step 5: Record the Answer

The candidate records a response using the Streamlit audio input component.

### Step 6: Submit the Answer

The recorded response is submitted for coaching.

### Step 7: Generate AI Feedback

The response is passed to the Groq-powered coaching function along with the question and selected role.

### Step 8: Continue the Interview

After the feedback is generated, the application moves to the next question.

### Step 9: Review the Transcript

The session transcript contains the interview interaction and AI coaching feedback.

### Step 10: Generate the Final Report

Once the candidate has completed the session, they can generate a structured performance report.

---

## Performance Report Card

The application includes a final report generation feature that analyzes the interview transcript.

The report is designed around the following sections:

```text
OVERALL SCORE
TOP 3 STRENGTHS
TOP 3 AREAS TO IMPROVE
HR VS TECHNICAL PERFORMANCE SUMMARY
ONE PRIORITY ACTION
```

The purpose of this report is to provide a concise summary of the candidate's overall interview performance rather than requiring them to manually review every individual response.

The report generation function passes the complete interview transcript and target role to the Generative AI model and requests a structured post-session evaluation.

---

## Live Transcript

The application maintains the interview conversation inside Streamlit session state.

The transcript records both candidate responses and AI coaching feedback.

This allows the candidate to review the interview session while progressing through the questions.

The transcript concept also provides a foundation for future features such as:

* Interview history
* Response comparison
* Performance tracking
* Question-level scoring
* Session analytics
* Personalized improvement plans

---

## User Interface

The application uses Streamlit for the user interface.

The interface includes:

* Sidebar configuration
* Target role selection
* Session summary
* Question progress
* Active interview category
* Interview question display
* Audio playback
* Voice recording
* Live transcript
* AI coaching feedback
* Final performance report

Custom CSS is also used to create metric cards, question containers, feedback sections, and role/category badges.

The objective was to make the application feel more like an actual interview tool rather than a basic Python demonstration.

---

## Technology Stack

### Programming Language

**Python**

Python is used for the core application logic, question management, session handling, API integration, and application workflow.

### Frontend / Application Framework

**Streamlit**

Streamlit provides the interactive web interface and handles:

* User inputs
* Audio recording
* Session state
* Progress indicators
* Tabs
* Buttons
* Audio playback
* Dynamic content

### Generative AI

**Groq API**

Groq is used to generate interview coaching feedback and the final performance report.

### Language Model

The current configuration uses:

```text
openai/gpt-oss-20b
```

### Text-to-Speech

**gTTS**

gTTS converts interview questions into spoken audio so that candidates can listen to the questions instead of only reading them.

### Supporting Python Libraries

The project uses libraries including:

```text
streamlit
groq
gtts
```

Additional Python standard-library modules such as `io`, `random`, and `os` are also used.

---

## Project Architecture

The project follows a relatively simple architecture designed around a Streamlit application.

```text
                +----------------------+
                |      Streamlit UI    |
                +----------+-----------+
                           |
                           v
                +----------------------+
                |   Role Selection      |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | Question Bank Engine |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | Interview Session    |
                +----------+-----------+
                           |
             +-------------+-------------+
             |                           |
             v                           v
      +-------------+             +-------------+
      |   gTTS      |             | Voice Input |
      | Text Speech |             |  Recording  |
      +-------------+             +------+------+
                                          |
                                          v
                                +------------------+
                                |    Groq API      |
                                | Generative AI    |
                                +--------+---------+
                                         |
                                         v
                                +------------------+
                                | Coaching Feedback|
                                +--------+---------+
                                         |
                                         v
                                +------------------+
                                | Session Transcript|
                                +--------+---------+
                                         |
                                         v
                                +------------------+
                                | Performance Report|
                                +------------------+
```

---

## Project Structure

A recommended GitHub repository structure is:

```text
AI-Interview-Coach/
│
├── app.py
├── README.md
├── requirements.txt
├── .gitignore
│
└── .streamlit/
    └── secrets.toml
```

If you keep the project in a single Python file, `app.py` contains the main application logic, question banks, UI configuration, AI integration, session management, voice functionality, and report generation.

As the project grows, the question banks and utility functions can be separated into individual modules.

For example:

```text
AI-Interview-Coach/
│
├── app.py
├── questions/
│   ├── hr_questions.py
│   ├── analyst_questions.py
│   ├── powerbi_questions.py
│   └── genai_questions.py
│
├── utils/
│   ├── ai_coach.py
│   ├── report_generator.py
│   └── speech.py
│
├── requirements.txt
├── README.md
└── .gitignore
```

This structure would make the application easier to maintain as more interview domains and features are added.

---

## Installation

### 1. Clone the Repository

```bash
https://github.com/thedataraj/AI-Interview-Coach.git
```

Move into the project directory:

```bash
cd AI-Interview-Coach
```

### 2. Create a Virtual Environment

Creating a virtual environment is recommended so that project dependencies remain isolated.

On Windows:

```bash
python -m venv venv
```

Activate it:

```bash
venv\Scripts\activate
```

On macOS or Linux:

```bash
python3 -m venv venv
```

Activate it:

```bash
source venv/bin/activate
```

### 3. Install Dependencies

Install the required packages:

```bash
pip install -r requirements.txt
```

If you have not created a `requirements.txt` file yet, the main dependencies used by the project include:

```text
streamlit
groq
gTTS
```

---

## API Key Configuration

The application requires a Groq API key to generate AI coaching feedback.

Do not hard-code your API key directly inside the Python source code.

The application is designed to retrieve the API key from either Streamlit secrets or an environment variable:

```python
groq_api_key = st.secrets.get(
    "GROQ_API_KEY",
    os.environ.get("GROQ_API_KEY")
)
```

This allows the same codebase to be used locally and in a deployment environment without exposing the secret in the source code.

---

## Local Secrets Configuration

For local Streamlit development, create:

```text
.streamlit/secrets.toml
```

Add:

```toml
GROQ_API_KEY = "your_groq_api_key_here"
```

Replace the placeholder with your actual API key.

Make sure the secrets file is included in `.gitignore`.

Example:

```gitignore
.streamlit/secrets.toml
.env
venv/
__pycache__/
*.pyc
```

Never commit your actual API key to GitHub.

If an API key is accidentally exposed publicly, revoke it and generate a new one.

---

## Running the Application

Once the dependencies and API key have been configured, run:

```bash
streamlit run app.py
```

Streamlit will start the application locally.

Open the local URL displayed in the terminal, usually:

```text
http://localhost:8501
```

---

## How to Use the Application

After launching the application:

### 1. Select Your Target Role

Use the sidebar to select the professional role you want to practice.

### 2. Review the Session Summary

The sidebar displays the number of HR and domain-specific questions selected for the session.

### 3. Start the Interview

The application displays the first question.

### 4. Listen to the Question

Use the generated audio to listen to the question.

### 5. Record Your Answer

Use the microphone input to record your response.

### 6. Submit the Response

Submit your recorded answer for AI coaching.

### 7. Read the Feedback

The AI-generated feedback appears in the session transcript.

### 8. Continue

The application automatically moves through the remaining questions.

### 9. Generate Your Report

After completing the interview, generate the final report card to review your overall performance.

---

## Interview Question Coverage

The project contains a large collection of questions across different analytical, business, technical, financial, marketing, operations, product, HR, and Generative AI domains.

Examples of Data Analyst topics include:

* SQL joins
* Window functions
* Data cleaning
* Pandas
* Data normalization
* EDA
* Statistical analysis
* A/B testing
* Cohort analysis
* RFM segmentation
* Data visualization
* Power BI
* DAX
* ETL
* Data governance
* Query optimization
* Time-series analysis
* Business metrics

The Business Analyst section covers areas such as:

* Requirements gathering
* Requirements elicitation
* Stakeholder management
* User stories
* Acceptance criteria
* Process mapping
* Gap analysis
* Root-cause analysis
* BRD and FRD
* Agile
* Scrum
* UAT
* Business cases
* ROI
* Risk management
* Process improvement

The Power BI section includes topics such as:

* Data modeling
* Star schema
* DAX
* Measures
* Calculated columns
* Filter context
* Row context
* CALCULATE
* Time intelligence
* Power Query
* Query folding
* Incremental refresh
* Import and DirectQuery
* Row-level security
* Power BI Service
* Performance optimization

The SQL section covers:

* SQL fundamentals
* Joins
* Aggregations
* Window functions
* CTEs
* Subqueries
* NULL handling
* Database keys
* Indexes
* Views
* Transactions
* Query optimization
* Customer analysis
* Cohort analysis
* Retention analysis
* Advanced analytical SQL

The project also contains question banks for financial, marketing, operations, product, HR/People Analytics, and Generative AI roles.

---

## Generative AI Developer Interview Section

The Generative AI section is designed around modern AI and LLM concepts.

Topics include areas such as:

* Generative AI
* Large Language Models
* Tokens
* Tokenization
* Context windows
* Transformers
* Self-attention
* Multi-head attention
* GPT architecture
* BERT
* Pre-training
* Fine-tuning
* Instruction tuning
* RLHF
* Prompt engineering
* System prompts
* User prompts
* Zero-shot prompting
* Few-shot prompting

This section is intended to help candidates prepare for entry-level and intermediate Generative AI interviews.

---

## Session State Management

Streamlit session state is used to maintain important information during the interview.

The application tracks values such as:

```text
current_question_idx
selected_hr_questions
selected_domain_questions
active_role
transcript
report
```

This allows the interview to continue across Streamlit interactions without losing the current session state.

When a new role is selected or a new session is started, the relevant session information is reset and a new question set is generated.

---

## AI Coaching Workflow

The coaching process can be summarized as:

```text
Question
   |
   v
Candidate Response
   |
   v
Role + Question + Answer
   |
   v
Groq API
   |
   v
Generative AI Model
   |
   v
Coaching Feedback
   |
   v
Session Transcript
```

The coaching function constructs a prompt containing the target role, interview question, and candidate answer before sending it to the configured Groq model.

---

## Final Evaluation Workflow

At the end of the interview, the complete transcript is formatted and sent to the AI model for analysis.

The generated report focuses on:

* Overall performance
* Strengths
* Improvement areas
* HR versus technical performance
* Most important improvement action

This provides the candidate with a consolidated view of the interview rather than requiring them to manually analyze every response.

---

## What I Learned From This Project

Building this project helped me work with several practical areas of modern application development.

### Generative AI Integration

I learned how to integrate an external LLM API into a Python application and use structured prompts to generate role-specific interview feedback.

### Prompt Design

The quality of AI feedback depends heavily on the context provided to the model. Structuring the prompt around the target role, question, candidate response, and desired feedback format makes the output more useful.

### Streamlit Application Development

The project provided practical experience with building an interactive Python web application using Streamlit.

### Session State

Managing interview progress required maintaining state across Streamlit interactions.

### Voice Interaction

Integrating audio playback and microphone input introduced another layer beyond traditional text-based applications.

### Dynamic Question Selection

Randomized question selection helped make the interview sessions less repetitive.

### User Experience

The project also required thinking about how a candidate would actually use the application, including progress indicators, question categories, transcripts, and final reporting.

---

## Current Limitations

This project is still a work in progress and there are several areas that can be improved.

One important limitation in the current implementation is that the recorded audio is represented in the transcript using a placeholder such as:

```text
[Live Voice Response Recorded for Question X]
```

The current coaching function therefore does not perform speech-to-text transcription of the recorded audio before sending the answer to the Groq model.

A future version can integrate a speech recognition or transcription model so that the actual spoken response is converted into text before AI evaluation.

Other areas for improvement include:

* More detailed answer scoring
* Dedicated speech-to-text integration
* Pronunciation analysis
* Speaking pace analysis
* Filler-word detection
* Confidence analysis
* Interview history
* User accounts
* Persistent performance tracking
* More detailed technical scoring
* Question difficulty levels
* Custom interview lengths
* Resume-based interview questions
* Job-description-based questions
* Personalized question generation
* Downloadable performance reports

---

## Future Improvements

I plan to continue improving the project by adding more realistic interview capabilities.

### Speech-to-Text

Integrate a dedicated speech recognition model so the application can convert spoken responses into text automatically.

### Better Answer Evaluation

Instead of only generating general coaching feedback, future versions can score individual dimensions such as:

```text
Technical Accuracy
Communication
Structure
Relevance
Confidence
Completeness
Problem Solving
```

### Resume-Based Interviews

A future version could allow users to upload their resume and automatically generate questions based on:

* Skills
* Projects
* Work experience
* Certifications
* Education
* Technologies

### Job Description Integration

The system could accept a job description and create an interview specifically tailored to that position.

### Difficulty Levels

Interview sessions could be divided into:

```text
Beginner
Intermediate
Advanced
Expert
```

### Performance History

A database could be added to track performance across multiple sessions.

For example:

```text
Session 1: 6.2/10
Session 2: 7.1/10
Session 3: 7.8/10
Session 4: 8.4/10
```

This would allow candidates to measure their improvement over time.

### Personalized Coaching

The application could identify repeated weaknesses and automatically focus future interview sessions on those areas.

---

## Why I Built This

I built this project because interview preparation is not only about knowing the correct answer.

A candidate also needs to practice:

* Thinking under pressure
* Explaining technical concepts
* Structuring answers
* Communicating clearly
* Handling behavioral questions
* Speaking confidently
* Responding to unexpected questions
* Understanding where their answers need improvement

Traditional interview preparation often involves reading questions and memorizing answers. I wanted to build something more interactive where the candidate can actually participate in an interview session.

This project is my attempt to combine data and AI skills with a practical career-focused application.

---

## Project Goals

The main goals of this project are:

1. Make interview preparation more interactive.
2. Provide role-specific interview practice.
3. Combine HR and technical interview preparation.
4. Introduce voice-based interview interaction.
5. Use Generative AI for personalized coaching.
6. Provide a structured final performance report.
7. Create a foundation for a more advanced AI interview platform.

---

## Technologies Used

| Technology    | Purpose                       |
| ------------- | ----------------------------- |
| Python        | Application development       |
| Streamlit     | Web application interface     |
| Groq API      | Generative AI integration     |
| GPT-OSS-20B   | AI interview coaching         |
| gTTS          | Text-to-speech                |
| Random        | Random question selection     |
| Session State | Interview progress management |
| HTML/CSS      | Custom interface styling      |

---

## Example Interview Flow

A typical session can look like this:

```text
User selects:
Data Analyst

        ↓

Application creates interview

        ↓

Core HR Questions

        ↓

Random HR Questions

        ↓

Data Analyst Questions

        ↓

AI reads question

        ↓

Candidate records answer

        ↓

AI generates coaching feedback

        ↓

Next question

        ↓

Interview completed

        ↓

Final Performance Report
```

---

## Repository Purpose

This repository is primarily a portfolio and learning project demonstrating how Python, Streamlit, Generative AI, and voice interfaces can be combined into a practical application.

It is also intended to serve as a foundation for future development.

The project can be extended into a more complete interview preparation platform with persistent user profiles, speech recognition, detailed analytics, resume parsing, job-description matching, and personalized interview plans.

---

## Author

**Raj Singh**

Data Analytics and Generative AI Enthusiast

I am interested in building practical applications using data analytics, business intelligence, automation, and Generative AI.

### Skills

* Python
* SQL
* Power BI
* Advanced Excel
* VBA
* Generative AI
* Data Analytics
* Business Intelligence
* Data Visualization

### Project Background

This AI Interview Coach was designed and developed by me as a practical project to combine my knowledge of Python, Data Analytics, Generative AI, Streamlit, and AI-powered application development.

The project reflects my interest in building practical solutions that solve real-world problems rather than limiting my work to theoretical learning.

### Connect With Me

**Name:** Raj Singh
**GitHub:** [thedataraj](https://github.com/thedataraj)
**LinkedIn:** [Raj Singh](https://www.linkedin.com/in/rajsingh1801/)
**Location:** Kolkata, India

---

**Built and developed by Raj Singh | Python | SQL | Power BI | Excel | Generative AI | Streamlit**

# Chat basis application_System instructions-Gemini

## Description
This is a project that utilizes [Google Gemini](https://cloud.google.com/generative-ai) for generative AI capabilities. It allows you to interact with models for various tasks like text generation, multi-turn conversations, role-based interactions, and code generation.

## Features
- Multi-turn chat conversations with system instructions.
- Role-based text generation for various professions (e.g., project manager, data engineer).
- Code generation to assist in building sample webpages and other front-end tasks.
- Text generation with customized system instructions to simulate specific roles or job functions.

## Requirements

- Google Colab (optional)
- Google Cloud API key for accessing the [Gemini API](https://cloud.google.com/generative-ai)

## Installation
### 1. Install the necessary libraries

Run the following command to install the required dependencies:

!pip install -qU 'google-generativeai>0.4.1

## Features
- Multi-turn chat conversations with system instructions.
- Role-based text generation for various professions (e.g., project manager, data engineer).
- Code generation to assist in building sample webpages and other front-end tasks.
- Text generation with customized system instructions to simulate specific roles or job functions.

## Requirements

- Google Colab (optional)
- Google Cloud API key for accessing the [Gemini API](https://cloud.google.com/generative-ai)

# 2. Set up the Google API Key

Enable the Generative AI API for your project.
Obtain the API key and store it securely.
In Colab, store your API key in the secrets manager or use the following code snippet to load it:

python
Copy code
from google.colab import userdata
GOOGLE_API_KEY = userdata.get('GOOGLE_API_KEY')

# 3. Configure the Gemini model
Set up and configure the google-generativeai SDK with your API key:

python
Copy code
import google.generativeai as GenAi

GenAi.configure(api_key=GOOGLE_API_KEY)
Usage

# Example 1: Role-Based Interaction (Project Manager)
python
Copy code
model = GenAi.GenerativeModel(
    "models/gemini-1.5-pro-latest",
    system_instruction="You are a project manager. Your name is Sathish."
)

response = model.generate_content("Can you give me your roles and responsibilities in your current project?")
print(response.text)

# Example 2: Multi-Turn Conversations
python
Copy code
chat = model.start_chat()
response = chat.send_message("How was your day?")
print(response.text)

response1 = chat.send_message("Do you feel stressed in your role?")
print(response1.text)

# Example 3: Code Generation
```bash
instruction = "You are a coding expert that specializes in front-end interfaces. Now build a sample webpage for students."
model = GenAi.GenerativeModel("models/gemini-1.5-pro-latest", system_instruction=instruction)
prompt = "Build a web interface for students to search their subjects with different color formats."
response = model.generate_content(prompt)
print(response.text)


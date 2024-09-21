# chatbot_gemini
A demo chatbot using gemini API and gradio library , using python

# Import the Python SDK
import gradio as gr
import google.generativeai as genai
# Used to securely store your API key
from google.colab import userdata
userdata.get('GOOGLE_API_KEY')

#api integration 
GOOGLE_API_KEY='<GOOGLE_API_KEY>' # Replace with your actual API key
genai.configure(api_key=GOOGLE_API_KEY)

# model specifications 
model = genai.GenerativeModel('gemini-1.5-flash')

#chat response
def get_text_response(user_message,history):
    response = model.generate_content(user_message)
    return response.text
    
#interface 
demo = gr.ChatInterface(get_text_response)

#launch 
if __name__ == "__main__":
    demo.launch() #To create a public link, set `share=True` in `launch()`. To enable errors and logs, set `debug=True` in `launch()`.

# WhatsApp Chatbot

Happy holi! this is a Flask blueprint that handles webhooks from the WhatsApp API. It provides endpoints for verifying the webhook and processing incoming WhatsApp messages aka a whatsapp-bot.

## Prerequisites

Before running the webhook handler, make sure you have the following prerequisites installed:

- Python 3.x
- Flask
- Any other required Python packages specified in the project
- openai (or any other gen ai model like gemini which i have also used here)

## Setup

1. Clone or download the repository to your local machine.
2. Set the following configuration variables in your Flask application:

```python
app.config["VERIFY_TOKEN"] = "<your_verify_token>"
```

Replace `<your_verify_token>` with the verification token provided by the WhatsApp API.

3. Register the `webhook_blueprint` with your Flask application:

```python
from webhook import webhook_blueprint

app.register_blueprint(webhook_blueprint)
```

4. Set up the appropriate routes and URLs in your Flask application to handle the webhook endpoints.

## Usage

1. Run your Flask application.
2. Configure the WhatsApp API to send webhooks to the appropriate endpoint (e.g., `https://your-domain.com/webhook`).
3. The webhook handler will verify the incoming requests and process any valid WhatsApp messages.

## Code Overview

The code consists of the following main components:

1. **Verification Endpoint**: The `webhook_get` function handles the GET request from the WhatsApp API for verifying the webhook. It checks the provided verification token and returns the challenge if the verification is successful.

2. **Message Processing Endpoint**: The `webhook_post` function handles the POST request from the WhatsApp API containing the WhatsApp message. It checks if the incoming request is a valid WhatsApp API event and processes the message accordingly.

3. **Message Validation**: The `is_valid_whatsapp_message` function checks if the incoming request is a valid WhatsApp API event.

4. **Message Processing**: The `process_whatsapp_message` function handles the processing of the incoming WhatsApp message. This function is not provided in the given code and needs to be implemented based on your specific requirements.

5. **Security Decorator**: The `signature_required` decorator is used to secure the `webhook_post` endpoint by verifying the request signature. This decorator is not provided in the given code and needs to be implemented based on your security requirements.


# WhatsApp Webhook Handler

## Configure Webhooks to Receive Messages

> Please note, this was very very hard (for me lol) and even more boring so i will suggest you to skip this  :sweat_smile:

### Start your app

- Make sure you have a Python installation or environment and install the requirements: `pip install -r requirements.txt`
- Run your Flask app locally by executing `run.py`

### Launch ngrok

The steps below are taken from the ngrok documentation.

> You need a static ngrok domain because Meta validates your ngrok domain and certificate!

Once your app is running successfully on localhost, let's get it on the internet securely using ngrok!

1. If you're not an ngrok user yet, sign up for ngrok for free.
2. Download the ngrok agent.
3. Go to the ngrok dashboard, click Your Authtoken, and copy your Authtoken.
4. Follow the instructions to authenticate your ngrok agent. You only have to do this once.
5. On the left menu, expand Cloud Edge and then click Domains.
6. On the Domains page, click "+ Create Domain" or "+ New Domain". (Here, everyone can start with one free domain.)
7. Start ngrok by running the following command in a terminal on your local desktop:

   ```
   ngrok http 8000 --domain your-domain.ngrok-free.app
   ```

   Replace `your-domain.ngrok-free.app` with the domain you created in step 6.

8. ngrok will display a URL where your localhost application is exposed to the internet (copy this URL for use with Meta).



   
## Testing

**Test-bot setup** (idk why the hi was not upperCase)

![ss1](https://github.com/Anushlinux/Whatsapp-chatbot/assets/77314503/72d8ace2-568b-45d3-8130-fc0f3d559a92)


**Intelligence check** (lol)

![ss2](https://github.com/Anushlinux/Whatsapp-chatbot/assets/77314503/91bd2d5e-5cb1-45da-ac7a-9f5fd1801ae1)



## Customization

You can customize the behavior of the webhook handler by modifying the following components:

- **Message Processing**: Implement the `process_whatsapp_message` function to handle the incoming WhatsApp messages according to your requirements.
- **Logging**: Adjust the logging statements or integrate a logging framework to suit your needs.

## Contributing

Contributions to this project are welcome. If you find any issues or have suggestions for improvements, please open an issue or submit a pull request.

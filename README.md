# OpenAI GPT-4o Audio Response Example
## Question for testing 
- Is a golden retriever a good family dog?
## Result
[Listen to the audio](dog.wav)



This project demonstrates how to use OpenAI's `GPT-4o` model to generate both text and audio responses. The script sends a question to OpenAI's API and saves the resulting `.wav` audio file.

## Prerequisites

- Python 3.8+
- OpenAI Python SDK
- An OpenAI API key

## Installation

1. Clone the repository or copy the script.
2. Install dependencies:
   ```sh
   pip install openai
   ```
3. Set up your OpenAI API key:
   ```sh
   export OPENAI_API_KEY="your-api-key-here"
   ```
   Or set it inside your script before creating the OpenAI client.

## Usage

Run the script to generate an audio response:

```sh
python script.py
```

## Example Code

```python
import base64
from openai import OpenAI

client = OpenAI()

completion = client.chat.completions.create(
    model="gpt-4o-audio-preview",
    modalities=["text", "audio"],
    audio={"voice": "alloy", "format": "wav"},
    messages=[
        {
            "role": "user",
            "content": "Is a golden retriever a good family dog?"
        }
    ]
)

print(completion.choices[0])

wav_bytes = base64.b64decode(completion.choices[0].message.audio.data)
with open("dog.wav", "wb") as f:
    f.write(wav_bytes)
```

## Output
- The text response is printed to the console.
- The audio response is saved as `dog.wav` in the same directory.

## License
This project is open-source under the MIT License.


# --- Define the First Agent (Topic Analysis) ---

```python

@ell.simple(model="llama3.2:3b", client=CLIENTS["ollama"], max_tokens=1000)

def analyze_topic(topic: str) -> str:

"""

You are a blog strategist. Use a system prompt and a user prompt to provide a concise analysis.

"""

system_prompt = "You are a blog strategist. Analyze the topic and return key insights."

user_prompt = f"Please analyze the topic: '{topic}'."

return [ell.system(system_prompt), ell.user(user_prompt)]

```


# --- Define the Storyteller Agent (Write Blog) ---

```python

@ell.complex(model="llama3.2:3b", client=CLIENTS["ollama"], temperature=0.5, max_tokens=1500)

def write_blog(topic: str, context: str) -> str:

"""

You are an experienced storyteller and blog writer. Using the provided topic and context,

generate an engaging and comprehensive blog post.

Construct your response using multiple message formats.

"""

system_prompt = (

"You are an engaging blog writer. Your writing is vivid, descriptive, and informative. "

"Craft a blog post that is both creative and well-structured."

)

user_prompt = (

f"Write a blog post about the topic '{topic}'. Use the following context to inform your response:\n{context}\n"

"Ensure your response is coherent, detailed, and flows naturally."

)

return [ell.system(system_prompt), ell.user(user_prompt)]

```
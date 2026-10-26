# Brochure Maker

Give it a company's website and it writes a short brochure about the company. It works in two LLM steps:

1. **Choose the pages.** The model gets every link on the homepage and returns JSON naming the pages worth reading, such as About, Careers and Customers.
2. **Write the brochure.** Those pages are scraped, cut to size and passed to a second prompt that writes a Markdown brochure in the chosen tone.

## Notebooks

| File | What it shows |
|---|---|
| [`brochure_generator.ipynb`](brochure_generator.ipynb) | A Gradio app with a streamed result. You can switch between OpenAI, Anthropic, Google and Groq models, all through one OpenAI-compatible client, and between tones (professional, casual, humorous, sarcastic…). |
| [`groq_brochure_maker.ipynb`](groq_brochure_maker.ipynb) | The two-step pipeline on Groq, with the system prompts, user prompts and logic kept in separate sections so each is easy to change. |
| [`groq keynes analyzer.ipynb`](<groq keynes analyzer.ipynb>) | A one-shot summarizer for any web page. |
| [`scraper.py`](scraper.py) | Shared helpers: page text with scripts and styles removed, and a page's links. |

## Run it

```bash
pip install python-dotenv openai groq gradio beautifulsoup4 requests
```

Create a `.env` file with the keys for the providers you want (`OPENAI_API_KEY`, `ANTHROPIC_API_KEY`, `GOOGLE_API_KEY`, `GROQ_API_KEY`), then open a notebook.

Built while working through Ed Donner's *LLM Engineering* course, then extended with more providers, tone control and a streaming UI.

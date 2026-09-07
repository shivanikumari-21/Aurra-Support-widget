# Aurra Support Widget

A self-contained, AI-powered customer support chat widget for websites. Drop a single HTML file into any site to add a floating chat launcher that answers customer questions using Claude.

## Features

- Floating launcher bubble that expands into a chat panel
- Answers grounded in a configurable knowledge base (shipping, returns, policies, etc.)
- Quick-reply suggestion chips
- Typing indicator, auto-scrolling, and mobile-responsive layout
- No build step, no dependencies — plain HTML/CSS/JavaScript

## Files

| File | Description |
|---|---|
| `support-widget.html` | The full widget: markup, styles, and logic in one file |

## Getting Started

1. Download `support-widget.html`.
2. Open the file and find the `SW_CONFIG` object near the bottom of the `<script>` tag.
3. Edit the config to match your business:

   ```js
   const SW_CONFIG = {
     businessName: "Aurra",
     headerTitle: "Aurra Support",
     knowledgeBase: `...your policies, FAQs, and facts go here...`,
     quickReplies: ["Where's my order?", "What's your return policy?"],
     greeting: "Hi! How can I help?",
     model: "claude-sonnet-4-6",
   };
   ```

4. Embed the widget in your site — either paste its `<style>`, HTML, and `<script>` blocks into an existing page, or load the whole file in an `<iframe>`.

## ⚠️ Before Going to Production

This demo calls the Anthropic API **directly from the browser**, which would expose your API key to anyone who views the page source. Before deploying publicly:

- Add a backend endpoint (e.g. a small Node/Express or serverless function) that holds your API key server-side.
- Change the `fetch()` call in `sendMessage()` to point to your backend endpoint instead of `https://api.anthropic.com/v1/messages`.
- Have your backend forward the request to the Anthropic API and return the response.

## Customization

- **Colors/fonts**: edit the CSS custom properties (`--moss`, `--paper`, `--ink`, etc.) at the top of the `<style>` block.
- **Tone/behavior**: adjust the system prompt appended in `sendMessage()` (the line after `knowledgeBase` in the `fetch` body).
- **Model**: change `SW_CONFIG.model` to any available Claude model.

## License

Use and modify freely for your own project.

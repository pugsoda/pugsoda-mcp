# PugSoda MCP server and agent skill

[PugSoda](https://pugsoda.com) turns one photo of a person, couple, friend pair or pet into trending TikTok AI meme videos and themed studio photo sets—paid per video with no subscription or account required, and with a free first-frame preview before checkout on supported templates. This repository holds the connection details for its remote MCP server and an [Agent Skill](skills/pugsoda/SKILL.md). The service is hosted; there is nothing to install or run locally.

- **MCP endpoint:** `https://pugsoda.com/mcp` (Streamable HTTP)
- **Auth:** none. Free, public read-only catalog—no API key or account needed.
- **Registry name:** `com.pugsoda/pugsoda` in the [official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=com.pugsoda/pugsoda)
- **Docs:** [pugsoda.com/docs/mcp](https://pugsoda.com/docs/mcp) · [llms.txt](https://pugsoda.com/llms.txt)

## Connect

**Claude Code**

```bash
claude mcp add --transport http pugsoda https://pugsoda.com/mcp
```

**Cursor** (`~/.cursor/mcp.json`)

```json
{
  "mcpServers": {
    "pugsoda": { "url": "https://pugsoda.com/mcp" }
  }
}
```

**Codex** (`~/.codex/config.toml`)

```toml
[mcp_servers.pugsoda]
url = "https://pugsoda.com/mcp"
```

In Claude Desktop or ChatGPT, add `https://pugsoda.com/mcp` as a custom connector.

## Tools

| Tool | What it does |
| --- | --- |
| `list_trending_memes` | List trending TikTok AI meme video templates ordered by heat and recency, optionally filtered by `subject` (`person`, `pair`, `couple`, `pet`), with clip length, starting one-time price, free preview availability and direct upload link |
| `search_templates` | Search all AI video templates, TikTok meme swaps, themed photo studios and product video templates by `query`, `subject` or `theme` (e.g. `cat`, `dance`, `cars`, `halloween`, `christmas`) |
| `get_template` | Full details for a template `slug` (e.g. `hit-the-road-dude`, `clapping-cat`, `wild-west-saloon`): photo instructions, duration, exact one-time price, free first-frame preview flag, step-by-step guide, FAQ and upload URL |

Photo upload, free first-frame preview and one-time checkout happen in the browser on each template page under [pugsoda.com/templates](https://pugsoda.com/templates).

## Markdown & LLMs endpoints

Every template page and guide can also be read directly without MCP:

- `https://pugsoda.com/llms.txt`
- Append `.md` to public pages (for example `https://pugsoda.com/templates.md`)

## Agent skill

[`skills/pugsoda/SKILL.md`](skills/pugsoda/SKILL.md) follows the [Agent Skills](https://agentskills.io) format. Install it with

```bash
npx skills add pugsoda/pugsoda-mcp
```

or copy the folder into your agent's skills directory (for Claude Code, `~/.claude/skills/pugsoda/`).

### One-line prompt for any AI agent

Paste into Claude Code, Cursor, Codex, or Gemini CLI:

```text
Read https://raw.githubusercontent.com/pugsoda/pugsoda-mcp/main/skills/pugsoda/SKILL.md and find trending TikTok meme video templates I can make from one photo.
```

## Support

support@pugsoda.com

## License

The files in this repository are MIT licensed. Template media and video generation on pugsoda.com are covered by [pugsoda.com/terms](https://pugsoda.com/terms).

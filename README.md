# adios for Claude

A Claude Code plugin that adds the hosted [adios.sh](https://adios.sh) MCP server. Ask Claude for a link and share a password, token or `.env` without leaving it in a chat, ticket or pull request. The link opens once (or as often as you choose) and then it is gone.

## Install

```
claude plugin marketplace add weblove-be/adios-claude-plugin
claude plugin install adios@weblove
```

Restart the session, then try: "make an adios link for `hello`, 1 hour, 1 read".

## Tools

| Tool | What it does |
| --- | --- |
| `create_secret` | `text`, `ttl` (`1h`, `24h`, `7d`), `reads` (1 to 10 or `null`), optional `password`. Returns the link and a delete token. |
| `secret_status` | Reads left and expiry, without using up a read. |
| `delete_secret` | Deletes the link before it expires. |

There is no tool to read a link, on purpose.

## Privacy

This plugin uses the hosted server at `https://mcp.adios.sh/mcp`. The text goes from Claude to that server, which encrypts it and stores only the encrypted version. It does not log or store the text, but "we cannot read it" does not hold for this route: Claude, its provider and the adios server handle the text while the link is made. For very sensitive text, create the link on adios.sh yourself. See the [privacy notice](https://adios.sh/privacy).

Only share what you mean to share. Be careful with tools that read pages or files you do not control, because content in them can try to make an agent share something it should not.

## Limits

The hosted server allows 60 requests a minute per IP and 256 KB per request, and links last at most 7 days.

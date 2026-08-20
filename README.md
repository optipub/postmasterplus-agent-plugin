# Postmaster+ Agent Plugin

> Email deliverability copilot that unifies Gmail Postmaster Tools, Outlook SNDS, Validity, universal feedback loops, and DNS into one health view — across all your teams.

An [Agent Plugins](https://agent-plugins.org) package that connects any compatible AI client (Cursor, Claude, ChatGPT, and others) to the **Postmaster+** deliverability platform over its hosted MCP server.

## What is Postmaster+?

Postmaster+ is a deliverability assistant that aggregates signals from across the sender ecosystem — Gmail Postmaster Tools, Outlook SNDS, Validity, universal feedback loops, DNS, and more — into a single live view of your sender reputation and inbox placement. Start with a bird's-eye health overview, then drill into specifics: track domains and IPs, catch blocklisted IPs, surface inactive mail streams, and monitor complaint rates and mailbox-provider compliance over time. Natural-language questions resolve to the right data via intent-specific tools — count domains, chart multi-metric trends, or ask when Gmail compliance changed — and an actionable feed shows what needs attention across every team you can access. It also provisions agent-managed seedboxes: throwaway inbox addresses an agent can use to subscribe to a newsletter and verify deliverability without exposing your own domain or IP.

## What this plugin provides

A single hosted **MCP server** (Streamable HTTP transport) exposing Postmaster+ tools to your agent:

- **Overview & health** — deliverability overview, actionable feed, unread counts
- **Domains & IPs** — list/count/inspect domains and IPs, timelines, complaint-rate history
- **Reputation signals** — Gmail compliance history, Gmail domain stats, ARF reports, spam identifiers
- **Blocklists** — list/count blocklisted IPs, start and check blocklist scans
- **Mail streams** — list mail streams, surface inactive ones
- **Seedboxes** — create/list/update/revoke agent-managed seedboxes, read messages, manage subscriptions and unsubscribes
- **Teams** — resolve and switch between every team you can access
- **Email intelligence** — on-demand intelligence scans

## Installation

### Cursor / Agent Plugins clients

Point the client at this repository, or add the MCP server directly:

```json
{
  "$schema": "https://agent-plugins.org/schemas/1.0.0/mcp.schema.json",
  "mcpServers": {
    "postmaster": {
      "type": "streamable-http",
      "url": "https://postmasterplus.app/mcp/postmaster"
    }
  }
}
```

The server is authenticated with OAuth 2.0. Your client handles the sign-in flow on first connect — no API keys are embedded in this package. You will be asked to authorize the scopes your workflow needs:

- `mcp:use` — read deliverability data
- `mcp:write` — create, update, revoke, and delete resources
- `mcp:spend` — spend credits (seedboxes, blocklist and intelligence scans)

## Package contents

```
postmasterplus-agent-plugin/
├── plugin.json   # Agent Plugins v1.0.0 manifest
├── mcp.json      # Hosted Postmaster+ MCP server (Streamable HTTP)
├── LICENSE
└── README.md
```

## Links

- Product: https://postmasterplus.app
- Agent Plugins standard: https://agent-plugins.org

# Growth Intel MCP Server (`net.growthintel/leads`)

[![MCP Registry](https://img.shields.io/badge/MCP-Streamable%20HTTP-003527)](https://growthintel.net/.well-known/mcp.json)
[![Growth Intel MCP connector](https://glama.ai/mcp/connectors/net.growthintel/growthintel-mcp/badges/score.svg)](https://glama.ai/mcp/connectors/net.growthintel/growthintel-mcp)
[![Zero PII](https://img.shields.io/badge/Privacy-Zero--PII%20Read--Only-0f5132)](https://growthintel.net/en/security)
[![Sandbox](https://img.shields.io/badge/Sandbox-Instant%20Live%20Key-1b4332)](https://growthintel.net/en/docs#mcp)

Official **Model Context Protocol (MCP)** server and discovery manifest for **[Growth Intel](https://growthintel.net)** — an AI-native CRM, multi-dimensional lead intent scoring, and omni-channel ad attribution platform (WhatsApp, Instagram, Web Forms, Meta Ads, Google Ads, LinkedIn, TikTok).

- **Remote Endpoint (Streamable HTTP):** `https://growthintel.net/mcp/leads`
- **Public Sandbox Token (Zero-Signup):** `Bearer gi_sandbox_live_demo_key`
- **Discovery Manifest:** `https://growthintel.net/.well-known/mcp.json`
- **Agent Instructions:** `https://growthintel.net/.well-known/agent-instructions.md`
- **Full Documentation:** `https://growthintel.net/en/docs`
- **LLMs Context:** `https://growthintel.net/llms.txt`

---

## Quick Start (Zero-Signup Sandbox)

Connect any MCP-compatible client directly to the hosted Streamable HTTP server using the public sandbox token:

### Cursor / Claude Code / Antigravity (`mcpServers`)

```json
{
  "mcpServers": {
    "growthintel": {
      "type": "http",
      "url": "https://growthintel.net/mcp/leads",
      "headers": {
        "Authorization": "Bearer gi_sandbox_live_demo_key"
      }
    }
  }
}
```

### Verify with `curl`

```bash
curl -s -X POST "https://growthintel.net/mcp/leads" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -H "Authorization: Bearer gi_sandbox_live_demo_key" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list","params":{}}'
```

---

## Available Read-Only, Zero-PII Tools

All 8 tools are **read-only**, **idempotent**, and **strictly anonymized** (never returning customer names, phone numbers, email addresses, or raw company PII):

| Tool | Purpose |
| :--- | :--- |
| `search-leads-tool` | Filter leads by status, source, budget tier, intent score range, qualified, and won flags. |
| `search-leads-by-natural-language-tool` | Query leads using natural language (Turkish or English) mapped to a constrained filter whitelist. |
| `campaign-performance-tool` | Retrieve ad campaign metrics (`spend`, `leads`, `conversions`, `clicks`, `impressions`, `cost_per_lead`). |
| `pipeline-overview-tool` | Aggregate lead counts grouped by `status`, `source`, or `budget_tier`. |
| `task-summary-tool` | Inspect sales task workload (`open`, `overdue`, `completed_recently`) without exposing free-text PII. |
| `creative-performance-tool` | Rank paid ad creatives by lead volume, qualification rate, won deals, and cost per won. |
| `creative-strategy-recommendations-tool` | Identify high-converting audience segments to scale and low-quality segments to prune. |
| `social-content-recommendations-tool` | Highlight organic Meta posts with strong engagement suitable for paid lead-gen promotion. |

---

## Authentication Options

1. **Public Sandbox (`gi_sandbox_live_demo_key`)**: Instant testing against anonymized demo data without creating an account.
2. **Tenant API Token**: Generate a workspace-scoped Bearer token inside your Growth Intel account.
3. **OAuth 2.0**: Standard MCP OAuth discovery via `/.well-known/oauth-authorization-server` and `/.well-known/oauth-protected-resource`.

---

## Related Resources

- [Growth Intel Platform](https://growthintel.net/en)
- [Meta Lead Form vs. Click-to-WhatsApp Ads Comparison](https://growthintel.net/en/compare/meta-lead-form-vs-whatsapp)
- [CPL, CPQL, CPW & ROAS Calculator](https://growthintel.net/en/tools/cpql-and-roas-calculator)
- [One-Click Google Tag Manager (GTM) Setup](https://growthintel.net/en/integrations/google-tag-manager)
- [OpenAPI 3.1 Specification](https://growthintel.net/openapi.json)

## License

MIT — see [LICENSE](./LICENSE).

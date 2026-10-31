# Vorsorge-Regeln MCP server

German estate planning with the legal source for every value: notary fees under the court and notary fees act (GNotKG) for wills, joint wills, inheritance contracts and powers of attorney; statutory inheritance shares and compulsory portions under the BGB; fees and deadlines of the Central Register of Lasting Powers of Attorney, will custody and inheritance; and the official emergency and estate planning folders (Notfallmappe, Vorsorgemappe) published by German districts and cities. Answers are in German. Information, not legal advice.

- **Website:** [vorsorge-regeln.de](https://vorsorge-regeln.de)
- **Documentation:** [vorsorge-regeln.de/ki-assistenten.html](https://vorsorge-regeln.de/ki-assistenten.html)
- **Endpoint:** `https://vorsorge-regeln.de/mcp.php` (MCP Streamable HTTP, public, no authentication, no API key)
- **MCP Registry:** `de.vorsorge-regeln/vorsorge-regeln`

## Tools

- `notarkosten_berechnen`: notary fee under the GNotKG (same calculation as the site's notary fee calculator)
- `erbquoten_berechnen`: statutory inheritance shares and compulsory portions (same calculation as the site's inheritance calculator)
- `vorsorge_fakten`: sourced fees, deadlines and rules with statute, official link and check date
- `notfallmappe_finden`: official emergency folders by district, city or state, from a register of 55 checked folders

All tools are read-only and stateless. They never ask for names, birth dates or health data, and the server stores nothing it receives.

## Connect

Any MCP client that supports remote servers:

```json
{
  "mcpServers": {
    "vorsorge-regeln": {
      "type": "streamable-http",
      "url": "https://vorsorge-regeln.de/mcp.php?src=mcp"
    }
  }
}
```

Quick test:

```bash
curl -s -X POST 'https://vorsorge-regeln.de/mcp.php?src=mcp' -H 'Content-Type: application/json' -d '{"jsonrpc":"2.0","id":1,"method":"tools/list"}'
```

This repository holds the listing metadata only. The server itself is a hosted service run by the Vorsorge-Regeln website (https://vorsorge-regeln.de); see the documentation link above for privacy and terms.

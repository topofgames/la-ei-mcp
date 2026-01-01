# La Ei MCP Server

A Model Context Protocol (MCP) server for [La Ei](https://laei.ro) - Romania's classified ads platform and business directory.

## Features

- **Search Classified Ads** - Find products, services, and listings across Romania
- **Business Directory** - Access 30,000+ Romanian businesses with contact details
- **Exchange Rates** - Real-time BNR (National Bank of Romania) currency rates
- **Location Data** - Explore Romanian cities, counties, and geographic information
- **Statistics** - Platform analytics and trends

## Available Tools

| Tool | Description |
|------|-------------|
| `cauta-anunturi` | Search classified ads with filters |
| `detalii-anunt` | Get complete ad details |
| `obtine-categorii` | Browse category hierarchy |
| `obtine-locatii` | Geographic locations data |
| `statistici-anunturi` | Platform statistics |
| `explorare-orase` | Explore Romanian cities |
| `cauta-firme` | Search business directory |
| `detalii-firma` | Business details |
| `categorii-firme` | Business categories |
| `curs-valutar` | BNR exchange rates |
| `posteaza-anunt` | Post new classified ad |

## Installation

### Claude Desktop

Add to your Claude Desktop configuration (`claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "la-ei-romania": {
      "command": "npx",
      "args": [
        "-y",
        "@anthropic-ai/mcp-remote@latest",
        "https://laei.ro/mcp?api=YOUR_API_KEY"
      ]
    }
  }
}
```

### Public Access (No API Key)

The server can be used without an API key for read-only access to public tools:
- Search ads and businesses
- View categories and locations
- Get exchange rates
- Explore cities

```json
{
  "mcpServers": {
    "la-ei-romania": {
      "command": "npx",
      "args": [
        "-y",
        "@anthropic-ai/mcp-remote@latest",
        "https://laei.ro/mcp"
      ]
    }
  }
}
```

### Full Access (With API Key)

For full access including posting ads and admin features:

1. Visit [https://laei.ro/mcp](https://laei.ro/mcp)
2. Create an account
3. Generate an API key from your dashboard
4. Add `?api=YOUR_API_KEY` to the URL

## Usage Examples

### Search Classified Ads
```json
{
  "name": "cauta-anunturi",
  "arguments": {
    "query": "apartament",
    "city_id": 658,
    "limit": 10
  }
}
```

### Get Exchange Rates
```json
{
  "name": "curs-valutar",
  "arguments": {
    "action": "latest"
  }
}
```

### Search Businesses
```json
{
  "name": "cauta-firme",
  "arguments": {
    "query": "restaurant",
    "city": "București",
    "limit": 20
  }
}
```

### Explore Cities
```json
{
  "name": "explorare-orase",
  "arguments": {
    "action": "top_cities",
    "limit": 10
  }
}
```

## API Endpoint

- **URL**: `https://laei.ro/mcp`
- **Protocol**: JSON-RPC 2.0
- **Transport**: Streamable HTTP
- **Authentication**: API key via URL parameter or Authorization header

## Rate Limits

- 100 requests per minute per IP
- Higher limits available for verified API keys

## Language

All tools are available in Romanian language, optimized for Romanian market data.

## Support

- Website: [https://laei.ro](https://laei.ro)
- MCP Documentation: [https://laei.ro/mcp](https://laei.ro/mcp)

## License

Proprietary - La Ei Platform

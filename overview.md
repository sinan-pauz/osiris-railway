# Deploy and Host Osiris on Railway

Osiris is an open-source, real-time global intelligence dashboard that aggregates live flight tracking, CCTV networks, earthquake monitoring, conflict zone mapping, NASA wildfire data, satellite tracking, and 24/7 news feeds into a single GPU-accelerated MapLibre interface. Every data point is rendered via WebGL for smooth 60fps performance.

## About Hosting Osiris

Osiris is a Next.js 16 application built with the App Router, Turbopack, and a standalone production output. It pulls data from public OSINT sources (OpenSky, USGS, NASA FIRMS, NOAA SWPC, NVD, GDELT, EONET, and 25+ broadcaster RSS feeds) through its own API routes and renders everything client-side via MapLibre GL. The app is stateless — no database, no persistent volume — which makes it ideal for Railway's containerized runtime. The included multi-stage Dockerfile produces a hardened, non-root runtime image that Railway can build and serve directly with zero configuration.

## Common Use Cases

- Real-time situational awareness dashboards for security operations centers
- OSINT research platform with integrated RECON toolkit (port scanner, DNS, WHOIS, SSL inspector, CVE lookup)
- Live conflict and crisis monitoring across 13 active zones
- Personal intelligence aggregator combining aviation, seismic, fire, and broadcast data on a single map

## Dependencies for Osiris Hosting

- Node.js 22 runtime (provided by the Dockerfile)
- Public outbound HTTPS access to OSINT data sources (OpenSky, USGS, NASA, NOAA, NVD, RSS feeds)

### Deployment Dependencies

- [Osiris GitHub Repository](https://github.com/simplifaisoul/osiris)
- [Osiris Live Demo](https://osirisai.live)
- [Osiris Discord Community](https://discord.gg/umBykEpb98)

### Implementation Details

Osiris ships fully functional with no required environment variables. All API integrations are optional and only enhance specific data layers:

- `OPENSKY_USERNAME` / `OPENSKY_PASSWORD` — increases OpenSky Network flight data quota
- `N2YO_API_KEY` — enables N2YO satellite tracking integration
- `AIS_API_KEY` — enables live AIS maritime vessel feeds
- `SCANNER_URL` / `SCANNER_KEY` — connects an external port-scanner backend for the RECON toolkit

The Dockerfile uses Next.js standalone output for a minimal runtime image (~150MB) and runs as a non-root `nextjs` user on port 3000.

## Why Deploy Osiris on Railway?

Railway is a singular platform to deploy your infrastructure stack. Railway will host your infrastructure so you don't have to deal with configuration, while allowing you to vertically and horizontally scale it.

By deploying Osiris on Railway, you are one step closer to supporting a complete full-stack application with minimal burden. Host your servers, databases, AI agents, and more on Railway.

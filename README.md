# Atmos — Weather Dashboard

Responsive weather dashboard built with HTML, CSS, vanilla JavaScript, and a Node.js Vercel serverless function.

## Features
- Search any supported city and ten quick-select city chips
- Current temperature, condition, feels-like, humidity, wind, UV, cloud cover, visibility, and local time
- Reusable mood engine with documented priority order
- Raw and formatted JSON inspector, syntax highlighting, copy action
- Server-side WeatherAPI proxy; key is not shipped to the browser
- Input validation, request timeout, graceful errors, best-effort per-instance rate limiting

## Local development
1. Install Node.js 18+ and Vercel CLI (npm install -g vercel).
2. Copy .env.example to .env and set WEATHERAPI_KEY to your rotated API key.
3. Run npm install, then vercel dev.
4. Open the local URL printed by Vercel.

## Vercel deployment
1. Import this repository at https://vercel.com/new.
2. In Project Settings > Environment Variables, add WEATHERAPI_KEY for Production (and Preview/Development if needed).
3. Deploy or redeploy after adding the variable.
4. Test the home page, /api/weather?city=Patna, invalid city handling, both JSON tabs, and clipboard copy.

## Mood priority
1. Temperature >= 38 C: Scorching
2. Temperature <= 5 C: Freezing
3. Humidity >= 80% and temperature >= 28 C: Muggy
4. Wind speed >= 30 km/h: Windy
5. Temperature 20–30 C, humidity <= 60%, wind <= 20 km/h: Pleasant
6. Temperature 15–30 C, humidity <= 75%, wind <= 30 km/h: Comfortable
7. Otherwise: Mixed

## Security
Never commit .env or credentials. Rotate credentials that have been exposed. The in-memory rate limiter is best-effort per serverless instance; use a shared rate-limit store for robust production enforcement.

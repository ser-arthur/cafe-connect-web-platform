# CafeConnect

A curated directory of cafés worth working from.

CafeConnect profiles each café on the things that decide whether you can settle in for a few hours: wifi strength, power sockets, seating, noise, the price of a coffee and opening hours. Members add the places they rely on, rate them and leave reviews. It is built as two surfaces over one set of data: a mobile-first web app, and a JSON REST API.

**Live demo: [cafe-connect.vercel.app](https://cafe-connect.vercel.app)**

Browsing is open to everyone. To try the signed-in features, adding a café and leaving a review, sign in with `member@cafeconnect.app` / `Member@1234`. The demo data resets nightly.

## What it offers

Browse and sort the directory, or search for cafés near you using your location. Open a café for its full profile, photos, facilities and member reviews. Sign in to add a café of your own and leave ratings and reviews. Administrators curate the directory and upload the photography.

## How it works

The web app and the API authenticate differently, which is the main architectural decision in the project. The web app uses server-side sessions through Flask-Login; the API is stateless and uses signed JWT bearer tokens. One set of data, two access patterns, two security models.

The app is server-rendered with Flask and Jinja rather than a single-page framework, so pages paint fast, and a little vanilla JavaScript handles the map and location search. Tailwind is compiled through the Tailwind CLI. In production it runs on PostgreSQL with object storage for images and a nightly data reset; locally it runs on SQLite with no external services required.

The interface uses a warm amber accent (`#ffc451`) over charcoal (`#222222`) and cream (`#faf9f7`), with Raleway for headings and Poppins for body text. The layout is built mobile-first and scales up to desktop.

## API

A full REST API sits alongside the web app, exposing the café data over JSON with token authentication, filtering, search and distance queries.

See **[API.md](API.md)** for the endpoint reference, authentication, testing and integration examples.

## Screenshots

<p align="center">
  <img src="screenshots/hero-mobile.png" alt="CafeConnect on mobile" width="60%"><br>
  <sub>On mobile: home, a listing, and amenities at a glance</sub>
</p>

<p align="center">
  <img src="screenshots/home.png" alt="The CafeConnect landing page" width="100%"><br>
  <sub>The landing page</sub>
</p>

<p align="center">
  <img src="screenshots/browse-city.png" alt="Browse cafés by city" width="100%"><br>
  <sub>Browse by city, with the directory's running totals</sub>
</p>

<table>
  <tr>
    <td width="50%">
      <img src="screenshots/browse.png" alt="The café directory with search and filters" width="100%"><br>
      <sub>The directory, with search, filters and sort</sub>
    </td>
    <td width="50%">
      <img src="screenshots/add-cafe.png" alt="Contributing a café" width="100%"><br>
      <sub>Contributing a café</sub>
    </td>
  </tr>
  <tr>
    <td width="50%">
      <img src="screenshots/cafe-detail.png" alt="A café listing in full" width="100%"><br>
      <sub>A listing in full</sub>
    </td>
    <td width="50%">
      <img src="screenshots/reviews.png" alt="Ratings and reviews on a café" width="100%"><br>
      <sub>Ratings and reviews on every café</sub>
    </td>
  </tr>
</table>

## Stack

| Layer | Technology |
| --- | --- |
| Language | Python |
| Web framework | Flask, Jinja |
| Data layer | SQLAlchemy |
| Web auth | Flask-Login (server sessions) |
| API auth | PyJWT (stateless bearer tokens) |
| Validation | marshmallow (API), WTForms (web) |
| Styling | Tailwind CSS, compiled via the Tailwind CLI |
| Client | Vanilla JavaScript |
| Database | PostgreSQL in production, SQLite in development |
| Image storage | Supabase Storage |
| Rate limiting | Flask-Limiter |
| Hosting | Vercel |

## Source code

CafeConnect is a personal project. This repository documents it; the application source is kept private, but it can be shared for review on request.

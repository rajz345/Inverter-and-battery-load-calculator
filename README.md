# Rajkumar Auto Electricals — Inverter & Battery Calculator

A responsive, single-page inverter and battery sizing calculator for Rajkumar Auto Electricals. The project is contained in `Rajkumar_Auto_Electricals_Modern_Calculator_Netlify_QR.html` and can be hosted as a static website.

## Features

- Appliance load calculator with preset household appliances and editable quantities.
- Custom appliance entry with wattage and motor-load option.
- Inverter size, battery bank, wiring, charger-current, and estimated backup recommendations.
- Tubular and LiFePO4 battery assumptions, selectable battery capacities, and load-use percentage.
- Copyable customer quote and a QR code linking to the hosted calculator.
- Responsive layout with light and dark color themes and print styling.

## Run locally

Open `Rajkumar_Auto_Electricals_Modern_Calculator_Netlify_QR.html` in a modern browser. No build step or package installation is required.

The page loads React, ReactDOM, HTM, jsPDF, and qrcode-generator from public CDNs. An internet connection is needed for these libraries to load. The calculator interface and its calculations will not initialize if the required React or HTM scripts are unavailable.

## Deploy to Netlify

1. Put the HTML file in the root of a Git repository.
2. In Netlify, import the repository as a new site.
3. Leave the build command empty and set the publish directory to the directory containing the HTML file (usually `.`).
4. Ensure the deployed page is named `index.html`, or configure a redirect to the calculator file.
5. After deployment, update the QR target in the source as described below and redeploy.

You can also deploy the HTML file using Netlify Drop or another static hosting provider.

## Configuration

The hosted address used to generate the QR code is set near the beginning of the script:

```js
const APP_URL = "https://rajkumar-auto.netlify.app";
```

Change this value to the final public URL before generating or publishing the page. The on-page QR code and the QR code in generated quotes use this address.

## Calculator assumptions

- Preset appliance wattages are typical estimates; actual equipment may use different power.
- The inverter recommendation uses connected load, a 0.8 power factor, a 20% margin, and a motor-start allowance for marked motor loads.
- Battery sizing uses the selected percentage of connected load, the requested backup hours, and 85% inverter efficiency.
- Usable battery depth is assumed to be 50% for tubular batteries and 90% for LiFePO4 batteries.
- The calculator rounds up to a standard inverter capacity where available. It does not replace checking manufacturer specifications, actual starting current, battery condition, or site wiring.

These are estimates for shop guidance; confirm the final product selection with the customer and the equipment manufacturer.

## Quote features

The **Copy quote** button works in modern browsers that permit clipboard access; if clipboard access is unavailable, the page attempts a legacy copy fallback. A PDF download button is exposed only when the hosting environment provides the `window.claude.use("downloads")` integration. The standalone HTML by itself does not provide that integration, so PDF download may not appear in a regular browser.

## Project file

```text
Rajkumar_Auto_Electricals_Modern_Calculator_Netlify_QR.html
```


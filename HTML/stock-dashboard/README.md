# Stock Dashboard

A single-file stock dashboard that runs directly in the browser with no build step and no dependencies.

The app loads market data from Yahoo Finance through a CORS proxy, renders responsive sparkline charts, supports live ticker search, and remembers your layout and watchlist settings in local storage.

## Highlights

- Single HTML file: `index.html`
- No install or build required
- Live ticker autocomplete/search
- Per-card chart ranges: `1D`, `5D`, `1M`, `6M`, `YTD`, `1Y`, `5Y`, `Max`
- Custom date range picker per stock
- 52-week high/low range bar
- Shares input with position value and daily P&L
- Drag-to-reorder watchlist cards
- Light and dark theme toggle
- Persistent watchlist, ranges, layout, theme, custom ranges, and shares
- Inline help panel and keyboard shortcuts
- CORS proxy fallback for better reliability

## Run

Open `index.html` in a browser.

Because this is a static file, there is no package install step and no local server requirement for the current implementation.

## How To Use

### Add stocks

- Type a ticker such as `AAPL`, `MSFT`, `NVDA`, `BTC-USD`, or `BMO.TO`
- Pick a result from autocomplete or press `Enter`
- Invalid symbols are rejected automatically

### Change chart ranges

Use the range tabs on each card:

- `1D` for intraday
- `5D` for 5 trading days
- `1M`, `6M`, `YTD`, `1Y`, `5Y`, `Max` for wider history

### Use a custom date range

- Click `Custom` on a card
- Select `From` and `To`
- Click `Apply`

After applying, the selected window is shown as a compact summary and can be edited again later.

### Reorder cards

- Drag the `⠿` handle in the top-right area of a card
- Drop it over another card to move it

### Track holdings

- Enter a share count in the `Shares` field
- The card shows:
  - current position value
  - daily gain/loss based on the stock's current daily move

## Keyboard Shortcuts

- `/` focuses the symbol input
- `R` refreshes all cards

## What The Card Shows

### Price

The large number is the latest market price.

### Currency

The small code next to the price shows the trading currency, such as `USD` or `CAD`.

### Daily/range change

- Green `▲` means the stock is up
- Red `▼` means the stock is down
- On `1D`, change is relative to the previous close
- On other ranges, change is measured across the selected chart window

### 52-week bar

The bar under the price shows where the current price sits between the 52-week low and 52-week high.

- `L` = 52-week low
- `H` = 52-week high
- The blue dot marks the current price within that range

## Data Source

The dashboard uses Yahoo Finance chart/search endpoints and accesses them through a CORS proxy.

Current behavior includes a fallback proxy path if the primary proxy is unavailable.

## Persistence

The dashboard stores state in `localStorage`, including:

- watchlist symbols
- selected range per symbol
- custom date ranges
- column layout
- theme
- share counts

## File Structure

- `index.html` — the entire application: HTML, CSS, and JavaScript

## Notes

- Some symbols may not provide intraday data for `1D`; the dashboard falls back when possible
- Custom date ranges with no trading activity may show a no-data message
- Since data depends on third-party endpoints and proxies, availability can vary

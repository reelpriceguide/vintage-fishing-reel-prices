# Vintage fishing reel prices: Penn and Abu Garcia

What vintage Penn and Abu Garcia fishing reels actually sell for: the median price paid in completed eBay sales, per reel
model, and a monthly price index. Published by [Reel Price Guide](https://reelpriceguide.com/), which shows the same figures page by page and
updates them every day. This repository is refreshed once a month.

Data date: 2026-11-09. Rows: 174 in `data/values.csv` (reels with a current value), 6 in
`data/price-index.csv` (3 months of the price index), 149 in `data/price-index-reels.csv`.

## Files

### `data/values.csv`

One row per reel model with a value from the last 90 days (a median of at least 5 sales).

| Column | Meaning |
|---|---|
| `id` | the reel's id on the site |
| `brand` | `penn` or `abu_garcia` |
| `brand_name` | the brand as written: Penn, Abu Garcia |
| `line` | the reel's line (Senator, Ambassadeur, Squidder...) |
| `model` | the model number within the line, as the site shows it |
| `reel_type` | `conventional`, `baitcaster`, `spinning` or `spincast` |
| `name` | the reel's name on the site |
| `url` | its page, with every sale behind the value |
| `median_usd` | the median price paid, US dollars, item price without shipping |
| `sales_90d` | the number of sales the median is taken from |
| `value_date` | the date of the value |

### `data/price-index.csv`

One row per month and brand. A reel is compared when it sold at least 5 times in both the month and the month before; its
change is the change in its median sale price. The brand's `change` is the median of those changes, left empty when fewer
than 5 reels could be compared. Columns: `month`, `brand`, `brand_name`, `change` (a fraction: `0.0370` is +3.70%),
`compared`, `rose`, `fell`, `unchanged`, `brand_sales` (all the brand's sales that month), `published_date`, `url` (the
month's page).

### `data/price-index-reels.csv`

The reels behind each figure: `month`, `brand`, `id`, `name`, `prev_sales`, `prev_median_usd`, `sales`, `median_usd`,
`change`.

## How the prices are collected

Public eBay listings of vintage Penn and Abu Garcia reels are read as they appear and checked after they end; only completed
sales count, at the item price paid. Reels sold for parts or repair, lots, combos with a rod and reproductions are left out.
Details: [how the values are computed](https://reelpriceguide.com/methodology/) and [the price index](https://reelpriceguide.com/price-index/).

## Licence and citation

[CC BY 4.0](LICENSE): free to share and adapt, also commercially, with attribution and a link to https://reelpriceguide.com/.

Cite as: Reel Price Guide, reelpriceguide.com, November 2026.

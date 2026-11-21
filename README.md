# GlobalID Data Downloads

This repository stores directly downloadable datasets for the GlobalID public site.

- Generated at: `2026-11-21T00:00:00+00:00`
- Country datasets: `326`
- Disease datasets: `239`
- Formats: CSV, JSON and XLSX
- Partitioning: one file per country, disease and calendar window; unchanged cells are not rewritten
- Manifest: [`manifest.json`](./manifest.json)

Public files are stable branch links under:

`https://raw.githubusercontent.com/xmusphlkg/globalID2_data_download/main`

## Manifest encoding

Schema 5 uses `cell_metadata: country_parts_v1`. Country `parts` own the cell
metadata. Disease `parts` reference it by `country_code` and window `id`,
using the disease entry's `disease_id`. Each format declares its size and SHA-256.
Default paths are `cells/<lowercase-country>/<lowercase-disease>/<window>.<format>`;
prepend `download_url_base` for the public URL. The default download filename is
`globalid-<lowercase-country>-<lowercase-disease>-<window>.<format>`.
The cell content hash defaults to its JSON file's SHA-256. Explicit fields override
these defaults. This stores shared cell metadata once and keeps the manifest below
GitHub's 100 MiB per-file limit.

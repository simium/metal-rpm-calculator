# CNC Cutting Speed Calculator

A lightweight, browser-based calculator for estimating **spindle speed (RPM)** from recommended cutting speeds (**Vc**) for common machining materials.

Built with plain **HTML, CSS and JavaScript**. No dependencies, backend, installation or build step required.

## Features

- Cutting-speed reference values for **24 workpiece materials**, transcribed from a Spanish machining table.
- Operations: **milling (fresado)**, **drilling (taladrado)** and **turning (torneado)**.
- Tool material selection: **HSS** or **Cermet**, where the source provides values.
- **Roughing (desbaste)** and **finishing (acabado)** speeds for milling and turning.
- Enter a diameter in millimetres to calculate RPM instantly.
- View the underlying cutting-speed values for the selected material and operation.
- Responsive layout for desktop and mobile.
- Blank entries in the source table remain unavailable; the calculator does not invent missing values.

**Note:** The source table specifies HSS only for drilling and does not distinguish drilling roughing/finishing speeds.

## Calculation

The spindle speed is calculated using:

\[
\mathrm{RPM} = \frac{1000 \times V_c}{\pi \times D}
\]

Where:

- **Vc** is the cutting speed in metres per minute (m/min).
- **D** is the diameter in millimetres (mm): **tool diameter** for milling and drilling, or **workpiece diameter at the cutting surface** for turning.

For example, with **Vc = 20 m/min** and **D = 6 mm**:

```text
RPM = (1000 × 20) / (π × 6) ≈ 1,061 RPM
```

## Use locally

Download or clone this repository and open `index.html` in any modern web browser. The calculations run entirely in the browser, including when offline.

## Publish with GitHub Pages

1. Push `index.html` to the root of your GitHub repository.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**.
4. Select the `main` branch and `/(root)` folder, then save.

Your site will be available at:

```text
https://YOUR_USERNAME.github.io/YOUR_REPOSITORY/
```

## Customizing the table

All reference values are defined in the `materials` array inside `index.html`. Each material has two arrays:

- `r`: roughing values, ordered as `[turning HSS, turning Cermet, milling HSS, milling Cermet, drilling HSS]`.
- `f`: finishing values, ordered as `[turning HSS, turning Cermet, milling HSS, milling Cermet]`.

Use `null` for cells not provided by the source table. Review values against the original reference before relying on them.

## Important safety note

These are **reference calculations**, not guaranteed safe machine settings. Always check the cutting-tool manufacturer's recommendations, machine speed limits, tool condition, workholding, material grade and machining setup. This calculator does **not** estimate feed rate, chip load or machining power.

## Source

Cutting-speed values transcribed from a user-supplied Spanish reference table titled *Velocidad de corte recomendada (m/min)*. Its original publisher and publication date are not identified.

## License

No license has been specified yet. Add a `LICENSE` file if you want to define how others may reuse the project.

# Daysworth Icon Assets

## Design system

| | Value |
|---|---|
| Base leaf shape | A2 (rounded eucalyptus) |
| Leaf fill | `#2E7D32` (forest green) |
| Vein color | `#56BE50` (leaf +20% lightness, "明るい緑") |
| Vein stroke width | 1.2% of icon size |
| Light theme background | `#FFFFFF` |
| Memento Mori theme background | `#1A1A1A` |
| Corner radius | 22% of icon size (iOS squircle approximation) |

**Brand consistency principle**: leaf shape and leaf color are identical across both themes. Only the background differs. This keeps brand recognition strong while letting the theme do its emotional work.

## Folder structure

```
daysworth-icons/
├── ios/
│   ├── light/                     iOS sizes, Light theme
│   │   ├── icon-1024.png          App Store
│   │   ├── icon-180.png           60pt @3x
│   │   ├── icon-120.png           60pt @2x / 40pt @3x
│   │   ├── icon-87.png            29pt @3x (Settings)
│   │   ├── icon-80.png            40pt @2x (Spotlight)
│   │   ├── icon-58.png            29pt @2x (Settings)
│   │   └── icon-40.png            40pt @1x / 20pt @2x
│   └── memento-mori/              (same sizes)
│
├── android/
│   ├── light/                     Android sizes, Light theme
│   │   ├── icon-512.png           Play Store
│   │   ├── icon-192.png           xxxhdpi
│   │   ├── icon-144.png           xxhdpi
│   │   ├── icon-96.png            xhdpi
│   │   ├── icon-72.png            hdpi
│   │   └── icon-48.png            mdpi
│   └── memento-mori/              (same sizes)
│
├── app-store-hero/                Full marketing composition (1290×2796)
│   ├── hero-light.png             with B-3 hourglass-vein leaf
│   ├── hero-memento-mori.png
│   └── hero-*.svg                 source SVGs
│
├── vein-variants/                 Vein color comparison reference (1024)
│   ├── light-vein-bright_green.png    #56BE50  ★採用
│   ├── light-vein-pure_white.png       #FFFFFF  純白
│   ├── light-vein-white_tinted.png     #E0F0DD  白に少し緑
│   └── (same 3 for memento-mori)
│
├── icon-hero-1024-light.png       B-3 hourglass-vein icon
├── icon-hero-1024-memento-mori.png    (for splash / onboarding / large in-app use)
├── icon-hero-light.svg            source SVGs for B-3 design
├── icon-hero-memento-mori.svg
│
├── master-light.svg               1024 master SVG (regular A2)
├── master-memento-mori.svg        1024 master SVG (regular A2, dark bg)
│
└── generate*.py                   regeneration scripts (rerun anytime to re-export)
```

## How to regenerate / change a parameter

Edit `generate.py` to change colors, leaf geometry, or sizes, then run:

```bash
python3 generate.py
python3 generate_hero.py
python3 generate_vein_variants.py
```

Each script is independent and idempotent.

## B-3 hourglass-vein notes

The hourglass-vein variant (`icon-hero-*.png`) is **not for the app icon itself** — it
disappears at 58×58px. Use it for:

- App Store screenshot / marketing hero (see `app-store-hero/`)
- Splash / launch screen
- Onboarding intro slides
- Settings / About page large logo
- Web favicon at ≥128px
- In-app empty states or "welcome back" cards

When the icon needs to read at small sizes, use the regular `ios/` or `android/` assets.

## Transparency

All PNG corners are transparent (the rounded-square shape is the actual icon
boundary). Drop these straight into Xcode asset catalogs or Android `res/mipmap-*/`
folders — no extra masking needed.

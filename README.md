# LÀ TAMIQ — implementação e handoff

## Palette provisionally used

The palette PNG referred to in the brief was not included with the pasted files, so these are **temporary, replaceable values** defined in `styles.css`. No claim is made that they were extracted from an image.

| CSS token | HEX | Current role | Contrast-safe use |
|---|---:|---|---|
| `--ink` | `#22201D` | Primary text, primary button, footer | AA on `--paper`, `--white`, `--cream` |
| `--paper` | `#F7F3EC` | Main background / light button text | AA with `--ink` |
| `--cream` | `#EFE7DB` | Alternate surface | AA with `--ink` |
| `--clay` | `#B9987C` | Accent / eyebrow on light surfaces | Decorative only; not body text |
| `--brown` | `#715B4D` | Secondary text / dark section | AA for normal text on `--paper` |
| `--mist` | `#D9D5CF` | Soft surface | Decorative only |
| `--white` | `#FFFCF8` | Elevated surface | AA with `--ink` |
| `--line` | `#CFC5B7` | Borders | Non-text only |
| `--quartz` | `#D6A7A8` | Love Spell accent | Decorative/tile only |
| `--bordeaux` | `#6E2637` | Passion accent | Tile only; light text required |
| `--lavender` | `#B8A9CD` | Floral accent | Decorative/tile only |
| `--aqua` | `#8DBFC0` | Fresh Line accent | Decorative/tile only |
| `--blush` | `#D7A3A2` | Rose Petals accent | Decorative/tile only |
| `--sand` | `#CFB999` | Chamomile accent | Decorative/tile only |

## Sitemap

- Home (the supplied prototype): Hero, aromas, novidades, rituals, story, contacts/footer
- Collection: filters for aroma, product type, price; sorting; WhatsApp CTA per item
- Product: gallery, scent-note placeholder, poetic description, variant and quantity selectors, WhatsApp CTA, care/delivery and ritual cross-sells
- Rituais
- A nossa história
- Contactos / FAQ
- Policies: deliveries/payments, exchanges/returns, service terms, privacy

## Implementation notes

- All WhatsApp configuration and templates live in `script.js` as `CONFIG`. Replace `[NUMERO_WHATSAPP]` before launch.
- Product and ritual buttons create an encoded WhatsApp message. The tracking hook is ready for GA4 `dataLayer` and Meta `fbq`.
- The prototype includes semantic landmarks, labelled controls, visible focusable controls, and mobile sticky ordering CTA.
- Replace the CSS-only art placeholders with optimised images. Preserve each supplied `role="img"`/`aria-label`, or replace it with accurate `<img alt>` text.

## Image-generation prompts

**Hero:** “High-end editorial still life for a premium Portuguese home fragrance brand, warm limestone surface, translucent glass diffuser and sculptural candle, ethereal pale smoke drifting through soft late-afternoon window light, quiet luxury, muted sand, parchment and antique brass, large negative space on left for typography, no text, no labels, cinematic, 16:9.”

**Love Spell tile:** “Abstract premium fragrance artwork, rose quartz silk, translucent interlaced organic lines suggesting two hearts, scattered pale petals, subtle soft-gold glints and mist, calm intimate romance, editorial still life, no typography, vertical 4:5.”

**Passion tile:** “Quiet luxury fragrance artwork, deep bordeaux satin and near-black wine tones, single crescent moon, sparse tiny gold constellation, delicate smoke and slow water-like folds, restrained mysterious atmosphere, editorial, no text, vertical 4:5.”

**Floral tile:** “Fine botanical illustration meets premium still life, pale lavender ground, delicate lilac branches and petals, early spring light, elegant airy composition, very refined, no text, vertical 4:5.”

**Fresh Line tile:** “Minimal abstract premium fragrance visual, aqua and sea-green translucent fluid lines, one glass water drop, soft ripples and generous negative space, clean renewal, calm daylight, no text, vertical 4:5.”

**Rose Petals tile:** “Antique rose and blush fragrance artwork, stylised rose petals in gentle movement, subtle vintage gold detail, textile texture, romantic but sophisticated and modern, no text, vertical 4:5.”

**Chamomile tile:** “Natural premium wellness still life, dried chamomile flowers and fine branches on warm sand-coloured handmade paper, organic shadows, linen texture, serene and quiet, no text, vertical 4:5.”

**Ritual scenes:** “Premium home ritual editorial, [bedroom/bathroom/living room], LÀ TAMIQ-style unbranded candle, diffuser and linen spray placed naturally, tactile linen/stone/wood surfaces, low contrast natural light, calm Portuguese coastal interior, generous open space for hotspot overlays, no text, 3:2.”

## Future Shopify / WooCommerce adaptation

Keep the product and aroma data in one source (CMS metafields, Shopify metaobjects, or WooCommerce attributes). Swap the current `whatsapp()` handler for a product-template component reading selected variant/quantity. If a cart is added, retain WhatsApp as a concierge CTA alongside `add to cart`; use platform-native inventory, checkout, tax and order tracking rather than custom JavaScript.

# NeoX for After Effects

**Version 3.0.0** · Windows & macOS · After Effects 2019 (16.0) and newer

NeoX is a toolset panel for Adobe After Effects. It covers:

- quick offsets, alignment and layouts (ring, arc, grid);
- an ease graph editor;
- comp tools;
- copy/paste of properties and expressions;
- text splitting and styling, and an expression helper;
- project tools: Media Encoder, Render Queue, Precomp Importer, Find & Replace, a live Storyboard and an asset Organizer.

It comes with **NeoX Note**, a small task board with notes, in the same package. From 3.0.0 on, NeoX tells you when a new version is out and installs it for you.

One signed `NeoX.zxp` installs five panels under **Window › Extensions**:

| Panel | What it is |
|---|---|
| **NeoX** | The main toolset (tabs Offsetter, Coopy, Flex Text, Xpressor, Xtra) |
| **NeoX Note** | Task board (To Do / Doing / Done) with a rich-text note in every card |
| **NeoX Importer** | Import only the comps you need from another project |
| **NeoX Replacer** | Find & replace text or layer sources across comps |
| **NeoX Storyboard** | Live grid of scene frames built from comp markers |

---

## Install

1. Download **`NeoX.zxp`** from the [Releases](https://github.com/zyox/neox/releases/latest) page.
2. Install it with one of these:
   - [aescripts + aeplugins ZXP Installer](https://aescripts.com/learn/zxp-installer/) (free, Windows & macOS), or
   - Anastasiy's Extension Manager, or
   - Adobe's command-line installer (UPIA).
3. Restart After Effects.
4. Open **Window › Extensions › NeoX**.

No debug mode or registry changes are needed: the package is signed.

**Coming from NeoX 2.x?** Install 3.0.0 over it once, by hand, as above. Your NeoX Note board and settings are kept. After that, updates come to you inside NeoX.

**Coming from an old unsigned copy of NeoX Note?** First delete the folder `%APPDATA%\Adobe\CEP\extensions\NeoX Note` (Windows) or `~/Library/Application Support/Adobe/CEP/extensions/NeoX Note` (macOS). Your tasks are stored elsewhere and are not touched.

**Tip:** in *Edit › Preferences › Scripting & Expressions*, turn on **Allow Scripts to Write Files and Access Network**. Storyboard (saving frames) and links in NeoX Note need it.

---

## Updates

NeoX checks this repository for a newer release when the panel opens, then at most every 6 hours.

- When there is one, a banner appears at the top of the panel with the new version number and **What's new**.
- **Install update** downloads it and installs it with Adobe's own installer, which comes with Creative Cloud. Then restart After Effects.
- **Later** hides that version for a day.
- Click the version number next to the NeoX logo to check right away.
- NeoX only installs packages signed with the NeoX certificate, and only from the latest published release here.
- If the automatic install isn't possible (for example, no Creative Cloud), **Show file** opens the downloaded `.zxp` so you can install it with ZXP Installer.

---

## The NeoX panel

The page scrolls with the mouse wheel. Inputs, options, the current tab and the graph mode are remembered. Messages appear as short notes at the bottom of the panel.

### Offsetter tab

**Offsetter**
- **Arrows**: move the selected layers by *Amount* px. **Shift** = double, **Ctrl/Cmd** = 1 px.
  **Alt + arrow**: snap the anchor point to that side of the layer (masks are taken into account).
- **Center button**: reset Position · **Alt**: snap the anchor point to the center.
- **Scale + / −**: scale by *Amount* % (**Shift** = double, **Ctrl/Cmd** = 1 %) · **Reset scale** button.
- **Flip** vertical / horizontal.
- **Follow Scale**: select the guide layer first, then the others. Only their **Scale** changes, with proportions kept; parents' Scale is taken into account and keyframed Scale is resized key by key.
  - **Click: Center Fit**, fit inside the guide's box.
  - **Right-click → Height Fit**: as tall as the guide (may stick out at the sides).
  - **Right-click → Width Fit**: as wide as the guide (may stick out above and below).
- Quick amounts: 10, 20, 50, 100.

**Align**
- Align to the **Composition** or to the **Selection** (the first selected layer is the reference).
- Left, center, right, top, middle, bottom, absolute center; distribute horizontally / vertically (3+ layers).
- Uses the visible bounds of each layer, including masks and parented layers.

**Align Form**: arranges the selected layers, in the order you selected them, into a shape. The shape is centred in the comp and kept inside the title-safe area. Layers are only moved: no rotation and no scaling.
- **Ring**: evenly spaced around a circle, the first layer at 12 o'clock, clockwise. **Radius** = px from the centre (default 600).
- **Arc**: evenly spaced along the top of a circle, symmetric. **Radius** in px (default 600): smaller = rounder, bigger = flatter.
- **Grid**: rows and columns, 20 px apart, last row centred. **Rows** = how many rows (default 2).
- If a radius or gap doesn't fit inside the title-safe area, NeoX adjusts it and says what it used.
- Double-click Ring / Arc / Grid to apply it directly.

**Graph Editor**
- **Speed graph** (like After Effects) or **Value graph** for the selected keyframes; drag the handles, **Shift** = 0 speed.
- Follows the keyframes you select in the timeline.
- **Copy Ease / Paste Ease**, **Continuous** (lock outgoing velocity to incoming), **Rove Across Time** (Position).

**EasyComp**
- **True Comp Duplicate**: duplicates the selected comps (or the open comp) with *every* nested precomp **and every asset** copied too, so nothing is shared with the original.
  - Assets include footage, images, audio, image sequences and solids.
  - Each copy goes into the same Project folder as its original.
  - Expressions inside the copies that use `comp("…")` or `footage("…")` now point to the copies.
  - **Alt + click**: copy the comps only and keep the assets shared.
- **Complosion**: expand layers to the comp size.
- **Compfitted**: crop the comp to the layers' bounds, with **Pad** in px.
- **Note**: opens NeoX Note.

### Coopy tab

- **Coopy / Paste**: copy the selected properties (choose Animators, FX, Layer Style) and paste them into other layers. Paste puts the keyframes at each layer's own start, with the same gap as in the copied layer; the time indicator stays where it is.
- **Copy Expr / Paste Expr**: copy expressions from Position, Scale, Rotation, Opacity and paste them onto other layers.

### Flex Text tab

- **Split** a text layer by characters, words or lines. Each piece keeps its own style: different fonts, sizes and colors on different lines stay as they were (After Effects 2024 / 24.3 or newer).
- **Pull word up / Push word down** between lines; **leading** tools (distribute by font size, ±5 px).
- **Text align** left / center / right without the text moving; **reset baseline shift & center anchor**.
- **Normalize Text**: bakes the layer's Scale into the font size. Scale goes back to 100 % and the text stays exactly where it is, also when parented, keyframed or with mixed font sizes.
- **Extract Styles**: reads the fonts / sizes / colors used in the selected text layers (up to 4) so you can apply them to other text layers with one click.

### Xpressor tab

- Write an expression, with click-to-insert suggestions such as `wiggle(freq, amp)`, `loopOut()` and `posterizeTime()`.
- Set the **Frequency** / **Amplitude** variables.
- **Apply** it to Position, Scale, Rotation, Opacity, or to the properties selected in the timeline.
- **Remove Expression** clears them.

### Xtra tab

**Render**
- **Media Encoder**: sends the comps selected in the Project panel (or the open comp) to Adobe Media Encoder, like *Ctrl+Alt+M*.
- **Render Queue**: adds them to After Effects' Render Queue.

**Project tools**
- **Importer** (window): import only the comps you need from another `.aep`. Searchable comp list with folder, size, duration and fps, nested-comp tags, recent projects, *Update existing*.
- **Replacer** (window): find & replace **text content** (also inside every Source Text keyframe) or **layer sources** across comps, with a live before/after preview of every match.
- **Storyboard** (window): every comp marker is a scene.
  - *Create storyboard* finds the scene starts from your layer timing and places normal comp markers (your own markers are kept; markers whose comment starts with `#` are ignored).
  - Add or delete a marker to add or remove a scene; the board updates live while you work.
  - Grid of frames in the comp's aspect ratio with **View** zoom and **Zoom to Fit**, thumbnail at the start / middle / end of each scene, Full / Half / Quarter quality.
  - Hover a frame to see its layers; click to jump there, double-click to select its layers.
  - **Screenshot** copies the whole board as one image to the clipboard (and saves a PNG).
- **Organizer**: sorts the assets selected in the Project panel into **Audio**, **Footage** and **Images** folders, using the folders your project already has (also `01_Audio`, `Images`, `Img`…) or creating them.
  - All static files count as images: PNG, JPG, PSD, AI, EPS, PDF, SVG…
  - Videos, image sequences and animated GIFs go to Footage.
  - A PSD / AI imported as a composition moves as one item (the comp together with its *Layers* folder).
  - Comps and solids stay where they are.

---

## NeoX Note

A simple Trello-style board inside After Effects: **Window › Extensions › NeoX Note**, or the Note button in NeoX.

- Columns **To Do / Doing / Done** (tabs when the panel is narrow). Add, drag to move or reorder, mark as done, delete with Undo.
- Right-click a card (or click its color dot) for label color, move, open, delete.
- Each card has:
  - a title, status and color label;
  - a **deadline with date and time**, shown red when overdue, lime today, amber within 48 h;
  - a **rich-text note**: headings, bold / italic / underline / strike, text and highlight colors, bullet, numbered and check lists, dividers and links;
  - **images** in the note: paste or drop, resize, place side by side. The first image becomes the card cover.
- Markdown-style shortcuts while typing: `-`, `1.`, `[ ]`, `#` + space, `---` + Enter.

---

## Where your data is stored

| What | Windows | macOS |
|---|---|---|
| NeoX Note board | `%APPDATA%\NeoX\NeoX_Board.json` | `~/Library/Application Support/NeoX/NeoX_Board.json` |
| Note images | `%APPDATA%\NeoX\images\` | `~/Library/Application Support/NeoX/images/` |
| Storyboard frames | `%APPDATA%\NeoX\Storyboard\` | `~/Library/Application Support/NeoX/Storyboard/` |

Back up the `NeoX` folder to keep your board.

---

## What's new

**3.0.0**
- **Update notifications**: NeoX tells you about new versions and installs them for you (see *Updates*).
- **Align Form** in the Align section: **Ring**, **Arc** and **Grid** layouts with Radius / Rows, centred and kept inside the title-safe area.
- **Follow Scale** next to Flip: Center Fit (click), Height Fit and Width Fit (right-click); changes Scale only.
- Fixed: Storyboard's *Start* thumbnail showed the scene's last frame.
- Fixed: True Comp Duplicate with Alt could mention "0 assets" in its message.
- Fixed: options with three choices could pick the wrong one in After Effects.

**2.10.2**
- Organizer: PSD, AI, EPS, PDF, SVG and every other static file go to Images; a PSD / AI imported as a composition moves as one item with its Layers folder.

**2.10.1**
- True Comp Duplicate copies the assets too (footage, images, audio, sequences, solids), each next to its original. Alt + click keeps them shared.

**2.10.0**
- New **Organizer** in Xtra.

**2.9**
- New **True Comp Duplicate** in EasyComp.

**2.8**
- Storyboard: View zoom, Zoom to Fit, scene hover card, cleaner cards.

**2.7**
- Offsetter and Align respect masks.
- Extract Styles works again.
- Split by Line / Word keeps each line's font size and style.
- Storyboard: automatic scene tolerance and faster frames.

**2.6**
- **Storyboard** built on normal comp markers, with live updates and screenshot to clipboard.

# 📦 WackyFlip-ContentPipeline

**Automated Tools for Publishing Games, Assets & Updates**
Internal toolchain for packaging, validating, and distributing Wacky Flip content — including games, sprites, UI assets, translations, and level data — across web, mobile, and editor platforms.

---

## 🚀 Purpose

`WackyFlip-ContentPipeline` powers the delivery system behind the [Wacky Flip](https://wackyflip.com) ecosystem, ensuring that new content is securely bundled, versioned, and published across environments with minimal friction.

It supports **CI/CD pipelines**, **hot content reloads**, and **multi-platform packaging** for everything from single-level games to global asset packs.

---

## 🧰 Core Features

| Feature                   | Description                                                                       |
| ------------------------- | --------------------------------------------------------------------------------- |
| 📁 **Content Bundler**    | Packages levels, metadata, art assets, configs, and sound into deployable units   |
| 🔄 **Version Manager**    | Auto-increments versions, generates changelogs, and manages semver across modules |
| 🌐 **Platform Deployer**  | Pushes bundles to Web, Mobile, Labs, and Sandbox targets                          |
| 🧪 **Validation Layer**   | Runs automated QA on levels (broken objects, dead-ends, missing assets)           |
| 📤 **Delta Uploader**     | Publishes only changed files to CDN or target S3 buckets                          |
| 🔄 **Auto-Sync**          | Syncs content between game engine and live deployment                             |
| 📝 **Manifest Generator** | Builds content manifests with hash-checks and meta-data for integrity checks      |

---

## 🧱 Content Types

* 🕹️ Game Modules (levels, physics configs, spawn tables)
* 🎨 Sprites, UI packs, animations (from `WackyFlip-Assets`)
* 🌍 Localization files (from `WackyFlip-Locale`)
* 🔊 Audio bundles (from `WackyFlip-Audio`)
* 🎮 Mini-games & labs (from `WackyFlip-Minis`, `WackyFlip-Labs`)
* ⚙️ Editor exports (from `WackyFlip-DevTools`)

---

## 📂 Project Structure

```
WackyFlip-ContentPipeline/
├─ bundlers/            # Game, Asset, Audio, and Locale packagers
├─ validators/          # Linting and QA checks for level data
├─ publishers/          # Push to CDN/S3/staging environments
├─ manifests/           # Versioned content registry
├─ cli/                 # Command-line interface for internal devs
├─ scripts/             # CI-friendly publishing scripts
├─ docs/                # Developer docs and setup guides
└─ README.md
```

---

## ⚙️ CLI Commands

```bash
# Bundle and publish latest mini-game
wackyflip-pipeline bundle game --input=./games/NoobFlip --platform=web

# Deploy new asset pack to mobile and labs
wackyflip-pipeline publish assets --target=mobile,labs

# Validate level design before packaging
wackyflip-pipeline validate levels/flip_mania.json
```

---

## 🔄 Integration with CI/CD

Used by `WackyFlip-CI` in GitHub Actions and GitLab Runners to:

* Trigger builds on merge
* Run validators
* Publish bundles to staging or production
* Generate content manifests and update CDN cache

---

## 🧪 Example Output

```json
{
  "game": "BottleFlip",
  "version": "1.4.2",
  "platforms": ["web", "mobile"],
  "assetsHash": "c2a89e1d",
  "bundleSize": "4.6MB",
  "manifestUrl": "https://cdn.wackyflip.com/manifests/bottleflip_1.4.2.json"
}
```

---

## 📘 Developer Docs

* [docs/setup.md](docs/setup.md): Local dev setup
* [docs/bundling.md](docs/bundling.md): How to create game/asset bundles
* [docs/deploy.md](docs/deploy.md): Deployment and versioning
* [docs/ci-config.md](docs/ci-config.md): Integrating with CI pipelines

---

## 🧩 Related Repos

* [`WackyFlip-Web`](https://github.com/wackyflipgame/WackyFlip-Web) – consumes published manifests
* [`WackyFlip-DevTools`](https://github.com/wackyflipgame/WackyFlip-DevTools) – sources content from internal editors
* [`WackyFlip-Labs`](https://github.com/wackyflipgame/WackyFlip-Labs) – tests bundles before going live
* [`WackyFlip-CI`](https://github.com/wackyflipgame/WackyFlip-CI) – manages automated builds and publishing
* [`WackyFlip-Stats`](https://github.com/wackyflipgame/WackyFlip-Stats) – logs content delivery performance

---

## 🛡️ License

**Private/Internal** – For use only by Wacky Flip development team.

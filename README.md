# Reveal the Dream, desktop installers

Signed and notarised desktop builds of [Reveal the Dream](https://revealthedream.com).

**Download from [revealthedream.com/download](https://revealthedream.com/download)** rather than
from here. That page sends you to the current build for your platform and will keep working if
these files ever move.

| Platform | File | Requirements |
|---|---|---|
| macOS | `RevealTheDream.dmg` | macOS 14 or later, Apple silicon or Intel |
| Windows | coming soon | |

The mobile and watch apps are on the App Store and Google Play, not here.

## What this repository is

Installers only. **There is no source code here and there never will be.** The application source
is private. This repository exists so the builds have a stable public home with a CDN in front of
them, and it holds nothing but this README and a release workflow.

The installers are attached as **release assets**, not committed to the repository, so cloning it
costs nothing and the binaries never enter git history.

## latest.json

Each release carries a small manifest so the website and the app can resolve the current build
without anything hardcoding a filename:

```json
{
  "buildEpoch": 0,
  "version": "1.0.0",
  "macUrl": "https://github.com/none298-dotcom/revealthedream-installers/releases/download/latest/RevealTheDream.dmg",
  "winUrl": null
}
```

`winUrl` is null until the Windows build exists. Anything reading this must handle null rather
than assume both platforms are present.

## Verifying a download

macOS builds are signed with Developer ID "Augustus Travels LLC (ZX4XWHUB9W)" and notarised by
Apple, with the ticket stapled so a first launch works offline. To check a download yourself:

```
spctl -a -t open --context context:primary-signature -vv RevealTheDream.dmg
```

It should say `accepted` and `source=Notarized Developer ID`.

## Reporting a problem

Please use [revealthedream.com/support](https://revealthedream.com/support.html). Issues are not
monitored on this repository.

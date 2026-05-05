Recommended commit grouping and deployment steps

Suggested commits (group related changes together):

- feat(assets): make asset downloads non-blocking; add asset browser UI
  - Files: changes in `src/main/kotlin/io/unthrottled/amii/assets/*`, `src/main/java/.../CustomMemeList.*`

- fix(threading): ensure EDT-safety for meme display and services; dispose readers
  - Files: `src/main/kotlin/io/unthrottled/amii/memes/*`, `src/main/kotlin/io/unthrottled/amii/services/*`, `src/main/kotlin/io/unthrottled/amii/services/GifService.kt`

- refactor(ui): PluginSettingsUI cleanup, parsing helpers, and disposal
  - Files: `src/main/java/io/unthrottled/amii/config/ui/PluginSettingsUI.java`

- test: add regression/unit tests for asset managers and project lifecycle
  - Files: `src/test/kotlin/...` (new tests)

One-line commit examples (pick grouping you prefer):

```bash
git add -A
git commit -m "feat(assets): non-blocking asset downloads and custom asset browser"
git commit -m "fix(threading): ensure EDT-safety for meme display and services"
git commit -m "refactor(settings): PluginSettingsUI parsing and helpers"
git commit -m "test: add regression tests for asset and lifecycle managers"
git tag -a v1.6.1 -m "Release v1.6.1"
git push origin HEAD
git push origin v1.6.1
```

If you prefer a single commit instead (squash):

```bash
git add -A
git commit -m "chore(release): prepare 1.6.1 — assets non-blocking, UI improvements, threading fixes, tests"
git tag -a v1.6.1 -m "Release v1.6.1"
git push origin HEAD --follow-tags
```

Notes

- Run the test suite locally before tagging: `./gradlew test`.
- If CI runs formatting or checks, ensure they pass and fix problems before merging.
- Update the version in build files if your release process requires it.

# Aoba Video and Mamoru

Two standalone, browser-based prototypes for exploring video safety workflows:

- **Aoba Video** checks uploads for an exact SHA-256 duplicate. The first harmless test clip is allowed in the simulation; an identical file is blocked on a later attempt.
- **Mamoru 守る** provides on-device fingerprint tools, practical safety resources, and an optional local Ollama assistant for users who are unsure what to do next.

These are prototypes, not real hosting, reporting, takedown, licensing, or blocking services. Aoba does not upload or publish videos to a platform. Its duplicate history is kept in the current browser's local storage and can be reset from the page. Exact SHA-256 matching only detects byte-identical files; edited or re-encoded copies have different hashes.

## Open the sites

Open [index.html](./index.html) in a browser, then choose a site:

- [Aoba Video — Duplicate Upload Demo](./Aoba%20Video%20%E2%80%94%20Duplicate%20Upload%20Demo.html)
- [Mamoru 守る — Private Video Safety Assistant](./Mamoru%20%E5%AE%88%E3%82%8B%20%E2%80%93%20Video%20hash%20protection%20demo.html)

No Node.js packages or build step are required. A current Chromium-based browser is recommended. Use only harmless videos that you have permission to process.

## Try Aoba's duplicate check

1. Open Aoba Video and select a harmless test video.
2. Confirm the adult/permission checkbox and select **Check & simulate upload**. The first copy is allowed in the local demo.
3. Select the exact same file again. Its matching SHA-256 hash is blocked before the simulated publish step.
4. Use **Reset demo history** to clear the browser-local duplicate list.

## Use Mamoru's local AI helper

The safety guide and fingerprint tools work without an AI model. To use the optional chat helper:

1. Install [Ollama](https://ollama.com/download) on this device and start it.
2. Download a local model in a terminal, for example:

   ```powershell
   ollama pull qwen2.5:3b
   ```

3. Open Mamoru, select **Get help**, leave the Ollama address as `http://127.0.0.1:11434`, and use the installed model name `qwen2.5:3b` (or enter a different installed model).
4. Select **Check local model**, then ask a question.

Mamoru sends the question only to the Ollama service on this device. The page does not save chat questions or answers. Do not enter names, account details, links, or video content. The assistant can make mistakes and is not a substitute for emergency, legal, or professional support. For urgent situations use the official local resources shown in Mamoru.

If browser security prevents a page opened directly from disk (`file://`) from connecting to Ollama, serve this folder from localhost or configure Ollama to allow the page's local browser origin. Do not expose the Ollama API to the public internet.

## Safety and privacy

- Do not select, hash, upload, download, or share sexual content involving anyone who was under 18 when recorded. Use Mamoru's fixed safety guidance and contact a trusted adult or appropriate local support.
- Fingerprints can be sensitive information. Keep them private; remove saved fingerprints when no longer needed.
- AI-generated guidance may be incorrect. Prefer the fixed safety checklist and official support resources for sensitive decisions.
- Nothing in these pages contacts a real platform, reports content, performs takedowns, or prevents an actual upload.

## Hosting

The pages are static HTML and can be served by any static web host. For GitHub Pages, publish the repository's root from the `main` branch in the repository's **Settings → Pages**. The Mamoru chat still requires Ollama running on the visitor's own device; a hosted site does not host or share that local model.

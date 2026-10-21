# ModelSeal

Permanent fingerprints for open AI models.

ModelSeal hashes AI model files (SHA-256) locally in the browser, builds a small JSON manifest, and anchors it permanently on Arweave. Anyone can later verify a downloaded file against that record: **Match**, **Mismatch** or **Unknown**.

- No backend. Files never leave your device.
- Streaming hashing (8 MB chunks via hash-wasm) handles multi-GB files.
- Verify by Arweave transaction ID, by model-name tag search (Arweave GraphQL), or by pasting a manifest.
- Publish via ArDrive (free under 100 KB) or the Wander wallet.

## Run
Open `index.html` in a browser, or deploy the folder to GitHub Pages / Vercel / Netlify.

## Manifest format (`modelseal/1`)
```json
{ "app": "ModelSeal", "schema": "modelseal/1", "model": "name", "version": "v1.0",
  "licence": null, "author": null, "source": null, "sealedAt": "ISO-8601",
  "files": [ { "name": "model.safetensors", "size": 123, "sha256": "hex" } ] }
```
Arweave tags: `App-Name=ModelSeal`, `Model-Name`, `Model-Version`, `Content-Type=application/json`.

## Limitations
A fingerprint proves a file is unchanged since sealing. It does not prove the model is safe or that the sealer is the real author. Author wallet signatures are on the roadmap.

Built by Lawal Ridwan for the HackerNoon Decentralize AI Hackathon. MIT licence.

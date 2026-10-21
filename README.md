# DSH Market

Public plugin index for the `weft-audit` DeepSeek Harness plugin family.

This repository is metadata-only. It contains no executable plugin code and no
credentials. The source of truth is [`plugin_index.json`](plugin_index.json);
each plugin remains owned and tested in its own repository.

## Plugins

| Plugin | Purpose |
|---|---|
| [`dsh-guardrail`](https://github.com/weft-audit/dsh-guardrail) | Hard safety checks plus soft gap hints |
| [`dsh-audit`](https://github.com/weft-audit/dsh-audit) | Fixed-rubric 0–10 scorer; scores only |
| [`dsh-ledger`](https://github.com/weft-audit/dsh-ledger) | Append-only usage ledger and reports |
| [`dsh-checkpoint`](https://github.com/weft-audit/dsh-checkpoint) | Checkpoint and resume protocol without automatic execution |
| [`dsh-judgement`](https://github.com/weft-audit/dsh-judgement) | Twenty-item judgement checklist skill |
| [`dsh-dod`](https://github.com/weft-audit/dsh-dod) | Evidence-first completion hints and report checker |

## Install

Install from a plugin repository according to the target DSH profile:

```bash
dsh plugin --profile web add git+https://github.com/weft-audit/dsh-guardrail
```

Replace the final repository name with the plugin you need. Follow that
plugin's README for tests, tool permissions, and known limitations.

## Index contract

- `format` identifies the index schema generation;
- every `versions[].source.commit` pins the published source revision;
- `engines.dsh` records the supported Harness range;
- plugin descriptions must not imply capabilities that are absent from the
  linked source repository.

## Validation

```powershell
$index = Get-Content .\plugin_index.json -Raw | ConvertFrom-Json
$index.plugins.Count
```

Expected count: `6`.

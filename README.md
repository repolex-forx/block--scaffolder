# Repolex Knowledge Graph of block/scaffolder

RDF knowledge graph data for [block/scaffolder](https://github.com/block/scaffolder), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download block/scaffolder
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── fdfb0f43471e1e5011ee4b95e62653f1529e9027
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── fdfb0f43471e1e5011ee4b95e62653f1529e9027.nq.gz
│   └── repolex
│       └── fdfb0f43471e1e5011ee4b95e62653f1529e9027
│           └── chunk-001.nq.gz
├── blob
│   ├── 03e2c411cda186665d6d60df39a8e78dd20fa04f.nq.gz
│   ├── 05d5a01c7f80c40d99fb00fd9a160111e230be1c.nq.gz
│   ├── 132784aabf9616363faffee13f31ea5004c93682.nq.gz
│   ├── 133f18c58c8d2d2a5095f86bdd76305f33b64bf0.nq.gz
│   ├── 1bcd5debd89d2daf74b6ff500721412fd0a66f5f.nq.gz
│   ├── 2394b051774840f839a8e2844fc9c6a38183e9b7.nq.gz
│   ├── 276afa520d160c9bbc44614ed6088ea09582d49d.nq.gz
│   ├── 28ea5a7467f83ab576ca9a7a044e2621dce69089.nq.gz
│   ├── 2c8ea520df82b74c19deee380dfcffcd6913e2a9.nq.gz
│   ├── 383f4511d444516caed0fd113ee8a2b640cd2290.nq.gz
│   ├── 47e4c5a4915f1c106cf29759e9fb9bf0b710363e.nq.gz
│   ├── 56d54f0c27dafb44fb059d298c317698ddeb001e.nq.gz
│   ├── 659b36b065b2432d374a6700e386531120365744.nq.gz
│   ├── 666839a354d56f0f9b2cb9251f1a9a79ac019877.nq.gz
│   ├── 7ea5c9c0cafc5ea7ec10ddbde94f439979c3545e.nq.gz
│   ├── 7fd3466bbc115c1ec9feaca3de439d82758c119d.nq.gz
│   ├── 7fef769248e85eab6c828b9f2f7b802296cddadc.nq.gz
│   ├── 816066f4755caecbea428ebfe33fecd477e0bb7e.nq.gz
│   ├── 8da40da65a507e634b163b69ad7ad5749eecb7dd.nq.gz
│   ├── 92c401c8d7c9b9aa3d5831ab4a0cdb38f8c78f24.nq.gz
│   ├── 9fed50950ad0bf59491677eadd7f9a22979b704f.nq.gz
│   ├── a1ff073f84616432496d9f764efc45136beba5d0.nq.gz
│   ├── a4f108cc7a92e2abe1a8e3acec50c5001a9479b5.nq.gz
│   ├── a651caf1f0f65b7dcb094921e75aa1fe63f9aa56.nq.gz
│   ├── b2c90a4174587884f23ab47e9246de0082034f1d.nq.gz
│   ├── c20c86f94d050a20490440f52ae1078a751d645c.nq.gz
│   ├── c88525427884f4bc2901b093409e675349e5b052.nq.gz
│   ├── dc9c890a09a7386db80b1e7d3b0bd81fc04bd72c.nq.gz
│   ├── e63104de0f4da91f090f7b399e1feb95144cfce9.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e889550ba4cbc92a720527042e5f6e7a303bfcbc.nq.gz
│   ├── ecb626b805a01629eed646a1c5edfa512f5cac5f.nq.gz
│   ├── f49a4e16e68b128803cc2dcea614603632b04eac.nq.gz
│   ├── fd20040a28d88e6a279743171b00101e9afc3adc.nq.gz
│   ├── fe0867819936afc4af0bf1512d453bc7465e7db2.nq.gz
│   ├── fe28214d3352b0ed40820a4999317694c8b1ef57.nq.gz
│   └── fe4e76db24ffb8bf4beb0f10dc916d29a37b90ea.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── fdfb0f43471e1e5011ee4b95e62653f1529e9027.nq.gz
├── filetree
│   └── fdfb0f43471e1e5011ee4b95e62653f1529e9027.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

15 directories, 47 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[block/scaffolder](https://github.com/block/scaffolder)

---
*Parsed on 2026-10-01 by [repolex](https://repolex.ai)*

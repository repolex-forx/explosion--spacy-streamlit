# Repolex Knowledge Graph of explosion/spacy-streamlit

RDF knowledge graph data for [explosion/spacy-streamlit](https://github.com/explosion/spacy-streamlit), parsed by [repolex](https://repolex.ai).

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
rlex download explosion/spacy-streamlit
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 715d463ff3e00097ee638f52aba971651bd74b38
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 715d463ff3e00097ee638f52aba971651bd74b38
│           └── chunk-001.nq.gz
├── blob
│   ├── 28089f6e42c1301e0cc47cc7395755ef7f195beb.nq.gz
│   ├── 44bd66b30373ece3adf816b51d8f1424c755aa91.nq.gz
│   ├── 48869cb89148410c4134cdb359226685e9213647.nq.gz
│   ├── 4d73207f320f3fb514ecb1303429ca9357b02419.nq.gz
│   ├── 5162d9b6642d318e335bf19db111d185689884a9.nq.gz
│   ├── 599dedb394a84713298d760cb5ecb6c90bcad01f.nq.gz
│   ├── 663e635189cb081a7e5f089cc1bf0327204bc07c.nq.gz
│   ├── 6685713e92fa8b4dd140494f339b17d08b8b1cd5.nq.gz
│   ├── 914186e6533591b673cff3ba739b45c2951eedec.nq.gz
│   ├── b0fc79bf559859e0856b0729cbc3f19a90455ff3.nq.gz
│   ├── bc32f7f5fb58b57405886e6ce36ac9089911d417.nq.gz
│   ├── c0dbc6eba8638a446404ae7e9c1d4809ef8be57a.nq.gz
│   ├── d4c184faa04d4066a01cc9816eacc12a0479f14f.nq.gz
│   ├── d732f9d31c028f8db81e650e01410b0e8d8bb38f.nq.gz
│   └── e730561ad2b2697235fa3ffa693146d931bb30b6.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 715d463ff3e00097ee638f52aba971651bd74b38.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 23 files
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

[explosion/spacy-streamlit](https://github.com/explosion/spacy-streamlit)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*

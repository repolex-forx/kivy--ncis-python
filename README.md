# Repolex Knowledge Graph of kivy/ncis-python

RDF knowledge graph data for [kivy/ncis-python](https://github.com/kivy/ncis-python), parsed by [repolex](https://repolex.ai).

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
rlex download kivy/ncis-python
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── e70e138cd3bdae41b62103056cba5e1afbe5d9be
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── e70e138cd3bdae41b62103056cba5e1afbe5d9be
│           └── chunk-001.nq.gz
├── blob
│   ├── 38c34d10ef60c6fbe560c18d1fd27eb2e708ec1f.nq.gz
│   ├── 5a25821ae138f1cdf7531defcff73958555a036b.nq.gz
│   ├── 8ab41ebd5ad624ea73199d37b83711a93ccb67d9.nq.gz
│   └── dc96e8fe206a1a8064dd4554b1ee18cb166a4dd6.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── e70e138cd3bdae41b62103056cba5e1afbe5d9be.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 10 files
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

[kivy/ncis-python](https://github.com/kivy/ncis-python)

---
*Parsed on 2026-11-07 by [repolex](https://repolex.ai)*

# Repolex Knowledge Graph of ActiveState/ez_setup

RDF knowledge graph data for [ActiveState/ez_setup](https://github.com/ActiveState/ez_setup), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [lexq](https://github.com/repolex-ai/lexq) query tool using [uv](https://docs.astral.sh/uv/getting-started/installation/).

If you have uv installed, just copy/paste this into your terminal:

```bash
uv tool install git+https://github.com/repolex-ai/lexq
```

This installs lexq onto your system, in your user context. Verify the install:

```bash
lexq --help
```

**lexq is designed to be used primarily by LLMs in a terminal.** Start up your favorite LLM and ask it to use the lexq tool. It's that easy!

To load this repo's data:

```bash
lexq download ActiveState/ez_setup
```

This will automatically download essential data files from the last parsed commit. Consult `lexq --moreinfo` for other options, including downloading multiple commits, blobs, etc.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 3afe93e5b1bb1c3dd8c37cff614d00a41215c6f1
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── 3afe93e5b1bb1c3dd8c37cff614d00a41215c6f1.nq.gz
│   └── repolex
│       └── 3afe93e5b1bb1c3dd8c37cff614d00a41215c6f1
│           └── chunk-001.nq.gz
├── blob
│   ├── 1e7e5684768fe0489618cb06dc1e19f9d3d36e75.nq.gz
│   ├── 3ea2e667f1eda6cf54465a0acccfdff587a60663.nq.gz
│   ├── 3f52e52fb5c451d71c8cacf047990ae2ceed1144.nq.gz
│   ├── 659163648ccf8a0076c788c1300a2ed4cf228c8b.nq.gz
│   ├── c0510a9573b25f928aea92cbf2c0c9a52b508355.nq.gz
│   ├── dfb5e0103c76c72ae5c976b163bcd11cdf3acc11.nq.gz
│   └── fba2675ae7ece409d2d0d6b1f1be910eb3aaa4e4.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── 3afe93e5b1bb1c3dd8c37cff614d00a41215c6f1.nq.gz
├── filetree
│   └── 3afe93e5b1bb1c3dd8c37cff614d00a41215c6f1.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

15 directories, 17 files
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

## Source repository

[ActiveState/ez_setup](https://github.com/ActiveState/ez_setup)

---
*Parsed on 2026-04-13 by [repolex](https://repolex.ai)*

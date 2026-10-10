# Repolex Knowledge Graph of tiangolo/issue-manager

RDF knowledge graph data for [tiangolo/issue-manager](https://github.com/tiangolo/issue-manager), parsed by [repolex](https://repolex.ai).

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
rlex download tiangolo/issue-manager
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 0863a9cf6ea59164b173655b37bffafadd33ff95
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 0863a9cf6ea59164b173655b37bffafadd33ff95
│           └── chunk-001.nq.gz
├── blob
│   ├── 050612cd5278e851510e16222d2a514f31f8ecf8.nq.gz
│   ├── 06d3d52d218ed67eb054fe9d3d5879134bb56bb3.nq.gz
│   ├── 0aef27b95914857e95cb3c04e9106cb3aa80baff.nq.gz
│   ├── 2ce119b1663387d64814ff31410435239b2c6b30.nq.gz
│   ├── 30c64322fc91164ead15bac265b13287ba2c4ef7.nq.gz
│   ├── 30f6eb1d40a89985cd77e10b82bc165a3377bcf3.nq.gz
│   ├── 53887134038db3bd26277a5c5cec9c08eaeba335.nq.gz
│   ├── 6d0ca61c391c0d54fa97e1e8244139dea29c09cf.nq.gz
│   ├── 7de020be2101308831faf589e3154f4cdec03eb8.nq.gz
│   ├── 85876665e0a2da58f86c38d1489ff411c8904da5.nq.gz
│   ├── ab691199d2e4f6fb95883a26c9406c4a58d7e564.nq.gz
│   ├── b4687aa9c747cd37ccfbd727110ddec9c19204f9.nq.gz
│   ├── c20ec0520356b86126db3a3c73296d7a56e2fef1.nq.gz
│   ├── c92884c533538ace679c62dff0dc9e1eff30662f.nq.gz
│   ├── d30386da51824a9cf582bdc25cc692a96d1a3521.nq.gz
│   ├── f11987b50cfa15ae4f99d4c559137458c87d7a69.nq.gz
│   └── ff0e915742532dd3af88c3285d7f86ec83120849.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 0863a9cf6ea59164b173655b37bffafadd33ff95.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 25 files
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

[tiangolo/issue-manager](https://github.com/tiangolo/issue-manager)

---
*Parsed on 2026-10-10 by [repolex](https://repolex.ai)*

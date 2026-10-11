# Repolex Knowledge Graph of python-trio/ahip

RDF knowledge graph data for [python-trio/ahip](https://github.com/python-trio/ahip), parsed by [repolex](https://repolex.ai).

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
rlex download python-trio/ahip
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── a0085fd9a76fa652ec90b81129907fd6156dcd2a
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── a0085fd9a76fa652ec90b81129907fd6156dcd2a
│           └── chunk-001.nq.gz
├── blob
│   ├── a2f71c25642baa340d7075abf07495a58e71f56f.nq.gz
│   ├── b185fc15b3ef363d8457b93e284b6761a63aa841.nq.gz
│   ├── bb3ec5f0d4c70ef732aa4d399282a5ddb2a008fd.nq.gz
│   └── c9cc9cbd5250b6275a11e88e6591c118f2558c7b.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── a0085fd9a76fa652ec90b81129907fd6156dcd2a.nq.gz
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

[python-trio/ahip](https://github.com/python-trio/ahip)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*

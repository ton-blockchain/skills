# TON dev skills

Reusable coding-agent skills for Acton, Tolk, TON, and FunC-to-Tolk workflows.

These skills help coding agents working on TON smart contracts write code, choose the right
docs, commands, project layout, and safety checks before editing code.

**Note**: Skills guide the assistant, but they do not replace local validation.

## Available skills

- [`acton`](./acton): Acton CLI workflows for installation and updates, project
  creation, `Acton.toml` configuration, builds, single-file compilation,
  wrapper generation, tests, scripts, wallets, verification, RPC inspection,
  libraries, linting, formatting, hooks, IDE support, and troubleshooting.
- [`tolk`](./tolk): Writing, reviewing, debugging, and testing idiomatic Tolk
  smart contracts. Covers typed storage and message schemas, union dispatch,
  auto-serialization, typed maps, explicit bounce and fee behavior, standard
  getter shapes, and focused contract tests.
- [`func2tolk`](./func2tolk): Porting FunC contracts to idiomatic Tolk while
  preserving TL-B layouts, opcodes, error codes, send modes, bounce behavior,
  and observable behavior. Combines `acton func2tolk` with a compatibility and
  refactoring checklist.
- [`ton-blockchain`](./ton-blockchain): TON ecosystem context and standards.
  Sends agents to primary TON Docs for TL-B, TVM, cells, BoC, Jettons, wallets,
  TON Connect, workchains, shardchains, liteservers, and other blockchain
  concepts.

## Installation

Use `npx skills add -g` to install Acton skills globally:

```bash
npx skills add -g https://github.com/ton-blockchain/skills
```

Remove the `-g` flag to install skills in the current project only:

```bash
npx skills add https://github.com/ton-blockchain/skills
```

Pass `-a <AGENT_NAME>` to install skills for a specific agent only:

```bash
# Codex
npx skills add -a codex https://github.com/ton-blockchain/skills

# Claude Code
npx skills add -a claude-code https://github.com/ton-blockchain/skills
```

Install an individual skill by changing the final path:

```bash
npx skills add https://github.com/ton-blockchain/skills/acton
npx skills add https://github.com/ton-blockchain/skills/tolk
npx skills add https://github.com/ton-blockchain/skills/func2tolk
npx skills add https://github.com/ton-blockchain/skills/ton-blockchain
```

After installation, mention a skill by name in the coding-agent prompt, for
example `$acton`, `$tolk`, `$ton-blockchain`, or `$func2tolk`.

## Example prompts

```text
$acton inspect this Acton project and tell me the right build/test commands.
```

```text
$tolk review this Jetton wallet contract for typed message parsing, bounce
handling, and getter compatibility.
```

```text
$func2tolk port this FunC contract to idiomatic Tolk and preserve storage and message layout.
```

```text
$ton-blockchain how many references does the cell contain
```

## Repository layout

Each skill is self-contained folder:

- `SKILL.md` contains the instructions loaded by the coding agent.
- `agents/openai.yaml` contains OpenAI agent metadata.
- `references/` contains focused checklists, command maps, examples, and
  troubleshooting notes used by the skill when needed.

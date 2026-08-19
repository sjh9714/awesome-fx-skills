# Awesome fx Skills

A curated list of skills, tools, and resources for [fx](https://github.com/vercel-labs/fx), the tiny open-source coding agent from Vercel Labs.

fx is a 7.8 MiB native agent written in Zig. Its killer feature for skills is compatibility. fx reads standard `SKILL.md` files and discovers them from the directories other agents already use (`.claude/skills/`, `.codex/skills/`, `.agents/skills/`, `.opencode/skills/`, `.claw/skills/`), and extra frontmatter for other agents is simply ignored. Most skills written for Claude Code or Codex run in fx unchanged.

## How skills work in fx

```sh
# install one skill from a repository (goes to ~/.fx/skills/)
/skills install owner/repo --skill skill-name

# browse the interactive catalog
/skills

# inspect without invoking
/skills show skill-name
```

A skill is a directory with a `SKILL.md` (YAML frontmatter, `name` required). Discovery happens at startup, but instructions load only when the skill is invoked, so installed skills cost nothing until used. Docs at [fx.sh/docs/capabilities/skills](https://fx.sh/docs/capabilities/skills).

## Official skills

From [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills), install with `/skills install vercel-labs/agent-skills --skill <name>`.

- **find-skills** - discover and install more skills from inside a session
- **react-best-practices** - React and Next.js performance rules, eliminating request waterfalls and bundle bloat
- **web-design-guidelines** - audit UI code for accessibility, UX, and performance
- **composition-patterns** - component composition and server/client boundary patterns for Next.js
- **react-view-transitions** - the View Transitions API in React and Next.js
- **deploy-to-vercel** - deploy the current project from the session
- **writing-guidelines** - prose style enforcement for docs and READMEs

## Design and visuals

- [diagram-design](https://github.com/cathrynlavery/diagram-design) - editorial technical diagrams as standalone HTML, no Mermaid slop
- [archify](https://github.com/tt-a1i/archify) - verifiable architecture, workflow, and sequence diagrams with motion and crisp export
- [ip-as-logo-skill](https://github.com/s1dashu/ip-as-logo-skill) - rounded mascot logos in one cohesive style (needs an agent with image generation)
- [repo-cover](https://github.com/sjh9714/repo-cover) - designs your repo's GitHub social preview card as one self-contained HTML file, five moods, CJK-first
- [profile-cover](https://github.com/sjh9714/profile-cover) - designs your GitHub profile README as an editorial page with kerned serif mastheads

## Engineering

- [Trail of Bits skills](https://github.com/trailofbits/skills) - security skills for static analysis, variant analysis, and code auditing
- [mattpocock/skills](https://github.com/mattpocock/skills) - TDD, code review, and writing-for-agents skills
- [claude-scientific-skills](https://github.com/K-Dense-AI/claude-scientific-skills) - scientific libraries and databases
- [book-to-skill](https://github.com/Leutenegger/book-to-skill) - turn a PDF book into a skill

## Workflow

- [get-shit-done](https://github.com/gsd-build/get-shit-done) - lightweight meta-prompting and spec-driven development
- [superpowers](https://github.com/obra/superpowers) - process skills for brainstorming, debugging, and TDD discipline

## Beyond skills

- [MCP in fx](https://fx.sh/docs/capabilities/mcp) - connect external tools through the Model Context Protocol
- [Subagents](https://fx.sh/docs/capabilities/subagents) - delegate independent work
- [WebAssembly SDK](https://github.com/vercel-labs/fx/tree/main/sdk) - embed the agent core or terminal in a JavaScript host
- [ACP](https://fx.sh/docs/using-fx/acp) - connect fx to editors via the Agent Client Protocol
- [fx-gateway-proxy](https://github.com/Xeron2000/fx-gateway-proxy) - route fx through alternative model gateways

## Compatibility notes

- fx ignores frontmatter fields it does not know, so skills carrying Claude or Codex metadata load fine.
- Managed installs always land in `~/.fx/skills/`; fx never writes into another agent's directory.
- A skill that shells out to tools (Python, Chrome, gh) works when those tools exist on your machine, same as in any other agent.

## Contributing

One skill or resource per PR. Format: `- [name](url) - what it does in one honest line.` Requirements: a valid `SKILL.md`, open source, and you have actually run it in fx or a compatible agent. No SaaS funnels.

## License

[CC0](LICENSE)

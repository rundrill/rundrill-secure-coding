# RunDrill Secure Coding

Your personal **secure-coding coach** inside your AI agent — learn to find, exploit, and fix the
vulnerabilities that ship in real software: **injection** (SQL, command, XXE, SSTI), **XSS**, **broken
authentication and access control** (sessions, CSRF, IDOR, JWT, OAuth), **weak cryptography**, **SSRF**,
**insecure deserialization**, **supply-chain** and **AI** risks. Short targeted drills, an honest
picture of where you are, and mistake memory that resurfaces the vulnerability classes you got wrong.
Your level and progress live on the RunDrill MCP server (`mcp.rundrill.com`), synced across machines —
not in a local file.

**Why this course is different.** AI assistants write insecure code by default — they concatenate user
input into SQL, render output without encoding, hash passwords with MD5, accept `alg=none` JWTs, and
skip the authorization check. The real risk in the AI era is shipping plausible code that is quietly
exploitable. So this course trains the skill that matters most: the **signature drill hands you a clean,
professional-looking snippet an AI wrote with a planted vulnerability** and asks you to find it, name
the class, explain exactly how an attacker exploits it, and write the fix — like a security pull-request
review. Plus **fix-the-vuln** patching, **exploit-then-fix** against your own local lab, **STRIDE
threat models**, **ASVS checklists**, **taint tracing** from source to sink, and **SAST/SCA triage**.
The coach never writes the fix for you, and every fix is checked against the relevant OWASP ASVS control.

The course walks the OWASP attack surface front to back, across five areas — **Foundations** (secure
SDLC, threat modeling with STRIDE, secure-design principles, common design flaws) → **Input & Output**
(input validation, SQL/command injection, reflected/stored/DOM XSS, output encoding, XXE, SSTI, file
upload, path traversal, SSRF, mass assignment) → **Identity** (password storage, auth bypass and
enumeration, brute-force protection, MFA, password reset, session management and attacks, CSRF, RBAC/ABAC,
IDOR, JWT, OAuth/OIDC, federated identity) → **Data & Crypto** (symmetric/asymmetric encryption, hashing
and MACs, secure random, key management, TLS, HSTS, data protection, client-side storage) → **Platform**
(REST and GraphQL API security, CORS, security headers, business-logic flaws, rate limiting, supply
chain, deserialization, secure configuration and secrets, CI/CD security, logging and error handling,
monitoring, WebRTC, AI prompt injection and model protection). It is grounded in **OWASP ASVS 5.0**, the
**OWASP Cheat Sheet Series**, the **Web Security Testing Guide (WSTG)**, and the **OWASP OCSD**
curriculum, targeting the **OWASP Certified Secure-Software Developer** credential.

**Learn in your language.** The standards, tooling, and job are in English, but you don't have to study
only in English: set your native language and the coach explains in it — keeping all code, payloads,
HTTP headers, tool names, and ASVS/CWE identifiers in English and giving each security term as *native
(English original)*, e.g. *межсайтовый скриптинг (cross-site scripting, XSS)* — so you reason naturally
and still recognise the exact terms on the standard, in the scanner, and on the job.

## Safety

Every exploit or tool drill is run **only against your own local throwaway app or an authorised lab —
never a system you don't own**. The coach states this, and the course teaches defensive secure coding,
not attacks on third parties.

## One plugin, three hosts

The coaching skill (`skills/secure-coding-coach/SKILL.md`) and `.mcp.json` are shared; each host reads
its own manifest and ignores the rest.

| Host | Reads |
|---|---|
| Claude Code / Claude Desktop | `.claude-plugin/plugin.json` + `.mcp.json` |
| OpenAI Codex | `.codex-plugin/plugin.json` + `.mcp.json` |
| Google Antigravity | `plugin.json` + `mcp_config.json` (+ `rules/`) |

The MCP endpoint is `https://mcp.rundrill.com/skills/secure-coding` — the skills-course host, passing
`subject: "secure-coding"`. The server routes on the `/skills` segment and ignores the course name; the
name makes this register as its own MCP server in your agent. On first use the host opens a browser tab
for the OAuth handshake, then closes it — no API key to paste.

## Install

- **Claude Code / Desktop** — via the RunDrill marketplace:
  ```
  /plugin marketplace add rundrill/rundrill
  /plugin install rundrill-secure-coding@rundrill
  ```
  Then run `/secure-coding-coach`.
- **OpenAI Codex** — `codex plugin marketplace add rundrill/rundrill`, then install `rundrill-secure-coding`.
- **Google Antigravity** — drop this folder into `~/.gemini/config/plugins/rundrill-secure-coding/`
  (global) or `<workspace>/.agents/plugins/rundrill-secure-coding/` (workspace-scoped).

## License & attribution

© RunDrill. Licensed under **Creative Commons Attribution-NonCommercial-NoDerivatives 4.0
International (CC BY-NC-ND 4.0)** — full text in [LICENSE](LICENSE). You may view, run, and share this
plugin unchanged, non-commercially, with attribution; you may not use it commercially or publish
modified/derivative versions. For other licensing, contact **hello@rundrill.com**.

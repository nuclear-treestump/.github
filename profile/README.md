# Nuclear Treestump Technologies

> v1.0 - Last Updated: 2026-05-03
 
Python tooling. Mostly supply chain security, with a few research and side projects.
 
Maintainer contact: ikari@nuclear-treestump.com

## Staff
* 0xIkari ([github.com/0xIkari](https://github.com/0xIkari)) - Primary Developer

---
 
## Security tooling
 
### pydepgate
 
[github.com/nuclear-treestump/pydepgate](https://github.com/nuclear-treestump/pydepgate)
 
Static analysis for Python supply chain attacks. pydepgate scans wheels, sdists, installed environments, and individual files for the startup-vector patterns used in real-world incidents like LiteLLM 1.82.8: malicious `.pth` files, `setup.py` payloads, top-level `__init__.py` exec, `sitecustomize.py` and `usercustomize.py` injection, and console-script entry points that fire on import or install.
 
Zero third-party dependencies. Parsers never execute, compile, or import the content they analyze. Findings come with rule IDs, severities, line numbers, and explanations. Output formats include human-readable, JSON, and SARIF.
 
Audience: AppSec teams, package reviewers, developers who want to vet a package before installing it, and anyone who suspects something is off with a Python release.
 
In development: a `depscan` subcommand that takes a `requirements.txt`, resolves the full dependency closure with pip in wheel-only mode (so resolution never executes sdist build hooks), bounces to a direct HTTP fetch for any sdist-only transitive, and produces a combined static-scan report covering direct and transitive packages. A runtime-interdiction `exec` subcommand is roadmapped for v0.4.
 
### PyDepGuard

[github.com/nuclear-treestump/pydepguard](https://github.com/nuclear-treestump/pydepguard)

The broader Python security framework. PyDepGuard covers runtime sandboxing, dependency management, and lockfile verification.

pydepgate's startup-vector engine is designed to eventually integrate with PyDepGuard as a subsystem. The relationship is not yet final: the current intent is integration, but pydepgate may end up the surviving project if its scope grows to cover what PyDepGuard provides. Either way, pydepgate will remain available as a standalone tool. It will not be removed, restricted, or made obsolete by any future consolidation.

If you only need startup-vector protection and static analysis, use pydepgate. If you need the full runtime security model, look here.

---
 
## Research
 
### quintesseract
 
[github.com/nuclear-treestump/quintesseract](https://github.com/nuclear-treestump/quintesseract)
 
Exploratory research into a quinary (base-5) computer. Investigates what computation looks like when the underlying logic has five states instead of two.

Unreleased.

---
 
## Other projects
 
### FoxCAD
 
[github.com/nuclear-treestump/FoxCAD](https://github.com/nuclear-treestump/FoxCAD)
 
A spiritual successor to KeyCAD. Aiming to be the simplest possible CAD tool for people who bounce off AutoCAD or never wanted to learn it in the first place. Background project; progress moves when there is time.

---

## How to read this org
 
Active work is in the security tooling. If you arrived here through a security incident, an audit, or curiosity about pydepgate, that is where to start. Research and other projects move at their own pace.
 
Issues and pull requests are welcome on individual project repositories. For security reports related to a specific tool, open an issue on that repository or email the address above.

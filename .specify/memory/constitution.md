<!--
Sync Impact Report
- Version change: (unversioned template) → 1.0.0
- Modified principles (template placeholder → new title):
  - [PRINCIPLE_1_NAME] → I. Clean Code
  - [PRINCIPLE_2_NAME] → II. Simple UX
  - [PRINCIPLE_3_NAME] → III. Responsive Design
  - [PRINCIPLE_4_NAME] → IV. Minimal Dependencies
  - [PRINCIPLE_5_NAME] → V. No Automated Testing (NON-NEGOTIABLE)
- Added sections: Technology Stack & Version Constraints; Development Workflow & Quality Gates
- Removed sections: none
- Templates: not modified (dependent templates and commands read this constitution at runtime).
  Note: plan/tasks templates may suggest test tasks; Principle V overrides them.
- Deferred TODOs: none
-->

# next-speckit-claude Constitution

## Core Principles

### I. Clean Code

- Code MUST be readable first: descriptive names, small single-purpose functions and components,
  and no dead, commented-out, or speculative code.
- Each module MUST have one clear responsibility; shared logic is extracted only once it is used
  in at least two places (no premature abstraction).
- TypeScript MUST be used for all source files with `strict` mode; `any` is forbidden unless
  justified inline.
- Code MUST pass `npm run lint` with zero errors before it is considered complete.
- Comments explain *why*, not *what*; self-explanatory code needs no comment.

Rationale: Without automated tests (Principle V), readability and simplicity are the primary
defense against defects and the main enabler of safe change.

### II. Simple UX

- Every screen MUST have one obvious primary action; secondary actions are visually subordinate.
- Interfaces MUST use plain language, consistent patterns, and the fewest steps needed to
  complete a task.
- Features MUST NOT add settings, modals, or options unless a user need is stated in the spec.
- Interactive elements MUST provide visible feedback (hover/focus/loading/error states) and be
  keyboard accessible with semantic HTML.

Rationale: Simplicity reduces user error and implementation surface area alike.

### III. Responsive Design

- All UI MUST be mobile-first and usable from 320px width up to large desktop viewports, with no
  horizontal scrolling of page content.
- Layouts MUST use Tailwind responsive utilities (`sm:`, `md:`, `lg:`, …) and fluid flex/grid
  rather than fixed pixel widths.
- Touch targets MUST be at least 44×44px; text MUST remain legible without zooming.
- Images MUST be responsive (e.g. `next/image` with appropriate `sizes`).

Rationale: The application must work equally well on every device users bring.

### IV. Minimal Dependencies

- New runtime or dev dependencies MUST NOT be added unless the need cannot reasonably be met by
  the platform (Web APIs), Next.js, React, Tailwind CSS, or a small amount of local code.
- Any proposed dependency MUST be justified in the feature's plan (need, size, maintenance
  status, alternatives considered) and approved before installation.
- UI component libraries, CSS-in-JS libraries, and state-management libraries are disallowed by
  default; use React built-ins and Tailwind.
- Unused dependencies MUST be removed.

Rationale: Every dependency adds bundle weight, upgrade burden, and supply-chain risk.

### V. No Automated Testing (NON-NEGOTIABLE)

- The project MUST NOT contain unit tests, integration tests, end-to-end tests, or any other
  automated test suites.
- Testing frameworks and tooling (e.g. Jest, Vitest, Testing Library, Playwright, Cypress) MUST
  NOT be installed or configured, and no `test` scripts are to be added to `package.json`.
- Specs, plans, and task lists MUST NOT include test-writing tasks, TDD steps, or test-coverage
  gates.
- This principle SUPERSEDES any other guidance, template, command, or default practice that
  calls for tests. Where any such guidance conflicts, this principle wins.
- Verification is performed through linting, type-checking, a successful `npm run build`, and
  manual review in the browser.

Rationale: Explicit project-owner decision to keep the codebase and workflow lean.

## Technology Stack & Version Constraints

- The project MUST use exactly the framework versions pinned in `package.json`:
  - Next.js `16.4.6` (App Router, `app/` directory)
  - React `19.3.0` and React DOM `19.3.0`
  - Tailwind CSS `4.3.3` (with `@tailwindcss/turbopack` `4.3.3`)
- These versions MUST NOT be upgraded, downgraded, or replaced without a constitution amendment.
- This Next.js version has breaking changes relative to earlier releases. Before writing
  Next.js code, contributors (human or AI) MUST consult the bundled docs in
  `node_modules/next/dist/docs/` and heed deprecation notices rather than relying on prior
  knowledge.
- Styling MUST use Tailwind CSS utilities; custom CSS is limited to what Tailwind cannot express.
- TypeScript is the only permitted source language for application code.

## Development Workflow & Quality Gates

- A change is complete only when all of these pass: `npm run lint` (zero errors), TypeScript
  type-check with no errors, and `npm run build` succeeds.
- Each change MUST be manually checked in the browser at mobile (≈375px) and desktop (≥1280px)
  widths before it is considered done.
- Plans MUST include a Constitution Check confirming compliance with all principles, including
  any dependency justifications required by Principle IV.
- No quality gate may require writing or running automated tests (Principle V).

## Governance

- This constitution supersedes all other practices, templates, and default command behavior.
  Principle V (No Automated Testing) takes precedence over any conflicting guidance anywhere.
- Amendments MUST be made by updating this file via `/speckit-constitution`, with a Sync Impact
  Report describing the change and rationale.
- Versioning follows semantic versioning: MAJOR for removing or redefining principles, MINOR for
  adding principles/sections or materially expanding guidance, PATCH for clarifications and
  wording fixes.
- Every spec, plan, task list, and code review MUST verify compliance; any deviation MUST be
  explicitly justified and approved, or the work MUST be revised.
- Runtime development guidance for agents lives in `AGENTS.md`.

**Version**: 1.0.0 | **Ratified**: 2026-11-25 | **Last Amended**: 2026-11-25

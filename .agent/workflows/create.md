---
description: Create new application command. Triggers App Builder skill and starts interactive dialogue with user.
---

# /create - Create Application

$ARGUMENTS

---

## Task

This command starts a new application creation process.

## Mandatory Rule

Before writing implementation code, complete a **Discovery + Brainstorm + Planning** kickoff.

- If the user provides only a short app idea, **do not jump to scaffolding**.
- Run a structured question round first (goals, users, constraints, risks).
- Produce a clear task list and get confirmation of direction.

### Steps:

1. **Discovery Interview (Required)**
   - Clarify business goal, target users, and success criteria
   - Identify constraints (timeline, budget, team skill, compliance)
   - Confirm non-functional requirements (security, scalability, observability)
   - Define MVP scope vs future scope

2. **Structured Brainstorm (Required)**
   - Generate at least 3 implementation directions
   - Evaluate trade-offs (speed, cost, complexity, maintainability)
   - Recommend one path with reasoning

3. **Request Analysis**
   - Understand what the user wants
   - If information is missing, use `conversation-manager` skill to ask

4. **Project Planning**
   - Use `project-planner` agent for task breakdown
   - Determine tech stack
   - Plan file structure
   - Create `PLAN-{app-slug}.md` with phases, milestones, and acceptance criteria
   - Create `TASKS-{app-slug}.md` with prioritized implementation checklist
   - Ask user to approve plan before build

5. **Application Building (After Approval)**
   - Orchestrate with `app-builder` skill
   - Coordinate expert agents:
     - `database-architect` → Schema
     - `backend-specialist` → API
     - `frontend-specialist` → UI

6. **Preview**
   - Start with `auto_preview.py` when complete
   - Present URL to user

---

## Kickoff Output Contract

When `/create` begins, provide these artifacts before implementation:

1. **Problem Brief** (1-2 paragraphs)
2. **Assumptions & Open Questions**
3. **3+ Solution Options with trade-offs**
4. **Recommended Architecture**
5. **MVP Boundary** (in-scope / out-of-scope)
6. **Execution Plan** (phases + milestones)
7. **Implementation Task List** (atomic tasks)
8. **Top Risks + Mitigations**

---

## Usage Examples

```
/create blog site
/create e-commerce app with product listing and cart
/create todo app
/create Instagram clone
/create crm system with customer management
```

---

## Before Starting

If request is unclear, ask these questions:
- What type of application?
- What are the basic features?
- Who will use it?

Use defaults, add details later.

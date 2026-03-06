# Claude Code Guide  
**Vibe Coder Edition**  

How to talk to Claude so it actually ships instead of philosophizing

2025–2026 era • for people who say "vibe check", "slaps", "just ✨vibes✨"

---

## 0. Golden Rules (tattoo these)

1. **Never start with "Write the best possible…"** → instant 40-page essay  
2. **Temperature 0.7–0.9 energy** → tell it to be based + short + spicy  
3. **One vibe per message** > five vibes in one prompt  
4. **When it yaps** → reply only: `"shorter"`  
5. **Show, don't tell** → paste code/error, don't describe it  
6. **Context is king** → 5 lines of existing code > 500 words of explanation

---

## 1. Prompt Structure (the formula)

### Good Prompt Format
```
[Context: what you're building]
[Problem: what's broke or what you need]
[Constraint: keep it short/use X library/whatever]
[Example: one before/after or error output]
```

### Bad Prompt (don't do)
```
"I need you to create a beautiful, scalable, production-ready solution for managing user authentication 
with comprehensive error handling, logging, and documentation."
```

### Good Prompt (do this)
```
Next.js 14 app handler. I GET a user token from query param, validate it against Redis.
Return 200 + user data if valid, 401 if expired.

Export async function GET(req) {
  // validate token
}

Show me the full GET handler.
```

**Why it works**: Specific file, clear input/output, one job, no fluff.

---

## 2. The Patterns That Slap

### Pattern A: "Fill the gap"
Paste your code → point to the part that's missing → ask to fill it.
```
I have this handler:
[your code here]

Fill in the Redis validation part. Keep it minimal.
```

### Pattern B: "Debug this output"
```
My request returns:
[error or weird output]

Why? (1 sentence explanation + fix)
```

### Pattern C: "Refactor for X"
```
[Show code]

Refactor for readability. Use better variable names.
```

### Pattern D: "Convert this to Y"
```
[SQL query / API endpoint / whatever]

Convert to [format]. Same functionality, no extra bells.
```

---

## 3. What Works / What Doesn't

### ✅ Does Work
- "I got this error [paste error] — fix it"  
- Pasting 20 lines of context code  
- "Make this shorter" / "Make this faster"  
- Specific file types: "TypeScript utility for X"  
- Clear success criteria: "Handle 3 cases: A, B, C"  

### ❌ Doesn't Work
- "Make this enterprise-grade"  
- "Beautiful" / "elegant" / "clean" code requests  
- Vague: "Fix my code" (which code? what's wrong?)  
- 5 different asks in one message  
- "Write tests" without showing test framework  

---

## 4. Real Examples

### Example 1: API Route (works)
```
Next.js 13 API route. GET /api/users/[id]
Validate ID is UUID, fetch from DB, return 404 if not found.
```

### Example 2: Util Function (works)
```
Util function to parse CSV into objects.
Input: string (CSV), Output: Array<{name, email, role}>
Skip rows with missing columns.
```

### Example 3: Bad Example (doesn't work)
```
"I need a way to handle data. Please write a comprehensive solution."
```

**Why**: No language, no context, no constraint.

---

## 5. Pro Tips & Hacks

1. **Start with the error** → paste the full error stack  
2. **Use comments as placeholders** → `// TODO: validate input` → "implement this line"  
3. **Split big tasks** → don't ask for "full auth system", ask for "login handler"  
4. **Type hints matter** → if you show TypeScript types, Claude codes faster  
5. **Say "no X"** → "no regex" / "no dependencies" / "no loops" to constrain it  
6. **Copy good responses** → bookmark 2–3 Claude responses you loved, reuse that vibe  
7. **Show me, then tell me** → paste code that almost works, ask for one fix  

---

## 6. Temperature & Tone Settings

**For code prompts:**
- **Explicit task** → Direct instructions, short  
- **Stuck & creative** → Ask broader, Claude gets curious  
- **Production code** → Show examples, ask for consistency  
- **Learning mode** → Ask "why" and "explain"  

**Magic phrase**: Add at end of prompt:
```
Keep it short. Max [lines/words]. No comments. Go.
```

---

## 7. When Claude Yaps (gets verbose)

**Your move:**
1. Reply: `"shorter"`  
2. Reply: `"tl;dr just the code"`  
3. Reply: `"actually just the [part] I asked for"`  
4. Start fresh prompt, set constraint upfront: `"Max 30 lines."`  

---

## 8. Red Flags (when to not use Claude Code)

- ❌ "Write my entire backend" (split it up)  
- ❌ "Make it work with 47 different services" (one service at a time)  
- ❌ "I'll know it when I see it" (you won't, be specific)  
- ❌ Pasting entire codebase without a target  
- ❌ Asking for best practices (it'll write a book)  

**Fix**: Zoom in. Be surgical. One problem per message.

---

## 9. Workflow (how devs actually use this)

```
1. Stuck on: [describe 1 line]
2. Paste: [the code or error]
3. Ask: [one specific thing]
4. Get: [response in <60 seconds]
5. Copy/test/iterate
```

Repeat 3–4 times per feature. Then move on.

---

## 10. Common Pitfalls & How to Dodge Them

### Pitfall 1: Asking for "optimization"
**Bad**: "Can you optimize this?"  
**Better**: "This runs on 1M rows. Make it faster."

### Pitfall 2: Forgetting context
**Bad**: "Fix this bug in my auth flow"  
**Better**: [paste handler + error log]

### Pitfall 3: Too many constraints
**Bad**: "Write X, Y, Z. Handle edge cases. Add logging."  
**Better**: Ask for X. Then ask for Y separately.

### Pitfall 4: Comparing to "enterprise" code
**Bad**: "Make it enterprise-grade"  
**Better**: "Add error handling for [case]"

### Pitfall 5: Vague architecture questions
**Bad**: "Monorepo or microservices?"  
**Better**: "My 3 packages need shared util code. Best approach?"

---

## 11. Prompting Examples (copy these vibes)

**Get unstuck (2 min)**
```
Auth handler crashes on empty token:
[paste error + code snippet]

Fix without rewriting the whole thing.
```

**Need a function (1 min)**
```
Util: slugify(title: string) -> string
"Hello World!!" -> "hello-world"
Lowercase. Dashes only. No special chars.
```

**Refactor something (3 min)**
```
[paste code]

This is doing too much. Split into 2 functions. Shorter names.
```

**Debug output (2 min)**
```
Getting:
{status: 200, data: null}

Should be:
{status: 200, data: [{id: 1, name: "test"}]}

Why?
```

---

## 12. Tools & Setup That Help

- **Show types** → TypeScript helps Claude code 30% better  
- **Small files** → Paste <100 lines for best results  
- **Git diffs** → If you're refactoring, show what changed  
- **Error traces** → Full stack > summarized message  
- **Live code** → "Here's my current app.tsx" > "I have a React component"  

---

## Final Mantra

> **Code at 3 a.m. Vibe at 3 p.m. Refactor never.**

Ship it. Fix it later. (You won't, but tell yourself that.)

---

## Join the Community

Got tips? Questions? Want to discuss Claude prompting vibes?

**Join us on Telegram**: [https://t.me/swordofshivaji](https://t.me/swordofshivaji)

---

**Last Updated**: 2026  
**For**: Devs who want to Actually Ship™  
**Vibes Only** 🚀
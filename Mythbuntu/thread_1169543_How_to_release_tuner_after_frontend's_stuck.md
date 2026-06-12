---
title: "How to release tuner after frontend's stuck?"
date: 2009-05-25
forum: Mythbuntu
---

### Post by klirik on 2009-05-25
The problem that if the hardware/network/frontend itself not stable and could stuck, the backend actually still serve it.

I have two tunners. And once a frontend stucks, it then (after restarting) connects to another (second) tuner. After the second stuck (finally) - no mo tunners available, and so, it is impossible neither watch live-tv, neither do sheduled recordings. Information center says simple that both tunners are occupied with "watching live-tv" (with no frontends actually working).

For the moment I've found the only way to release the tunners - just to restart backend with "sudo /etc/init.d/myth-backend restart". However, this is not perfect, since it needs sudo, and it needs manual work. If the backend is not available physically, and if the user has no skills with working in command line - it became a real problem (for example - mama of my wife, watching tv on Asus EeePC with mythbuntu knows only about "watch tv" button and wants nothing to do with any "computer deals").

Is any way exists to "reset", or "release" tunners on user level? Or - is any way exists for backed to determine the "death" frontends which actually were disconnected, but by some reasons still occupy the tunners?

---


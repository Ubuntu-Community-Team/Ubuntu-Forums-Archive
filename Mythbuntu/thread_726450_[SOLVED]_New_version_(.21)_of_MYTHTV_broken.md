---
title: "[SOLVED] New version (.21) of MYTHTV broken"
date: 2008-03-16
forum: Mythbuntu
---

### Post by ravalox on 2008-03-16
I let the package manager update to the latest Mythtv, and now it doesn't behave. It loses it's recordings and I can't watch television normally.  I suspect it may be a database issue; but whatever the reason I want to cycle back to the previous mythtv.  Is this practical?  If it is, how do I do it?

---

### Post by lokimon on 2008-03-16
i am having a similar problem where it is no longer playing back video smoothly, and also the mythvideo package no longer works.  during the update, it stayed greyed out and didn't install.

---

### Post by superm1 on 2008-03-16
Mythvideo is a known thing.  You have to let it remove mythdvd since it's now integrated.  Search this forum and there are at least 3 threads on this.

As for not smooth playback, the new deinterlacer by default is more CPU intensive.  You can change it to a different one.

---

### Post by pjman on 2008-03-16
> **superm1 said:**
> As for not smooth playback, the new deinterlacer by default is more CPU intensive.  You can change it to a different one.

Can you tell us where this is located?

Thanks!

---

### Post by superm1 on 2008-03-16
Utilities/Setup->Setup->TV Settings->Playback->Playback profiles.

Choose the resolution that you are working with and hit the Edit button.

The second page in will have "Primary Deinterlacer" and "Fallback Deinterlacer"

---

### Post by pjman on 2008-03-17
That did the trick.

Thank you!

---


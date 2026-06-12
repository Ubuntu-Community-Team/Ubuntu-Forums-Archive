---
title: "[SOLVED] Config Mythtv without graphical frontend"
date: 2008-01-12
forum: Mythbuntu
---

### Post by Braedley on 2008-01-12
So my roommate was messing around with the living room mythtv install, and now we can't see the menu items when myth starts.  He changed the prefs for the rendering engine (I forget what it was before and what it is now).  Is there a way to set the mythtv frontend configurations without actually being in the mythtv frontend?

Thanks

---

### Post by volkswagner on 2008-01-12
You can try to ssh -X with another machine.  Run mythtv It is worth a shot.

---

### Post by superm1 on 2008-01-13
> **volkswagner said:**
> You can try to ssh -X with another machine.  Run mythtv It is worth a shot.
Launch it with

```
mythfrontend -O ThemePainter=qt
```

---

### Post by Braedley on 2008-01-13
> **superm1 said:**
> Launch it with

```
mythfrontend -O ThemePainter=qt
```

Thanks a lot.  Solved the problem.

---


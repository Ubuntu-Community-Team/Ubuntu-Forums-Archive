---
title: "Screen flicker in some apps (OpenGL?)"
date: 2008-06-07
forum: Multimedia Software
---

### Post by Jeztastic on 2008-06-07
Hi

I've been getting really bad flicker in some applications such as google earth, Warsow, Mplayer. I suspect it's an OpenGL problem, as that seems to be the common theme. 

I am using the laptop in my sig, using flrgx as the driver.

Please help!

---

### Post by Jeztastic on 2008-06-09
Bump

---

### Post by prshah on 2008-06-10
> **Jeztastic said:**
> 
I've been getting really bad flicker in some applications such as google earth, Warsow, Mplayer. I suspect it's an OpenGL problem, as that seems to be the common theme. 


Apparently there are known problems with OpenGL, ATI (restricted driver) and Compiz combos. Try (temporarily) setting your System-Preferences-Visual Effects to none; then check with your applications again... any improvement?

---

### Post by Jeztastic on 2008-06-10
That's fixed it. Thanks a lot.

Annoyingly though, compiz forgets all my settings when I switch back to it... Grrr...

---

### Post by prshah on 2008-06-10
> **Jeztastic said:**
> That's fixed it. Thanks a lot.

Annoyingly though, compiz forgets all my settings when I switch back to it... Grrr...

If you switch back using the "Visual effects" panel, it will reset most settings to the default. You can avoid this by starting compiz directly; press Alt+F2, then give the command```
compiz --replace
```

---


---
title: "Jaunty &amp; Intel 945GM : black screen (powersave)"
date: 2009-04-24
forum: Multimedia Software
---

### Post by n808 on 2009-04-24
I just installed Jaunty on a system I have been running Gutsy on, but I can not get the Intel driver to work. The video controller is an Intel Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller.

The screen just goes into power save mode when X11 is starting up. 

The same happens when running directly from the CD. I have had to resort to VESA (Safe) graphics mode.

Any suggestions how to figure this out?

---

### Post by deathspal on 2009-04-24
the rls notes prior to final rls noted problems with almost all Intel i9x5 drivers. I know that My i915 will not return from sleep and hangs x randomly. Scrolling in Firefox is almost a guaranteed trigger hangup. I'm probably going to go back to 8.10 until they improve support for Intel video. Sorry if that doesn't help much. I did see some things about trying the non accelerated vesa drivers (so no effects bah) or trying the new acceleration method. but they claim it is less stable...

---


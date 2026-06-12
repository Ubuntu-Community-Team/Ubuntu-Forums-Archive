---
title: "mythfrontend will not start - segfault"
date: 2009-11-08
forum: Mythbuntu
---

### Post by MountainX on 2009-11-08
I really screwed up. I was trying to fix a crash when I start Live TV and I changed the frontend appearance from using Qt to OpenGL. Now the frontend will not even start up. I get this error:

```
[23741.548836] mythfrontend.re[5912]: segfault at 14 ip 07becea5 sp bf8ab370 error 4 in radeon_dri.so[7ba0000+24f000]
```How do I revert the config so I can at least open the frontend to make config changes?

Here's the backstory:
[http://www.mythtvtalk.com/forum/general/12203-mythtv-fails-4-4-computers-me-sagetv-ok.html](http://www.mythtvtalk.com/forum/general/12203-mythtv-fails-4-4-computers-me-sagetv-ok.html)

---

### Post by SiHa on 2009-11-09
Have a look at post #2 in this thread:
[http://ubuntuforums.org/showthread.php?t=1298444&highlight=qt+opengl](http://ubuntuforums.org/showthread.php?t=1298444&highlight=qt+opengl)

---

### Post by MountainX on 2009-11-09
> **SiHa said:**
> Have a look at post #2 in this thread:
[http://ubuntuforums.org/showthread.php?t=1298444&highlight=qt+opengl](http://ubuntuforums.org/showthread.php?t=1298444&highlight=qt+opengl)

Thanks! That worked.

```
mythfrontend -O ThemePainter=qt
```

---


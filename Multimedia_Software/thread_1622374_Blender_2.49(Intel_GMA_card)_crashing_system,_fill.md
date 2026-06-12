---
title: "Blender 2.49(Intel GMA card) crashing system, filling swap space"
date: 2010-11-15
forum: Multimedia Software
---

### Post by DangerOnTheRanger on 2010-11-15
Blender 2.49 has never worked for me under Lucid. Primarily(besides being complex :) nah, just kidding) because it slows down to a halt, and then freezes the *entire *system after a few minutes.

I discovered(or so I think) the cause of the problem by opening up the System Monitor(**System > Administration > System Monitor**)  and selecting the Resources tab.
I then opened up Blender in window mode(**Applications > Graphics > Blender(windowed)** or **blender -w **in a terminal) and stuck it side by side with the System Monitor.

Lo and behold, after 5 minutes, system RAM usage had not surpassed 30%,
but swap space usage had skyrocketed to *95%!* Unfortunately, I cannot provide a screenshot, because Blender crashed my system soon after.

Anyone else have problems with Blender 2.49?
If so, it would indicate a bug with Blender, and a serious bug at that.

Blender has always had problems with Intel graphics cards, but Intel cards just make the interface scrambled, not something like this.

**System stats:**

Blender version: 2.49 (sub 2)(retrieved, pre-compiled, from software repos)

OpenGL vendor: Tungsten Graphics, Inc
OpenGL version: 2.1 with Mesa 7.7.1
OpenGL renderer: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20091221 2009Q4 x86/MMX/SSE2

I have a DRI driver, so it's not a slow driver issue.

Graphics card: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
Ubuntu version: 10.04(Lucid Lynx)

I would *really *appreciate it if anyone could solve this problem!

---

### Post by DangerOnTheRanger on 2010-11-15
Bump!

---

### Post by DangerOnTheRanger on 2010-11-17
*sigh* bump again...

---


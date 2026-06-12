---
title: "Xorg won't start (but does work) with widescreen TV"
date: 2005-10-29
forum: Multimedia &amp; Video
---

### Post by jonny on 2005-10-29
Setting up a home media server... but have a problem.  I can't get xorg to start when my PC's connected to my flat panel TV (using the regular output, not TV out).  The error log tells me that I've "exceeded my BIOS programmed panel size".

If I hook up a normal flat panel monitor to the same output on the same video card, I can start X without any problem.  If I unplug the monitor and substitute my TV, I get perfect output.

How can I persuade X to start?  Is there a way of telling it not to worry what's on the end of the cable?

---

### Post by jonny on 2005-10-30
Solved the problem by using the offiial nvidia drivers.

---


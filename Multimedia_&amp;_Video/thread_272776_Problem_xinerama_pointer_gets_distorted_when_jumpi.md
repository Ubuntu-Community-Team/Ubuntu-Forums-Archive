---
title: "Problem xinerama: pointer gets distorted when jumping between screens. Any idea?"
date: 2006-10-06
forum: Multimedia &amp; Video
---

### Post by marshallfox on 2006-10-06
Hi,

I have a widescreen LCD monitor (1680x1050) running alongside my old CRT (1600x1200) in dual head mode. Both are connected to an ATI RADEON 9600 (one to the VGA and the other to the DVI otuputs) and the combination fglrx(8.29.6)/xinerama(the one in dapper) works fine except for a small but quite annoyinf detail. Whenever I move the pointer from the LCD (primary) to the CRT it gets completely messed up (it turns into an odd square color pattern the size of a desktop icon). It is very hard to manage windows with such a large pointer 'cause I don't know where I am pointing at... have anyone seen this problem before?

Note: If I dissable xinerama the problem is gone... but so is my extended desktop :(

I'll appreciate any suggestion.

Marshall

---

### Post by dukat on 2006-12-14
Hi, I can backup this.

Running Kubuntu 6.10 with the supplied ATi fglrx Radeon 8.28.08 on Mobility FireGL V5200 (Xinerama Dual Head). Mouse pointer is ok on the primary display, but on the other one (attached to DVI) it becomes this garbled square. 

Note - this didn't happen with Kubuntu 6.06 and the supplied fglrx. 
Very annoying!

---

### Post by dukat on 2006-12-14
Found a fix here:

[http://ubuntuforums.org/showthread.php?t=314162](http://ubuntuforums.org/showthread.php?t=314162)

(worked also for me!)

---


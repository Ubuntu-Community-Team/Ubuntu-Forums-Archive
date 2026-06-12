---
title: "VMware Joost problem"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by willsomebody on 2007-08-10
I recently installed VMware Server through Aoutomatix and then from there installed Windows XP SP2 in VMware.  With that done, I installed Joost in windows, and I apparently do not meet the graphics requirements--Although I do physically--I seem not to in VMware.  It only allotted 16MB of graphics memory, and Joost requires 64.  It said it might work without all requirements fully met, but it does not.  Does anybody know of another way to use Joost in linux or how to adjust emulated video hardware in VMware Server?




I am using Feisty Fawn 7.04 x86 32 bit on an AMD Athlon 64 x2 3200+, with a GeForce FX 5500 with 128MB of graphics RAM, and 1 gig of system RAM.

---

### Post by jpeddicord on 2007-08-12
VMware Server currently does not have the functionality required to use any graphics acceleration. The Workstation edition might, but even then the functionality is alpha.

Also, your troubles will be easier to handle if you refrain from using Automatix. While it is a handy program, it is a support nightmare. You can install VMware server directly from the Add/Remove application as an alternative.

Jacob

---


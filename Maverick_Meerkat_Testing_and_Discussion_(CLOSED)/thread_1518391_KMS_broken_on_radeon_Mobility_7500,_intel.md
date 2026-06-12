---
title: "KMS broken on radeon Mobility 7500, intel"
date: 2010-06-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2010-06-26
After initial Alpha kernel, boot booting on all later kernels freezes on my IBM Thinkpad T40 with ati radeon mobility 7500.  See launchpad bug #598322.

radeon.modeset=0
to turn off KMS fixes it, I think, booted a couple times O.K.

Tried it by hand on boot editing the linux line, then by altering /etc/default/grub to 
quiet splash radeon.modeset=0
worked both times.

Do note on another of my pc's booting Maverick with intel i845G I use
i915.modeset=0

Maverick KMS is buggy on two of my three pc's.  The one that is booting O.K. has Radeon Xpress 200.  I'll check it tonight to see if KMS is in fact on.

Jerry

---

### Post by jerrylamos on 2010-06-26
KMS does appear to work, i.e. Ctrl-Alt-F1 shows tiny print, on  
ATI Technologies Inc RC410 [Radeon Xpress 200]

with Linux version 2.6.35-3-generic-pae (buildd@palmer) (gcc version 4.4.4 (Ubuntu 4.4.4-4ubuntu1) ) #4-Ubuntu SMP Tue Jun 15 01:59:43 UTC 2010

KMS doesn't work on radeon mobility 7500 when System Preferences Monitor is set to external monitor any any Linux version so far past the initial Alpha 1 2.6.34-5.

Jerry

---


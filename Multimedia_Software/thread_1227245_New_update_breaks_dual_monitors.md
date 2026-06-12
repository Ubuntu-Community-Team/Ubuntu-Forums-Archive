---
title: "New update breaks dual monitors"
date: 2009-07-30
forum: Multimedia Software
---

### Post by gazotz on 2009-07-30
I just got a required update on Jaunty, which included a new kernel.  No idea what's in it.  After the reboot, only my first monitor will work.  In Display Preferences, I do Detect Monitors and it's apparently convinced I only have one monitor.

Is anyone else having this problem?  Is a fix in the works, or something I can do?

---

### Post by igorzwx on 2009-07-30
QUOTE:
"I just got a required update on Jaunty, which included a new kernel.  No idea what's in it."

It was perhaps a kernel update.
some security problems
(Pulse +** **the SELinux vulnerability):
[http://ubuntuforums.org/showthread.php?t=1209361](http://ubuntuforums.org/showthread.php?t=1209361)

It looks like they hacked the Linux kernel to make pulse working
and this made the Linux kernel vulnerable to exploits.

some hints, you may find here:
[http://www.theregister.co.uk/2009/07/17/linux_kernel_exploit/comments/](http://www.theregister.co.uk/2009/07/17/linux_kernel_exploit/comments/)

---

### Post by gazotz on 2009-07-30
Thanks, it's good to know what the fix was for.  Can't imagine what that would have to do with breaking dual monitors, though.  Any hints to get my 2nd monitor working again?

---

### Post by igorzwx on 2009-07-30
I have already stopped to fix such things.
Averything changes with each new update.
During some two days, I had the "Brown Screen of Death"
on a regular basis.
It seems that the last update cured this problem

---

### Post by igorzwx on 2009-07-30
I tried to google this problem:
[http://www.google.com/search?q=ubuntu%20New%20update%20breaks%20dual%20monitors&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=ubuntu%20New%20update%20breaks%20dual%20monitors&ie=UTF-8&oe=UTF-8)

---

### Post by Sid_R on 2009-07-30
I'm having the same problem using a projector, I'm actually the very next post after you. I'm glad I'm not the only one having the problem, hopefully a fix is in the works.

---

### Post by gazotz on 2009-07-30
Mine turned out to be a hardware problem.  

While troubleshooting, I checked the other box on the KVM: both monitors were OK.  I tried booting the previous kernel (same problem) and backing out the menu.lst file in /boot/grub (same problem.)  I also booted Vista and had the same problem.  This felt like hardware, especially the KVM.

I powered everything off: tower, both monitors, KVM.  Sat a few minutes.  Reseated the cables.  Powered back on and now it's working OK with both Vista and Jaunty.

Yes, I know I should have tried this before posting.  Hopefully my ideas will help the person having the projector problem.

---


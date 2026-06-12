---
title: "Ubuntu 9.10 &amp; GeForce MX400"
date: 2010-02-28
forum: Multimedia Software
---

### Post by mpn_1990 on 2010-02-28
I currently run Ubuntu on a (very) old Dimension 2100 box for development work and other things I feel Linux is better suited for. 

However, the Intel 82810 integrated graphics controller is pretty much a joke and it was when they first made it. It stole 16MB of my system ram, and video on sites such as YouTube are unwatchable due to the lag. I don't even play games on this system, but the integrated graphics are just so bad, they make general computing unusable. Programs lag when opening, the CPU is always bogged down...it's just made Ubuntu a slow mess.

So, I was thinking of just getting an old cheapo GeForce MX4000 PCI to stick in there (as this system has no AGP port) just to make it somewhat more usable. In Ubuntu 9.10, is there any support for this card? Will I be able to run it at 1280x1024, and will it show any improvement in general computing tasks against the awful 82810?

---

### Post by ShadowTek on 2010-02-28
I just bought an old 420 from Ebay, and it works fine. Actually, I had to use Xubuntu since the computer in question had little RAM. The proprietary drivers are also available for it; I installed them with no problems.

ATI are the ones to avoid. Their proprietary drivers for older cards don't work with the latest Xorg in Ubuntu.

---


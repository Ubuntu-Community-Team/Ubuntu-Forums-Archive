---
title: "Nvidia new proprietary driver - Bugs"
date: 2008-05-12
forum: Multimedia Software
---

### Post by thedevnull on 2008-05-12
I have Ubuntu 8.04 64bit on AMD 64X2 with the Nvidia 8800 GT (XFX) and the Samsung SyncMaster 245bw.

When I first installed I loaded the proprietary Nvidia X.org drivers and they worked flawlessly for all of 10ish reboots and then it stopped.

Randomly on the 10th reboot it started my machine in low graphics mode and then gave me some blurred output that can't be read.  I can see like half the screen blurred and then the Ubuntu logo down beyond where I can click on it.  =(  So I restarted in recovery mode and repaired X config.  There after I try to reconfigure as I had it before but it doesn't ever load right.  Even tried to remove the proprietary driver and re-download and reconfigure it and it doesn't work. Maybe a recent patch broke it? 

Also where did the displayconfig-gtk go?  7.10 did have it but I don't see it in Systems in 8.04.  

Anyone seen this one?

---

### Post by thedevnull on 2008-06-12
Anyone?  The problem just started again today...  :confused:

---

### Post by thedevnull on 2008-06-25
Yeah, so this is a series of known bugs.

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/222407](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/222407)

---


---
title: "nforce3 drivers"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by OptixSoldier on 2007-08-16
Hello, I have just installed ubuntu 6.06 and have installed graphics for my nvidia card via Envy.  I am now trying to install platform drivers, I have downloaded the run file and saved it to the desktop and followed the instructions from here:

[http://www.nvidia.com/object/linux_nforce_1.0-0310.html](http://www.nvidia.com/object/linux_nforce_1.0-0310.html)


When I type sh NFORCE-Linux-x86-1.0-0310-pkg1.run

I get this:

No such file or directory

I really need to get these drivers installed! so if anyone could help me out i'd appreciate it! :)

PS I have installed ubuntu updates via the update manager!

---

### Post by Steve1961 on 2007-08-16
You shouldn't need to install nforce3 drivers as the Linux kernel supports nforce3 boards - unless, that is, you're having problems with an ethernet card or something else that requires special treatment.  If so, drag teh file into your home directory, then type:

sudo sh NFORCE-Linux-x86-1.0-0310-pkg1.run

---

### Post by OptixSoldier on 2007-08-16
Thank you, installed without a problem! :)

---


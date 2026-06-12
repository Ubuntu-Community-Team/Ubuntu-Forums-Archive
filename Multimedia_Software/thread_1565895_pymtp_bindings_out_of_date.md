---
title: "pymtp bindings out of date?"
date: 2010-09-01
forum: Multimedia Software
---

### Post by Huwle on 2010-09-01
I have recently been trying to hack around a MTP plugin for the Exaile music player, but the first hurdle was getting any basic MTP operations to succeed. The following python calls caused a segmentation fault:
```
>>> import pymtp
>>> dev = pymtp.MTP()
>>> dev.connect()
>>> tracks = dev.get_tracklisting()
Segmentation fault
```I had a look at pymtp 0.0.4.1-1 and I think that it is not in sync with the libmtp8 package (version 1.0.2) I have installed on my xubuntu 10.04 system.

I have looked at the libmtp.h file for 1.0.2 and made some changes to pymtp which appear to do the job - no more crash, but I haven't yet tested the other parts of the interface.

Feel free to use the attached patched file. I will try to get it to the package owner for further testing and hopefully an eventual package update.

---

### Post by Huwle on 2010-09-01
See bug [https://bugs.launchpad.net/ubuntu/+source/pymtp/+bug/575091](https://bugs.launchpad.net/ubuntu/+source/pymtp/+bug/575091)

---


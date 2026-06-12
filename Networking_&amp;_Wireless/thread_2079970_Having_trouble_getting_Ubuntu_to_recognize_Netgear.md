---
title: "Having trouble getting Ubuntu to recognize Netgear WNA3100"
date: 2012-11-02
forum: Networking &amp; Wireless
---

### Post by Zuelajindi on 2012-11-02
Hello all, I am in a predicament getting Ubuntu to recognize my USB wireless adapter. When I entered "lsusb" I got the following:

Bus 002 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]

Of course, this was for the one particular hardware. What sort of Linux sorcery will I have to do in order to get Ubuntu to recognize this adapter and therefore make it work? Thanks in advance.

---

### Post by chili555 on 2012-11-02
You will need to install ndiswrapper and the Windows XP .inf and .sys files. Here is a long thread about the process: [http://ubuntuforums.org/showthread.php?t=1965989&highlight=0846%3A9020](http://ubuntuforums.org/showthread.php?t=1965989&highlight=0846%3A9020)

Please help me get you started. Please post:```
lsb_release -d
arch
```Thanks.

---


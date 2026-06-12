---
title: "NETGEAR WNDA3100v2 N600 (Broadcom BCM4323) on 12.04"
date: 2013-04-09
forum: Networking &amp; Wireless
---

### Post by UltPokemonFan on 2013-04-09
Let me start off by saying that I am pretty much a total noob to the forums and Linux in general. I have a NETGEAR WNDA3100v2 N600 Wireless Dual Band USB Adapter and it is currently the only means of accessing the internet on my computer. On Windows 7, the device works 100% perfectly. However, on Ubuntu 12.04 LTS x64, it simply will not work. It comes up in lsusb, as shown below:```
Bus 003 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
```Attached is a document with some other info, including lsusb, iwconfig, etc. If there is anything else I can add, please let me know.
[ATTACH]241168[/ATTACH]

---

### Post by mbm1980 on 2013-04-10
Hi

I'm doing the same right now.
I have the Netgear N600 (0846:9011) device like you and this is what I've found so far:
Read this: [http://ubuntuforums.org/showthread.php?t=2032025](http://ubuntuforums.org/showthread.php?t=2032025)

I'll download that file and run it through ndiswrapper from the repository.
If it doesn't work I'll try to compile ndiswrapper from source, some topics suggests that.

When I have wireless working I'll post here what worked. Good luck. :-)

---

### Post by UltPokemonFan on 2013-04-10
Alright, so I understand I need to install the driver through ndiswrapper, but how should I go about getting it? Since I have no internet on Ubuntu, could I maybe put the packages on a flash drive and install them? If that is possible, what packages will I need?

---

### Post by UltPokemonFan on 2013-04-14
I've gotten the latest version of ndiswrapper from SourceForge, however when I run make to install it I get this error:
```
Makefile:28: *** No .config found in /lib/modules/3.5.0-17-generic/build, please set KBUILD to configured kernel.  Stop.
```
What do I need to do?

---


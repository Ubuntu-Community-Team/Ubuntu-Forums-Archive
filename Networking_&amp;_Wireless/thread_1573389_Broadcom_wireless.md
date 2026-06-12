---
title: "Broadcom wireless"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by irish.inferno on 2010-09-12
Hey guys I just installed Lucid Lynx on my Dell Vostro 1000 laptop.  The problem I'm having is that my wired network card has died on me prior to installation.  I'm having the hardest time finding the required files to make my Broadcom BCM4311 wireless card work without being able to download any packages from the web.  If anyone knows which files I need and which order I should use to install them that would be great.

---

### Post by PRC09 on 2010-09-12
The instructions are for 9.10 but should still work...


[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by irish.inferno on 2010-09-12
When I attempt to install bcmwl-kernel-source it errors with the following.

E: bcmwl-kernel-source: subprocess installed post-installation script returned error exit status 6

---

### Post by bkratz on 2010-09-12
> **irish.inferno said:**
> When I attempt to install bcmwl-kernel-source it errors with the following.

E: bcmwl-kernel-source: subprocess installed post-installation script returned error exit status 6

You might want to look through this bug report, it does have some help in it.

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/584180](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/584180)

---

### Post by irish.inferno on 2010-09-13
I see from the bug report that I need to install dpkg-dev manually when I do I get dependency errors where synaptic tells me that it cannot download the file from the disc even though it is there.  This dependency hell is killing me.

---

### Post by bkratz on 2010-09-13
> **irish.inferno said:**
> I see from the bug report that I need to install dpkg-dev manually when I do I get dependency errors where synaptic tells me that it cannot download the file from the disc even though it is there.  This dependency hell is killing me.

Well, there is an alternate way of implementing the STA driver. See posts 23 and on of this thread. 
[http://ubuntuforums.org/showthread.php?t=1471028&page=3](http://ubuntuforums.org/showthread.php?t=1471028&page=3)

It involves actually using the Broadcom files and "patch" at 
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

It may or may not be an easy alternative, but I would read all documentation before deciding.

---


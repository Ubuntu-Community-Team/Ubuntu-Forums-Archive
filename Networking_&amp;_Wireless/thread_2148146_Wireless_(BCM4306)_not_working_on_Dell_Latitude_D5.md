---
title: "Wireless (BCM4306) not working on Dell Latitude D505"
date: 2013-05-23
forum: Networking &amp; Wireless
---

### Post by Hoscotx on 2013-05-23
I'm hoping you can help me out ... my results for the input commands are below:

```
01:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
    Subsystem: Dell TrueMobile 1300 WLAN Mini-PCI Card [1028:0001]
    Kernel driver in use: wl
--
01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 81)
    Subsystem: Dell Latitude D500 [1028:2002]
    Kernel driver in use: e100

scott@scott-Latitude-D505:~$ uname -mr
3.2.0-43-generic i686
scott@scott-Latitude-D505:~$ lsb_release -d
Description:    Ubuntu 12.04.2 LTS
scott@scott-Latitude-D505:~$
```

---

### Post by varunendra on 2013-05-24
> **Hoscotx said:**
> I have the exact same computer and problem so I'm hoping you can help both of us... my results for the input commands are below:

01:03.0 Network controller [0280]: Broadcom Corporation **BCM4306** 802.11b/g Wireless LAN Controller **[14e4:4320] ([COLOR="#0000CD"]rev 02[/COLOR])**
    Subsystem: Dell TrueMobile 1300 WLAN Mini-PCI Card [1028:0001]
    Kernel driver in use: **wl**
While you are connected via cable, please do -
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
sudo apt-get install b43-fwcutter firmware-b43legacy-installer
```

If you do not have a wired connection available, just run the first command, download the "linux-firmware-nonfree" package from here : [http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download) , copy the downloaded package to your Ubuntu machine, and double-click to install. Reboot if required.

---

### Post by Bucky Ball on 2013-05-24
@ Hoscotx: I have moved your post to a thread of its own. The other thread is dead and OP is inactive so you have a better chance here. You may want to add more info and elaborate on your problem in your first post. 

Incidentally, you are using a different driver to the OP on the other thread so problem wasn't really the same. Good luck with it. ;)

---


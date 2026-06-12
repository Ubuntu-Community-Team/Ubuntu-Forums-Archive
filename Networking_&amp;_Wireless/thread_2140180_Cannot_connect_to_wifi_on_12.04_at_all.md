---
title: "Cannot connect to wifi on 12.04 at all"
date: 2013-04-28
forum: Networking &amp; Wireless
---

### Post by ObeseRocket on 2013-04-28
Hey there,

Just installed 12.04 on my laptop and I keep getting the "Wireless Network-Disconnected" message pop up, and have, in vain, been unable to find some sort of solution to get my laptop to connect to wifi.

Help?

and please bear with me, i am an ubuntu nub. SERIOUS nub

thanks

---

### Post by varunendra on 2013-04-29
Welcome to the forums ObeseRocket! :)

Please open a terminal (Ctrl + Alt + T), enter the following command (you may copy-paste to avoid typo) and post back its output here -
```
lspci -nnk | grep -iA2 net
```

If it is a USB adapter, then -
```
lsusb
```

**PS:**
We all were noobs once, and still are in many respects ;)

---

### Post by ObeseRocket on 2013-04-29
Alright, got this


02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:145c]
    Kernel driver in use: wl
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1444]
    Kernel driver in use: r8169

---

### Post by varunendra on 2013-04-30
> **ObeseRocket said:**
> 02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [**[COLOR="#FF0000"]14e4:4727[/COLOR]**] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:145c]
    Kernel driver in use: wl

Oh my! Please check :
```
dmesg | grep wl
```
If it shows error messages like -
> ERROR @wl_cfg80211_get_station : Could not get....
.. then please check out this thread : [http://ubuntuforums.org/showthread.php?t=2140263](http://ubuntuforums.org/showthread.php?t=2140263)

A possible solution is in post #6 (not confirmed yet, awaiting feedback from the OP)

However, if your dmesg output is free of such error messages, please follow the "Wireless Script" link in my signature and post back what the linked post asks to.

---

### Post by ObeseRocket on 2013-04-30
Omigosh, post #6 worked, I am now connected to wifi for the first time in my experience with ubuntu.

Thank you VERY VERY much

now, how do i change to [SOLVED]?

---

### Post by Iowan on 2013-04-30
> **ObeseRocket said:**
> Omigosh,
now, how do i change to [SOLVED]?[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
Or, use the link in ** varunendra's ** signature...

---

### Post by varunendra on 2013-04-30
> **ObeseRocket said:**
> Omigosh, post #6 worked, I am now connected to wifi for the first time in my experience with ubuntu.

..and is such a nice and welcome feedback! :)

Hope it proves to be stable and let's also hope it gets fixed soon in the newer kernel modules so that users don't have to go for workarounds.

---

### Post by varunendra on 2013-04-30
> **ObeseRocket said:**
> Omigosh, post #6 worked, I am now connected to wifi for the first time in my experience with ubuntu.

..and is such a nice and welcome feedback! :)

Hope it proves to be stable and let's also hope it gets fixed soon in the newer versions of the driver so that users don't have to go for workarounds.

---


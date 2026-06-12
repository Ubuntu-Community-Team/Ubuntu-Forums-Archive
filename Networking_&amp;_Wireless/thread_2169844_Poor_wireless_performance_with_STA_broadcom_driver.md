---
title: "Poor wireless performance with STA broadcom drivers."
date: 2013-08-23
forum: Networking &amp; Wireless
---

### Post by jerry10 on 2013-08-23
I have noticed very poor performance in ubuntu 12.04 when I use the STA drivers for my hp-pavilion g series laptop with broadcom 4313 wireless when compared to the same with windows 7. Also when I am connected with the laptop it will not allow any of my android devices to connect and if they do they are very slow.

---

### Post by chili555 on 2013-08-23
There is a bit of controversy as to whether the Broadcom STA driver is even correct for your device. Please run:```
lspci -nn -d 14e4:
```Is your device 14e4:4727? I'd remove the STA driver and try brcmsmac.

---

### Post by jerry10 on 2013-08-23
It is

07:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
  
I am not familiar with that driver I'll run a search

---

### Post by chili555 on 2013-08-23
Let me save you a few moments:```
sudo apt-get remove --purge bcmwl-kernel-source
```Reboot. Post back and tell us if the wireless works better.

---

### Post by jerry10 on 2013-08-23
Fixed! thanks alot

---

### Post by chili555 on 2013-08-23
Awesome! Please mark the thread Solved. [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


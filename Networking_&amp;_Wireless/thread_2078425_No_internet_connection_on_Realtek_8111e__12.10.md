---
title: "No internet connection on Realtek 8111e / 12.10"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by Blodoffer on 2012-10-31
Just build a new set up with Realtek 8111F Lan controller. I got no connection so I installed r8168 drivers. The autorun.sh did nothing so I used some old modswitch12.04 script. Everything seemed to go as intended but I still got no luck with internet. What should I do next? Or could I just buy a PCI network card that would actually work with Ubuntu?

---

### Post by Blodoffer on 2012-10-31
Also I expect wired internet to work just by connecting PC to network box. If that isn't the case and other steps are required to establish the connection, please let me know.

---

### Post by chili555 on 2012-10-31
First, let's be sure what you have. Please run and post:```
lspci -nn | grep 0200
```> The autorun.sh did nothingNothing? No errors? No text? No warnings? Nothing?? Details may be helpful.

---

### Post by Blodoffer on 2012-10-31
> 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 09)


I was actually able to install drivers by autorun.sh as root. Still the problem persists.

---

### Post by chili555 on 2012-10-31
Let's verify that the correct driver *only* is loading:```
lsmod | grep r816
ifconfig
nm-tool
```Thanks.

---


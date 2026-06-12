---
title: "No enable wireless option in network manager after installation of 12.10"
date: 2013-06-15
forum: Networking &amp; Wireless
---

### Post by patagriff on 2013-06-15
I just installed Ubuntu 12.10 AMD 64 on my laptop. The proprietary driver for my Broadcom adapter is installed. The light by the adapter switch is on. However, when I click on the network icon at the top of the screen. there is no enable/disable wireless option available and no wireless networks appear. 

How do I enable wireless? At this point I can only access the internet via ethernet connection.

---

### Post by chili555 on 2013-06-15
Please open a terminal and run and post:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

---


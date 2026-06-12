---
title: "Ndiswrapper does not load on startup"
date: 2013-01-28
forum: Networking &amp; Wireless
---

### Post by pspencil on 2013-01-28
I have a rtl8192se driver which does not seem to work well. so i installed ndiswrapper 1.58 and installed the driver for xp. 

after that i run (sudo +.....)

modprobe ndiswrapper 
ndiswrapper -m
ndiswrapper -mi
ndiswrapper -ma 

it works but when i restart, the system cannot detect the wireless card(iwconfig) but it is still present in lspci

---

### Post by pspencil on 2013-01-28
anyone??

---

### Post by rrich1974 on 2013-01-28
hi there...
few days ago i just installed wireless driver and i fallowed this topic. 
[http://ubuntuforums.org/showthread.php?t=1481710](http://ubuntuforums.org/showthread.php?t=1481710)
now, you should adapt to your wireless card.

---


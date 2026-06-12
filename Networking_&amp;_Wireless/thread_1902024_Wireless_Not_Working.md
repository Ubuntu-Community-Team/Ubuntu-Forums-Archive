---
title: "Wireless Not Working"
date: 2011-12-29
forum: Networking &amp; Wireless
---

### Post by tacOS&gt;MacOS on 2011-12-29
I just downloaded Ubuntu 11.10 x86 alongside Microsoft Windows XP using Wubi.  When i try to connect to my WiFi (802.11n) home network, i get a message that it is missing some firmware.  I'm brand new to Ubuntu so i don't really know what to do.

---

### Post by wildmanne39 on 2011-12-29
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---


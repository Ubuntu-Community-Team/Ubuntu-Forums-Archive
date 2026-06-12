---
title: "WIFI connection problems"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by soulresonence on 2012-06-13
Hi,
Since re-installing ubuntu 10.04 i've been having some WiFi problems. 
Laptop connects on statup but after a few minutes disconnects from the router and is unable to re-establish a connection. Had no problems prior to doing the re-install and all other computers in the house connect no problem (all running windows)
Would appreciate any help.

---

### Post by wildmanne39 on 2012-06-23
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---


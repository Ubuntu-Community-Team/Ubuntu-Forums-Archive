---
title: "Inspiron 910: Wireless card (Anatel / Broadcom 94312MCG) does not work"
date: 2013-04-15
forum: Networking &amp; Wireless
---

### Post by Ek1 on 2013-04-15
The WLAN is not recognized. I found this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/976246](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/976246) but I don't know what to do next.
The card says Broadcom94312MCG but I can't find anything about those. If you loose the 9 from the start of the numbers, then there is lots of hits, but that cant be right?

---

### Post by mörgæs on 2013-04-15
Moved, as this is not specific to Dell.

---

### Post by Hadaka on 2013-04-15
Hi, please open a terminal   ctrl/alt/t
then COPY and paste the following..
```
lspci -nn | egrep '0200|0280'
lsmod
rfkill list all
```
post the results
thanks.

---


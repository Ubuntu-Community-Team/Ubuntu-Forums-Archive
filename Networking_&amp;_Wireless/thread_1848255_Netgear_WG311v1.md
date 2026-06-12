---
title: "Netgear WG311v1"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by Steam. on 2011-09-22
Ubuntu doesn't detect it at all.lspci just gives it as "Ethernet Controller".

It uses a AR5001/X chip so if someone can find me some drivers or something to aid here(remember it's v1, the very first WG311) would be very grateful.Thanks.

---

### Post by chili555 on 2011-09-22
A number of Atheros wireless chipsets mis-identify themselves as ethernet controllers. It's a misnomer that confuses many a new Ubuntu user. Please open a terminal and run and post:```
lspci -nn | grep 0280
lsmod | grep ath
dmesg | grep ath
```Thanks.

---


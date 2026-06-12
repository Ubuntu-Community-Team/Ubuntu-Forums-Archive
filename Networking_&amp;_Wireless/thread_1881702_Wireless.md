---
title: "Wireless"
date: 2011-11-16
forum: Networking &amp; Wireless
---

### Post by Gwaro on 2011-11-16
I am unable to activate wireless drivers for Ubuntu 10.04 LTS. I keep getting this (see attachment) each time i try to activate them

---

### Post by praseodym on 2011-11-16
Hi,

which device do you use? Please show:

```
lspci -nnk | grep -iA2 net
iwconfig
lsmod
sudo iwlist scan
```
Do you have a wired connection for that installation?

---


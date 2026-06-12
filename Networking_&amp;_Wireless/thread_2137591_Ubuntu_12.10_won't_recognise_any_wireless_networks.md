---
title: "Ubuntu 12.10 won't recognise any wireless networks"
date: 2013-04-21
forum: Networking &amp; Wireless
---

### Post by mattypks1870 on 2013-04-21
Ok so I've only just installed Ubuntu and I'm already having problems, when I go into Network Manager and then to the wireless tab, nothing shows up. All I know is that I have a bcm4321 driver. I think...

---

### Post by praseodym on 2013-04-21
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```
Can you connect via cable?

---


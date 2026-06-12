---
title: "Internet not working at all"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by jameswm on 2011-09-19
I just installed Ubuntu 11.04 through Wubi on my Lenovo B575. It has a  raLink rt3090 wireless card. I put the ethernet cable in, no internet access. As far as wifi, switch is on. It wont even give me the option to find connections. I downloaded the driver from [https://launchpad.net/~markus-tisoft...0~ppa1_all.deb](https://launchpad.net/~markus-tisoft...0~ppa1_all.deb)
and when I try to double click it, the only option is open in software center, but I have no internet. I tried sudo dpkg -i package.deb and it said something along the lines of it not existing. What do I do???

---

### Post by Grenage on 2011-09-19
When you plugged in the wired connection, you said you had no internet; did you get an IP address from the router?  If we can get the wired connection working (which is usually out of the box) then it should be a case of selecting the drivers for the wireless, under Additional Drivers.

---

### Post by praseodym on 2011-09-19
Hi,

please show the outputs of

```
lspci -nnk | grep -iA2 net
lsmod
```

---


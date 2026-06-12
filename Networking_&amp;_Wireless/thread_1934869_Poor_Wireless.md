---
title: "Poor Wireless"
date: 2012-03-03
forum: Networking &amp; Wireless
---

### Post by mkabwilliams on 2012-03-03
I'm very new to ubuntu I had a Latitud XT2 that I decided to load it on and its having some wireless problems I get very slow loads on pages and then sometimes they won't load at all. I can plug in to my network and it works great. Could someone help me fix the wireless problems. Thanks

---

### Post by praseodym on 2012-03-03
Hi,

please show the terminal (CTRL+ALT+T) outputs of the commands

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
cat /etc/resolv.conf
route -n
```

---


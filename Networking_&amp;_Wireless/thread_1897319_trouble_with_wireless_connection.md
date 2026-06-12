---
title: "trouble with wireless connection"
date: 2011-12-19
forum: Networking &amp; Wireless
---

### Post by munez on 2011-12-19
I got Ubuntu 11.10 installed in my laptop recently. My laptop also has dual boot with windows 7. The wireless and wired connection both work smoothly in windows 7, but there seems to be a problem when operating with Ubuntu, as it is the wired connection works smoothly and the wireless connection is established but still shows offline....................................................plz help in this matter.

---

### Post by praseodym on 2011-12-19
Hi,

please show the terminal (CTRL+ALT+T) outputs of:

```
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
iwconfig
rfkill list
sudo iwlist scan
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```

---


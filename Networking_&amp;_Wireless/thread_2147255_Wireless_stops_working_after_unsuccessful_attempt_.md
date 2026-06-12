---
title: "Wireless stops working after unsuccessful attempt at Ndiswrapper!"
date: 2013-05-21
forum: Networking &amp; Wireless
---

### Post by SukuC23101993 on 2013-05-21
I didn't solve this but I'm going ahead to install Mint 15!

---

### Post by praseodym on 2013-05-21
Hi,

please show the outputs of these terminal (CTRL+ALT+T) commands:
```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by mörgæs on 2013-05-21
OK, but if you want help to solve it you should begin with stating which card you are using.

---


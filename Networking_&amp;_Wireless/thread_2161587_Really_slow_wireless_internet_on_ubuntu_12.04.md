---
title: "Really slow wireless internet on ubuntu 12.04"
date: 2013-07-11
forum: Networking &amp; Wireless
---

### Post by Boris98gizmo on 2013-07-11
Today i installed Ubuntu 12.04 using wobi. However when i use the wifi my internet gets really slow and it doesnt load the page.
My wifi was great when i used windows.
Helppp

---

### Post by praseodym on 2013-07-11
Please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
sudo iwlist scan
cat /etc/resolv.conf
```

---


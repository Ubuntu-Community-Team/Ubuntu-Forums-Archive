---
title: "Wireless unavailable on Acer S3"
date: 2013-05-27
forum: Networking &amp; Wireless
---

### Post by Tohiko on 2013-05-27
I have an Acer S3 with ubuntu 12.10.
Every time I connect to wireless the connection is lost after a few hours and the wireless menu (from the notification area in the upper right) shows "Hardware unavailable" next to wireless.
It's bad enough that this happens and I have no idea why, but also my only resolution is to restart ubuntu which is a pain.
Any idea how to resolve this? Or how to make the wireless available without having to reboot

Thanks

---

### Post by praseodym on 2013-05-27
Please show the terminal outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---


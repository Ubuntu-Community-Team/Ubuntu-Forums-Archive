---
title: "wireless D-Link DWL-G122/b1"
date: 2013-07-15
forum: Networking &amp; Wireless
---

### Post by anker020 on 2013-07-15
Hi all, When i trying to turn on wireless works, past 1 minute or less  doesn't work, but internet connection is still on, dunno why this  happened, any help?

Best Regards, anker020. :smile:

---

### Post by praseodym on 2013-07-15
Please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
cat /etc/resolv.conf
sudo iwlist scan
```

---


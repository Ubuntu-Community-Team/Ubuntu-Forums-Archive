---
title: "RT3090 wireless driver not working Ubuntu 11.04"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by axi.torvalds on 2011-10-19
Hello,I am new to Ubuntu and I would like someone to help me to make my RT3090 wirless driver work properly it used to work perfectly in open SUSE and after I switched to Ubuntu it doesn't. Any Ideas?

:confused:

I have a HP G62 B51EE

---

### Post by praseodym on 2011-10-19
Hello,

please show the terminal outputs of:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
sudo iwlist scan
rfkill list
dmesg | egrep 'rt2|rt3'
```

---


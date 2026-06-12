---
title: "wireless not working"
date: 2013-06-18
forum: Networking &amp; Wireless
---

### Post by JustAsad on 2013-06-18
i have just installed Ubuntu 12.04 on my Dell Inspiron n5520 but wirless is not workng.Need help

---

### Post by praseodym on 2013-06-18
Hi,

we need some more information ;)

Please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
route -n
```

---


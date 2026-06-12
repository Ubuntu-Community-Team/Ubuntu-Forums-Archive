---
title: "dual boot w/Window XP Ubuntu not go online"
date: 2013-04-06
forum: Networking &amp; Wireless
---

### Post by ellymayh on 2013-04-06
:mad:Ubuntu 12.04 disconnected me from the internet during installation and will not go online from Ubuntu partition. works fine with up-to-date Windows XP and the wifi connection is strong. frustrated

---

### Post by praseodym on 2013-04-07
Hi,

please show the terminal (CTRL+ALT+T) outputs of these commands:
```

uname -r
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---


---
title: "Can't get linksys wireless wmp300n to work with ubuntu 10.04"
date: 2011-11-19
forum: Networking &amp; Wireless
---

### Post by leeryan on 2011-11-19
Hello,

I have a linksys wireless wmp300n card.  I can't get it to work with my ubuntu 10.04.  I have download ndiswrapper 1.56.  I am not sure if I have yet extracted all the neccessary files.  I have the cd that came with the card which i got the windows driver from.  I have downloaded the windows wireless driver program and have gotten as far as getting the windows drivers to show up on that screen.  I am very new to linux and I don't really understand how to use the terminal other than copy and pasting commands that I find on this forum.  Any help would be greatly appreciated.

Best

---

### Post by praseodym on 2011-11-20
Hi,

please show the terminal outputs of:
```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
route -n
```

---


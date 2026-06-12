---
title: "Wireless Problems, Network Manager missing Wireless options"
date: 2012-04-01
forum: Networking &amp; Wireless
---

### Post by Nakor1991 on 2012-04-01
Hi I'm experiencing some problems getting my wireless working.

To begin with every time I tried connect to wireless network it killed the router, so I ended up just plugging in an ethernet cable so I could get some work done.

Decided to have another go at connecting to the wireless however the option for wireless is now missing from Network Manager.

[[IMG]http://www.freeimagehosting.net/t/w866a.jpg[/IMG]]("http://www.freeimagehosting.net/w866a")

---

### Post by Ms. Daisy on 2012-04-03
What's the output of
```
lspci -nnk | grep -iA2 net 
lsusb
```

---

### Post by alex.nucleo on 2012-04-04
See my comments here [http://ubuntuforums.org/showthread.php?t=1951032](http://ubuntuforums.org/showthread.php?t=1951032)
Maybe it helps.

---


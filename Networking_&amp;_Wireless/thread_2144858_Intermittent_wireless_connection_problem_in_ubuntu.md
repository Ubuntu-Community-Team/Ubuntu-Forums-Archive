---
title: "Intermittent wireless connection problem in ubuntu 12.10"
date: 2013-05-13
forum: Networking &amp; Wireless
---

### Post by danba185 on 2013-05-13
Hi, I'm running dual-boot on my laptop with ubuntu 12.10 and windows 8. Sometimes I can't connect to my wireless network in ubuntu (always works in windows), after a couple of reboots or disconnecting/connecting to the wireless network makes it work again but it feels very random. Sometimes there isn't any problem at all and the connection to the wireless network works nice for a couple of times. Any suggestions how I can get rid of this intermittent and annoying problem? 

/Dan

---

### Post by praseodym on 2013-05-13
Hi,

please show
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
```
What laptop is it?

---


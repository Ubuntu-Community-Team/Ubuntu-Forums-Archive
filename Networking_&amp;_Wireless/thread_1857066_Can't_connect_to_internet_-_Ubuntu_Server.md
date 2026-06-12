---
title: "Can't connect to internet - Ubuntu Server"
date: 2011-10-09
forum: Networking &amp; Wireless
---

### Post by jaxnif on 2011-10-09
Hi, i am kind of a beginner at this whole thing, not totally incapable though, but this is my first time using a ubuntu server and i can not figure out how to connect to my wifi..... When i was first setting up the server, i put in the essid of my wifi and the password but it said that there was something wrong with the dhcp and stuff...

-Thank you
Jaxnif

---

### Post by praseodym on 2011-10-09
Hi,

can you show the outputs of:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---


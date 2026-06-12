---
title: "getting wireless to work on ubuntu"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by joslezio on 2011-09-20
Hi, I'm currently installing Ubuntu 11.04. This will be the first time I've ever had Ubuntu and need a little help. One. How do I get my wireless network adapter to work. It's a Linksys Wireless-N USB Network Adapter 2.4 ghz and the model number is wusb300n
Two. I've read about a way to get my Zune software to work with Ubuntu as well, but can't seem to locate that source again. Any help is much appreciated. Thanks.

---

### Post by praseodym on 2011-09-20
Hi,

please show the terminal outputs of

```
lsusb
lsmod
iwconfig
rfkill list
```
Which version of zune is that? Try it with wine, maybe with playonlinux, too, which can handle several wine versions in parallel. Which wine version works for your software can be searched here:

[http://www.winehq.org/](http://www.winehq.org/)

---


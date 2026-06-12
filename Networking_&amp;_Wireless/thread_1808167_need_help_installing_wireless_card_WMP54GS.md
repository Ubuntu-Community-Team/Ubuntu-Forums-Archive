---
title: "need help installing wireless card WMP54GS"
date: 2011-07-20
forum: Networking &amp; Wireless
---

### Post by mr521 on 2011-07-20
The post I saw regarding this card was back in 2007 and is not helping me at all. I am completely new to Ubuntu and I followed the steps to finding WINE but can't locate it at all. Apparently I need this installed before trying to install the driver (which I already downloaded from lynsys' site). I will greatly appreciate the help. Thanks in advance.

---

### Post by linuxman94 on 2011-07-20
Wine will not work for installing system drivers.  So don't bother with it for now.  In order to help you better, can you post the results of these commands?  Enter them into the terminal (search for it in unity if you're using 11.04)

```
sudo lshw -C network
lspci
iwconfig
```

Post the output between code tags (# sign in the editor)

---

### Post by Perfect Storm on 2011-07-20
Moved to Networking & Wireless forum.

---


---
title: "Broadcom Wireless switching between monitor and normal mode, crashes the system"
date: 2013-03-26
forum: Networking &amp; Wireless
---

### Post by vinit.tiwari2012 on 2013-03-26
Hi,

I have Ubuntu 12.04 installed on my Dell Inspiron machine along with windows8. I have Broadcom wireless [14e4:4365] on my machine. I found there are two drivers available for Broadcom 43xx card 
1. b43 - open source
2. STA/wl - Provided by Broadcom.

I tried b43 but It didn't work for my card so I switched to STA/wl which is working perfectly, although it is not listed in the supported drivers list in the [Readme]("http://www.broadcom.com/docs/linux_sta/README.txt") file because list ends at 4359. 

I want to put my card in monitoring mode to capture wireless packets, so somewhere on internet I found I need to change the op-code in file ```
/proc/brcm_monitor0 using # echo 1 | tee /proc/brcm_monitor0
```

Also as per the comments mentioned over there [Optional Monitor Mode]("http://en.gentoo-wiki.com/wiki/Broadcom_43xx") **it will create a new interface named prism0 which will be listed in iwconfig, which I don't get although I am able to run airodump-ng on this interface and it captures the packets.**

Everything works fine except when I tries to turn off the monitor mode using ```
# echo 0 | tee /proc/brcm_monitor0
``` it crashes my system with a stacktrace being displayed. and if I try to shutdown without switching to normal mode it don't shuts down at all and only the shutting down screen is displayed.

Please help

---

### Post by vinit.tiwari2012 on 2013-04-02
Please help guys...

---


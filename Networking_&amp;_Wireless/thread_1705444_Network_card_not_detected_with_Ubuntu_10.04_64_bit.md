---
title: "Network card not detected with Ubuntu 10.04 64 bit on Dell vostro 200"
date: 2011-03-12
forum: Networking &amp; Wireless
---

### Post by gargjiv on 2011-03-12
I recently changed the Operating system from Windows XP to Ubuntu 10.04 64 bit on my Dell Vostro 200.  However the LAN network card was not detected. I searched online for relevant drivers and compiled and installed e1000 driver. However I still have no internet. Does anyone know what driver might work with ubuntu 10.04 on Dell vostro 200.

---

### Post by sully101 on 2011-09-22
I am having trouble with mine but I have the e1000e module loaded, it was detected automatically but it seems a bit flaky.

```
$ lspci | grep Ethernet
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
```

```
$ lsmod | grep 1000
e1000e                136301  0
```

I am dual boot here and it never fails in the other os, so I can only assume it is a problem with the module. Some times after a boot it wont connect. doing a ```
rmmod e100e
``` then ```
modprobe e1000e
``` a couple of times seems to get it going then its fine till the next reboot.

You will note that mine is a 10/100 connection, which is what it is in the other os.

---


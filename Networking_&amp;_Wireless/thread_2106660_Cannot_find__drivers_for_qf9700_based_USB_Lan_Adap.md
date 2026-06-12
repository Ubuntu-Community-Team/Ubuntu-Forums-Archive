---
title: "Cannot find  drivers for qf9700 based USB Lan Adapter that work in Ubuntu 12.04"
date: 2013-01-19
forum: Networking &amp; Wireless
---

### Post by pawanh on 2013-01-19
I purchased a cheap USB Lan Adapter (DOMO nHance U1) on ebay, kinda assuming that there will be drivers somewhere (epic noobity!). The company sent me a link to a driver that works on 2.6 something kernels.
I've tried compiling, but I get errors. It is based on QF9700 chipset as mentioned in the title.
I'd be so so thankful if someone could give me the drivers, or show me how to compile the cryptic source file for my kernel (3.2+)

```
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-35-generic'
  CC [M]  /home/pawan/Data/Linux/qf9700.o
/home/pawan/Data/Linux/qf9700.c: In function ‘qf_read’:
/home/pawan/Data/Linux/qf9700.c:36:2: error: implicit declaration of function ‘devdbg’ [-Werror=implicit-function-declaration]
/home/pawan/Data/Linux/qf9700.c: In function ‘qf_write_async_helper’:
/home/pawan/Data/Linux/qf9700.c:115:3: error: implicit declaration of function ‘deverr’ [-Werror=implicit-function-declaration]
/home/pawan/Data/Linux/qf9700.c: In function ‘qf9700_set_multicast’:
/home/pawan/Data/Linux/qf9700.c:356:45: error: ‘struct net_device’ has no member named ‘mc_count’
/home/pawan/Data/Linux/qf9700.c:358:16: error: ‘struct net_device’ has no member named ‘mc_count’
/home/pawan/Data/Linux/qf9700.c:359:36: error: ‘struct net_device’ has no member named ‘mc_list’
/home/pawan/Data/Linux/qf9700.c:362:22: error: ‘struct net_device’ has no member named ‘mc_count’
/home/pawan/Data/Linux/qf9700.c:362:56: error: dereferencing pointer to incomplete type
/home/pawan/Data/Linux/qf9700.c:363:14: error: dereferencing pointer to incomplete type
/home/pawan/Data/Linux/qf9700.c: In function ‘qf9700_bind’:
/home/pawan/Data/Linux/qf9700.c:380:10: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/pawan/Data/Linux/qf9700.c:381:10: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/pawan/Data/Linux/qf9700.c: In function ‘qf9700_rx_fixup’:
/home/pawan/Data/Linux/qf9700.c:443:25: error: ‘struct usbnet’ has no member named ‘stats’
/home/pawan/Data/Linux/qf9700.c:444:25: error: ‘struct usbnet’ has no member named ‘stats’
/home/pawan/Data/Linux/qf9700.c:445:25: error: ‘struct usbnet’ has no member named ‘stats’
/home/pawan/Data/Linux/qf9700.c:446:25: error: ‘struct usbnet’ has no member named ‘stats’
/home/pawan/Data/Linux/qf9700.c:447:25: error: ‘struct usbnet’ has no member named ‘stats’
cc1: some warnings being treated as errors
make[2]: *** [/home/pawan/Data/Linux/qf9700.o] Error 1
make[1]: *** [_module_/home/pawan/Data/Linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-35-generic'
make: *** [all] Error 2

```

---

### Post by dgharmon on 2013-01-19
> **pawanh said:**
> I've tried compiling, but I get errors

Dunno .. this might help ...

[qf9700.ko]("http://eyesonly666.wordpress.com/2012/10/15/compiling-linux-drivers-for-rd9700-qf9700-ko-under-debian-squeeze/")

---


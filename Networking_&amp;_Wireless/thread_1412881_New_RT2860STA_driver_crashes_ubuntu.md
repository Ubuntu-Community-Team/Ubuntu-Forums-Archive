---
title: "New RT2860STA driver crashes ubuntu"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by Addicted247 on 2010-02-21
I've had problems with the included driver for my new wireless card, which lspci reports as:```
05:06.0 Network controller: RaLink RT2800 802.11n PCI
    Kernel driver in use: rt2860
    Kernel modules: rt2860sta

```The connection drops out with an error message that I've since googled. It seemed that people were able to solve the problem by compiling the newest driver. So I downloaded the driver source from the ralink website and compiled it. I used these steps:

1. Modified config.mk to be compatible with NetworkManager. (I didn't know how to "define" the GCC and LD or CFLAGS)
2. Make
3. Per the readme instructions, I unloaded the existing module and loaded the new one by typing```
/sbin/insmod rt2860sta.ko
```This works, BUT the connection still drops under heavy traffic. When I try to rescan for wireless networks, ubuntu freezes.

If I instead "make install" the new driver, ubuntu freezes during boot. The logs don't even show any error, they just stop mid-line.

Could this be due to me not changing the GCC, LD or CFLAGS? I've read quite a bit about installing new ralink drivers, but there was never any mention of how to deal with that part.

I've been stuck on this for a while and would greatly appreciate any help.

---

### Post by Addicted247 on 2010-02-22
Turns out it was all due to having wicd installed as a replacement for the Gnome NetworkManager. I uninstalled wicd and reinstalled NetworkManager. Everything works fine now :)

---


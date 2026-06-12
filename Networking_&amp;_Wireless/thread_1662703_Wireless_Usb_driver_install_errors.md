---
title: "Wireless Usb driver install errors"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by erusnex on 2011-01-08
Hello,

I am trying to install usb wireless network card drivers on to lucid. I didnt think i was soo much a noob but it has come apparent to me now.
Anyway when i use 'sudo make' i get errors that i do not understand. Can anybody make it clear for me and sort out this problem.

I have been following this guide. [http://ubunturt2870.pbworks.com/w/page/8928776/FrontPage]("http://ubunturt2870.pbworks.com/w/page/8928776/FrontPage")

```
/home/luke/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1624: error: ‘struct net_device’ has no member named ‘open’
/home/luke/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1625: error: ‘struct net_device’ has no member named ‘stop’
/home/luke/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1626: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/luke/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1627: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/luke/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1633: error: ‘struct net_device’ has no member named ‘get_stats’
/home/luke/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1667: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/home/luke/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/luke/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-27-generic-pae'
make: *** [LINUX] Error 2

```

---

### Post by chili555 on 2011-01-08
First, the newest version is 2.4.0.0; I have no doubt that an older version is troublesome. Did you install build-essential and linux-headers-generic?

Second, rt2870sta is built in to the kernel. Is there any reason it won't work for you? What is your usb.id?```
lsusb
```

---

### Post by erusnex on 2011-01-08
The older version is trouble but so is my lack of understanding.


> **chili555 said:**
> Did you install build-essential and linux-headers-generic?
What is this? Are they programs (programs no doubt being the incorrect word)or are they process i should be doing before sudo make

```
Bus 002 Device 005: ID 148f:3070 Ralink Technology, Corp.
```
thats the one you wanted i believe?

I will just try it with the new version a sec.

Thank you

---

### Post by erusnex on 2011-01-08
Well the newer version doesnt cause this problem so it is sorted.
Now onto the next stage.
I will make a new thread for it once i work out what the problem is.

Thank you i have been struggling with it for hours.
Cheers

---

### Post by chili555 on 2011-01-08
> I will make a new thread for it once i work out what the problem is.You may post it here; I will be glad to help.

---


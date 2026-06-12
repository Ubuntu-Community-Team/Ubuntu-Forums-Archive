---
title: "RT2870 compiler errors - Help please!"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by zilog32 on 2009-11-28
Hi,
I've downloaded **2009_0820_RT2870_Linux_STA_V2.2.0.0.tar.bz2** for my Edimax USB Dongle. After extracting I have the folders and sources etc in;

**/home/zilog/edimax/2009_0820_RT2870_Linux_STA_V2.2.0.0**

Following the instructions in README_STA I've ensured that **MODE = STA** and **TARGET = LINUX** in the **Makefile**

In the **os/linux/comfig.mk** I have set **HAS_WPA_SUPPLICANT=y** and **HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y** as per instructions in README_STA.

However, when I execute **'sudo make**' I eventually get the following errors when it gets to **rt_linux.c/o**;

make[1]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  CC [M]  /home/zilog/edimax/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.o
/home/zilog/edimax/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSIRQRequest’:
/home/zilog/edimax/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1068: warning: unused variable ‘net_dev’
/home/zilog/edimax/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSTaskAttach’:
/home/zilog/edimax/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1282: warning: unused variable ‘pid_number’
/home/zilog/edimax/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/zilog/edimax/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1624: error: ‘struct net_device’ has no member named ‘open’
/home/zilog/edimax/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1625: error: ‘struct net_device’ has no member named ‘stop’
/home/zilog/edimax/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1626: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/zilog/edimax/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1627: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/zilog/edimax/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1633: error: ‘struct net_device’ has no member named ‘get_stats’
/home/zilog/edimax/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.c:1667: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/home/zilog/edimax/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/zilog/edimax/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make: *** [LINUX] Error 2


I have trawled through the C code in 'rt_linux.c' and associated headers etc , ( I am well versed in C/C++ - embedded though! ), and can't seem to see the wood for the trees! Have I not set a directive in the make files or something?

If I can get the damn thing to compile I will be a very happy camper and will deal with installation later.

Any help would be much appreciated.

Thank you in advance.

PS Is it possible that there is something wrong with the Linux versions?

---

### Post by zilog32 on 2009-11-28
**SOLVED**;)

After much digging around I found others with the same compiling problems. There is a very simple solution, ( as there always is! ), by member **jh55chn** at thread;

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8315642](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8315642)

Scroll down to his post.

So 10 million brownie points to him.:popcorn:

Thanks [B]jh55chn.:KS

[/B]PS Hope this helps others.

Zilog32.

---


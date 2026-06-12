---
title: "ieee80211 problems.. 10.04"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by defaultPlayer on 2010-05-08
Hello,
I recently decided to install the latest linux on my really old aptop, great so far, except for the fact i can't solve this issue, i'm trying to install ieee80211 so i can install my wireless card,  Intel® PRO/Wireless 2100.

I basically get this.
laptop@laptop-laptop:~/Desktop/ieee80211-1.2.18$ sudo make SHELL=/bin/bash

Checking in /lib/modules/2.6.34-020634rc6-generic for ieee80211 components...
egrep: /lib/modules/2.6.34-020634rc6-generic/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/2.6.34-020634rc6-generic/build M=/home/laptop/Desktop/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.34-020634rc6-generic'
  CC [M]  /home/laptop/Desktop/ieee80211-1.2.18/ieee80211_module.o
/home/laptop/Desktop/ieee80211-1.2.18/ieee80211_module.c: In function ‘alloc_ieee80211’:
/home/laptop/Desktop/ieee80211-1.2.18/ieee80211_module.c:148: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/laptop/Desktop/ieee80211-1.2.18/ieee80211_module.c:149: error: ‘struct net_device’ has no member named ‘change_mtu’
/home/laptop/Desktop/ieee80211-1.2.18/ieee80211_module.c:153: error: ‘struct net_device’ has no member named ‘get_stats’
/home/laptop/Desktop/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/home/laptop/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/home/laptop/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/laptop/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/laptop/Desktop/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/laptop/Desktop/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/home/laptop/Desktop/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/laptop/Desktop/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.34-020634rc6-generic'
make: *** [modules] Error 2

And i do have the latest headers and kernel.

laptop@laptop-laptop:~/Desktop/ieee80211-1.2.18$ sudo apt-get install linux-headers-2.6.34-020634rc6-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.34-020634rc6-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I'm hoping someone can help me since i've only done a little bit of c programming so i know a few basic commands and ubuntu. Thanks.

---


---
title: "how install wi-fi drivers"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by venio on 2010-07-01
hy gyes i have some trouble, I have Wi-fi card Level one with 8185 chip, Pci card .i run the Ubuntu 8.04.4 version under Wirtoal Station.and i try install the drivers for injection but i get this error massage 

root@venio-desktop:/home/venio/rtl8180-0.21# tar -xvzf rtl8180-0.21.tar.gz
rtl8180-0.21/
rtl8180-0.21/Makefile
rtl8180-0.21/AUTHORS
rtl8180-0.21/CHANGES
rtl8180-0.21/COPYING
rtl8180-0.21/INSTALL
rtl8180-0.21/LICENSE
rtl8180-0.21/Makefile26
rtl8180-0.21/README
rtl8180-0.21/README.adhoc
rtl8180-0.21/compat24.h
rtl8180-0.21/ieee80211.h
rtl8180-0.21/ieee80211_crypt.c
rtl8180-0.21/ieee80211_crypt.h
rtl8180-0.21/ieee80211_crypt_wep.c
rtl8180-0.21/ieee80211_module.c
rtl8180-0.21/ieee80211_rx.c
rtl8180-0.21/ieee80211_tx.c
rtl8180-0.21/ieee80211_wx.c
rtl8180-0.21/ieee802_11.h
rtl8180-0.21/module_load
rtl8180-0.21/module_load24
rtl8180-0.21/module_unload
rtl8180-0.21/module_unload24
rtl8180-0.21/r8180.h
rtl8180-0.21/r8180_93cx6.c
rtl8180-0.21/r8180_93cx6.h
rtl8180-0.21/r8180_core.c
rtl8180-0.21/r8180_gct.c
rtl8180-0.21/r8180_gct.h
rtl8180-0.21/r8180_hw.h
rtl8180-0.21/r8180_max2820.c
rtl8180-0.21/r8180_max2820.h
rtl8180-0.21/r8180_pm.c
rtl8180-0.21/r8180_pm.h
rtl8180-0.21/r8180_sa2400.c
rtl8180-0.21/r8180_sa2400.h
rtl8180-0.21/r8180_wx.c
rtl8180-0.21/r8180_wx.h
rtl8180-0.21/README.master
root@venio-desktop:/home/venio/rtl8180-0.21# cd rtl8180-0.21
root@venio-desktop:/home/venio/rtl8180-0.21/rtl8180-0.21# patch -Np1 -i ../rtl8180-0.21v2.patch
patching file ieee80211_crypt.c
patching file ieee80211_crypt_wep.c
patching file ieee80211_module.c
patching file ieee80211_rx.c
patching file ieee80211_tx.c
patching file ieee80211_wx.c
patching file Makefile
patching file Makefile26
patching file r8180_core.c
patching file r8180.h
root@venio-desktop:/home/venio/rtl8180-0.21/rtl8180-0.21# make
make -C /lib/modules/2.6.24-26-generic/build SUBDIRS=/home/venio/rtl8180-0.21/rtl8180-0.21 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-26-generic'
  CC [M]  /home/venio/rtl8180-0.21/rtl8180-0.21/ieee80211_rx.o
In file included from /home/venio/rtl8180-0.21/rtl8180-0.21/ieee80211_rx.c:43:
/home/venio/rtl8180-0.21/rtl8180-0.21/ieee80211.h:43:1: warning: "BIT" redefined
In file included from include/linux/kernel.h:15,
                 from include/linux/skbuff.h:17,
                 from include/linux/if_ether.h:113,
                 from include/linux/netdevice.h:29,
                 from include/linux/if_arp.h:26,
                 from /home/venio/rtl8180-0.21/rtl8180-0.21/ieee80211_rx.c:25:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/venio/rtl8180-0.21/rtl8180-0.21/ieee80211_rx.c: In function ‘auth_parse’:
/home/venio/rtl8180-0.21/rtl8180-0.21/ieee80211_rx.c:57: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/venio/rtl8180-0.21/rtl8180-0.21/ieee80211_rx.c: In function ‘auth_rq_parse’:
/home/venio/rtl8180-0.21/rtl8180-0.21/ieee80211_rx.c:70: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/venio/rtl8180-0.21/rtl8180-0.21/ieee80211_rx.c: In function ‘assoc_rq_parse’:
/home/venio/rtl8180-0.21/rtl8180-0.21/ieee80211_rx.c:121: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/venio/rtl8180-0.21/rtl8180-0.21/ieee80211_rx.c: In function ‘assoc_parse’:
/home/venio/rtl8180-0.21/rtl8180-0.21/ieee80211_rx.c:136: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/venio/rtl8180-0.21/rtl8180-0.21/ieee80211_rx.c: In function ‘ieee80211_monitor_rx’:
/home/venio/rtl8180-0.21/rtl8180-0.21/ieee80211_rx.c:296: error: ‘struct sk_buff’ has no member named ‘mac’
/home/venio/rtl8180-0.21/rtl8180-0.21/ieee80211_rx.c: In function ‘ieee80211_r8180_rx’:
/home/venio/rtl8180-0.21/rtl8180-0.21/ieee80211_rx.c:1131: error: ‘struct sk_buff’ has no member named ‘mac’
/home/venio/rtl8180-0.21/rtl8180-0.21/ieee80211_rx.c:1131: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/home/venio/rtl8180-0.21/rtl8180-0.21/ieee80211_rx.o] Error 1
make[1]: *** [_module_/home/venio/rtl8180-0.21/rtl8180-0.21] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-2
 
i download the drivers paches and all staff and when i type make ,the system show me this errors!
Please if somebody knows what's go on why i get this errors and what i can do to fix it and continue whit the installation,please tell me because i read lot of forums and i can't continue yet! Thank'you in advance and sorry for my not so good English!!!

---


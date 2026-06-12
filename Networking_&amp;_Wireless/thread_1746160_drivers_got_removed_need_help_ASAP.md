---
title: "drivers got removed need help ASAP"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by war.ace on 2011-05-01
I tried to install ieee80211-1.2.17 and ipw2200-1.2.1 to get aircrack to work. I followed the steps here [http://ubuntuforums.org/showthread.php?t=501148](http://ubuntuforums.org/showthread.php?t=501148) but I removed both ieee80211 and ipw2200 by accident and I can't compile ieee80211-1.2.17. I get this:
```
christopher@christopher-laptop:~/Downloads/ieee80211-1.2.17$ sudo make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.32-31-generic for ieee80211 components...
make -C /lib/modules/2.6.32-31-generic/build M=/home/christopher/Downloads/ieee80211-1.2.17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-31-generic'
/home/christopher/Downloads/ieee80211-1.2.17/Makefile:17: 
/home/christopher/Downloads/ieee80211-1.2.17/Makefile:18: WARNING: $SHELL not set to bash.
/home/christopher/Downloads/ieee80211-1.2.17/Makefile:19: If you experience build errors, try
/home/christopher/Downloads/ieee80211-1.2.17/Makefile:20: 'make SHELL=/bin/bash'.
/home/christopher/Downloads/ieee80211-1.2.17/Makefile:21: 
  CC [M]  /home/christopher/Downloads/ieee80211-1.2.17/ieee80211_module.o
/home/christopher/Downloads/ieee80211-1.2.17/ieee80211_module.c: In function &#8216;alloc_ieee80211&#8217;:
/home/christopher/Downloads/ieee80211-1.2.17/ieee80211_module.c:148: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/christopher/Downloads/ieee80211-1.2.17/ieee80211_module.c:149: error: &#8216;struct net_device&#8217; has no member named &#8216;change_mtu&#8217;
/home/christopher/Downloads/ieee80211-1.2.17/ieee80211_module.c:153: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/home/christopher/Downloads/ieee80211-1.2.17/ieee80211_module.c: In function &#8216;ieee80211_init&#8217;:
/home/christopher/Downloads/ieee80211-1.2.17/ieee80211_module.c:267: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/christopher/Downloads/ieee80211-1.2.17/ieee80211_module.c:267: error: (Each undeclared identifier is reported only once
/home/christopher/Downloads/ieee80211-1.2.17/ieee80211_module.c:267: error: for each function it appears in.)
/home/christopher/Downloads/ieee80211-1.2.17/ieee80211_module.c: In function &#8216;ieee80211_exit&#8217;:
/home/christopher/Downloads/ieee80211-1.2.17/ieee80211_module.c:296: error: &#8216;proc_net&#8217; undeclared (first use in this function)
make[2]: *** [/home/christopher/Downloads/ieee80211-1.2.17/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/christopher/Downloads/ieee80211-1.2.17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-31-generic'
make: *** [modules] Error 2
christopher@christopher-laptop:~/Downloads/ieee80211-1.2.17$ ^C
christopher@christopher-laptop:~/Downloads/ieee80211-1.2.17$ 

```the control c you see there was by accident I was trying to copy the message after the error

---


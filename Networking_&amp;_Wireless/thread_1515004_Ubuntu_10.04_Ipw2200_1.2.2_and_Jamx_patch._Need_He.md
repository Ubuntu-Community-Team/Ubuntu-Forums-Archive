---
title: "Ubuntu 10.04 Ipw2200 1.2.2 and Jamx patch. Need Help!"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by gooch1025 on 2010-06-21
So I've been looking around and some people say that the IPW2200 driver doesn't need Ieee80211 to work properly. What I'm trying to do is compile my own driver with the Jamx patch for version 1.2.2 but then it says that I do in fact need Ieee80211 to be installed. Even though I don't have it installed, my wireless works great. I just need the patch to work with the driver. I've also tried configuring some of the files in the Ieee80211 folder but it doesn't seem to help at all. When I try to use the make command for Ieee80211 I get this:

> gooch@gooch-laptop:~/Downloads/ieee80211-1.2.18$ make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.32-22-generic for ieee80211 components...
make -C /lib/modules/2.6.32-22-generic/build M=/home/gooch/Downloads/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
/home/gooch/Downloads/ieee80211-1.2.18/Makefile:17: 
/home/gooch/Downloads/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/gooch/Downloads/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/gooch/Downloads/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/gooch/Downloads/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/gooch/Downloads/ieee80211-1.2.18/ieee80211_module.o
/home/gooch/Downloads/ieee80211-1.2.18/ieee80211_module.c: In function ‘alloc_ieee80211’:
/home/gooch/Downloads/ieee80211-1.2.18/ieee80211_module.c:148: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/gooch/Downloads/ieee80211-1.2.18/ieee80211_module.c:149: error: ‘struct net_device’ has no member named ‘change_mtu’
/home/gooch/Downloads/ieee80211-1.2.18/ieee80211_module.c:153: error: ‘struct net_device’ has no member named ‘get_stats’
/home/gooch/Downloads/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/home/gooch/Downloads/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/home/gooch/Downloads/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/gooch/Downloads/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/gooch/Downloads/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/gooch/Downloads/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
{standard input}: Assembler messages:
{standard input}:9: Warning: can't open .lst: Permission denied
GAS LISTING              page 1


   1                  .file "ieee80211_module.c"
   9                  .Ltext0:

GAS LISTING              page 2


DEFINED SYMBOLS
                            *ABS*:0000000000000000 ieee80211_module.c

NO UNDEFINED SYMBOLS
make[2]: *** [/home/gooch/Downloads/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/gooch/Downloads/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [modules] Error 2After configuring the files a little bit, this is what I come up with:

> gooch@gooch-laptop:~/ieee80211-1.2.18$ make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.32-22-generic for ieee80211 components...
make -C /lib/modules/2.6.32-22-generic/build M=/home/gooch/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
/home/gooch/ieee80211-1.2.18/Makefile:17: 
/home/gooch/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/gooch/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/gooch/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/gooch/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/gooch/ieee80211-1.2.18/ieee80211_module.o
/home/gooch/ieee80211-1.2.18/ieee80211_module.c: In function ‘alloc_ieee80211’:
/home/gooch/ieee80211-1.2.18/ieee80211_module.c:148: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/gooch/ieee80211-1.2.18/ieee80211_module.c:149: error: ‘struct net_device’ has no member named ‘change_mtu’
/home/gooch/ieee80211-1.2.18/ieee80211_module.c:153: error: ‘struct net_device’ has no member named ‘get_stats’
{standard input}: Assembler messages:
{standard input}:9: Warning: can't open .lst: Permission denied
GAS LISTING              page 1


   1                  .file "ieee80211_module.c"
   9                  .Ltext0:

GAS LISTING              page 2


DEFINED SYMBOLS
                            *ABS*:0000000000000000 ieee80211_module.c

NO UNDEFINED SYMBOLS
/home/gooch/ieee80211-1.2.18/ieee80211_module.c: At top level:
/home/gooch/ieee80211-1.2.18/ieee80211_module.c:339: fatal error: opening dependency file /home/gooch/ieee80211-1.2.18/.ieee80211_module.o.d: Permission denied
compilation terminated.
make[2]: *** [/home/gooch/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/gooch/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [modules] Error 2As you can see, It looks like it got rid of the proc_net errors but I still can't get it to install properly. Also, if I try to do the make SHELL=/bin/bash, it ends up being the exact same thing. This is really starting to get frustrating. Is there any way I can bypass this or do I need to install Ieee80211? If so, how can I do it without all these errors in Ubuntu 10.04. Please help me out guys. Thanks.

---

### Post by bachenke on 2010-07-21
I'm also stuck at this stage. After spending the better part of two days googling for a solution I'm about to give up...

---


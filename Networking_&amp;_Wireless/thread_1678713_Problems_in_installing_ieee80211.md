---
title: "Problems in installing ieee80211"
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by israeltan on 2011-01-30
Hi!
 I'm trying to Install ieee80211-1.2.18, and i tried to follow instructions from other threads.
And when I type 'make', i get these messages:
> 
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.35-25-generic for ieee80211 components...
make -C /lib/modules/2.6.35-25-generic/build M=/home/tan/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
/home/tan/ieee80211-1.2.18/Makefile:17: 
/home/tan/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/tan/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/tan/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/tan/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/tan/ieee80211-1.2.18/ieee80211_module.o
/home/tan/ieee80211-1.2.18/ieee80211_module.c: In function ‘alloc_ieee80211’:
/home/tan/ieee80211-1.2.18/ieee80211_module.c:150: error: ‘struct net_device’ has no member named ‘change_mtu’
/home/tan/ieee80211-1.2.18/ieee80211_module.c:155: warning: assignment from incompatible pointer type
{standard input}: Assembler messages:
{standard input}:9: Warning: can't open .lst: Permission denied
GAS LISTING              page 1


   1                   .file "ieee80211_module.c"
   9                  .Ltext0:

GAS LISTING              page 2


DEFINED SYMBOLS
                            *ABS*:0000000000000000 ieee80211_module.c

NO UNDEFINED SYMBOLS
make[2]: *** [/home/tan/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/tan/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make: *** [modules] Error 2

I'm using ubuntu 10.
And I've already searched the forums for days about this topic and can't find anything. :(
What should I do?  I'm quite new to this.
Thanks for your help! :D

---

### Post by myth1914 on 2011-01-30
First, I would attempt > make SHELL=/bin/bash

Also, have you confirmed you have build-essentials installed?

---

### Post by israeltan on 2011-01-30
Yes, I have also tried 'make SHELL=/bin/bash'
And i have also ran these lines:
'sudo apt-get install build-essential
sudo apt-get install libssl-dev'

Any ideas? Thanks! :D

---


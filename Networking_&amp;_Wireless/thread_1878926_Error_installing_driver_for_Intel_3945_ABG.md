---
title: "Error installing driver for Intel 3945 ABG"
date: 2011-11-10
forum: Networking &amp; Wireless
---

### Post by swooshgt on 2011-11-10
I'm trying to install wireless driver for my notebook to make possible  to Inject packet 


```
wget http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2 tar -xjf ipwraw-ng* cd ipwraw-ng
```But when i do the

```
Make
[/CODE

]I get the following errors:

[CODE]WARNING: $SHELL not set to bash. If you experience build errors, try 'make SHELL=/bin/bash'.  make -C /lib/modules/2.6.38-11-generic/build M=/home/giacomo/ipwraw-ng modules make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'  WARNING: $SHELL not set to bash. If you experience build errors, try 'make SHELL=/bin/bash'.    CC [M]  /home/giacomo/ipwraw-ng/ipwraw.o /home/giacomo/ipwraw-ng/ipwraw.c:43:27: fatal error: net/ieee80211.h: No such file or directory compilation terminated. make[2]: *** [/home/giacomo/ipwraw-ng/ipwraw.o] Error 1 make[1]: *** [_module_/home/giacomo/ipwraw-ng] Error 2 make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic' make: *** [modules] Error 2




```net/ieee80211.h: No such file or directory compilation terminated.

I already updated headers btw

---


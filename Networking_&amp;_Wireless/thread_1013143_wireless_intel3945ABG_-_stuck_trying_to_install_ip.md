---
title: "wireless intel3945ABG - stuck trying to install ipw345"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by kenny99 on 2008-12-16
Hi, I'm having a nightmare trying to sort out wireless with intel3945ABG, have worked through most of the ndiswrapper guide but i can't install ipw345 and get the following errors, which i don't know how to rectify - can anyone help?

```
nicky@nicky-laptop:~$ modprobe ipw3945
FATAL: Module ipw3945 not found.
nicky@nicky-laptop:~$ modprobe ipw3945
FATAL: Module ipw3945 not found.
nicky@nicky-laptop:~$ clear
nicky@nicky-laptop:~$ cd ieee80211-1.2.18/
nicky@nicky-laptop:~/ieee80211-1.2.18$ sudo make install
[sudo] password for nicky: 
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
make -C /lib/modules/2.6.24-22-generic/build M=/home/nicky/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-22-generic'
/home/nicky/ieee80211-1.2.18/Makefile:17: 
/home/nicky/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/nicky/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/nicky/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/nicky/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/nicky/ieee80211-1.2.18/ieee80211_module.o
/home/nicky/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/home/nicky/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/home/nicky/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/nicky/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/nicky/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/nicky/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/home/nicky/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/nicky/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
make: *** [modules] Error 2
nicky@nicky-laptop:~/ieee80211-1.2.18$
```

---


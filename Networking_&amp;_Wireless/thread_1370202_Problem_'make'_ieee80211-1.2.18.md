---
title: "Problem 'make' ieee80211-1.2.18"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by terminator557 on 2010-01-02
well, im having some problems , just read the code


```
terminator557@Dissimulo:~/ieee80211-1.2.18$ sudo make INC=/path/to/kernel-headers/include/
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.31-16-generic for ieee80211 components...
make -C /lib/modules/2.6.31-16-generic/build M=/home/terminator557/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
/home/terminator557/ieee80211-1.2.18/Makefile:17: 
/home/terminator557/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/terminator557/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/terminator557/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/terminator557/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/terminator557/ieee80211-1.2.18/ieee80211_module.o
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c: In function ‘alloc_ieee80211’:
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c:148: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c:149: error: ‘struct net_device’ has no member named ‘change_mtu’
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c:153: error: ‘struct net_device’ has no member named ‘get_stats’
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/home/terminator557/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/terminator557/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [modules] Error 2
terminator557@Dissimulo:~/ieee80211-1.2.18$ 
```

---

### Post by aalkounis on 2010-03-23
same problems here...also

```
sudo make SHELL=/bin/bash
```

doesn't work

---

### Post by Aitz on 2010-04-08
Hi,

I have the same problem. Can anybody help us?

Bye

---

### Post by fisix on 2011-02-24
bump, really need help on this!
thanks :)

---

### Post by war.ace on 2011-05-01
I have the same problem as well. can noone help us? I'm dying without my wireless :(

---


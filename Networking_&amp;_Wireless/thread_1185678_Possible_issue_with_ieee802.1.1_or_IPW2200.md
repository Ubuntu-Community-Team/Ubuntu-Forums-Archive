---
title: "Possible issue with ieee802.1.1 or IPW2200"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by neonic75 on 2009-06-12
Hi folks,
I 'll be honest in new enough to linux and already iv made a mess.  I was trying to update IPW drivers and now have no wireless. Tried reinstalling and I get an error2. Kinda scratching my head with this one.
First a few outputs:
```

nick@nick-linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```Now i know my card is there upuntill the update pan0 was called en0.
so i try and install the update and this is what i get.

```

nick@nick-linux:~/Desktop/ipw2200-1.2.2$ make
-e 
 ERROR: ieee80211.h not found in '/lib/modules/2.6.28-11-generic/include'.

-e You need to install the ieee80211 subsystem from http://ieee80211.sf.net
and point this build to the location where you installed those sources, eg.:

% make IEEE80211_INC=/usr/src/ieee80211/

will look for ieee80211.h in /usr/src/ieee80211/net/

make: *** [check_inc] Error 1


```ok fair enough... i can deal with this... rtfm and all the rest just follow on screen instructions....so thats what I do. But......

```

nick@nick-linux:~/Desktop/ieee80211-1.2.18$ sudo make
[sudo] password for nick: 
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.28-11-generic for ieee80211 components...
make -C /lib/modules/2.6.28-11-generic/build M=/home/nick/Desktop/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
/home/nick/Desktop/ieee80211-1.2.18/Makefile:17: 
/home/nick/Desktop/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/nick/Desktop/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/nick/Desktop/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/nick/Desktop/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/nick/Desktop/ieee80211-1.2.18/ieee80211_module.o
/home/nick/Desktop/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/home/nick/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/home/nick/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/nick/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/nick/Desktop/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/nick/Desktop/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/home/nick/Desktop/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/nick/Desktop/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [modules] Error 2


```And now I'm nice and stuck...
Has anyone got any ideas? All greatly appericiated.
Cheers

---

### Post by mikimis on 2009-06-13
I'm having this problem too...I've read through all the other material on this issue but nothing has turned up yet.

---


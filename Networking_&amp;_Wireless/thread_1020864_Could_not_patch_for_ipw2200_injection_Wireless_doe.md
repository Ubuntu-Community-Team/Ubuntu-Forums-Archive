---
title: "Could not patch for ipw2200 injection: Wireless does not work anymore"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by silent contender on 2008-12-24
I tried to follow several tutorials in this forum to enable injection my ipw2200 driver.  I removed the original driver from within the ipw2200 folder (so no wireless anymore):

```
sudo .remove-old
```

Also, I cannot compile the ieee80211 library(?).  I get this error:

```
sudo make SHELL=/bin/bash
Checking in /lib/modules/2.6.27-9-generic for ieee80211 components...
make -C /lib/modules/2.6.27-9-generic/build M=/home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17/ieee80211_module.o
/home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17/ieee80211_module.c: In function ‘ieee80211_init’:
/home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17/ieee80211_module.c:267: error: ‘proc_net’ undeclared (first use in this function)
/home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17/ieee80211_module.c:267: error: (Each undeclared identifier is reported only once
/home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17/ieee80211_module.c:267: error: for each function it appears in.)
/home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17/ieee80211_module.c:296: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [modules] Error 2

```

My computer specs and the downloads 
OS: Ubuntu 8.10
Kernel: 2.6.27-9-generic
Downloaded: ipw2200-1.2.1.tar.gz ieee80211-1.2.17.tgz ipw2200-1.2.1-inject_patch.tar.gz

Any help would be appreciated.

Edit:
I reinstall the kernel and the original driver.  I tried compiling ieee80211-1.2.17 again, got a little further:

```
sudo make SHELL=/bin/bash
Checking in /lib/modules/2.6.27-9-generic for ieee80211 components...
/lib/modules/2.6.27-9-generic/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.27-9-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.27-9-generic/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.27-9-generic/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.27-9-generic/kernel/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.27-9-generic/build/include/config/ieee80211.h
/lib/modules/2.6.27-9-generic/build/include/linux/ieee80211.h
/lib/modules/2.6.27-9-generic/build/include/config/ieee80211.h
/lib/modules/2.6.27-9-generic/build/include/linux/ieee80211.h
Above files found.  Remove? [y],n y
CONFIG_IEEE80211=m
CONFIG_IEEE80211_CRYPT_CCMP=m
CONFIG_IEEE80211_CRYPT_TKIP=m
CONFIG_IEEE80211_CRYPT_WEP=m
Above definitions found.  Comment out? [y], n y
ieee80211 symbols are found from /lib/modules/2.6.27-9-generic/build/Module.symvers. Do you want to strip them? [y],n y
make -C /lib/modules/2.6.27-9-generic/build M=/home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17/ieee80211_module.o
/home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17/ieee80211_module.c: In function ‘ieee80211_init’:
/home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17/ieee80211_module.c:267: error: ‘proc_net’ undeclared (first use in this function)
/home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17/ieee80211_module.c:267: error: (Each undeclared identifier is reported only once
/home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17/ieee80211_module.c:267: error: for each function it appears in.)
/home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17/ieee80211_module.c:296: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/bryant/Toolkit/wirelessDriver/ieee80211-1.2.17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [modules] Error 2

```

---

### Post by Vitron on 2008-12-26
I seem to be having a similar problem...? :(

```
vitron@AndrAIa:~/ieee80211-1.2.17$ sudo make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.27-9-generic for ieee80211 components...
make -C /lib/modules/2.6.27-9-generic/build M=/home/vitron/ieee80211-1.2.17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
/home/vitron/ieee80211-1.2.17/Makefile:17: 
/home/vitron/ieee80211-1.2.17/Makefile:18: WARNING: $SHELL not set to bash.
/home/vitron/ieee80211-1.2.17/Makefile:19: If you experience build errors, try
/home/vitron/ieee80211-1.2.17/Makefile:20: 'make SHELL=/bin/bash'.
/home/vitron/ieee80211-1.2.17/Makefile:21: 
  CC [M]  /home/vitron/ieee80211-1.2.17/ieee80211_module.o
/home/vitron/ieee80211-1.2.17/ieee80211_module.c: In function ‘ieee80211_init’:
/home/vitron/ieee80211-1.2.17/ieee80211_module.c:267: error: ‘proc_net’ undeclared (first use in this function)
/home/vitron/ieee80211-1.2.17/ieee80211_module.c:267: error: (Each undeclared identifier is reported only once
/home/vitron/ieee80211-1.2.17/ieee80211_module.c:267: error: for each function it appears in.)
/home/vitron/ieee80211-1.2.17/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/vitron/ieee80211-1.2.17/ieee80211_module.c:296: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/home/vitron/ieee80211-1.2.17/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/vitron/ieee80211-1.2.17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [modules] Error 2


vitron@AndrAIa:~/ieee80211-1.2.17$ sudo make SHELL=/bin/bash
Checking in /lib/modules/2.6.27-9-generic for ieee80211 components...
make -C /lib/modules/2.6.27-9-generic/build M=/home/vitron/ieee80211-1.2.17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/vitron/ieee80211-1.2.17/ieee80211_module.o
/home/vitron/ieee80211-1.2.17/ieee80211_module.c: In function ‘ieee80211_init’:
/home/vitron/ieee80211-1.2.17/ieee80211_module.c:267: error: ‘proc_net’ undeclared (first use in this function)
/home/vitron/ieee80211-1.2.17/ieee80211_module.c:267: error: (Each undeclared identifier is reported only once
/home/vitron/ieee80211-1.2.17/ieee80211_module.c:267: error: for each function it appears in.)
/home/vitron/ieee80211-1.2.17/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/vitron/ieee80211-1.2.17/ieee80211_module.c:296: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/home/vitron/ieee80211-1.2.17/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/vitron/ieee80211-1.2.17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [modules] Error 2
vitron@AndrAIa:~/ieee80211-1.2.17$ 

```

---

### Post by silent contender on 2008-12-27
Here is a similar (actually identical) and more active thread:

[http://ubuntuforums.org/showthread.php?t=996574]("http://ubuntuforums.org/showthread.php?t=996574")

---

### Post by sambita on 2009-02-04
I was trying to patch it too and now wireless doesnt work anymore, can you tell me how did you resintalled the kernel and the original driver?

Thanks in advance

*Edit: ive been able to solve this problem. [here is how]("http://ubuntuforums.org/showthread.php?p=6688433#post6688433")

---


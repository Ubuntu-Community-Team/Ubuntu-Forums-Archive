---
title: "Installing ieee80211 fails"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by WarholsGhost on 2009-06-17
i'm trying to install the linux driver from intel and it wants me to install ieee80211 and this is the error i'm getting from that makefile:

```

frenzy@emma:~/Desktop/ieee80211-1.2.18$ sudo make IEEE80211_INC=/usr/src/ieee80211/
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.28-11-generic for ieee80211 components...
make -C /lib/modules/2.6.28-11-generic/build M=/home/frenzy/Desktop/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
/home/frenzy/Desktop/ieee80211-1.2.18/Makefile:17: 
/home/frenzy/Desktop/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/frenzy/Desktop/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/frenzy/Desktop/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/frenzy/Desktop/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/frenzy/Desktop/ieee80211-1.2.18/ieee80211_module.o
/home/frenzy/Desktop/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/home/frenzy/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/home/frenzy/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/frenzy/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/frenzy/Desktop/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/frenzy/Desktop/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/home/frenzy/Desktop/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/frenzy/Desktop/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [modules] Error 2

```

---

### Post by synapsys on 2009-06-17
Did you do what it said to do?

---

### Post by WarholsGhost on 2009-06-17
yes i did it still gives an error:

```

$ sudo make IEEE80211_INC=/usr/src/ieee80211/ SHELL=/bin/bash
Checking in /lib/modules/2.6.28-11-generic for ieee80211 components...
make -C /lib/modules/2.6.28-11-generic/build M=/home/frenzy/Desktop/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/frenzy/Desktop/ieee80211-1.2.18/ieee80211_module.o
/home/frenzy/Desktop/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/home/frenzy/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/home/frenzy/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/frenzy/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/frenzy/Desktop/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/frenzy/Desktop/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/home/frenzy/Desktop/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/frenzy/Desktop/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [modules] Error 2

```

---

### Post by kerry_s on 2009-06-17
how about you tell us what kind of wireless it is & some one who's already got it working can tell you how.

---

### Post by WarholsGhost on 2009-06-17
It's an intel card, i'm trying to install the linux driver from intel.

---

### Post by selepo on 2009-06-28
This should help you modify 2 of the files to solve the compile errors, I however get others.

http://ubuntuforums.org/showpost.php?p=6688433&postcount=2]this%20post[/URL].%20Now,%20if%20you%20want%20to%20enable%20injection,%20you%27ll%20need%20to%20follow[URL=%22http://ubuntuforums.org/showpost.php?p=6934824&postcount=34

---


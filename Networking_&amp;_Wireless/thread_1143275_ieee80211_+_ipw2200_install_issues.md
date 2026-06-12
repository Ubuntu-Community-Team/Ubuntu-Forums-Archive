---
title: "ieee80211 + ipw2200 install issues"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by acidgawd on 2009-04-29
This problem has been posted before and there was no working solution given.

How do you install these when you get this:


waqar@waqslaptop:/Desktop/ieee80211-1.2.18$ make
Makefile:17:
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21:
Checking in /lib/modules/2.6.24-16-generic for ieee80211 components...
make -C /lib/modules/2.6.24-16-generic/build M=/home/waqar/Desktop/ieee80211-1.2.18 modules
make [1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
/home/waqar/Desktop/ieee80211-1.2.18/Makefile:17:
/home/waqar/Desktop/ieee80211-1.2.18/Makefile:18: WARNING:$SHELL not set to bash
/home/waqar/Desktop/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/waqar/Desktop/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/waqar/Desktop/ieee80211-1.2.18/Makefile:21:
  CC [M]  /home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.o
/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.c: In function 'ieee80211_init':
/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: 'proc_net' undeclared (first use in this function)
/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.c: In function 'ieee80211_exit':
/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.c:297: error: 'proc_net' undeclared (first use in this function)
{standard input}: Assembler messages:
{standard input}:9: Warning: can't open .lst: Permission denied
GAS LISTING                      page 1


    1                    .file "ieee80211_module.c"
    9                    .Ltext0:

GAS LISTING                     page 2


DEFINED SYMBOLS
                             *ABS*:0000000000000000 ieee80211_module.c

NO UNDEFINED SYMBOLS
make[2]: *** [/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/waqar/Desktop/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2                      




I have searched everywhere and the only thing this forum has come up with yet is:

"You can reinstall the ieee80211 subsystem by going to synaptic and searching for the current kerner (i.e. search for '2.6.27-9') select reinstall for everything that you find that is already installed. This should do it."


THAT DOESN'T FIX IT:(:(:(

please help

---


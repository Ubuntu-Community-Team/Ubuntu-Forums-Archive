---
title: "Network Manager Wireless won't start. Help Please"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by maddbaron on 2011-07-14
Hi, I've been using a wired connection for the past few months,  I took the ethernet cable out and network manager won't switch to my wireless connection it won't even search for open connections. Only when I plug the cable back in does it work. 

Can someone help me fix this?

---

### Post by bkratz on 2011-07-14
> **maddbaron said:**
> Hi, I've been using a wired connection for the past few months,  I took the ethernet cable out and network manager won't switch to my wireless connection it won't even search for open connections. Only when I plug the cable back in does it work. 

Can someone help me fix this?



You really have not given anyone much information to go on. You might read this thread

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by maddbaron on 2011-07-14
I looked into my prop addtional drivers and saw that the broadcom driver wasn't activated.  I attempted to and I got an error to check a var log file and this is what I received

> 2011-07-14 23:31:58,523 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-07-14 23:31:58,523 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-07-14 23:31:58,523 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-07-14 23:31:58,606 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-07-14 23:31:58,607 DEBUG: fglrx.available: falling back to default
2011-07-14 23:31:58,867 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-07-14 23:31:58,868 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-07-14 23:31:58,894 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

I don't have anything nvidia in my system...so I'm a bit confused...I'm on an amd processor.

help please

---

### Post by wildmanne39 on 2011-07-15
Hi, the drivers for the broadcom chip that comes in natty do not work. Type this in a terminal
```
lspci -nn
```
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---


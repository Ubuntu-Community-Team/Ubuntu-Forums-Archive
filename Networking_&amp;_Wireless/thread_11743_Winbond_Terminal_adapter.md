---
title: "Winbond Terminal adapter"
date: 2005-01-19
forum: Networking &amp; Wireless
---

### Post by Rink on 2005-01-19
Hi

Trying to get my Winbond Terminal adapter running.

HiSax Drivers seem to load ok according to dmesg.
mISDNd starts.
Winbond w6692 driver starts.
mISDN_w6692 finds the adapter
w6692 card installed IRQ 177

All well and good. But then:

mISDN INTERNAL_ERROR in drivers/isdn/hardware/mISDN/stack.c:595
mISDN:addr(f0000) prim(f1980) failed err(fffffa4)

"wvdialconf" says:
Sorry, no modem was detected.

"isdnctrl dial ippp0" says:
Can't open /dev/isdninfo or /dev/isdn/isdninfo: no such file or directory

Any help would be appreciated.

Many thanks,

Dave

---

### Post by Rink on 2005-01-21
From what I can see from searching the net, the order in which the modules are loaded is important.

Anyone know where the modules are loaded?

Which script loads them on startup?

Many thanks

---

### Post by Nunnsby on 2008-02-06
Hi Rink, not sure if you are still checking this, as 3 years on is significant time, but can you tell me how you loaded the Winbond drivers? 
I am setting up a server for Hylafax, and the ISDN stuff is driving me crazy. Ihave no idea what to do here.

I have the same card, Winbond 6692, but have no clue where to start or how to go about this. ISDN support is very poorly documented anywhere! 

Any help would be appreciated.

Regards 

Richard

---


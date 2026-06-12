---
title: "Installing VS10259 PCMCIA &amp; Broadcom BCM94306MP REV 4"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by Sliphorn on 2010-03-31
Hello there...

Okay, I'm trying to install two devices...one at a time.  So far I've had zero luck with either.

1. ViewSonic VS10259 PCMCIA Wireless 802.11G PC Card Adapter.

2. Broadcom BCM94306MP REV 4 Internal Wireless Adapter.

I can't get either of these installed on an old Dell Inspiron 8500.  I'm really an absolute beginner with this...I've installed the newest Ubuntu on this machine and am trying to get it to connect to the internet, but am clueless.

Sorry if this should be posted in absolute beginner.  Don't want to double-post.

Thanks for any help.  I could use as much hand-holding with this as possible.

^_^

Sliphorn

---

### Post by johngreth on 2010-03-31
goto System->Administration->Hardware (or something like that). It should be able to automatically find the hardware and drivers for you to install. 

If that doesn't/didn't work:
Are you using 10.04 Beta or 9.10 or 8.10?

---

### Post by Sliphorn on 2010-03-31
Thanks for the quick reply.  No dice.  I went to system/administration/Hardware Drivers...and eventually I get a message:

No proprietary drivers are in use on this system.

I'm using 9.10...Any ideas?

---

### Post by johngreth on 2010-03-31
> No proprietary drivers are in use on this system.
It always says that until you enable the drivers, but if the drivers don't show up there, you could check the Hardware Support page to make sure Ubuntu Supports your hardware.

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by Sliphorn on 2010-03-31
Okay, how do I enable the drivers?  None show up...

In looking at the list of supported devices, mine doesn't show up...will one of the drivers for another card using the same chipset work?

I'm a bit confused...thanks for any help.

---

### Post by johngreth on 2010-03-31
If the devices don't show up in Hardware Drivers and they aren't in the list of supported devices, it is very difficult if not impossible to get them to work, especially for a beginner. I'm sorry, but I can't really help. Whenever things like this happen to me I back up all my files and spend a few days strait messing with my computer until I find a solution, and usually end up crashing my computer several times in the process. I always learn a lot from this, but I can't give a step by step to find a solution because I'm not familiar with the specific drivers. Maybe someone else can.

---

### Post by Sliphorn on 2010-03-31
Okay.  Thanks for your time.

---


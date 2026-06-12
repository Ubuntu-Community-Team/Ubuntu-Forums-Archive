---
title: "Antec Fusion Black LCD won't turn off on shutdown"
date: 2011-03-08
forum: Multimedia Software
---

### Post by gunnarflax on 2011-03-08
Hi! I've been struggling a while with getting the iMON LCD/IR-receiver on my Antec Fusion Black case to shutdown together with the system (XBMC Live 10). But it won't. When it's turned off the LCD still lights up the whole room. Many have proposed the "solution" of setting the machine into hibernation instead but that however won't work for me, since I'm unable to suspend my system.

It is the LCD/IR-module that prevents me from suspending and I haven't found a solution to properly unload it on suspending (it's way above my linux knowledge). I need help with getting the display to turn off the backlight when the system is turned off. Can anyone please help me?

If anyone also has the knowledge on how to get the eject function to work on my Antec Veris rm200 remote I would be very grateful, I was told about that it could get fixed with irexec but I do not know how since I haven't been able to find a good tutorial on the subject.

Thank you for helping me!

---

### Post by gunnarflax on 2011-03-09
bump*

---

### Post by gunnarflax on 2011-03-09
I just realised that I cannot turn off the power supply for LCD/IR-receiver because then I (probably) cannot boot the htpc with my remote control. What I want is for the backlight to go off on the display.

---

### Post by gunnarflax on 2011-03-09
I think I've managed to get it working (kinda). I read that it is a bug with USB3.0 that has been fixed in the Natty release but has not been included in Maverick. What I need to do was to add the line ```
SUSPEND_MODULES="xhci"
``` to the file ```
/etc/pm/config.d/unload_module
``` and then it suspended ergo the LCD is also black. I think I will settle with that, even though i'm unable to fully shut the computer down, if not anyone has a better solution.

---


---
title: "[SOLVED] strange display error with radeon X600 SE"
date: 2008-10-30
forum: Multimedia Software
---

### Post by Bazon on 2008-10-30
Hello!

After a fresh Intrepid Installation on my Fujitsu Siemens Amilio M6453G with an ATI Radeon X600 SE Graphicscard there occur strange display errors:
[b]Windows are partly transparent, which means you can see the desktop in parts of the window. 
When I hover with the mouse over that window, the window re-appears in small rectangulars.
[/b]In order to see the window again, I have to hover the whole window with the mouse, or minimize and maximize the window again, or make a screenshot. (On a screenshot everything is alright, so I can't show you....)

**So what can I do to avoid this strange behaviour? **

Unfortunatly, I don't even know which driver I use, as the xorg.conf is empty now.... :-(
I didn't change any graphic settings since intrepid installation.

---

### Post by Bazon on 2008-10-30
Could anybody at least give me a tip how to change the driver, please?
I installed xorg-driver-fglrx but I don't know how to use it, as all old descriptions with editing the xorg.conf are now useless....

---

### Post by Bazon on 2008-10-30
OK, I found it:
After installing xorg-driver-fglrx it appeared in system -> system-settings -> hardware-drivers as a new driver and could be activated there.
After rebooting the graphic errors disappeared, so this driver seems to work...
...looks like the problem is solved...! :-)

---


---
title: "Random Display Resolution changes"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by ArmedStupidity on 2007-06-25
My Edubuntu Feisty installs tend to randomly change display resolutions to 640x480, even after I edited "xorg.conf" to eliminate the resolutions other than 1024x768. Sometimes they boot at the native 1024x768 resolution, and sometimes they go to 640x480. Any help is greatly appreciated!

-A.C.

---

### Post by ArmedStupidity on 2007-06-29
*bump* 

Any help?

---

### Post by dondizzle on 2007-06-30
Had the problem and bought a new lcd and video card. I have the same problem even with my new 32" LCD and AGP -  BFG 7600. I have not found a way to resolve the issue yet. I also edited the xorg.conf with no success. Previously had 19" samsung CRt and Geforce2 MX.

---

### Post by ArmedStupidity on 2007-07-05
The monitor I use is an IBM CRT, an older 15' model. Graphics chipset is Intel onboard. I don't know much more about it, since I can't use them.

---

### Post by gtg on 2007-10-10
I am experiencing similar problems with 7.04 on a dual-boot Dell machine.

Just this morning the sequence went: powered on, got 640x480 (with no way to change it via System/Preferences/Screen Resolution Preferences), rebooted (via Reboot, not power down) and got the same low resolution screen, shut down, powered back on, and got the "right" resolution (1600 x 1200) with options to change via the Screen Resolution Preferences interface.

Hmmmm ...

Any update on how to solve this?

---

### Post by doctor_overbyte on 2007-12-27
I have the same random display resolution problem.   30% of the times I start up, the resolution is low (probably 640x480) at the "greeter" screen (login screen), and the other 70% of the startups have the resolution I actually have set in the preferences.  When I login and get the Gnome desktop, the resolution is the same as it was at the login screen and in the low-res mode the top panel is very confused.   That is, the normal "System" menu is missing (probably overlaid by other icons on the panel).  When I hover, the wrong tooltip pops up for some of the panel items as though there is something very wrong with the mapping between mouse pointer position and the icon positions.  This happens on Ubuntu 7.10 and 8.04 alpha 2 with the same probabilities.   That is, for 10 startups, I get 3 of the wrong resolution, randomly.  When I use ctrl-alt-backspace to shutdown the X server and it restarts without doing a complete warm boot of the system, the same thing happens randomly.  My computer has a GeForce FX 5500 nVidia graphics adapter.  I am using the nVidia restricted driver.  I tried it again with the open-source driver just to see if it is a driver bug rather than an X.org bug.   That is, I used Restricted Drivers Manager to remove the nVidia proprietary driver and revert to the open source driver for nVidia graphics adapters.  Then I re-booted 10 consecutive times on the same computer as before.   This time there were no low-resolution startups; every time the resolution was correct at the login (greeter) screen and on the desktop after I logged in.   My conclusion:   this is a bug in the nVidia restricted (proprietary) driver written by nVidia itself.

Has anyone reported this as a bug yet? I haven't been able to find anything like it by searching at bugs.ubuntu.com .

---


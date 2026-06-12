---
title: "Samsung SH-S223Q SATA DVD not playing"
date: 2009-02-07
forum: Mythbuntu
---

### Post by DrJohn999 on 2009-02-07
Using 8.10 on an Asus M3N878-EM, Samsung SH-S223Q SATA DVD is recognized by the BIOS, boots from DVD (to install MythBuntu for example). But, load a movie DVD, select 'Optical Disks' - 'Play DVD' and Myth frontend first crashed back to the desktop, where the DVD appeared as an available device (didn't try to play it from there though). Restarted the frontend, tried again, and this time 'Play DVD' paused with a blank screen for 10 sec and then returned to the 'Optical Disks' menu.

Is this SATA DVD a no-go for MythBuntu? I can swap in an IDE unit from my main PC and try again, but first I wanted to hear if anyone has had success with this type of DVD device.

-- DJ

---

### Post by klc5555 on 2009-02-08
> **DrJohn999 said:**
> Using 8.10 on an Asus M3N878-EM, Samsung SH-S223Q SATA DVD is recognized by the BIOS, boots from DVD (to install MythBuntu for example). But, load a movie DVD, select 'Optical Disks' - 'Play DVD' and Myth frontend first crashed back to the desktop, where the DVD appeared as an available device (didn't try to play it from there though). Restarted the frontend, tried again, and this time 'Play DVD' paused with a blank screen for 10 sec and then returned to the 'Optical Disks' menu.

Is this SATA DVD a no-go for MythBuntu? I can swap in an IDE unit from my main PC and try again, but first I wanted to hear if anyone has had success with this type of DVD device.

-- DJ

I use a SATA DVD with Mythtv 0.21, but not on a Ubuntu machine.

But I see from your sig that you are/were using 7.10 (presumably with 0.21 backports) and are now using 8.10. If this is the same machine, and if this move to 8.10 was via upgrade (not a new 8.xx install), and if the machine had at one time Mythtv 0.20.2 on it, the upgrade routine seems to fairly consistently fail to replace the old Mythdvd from Gutsy+0.20.2 with the Mythvideo that 0.21 uses. You may have to go into Synaptic and nuke the 0.20.2 Mythdvd packages manually, and then install/reinstall and configure Mythvideo.

If, however, the machine does not contain a package upgrade from the 0.20.2 version of Mythtv, then the problem must be something else. Perhaps make sure you have all the extra Medibuntu codecs/libraries installed for commercial DVDs as listed in the appropriate panel of the Mythbuntu control center. 

Good luck!

---

### Post by DrJohn999 on 2009-02-08
Thanks klc5555,

> ...make sure you have all the extra Medibuntu codecs/libraries installed for commercial DVDs as listed in the appropriate panel of the Mythbuntu control center

This is a new from scratch install. That was it. Works great now!

And... I hadn't even looked at my sig info since I first signed on. Updated now.

-- DJ

---

### Post by jory88 on 2009-03-07
Got a similar problem with an IDE DVD. Works from the desktop.. .but not recognized from Myth.

mythbuntu live disk 8.10

suggestions?

---


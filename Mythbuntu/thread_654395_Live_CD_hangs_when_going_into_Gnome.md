---
title: "Live CD hangs when going into Gnome"
date: 2007-12-31
forum: Mythbuntu
---

### Post by Lido on 2007-12-31
I'm trying to run the mythbuntu AMD64 7.10 live/install cd and it hangs up while going into gnome apparently.

The screen flashes the "LIRC IS NOT CONFIGURED" few lines that ends with ```
* Running local boot scripts (/etc/rc.local)           [OK]
``` three times, then it goes to something like "Reduced graphics mode" and asks if I want to configure or continue. I selected my monitor and graphics card and test it and it works, but then it goes back to the aformentioned text and doesn't properly go into gnome. Same thing if I don't try to configure and just hit 'continue'.  Hitting 'esc' and ctrl-c or enter doesn't help, but what I type shows up on the screen. No prompt though, it just lets me type and doesn't do much else. To get out of it, I've hit ctrl/alt/delete and it gives me a message that starts with "Stopping Gnome Display Manager" and reboots. I haven't found any posts that cover this.

I've tried a different keyboard (my usb one won't let me select the initial startup menu that comes up when the cd first loads).

My hardware is an ASROCK AM2 motherboard with NVIDIA 7 series graphics on board. One sata hard drive, an IDE CD/DVD drive and 2gb of ram.

---

### Post by superm1 on 2007-12-31
> **Lido said:**
> I'm trying to run the mythbuntu AMD64 7.10 live/install cd and it hangs up while going into gnome apparently.

The screen flashes the "LIRC IS NOT CONFIGURED" few lines that ends with ```
* Running local boot scripts (/etc/rc.local)           [OK]
``` three times, then it goes to something like "Reduced graphics mode" and asks if I want to configure or continue. I selected my monitor and graphics card and test it and it works, but then it goes back to the aformentioned text and doesn't properly go into gnome. Same thing if I don't try to configure and just hit 'continue'.  Hitting 'esc' and ctrl-c or enter doesn't help, but what I type shows up on the screen. No prompt though, it just lets me type and doesn't do much else. To get out of it, I've hit ctrl/alt/delete and it gives me a message that starts with "Stopping Gnome Display Manager" and reboots. I haven't found any posts that cover this.

I've tried a different keyboard (my usb one won't let me select the initial startup menu that comes up when the cd first loads).

My hardware is an ASROCK AM2 motherboard with NVIDIA 7 series graphics on board. One sata hard drive, an IDE CD/DVD drive and 2gb of ram.
Try "safe graphics mode" in the cd boot options.

---

### Post by StampU on 2007-12-31
I am having the same issue.  Safe graphics mode hangs as well :(.  I think there is a problem with my video card.  I am using the ATI Saphire (Radeon) HD 2600.  So far my only success is with Ubuntu Alt CD, installing in command line.  lspci lists the ATI card as unknown :(.

Is there any way I can load 3rd party ATI drivers on the installation of Mythbuntu Live?  My plan at this point is to continue with Ubuntu Alt on the command line, hopefully install the ATI drivers, install ubuntu desktop. and then finish up with MythTV.  If anyone has a better suggestion, I would appreciate it. Thanks

---

### Post by superm1 on 2007-12-31
> **StampU said:**
> I am having the same issue.  Safe graphics mode hangs as well :(.  I think there is a problem with my video card.  I am using the ATI Saphire (Radeon) HD 2600.  So far my only success is with Ubuntu Alt CD, installing in command line.  lspci lists the ATI card as unknown :(.

Is there any way I can load 3rd party ATI drivers on the installation of Mythbuntu Live?  My plan at this point is to continue with Ubuntu Alt on the command line, hopefully install the ATI drivers, install ubuntu desktop. and then finish up with MythTV.  If anyone has a better suggestion, I would appreciate it. Thanks
Yeah,

You should be able to hit <ctrl><alt><f1> and then have access to do apt-get install xorg-driver-fglrx, or to wget the .run file etc.

---

### Post by Lido on 2007-12-31
:redface:Thanks! I probably would have tried that earlier, but got distracted because my usb keyboard wasn't working at that stage of the startup process so I couldn't choose anything besides the default until I attached a ps2 keyboard. Now I've got to figure out how to get everything working now that the installation is done.

---


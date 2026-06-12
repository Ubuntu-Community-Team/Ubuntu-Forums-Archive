---
title: "Black screen with Sapphire 4350 ATI card"
date: 2009-08-13
forum: Multimedia Software
---

### Post by hopwon on 2009-08-13
Hi, when I added this card to my system and booted. The system noted the HW change and tried to reconfigure for the new card. This failed with an error (EE no drivers found) and after a reboot tty7 is black - nothing - nada. If I copy back the backup xconf.org file and also configure the MB BIOS to use the on board VGA it all comes back fine. 
I want to use my shiny new graphics card. Has anyone fixed this?
I have tried loading Nvidia drivers but this reports no hardware.

Ubuntu 9.04, 1GB ram, 3TB disk

---

### Post by markbuntu on 2009-08-13
nvidia drivers will not work with ati hardware. What you need is the latest ati driver from the ati site. 

But first you need to make sure that you have completely removed any proprietary driver you may have on your system, like an old nvidia driver or old ati driver that you used for your previous card and set xorg.conf to use the VESA driver.

Once you have done that you should be able to boot with your new card in VESA mode and then get the new driver from ati and install it. I do not think the driver in the Jaunty repository supports your card but the newest one at ati does for sure.

---

### Post by hopwon on 2009-08-14
> **markbuntu said:**
> nvidia drivers will not work with ati hardware. What you need is the latest ati driver from the ati site. 

But first you need to make sure that you have completely removed any proprietary driver you may have on your system, like an old nvidia driver or old ati driver that you used for your previous card and set xorg.conf to use the VESA driver.

Once you have done that you should be able to boot with your new card in VESA mode and then get the new driver from ati and install it. I do not think the driver in the Jaunty repository supports your card but the newest one at ati does for sure.

Thanks dude, I've tried the following but still get a black screen: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Alternatives](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Alternatives)

But I never did the full removal of all other drivers first. Will try your suggestion. 
Thanks!

---


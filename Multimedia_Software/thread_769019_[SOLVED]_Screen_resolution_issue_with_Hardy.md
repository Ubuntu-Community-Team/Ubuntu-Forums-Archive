---
title: "[SOLVED] Screen resolution issue with Hardy"
date: 2008-04-26
forum: Multimedia Software
---

### Post by kgriff on 2008-04-26
I just installed Hardy on a machine with video on the motherboard.  Video chipset is Nvidia GeForce6-class(That, from the manual.  I do not know what the actual chipset is.
Restricted drivers have been installed.

Roughly every other reboot of the machine, it comes up in safe graphics mode.  If I reboot again, it comes up normally.  Another reboot, it&#347; in safe graphics mode.  Rinse, lather, repeat.

Not sure what&#347; going on here.  I also do not know where Hardy gets the video resolution from.  Apparently, it&#347; not in xorg.conf?  Presumably, I could still specify video resolution in xorg.conf, but looking at this file after install of the restricted drivers, there is no video resolution called out.

Can anyone tell me what´s going on?  It may be obvious from the question here that I am a beginner.  If it&#347; not obvious, now you know.  Any help would be greatly appreciated.  It get&#347; moderately annoying to have to reboot the machine every other time I want to use in order to get anything other than 640x480.

---

### Post by ubuntu-freak on 2008-04-26
Not sure why it keeps reverting to safe-mode, but in Gutsy it seemed to help make the driver choice stick when I enabled effects in System>Preferences>Appearance>Effects. Would be worth filing a bug report though.
 
Is your resolution okay when the correct driver is used? If not, you should file a bug report for that too, but you may be able to fix that by using the Terminal or Alt-F2 and typing "gksudo displayconfig-gtk" and your password when prompted, then set your resolution with that. Reboot.
 
Nathan

---

### Post by irifan on 2008-04-26
have you tried 

sudo displayconfig-gtk ?

After that I had a proper xorg.conf file.

---

### Post by kgriff on 2008-04-26
Since I started this thread, I left my computer for a while, then came back, only to have it start up with the correct resolution.  I proceeded to reboot several times since then just to see what would happen.  It has come up with the correct resolution each time.
For the moment, all seems to be okay.  If it happens again, though, I&#314;l try displayconfig-gtk and maybe file a bug report.
Thanks for you input.

---

### Post by ubuntu-freak on 2008-04-26
> **kgriff said:**
> Since I started this thread, I left my computer for a while, then came back, only to have it start up with the correct resolution.  I proceeded to reboot several times since then just to see what would happen.  It has come up with the correct resolution each time.
For the moment, all seems to be okay.  If it happens again, though, I&#314;l try displayconfig-gtk and maybe file a bug report.
Thanks for you input.

 
Sounds like the issue I had, something somewhere made it stick, just like enabling effects did for me.
 
Glad you got it sorted,
 
Nathan

---


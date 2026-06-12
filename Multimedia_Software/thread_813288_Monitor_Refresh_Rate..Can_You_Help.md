---
title: "Monitor Refresh Rate..Can You Help?"
date: 2008-05-30
forum: Multimedia Software
---

### Post by newbrain on 2008-05-30
Hi,
I'm a real green horn when it comes to linux so please be patient with me. I've just installed ubuntu 8.04 (2.6.24-17) onto my old Dell GX270. I have updated the bios (A07).

When ubuntu is loading i see the progress bar, and everything looks fine. However when it comes to the login-screen. the refresh rate is set to high, and the monitor has problems. when i log it, it reset the refresh rate back (becuase i went into the System/Pref/Screen Resolution and changed it)

My question is this. how do i configure ubuntu to use the correct refesh rate between the progress bar, the unbuntu desktop. I have looked at xorg.config, but it does not seem to contain what I expected:

Section Screen
Identifier "Default Screen"
Monitor "Configured Monitor"
...

what does configured monitor mean, and were is all the resolution and rate stuff I expect to see..

Oh i should point out that the Dell uses the intel exteme2 graphics chipset (nice....)
Section "Screen"

Regards
Steven (NewBrain)

---

### Post by Sam Lars on 2008-05-30
Try
```
gtf 1280 768 70
```
where 1280 768 is the resolution you want and 70 is the refresh rate.  It will give you something like this:
```
Modeline "1280x768_70.00" 94.98 1280 1352 1488 1696 768 769 772 800 -HSync +Vsync 
```
Paste that into the "Monitor" section of xorg.conf like this:
```
Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Plug 'n' Play"
Modelname "Plug 'n' Play"
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
Gamma 1.0
EndSection
```
and restart the X server.

---

### Post by newbrain on 2008-05-31
Thanks, but this did not work.

I think there must be another mechanism at play. Come on guys, does anyone know how the ubuntu decides which resolution and refresh rate to use at the login prompt?

Regards
Steven

---

### Post by Sam Lars on 2008-05-31
It's based on the X server, and the xorg.conf.  However, with Hardy, it seems that it wants to use xorg.conf.failsafe instead.  Whenever I have had to edit my xorg.conf, I removed all of the other xorg.conf.* files in the directory, and then X would use the xorg.conf.  Check the top of /var/log/Xorg.0.log to see what configuration file it is using.

---


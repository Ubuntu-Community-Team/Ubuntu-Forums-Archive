---
title: "Cannot Get Proper Resolution on Nvidia 5600"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by RobbieCrash on 2007-05-17
My monitor's native resolution is 1280*1024, but I cannot get anything more than 1280*960.

I've already done all the walk throughs everywhere, and tried to ignore the edid information my monitor is giving. Tried explicitly setting the resolution to 1280x1024_60, and commented out everything else in the monitor options, that left me with 1024*768 and 800*600 at 50 hz.

There is a verbose output of my x starting, and my xorg.conf at [http://pastebin.ca/488366](http://pastebin.ca/488366)

I am running feisty, with the restricted driver. Everything else related to my graphics works great, just the resolution is off.

---

### Post by rainforest on 2007-05-18
I had the same problem on my new Gateway laptop.
My display device is listed as Mobile 945GM/GMS/940GML Express Integrated Graphics Controller.

The solution that worked for me was found at [https://answers.launchpad.net/ubuntu/+source/gnome-media/+question/6436](https://answers.launchpad.net/ubuntu/+source/gnome-media/+question/6436)

In a nutshell I ...

* installed xserver-xorg-video-intel (which forced the removal of xserver-xorg-video-i810)

* ran sudo dpkg-reconfigure xserver-xorg (and followed prompts and used "i810" as the driver)

Don't know if this will help, but it may be along the right path for you.

-Ray

---

### Post by RobbieCrash on 2007-05-18
Reinstalling my driver and reconfiguring X doesn't work.

Oddly the nv driver gets the resolution and refresh rates perfectly.

---

### Post by RobbieCrash on 2007-05-21
Still looking for help on this one.

---

### Post by RobbieCrash on 2007-05-26
One more bump in hopes of some resolution.

No pun intended.

---


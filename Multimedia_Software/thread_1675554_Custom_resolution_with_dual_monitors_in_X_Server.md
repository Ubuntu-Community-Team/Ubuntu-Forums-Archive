---
title: "Custom resolution with dual monitors in X Server?"
date: 2011-01-25
forum: Multimedia Software
---

### Post by stugi on 2011-01-25
I'm currently running 10.10 64-bit version, with the current Nvidia driver installed for my 9600GT graphics card (2x DVI-out). With the card, I am running one VGA monitor and one HDMI TV (both using adaptors). I am running the screens in TwinView, using X Server Settings.

My problem is, with the resolution available for my HDTV. In both Windows (XP and 7) and Ubuntu, the current Nvidia drivers all report the native resolution as 1920x1080, this however, is incorrect; the reported native resolution of the TV (according to the manufacturer) is 1280x720; but even set to that, there are still a few pixels missing outside of the screen. 

In Windows, the Nvidia Control Panel lets me manually resize the desktop area on the HDTV, to a slightly smaller resolution than 1280x720, so that all pixels are within the viewing area. Is there anyway to do this with Ubuntu, using the current Nvidia driver? I cannot seem to find a way, using Nvidia X Server Settings.

---

### Post by BicyclerBoy on 2011-01-25
Your TV display maybe exhibiting overscan. Normally the default setting for TVs.

Try disable overscan in TV by using PC mode/just-scan/direct-pixel-mapping.
This will result in the best picture quality.
This is only possible via HDMI/DVI connection (as you are using).

The TV may be reporting full HD videos modes & scaling (internal pre-scaler) to native.
Marketing trick to allow HD logo.
The best result is using real native resolution direct pixel mapping.

Twinview prevents independent video mode settings because it uses a meta-mode virtual box.

Post/attach your /var/log/Xorg.0.log file..

---

### Post by awells527 on 2011-01-26
What model TV do you have?  My Sharp Aquos would overstretch the image, but changing the Picture Mode resolved the issue.  I can't remember the exact mode I set it to off the top of my head, but just scan through the options until you find one that works.

My TV also registered as 1280x720 (720p TV) by default, although I could send 1920x1080, but it looked horrible.

---

### Post by stugi on 2011-01-26
Thanks folks, I didn't realise the meaning of the term "overscan" until now. It seems, that there is an option on X Server Settings, to compensate for/reduce this. This works perfectly for me now :)

Didn't try changing the settings on my TV yet (an Alba model), as I've lost my remote and am awaiting a replacement. So glad I have Ubuntu running exactly how I need :)

---


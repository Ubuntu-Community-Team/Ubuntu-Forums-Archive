---
title: "Video configuration issues on Mini-Ubuntu"
date: 2012-11-26
forum: Multimedia Software
---

### Post by kyldere on 2012-11-26
I have installed Mini-Ubuntu (12.04.1 x86) on a [Kontron pITX system]("http://us.kontron.com/products/boards+and+mezzanines/embedded+sbc/pitx+25+sbc/pitxsp.html?searchtermresultpage=03001-0000-11-2") and installed Fluxbox as a window manager. Currently, I need to get the frequency to lock to 60Hz, but so far, xrandr shows a frequency of 0. Eventually, I'll need to get the display outputting to 1280x720, but I guess that it's probably best to tackle one issue at a time. I'm willing to post more information, but just don't know where to start. Any help would be appreciated. Thank you.

---

### Post by BicyclerBoy on 2012-11-26
That h/w uses atom pineview CPU/GPU & is supported by open source intel i915/i965 driver that is included with ubuntu in some form..

Post your /var/log/Xorg.0.log file (if there is one)...
Possible you have the fallback VESA or framebuffer driver..

---

### Post by kyldere on 2012-11-26
Here is the most recent Xorg.0.log (saved with a .txt extension added to the end; why aren't we able to upload logs?) I did have the xorg.conf cleaned up at one point (got rid of the directory errors, etc.), but I reloaded a base image onto the system after I got to the point where I could no longer even ssh into the system... Thanks for looking at this with me, by the way.

---

### Post by BicyclerBoy on 2012-11-26
The graphics is claimed by FBDEV.

You could try the most basic xorg.conf with:
```

Section "DRI"
    Group "video"
    Mode 0660
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
#        Option          "AccelMethod" "EXA"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```
Not sure what AccelMethod is supported by PineView..

If that makes no difference then you can blacklist fbdev in /etc/modprobe.d/blacklist-framebuffer.conf.

Changes to files in modprobe.d/*.conf may or may not need :
depmod -ae
&/or
update-initramfs -u
&/or a reboot logout/login..

---

### Post by kyldere on 2012-11-27
Thanks for the ideas and the trimmed down xorg.conf. I tried just using the "light" xorg.conf without any AccelMethod and with both SNA and UXA, without any noticeable difference. I'm still looking into other AccelMethod options that might be available for the GMA500.

Following your advice for next steps, I added "blacklist fbdev" to the end of the blacklist-framebuffer.conf list and ran depmod -ae -F /boot/System.map-3.2.0-32-generic-pae (it wanted a System.map file with the -e switch) and update-initramfs -u and rebooted, all with no luck. xrandr still reports only a resolution of 1024 x 768 @ 0Hz, regardless of which monitor (or EDID) is hooked up to the DVI port.

What can I look at next?

---

### Post by BicyclerBoy on 2012-11-27
On closer inspection your CPU is atom Z510 Silverthorne & not Pinview GMA3150..
The chipset is US15W with GMA500 poulsbo GPU (like you mentioned).

That's too bad..the potential of GMA500 might never be realised in linux.

There were a couple of GMA500 driver projects, one was using the close source PowerVR core.
All very messy & confusing.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

So the FBDEV driver (in Xorg.0.log) could be the codename for the right driver after all..
See if gma500_gfx is loaded..

I would try xorg-edgers ppa (later kernel) & then give it away & buy a new one..

---

### Post by kyldere on 2012-11-30
I managed to get the frequency set (and the resolution) by installing Mini-Ubuntu 11.10 and forcing the emgd drivers to be used. While this will work for the short term, I hope that the emgd drivers can eventually be made to work in the 12.04.x environment.

---

### Post by BicyclerBoy on 2012-11-30
From the posts I've seen, here on the forums, that's not going to happen..it is gma500_gfx only.
Look for posts by Bodhi Zazen.

[http://ubuntuforums.org/showthread.php?t=1984236&highlight=poulsbo](http://ubuntuforums.org/showthread.php?t=1984236&highlight=poulsbo)

If using 12.04 & later:
I would think you would have more "success" with later kernels fro xorg-edgers.

---


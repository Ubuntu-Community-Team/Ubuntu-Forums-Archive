---
title: "Screen just turns black when using fglrx module"
date: 2005-10-18
forum: Multimedia &amp; Video
---

### Post by matthias_k on 2005-10-18
I installed the fglrx driver for ATI Radeon cards. I first tried it the easy way and just told X to load the fglrx module instead of the ati module. Well, unfortunately, when starting X, the screen will turn black and I can't see a thing. I know that loading GDM for example works, I can even hear the annoying bongo sound. But no visuals.

The X logfile doesn't report any errors, so I don't even have a point where to start looking. Maybe it's my TFT making trouble? It works flawlessly with the settings which were detected on installation though, along with the ati driver module.

Any ideas? ^^

---

### Post by jrohde on 2005-10-18
Hi,

I had experience like this, but it was because i had an external monitor attached to my laptop. If you have the same, you should simply unplug the external monitor, until the laptop is properly configured.

Jakob

---

### Post by aSTeRiX on 2005-10-18
Maybe either or both the refresh rate and resolution are too large for your monitor to handle? That's happened to me when I set either of those too high.

---

### Post by mlomker on 2005-10-18
> The X logfile doesn't report any errors, so I don't even have a point where to start looking. Maybe it's my TFT making trouble? It works flawlessly with the settings which were detected on installation though, along with the ati driver module.


I'd guess that the resolution or refresh rates are off.  I'd **sudo dpkg-reconfigure xserver-xorg** and when you are asked about the resolution and refresh rates you'll want to input the numbers from your monitor's manual.  In the case of a TFT it probably only supports 60hz.

---

### Post by matthias_k on 2005-10-18
Hm, I didn't change anything in xorg.conf besides the driver. Since it's a TFT display, it should switch automatically to its native display mode (I have it connected to the DVI port on my graphics card).
That hasn't been an issue so far.

But did you run fglrxconfig and use this file instead of the xorg.conf that came with Breezy? Because I didn't.

---

### Post by matthias_k on 2005-10-18
Okay, now I have tried both: Reconfiguring xorg.conf using dpkg-reconfigure and using fglrxconfig, but neither worked. Even when I manually entered the display modes it didn't seem to show up anywhere in the xorg.conf file.

---

### Post by mlomker on 2005-10-18
You could give [this one]("http://www.objorkum.com/scripts/fglrxconfig/") a whirl.

If that doesn't work then you'll probably want to post your Xorg.0.log (preferably as an attachment).  You've looked through the output of **dmesg** for errors?

---

### Post by matthias_k on 2005-10-18
UPDATE:

I am getting errors/warnings now:

> matthias:~$ cat Xorg.0.log | grep ^\(WW\)
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) Ignoring request to load module GLcore
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): Bad V_BIOS checksum
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Specified desktop setup not supported: 8
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(EE) fglrx(0): DRIScreenInit failed!

Looks as if DRI doesn't work. But I nowhere set the bit-depth to 8! It's defaulted to 24. I even tried to remove everything related to the 8-Bit color depth settings, but no luck.

EDIT: Oh and, thanks for the link, but didn't work for me either :(
EDIT: No, dmesg output looks just fine, no kernel errors

---


---
title: "NVIDIA FX5500 resolution fix"
date: 2010-05-16
forum: Multimedia Software
---

### Post by CaponeSA on 2010-05-16
I have a FX5500 AGP Nvidia card and the 173 drivers works well.  I however bought a new Acer HD 22" monitor which supports up to 1920 x 1080 resolution.  The Nvidia driver seems to only support up to 1440x900 on this monitor via DVI.  Although the Nouveau driver supports the full resolution via DVI, the lack of 3D is a problem and the general performance is still not comparable to the Nvidia drivers.  

I then changed the DVI to VGA and got full resolution and even a very nice 1920 x 1200, which is strictly not supported by the Acer P225HQ.  The problem is that the VGA, being analog displays a bit fuzzy, so I spend a few hours trying to get the Nvidia 173 driver to support the full resolution.  Nearly giving up, I found a very elegant solution, as follows:

1 - Install the recommended Nvidia driver (System/Administration/Hardware Drivers)
2 - Reboot and open Nvidia control panel (System/Administration/Nvidia x server setting)
3 - Do not change anything, but click on "X server display configuration" and click on "save to X configuration file" (follow the steps)
4 - Your new XORG will be written and then close the control panel
5 - Edit XORG (sudo nano /etc/X11/xorg.conf) and add the following to the Monitor section:  Option "ModeValidation" "NoMaxPClkCheck"
6 - Save Xorg and restart

Viola, 1920 x 1080 fully supported with desktop effects via DVI on an old FX5500 card (glxgears runs smoothly and reports about 10000 fps)

If this does not work, try: Option "ModeValidation" "NoMaxPClkCheck,NoEdidMaxPClkCheck"

---

### Post by jmagsho on 2011-03-17
Just wanted to post a quick thanks for the fix. Worked like a charm with my FS 5600 and my new HD monitor.

---


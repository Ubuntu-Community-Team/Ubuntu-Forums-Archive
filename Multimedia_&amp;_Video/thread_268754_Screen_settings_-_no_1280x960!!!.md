---
title: "Screen settings - no 1280x960!!!"
date: 2006-09-30
forum: Multimedia &amp; Video
---

### Post by halon314 on 2006-09-30
I recently upgraded to a ViewSonic VX2025WM.  This is a 20.1" widescreen LCD.  I would like to run it at 1280x960, but only have the option for 1280x1024 which looks stretched.  How can I get 1280x960?

That section of my my /etc/X11/xorg.conf looks like this:

---------------------------
Section "Device"
Identifier "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
Driver "i810"
BusID "PCI:0:2:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "VX2025wm"
Option "DPMS"
HorizSync 30-82
VertRefresh 50-75
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
Monitor "VX2025wm"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
EndSection
---------------------------

Any input would be greatly appreciated!

Thanks,
-Brian

---

### Post by henriquemaia on 2006-09-30
Have you tried running

```
sudo dpkg-reconfigure xserver-xorg
```
?

---

### Post by croak77 on 2006-09-30
Or put  "1280x960" first in the "Modes" line.

---

### Post by halon314 on 2006-09-30
I'll try the 
      sudo dpkg-reconfigure xserver-xorg

I don't think putting "1280x960" first in the "Modes" line would help, considering the "1680x1050" option is first, and it doesn't show up on the options list either.

Alas, I will try.

Thank you for the input.

---

### Post by Over1ord on 2006-09-30
I just got a new Sumsung 19" widescreen SyncMaster 940bw and it has the same problem but I cant get the resolution 1440x900, even though its in my xorg.conf, only 1440x1050 which chops my bottom tool bar off the screen so I have to use 1600x1200 resolution cuz that one is the proper ration but it makes everything so small!  Not to mention my monitor keeps giving me error messages telling me I need  1440x900 resolution LOL.

---


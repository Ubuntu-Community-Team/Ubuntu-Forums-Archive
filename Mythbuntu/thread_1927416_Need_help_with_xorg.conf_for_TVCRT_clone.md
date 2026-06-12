---
title: "Need help with xorg.conf for TV/CRT clone"
date: 2012-02-18
forum: Mythbuntu
---

### Post by JimLS on 2012-02-18
I have Ubuntu 11.10 and a FX5200 card with svideo and VGA output.  I want the same display on both.  I was able to get TV output or VGA with almost nothing in my xorg.conf file (not sure why it only had about 3 lines).  It would use which ever was connected.  I did some searching for a file that would use both.  I have it working but not completely correctly.  The TV shows only the left upper about 2/3 of the screen.  And the same section is shaded slightly differently on the VGA monitor.  Here is what I think are the relevant sections of the file:
```

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Unknown monitor"
HorizSync 31.5 - 37.9
VertRefresh 50.0 - 70.0
Option "dpms"
EndSection

Section "Monitor"
Identifier "Monitor1"
HorizSync 30-50
VertRefresh 60
EndSection

Section "Device"
Identifier "Videocard0"
Driver "nvidia"
VendorName "Videocard vendor"
BoardName "NVIDIA GeForce FX (generic)"
Option "TwinView" "true"
Option "TwinViewOrientation" "Clone"
Option "MetaModes" "800x600,640x480"
Option "HorizSync" "CRT-0: 31.5-37.9; TV-0: 30-50"
Option "VertRefresh" "CRT-0: 50.0-70.0; TV-0: 60"
Option "ConnectedMonitor" "crt,tv"
EndSection

Section "Screen"
Identifier "Screen_tv"
Device "Videocard0"
Monitor "Monitor1"
DefaultDepth 24
subSection "Display"
Viewport 0 0 
Depth 24
Modes "800x600" "640x480"
EndSubSection
EndSection


Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
Modes "800x600" "640x480"
EndSubSection

EndSection
```

I tried replacing 
Option "TwinViewOrientation" "Clone"
with 
Option "Clone" "true" 
but that made the TV screen an extension to the right of the CRT screen.

First time messing with this stuffso I could use some help...

---

### Post by nickrout on 2012-02-18
what resolution are you running at? Most CRTs won't go over 800x600, and that is pushing it.

---

### Post by JimLS on 2012-02-19
I figured it out.  For clone mode the metamodes line needs to have the same resolution for tv and crt.  I put in:
"800x600,800x600;640x480,640x480" 
and it is working ok.  I think the default is the first one.

---


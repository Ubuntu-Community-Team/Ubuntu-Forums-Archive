---
title: "Dual Head: Powerbook and Cinema Display"
date: 2006-07-06
forum: Multimedia &amp; Video
---

### Post by Jason C. on 2006-07-06
Hello all,

I am running Ubuntu 6.06 (with Xorg 7.0.0) on a Powerbook G4 (video is
ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]).  I also have an
external Apple Cinema Display (20") and run these as a dual head setup
in Mac OS X.  I am trying to achieve the same result in Ubuntu, but have
failed miserably.  I have tried setting up the dual head using mergedfb
(configuration below)  following the example at:
[http://ozlabs.org/~jk/docs/mergefb/](http://ozlabs.org/~jk/docs/mergefb/)

as well as following the instructions in "man radeon."  This setup
displays the proper screen size as determined with "xrandr -q", but
displays the entire desktop on the Powerbook screen such that the screen
scrolls ("scrolling screen" phenotype) and the Cinema Display is blank.
Scrolling through the xserver log there are a few warnings (a video BIOS
error, a DRI error and an invalid IO allocation); the xserver appears to
be able to query(?) the Cinema Display (the serial no. and date of
manufacture for the display show up in the log).  If I have left out any
essential information please let me know and I will post, or if I should
be posting this elsewhere kindly point me in the appropriate direction.
I sincerely appreciate any help (I have been banging my head against the
wall for a few days now).

Thanks, Jason

----xorg.conf using mergedfb that gives scrolling screen-----
[Other sections deleted for brevity]

Section "Device"
Identifier "ATI (Primary)" 
Driver "radeon"
BusID "PCI:0:16:0"
Option "MergedFB" "true"
Option "MetaModes" "1280x854-1280x854 1280x854-1680x1050"
Option "CRT2Position" "LeftOf"
Option "MergedDPI" "100 100"
Screen 0
EndSection

Section "Device"
Identifier "ATI (Secondary)" 
Driver "radeon"
BusID "PCI:0:16:0"
Screen 1
EndSection

Section "Monitor"
Identifier "Notebook LCD"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Notebook"
Device "ATI (Primary)" 
Monitor "Notebook LCD"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x854"
EndSubSection
EndSection

Section "Monitor"
Identifier "Apple Cinema"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Cinema"
Device "ATI (Secondary)"
Monitor "Apple Cinema"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x854" "1680x1050"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "Notebook"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection

---


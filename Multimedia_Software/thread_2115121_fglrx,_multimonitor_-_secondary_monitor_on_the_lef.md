---
title: "fglrx, multimonitor - secondary monitor on the left problem"
date: 2013-02-12
forum: Multimedia Software
---

### Post by unheeding on 2013-02-12
Hello all! I'm having some difficulty with setting up my monitors as I would like them, I'll try to provide as much info as I can to diagnose the problem.

What I want is my Laptop screen(LVDS) to be on the right, and my CRT to be on the left, here is what my xorg.conf looks like:

[ryan@ubuntop X11]$ cat xorg.conf
Section "ServerLayout"
Identifier "aticonfig Layout"
Screen 0 "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]-0"
Option	 "VendorName" "ATI Proprietary Driver"
Option	 "ModelName" "Generic Autodetecting Monitor"
Option	 "DPMS" "true"
EndSection

Section "Monitor"
Identifier "0-LVDS"
Option	 "VendorName" "ATI Proprietary Driver"
Option	 "ModelName" "Generic Autodetecting Monitor"
Option	 "DPMS" "true"
Option	 "PreferredMode" "1366x768"
Option	 "TargetRefresh" "60"
Option	 "Position" "1024 0"
Option	 "Rotate" "normal"
Option	 "Disable" "false"
EndSection

Section "Monitor"
Identifier "0-CRT1"
Option	 "VendorName" "ATI Proprietary Driver"
Option	 "ModelName" "Generic Autodetecting Monitor"
Option	 "DPMS" "true"
Option	 "PreferredMode" "1024x768"
Option	 "TargetRefresh" "85"
Option	 "Position" "0 0"
Option	 "Rotate" "normal"
Option	 "Disable" "false"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "fglrx"
Option	 "Monitor-LVDS" "0-LVDS"
Option	 "Monitor-CRT1" "0-CRT1"
BusID "PCI:0:1:0"
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]-0"
Device "aticonfig-Device[0]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Virtual 2966 2966
Depth 24
EndSubSection
EndSection


That works! I get what I want: The CRT on the left, and my Laptop screen on the right. Perfect! Or so it would seem...


When the CRT is disconnected and disabled, everything works as usual. That is, until the computer is put into suspend and then woken up - the entire screen is shifted to the left by 1024 pixels. The mouse cannot go to the right side of the screen, it pushes against that 1024 pixel boundry like it was the edge of the screen. When I go into a tty, I am able to kill the X server. When it returns, everything is fine.

Note: this only happens when the CRT is disabled. If it is disconnected but still enabled, resuming from suspend works as normal.


As a workaround I have "moved" the CRT to be beneath the laptop screen, and that works. Any ideas? Is this just a bug in the catalyst drivers? I've experienced this on multiple distros, so I know it isn't just a Ubuntu problem, but I'd appreciate the help! Thanks.

---

### Post by unheeding on 2013-02-12
Bump.  I'd really like some answers!  Thanks.

---

### Post by jp734 on 2013-07-04
I think the problem is because you set the monitor as your primary display by setting its viewport to '0 0'. Your laptop screen should be the main screen "viewport 0 0".

---


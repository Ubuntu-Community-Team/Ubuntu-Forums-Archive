---
title: "add a custom modeline // nvidia drivers // on jaunty"
date: 2009-09-20
forum: Multimedia Software
---

### Post by jorgemarmo on 2009-09-20
Hi, I need some help here, hopefully u can help me...

I get a Samsung P2070 LCD monitor and when I plug it on the DVI of my GeFroce4 MX420 (running jackalope), it shrink, it's continuously blinking.... On WinXP I had to set a "custom timing" to CVT-RB to make it work... now on the linux nvidia control panel that option is not there, so I check a lot of forums and I believe to understand that I have to manually set the modeline, so I get it from Windows, (whit MonInfo) and I want to try it on jaunty, however I try to add this modeline to the xorg.conf but it doesn't work....

Modeline "1600x900" 108.000 1600 1624 1704 1800 900 901 904 1000 +hsync +vsync


nvidia drivers 96.43.10

This is my xorg.conf file
######
Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
Option "AddARGBGLXVisuals" "True"
EndSection

Section "Module"
Load "glx"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"
Option "NoLogo" "True"
EndSection
#####

1) could you tell me why this file looks empty compared with previous xorg.conf?? has something to do with xrandr??? because I also want to change a mouse configuration and it suppose to be there but it isn't.

2) could you tell me how to try this modeline?

thanks!

---


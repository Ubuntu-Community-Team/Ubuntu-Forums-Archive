---
title: "ATI Stuck in Clone Mode"
date: 2008-03-27
forum: Multimedia &amp; Video
---

### Post by tjwallis on 2008-03-27
I'm using 8.04 and I installed fglrx drivers, and they are working great. The only problem is I'm stuck in clone mode and I have another screen i want to utilize. I have tried lots of things.

1.amdccc
This works as so long as i don't reboot/restartX as soon as I do X goes back to using clone mode.

2. sudo aticonfig --initial=dual-head --screen-layout=left
This setup dual X servers on each screen. I could live with this if 3D worked correctly but it dosen't

3. sudo aticonfig --dtop=horizontal --overlay-on=1
Reboot/restartX It reverts to clone mode.

Thanks

---

### Post by uDanimal on 2008-03-28
[http://ubuntuforums.org/showthread.php?t=301941&highlight=ati+dual+head+fglrx](http://ubuntuforums.org/showthread.php?t=301941&highlight=ati+dual+head+fglrx)

This worked for me on Gutsy, I haven't tried dual screens yet in Hardy.

---

### Post by tjwallis on 2008-03-28
I tried it no luck. I think it might be something thats run on login. Because it works in the login screen but as soon as I login in my monitors go dark, like X was just reset, and the come back  as clone displays.

---

### Post by tjwallis on 2008-03-28
bump

---

### Post by Yellow Pasque on 2008-03-28
What does your /etc/X11/xorg.conf look like at this point?

---

### Post by misterhead on 2008-03-28
There is a new Xrandr gui that should remeber your settings after restart, unless something in your xorg.config tells it otherwise.

I believe it was under Applications/Other. ( I just switched back to 7.10 so I'm unable to look at it now.) When I used it, it would remember "big desktop" after reboot, but it didn't give me the option to move screens around. (left of/ right of placement) So I still had to open a terminal and and "xrandr" my desired setup. DVI-0 right of LVDS or whatever.

---

### Post by tjwallis on 2008-03-28
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by tjwallis on 2008-03-28
After using amdcccle to manipulate xorg.conf

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "vmmouse"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal,reverse"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

it stays like this after reboot but it is in clone display instead of big desktop.

The Xrandr gui doesn't even detect both my screens.

Here is the output from xrandr ran in terminal

Screen 0: minimum 0 x 0, current 1600 x 1200, maximum 3600 x 1440
default connected 1600x1200+0+0 0mm x 0mm
   3600x1440      60.0  
   1800x1440      70.0     60.0  
   1792x1344      75.0     60.0  
   1680x1050      60.0  
   1600x1200      85.0     75.0     60.0*   100.0  
   1280x1024      85.0     75.0     70.0     60.0     47.0     43.0     90.0    100.0  
   1440x900       60.0  
   1400x1050      60.0  
   1280x960       60.0  
   1280x768       60.0  
   1280x720       60.0  
   1152x864       85.0     75.0     70.0     60.0     47.0     43.0    100.0  
   1024x768       85.0     75.0     72.0     70.0     60.0     43.0    150.0    120.0    100.0     90.0  
   800x600        85.0     75.0     72.0     70.0     60.0     56.0    160.0    120.0    100.0     90.0  
   720x480        60.0  
   640x480        85.0     75.0     72.0     60.0    160.0    120.0    100.0     90.0  
   640x400        75.0     60.0  
   512x384        75.0     60.0  
   400x300        75.0     60.0  
   320x240        75.0     60.0  
   320x200        75.0     60.0  
   1x1            60.0  
   0x0             0.0

---

### Post by tjwallis on 2008-03-28
I Solved the problem I have to change the resolution to 3600x1400 with the Screen Resolution tool.

---


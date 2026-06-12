---
title: "ati dual display big desktop not working properly"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by antifix on 2006-06-03
I just completed a fresh kubuntu dapper install and used adept to get the ubuntu fglrx package and control panel.  I used aticonfig --initial=dual-head --dtop=horizontal --overlay-on=0 to configure the fglrx driver.  The driver is installed and confirmed via fglrxinfo.

Problem I'm having is the secondary display is unusable in "big desktop" mode.  I can get my mouse to the left most edge if I try to traverse the two displays, and it stops.  For some reason even though the display looks functional, and has a drawn background similar to that when you're in kdm, it's unusable after the KDE session starts.  Similarly, if I try to configure it in single mode, the other screen just has garbage on it rather than staying black.  In clone mode, it works fine (but who wants to use that!)

Any hints?  I have a Radeon 9600 Pro and I'm using Dapper LTS 

Yea, I know, but I like KDE. :mrgreen:

---

### Post by twstokes on 2006-06-03
I've got the exact same problem. When I am at the KDM login screen, I can move the mouse over to the second monitor, but as soon as I log in the mouse can only go to the very edge of the second monitor and no more.

I ran the setup for the card a second time and managed to get the second screen to work, but it actually loads another session instead of just expanding my desktop.

In Breezy, it was no problem at all getting this going, but now that I'm using Dapper it's acting completely different. I even copied the working xorg.conf from my Breezy install and it didn't work, so something's telling me it might not be related to Xorg but more to KDE somehow.

I have an ATI x300.

Any help would be great.

---

### Post by bouvittel on 2006-06-04
Hi

same problem here using ATI x600 card and fglrx driver.
In dual-head mode it starts two sessions and I can not change open applicatioin
to other Monitor. In dual-head "Big Desktop" mode I have also the same problem
like antifix. Till now i have not found a solution.

---

### Post by aro_ron_chynn on 2006-06-04
I am having this problem too. I just installed Dapper the other day, and have ben fighting to get dual head working ever since. I have basic dual-head working now, but not big desktop mode, I have a copy of X running on each monitor, and cant move things between them. 

Yet big desktop mode borks my graphics completly. Like others have said, mouse will move to the second monitor, but only far enough in to see the mouse, then it stops. I also loose all my panels, so no menus, no way to start terminal, nothing.

Sometimes it just kills the monitors completly, nothing but distorted garbage I can't even read.

I have a Radeon 9800 Pro.

---

### Post by noof on 2006-06-04
I'm having the same problem. You can move the mouse pointer around on the other screen when you're in GDM, but after you log in it gets werid.

---

### Post by twstokes on 2006-06-05
I've managed to get dual screens - but no acceleration. Has anyone else had any luck? I keep reading more and more of people having the same problem, but have yet to see one solution. This is really holding me back from using Dapper.

---

### Post by noof on 2006-06-06
I've had acceleration.. for some time at least :) Had ~20 fps i wow (~30 in xp, so :P ) which I don't think was unaccelerated..

---

### Post by twstokes on 2006-06-06
I can get acceleration with one screen just fine but with two it's a no go. I'm not worried now though - I bit the bullet last night and an NVIDIA is on the way :D. I know that it will have its bugs too, but hopefully not the serious ones I've been having with my ATI (hard lockups when logging out of KDE, no dual screens, etc.).

I just bought a mediocre GeForce 6600, but it's better than my ATI x300 and has more compatibiliy in Linux. Plus it was only around $100 bucks so I'll easily replace it later when I need more power.

---

### Post by soce_32 on 2006-06-06
I have big desktop working with an ATI x600 on EMT64, but I am not impressed.  It miscalculates the size of the two desktops, and any time I am in areas that the X server has created, but are not actually viewable, I get the cursor wrapping to the other side of the screen and all sorts of really annoying artifacts on my main screen.  Since some of this virtual space is below my bottom panel, every time I try to use applets down there, I get streaks all over my screen.  This happened with both ubuntu-packaged fglrx and the ATI binary drivers (they're the same version now anyway). 

Here is my xorg.conf incase anyone wants to try to get big desk working.  The key elements seem to be the Virtual setting and the Mode2 setting.  The rest of the stuff I have commented out doesn't seem to do anything.  Even though glxinfo reports that DRI is working, I can't actually run any 3D apps.


```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "DELL 2005FPW"
	Option	    "DPMS"
EndSection


Section "Device"
	Identifier  "ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal,reverse"
	Option	    "Mode2" "1920x1080"
#	Option	    "ForceMonitors" "lvds,crtl"
#	Option	    "VideoOverlay" "on"
#	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
	Monitor    "DELL 2005FPW"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Virtual   1920 1080
		Depth     24
		Modes    "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

---

### Post by antifix on 2006-06-06
This is very frustrating.  I believe it has something to do with Xorg 7.0 and the new ATI drivers.  It worked fine in Breezy as well as SuSE 10.1 which uses Xorg 6.9.  I doubt KDE 3.5 is the problem.  I agree with posters above, I am anxious to move to Dapper, but with this hinderance I won't be doing so anytime soon.

Really frustrating, but not enough to spend the loot on an Nvidia card. :mad:

---

### Post by wblancqu on 2006-06-07
Really Weird. It worked for me for like 2 days on Dapper. And suddenly I'm having the same problem... Can't get my mouse to the right screen, although it's working.

Weird..

---

### Post by Punterfpc on 2006-06-08
Hey fellas, here is your solution. (well, it works in Gnome, at least...). 

Once you have setup the dual monitor "big desktop" settings, you need to completely restart the computer. On the sign-on screen you will probably notice that you are able to move the mouse from one screen to the other without any problems. 

There is one thing you need to do once you login. Now, I'm not entirely adept at using the KDE enviroment, but I am sure that there is someplace where you can change the resolution of your monitors. What you need to do is change the resolution of the horizontal component to twice what it is already (assuming you are using two monitors of the same resolution).

So, for instance, I have 2 17" CRT monitors; my primary is on the left and my secondary is on the right. The resolution they are native to is 1280x1024, so in clone mode they are both running at that resolution. So, twice the resolution should now be 2560x1024, right? So, change your resolution using the respective KDE tool (or, I guess you could edit the xorg file... but, that would be more difficult, probably...). In gnome all you have to is go to:

System > Preferences > Screen Resolution

After you're done, you may have to restart the computer again (restarting X, just doesn't work sometimes when you make these kinda changes...).

Good luck to all. (By the way, I have a Radeon 9600 XT All-in-Wonder, and, yes, I do believe I have lost some 3D-acceleration capabililty.)

---

### Post by Kazade on 2006-06-09
I'm having the same problem, I can set individual resolutions for both monitors in system settings but it doesn't allow me to set a double width resolution (thats how I had it set in Breezy) anyone else have any ideas?

Luke.

---

### Post by Kazade on 2006-06-10
I fixed it :)

In a terminal type:

```
sudo xrandr -q
```

This should bring up a list of possible video modes (my last one had a double width) then when you have the ID number of the resolution type:

```
sudo xrandr -s 10
```

Where '10' is the ID number of the resolution you want. 

Luke.

---

### Post by kevnician on 2006-06-10
I started with not being able move my mouse to the right hand screen, then I had a corrupted display, and finally I ended with two functioning monitors after much ](*,) .  Now I have never tried dual head on linux before so I'm confused. In KDE it is like I have two desktops I can move the mouse between them but each runs there own set up programs (which don't move) and has their own menu's etc, is this normal.... I've only used windows dual-head before.  I added my config in case it helps anyone.]



```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

  # path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "extmod"
	Load  "freetype"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "glx"
	Load  "GLcore"
	Load  "v4l"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"# Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"# Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"# Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "monitor0"
	VendorName   "Mitsubishi"
	ModelName    "Mitsubishi Diamond Pro 900u (NFJ9905)"
	HorizSync    30.0 - 95.0
	VertRefresh  50.0 - 152.0
	Gamma        1
	ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	ModeLine     "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
	ModeLine     "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
	ModeLine     "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	ModeLine     "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
	ModeLine     "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
	ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
	ModeLine     "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
	ModeLine     "1152x768@54" 65.0 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
	ModeLine     "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
	ModeLine     "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	ModeLine     "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
	ModeLine     "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
	ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
	ModeLine     "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	ModeLine     "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
	ModeLine     "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	ModeLine     "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
	ModeLine     "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
	ModeLine     "2048x1536@60" 266.9 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	VendorName   "Samsung"
	ModelName    "Samsung SyncMaster 753DF(X)/703DF(X)/783DF(X)/CD173A(T)"
	HorizSync    30.0 - 71.0
	VertRefresh  50.0 - 160.0
	Gamma        1
	ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	ModeLine     "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
	ModeLine     "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
	ModeLine     "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	ModeLine     "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
	ModeLine     "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
	ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
	ModeLine     "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
	ModeLine     "1152x768@54" 65.0 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
	ModeLine     "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
	ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	BusID       "PCI:3:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:3:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024@60" "1280x960@75" "1280x1024@85" "1400x1050@60" "1280x960@85" "1400x1050@75" "1280x960@60" "1600x1200@65" "1280x1024@75" "1600x1200@60" "1280x854" "1600x1200@75" "1152x768@54" "1600x1200@70" "1152x864@75" "1792x1344@60" "1024x768@43" "1856x1392@60" "1024x768@60" "1920x1440@60" "1024x768@70" "2048x1536@60" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

---

### Post by httpnetworks.com on 2006-06-23
I think it's to do with the dpi,

Try what I have suggested [here]("http://www.ubuntuforums.org/showthread.php?t=66595").

---

### Post by antifix on 2006-07-04
Luke,

Thanks a million!  This solution worked like a charm!   Now I can use Dapper and get rid of SuSE!  Universe multiverse here I come!

Thanks again,

Ryan \\:D/

---

### Post by struess on 2006-07-10
luke, you're the man now dog.  thanks for the fix, that's been bugging me.

---

### Post by herr-k on 2006-07-16
Hi,
I've heard this fglrx stuff has always been a pita but I'd like to revive this topic.
I'm also running Dapper with Kde on a radeon 9200SE and got the same problem. Unfortunately httpnetworks' solution won't work for me :( Hence I followed Kazade's suggestion and created this file:

> #! /bin/sh
xrandr -s 10	# please mention there's no sudo necessary

And put it in ~/.kde/Autostart/

But I'm unable to create any objects (folders or application link ...) on second screen and would really appreciate any kind of “proper” or “final” solution.

And I still have a question for the experts: Would my anger really reduced by purchasing a nvidia card? Because this is not the first time I run into problems with this card but I really wished it was the last time ;)

---

### Post by Adcadet on 2006-07-20
I managed to get my ATi dual display working, although I need to use the above mentioned xrandr -s 10 trick to reset the resolution every time I log on to KDE.  Thanks to everyone for the help.  

The problem I'm having is that I the display resolutions listed by xrandr -q only includes a single "dual display" resolution - 3200x1200.  I would love to run at 2560x1024 (1280x1024 x2), and I put in this resolution into xorg.conf under Section "Screen" under the listings for the depths 4, 15, 16, and 24.  Interestingly, there is no 3200x1200 listed anywhere in xorg.conf, so I have no idea where the xrandr -q command is pulling the resolutions from.  Is there another file I need to edit somewhere?  Any help would be much appreciated.  I'm using an ATi X800 with the fglrx driver.

---

### Post by djgenesis on 2006-07-22
Hello all, 
can anyone post a complete solution or a mini howto also adding his working xorg.conf and then the commands?

---

### Post by MrNiceguy on 2006-07-24
> **Adcadet said:**
> The problem I'm having is that I the display resolutions listed by xrandr -q only includes a single "dual display" resolution - 3200x1200.  I would love to run at 2560x1024 (1280x1024 x2), and I put in this resolution into xorg.conf under Section "Screen" under the listings for the depths 4, 15, 16, and 24.  Interestingly, there is no 3200x1200 listed anywhere in xorg.conf, so I have no idea where the xrandr -q command is pulling the resolutions from.  Is there another file I need to edit somewhere?  Any help would be much appreciated.  I'm using an ATi X800 with the fglrx driver.

I'm wondering this too, as I'm having a simila problem.  My only "Dual Display" resolution. is 2560x1024, which I would love except my second monitor, (an older LCD) only supports up to 1024x768.  I would love to set my resolution to 2048x768, but the option isn't listed.  How can I add it to the list of available resolutions?

---

### Post by jrjr on 2006-07-24
When I finally got my big desktop working the resolution was set to 2048x768. I did not choose this anywhere, it did it all by itself. I have an older LCD too with max res @ 1024x768 and that is what I chose when I went through X config. So... it did it automatically for me. Why you ask? Dunno I reply!

---

### Post by djgenesis on 2006-07-24
> **Punterfpc said:**
> Hey fellas, here is your solution. (well, it works in Gnome, at least...). 

Once you have setup the dual monitor "big desktop" settings, you need to completely restart the computer. On the sign-on screen you will probably notice that you are able to move the mouse from one screen to the other without any problems. 

There is one thing you need to do once you login. Now, I'm not entirely adept at using the KDE enviroment, but I am sure that there is someplace where you can change the resolution of your monitors. What you need to do is change the resolution of the horizontal component to twice what it is already (assuming you are using two monitors of the same resolution).

So, for instance, I have 2 17" CRT monitors; my primary is on the left and my secondary is on the right. The resolution they are native to is 1280x1024, so in clone mode they are both running at that resolution. So, twice the resolution should now be 2560x1024, right? So, change your resolution using the respective KDE tool (or, I guess you could edit the xorg file... but, that would be more difficult, probably...). In gnome all you have to is go to:

System > Preferences > Screen Resolution

After you're done, you may have to restart the computer again (restarting X, just doesn't work sometimes when you make these kinda changes...).





Thanks man ! That worked for me!

Only one thing... The refresh rate is 60Hz and it is hurting my eyes..

Adcadet is right.. Where is xrandr pulling the settings from ?

---

### Post by antifix on 2006-07-24
I agree.  While the fix works, there's something more to this and there has to be a viable permanent solution somewhere.

Anyone?

---

### Post by jrjr on 2006-07-25
I dont have the answer but -
I didnt have to change my xorg.conf. Double the resolution of one monitor is not listed in my file either and my big desktop still works. There has to be other places where this is configured too.

At the log in screen I can scroll the mouse from one to the other but the wallpaper is only shown on one screen. The other one is just brown.

---

### Post by jrjr on 2006-07-25
I think I found the cure... switch distros.

---

### Post by MrNiceguy on 2006-07-26
> **jrjr said:**
> I think I found the cure... switch distros.

Not really a helpful suggestion.  I think before I try blowing away my existing setup and start with a new distro, I'll just switch my old LCD with an old CRT and run 2560x1024.  I just may may do that even if we can solve the question of where xrandr gets the list of available resolutions.  I know I'll have to use the same refresh rate for both monitors, and while 60Hz works well on the LCD, staring at a 60Hz CRT for long will have me ready to jab pencils into my eyes.

Even so, I'd still like to know how to configure available resolutions for xrandr.

---

### Post by djgenesis on 2006-07-27
True you guys. 
I found this at the man page of xrandr.

> 
Table of Contents

Name
xrandr - primitive command line interface to RandR extension
Synopsis
xrandr [-help] [-display display] [-o orientation] [-q] [-v] [-s size] [-x] [-y] [--screen snum] [--verbose]
Description
Xrandr is used to set the screen size, orientation and/or reflection. The -s option is a small integer index used to specify which size the screen should be set to. To find out what sizes are available, use the -q option, which reports the sizes available, the current rotation, and the possible rotations and reflections. The default size is the first size specified in the list. The -o option is used to specify the orientation of the screen, and can be one of "normal inverted left right 0 1 2 3".

The -x option instructs the server to reflect the screen on the X axis. The -y option instructs the server to reflect the screen on the Y axis. Reflection is applied after rotation.

The -help option prints out a usage summary. The --verbose option tells you what xrandr is doing, selects for events, and tells you when events are received to enable debugging.
See Also
Xrandr(3)
Authors
Keith Packard, XFree86 Core Team and Cambridge Research Laboratory, HP Labs, HP. and Jim Gettys, Cambridge Research Laboratory, HP Labs, HP.


Should we try to mirror and flip at the resolution we want?

---

### Post by rockyjvec on 2006-07-29
I was having that same problem also, using AIW X800 xt 256mb.  I think I fixed it with various info from this forum (thanks).  It was only giving me the 4096x1536 dual screen mode in the Screen Resolution changer in gnome, so this is what I did:

1.  I removed the "Viewport    0 0" from both screens in the xorg.conf file, then I added all the modes I wanted including "2560x1024".  

2.  I restarted the x server

3.  I  used "xrandr -s 2560x1024" to change to the new mode (2560x1024) that I added.  It still didnt show up in the Screen Resolution changer and would revert back to the unusable mode when I rebooted/logged off.  So...

4.  I fired up the Configuration Editor (gconf-editor), went to desktop/gnome/screen/default/0 and 1 and changed the value of resolution to 2560x1024 for both of them.  

Now my preferred resolution of 2560x1024 shows up in the Screen Resolution changer and also stays when I restart the x server.

Hope that helps

Here is my xorg.conf file:
> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 151.0
	VertRefresh  43.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "2560x1024" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection

EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "2560x1024" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection



I just installed the Quake 3 Arena demo to test hardware acceleration, and it work great on both monitors.  Thanks for all the info.

---

### Post by cantormath on 2006-07-30
alright, this is what I did to get dual head with a 
RS300M AGP [Radeon Mobility 9100IGP] card.

HOWTO S-video out and with LCD on toshiba A70

This is gonna set up two independent desktops outputing at the same time.
This is just what I did in the order I did it.

synaptic
search: 
radeon
install: 
fglrx-control
radeontool
xorg-driver-fglrx
xserver-xorg-driver-ati (this was already installed.)

reboot

note: atitvout is install

run in terminal
sudo  aticonfig --initial=dual-head --screen-layout=above

reboot

now, when I have my s-video cable plugged into my tv Im able to have two desktops both of which can show and play video without a problem.  I havent a second monitor, but If I were to plug that in and unplug the s-video, it should have the same effect. All I have to do to get to the second display is drag the mouse up.  NOTE: the desktops are independent, so I cannot drag one app to the other display; however, there is a toolbar and menus in the other display so I can start any app.  I didnt want to stretch the desktop.

---


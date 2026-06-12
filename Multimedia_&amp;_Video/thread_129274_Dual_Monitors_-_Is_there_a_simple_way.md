---
title: "Dual Monitors - Is there a simple way?"
date: 2006-02-13
forum: Multimedia &amp; Video
---

### Post by Blind-Summit on 2006-02-13
I have been reading many posts about setting up dual monitor support. For anyone with a problem setting this up - I can feel your pain! I have used so many different versions of my xorg.conf file now that it's becoming second nature to sudo nano /etc/X11/xorg.conf now

I have the following setup - AGP slot NVidia GeForce 4 Ti4600 with an AOC Spctrum 17" at 1280x1024 and an Iiyama VisionMaster 500 21" at 1600x1200 (these resolutions are what i use under windows) Currently, I have just the 17" running at 1280x1024

Now, as I understand there are 3 areas to modify

1 - Section Devide
2 - Section Monitor
3 - Section Screen

The device describes the hardware and port address, the mmonitor describes the actual scree, and the screen describes the refresh rates / resolution etc.

Allow me to post my current config file

```

Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"AOC Spectrum"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Monitor		"AOC Spectrum"
	DefaultDepth	24

... removed the display modes to save space

EndSection

```

This works fine.

The next step is to decide on the type of dual monitor setup. I assume that most people would want the TwinView setup? Perhaps a bold choice, but does anyone have 2 screens displaying identical desktops?

I had a browse and found 2 posts that proved useful, until I tried the code out.

This code was found here: [http://ubuntuforums.org/archive/index.php/t-91045.html](http://ubuntuforums.org/archive/index.php/t-91045.html) - the code is a couple of posts from the bottom

```

Section "Device"
Identifier "Intel"
Driver "i810"
BusID "PCI:0:2:0"
EndSection


Section "Device"
Identifier "Geforce2 MX/MX400"
Driver "nv"
BusID "PCI:1:7:0"
EndSection

Section "Monitor"
Identifier "Monitor 1"
Option "DPMS"
HorizSync 30-65
VertRefresh 50-75
EndSection

Section "Monitor"
Identifier "Monitor 2"
Option "DPMS"
HorizSync 30-65
VertRefresh 50-75
EndSection

Section "Screen"
Identifier "Left"
Device "Geforce2 MX/MX400"
Monitor "Monitor 1"
DefaultDepth 24
SubSection "Display"
Depth 16
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier "right"
Device "Intel"
Monitor "Monitor 2"
DefaultDepth 24
SubSection "Display"
Depth 16
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

```

I replaced their settings with mine ie PCI bus and GeForce names but no luch. With some tweaking I got it to work with X Desktop, but only 1 screen. Basically, the config file was ok, but no dual screen.

I think I may need to setup my server layout options, but i will post back here with results.

Another semi-useful topic is here [http://ubuntuforums.org/archive/index.php/t-86394.html](http://ubuntuforums.org/archive/index.php/t-86394.html)

If anyone has a geforce setup with dual view, it would be nice to have some help here please. 

Alex

---

### Post by sfink01 on 2006-02-15
Check out the HowTo at:

[http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html)

Then if you have any questions post back to this thread for help:

[http://ubuntuforums.org/showthread.php?t=85769&goto=newpost](http://ubuntuforums.org/showthread.php?t=85769&goto=newpost)

Best,

Steve

---


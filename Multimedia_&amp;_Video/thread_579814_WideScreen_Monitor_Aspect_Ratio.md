---
title: "WideScreen Monitor Aspect Ratio"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by giutax on 2007-10-18
Hello all, I just Installed Gutsy Gibbon Today and I am having one small issue with my monitor. I do get the 1440x900 resolution I need but the the aspect ration? Not sure if that is the correct term is off. When in the 1440x900 resolution the screen shrinks and does not fill the whole monitor(I get about a 3" black line down the right side). At the  1280x1024 it does fill the whole screen. My goal here is to fill the whole screen using the 1440x900 resolution. My computer model is Lenovo 8807-97U and Monitor is Lenovo 19" widescreen. Here is a sample from my xorg.conf file: Thanks for any help.

Section "Device"
	Identifier	"Intel Corporation 82Q963/Q965 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82Q963/Q965 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x1440" "1440x900" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "544x32" "0x0"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection



Section "Extensions"
	Option "Composite" "Disable"
EndSection

---

### Post by giutax on 2007-10-18
I also ran this command sudo dpkg-reconfigure xserver-xorg and it does detect the right video card and the right monitor..........So now I really have no idea why I get a 2" black band down the right side....I figured it did not detect the wide screen monitor....

---

### Post by giutax on 2007-10-18
Ok sorry for all the post without a reply but i keep getting so close. After running sudo dpkg-reconfigure xserver-xorg  I now get another refresh rate of 75Hz(before only got 60hz)  and when I use 1440x900 at 75Hz I do indeed get a full screen  with the correct resolution. But I have encountered another issue. There is kinda like wavy lines going through the screen. I am able to see the screen but it is unusable. I'm thinking it is the refresh rate......Any one have any idea's?Thanks

---

### Post by ebullient on 2007-10-26
Try different drivers and see what you get.  Under the device section change 'Driver "intel"' to either "i810" or "vesa".  If you mess up your screen, never fear.  Just hit ctrl-alt-f4 or lower number and it will give you a terminal so you can restore your xorg.conf.

Be sure to back up your xorg.conf before you make any changes!

---


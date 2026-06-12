---
title: "Nvidia TV-Out Laggy - Ubuntu 7.10"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by roggo on 2007-10-31
Hello all!

I have managed to configure nvidia drivers and TV-Out on my new Ubuntu 7.10 OS. The only problem is that when I enable the TV my system response gets laggy. What I mean is ie. when I click on the menus like Applications or System it takes a second to respond. Adn then when I disable my TV everything runs sweet.

Here is the corresponding segment from xorg.conf (removing # to enable TV):
```
Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	screen 		0
EndSection

#Section "Device" 
#	Driver          "nvidia" 
#	Identifier      "Device[1]" 
#	Screen 1 
#	Option          "TVOutFormat" "SVIDEO"
#	Option          "TVStandard" "PAL-G"
#	Option          "ConnectedMonitor" "Monitor[1]" 
#	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
#EndSection

Section "Monitor"
	Identifier 	"Monitor[0]"
	Option		"DPMS"
	HorizSync 	30.0 - 75.0
	VertRefresh 	50.0 - 75.0
EndSection

#Section "Monitor" 
#	Identifier 	"Monitor[1]"
#	HorizSync 	30-50
#	VertRefresh 	50 
#EndSection

Section "Screen"
	Identifier  "Screen[0]" 
   	Device      "Device[0]" 
   	Monitor     "Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"
	EndSubSection
EndSection

#Section "Screen" 
#	Device "Device[1]" 
#	Identifier "Screen[1]" 
#	Monitor "Monitor[1]" 
#	DefaultDepth 24 
#	SubSection "Display" 
#		Depth 24 
#		Modes "1024x768_50" 
#	EndSubSection    
#EndSection

Section "ServerLayout" 
	Identifier  "Simple Layout" 
		Screen 0 "Screen[0]" 
#		Screen 1 "Screen[1]" RightOf "Screen[0]" 
	InputDevice "Configured Mouse" "CorePointer" 
	InputDevice "Generic Keyboard" "CoreKeyboard" 
EndSection
```

I have a quite good computer setup: 4gb ram, 7950GT gfx card and so on...

Please help! :(

---


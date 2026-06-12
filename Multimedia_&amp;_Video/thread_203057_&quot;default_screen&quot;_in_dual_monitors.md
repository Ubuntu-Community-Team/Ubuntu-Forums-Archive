---
title: "&quot;default screen&quot; in dual monitors?"
date: 2006-06-24
forum: Multimedia &amp; Video
---

### Post by Genix5 on 2006-06-24
I have an Nvidia 6800GT with dual monitors. I have a 15" on the VGA port, and a 19" on the DVI port. I couldn't get twinview to work, so I used the alternative setup on Nvidia's site. Everything works good, except for the fact that Ubuntu is defaulting stuff to my smaller 15" screen. The log on window is using that screen. When I insert media, such as a removable USB drive, the icon shows up on the smaller desktop by default. Is there anyway to make my other 19" on the DVI port the default screen for things to show up?

Another small related question: If I do get twinview setup properly, would it be possible to run two different resolutions on each monitor? 

Here's Nvidia's page that I followed: [link]("http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=176&p_created=1101836843&p_sid=PU1Z9Tai&p_lva=174&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NSZwX3Byb2RzPTImcF9jYXRzPTU4JnBfcHY9MS4yOzIudTAmcF9jdj0xLjU4OzIudTAmcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9mbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD10d2ludmlldw**&p_li=&p_topview=1")

Here's part of my xorg.conf:
```
Section "Device"
	Identifier	"nvidia0"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"nvidia1"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"monitor0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"nvidia0"
	Monitor		"monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"nvidia1"
	Monitor		"monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Screen0"
	Screen		1 "Screen1" RightOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection
```

Thanks for any suggestions. :)

---


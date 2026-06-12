---
title: "Dual monitor."
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by MacPC on 2007-04-18
Hi,

I asked this question a few months ago but still havn't found the solution. 

My PC has dual monitor. I have a 17" LCD connected the onboard video and a 22" wide screen connected to a nVidia MX400 video.

The computer is also dual boot with Windows 2000 pro and Ubuntu 6.06 Dapper. I have configured Ubuntu to use both monitors, but it won't let me  drag an application window from one monitor the the other. It would be really nice when I use Gimp, I can have all tool windows on the small monitor while take advange of the the wide screen to do my work. I can do it in Windows but not in Ubuntu. Can someone help me?

MacPC.

---

### Post by spin2cool on 2007-04-18
I think you'll need to post more details.  What kind of video card?  What does your xorg.conf look like?

---

### Post by MacPC on 2007-04-18
Hi,

Thanks for the reply.  My video card is an old nvidia Mad Dog MX400 card., I use the nVidia-glx-legacy driver. The onbord video is Intel 82845 G/GL [Brookdale-G] /GE Chipset integrated graphic device.
 My xorg.conf looks like this, I only posted the section regarding display:

Section "Device"
	Identifier	"Intel"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Device"
	Identifier	"nvidia MX400"
	Driver		"nvidia"
	BusID		"PCI:2:11:0"
EndSection

Section "Monitor"
	Identifier	"GEM GM17SL"
	Option		"DPMS"
	HorizSync	50-70
	VertRefresh	60-80
EndSection

Section "Monitor"
	Identifier	"ACER AL2216W"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Square Screen"
	Device		"Intel"
	Monitor		"GEM GM17SL"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Wide Screen"
	Device		"nvidia MX400"
	Monitor		"ACER AL2216W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Wide Screen"
	Screen		"Square Screen" LeftOf "Wide Screen"
	Option		"TwinView" "True"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

As you can see, in the ServerLayout section, the option is set to TwinView, I tried to use Xinerama but X won't work. I am not even sure if Xinerama will work on two different video source.

MacPC

---

### Post by spin2cool on 2007-04-18
I don't know the answer to this one.  Search these forums and the internet - I'm willing to bet that someone has to have experienced this problem before.  Open up your search to more than just your specific video card model.  It may be a general issue with using two video cards, etc.

---

### Post by MacPC on 2007-04-18
Hi spin2cool ,

Thanks for trying to help.

I got it working! :) I just noticed that in the xorg.conf file, I mistakenly set the Intel monitor depth to 16 instead of 24, that was why when I used Xinerama option, X won't start. Once I made the change, it works like a champ.

MacPC.

---


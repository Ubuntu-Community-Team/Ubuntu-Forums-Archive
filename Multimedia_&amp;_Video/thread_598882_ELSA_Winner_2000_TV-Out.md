---
title: "ELSA Winner 2000 TV-Out"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by olF23 on 2007-10-31
Hello everybody,

I just installed Ubuntu 7.10 on my older machine (PIII with 866MHz and 320 MB RAM) and was amazed at how perfectly almost everything worked out of the box (didn't visit Linux for a long time ;) ).
So I could start trying to make the TV-Out work earlier than I thought.

My graphics card is a ELSA Winner 2000/Office 4, which works perfectly with the "glint"-driver - at least the VGA-Output.
Unfortunately I didn't manage to get the TV-Out (S-Video) work :(

This is what I got so far [xorg.conf]:
```
###########################TFT######################
Section "Device"
	Identifier	"ELSA"
	Driver		"glint"
	BusID		"PCI:2:2:0"
EndSection

Section "Monitor"
	Identifier	"TFTk"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"ELSA"
	Monitor		"TFTk"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1024x768" "640x480"
	EndSubSection
EndSection

###################TV################################
Section "Device"
	Identifier	"ELSA-1"
	Driver		"glint"
	BusID		"PCI:2:2:0"
EndSection

Section "Monitor"
	Identifier	"TV"
	HorizSync	50
	VertRefresh	30-150
EndSection

Section "Screen"
	Identifier	"Screen2"
	Device		"ELSA-1"
	Monitor		"TV"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"640x480"
	EndSubSection
EndSection

####################################################
Section "ServerLayout"
	Identifier	"DefaultLayout"
	Screen		"Screen1"
	Screen		"Screen2"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```

I begin to fear that there is no way to get it work, since I tried the whole day and didn't come any further, so you are my last hope :(

Thanks in advance,
olF23

---


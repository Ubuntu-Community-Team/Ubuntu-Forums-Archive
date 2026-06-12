---
title: "can't get 1024x768 on 27&quot; lcd with DVI"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by twidget on 2007-05-29
Hi
I've been trying to get my 27" viewsonic N2750w to get 1024x768 but even if i go into xorg.conf and wipe everything except "1024x768" when i restart my xserver the highest resolution i can get is "832x624". i would suspect my video card except that i had this setup working at 1280x1024 using a different motherboard and slower cpu.also if i install a dvi to vga adapter and plug it into my old 15" lcd it'll do 1024x768 75Hz without any problem at all. this leads me to think that theres something about the DVI interface thats throwing my setup off.Here is my xorg.conf in case anyone can see something that i don't.

```
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"N2750w"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"N2750w"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" 
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

If someone can send me a good link about xserver configuration that would be helpful too.

---

### Post by twidget on 2007-05-29
its definately a DVI thing. using my DVI to VGA adapter imediately gets me the higher resolutions

---

### Post by reclusivemonkey on 2007-05-29
Have you installed NVIDIA's Linux drivers? You're still using the open source default "nv" driver. I suspect that's the problem.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#how_to_setup_nvidia_drivers_in_7.04](http://ubuntuguide.org/wiki/Ubuntu:Feisty#how_to_setup_nvidia_drivers_in_7.04)

---

### Post by twidget on 2007-05-30
actualy somebody gave me a radeon 9700 all in wonder yesterday and i just finished the driver install. everything works now except that kaffeine acts screwy whenever i check the "keep original aspect" checkbox no matter what resolution i'm at. its been this way since i switched motherboards,  on my old computer  it worked fine with the mx 440 :confused:.

---


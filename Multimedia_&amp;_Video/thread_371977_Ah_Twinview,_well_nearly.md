---
title: "Ah Twinview, well nearly"
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by addisor on 2007-02-27
Having a bit of twinview trouble, 

With   Option "UseDisplayDevice" "DFP, CRT" I get my LCD monitor via vga (want this as primary) and no projector.
With   Option "UseDisplayDevice" "CRT, DFP" I get HD Projector via dvi/hdmi (for films) and no LCD. Both there for grub and boot 


Here's some X11 if it help
Section "Monitor"
    Identifier     "Yamaha DPX-830"
    HorizSync       31.5 - 45.0
    VertRefresh     50.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce 6150"
    Driver         "nvidia"
    Option "UseDisplayDevice" "DFP, CRT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce 6150"
    Monitor        "Yamaha DPX-830"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "UseEdidFreqs" "True"
    Option         "MetaModes" "1024x768, 1024x768"
    SubSection     "Display"
        Depth       1
        Modes      "1280x720" "1200x800" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x768" "1200x800" "1024x768"
    EndSubSection

---

### Post by mojoman on 2007-03-15
This might be a bit late but are you sure you need to use "UseDisplayDevice" option at all? Here's the relevant section of my xorg.conf. I got a projector as well. 

```
Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:7:0:0"
	Option "TwinView" "True"
	Option "TwinViewOrientation" "RightOf"
	Option "MetaModes" "1024x768,1280x720"
EndSection

Section "Monitor"	#this section is from original xorg
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"	#this section is from projector xorg
	Identifier	"Projector"
	Option		"DPMS"
EndSection

Section "Screen"	#this section is from original xorg
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600"
    EndSubSection
EndSection

Section "Screen"	#this section is from projector xorg
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Projector"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x720" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x720" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x720" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x720" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x720" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x720" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection
```

/Mojoman

---

### Post by addisor on 2007-03-16
Thanks, here's my latest Xorg, as you can see much the same as yours.

Section "Monitor"
    Identifier     "LCD-15EX"
    HorizSync       31.5 - 60.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce 6150"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce 6150"
    Monitor        "LCD-15EX"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "UseEdidFreqs" "True"
    Option         "MetaModes" "1024x768, 1280x720; 1024x768, NULL; NULL, 1280x720"
  
I can get meta mode 1024x768;1280x720 to work woth films dragged to the projector, and i can get 1024x768,NULL to work. When i use NULL,1280x720 the projector works alone except films wont play, the syst just hangs with mplayer open, i have to hard reboot.  If its any help i can only swap meta modes using resolution change in syst/preferences.

---

### Post by mojoman on 2007-03-16
For what it's worth, I got my xorg.conf by autogenerating first one, with only my monitor hooked up. Then I autogenerated another, now with only the projector hooked up. I then "merged " these two, using the values auto-generated for each monitor. I then added the options the hard way, i.e. adding one option, restarting x. If X didn't brake down, I added another, restarting again, etc. Tedious as hell but when X couldn't start I knew what option caused it. Also, I ended upp with a lot fewer options enabled then what I've seen in the howto's and manual, but, hey, I can watch my movies now, right? It might be worth a try.

/Mojoman

---


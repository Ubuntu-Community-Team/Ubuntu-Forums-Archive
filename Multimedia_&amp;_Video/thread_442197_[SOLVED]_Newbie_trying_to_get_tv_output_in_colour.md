---
title: "[SOLVED] Newbie trying to get tv output in colour"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by forestpixie on 2007-05-13
Hi I have had a thread in the beginners forum in which I have had a few problems with getting tv output setup -

[http://ubuntuforums.org/showthread.php?t=435772](http://ubuntuforums.org/showthread.php?t=435772)

I searched further and got this result from this forum 

[http://ubuntuforums.org/showthread.php?t=432958&highlight=nvidia+black+white](http://ubuntuforums.org/showthread.php?t=432958&highlight=nvidia+black+white)

Am I right in assuming that I need to edit my xorg.conf to have options giving TVOUT FORMAT and TVSTANDARD for my setup 

I know that I'm using SVIDEO and fairly sure that it's PAL-I

but I could do with some help in the correct editing needed to add the lines to my xorg.conf, quite confident about backing up and restoring the file having had to do it twice on the road

---

### Post by WakkiTabakki on 2007-05-13
This is how my Device-section, looks (Nvidia 7300Go)
```
	
        Identifier     "NVIDIA Corporation NVIDIA Default Card"
    	Driver         "nvidia"
	Option		"AddARGBGLXVisuals"	"True"	
	Option		"AllowGLXWithComposite"	"True"
	Option		"TripleBuffer"		"True"
	Option   		"RenderAccel"   "true"
	Option   "BackingStore"   "true"

### Twinview config
	Option		"ConnectedMonitor"	"dfp, tv"
	Option		"TwinViewOrientation"	"DFP-0 LeftOf TV-0"
	Option		"TwinView"		"1"
	Option		"NoPowerConnectorCheck"	"true"
	Option 		"Metamodes" 		"DFP-0: 1280x800, TV-0: 640x480"

	Option 		"VertRefresh" "TV-0: 50"		#; DFP-0: 50"
	Option		"TVStandard"		"PAL-B"

```


Good luck
N

---

### Post by forestpixie on 2007-05-13
Mine hasn't got anything in it with 'Twinview config'

device section looks like this

```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 MX 440 with AGP8X"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 MX 440 with AGP8X"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1280x1024_75 +0+0; CRT: 1280x1024 +0+0; CRT: 1024x768 +0+0; CRT: 832x624 +0+0; CRT: 800x600 +0+0; CRT: 720x400 +0+0; CRT: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

question is how do i tell the conf that i need svideo and pal-i ?

can anyone help - a bit of hand holding wouldn't go amiss

---

### Post by forestpixie on 2007-05-13
Did it - added two lines to xorg.conf

for svideo and Pal - I , logged out restarted x and all was in colour

Thanks for your help

---


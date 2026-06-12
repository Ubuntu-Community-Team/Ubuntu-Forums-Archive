---
title: "Trying to get Fglrx to work..."
date: 2006-07-21
forum: Multimedia &amp; Video
---

### Post by BigJerm on 2006-07-21
Over the past couple of days, I have been trying to get linux to run with my Radeon 9200 SE. I have succesfully got my Radeon working with Ubuntu, with the help of a friend. I am currently using Vesa, seeing when I use Fglrx the screen brightness is incredibly overwhelming. I want to use the Fglrx drivers, seeing they are used in Direct Rendering, and the Vesa drivers operate slowly (Chopppy windows, ect..). Does anyone have any ideas? 

Here are my system specs:

2.93 Celeron D
1.25GB RAM
160GB HDD (80GB Linux Partition)
Radeon 9200 SE PCI

Here is my Xorg.conf file:

Section "Monitor"
	Identifier   "PH107C/F/H/T"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "Intel Corporation 82865G Integrated Graphics Controller"
	Driver      "i810"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "vesa"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:2:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Intel Corporation 82865G Integrated Graphics Controller"
	Monitor    "PH107C/F/H/T"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

I really love Ubuntu, and I want to use it to its full potential. I have tried the following code, to see how it runs. Its runs extremly slow. I don't know if that helps or not. 
```
glxgears
```

---

### Post by JerMe on 2006-07-21
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

I used method #2 for this box with a 9200se.  Afterward you follow that guide, you'll have to symlink a couple of files:

```
sudo ln -sf /usr/lib/fglrx/libGL.so.1.2 /usr/lib/libGL.so.1
sudo ln -sf /usr/lib/fglrx/libGL.so.1.2 /usr/lib/libGL.so.1.2
```

Hopefully I didn't forget anything.  Good luck

---

### Post by BigJerm on 2006-07-21
Thanks a lot for the info you have posted, it will help greatly. I am new to the Linux scene, so my knowledge is lacking. I really appreciate it.

---

### Post by Dubbayoo on 2006-07-22
If you want to use the fglrx drivers then you have to tell Xorg to use them. 

You have:
Section "Device"
Identifier "ATI Graphics Adapter 0"
Driver "vesa"
Option "(null)"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
BusID "PCI:1:2:0"
EndSection

so you're still telling the system to use vesa. That should be:
Driver      "fglrx"

---


---
title: "Resize resolution and HDMI audio for HTPC"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by bigbeatxl on 2007-10-22
I have an Abit F-190HD MB (integrated audio and video) connected to a Sony XBR1 HDTV via hdmi and could use some help with 2 problems.  This is on Fiesty.

1)  Video - I have the fglrx driver installed which properly presents me with resolutions the tv can handle.  However, 1920x1080 is too large and significant portions of the desktop on all sides are cut off (I guess the term is overscan).  So I drop down to the next resolution, 1776x1000, and it produces better results, but is still being cropped.  I was hoping I could scale and translate the image using the geometry option for aticonfig, but it has no effect.  What else could I try to properly size and center the image on the tv?  Obviously, the aim is to get every bit of a 1920x1080 picture in all its glory!

2) Audio - I originally had the hda-intel driver for sound, which worked properly except for the hdmi output.  So, I pulled the latest alsa drivers from the realtek site, which also worked....except for the hdmi output.  My scouring of the internet leads me to believe that I need to configure the driver with hda-codec-atihdmi, but I don't know how to do that and I may be off base.  Any suggestions on how to enable audio through the hdmi connection?

Please help me ditch Brighthouse!  As soon as this htpc is functioning, I'm kicking them to the curb.

---

### Post by nutz on 2007-12-30
I can help you with the video...

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1920x1080"
	Horizsync	31.5-67.0
	Vertrefresh	56.0 - 65.0
  modeline  "1920x1080@60" 172.80 1920 2040 2248 2576 1080 1081 1084 1118  -hsync +vsync
        Option  "DPMS"  "true"
        Option "UseEdidDpi" "FALSE"
        Option "DPI" "100 x 100"
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1080
		Modes		"1920x1080"
	EndSubSection
EndSection
```

That has worked so far on pretty much any 1080p tv it has been used with. Obviously you will need to adapt it to your system but you get the idea. If you post your xorg.conf I will have a go at cleaning it up for you. As long as the tv actually has a native resolution of 1920x1080 you should have no problem with a 1920x1080 desktop. The best way to accomplish this is with a DVI to HDMI cable so you can use a clean digital signal but the VGA connector that the tv has will also work. In the case of a CRT tv the VGA can actually be better depending on the model.

---

### Post by nutz on 2007-12-30
By the way I am also trying to get the audio over hdmi working. Mainboard is an Abit AN-M2HD with hdmi output...

---


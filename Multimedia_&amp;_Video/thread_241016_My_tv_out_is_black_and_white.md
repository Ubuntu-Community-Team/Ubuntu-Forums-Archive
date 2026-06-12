---
title: "My tv out is black and white"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by pasipasi on 2006-08-21
I'm trying to set up tv out for movies and such and I followed this guide [http://gentoo-wiki.com/HOWTO_Separate_x-screens_on_Monitor_and_TV](http://gentoo-wiki.com/HOWTO_Separate_x-screens_on_Monitor_and_TV)

Everything is now working except that I'm not getting any colours on my tv screen. I've tried everything in the past 4 hours and I'm getting desperate.

> Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
 #tv
	Identifier   "aticonfig-Monitor[1]"
	HorizSync    31.0 - 31.0
	HorizSync    5.0 - 35.0
	HorizSync    2.0 - 2.0
	VertRefresh  60.0 - 60.0
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "TVFormat" "PAL-G"
        Option      "TVStandard"    "SVIDEO"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Device[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "800x600"
	EndSubSection
EndSection


I do get colours with another conf file though and again I have no idea why. Here's the other conf file. With this file I do get a video picture too but the picture is cropped - I can only see half.

> Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option 	    "TVFormat" "PAL-G"
	Option 	    "TVStandard" "VIDEO"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


> pasi@samperi:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.5946 (8.27.10)



display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.5946 (8.27.10)



Any ideas?

---

### Post by mogelhead on 2006-08-22
When I had this black and white problem with my TV out, I had to change a setting in the TV. I had to tell the TV what type of input signal it was receiving: S-video. (It was a Philips 32" Widescreen TV. Only one of the three inputs could handle S-video.)

I noticed a difference between your two configuration files: 
the first one says 'Option "TVStandard" "SVIDEO"'
the second one 'Option "TVStandard" "VIDEO"'

Try one of the following:
1) Change the first configuration file from SVIDEO to VIDEO
2) Change the setting in the TV to S-video

For more information about S-video:
[http://en.wikipedia.org/wiki/S-Video](http://en.wikipedia.org/wiki/S-Video)

Edit: I checked the latest [nvidia driver readme file]("http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-h.html") and saw that only COMPOSITE and SVIDEO are valid. From the readme:

> The "TVOutFormat" option can be used to force S-video or composite output. Without this option the driver autodetects the output format. Unfortunately, it does not always do this correctly. The output format can be forced with the options:

    Option "TVOutFormat" "SVIDEO"

or

    Option "TVOutFormat" "COMPOSITE"

The "TVOverScan" option can be used to enable Overscan where supported. Valid values are decimal values in the range 1.0 (which means overscan as much as possible: make the image as large as possible) and 0.0 (which means disable overscanning: make the image as small as possible). Overscanning is disabled (0.0) by default.

Overscan is currently only available on GeForce4 or newer GPUs with either NVIDIA or Conexant TV encoders.


So I guess when you write 'Option "TVOutFormat" "VIDEO"' in your second configuration file, the option is ignored and the output format is autodetected.

---

### Post by nightmare03 on 2006-08-22
He is using an ati card :D

---

### Post by maubp on 2006-08-22
Is it an NTSC versus PAL issue?

---

### Post by pasipasi on 2006-08-22
I think the card is forcing ntsc output.

My tv is very old, I don't think I can change any settings in it. The tv out is working fine with Windows so I assume the problem is in this machine, not in the tv.

---

### Post by joris1977 on 2006-08-22
How are you connecting the s-video to the television? If you are using a scart adapter and it's an older television than that could be the problem. Don't worry, it´s easy to solve if you know a little bit about soldering. This link suplies a real nice tutorial: [http://camp0s.altervista.org/sVideo/sVideo.htm](http://camp0s.altervista.org/sVideo/sVideo.htm)

I heard you can also buy pre-solved scart cables on the web, but i have no experience with that. 

I was banging my head against the wall about this black and white tv out problem and accidently found this link, gave it a try and it worked! 8) 

hope it helps for you as well...

edit: sorry didn´t read your post well enough... i leave the comment might help someone else...

---

### Post by pasipasi on 2006-08-22
Nope, no scart adapter. It's a straight line from svideo out to svideo in.

Also, as stated before, the colours were working before, the image was just cropped so that I couldn't watch any movies. With there settings I can see the whole movie image but it's B&W. And it works fine under Windows.

---

### Post by pasipasi on 2006-08-22
Now I have colours plus a ok image on the tv. It's not perfect, because there are thick black borders all around the image (an inch or a few centimeters).

I did this:

> Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
        Option      "TVFormat" "PAL-G"
        Option      "TVStandard" "PAL-G"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "TVFormat" "PAL-G"
        Option      "TVStandard" "PAL-G"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLoverlay" "off"
        Option      "TVStandard" "PAL-G"                   Option      "TVFormat" "PAL-G"
        BusID       "PCI:1:0:1"
        Screen      1
EndSection


Haha.

---

### Post by mogelhead on 2006-08-22
> **nightmare03 said:**
> He is using an ati card :D

Oops, sorry!

Ignore the information below "Edit: I checked the latest nvidia driver readme file..."

---

### Post by pasipasi on 2006-08-22
Actually now the video is otherwise ok but it's running slow with little skips.. argh

NVM I fixed it. It would seem that every time I post something, I find a fix. Weird huh?

---


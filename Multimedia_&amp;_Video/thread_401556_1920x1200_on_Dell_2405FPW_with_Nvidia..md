---
title: "1920x1200 on Dell 2405FPW with Nvidia."
date: 2007-04-04
forum: Multimedia &amp; Video
---

### Post by MagicBottle on 2007-04-04
Hi...

I have this Dell 2405fpw monitor that is capable of running  1920x1200 (and did so long ago running an old version of Fedora).

My graphics card is an Nvidia Geforce FX with 256mb of Ram.

I've tried just about everything, but I can't get a resolution higher than 1600x1200.  I'm running kubuntu edgy eft.  

I'm using a dvi cable.  I've tried both the standard and proprietary drivers.  Nothing works.

What do you recommend?  How can I run this at 1920x1200?

---

### Post by tseliot on 2007-04-05
create a modeline by typing:
```
gtf 1900 1200 60
```

and you will get a modeline such as the following:
```
# 1904x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 191.96 MHz
  Modeline "1904x1200_60.00"  191.96  1904 2032 2240 2576  1200 1201 1204 1242  -HSync +Vsync
```

put this modeline in the Screen Section of your /etc/X11/xorg.conf and restart the Xserver

---

### Post by MagicBottle on 2007-04-11
Hmm...thanks for the advice.  Unfortunately, it doesn't work...

Here's what I assume is the relevant part of my Xorg.0.log:

(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.87.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     Dell 2405FPW (DFP-0)
(--) NVIDIA(0): Dell 2405FPW (DFP-0): 135.0 MHz maximum pixel clock
(--) NVIDIA(0): Dell 2405FPW (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1920x1200_60.00"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200

Here's the relevant part of my xorg.conf after your suggestion:

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
  # 1920x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 193.16 MHz
  Modeline "1920x1200_60.00"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200_60.00" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
   

What next?

You say to put the modeline in my screen section, but when I did that X wouldn't run, so I moved it to the monitor section.

Thanks for the help.

---

### Post by DannyW on 2007-04-11
Hi, I'm using a Dell 2407WFP but with an ATI Radeon X800.

The modes do go in the screen section. Here is the relevant part of my xorg.conf, if it helps.

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1920x1200"	"1680x1050"	"1600x1200"	"1440x900"	"1400x1050"	"1280x1024"	"1280x960"	"1280x854"	"1280x800"	"1280x768"	"1200x800"	"1152x864"	"1152x768"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection
```

Also, I suggest changing your HorizSync and VertRefresh values in the monitor section.

2405FPW:
Horizontal scan range 	30 kHz to 81 kHz (automatic)
Vertical scan range 	56 Hz to 76 Hz, exception 1680 x 1200 & 1920 x 1200 at 60 Hz only

From: [http://support.dell.com/support/edocs/monitors/2405fpw/en/about.htm#Specifioications](http://support.dell.com/support/edocs/monitors/2405fpw/en/about.htm#Specifioications)

So possibly:
```
Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "Unknown"
HorizSync 30.0 - 81.0
VertRefresh 60.0 - 60.0
Option "DPMS"
EndSection
```

Not sure if this will work for you, be sure to make a backup:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
To restore backup:
```
sudo mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by MagicBottle on 2007-04-11
Thanks for the advice!  I had the modes in the screen section, just the modeline in the monitor section.  

Your link to the dell page gave me a huge clue!

The Dell page says that at 1920x1200 @ 60 the modeline should have a horizontal frequency of 74 *which it does!* and a pixel clock of 154 --- *but gtf generates a pixel clock of 193.16*

I suspect this is the problem.   How do I get a modeline for 1920 x 1200 at 60 with 74 horizontal and 154 pixel clock?

Thanks!

(p.s. thanks for the advice on backing up my xorg.conf ---- I'm using bazaar on my /etc directory already.)  :)

---

### Post by MagicBottle on 2007-04-11
Okay, I got it working with a modeline I found on the web (not from gtf), and adding    Option         "ModeValidation" "NoMaxPClkCheck" to my device section.

Thanks for all the help!

Here are the relevant sections for anyone else with this problem:

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
  Modeline "1920x1200_60.00" 154.0  1920 1968 2000 2080  1200 1203 1209 1235 +Hsync -Vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "ModeValidation" "NoMaxPClkCheck"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200_60.00" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---


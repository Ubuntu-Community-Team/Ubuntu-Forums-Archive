---
title: "nVidia FX 5600 stuck resolution 800x600 @ 50hz"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by janimal on 2006-12-03
Hi all,
  long time windows developer, sick of windows. So this weekend I have installed Ubuntu.

   I followed some guides to install nvidia drivers and Beryl and everything works fine except for one teeny problem. 

   The only resolution available is 800x600 @ 50hz 
   My video card is an MSI nVidia FX 5600 256mb
   Monitor: Proview 786N.

 The monitor is a bit rubbish but under windows I can get 1168x whatever @ 75hz

 I have tried running nvidia config and specifying the resolution
 I have manually edited xorg.conf to ensure it has the video modes I would like to use
 I have tried reconfiguring Xserver (which didn't recognise the card and made things worse.

 I haven't been able to find exact specifications for the monitor, but nothing I put in there seems to be making a difference anyway. However I have guessed some conservative settings and tried a modeline.
 
 I have followed the fix resolution guide in the Ubuntu online docs
 
 Now I am fresh out of ideas, I have been searching the forums for three hours without success <sigh> 

 please don't make me install Vista (lol as if!!) 

I'd appreciate any ideas anyone has, although I am a total novice at this! 

Here's the relevant section of my xorg.conf

Section "Device"
	Identifier	"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-68
	VertRefresh	50-82
        Modeline "1024x768" 81.55  1024 1064 1168 1352   768  768  770  804
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
        Option "AddARGBGLXVisuals" "True"
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection


Ok I so I have found the Xorg log and this seems to be the part where it fails...

II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5600 at PCI:2:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 04.31.20.39.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5600 at PCI:2:0:0:
(--) NVIDIA(0):     @@@ (CRT-0)
(--) NVIDIA(0): @@@ (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 800 x 600
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.


Anyone know what this means? It looks to me like it is the monitor setup, but I am only guessing. Does anyone else have a Proview 786 N (17") 

thanks,

Janimal

---

### Post by exciliado on 2006-12-04
I got the same video card maybe this can help you:

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"LM-700"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"LM-700"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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



you can edit your xorg.conf with nano it's very easy. good luck

---

### Post by janimal on 2006-12-06
Hi ya,
 Unfortunately that doesn't really help me. Thanks for trying though.

 I am now pretty sure it is because of my monitor. I guess I'll know for sure when I get my new one <shrug>

 I'm still interested if anyone has specs for a Proview CRT 786N ( I mailed Proview but they haven't bothered to reply)

janimal

---

### Post by scatyb on 2006-12-06
try this, it worked for me:



10) If the driver ignores the modelines (and therefore the Resolution and 
Refresh Rate are not right) which (worked with version 8178) you have to add the 
following option to the Section "Device" in your xorg.conf: 
 
Code:  
Option "UseEDID" "False" 
 
 
Then get to the Section "Screen" and set you resolution and refresh rate in the 
following way: 
 
Put the desired Refresh rate beside the resolution you need to use. For example 
if you want to set the resolution to 1280x1024 and the refresh rate to 75hz you 
have to write 1280x1024_75 . See the example below: 
 
Section "Screen" 
    Identifier  	"Screen[0]" 
    Device      	"Device[0]" 
    Monitor     	"Monitor[0]" 
    DefaultDepth    24 
    SubSection     "Display" 
         Depth       15 
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" 
"640x480" 
    EndSubSection 
    SubSection     "Display" 
        Depth       16 
        Modes      "1280x1024_75" "1024x768" "832x624" "800x600" "720x400" 
"640x480" 
    EndSubSection 
    SubSection     "Display" 
        Depth       24 
        Modes      "1280x1024_75" "1024x768" "832x624" "800x600" "720x400" 
"640x480" 
    EndSubSection 
EndSection

---

### Post by OffHand on 2006-12-06
Did you happen to use the nvidia x server settings?

---

### Post by scatyb on 2006-12-06
no I didn't

---

### Post by saffsd on 2006-12-13
> **scatyb said:**
> 
Code:  
Option "UseEDID" "False" 


Thank you! That fixed it for me.

---

### Post by hikaricore on 2006-12-20
> **scatyb said:**
> try this, it worked for me:

10) If the driver ignores the modelines (and therefore the Resolution and 
Refresh Rate are not right) which (worked with version 8178) you have to add the 
following option to the Section "Device" in your xorg.conf: 
 
Code:  
Option "UseEDID" "False" 


I love you.

hehehe thanks

---


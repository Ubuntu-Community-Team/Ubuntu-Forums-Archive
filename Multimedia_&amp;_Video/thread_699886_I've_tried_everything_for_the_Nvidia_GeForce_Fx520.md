---
title: "I've tried everything for the Nvidia GeForce Fx5200"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by HHelsinger on 2008-02-17
All my attempts to load the Nvidia drivers fail.  The Screen always comes up blank.  Sometimes I get a drumroll, and sometimes Ubuntu loads -- I can tell because I can hear the start up sounds, but no screen!   I have looked at everything available:  here is my bibliography:

  Nvidia Read Me & Installation Guide 
[http://us.download.nvidia.com/XFree86/Linux-x86/169.09/README/index.html]("http://us.download.nvidia.com/XFree86/Linux-x86/169.09/README/index.html")

  Discussion about Modeline in xorg.conf 
[http://mail.opensolaris.org/pipermail/desktop-discuss/2007-July/010287.htm]("http://mail.opensolaris.org/pipermail/desktop-discuss/2007-July/010287.htm")

  Discussions on this Ubuntu Multimedia & Video forum 
[http://ubuntuforums.org/forumdisplay.php?f=138]("http://ubuntuforums.org/forumdisplay.php?f=138")
[http://ubuntuforums.org/showthread.php?t=490552&highlight=5200]("http://ubuntuforums.org/showthread.php?t=490552&highlight=5200")

  the Howto referred to at the top of  this forum 
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.htm]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.htm")

  Howto from Gentoo 
[http://gentoo-wiki.com/HOWTO_nVidia_Drivers]("http://gentoo-wiki.com/HOWTO_nVidia_Drivers") 

  Howto from the Ubuntu Gutsy on installing Nvidia 
[(http://www.funnestra.org/ubuntu/gutsy/#nvidia-driver)"][http://www.funnestra.org/ubuntu/gutsy/#nvidia-driver](http://www.funnestra.org/ubuntu/gutsy/#nvidia-driver)]("[http://www.funnestra.org/ubuntu/gutsy/#nvidia-driver)

The error message in /var/log/Xorg.0.log says
 > (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI 
(WW) NVIDIA(0):     from CRT-0's EDID. 
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default 


In the hope that someone can see where the problem is, I'm going to attach a whole lot of stuff from the log files, and the conf. file.   I'll take out some of the obviously irrelevant lines.  I"ve highlighted some lines possibly of interest -- Ubuntu says  my screen resolution is 1280x1024 at 60hz. 
Thanks in advance to anyone who finds something useful in this mess:


Here is the info on the Monitor, from the log file running the nv driver, when everything loads:
> (II) Loading sub module "i2c"

(II) LoadModule: "i2c"(II) Module already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: DEL  Model: 400d  Serial#: 1094796341
(II) NV(0): Year: 2005  Week: 41
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): Default color space is primary color space
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) NV(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
 ******
((II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
[COLOR="Red"](II) NV(0): Supported Future Video Modes:[/COLOR]
(II) NV(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[COLOR="Red"]
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897[/COLOR]
([COLOR="Blue"]II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) NV(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) NV(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[/COLOR]
(II) NV(0): Serial No: T61165A5AAD5
(II) NV(0): Monitor name: DELL 1905FP
(II) NV(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) NV(0): EDID (in hex):
************[hex code omitted]************
(--) NV(0): CRTC 1 is currently programmed for DFP
(II) NV(0): Using DFP on CRTC 1
(--) NV(0): Panel size is 1280 x 1024
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file

Here is what the log file reports when I try to load the nvidia drivers:
> 
--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0):     DELL 1905FP (DFP-0)
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(--) NVIDIA(0): DELL 1905FP (DFP-0): 135.0 MHz maximum pixel clock
(--) NVIDIA(0): DELL 1905FP (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024@75"
(II) NVIDIA(0):     "1280x960@60"
(II) NVIDIA(0):     "1152x864@75"
(II) NVIDIA(0):     "1280x1024@60"
*****************
(**) NVIDIA(0): Virtual screen size configured to be 1600 x 1200
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp


finally, here are the relevant parts of the xorg.conf file:
> Section "Device" 
	[INDENT]Identifier	"nVidia Corporation NV34 [GeForce FX 5200]" 
	Boardname	"nv" 
	Busid		"PCI:1:0:0" 
	Driver		"nvidia" 
	Screen	0 
	Option		"AddARGBVisuals"	"True" 
	Option		"AddARGBGLXVisuals"	"True" 
	Option		"NoLogo"	"True" [/INDENT]
EndSection 

Section "Monitor" 
	[INDENT]Identifier	"Generic Monitor" 
	Vendorname	"Dell" 
	Modelname	"Dell 1905FP (Digital)" 
	Horizsync	30.0-81.0 
	Vertrefresh	56.0-76.0 [/INDENT]
 [INDENT] ************************
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync 
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync 
[COLOR="Red"]  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync[/COLOR] 
  ****************************
	Gamma	1.0 [/INDENT]
EndSection 

Section "Screen" 
	[INDENT]Identifier	"Default Screen" 
	Device		"nVidia Corporation NV34 [GeForce FX 5200]" 
	Monitor		"Generic Monitor" 
	Defaultdepth	24 
	SubSection "Display" 
		Depth	24 
		Virtual	1600	1200 [/INDENT]
Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x1024@60"	"1024x768@60"	"1280x960@75"	"1024x768@70"	"1400x1050@60"	"1024x768@75"	"1600x1200@65"	"832x624@75"	"1600x1200@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60" 
	EndSubSection 
EndSection 

Section "Module"
	[INDENT]Load		"glx"
	Load		"v4l"[/INDENT]
EndSection


---

### Post by Shazaam on 2008-02-17
I also had similar problems getting xorg to work in Gutsy with my GeForce 7800gs. I have tried the Restricted Drivers way, tried Envy, everything. Finally installed the drivers from nvidia and ended up with the low graphics mode problem. Then I cheated. :)
I have a multi-boot system including Dapper and Gutsy. What I did was copy the working xorg.conf from Dapper over to Gutsy and now I have a working system. Here is part of my working Gutsy xorg.conf...........
```
Section "Monitor"
    Identifier     "A90"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "A90"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```
Obviously if you use this you would have to edit it for your monitor name.

---


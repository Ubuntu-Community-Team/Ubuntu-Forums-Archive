---
title: "Dell XPS One 2710 Resolution Issue"
date: 2012-09-11
forum: Multimedia Software
---

### Post by matre on 2012-09-11
Hi there,

I have a new Dell XPS One 2710 which for those not familiar is a Dell iMac like machine. I am leaving the XPSOne with Windows7 but it has a HDMI In port and I am going to use it as a external monitor for a separate Ubuntu 12.04 machine.  My Ubuntu machine has a NVidia GT640 and I am using a HDMI cable.  My issue is I cant get Ubuntu to use the monitors full 2560x1440 resolution.  

On installation the resolution is very poor at around the 1280x800 mark. First thing I did was install the latest x-swat NVidia drivers and this improved the situation and the default resolution was up to 1920x1080.

I have read lots of threads and figured it might was EDID related as I am using an external HDMI-In port.  So I exported the EDID from the windows machine and installed read-edid on ubuntu.  The EDID file looks okay....

```
~$ parse-edid /etc/X11/dell2710.bin 
parse-edid: parse-edid version 2.0.0
parse-edid: EDID checksum passed.

	# EDID version 1 revision 4
Section "Monitor"
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "XPS One 2710"
	VendorName "@@@"
	ModelName "XPS One 2710"
	# Block type: 2:0 3:fd
	HorizSync 15-99
	VertRefresh 55-65
	# Max dot clock (video bandwidth) 90 MHz
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:ff
	# DPMS capabilities: Active off:yes  Suspend:no  Standby:no

	Mode 	"2560x1440"	# vfreq 59.951Hz, hfreq 88.787kHz
		DotClock	241.500000
		HTimings	2560 2608 2640 2720
		VTimings	1440 1443 1448 1481
		Flags	"+HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:ff
EndSection
```

I then updated my /etc/X11/xorg.conf to use this custom edid file and generally kept it as simple as possible.  The following is the relevant sections of my xorg.conf file:

```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 640"
    Option	   "CustomEDID"  "DFP-1:/etc/X11/dell2710.bin"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
EndSection
```

On restart I get a resolution of 2048 x 1152 but I still cant get to 2560x1440.  In the Nvidia settings monitor section it knows default resoltion is 2560x1440 but its not using it....

The relevant section of my Xorg.0.log 

```
[     3.274] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Screen0" for depth/fbbpp 24/32
[     3.274] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     3.274] (==) NVIDIA(0): RGB weight 888
[     3.274] (==) NVIDIA(0): Default visual is TrueColor
[     3.274] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     3.274] (**) NVIDIA(0): Option "CustomEDID" "DFP-1:/etc/X11/dell2710.bin"
[     3.274] (**) NVIDIA(0): Enabling 2D acceleration
[     4.082] (II) NVIDIA(0): NVIDIA GPU GeForce GT 640 (GK107) at PCI:1:0:0 (GPU-0)
[     4.082] (--) NVIDIA(0): Memory: 2097152 kBytes
[     4.082] (--) NVIDIA(0): VideoBIOS: 80.07.26.00.34
[     4.082] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     4.082] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[     4.084] (--) NVIDIA(0): Valid display device(s) on GeForce GT 640 at PCI:1:0:0
[     4.084] (--) NVIDIA(0):     CRT-0
[     4.084] (--) NVIDIA(0):     DFP-0
[     4.084] (--) NVIDIA(0):     Sangyo XPS One 2710 (DFP-1) (connected)
[     4.084] (--) NVIDIA(0):     DFP-2
[     4.084] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[     4.084] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[     4.084] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[     4.084] (--) NVIDIA(0): Sangyo XPS One 2710 (DFP-1): 165.0 MHz maximum pixel clock
[     4.084] (--) NVIDIA(0): Sangyo XPS One 2710 (DFP-1): Internal Single Link TMDS
[     4.084] (--) NVIDIA(0): DFP-2: 330.0 MHz maximum pixel clock
[     4.084] (--) NVIDIA(0): DFP-2: Internal Single Link TMDS
[     4.084] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     4.084] (**) NVIDIA(0):     device Sangyo XPS One 2710 (DFP-1) (Using EDID frequencies
[     4.084] (**) NVIDIA(0):     has been enabled on all display devices.)
[     4.084] (==) NVIDIA(0): 
[     4.084] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     4.084] (==) NVIDIA(0):     will be used as the requested mode.
[     4.084] (==) NVIDIA(0): 
[     4.084] (II) NVIDIA(0): Validated MetaModes:
[     4.084] (II) NVIDIA(0):     "DFP-1:nvidia-auto-select"
[     4.084] (II) NVIDIA(0): Virtual screen size determined to be 2048 x 1152
[     4.110] (--) NVIDIA(0): DPI set to (86, 86); computed from "UseEdidDpi" X config
[     4.110] (--) NVIDIA(0):     option
[     4.110] (--) Depth 24 pixmap format is 32 bpp
[     4.110] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[     4.110] (II) NVIDIA:     access.
[     4.113] (II) NVIDIA(0): Setting mode "DFP-1:nvidia-auto-select"
[     4.146] (II) Loading extension NV-GLX
[     4.155] (==) NVIDIA(0): Disabling shared memory pixmaps
[     4.155] (==) NVIDIA(0): Backing store disabled
[     4.155] (==) NVIDIA(0): Silken mouse enabled
[     4.155] (==) NVIDIA(0): DPMS enabled
[     4.155] (II) Loading extension NV-CONTROL
[     4.156] (II) Loading extension XINERAMA
[     4.156] (II) Loading sub module "dri2"
[     4.156] (II) LoadModule: "dri2"
[     4.156] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     4.156] (II) Module dri2: vendor="X.Org Foundation"
[     4.156] 	compiled for 1.11.3, module version = 1.2.0
[     4.156] 	ABI class: X.Org Server Extension, version 6.0
[     4.156] (II) NVIDIA(0): [DRI2] Setup complete
[     4.156] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
```

Its getting all the right info but the "No modes were requested; the default mode "nvidia-auto-select".  nvidia-auto-select is not doing what I want!

I have tried a few different things to set the mode but have not managed to improve the situation.   I have tried a few different Option metamodes settings in the screen section of my xorg.conf but just get errors along the lines of unknown modes and it reverts to the default nvidia-auto-select.

Any ideas?  I feel I am close to getting this fixed but I am running around in circles right now.

Thanks in advance,

Matt

---


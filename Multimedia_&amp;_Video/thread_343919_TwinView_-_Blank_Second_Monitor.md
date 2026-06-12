---
title: "TwinView - Blank Second Monitor"
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by tumblebug on 2007-01-22
Ok - to preface this, I have done ALOT of extensive internet and forum searching, endless reboots and now I need to ask questions so please forgive the noobie long post :) 

I have a GeForce 4 MX440 video card, with a Diamond View 1772e connected to the VGA port, and a Daewoo 710B connected to the DVI port with a DVI-VGA adaptor. I am running Ubuntu 6.1, with the 7184 Nvidia legacy drivers on a hyperthreaded Dell with 256M of Ram (I think).

After actually getting the Nvidia drivers in and working (I have been using linux for about 5 days now), I want to get my second monitor running with Twinview. After following a great number of ideas from a lot of people's experiences, Linux is finally behaving as if the second monitor is working but all I can see on the second screen is a VERY faint outline of whatever is supposed to be displaying on it. 

I am suspecting the DVI-VGA adaptor and I've read that some adaptors don't carry the VGA info. I know the monitor works (have tried it in the VGA port of the card), and the resolutions and refresh rates are well within what the monitor is capable of. 

Anyone have any ideas/solutions on what could be happening? Can post xorg.conf etc if needed but I dont think the problem is there somehow.....](*,)

---

### Post by majoridiot on 2007-01-22
it's always helpful to post as much info as possible to help sort things out.  please post your
xorg.conf and /var/log/Xorg.0.log

if you suspect it may be the converter, you might try another one.  they are cheap... just
get a recommendation from a trusted local retailer.

---

### Post by tumblebug on 2007-01-23
righto - will upload the xorg.conf and the log file with this post, and the next one (40000 character limit on posting). In the text below, I've clipped out the unnecessary stuff, like Files, Inputdevices, etc - all that was preconfigured with my last "sudo dpkg-reconfigure..."

With the adapter, I've read that I need DVI-D plug and from the descriptions I've seen, thats the one I have (all the right pins in the right places), so maybe its not the adaptor....

Here's the files - please pardon the commented out lines, its a bit of a mess but once I got it working, I'll clean them up :) 

```


Section "Module"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "type1"
    Load           "v4l"
    Load           "vbe"
EndSection

Section "Monitor"
	Identifier     "DiamondView"
    	Option         "DPMS"
	# V-freq: 60.00 Hz  // h-freq: 63.73 KHz
 	Modeline "1280x1024_60" 109.62  1280 1336 1472 1720  1024 1024 1026 1062
	#Modeline "1280x1024" 123.01  1280 1344 1496 1776  1024 1024 1027 1065	
	Modeline "1024x768_60" 81.54  1024 1064 1168 1352   768  768  770  804  
EndSection

Section "Device"
	Identifier     	"GeForce MX440 AGP8"
    	Driver         	"nvidia"
	BusID		"AGP:1:0:0"
	Option		"UseEDID" "True"
	Option		"NvAGP" "1"
	Option		"RenderAccel" "Off"
#	Option		"IgnoreDisplayDevices" "DFP,TV"
	Option		"NoRenderExtension" "Off"
	Option		"AllowGLXWithComposite" "Off"
	Option		"TwinView" "True"
	Option		"TwinViewOrientation" "RightOf"   
	Option		"UseEdidFreqs" "True"
	Option		"HorizSync" "CRT-0: 30-72; CRT-1: 31-69" 
    	Option		"VertRefresh" "CRT-0: 50-120; CRT-1: 50-160"
#	Option		"MetaModes" "CRT-0:1280x1024,CRT-1:1280x1024; CRT-0:1024x768,CRT-1:1024x768"
	Option		"MetaModes" "CRT-0:1280x1024_60,CRT-1:1280x1024_60; CRT-0:1024x768_60, CRT-1:1024x768_60"
#	Option		"NoPowerConnectorCheck"
#	Option		"UseDisplayDevice" "CRT-0,CRT"
	Option		"ConnectedMonitor" "CRT-0,CRT-1"
EndSection

Section "Screen"
 	Identifier     "Default Screen"
    	Device         "GeForce MX440 AGP8"
    	Monitor        "DiamondView"
    	DefaultDepth    24
    	Option         "ExactModeTimingsDVI" "True"
#    	Option         "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
    	SubSection     "Display"
#		Viewport 	0 0        	
		Depth       	16
       		Modes      	"2560x1024" "2048x1536"
    	EndSubSection
    	SubSection     "Display"
#		Viewport	0 0
        	Depth   	24
        	Modes      	"2560x1024" "2048x1536"
    	EndSubSection
EndSection

Section "ServerLayout"
    	Identifier     	"Default Layout"
    	Screen         	"Default Screen"
    	InputDevice    	"Generic Keyboard"
    	InputDevice	"Configured Mouse"
#	Option		"Xinerama" "Off"
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```



hope it helps....any ideas would be appreciated

tumblebug

---

### Post by tumblebug on 2007-01-23
here's the logfile....again I trimmed out non-relevant info (I hope its not relevant)...

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux timbo-desktop 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.

(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 22 22:45:21 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DiamondView"
(**) |   |-->Device "GeForce MX440 AGP8"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfd000000 - 0xfeafffff (0x1b00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfcf00000 - 0xfcffffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xf80fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] rev 162, Mem @ 0xfd000000/24, 0xf0000000/27, BIOS @ 0xfea00000/17
(--) PCI: (2:0:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xf8001000/12
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7184
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers/v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.1
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7184
	Module class: XFree86 Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  1.0-7184  Tue Aug  1 18:40:06 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfcffb000 - 0xfcffbfff (0x1000) MX[B]
	[5] -1	0	0xfcffc000 - 0xfcffffff (0x4000) MX[B]
	[6] -1	0	0xfcffa800 - 0xfcffafff (0x800) MX[B]
	[7] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[9] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[10] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[11] -1	0	0xf8001000 - 0xf8001fff (0x1000) MX[B](B)
	[12] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[13] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[18] -1	0	0x0000ded8 - 0x0000dedf (0x8) IX[B]
	[19] -1	0	0x0000dee0 - 0x0000deff (0x20) IX[B]
	[20] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[21] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[22] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[23] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[24] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[25] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[26] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[29] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[30] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfcffb000 - 0xfcffbfff (0x1000) MX[B]
	[5] -1	0	0xfcffc000 - 0xfcffffff (0x4000) MX[B]
	[6] -1	0	0xfcffa800 - 0xfcffafff (0x800) MX[B]
	[7] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[9] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[10] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[11] -1	0	0xf8001000 - 0xf8001fff (0x1000) MX[B](B)
	[12] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[13] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[21] -1	0	0x0000ded8 - 0x0000dedf (0x8) IX[B]
	[22] -1	0	0x0000dee0 - 0x0000deff (0x20) IX[B]
	[23] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[24] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[25] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[26] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[27] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[28] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[29] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[32] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[33] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[36] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[37] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[38] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NvAGP" "1"
(**) NVIDIA(0): Option "ConnectedMonitor" "CRT-0,CRT-1"
(**) NVIDIA(0): Option "RenderAccel" "Off"
(**) NVIDIA(0): Option "UseEdidFreqs" "True"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "MetaModes" "CRT-0:1280x1024_60,CRT-1:1280x1024_60; CRT-0:1024x768_60, CRT-1:1024x768_60"
(**) NVIDIA(0): Option "NoRenderExtension" "Off"
(**) NVIDIA(0): Option "HorizSync" "CRT-0: 30-72; CRT-1: 31-69"
(**) NVIDIA(0): Option "VertRefresh" "CRT-0: 50-120; CRT-1: 50-160"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "Off"
(**) NVIDIA(0): Option "ExactModeTimingsDVI" "True"
(**) NVIDIA(0): Use of NVIDIA internal AGP requested
(**) NVIDIA(0): ConnectedMonitor string: "CRT-0,CRT-1"
(**) NVIDIA(0): TwinView enabled
(--) NVIDIA(0): Linear framebuffer at 0xF0000000
(--) NVIDIA(0): MMIO registers at 0xFD000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce4 MX 440 with AGP8X
(--) NVIDIA(0): VideoBIOS: 04.18.20.21.ad
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): VideoRAM: 65536 kBytes
(II) NVIDIA(0): Using ConnectedMonitor string "CRT-0, CRT-1"
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at  8 bpp: 350 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 16 bpp: 350 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 32 bpp: 350 MHz
(--) NVIDIA(0): Display device CRT-1: maximum pixel clock at  8 bpp: 350 MHz
(--) NVIDIA(0): Display device CRT-1: maximum pixel clock at 16 bpp: 350 MHz
(--) NVIDIA(0): Display device CRT-1: maximum pixel clock at 32 bpp: 350 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(WW) NVIDIA(0): Unable to use EDID frequencies for display device CRT-0 (EDID
(WW) NVIDIA(0):      found, but no frequencies given in EDID)
(WW) NVIDIA(0): config file hsync range 30-72kHz not within DDC hsync ranges.
(WW) NVIDIA(0): config file vrefresh range 50-120Hz not within DDC vrefresh ranges.
(II) NVIDIA(0): DiamondView: Using hsync range of 30.00-72.00 kHz
(II) NVIDIA(0): DiamondView: Using vrefresh range of 50.00-120.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 350.00 MHz
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1440x900" (width too large for virtual size)
(WW) NVIDIA(0): Not using mode "840x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
(WW) NVIDIA(0): Not using mode "700x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
(WW) NVIDIA(0): Not using mode "1152x768":
(WW) NVIDIA(0):   horizontal sync start (1178) not a multiple of 8
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Mode "1280x1024_60": 109.6 MHz, 63.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Mode "1024x768_60": 81.5 MHz, 60.3 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.0 Hz (I)
(**) NVIDIA(0):      Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(**) NVIDIA(0):      Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.9 Hz (D)
(**) NVIDIA(0):      Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NVIDIA(0): DiamondView: Using hsync range of 30.00-69.00 kHz
(II) NVIDIA(0): DiamondView: Using vrefresh range of 50.00-160.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 350.00 MHz
(WW) (1280x1024_60,DiamondView) mode clock 109.62MHz exceeds DDC maximum 90MHz
(WW) (1024x768,DiamondView) mode clock 94.5MHz exceeds DDC maximum 90MHz
(WW) (1152x864,DiamondView) mode clock 108MHz exceeds DDC maximum 90MHz
(WW) (1280x960,DiamondView) mode clock 108MHz exceeds DDC maximum 90MHz
(WW) (1280x960,DiamondView) mode clock 148.5MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(WW) (1280x1024,DiamondView) mode clock 108MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,DiamondView) mode clock 135MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(WW) (1280x1024,DiamondView) mode clock 157.5MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(WW) (1600x1200,DiamondView) mode clock 162MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,DiamondView) mode clock 175.5MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,DiamondView) mode clock 189MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(WW) (800x600,DiamondView) mode clock 94.5MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,DiamondView) mode clock 202.5MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(WW) (800x600,DiamondView) mode clock 101.25MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,DiamondView) mode clock 229.5MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(WW) (800x600,DiamondView) mode clock 114.75MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1792x1344,DiamondView) mode clock 204.8MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(WW) (896x672,DiamondView) mode clock 102.4MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(WW) (1792x1344,DiamondView) mode clock 261MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(WW) (896x672,DiamondView) mode clock 130.5MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(WW) (1856x1392,DiamondView) mode clock 218.3MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(WW) (928x696,DiamondView) mode clock 109.15MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(WW) (1856x1392,DiamondView) mode clock 288MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(WW) (928x696,DiamondView) mode clock 144MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(WW) (1920x1440,DiamondView) mode clock 234MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,DiamondView) mode clock 117MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(WW) (1920x1440,DiamondView) mode clock 297MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,DiamondView) mode clock 148.5MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(WW) (1152x864,DiamondView) mode clock 121.5MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(WW) (1400x1050,DiamondView) mode clock 122MHz exceeds DDC maximum 90MHz
(WW) (1400x1050,DiamondView) mode clock 151MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(WW) (1400x1050,DiamondView) mode clock 155.8MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(WW) (1400x1050,DiamondView) mode clock 184MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(WW) (700x525,DiamondView) mode clock 92MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(WW) (1440x900,DiamondView) mode clock 108.84MHz exceeds DDC maximum 90MHz
(WW) (1600x1024,DiamondView) mode clock 106.91MHz exceeds DDC maximum 90MHz
(WW) (1680x1050,DiamondView) mode clock 147.14MHz exceeds DDC maximum 90MHz
(WW) (1920x1200,DiamondView) mode clock 193.16MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(WW) (960x600,DiamondView) mode clock 96.58MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(WW) (1920x1200,DiamondView) mode clock 230MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(WW) (960x600,DiamondView) mode clock 115MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(WW) (1920x1440,DiamondView) mode clock 341.35MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,DiamondView) mode clock 170.675MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(WW) (2048x1536,DiamondView) mode clock 266.95MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(WW) (1024x768,DiamondView) mode clock 133.475MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(WW) (2048x1536,DiamondView) mode clock 340.48MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(WW) (1024x768,DiamondView) mode clock 170.24MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(WW) (2048x1536,DiamondView) mode clock 388.04MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(WW) (1024x768,DiamondView) mode clock 194.02MHz exceeds DDC maximum 90MHz
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1440x900" (width too large for virtual size)
(WW) NVIDIA(0): Not using mode "840x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
(WW) NVIDIA(0): Not using mode "700x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
(WW) NVIDIA(0): Not using mode "1152x768":
(WW) NVIDIA(0):   horizontal sync start (1178) not a multiple of 8
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device CRT-1:
(**) NVIDIA(0):      Mode "1280x1024_60": 109.6 MHz, 63.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Mode "1024x768_60": 81.5 MHz, 60.3 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.0 Hz (I)
(**) NVIDIA(0):      Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(**) NVIDIA(0):      Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.9 Hz (D)
(**) NVIDIA(0):      Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 2560 x 1024
(--) NVIDIA(0): Display dimensions: (570, 230) mm
(--) NVIDIA(0): DPI set to (114, 113)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfcffb000 - 0xfcffbfff (0x1000) MX[B]
	[7] -1	0	0xfcffc000 - 0xfcffffff (0x4000) MX[B]
	[8] -1	0	0xfcffa800 - 0xfcffafff (0x800) MX[B]
	[9] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[10] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[11] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[12] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[13] -1	0	0xf8001000 - 0xf8001fff (0x1000) MX[B](B)
	[14] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[23] -1	0	0x0000ded8 - 0x0000dedf (0x8) IX[B]
	[24] -1	0	0x0000dee0 - 0x0000deff (0x20) IX[B]
	[25] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[26] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[27] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[28] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[29] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[30] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[31] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[32] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[33] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[34] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[35] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[37] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[38] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[39] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[40] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "CRT-0:1280x1024_60,CRT-1:1280x1024_60"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(WW) NVIDIA(0): Option "UseEDID" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /usr/lib/xserver/SecurityPolicy
(II) NVIDIA(0): Setting mode "CRT-0:1280x1024_60,CRT-1:1280x1024_60"
(II) NVIDIA(0): Setting mode "CRT-0:1280x1024_60,CRT-1:1280x1024_60"
(II) NVIDIA(0): Setting mode "CRT-0:1024x768_60,CRT-1:1024x768_60"
(II) NVIDIA(0): Setting mode "CRT-0:1280x1024_60,CRT-1:1280x1024_60"

```

---

### Post by majoridiot on 2007-01-24
wow... what a mess.

lotsa problems there, including EDID failing and bad frequencies, etc.

try replacing these sections with this:

```
Section "Device"
	Identifier     	"GeForce MX440 AGP8"
    	Driver         	"nvidia"
	BusID		"AGP:1:0:0"
	Option		"NvAGP" "1"
	Option		"RenderAccel" "Off"
	Option		"TwinView" "True"
	Option		"TwinViewOrientation" "RightOf"   
	Option		"HorizSync" "CRT-0: 30-72; CRT-1: 31-69" 
    	Option		"VertRefresh" "CRT-0: 50-120; CRT-1: 50-160"
	Option		"MetaModes" "CRT-0:1280x1024_60,CRT-1:1280x1024_60; CRT-0:1024x768_60, CRT-1:1024x768_85"
EndSection

Section "Screen"
 	Identifier     "Default Screen"
    	Device         "GeForce MX440 AGP8"
    	Monitor        "DiamondView"
    	DefaultDepth    24
    	SubSection     "Display"
		Depth       	16
       		Modes      	"1280X1024" "1024X768"
    	EndSubSection
    	SubSection     "Display"
        	Depth   	24
        	Modes      	"1280X1024" "1024X768"
EndSection

Section "ServerLayout"
    	Identifier     	"Default Layout" 0 0
    	Screen         	"Default Screen"
    	InputDevice    	"Generic Keyboard"
    	InputDevice	"Configured Mouse"
EndSection
```

see what happens with that... post any errors you encounter.

---

### Post by tumblebug on 2007-01-24
Thanks for checking this out, Major

I did what you suggested (I did move the "0 0" in the "ServerLayout" section from the Layout line to the Screen line because I got a error on startup), however, the second monitor now does not even come out of stand-by, and from looking at the log, it wasn't even detected so Twinview shut itself down, and I'm running on one screen again...

Here's the log

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux timbo-desktop 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan 25 10:20:11 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DiamondView"
(**) |   |-->Device "GeForce MX440 AGP8"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1028,0174 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1028,0174 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1028,0174 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1028,0174 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1028,0174 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1028,0174 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1028,0174 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,24d1 card 1028,0174 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1028,0174 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0181 card 10de,01b6 rev a2 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 109e,036e card 11bd,0012 rev 11 class 04,00,00 hdr 80
(II) PCI: 02:00:1: chip 109e,0878 card 11bd,0012 rev 11 class 04,80,00 hdr 80
(II) PCI: 02:01:0: chip 1102,0004 card 1102,1003 rev 04 class 04,01,00 hdr 80
(II) PCI: 02:01:2: chip 1102,4001 card 1102,0010 rev 04 class 0c,00,10 hdr 80
(II) PCI: 02:02:0: chip 1102,0002 card 1102,8061 rev 07 class 04,01,00 hdr 80
(II) PCI: 02:02:1: chip 1102,7002 card 1102,0020 rev 07 class 09,80,00 hdr 80
(II) PCI: 02:08:0: chip 8086,1050 card 1028,0174 rev 02 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfd000000 - 0xfeafffff (0x1b00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfcf00000 - 0xfcffffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xf80fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] rev 162, Mem @ 0xfd000000/24, 0xf0000000/27, BIOS @ 0xfea00000/17
(--) PCI: (2:0:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xf8001000/12
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe8000000 from 0xefffffff to 0xe7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfcffb000 - 0xfcffbfff (0x1000) MX[B]
	[1] -1	0	0xfcffc000 - 0xfcffffff (0x4000) MX[B]
	[2] -1	0	0xfcffa800 - 0xfcffafff (0x800) MX[B]
	[3] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[4] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[5] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[6] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[7] -1	0	0xf8001000 - 0xf8001fff (0x1000) MX[B](B)
	[8] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[9] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[12] -1	0	0x0000ded8 - 0x0000dedf (0x8) IX[B]
	[13] -1	0	0x0000dee0 - 0x0000deff (0x20) IX[B]
	[14] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[15] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[16] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[17] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[18] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[19] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[20] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[27] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[28] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[29] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfcffb000 - 0xfcffbfff (0x1000) MX[B]
	[1] -1	0	0xfcffc000 - 0xfcffffff (0x4000) MX[B]
	[2] -1	0	0xfcffa800 - 0xfcffafff (0x800) MX[B]
	[3] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[4] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[5] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[6] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[7] -1	0	0xf8001000 - 0xf8001fff (0x1000) MX[B](B)
	[8] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[9] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[12] -1	0	0x0000ded8 - 0x0000dedf (0x8) IX[B]
	[13] -1	0	0x0000dee0 - 0x0000deff (0x20) IX[B]
	[14] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[15] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[16] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[17] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[18] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[19] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[20] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[27] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[28] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[29] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfcffb000 - 0xfcffbfff (0x1000) MX[B]
	[5] -1	0	0xfcffc000 - 0xfcffffff (0x4000) MX[B]
	[6] -1	0	0xfcffa800 - 0xfcffafff (0x800) MX[B]
	[7] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[9] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[10] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[11] -1	0	0xf8001000 - 0xf8001fff (0x1000) MX[B](B)
	[12] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[13] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[18] -1	0	0x0000ded8 - 0x0000dedf (0x8) IX[B]
	[19] -1	0	0x0000dee0 - 0x0000deff (0x20) IX[B]
	[20] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[21] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[22] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[23] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[24] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[25] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[26] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[29] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[30] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7184
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers/v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.1
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7184
	Module class: XFree86 Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  1.0-7184  Tue Aug  1 18:40:06 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfcffb000 - 0xfcffbfff (0x1000) MX[B]
	[5] -1	0	0xfcffc000 - 0xfcffffff (0x4000) MX[B]
	[6] -1	0	0xfcffa800 - 0xfcffafff (0x800) MX[B]
	[7] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[9] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[10] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[11] -1	0	0xf8001000 - 0xf8001fff (0x1000) MX[B](B)
	[12] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[13] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[18] -1	0	0x0000ded8 - 0x0000dedf (0x8) IX[B]
	[19] -1	0	0x0000dee0 - 0x0000deff (0x20) IX[B]
	[20] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[21] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[22] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[23] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[24] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[25] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[26] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[29] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[30] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfcffb000 - 0xfcffbfff (0x1000) MX[B]
	[5] -1	0	0xfcffc000 - 0xfcffffff (0x4000) MX[B]
	[6] -1	0	0xfcffa800 - 0xfcffafff (0x800) MX[B]
	[7] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[9] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[10] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[11] -1	0	0xf8001000 - 0xf8001fff (0x1000) MX[B](B)
	[12] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[13] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[21] -1	0	0x0000ded8 - 0x0000dedf (0x8) IX[B]
	[22] -1	0	0x0000dee0 - 0x0000deff (0x20) IX[B]
	[23] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[24] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[25] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[26] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[27] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[28] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[29] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[32] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[33] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[36] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[37] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[38] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NvAGP" "1"
(**) NVIDIA(0): Option "RenderAccel" "Off"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "MetaModes" "CRT-0:1280x1024_60,CRT-1:1280x1024_60; CRT-0:1024x768_60, CRT-1:1024x768_85"
(**) NVIDIA(0): Option "HorizSync" "CRT-0: 30-72; CRT-1: 31-69"
(**) NVIDIA(0): Option "VertRefresh" "CRT-0: 50-120; CRT-1: 50-160"
(**) NVIDIA(0): Use of NVIDIA internal AGP requested
(**) NVIDIA(0): TwinView enabled
(--) NVIDIA(0): Linear framebuffer at 0xF0000000
(--) NVIDIA(0): MMIO registers at 0xFD000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce4 MX 440 with AGP8X
(--) NVIDIA(0): VideoBIOS: 04.18.20.21.ad
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): VideoRAM: 65536 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at  8 bpp: 350 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 16 bpp: 350 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 32 bpp: 350 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(WW) NVIDIA(0): The HorizSync string "CRT-0: 30-72; CRT-1: 31-69" contains 2
(WW) NVIDIA(0):      ranges, but only 1 display devices are enabled; only
(WW) NVIDIA(0):      parsing the first 1.
(WW) NVIDIA(0): The VertRefresh string "CRT-0: 50-120; CRT-1: 50-160" contains
(WW) NVIDIA(0):      2 ranges, but only 1 display devices are enabled; only
(WW) NVIDIA(0):      parsing the first 1.
(WW) NVIDIA(0): Only one display device connected; disabling TwinView.
(WW) NVIDIA(0): config file hsync range 30-72kHz not within DDC hsync ranges.
(WW) NVIDIA(0): config file vrefresh range 50-120Hz not within DDC vrefresh ranges.
(II) NVIDIA(0): DiamondView: Using hsync range of 30.00-72.00 kHz
(II) NVIDIA(0): DiamondView: Using vrefresh range of 50.00-120.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 350.00 MHz
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using mode "1280X1024" (no mode of this name)
(II) NVIDIA(0): Not using mode "1024X768" (no mode of this name)
(WW) NVIDIA(0): Not using mode "1680x1050" (width 1680 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1280)
(WW) NVIDIA(0): Not using mode "1400x1050" (width 1400 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1280)
(WW) NVIDIA(0): Not using mode "1440x900" (width 1440 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1280)
(WW) NVIDIA(0): Not using mode "840x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
(WW) NVIDIA(0): Not using mode "700x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
(WW) NVIDIA(0): Not using mode "1152x768":
(WW) NVIDIA(0):   horizontal sync start (1178) not a multiple of 8
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Mode "1280x1024_60": 109.6 MHz, 63.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Mode "1024x768_60": 81.5 MHz, 60.3 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.0 Hz (I)
(**) NVIDIA(0):      Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(**) NVIDIA(0):      Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.9 Hz (D)
(**) NVIDIA(0):      Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): Display dimensions: (310, 230) mm
(--) NVIDIA(0): DPI set to (104, 113)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfcffb000 - 0xfcffbfff (0x1000) MX[B]
	[7] -1	0	0xfcffc000 - 0xfcffffff (0x4000) MX[B]
	[8] -1	0	0xfcffa800 - 0xfcffafff (0x800) MX[B]
	[9] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[10] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[11] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[12] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[13] -1	0	0xf8001000 - 0xf8001fff (0x1000) MX[B](B)
	[14] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[23] -1	0	0x0000ded8 - 0x0000dedf (0x8) IX[B]
	[24] -1	0	0x0000dee0 - 0x0000deff (0x20) IX[B]
	[25] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[26] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[27] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[28] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[29] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[30] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[31] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[32] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[33] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[34] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[35] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[37] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[38] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[39] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[40] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024_60"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) NVIDIA(0): v4l[/dev/video0]: using hw video scaling [YUY2].
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc11"
(**) Generic Keyboard: XkbModel: "pc11"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc104)" };
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

```

here's the xorg.conf as it stands now

```

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "type1"
    Load           "v4l"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc11"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier     "DiamondView"
    	Option         "DPMS"
	# V-freq: 60.00 Hz  // h-freq: 63.73 KHz
 	Modeline "1280x1024_60" 109.62  1280 1336 1472 1720  1024 1024 1026 1062
	#Modeline "1280x1024" 123.01  1280 1344 1496 1776  1024 1024 1027 1065	
	Modeline "1024x768_60" 81.54  1024 1064 1168 1352   768  768  770  804  
EndSection

Section "Device"
	Identifier     	"GeForce MX440 AGP8"
    	Driver         	"nvidia"
	BusID		"AGP:1:0:0"
	Option		"NvAGP" "1"
	Option		"RenderAccel" "Off"
	Option		"TwinView" "True"
	Option		"TwinViewOrientation" "RightOf"   
	Option		"HorizSync" "CRT-0: 30-72; CRT-1: 31-69" 
    	Option		"VertRefresh" "CRT-0: 50-120; CRT-1: 50-160"
	Option		"MetaModes" "CRT-0:1280x1024_60,CRT-1:1280x1024_60; CRT-0:1024x768_60, CRT-1:1024x768_85"
EndSection

Section "Screen"
 	Identifier     "Default Screen"
    	Device         "GeForce MX440 AGP8"
    	Monitor        "DiamondView"
    	DefaultDepth    24
    	SubSection     "Display"
		Depth       	16
       		Modes      	"1280X1024" "1024X768"
    	EndSubSection
    	SubSection     "Display"
        	Depth   	24
        	Modes      	"1280X1024" "1024X768"
	EndSubSection
EndSection

Section "ServerLayout"
    	Identifier     	"Default Layout"
    	Screen         	"Default Screen" 0 0
    	InputDevice    	"Generic Keyboard"
    	InputDevice	"Configured Mouse"
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```

---

### Post by jbayone on 2007-01-24
I think you may need to change the "ConnectedMonitor" "CRT-0,CRT-1" to "CRT, DFP" just not 100% sure, but it's what I had to do

---

### Post by tumblebug on 2007-01-25
Sorry Major - I stuffed up....it always helps to have the adapter and the monitor plugged into the DVI port so it can be detected

After doing that, and putting in your changes, I am still at the same point - VERY faint outline on the second monitor, yet able to move windows back and forth to it, etc.

Is there any way past the 40000 character posting limit???

---

### Post by tumblebug on 2007-01-25
@ jbayone

I tried the "DFP" in the ConnectedMonitors string but it didnt work - I read somewhere the TwinView needs to treat a CRT screen as a "CRT", even though it is connected to the DVI port (via an adaptor).

Thanks

---

### Post by kerry_s on 2007-01-25
Don't give it all those options for the resolution, just list the one you want to use. Also you can only go as high as both screens can handle, meaning if the max on 1 is 1280x1024, and the other 1 has a max of 1024x768, you need to use the 1024x768 for both.here's mine->

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/font-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    Load           "dbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "A70"
    Option         "DPMS"
    Option         "UseEdidDpi" "True"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
    Driver         "nvidia"
EndSection

Section "Screen"

# Only the official NVIDIA driver supports twinview
# these setting are an example
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
    Monitor        "A70"
    DefaultDepth    24
    Option         "SecondMonitorHorizSync" "31.468-71.0"
    Option         "SecondMonitorVertRefresh" "56.0-85.0"
    Option         "ConnectedMonitor" "crt,crt"
    Option         "RenderAccel" "true"
    Option         "nologo" "true"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "MetaModes" "1280x1024, 1280x1024"
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

Section "Extensions"
    Option         "Composite" "FALSE"
EndSection


```

---


---
title: "Can't get intel driver to work for Dell Studio Hybrid"
date: 2012-03-31
forum: Multimedia Software
---

### Post by danBhentschel on 2012-03-31
I'm sorry if this question has been answered elsewhere already. I have tried searching the forums and googling for a couple of days now without much luck. I recently purchased a Dell Studio Hybrid 140g since I thought it would make a slick Mythbuntu frontend to replace my current big, old box. Unfortunately, I can't get it to output video to my TV in anything other than 640x480. I just installed a clean install of Mythbuntu 11.10. It seems to insist on using the VESA driver rather than the Intel driver. Any help is appreciated. Here is some info:

lspci reports:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)

```


Excerpts from Xorg.0.log:
```

[    14.125] (II) LoadModule: "intel"
[    14.126] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    14.126] (II) Module intel: vendor="X.Org Foundation"
[    14.126]    compiled for 1.10.4, module version = 2.15.901
[    14.126]    Module class: X.Org Video Driver
[    14.126]    ABI class: X.Org Video Driver, version 10.0
[    14.127] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
        Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
        Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
        Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
        Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    14.201] (II) VESA(0): EDID vendor "SNY", prod id 248
[    14.201] (II) VESA(0): Using EDID range info for horizontal sync
[    14.201] (II) VESA(0): Using EDID range info for vertical refresh
[    14.201] (II) VESA(0): Printing DDC gathered Modelines:
[    14.201] (II) VESA(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    14.201] (II) VESA(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    14.201] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.201] (II) VESA(0): Searching for matching VESA mode(s):
[    14.293] (II) VESA(0): Monitor0: Using hsync range of 15.00-46.00 kHz
[    14.293] (II) VESA(0): Monitor0: Using vrefresh range of 59.00-61.00 Hz
[    14.293] (II) VESA(0): Monitor0: Using maximum pixel clock of 85.00 MHz
[    14.293] (II) VESA(0): Not using mode "1920x1080" (no mode of this name)
[    14.293] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[    14.293] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    14.293] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    14.296] (--) VESA(0): Virtual size is 640x480 (pitch 640)
[    14.296] (**) VESA(0):  Built-in mode "640x480"

```

---

### Post by 2F4U on 2012-04-01
How do you connect the machine to your monitor?

---

### Post by danBhentschel on 2012-04-01
The DVI out from the Studio Hybrid is connected to a DVI input on my HDTV. As far as I can tell, the detected supported resolutions are correct. I know that my TV supports 1080i and 720p. The problem is that it is starting up with the VESA driver, and neither 1080i or 720p is a standard, VESA-supported resolution.

I have since played a bit more. I hooked it up to a standard LCD monitor, and it was able to produce multiple higher resolutions, although still through the VESA driver. I then remembered that I specified "nomodeset" in the Grub kernel parameters. Changing this to "i915=nomodeset" fixed the problem, and it then booted up using the intel driver for Xorg on the LCD. However, when I went back to the TV, I didn't get any video on boot with these parameters. At this point I was compelled to stop. I have yet to look at any log files after this most recent boot attempt.

 - dan

---

### Post by BicyclerBoy on 2012-04-02
Get rid of the nomodeset keyword in grub..
i915=nomodeset has same effect as nomodeset..

It's a mystery how you got intel driver loading at any stage..

---

### Post by danBhentschel on 2012-04-02
Okay... So I got rid of all "nomodeset" commands in grub, and now the box boots up to a black screen on my TV. Some things to note:

* I can hit Alt-Ctrl-F1 through Alt-Ctrl-F6 to switch between ttys and login to a command prompt.
* Pressing Alt-Ctrl-F7 brings me back to a black screen and my TV displays "HD" in the corner, indicating that it is not getting a signal.
* Periodically (about once every few minutes) the screen will flicker and I will catch a brief glimpse of the desktop before it goes black again.

Here is a full Xorg.0.log output:

```
[    15.187] 
X.Org X Server 1.11.2.902 (1.11.3 RC 2)
Release Date: 2011-12-09
[    15.187] X Protocol Version 11, Revision 0
[    15.187] Build Operating System: Linux 2.6.24-29-xen i686 Ubuntu
[    15.187] Current Operating System: Linux mythman 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686
[    15.187] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=6ef26a67-1eb6-4cfb-b5d9-07d5d560be84 ro
[    15.187] Build Date: 10 December 2011  11:17:47PM
[    15.188] xorg-server 2:1.11.2.902+git20111209+server-1.11-branch.0ca8869e-0ubuntu0sarvatt~oneiric (For technical support please see http://www.ubuntu.com/support) 
[    15.188] Current version of pixman: 0.25.2
[    15.188] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    15.188] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.188] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr  2 21:04:11 2012
[    15.228] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.228] (==) No Layout section.  Using the first Screen section.
[    15.228] (==) No screen section available. Using defaults.
[    15.228] (**) |-->Screen "Default Screen Section" (0)
[    15.228] (**) |   |-->Monitor "<default monitor>"
[    15.229] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    15.229] (==) Automatically adding devices
[    15.229] (==) Automatically enabling devices
[    15.229] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.229] 	Entry deleted from font path.
[    15.229] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    15.229] 	Entry deleted from font path.
[    15.229] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    15.229] 	Entry deleted from font path.
[    15.229] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    15.229] 	Entry deleted from font path.
[    15.229] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    15.229] 	Entry deleted from font path.
[    15.255] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[    15.255] 	Entry deleted from font path.
[    15.255] 	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[    15.255] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    15.255] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.255] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.255] (II) Loader magic: 0x822a580
[    15.255] (II) Module ABI versions:
[    15.255] 	X.Org ANSI C Emulation: 0.4
[    15.255] 	X.Org Video Driver: 11.0
[    15.255] 	X.Org XInput driver : 13.0
[    15.255] 	X.Org Server Extension : 6.0
[    15.256] (--) PCI:*(0:0:2:0) 8086:2a02:1028:0279 rev 3, Mem @ 0xfdf00000/1048576, 0xd0000000/268435456, I/O @ 0x0000c400/8
[    15.256] (--) PCI: (0:0:2:1) 8086:2a03:1028:0279 rev 3, Mem @ 0xfe000000/1048576
[    15.256] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.256] (II) LoadModule: "extmod"
[    15.279] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.279] (II) Module extmod: vendor="X.Org Foundation"
[    15.279] 	compiled for 1.11.2.902, module version = 1.0.0
[    15.279] 	Module class: X.Org Server Extension
[    15.279] 	ABI class: X.Org Server Extension, version 6.0
[    15.279] (II) Loading extension MIT-SCREEN-SAVER
[    15.279] (II) Loading extension XFree86-VidModeExtension
[    15.279] (II) Loading extension XFree86-DGA
[    15.279] (II) Loading extension DPMS
[    15.279] (II) Loading extension XVideo
[    15.279] (II) Loading extension XVideo-MotionCompensation
[    15.279] (II) Loading extension X-Resource
[    15.279] (II) LoadModule: "dbe"
[    15.280] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.280] (II) Module dbe: vendor="X.Org Foundation"
[    15.280] 	compiled for 1.11.2.902, module version = 1.0.0
[    15.280] 	Module class: X.Org Server Extension
[    15.280] 	ABI class: X.Org Server Extension, version 6.0
[    15.280] (II) Loading extension DOUBLE-BUFFER
[    15.280] (II) LoadModule: "glx"
[    15.280] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    15.280] (II) Module glx: vendor="X.Org Foundation"
[    15.280] 	compiled for 1.11.2.902, module version = 1.0.0
[    15.280] 	ABI class: X.Org Server Extension, version 6.0
[    15.280] (==) AIGLX enabled
[    15.280] (II) Loading extension GLX
[    15.280] (II) LoadModule: "record"
[    15.281] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.281] (II) Module record: vendor="X.Org Foundation"
[    15.281] 	compiled for 1.11.2.902, module version = 1.13.0
[    15.281] 	Module class: X.Org Server Extension
[    15.281] 	ABI class: X.Org Server Extension, version 6.0
[    15.281] (II) Loading extension RECORD
[    15.281] (II) LoadModule: "dri"
[    15.281] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.281] (II) Module dri: vendor="X.Org Foundation"
[    15.281] 	compiled for 1.11.2.902, module version = 1.0.0
[    15.281] 	ABI class: X.Org Server Extension, version 6.0
[    15.281] (II) Loading extension XFree86-DRI
[    15.281] (II) LoadModule: "dri2"
[    15.281] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.281] (II) Module dri2: vendor="X.Org Foundation"
[    15.281] 	compiled for 1.11.2.902, module version = 1.2.0
[    15.281] 	ABI class: X.Org Server Extension, version 6.0
[    15.281] (II) Loading extension DRI2
[    15.281] (==) Matched intel as autoconfigured driver 0
[    15.281] (==) Matched vesa as autoconfigured driver 1
[    15.281] (==) Matched fbdev as autoconfigured driver 2
[    15.281] (==) Assigned the driver to the xf86ConfigLayout
[    15.281] (II) LoadModule: "intel"
[    15.295] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    15.295] (II) Module intel: vendor="X.Org Foundation"
[    15.295] 	compiled for 1.11.2.902, module version = 2.18.0
[    15.295] 	Module class: X.Org Video Driver
[    15.295] 	ABI class: X.Org Video Driver, version 11.0
[    15.295] (II) LoadModule: "vesa"
[    15.296] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.296] (II) Module vesa: vendor="X.Org Foundation"
[    15.296] 	compiled for 1.11.2.902, module version = 2.3.1
[    15.296] 	Module class: X.Org Video Driver
[    15.296] 	ABI class: X.Org Video Driver, version 11.0
[    15.296] (II) LoadModule: "fbdev"
[    15.296] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.296] (II) Module fbdev: vendor="X.Org Foundation"
[    15.296] 	compiled for 1.11.2.902, module version = 0.4.2
[    15.296] 	Module class: X.Org Video Driver
[    15.296] 	ABI class: X.Org Video Driver, version 11.0
[    15.296] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
	Ivybridge Server (GT2)
[    15.297] (II) VESA: driver for VESA chipsets: vesa
[    15.297] (II) FBDEV: driver for framebuffer: fbdev
[    15.297] (++) using VT number 7

[    15.299] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    15.299] (WW) Falling back to old probe method for vesa
[    15.299] (WW) Falling back to old probe method for fbdev
[    15.299] (II) Loading sub module "fbdevhw"
[    15.299] (II) LoadModule: "fbdevhw"
[    15.299] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.299] (II) Module fbdevhw: vendor="X.Org Foundation"
[    15.299] 	compiled for 1.11.2.902, module version = 0.0.2
[    15.299] 	ABI class: X.Org Video Driver, version 11.0
[    15.299] drmOpenDevice: node name is /dev/dri/card0
[    15.300] drmOpenDevice: open result is 9, (OK)
[    15.300] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    15.300] drmOpenDevice: node name is /dev/dri/card0
[    15.300] drmOpenDevice: open result is 9, (OK)
[    15.300] drmOpenByBusid: drmOpenMinor returns 9
[    15.300] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    15.300] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    15.300] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    15.300] (==) intel(0): RGB weight 888
[    15.300] (==) intel(0): Default visual is TrueColor
[    15.300] (II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[    15.300] (--) intel(0): Chipset: "965GM"
[    15.300] (**) intel(0): Relaxed fencing enabled
[    15.300] (**) intel(0): Wait on SwapBuffers? enabled
[    15.300] (**) intel(0): Triple buffering? enabled
[    15.300] (**) intel(0): Framebuffer tiled
[    15.300] (**) intel(0): Pixmaps tiled
[    15.300] (**) intel(0): 3D buffers tiled
[    15.300] (**) intel(0): SwapBuffers wait enabled
[    15.300] (==) intel(0): video overlay key set to 0x101fe
[    15.320] (II) intel(0): Output VGA1 has no monitor section
[    15.554] (II) intel(0): Output HDMI1 has no monitor section
[    15.576] (II) intel(0): EDID for output VGA1
[    15.810] (II) intel(0): EDID for output HDMI1
[    15.810] (II) intel(0): Manufacturer: SNY  Model: f8  Serial#: 16843009
[    15.810] (II) intel(0): Year: 2002  Week: 0
[    15.810] (II) intel(0): EDID Version: 1.3
[    15.810] (II) intel(0): Digital Display Input
[    15.810] (II) intel(0): Indeterminate output size
[    15.811] (II) intel(0): Gamma: 2.20
[    15.811] (II) intel(0): No DPMS capabilities specified
[    15.811] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    15.811] (II) intel(0): First detailed timing is preferred mode
[    15.811] (II) intel(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
[    15.811] (II) intel(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
[    15.811] (II) intel(0): Supported established timings:
[    15.811] (II) intel(0): 640x480@60Hz
[    15.811] (II) intel(0): Manufacturer's mask: 0
[    15.811] (II) intel(0): Supported detailed timing:
[    15.811] (II) intel(0): clock: 74.2 MHz   Image Size:  0 x 0 mm
[    15.811] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    15.811] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    15.811] (II) intel(0): Supported detailed timing:
[    15.811] (II) intel(0): clock: 27.0 MHz   Image Size:  0 x 0 mm
[    15.811] (II) intel(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    15.811] (II) intel(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    15.811] (II) intel(0): Monitor name: SONY TV
[    15.811] (II) intel(0): Ranges: V min: 59 V max: 61 Hz, H min: 15 H max: 46 kHz, PixClock max 85 MHz
[    15.811] (II) intel(0): Supported detailed timing:
[    15.811] (II) intel(0): clock: 74.2 MHz   Image Size:  0 x 0 mm
[    15.811] (II) intel(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    15.811] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    15.811] (II) intel(0): Supported detailed timing:
[    15.811] (II) intel(0): clock: 27.0 MHz   Image Size:  0 x 0 mm
[    15.811] (II) intel(0): h_active: 1440  h_sync: 1478  h_sync_end 1602 h_blank_end 1716 h_border: 0
[    15.811] (II) intel(0): v_active: 240  v_sync: 244  v_sync_end 247 v_blanking: 262 v_border: 0
[    15.811] (II) intel(0): Unknown vendor-specific block 1
[    15.811] (II) intel(0): Number of EDID sections to follow: 1
[    15.811] (II) intel(0): EDID (in hex):
[    15.811] (II) intel(0): 	00ffffffffffff004dd9f80001010101
[    15.811] (II) intel(0): 	000c0103800000780a0dc9a057479827
[    15.811] (II) intel(0): 	12484c20000001010101010101010101
[    15.811] (II) intel(0): 	010101010101011d8018711c1620582c
[    15.811] (II) intel(0): 	250000000000009e8c0ad08a20e02d10
[    15.811] (II) intel(0): 	103e9600000000000018000000fc0053
[    15.811] (II) intel(0): 	4f4e592054560a2020202020000000fd
[    15.811] (II) intel(0): 	003b3d0f2e08000a2020202020200102
[    15.811] (II) intel(0): 	02010400011d007251d01e206e285500
[    15.811] (II) intel(0): 	00000000001e8c0aa01451f01600267c
[    15.811] (II) intel(0): 	43000000000000980000000100525631
[    15.811] (II) intel(0): 	2e30304856312e30300a000000000000
[    15.811] (II) intel(0): 	00000000000000000000000000000000
[    15.811] (II) intel(0): 	00000000000000000000000000000000
[    15.811] (II) intel(0): 	00000000000000000000000000000000
[    15.811] (II) intel(0): 	00000000000000000000000000000014
[    15.811] (II) intel(0): Printing probed modes for output HDMI1
[    15.811] (II) intel(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    15.811] (II) intel(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    15.811] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.811] (II) intel(0): Output VGA1 disconnected
[    15.811] (II) intel(0): Output HDMI1 connected
[    15.811] (II) intel(0): Using fuzzy aspect match for initial modes
[    15.811] (II) intel(0): Output HDMI1 using initial mode 640x480
[    15.811] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    15.811] (II) intel(0): Kernel page flipping support detected, enabling
[    15.811] (==) intel(0): DPI set to (96, 96)
[    15.811] (II) Loading sub module "fb"
[    15.811] (II) LoadModule: "fb"
[    15.812] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.812] (II) Module fb: vendor="X.Org Foundation"
[    15.812] 	compiled for 1.11.2.902, module version = 1.0.0
[    15.812] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.812] (II) Loading sub module "dri2"
[    15.812] (II) LoadModule: "dri2"
[    15.812] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.812] (II) Module dri2: vendor="X.Org Foundation"
[    15.812] 	compiled for 1.11.2.902, module version = 1.2.0
[    15.812] 	ABI class: X.Org Server Extension, version 6.0
[    15.812] (II) UnloadModule: "vesa"
[    15.812] (II) Unloading vesa
[    15.812] (II) UnloadModule: "fbdev"
[    15.812] (II) Unloading fbdev
[    15.812] (II) UnloadModule: "fbdevhw"
[    15.812] (II) Unloading fbdevhw
[    15.812] (==) Depth 24 pixmap format is 32 bpp
[    15.812] (II) intel(0): [DRI2] Setup complete
[    15.812] (II) intel(0): [DRI2]   DRI driver: i965
[    15.813] (II) intel(0): Allocated new frame buffer 640x480 stride 2560, tiled
[    15.826] (II) UXA(0): Driver registered support for the following operations:
[    15.826] (II)         solid
[    15.826] (II)         copy
[    15.826] (II)         composite (RENDER acceleration)
[    15.826] (II)         put_image
[    15.826] (II)         get_image
[    15.826] (==) intel(0): Backing store disabled
[    15.826] (==) intel(0): Silken mouse enabled
[    15.826] (II) intel(0): Initializing HW Cursor
[    15.826] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    15.826] (==) intel(0): DPMS enabled
[    15.826] (==) intel(0): Intel XvMC decoder enabled
[    15.826] (II) intel(0): Set up textured video
[    15.826] (II) intel(0): Set up overlay video
[    15.826] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    15.826] (II) intel(0): direct rendering: DRI2 Enabled
[    15.826] (==) intel(0): hotplug detection: "enabled"
[    16.013] (--) RandR disabled
[    16.013] (II) Initializing built-in extension Generic Event Extension
[    16.013] (II) Initializing built-in extension SHAPE
[    16.013] (II) Initializing built-in extension MIT-SHM
[    16.013] (II) Initializing built-in extension XInputExtension
[    16.013] (II) Initializing built-in extension XTEST
[    16.013] (II) Initializing built-in extension BIG-REQUESTS
[    16.013] (II) Initializing built-in extension SYNC
[    16.013] (II) Initializing built-in extension XKEYBOARD
[    16.013] (II) Initializing built-in extension XC-MISC
[    16.013] (II) Initializing built-in extension SECURITY
[    16.013] (II) Initializing built-in extension XINERAMA
[    16.013] (II) Initializing built-in extension XFIXES
[    16.013] (II) Initializing built-in extension RENDER
[    16.013] (II) Initializing built-in extension RANDR
[    16.013] (II) Initializing built-in extension COMPOSITE
[    16.013] (II) Initializing built-in extension DAMAGE
[    16.025] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/i965_dri.so
[    16.121] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    16.121] (II) AIGLX: enabled GLX_INTEL_swap_event
[    16.121] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    16.121] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    16.121] (II) AIGLX: Loaded and initialized i965
[    16.121] (II) GLX: Initialized DRI2 GL provider for screen 0
[    16.122] (II) intel(0): Setting screen physical size to 169 x 126
[    16.138] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.142] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    16.142] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.142] (II) LoadModule: "evdev"
[    16.143] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.143] (II) Module evdev: vendor="X.Org Foundation"
[    16.143] 	compiled for 1.11.2.902, module version = 2.6.99
[    16.143] 	Module class: X.Org XInput Driver
[    16.143] 	ABI class: X.Org XInput driver, version 13.0
[    16.143] (II) Using input driver 'evdev' for 'Power Button'
[    16.143] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.143] (**) Power Button: always reports core events
[    16.143] (**) evdev: Power Button: Device: "/dev/input/event1"
[    16.143] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.143] (--) evdev: Power Button: Found keys
[    16.143] (II) evdev: Power Button: Configuring as keyboard
[    16.143] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    16.143] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    16.143] (**) Option "xkb_rules" "evdev"
[    16.143] (**) Option "xkb_model" "pc105"
[    16.143] (**) Option "xkb_layout" "us"
[    16.144] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    16.144] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.144] (II) Using input driver 'evdev' for 'Power Button'
[    16.144] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.144] (**) Power Button: always reports core events
[    16.144] (**) evdev: Power Button: Device: "/dev/input/event0"
[    16.144] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.144] (--) evdev: Power Button: Found keys
[    16.144] (II) evdev: Power Button: Configuring as keyboard
[    16.144] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    16.144] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    16.144] (**) Option "xkb_rules" "evdev"
[    16.144] (**) Option "xkb_model" "pc105"
[    16.144] (**) Option "xkb_layout" "us"
[    16.144] (II) config/udev: Adding input device PS/2+USB Mouse (/dev/input/event2)
[    16.144] (**) PS/2+USB Mouse: Applying InputClass "evdev pointer catchall"
[    16.144] (II) Using input driver 'evdev' for 'PS/2+USB Mouse'
[    16.144] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.145] (**) PS/2+USB Mouse: always reports core events
[    16.145] (**) evdev: PS/2+USB Mouse: Device: "/dev/input/event2"
[    16.145] (--) evdev: PS/2+USB Mouse: Vendor 0x1267 Product 0x201
[    16.145] (--) evdev: PS/2+USB Mouse: Found 3 mouse buttons
[    16.145] (--) evdev: PS/2+USB Mouse: Found scroll wheel(s)
[    16.145] (--) evdev: PS/2+USB Mouse: Found relative axes
[    16.145] (--) evdev: PS/2+USB Mouse: Found x and y relative axes
[    16.145] (II) evdev: PS/2+USB Mouse: Configuring as mouse
[    16.145] (II) evdev: PS/2+USB Mouse: Adding scrollwheel support
[    16.145] (**) evdev: PS/2+USB Mouse: YAxisMapping: buttons 4 and 5
[    16.145] (**) evdev: PS/2+USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.145] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input2/event2"
[    16.145] (II) XINPUT: Adding extended input device "PS/2+USB Mouse" (type: MOUSE, id 8)
[    16.145] (II) evdev: PS/2+USB Mouse: initialized for relative axes.
[    16.145] (**) PS/2+USB Mouse: (accel) keeping acceleration scheme 1
[    16.145] (**) PS/2+USB Mouse: (accel) acceleration profile 0
[    16.145] (**) PS/2+USB Mouse: (accel) acceleration factor: 2.000
[    16.145] (**) PS/2+USB Mouse: (accel) acceleration threshold: 4
[    16.145] (II) config/udev: Adding input device PS/2+USB Mouse (/dev/input/mouse0)
[    16.145] (II) No input driver/identifier specified (ignoring)
[    16.146] (II) config/udev: Adding input device DELL DELL USB Keyboard (/dev/input/event3)
[    16.146] (**) DELL DELL USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    16.146] (II) Using input driver 'evdev' for 'DELL DELL USB Keyboard'
[    16.146] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.146] (**) DELL DELL USB Keyboard: always reports core events
[    16.146] (**) evdev: DELL DELL USB Keyboard: Device: "/dev/input/event3"
[    16.146] (--) evdev: DELL DELL USB Keyboard: Vendor 0x413c Product 0x2005
[    16.146] (--) evdev: DELL DELL USB Keyboard: Found keys
[    16.146] (II) evdev: DELL DELL USB Keyboard: Configuring as keyboard
[    16.146] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input3/event3"
[    16.146] (II) XINPUT: Adding extended input device "DELL DELL USB Keyboard" (type: KEYBOARD, id 9)
[    16.146] (**) Option "xkb_rules" "evdev"
[    16.146] (**) Option "xkb_model" "pc105"
[    16.146] (**) Option "xkb_layout" "us"
[    16.146] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event6)
[    16.147] (II) No input driver/identifier specified (ignoring)
[    16.147] (II) config/udev: Adding input device Logitech 2.4GHz Cordless Desktop (/dev/input/event4)
[    16.147] (**) Logitech 2.4GHz Cordless Desktop: Applying InputClass "evdev keyboard catchall"
[    16.147] (II) Using input driver 'evdev' for 'Logitech 2.4GHz Cordless Desktop'
[    16.147] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.147] (**) Logitech 2.4GHz Cordless Desktop: always reports core events
[    16.147] (**) evdev: Logitech 2.4GHz Cordless Desktop: Device: "/dev/input/event4"
[    16.147] (--) evdev: Logitech 2.4GHz Cordless Desktop: Vendor 0x46d Product 0xc52a
[    16.147] (--) evdev: Logitech 2.4GHz Cordless Desktop: Found keys
[    16.147] (II) evdev: Logitech 2.4GHz Cordless Desktop: Configuring as keyboard
[    16.147] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input4/event4"
[    16.147] (II) XINPUT: Adding extended input device "Logitech 2.4GHz Cordless Desktop" (type: KEYBOARD, id 10)
[    16.147] (**) Option "xkb_rules" "evdev"
[    16.147] (**) Option "xkb_model" "pc105"
[    16.147] (**) Option "xkb_layout" "us"
[    16.148] (II) config/udev: Adding input device Logitech 2.4GHz Cordless Desktop (/dev/input/event5)
[    16.148] (**) Logitech 2.4GHz Cordless Desktop: Applying InputClass "evdev pointer catchall"
[    16.148] (**) Logitech 2.4GHz Cordless Desktop: Applying InputClass "evdev keyboard catchall"
[    16.148] (II) Using input driver 'evdev' for 'Logitech 2.4GHz Cordless Desktop'
[    16.148] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.148] (**) Logitech 2.4GHz Cordless Desktop: always reports core events
[    16.148] (**) evdev: Logitech 2.4GHz Cordless Desktop: Device: "/dev/input/event5"
[    16.148] (--) evdev: Logitech 2.4GHz Cordless Desktop: Vendor 0x46d Product 0xc52a
[    16.148] (--) evdev: Logitech 2.4GHz Cordless Desktop: Found 12 mouse buttons
[    16.148] (--) evdev: Logitech 2.4GHz Cordless Desktop: Found scroll wheel(s)
[    16.148] (--) evdev: Logitech 2.4GHz Cordless Desktop: Found relative axes
[    16.148] (--) evdev: Logitech 2.4GHz Cordless Desktop: Found x and y relative axes
[    16.148] (--) evdev: Logitech 2.4GHz Cordless Desktop: Found absolute axes
[    16.148] (--) evdev: Logitech 2.4GHz Cordless Desktop: Found keys
[    16.148] (II) evdev: Logitech 2.4GHz Cordless Desktop: Configuring as mouse
[    16.148] (II) evdev: Logitech 2.4GHz Cordless Desktop: Configuring as keyboard
[    16.148] (II) evdev: Logitech 2.4GHz Cordless Desktop: Adding scrollwheel support
[    16.148] (**) evdev: Logitech 2.4GHz Cordless Desktop: YAxisMapping: buttons 4 and 5
[    16.148] (**) evdev: Logitech 2.4GHz Cordless Desktop: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.148] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.1/input/input5/event5"
[    16.148] (II) XINPUT: Adding extended input device "Logitech 2.4GHz Cordless Desktop" (type: KEYBOARD, id 11)
[    16.148] (**) Option "xkb_rules" "evdev"
[    16.148] (**) Option "xkb_model" "pc105"
[    16.148] (**) Option "xkb_layout" "us"
[    16.148] (II) evdev: Logitech 2.4GHz Cordless Desktop: initialized for relative axes.
[    16.148] (WW) evdev: Logitech 2.4GHz Cordless Desktop: ignoring absolute axes.
[    16.149] (**) Logitech 2.4GHz Cordless Desktop: (accel) keeping acceleration scheme 1
[    16.149] (**) Logitech 2.4GHz Cordless Desktop: (accel) acceleration profile 0
[    16.149] (**) Logitech 2.4GHz Cordless Desktop: (accel) acceleration factor: 2.000
[    16.149] (**) Logitech 2.4GHz Cordless Desktop: (accel) acceleration threshold: 4
[    16.149] (II) config/udev: Adding input device Logitech 2.4GHz Cordless Desktop (/dev/input/mouse1)
[    16.149] (II) No input driver/identifier specified (ignoring)
[    17.078] (II) intel(0): EDID vendor "SNY", prod id 248
[    17.078] (II) intel(0): Using EDID range info for horizontal sync
[    17.078] (II) intel(0): Using EDID range info for vertical refresh
[    17.078] (II) intel(0): Printing DDC gathered Modelines:
[    17.078] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    17.078] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    17.078] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    17.078] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    17.078] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.334] (II) intel(0): EDID vendor "SNY", prod id 248
[    17.334] (II) intel(0): Using hsync ranges from config file
[    17.334] (II) intel(0): Using vrefresh ranges from config file
[    17.334] (II) intel(0): Printing DDC gathered Modelines:
[    17.334] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    17.334] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    17.334] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    17.334] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    17.334] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.032] (II) intel(0): EDID vendor "SNY", prod id 248
[    18.032] (II) intel(0): Using hsync ranges from config file
[    18.032] (II) intel(0): Using vrefresh ranges from config file
[    18.032] (II) intel(0): Printing DDC gathered Modelines:
[    18.032] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    18.032] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    18.032] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    18.032] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    18.032] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    20.890] (II) intel(0): EDID vendor "SNY", prod id 248
[    20.890] (II) intel(0): Using hsync ranges from config file
[    20.890] (II) intel(0): Using vrefresh ranges from config file
[    20.890] (II) intel(0): Printing DDC gathered Modelines:
[    20.890] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    20.890] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    20.890] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    20.890] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    20.890] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    21.147] (II) intel(0): EDID vendor "SNY", prod id 248
[    21.147] (II) intel(0): Using hsync ranges from config file
[    21.147] (II) intel(0): Using vrefresh ranges from config file
[    21.147] (II) intel(0): Printing DDC gathered Modelines:
[    21.147] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    21.147] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    21.147] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    21.147] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    21.147] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
```

---

### Post by BicyclerBoy on 2012-04-03
Your TV's HD mode is 1080i60.

The i915 driver has/did have a bugs where it can not do interlaced video modes over HDMI. This may only be with sandybridge..

Can you try to use a VGA cable, the video modes available could be more limited but it might work..

I don't think the GM965 is good enough for HD video playback.

---

### Post by danBhentschel on 2012-04-04
Okay, so last night I tried to install the latest Intel drivers as per the instructions here:

[http://intellinuxgraphics.org/2012.02.html](http://intellinuxgraphics.org/2012.02.html)

The first step is to update the kernel to 3.2... I followed instructions here:

[http://www.unixmen.com/how-to-upgrade-to-kernel-3-2-in-ubuntu11-10-and-linuxmint12/](http://www.unixmen.com/how-to-upgrade-to-kernel-3-2-in-ubuntu11-10-and-linuxmint12/)

All seemed to go well, but after reboot, the system would lock after about 10-15 seconds of uptime, every time, even when booting just to a command prompt (recovery mode).

After this, I completely gave up. I went back to my big, clunky box with an nVidia card in it. I was able to do a full wipe/reinstall of Ubuntu in under 60 minutes to a fully working system on my TV. I'm sticking with this for now.

Maybe I'll try the Studio Hybrid again when the next version of Mythbuntu is released. For now, the support for the GM965 is much too immature for me to be able to use it. I've spent too much time already. It's not just the 1080i on my TV that's causing it. I eventually settled on using 720p (1280x720) with my nVidia card. I would have been happy with this resolution on the Dell, but I couldn't get it to go there. Also, I tried using it on another LCD TV. This one supported 1080p, and it booted up in that resolution, but everything was all green.  Again, I spent a little time trying to figure this one out...

Sorry for venting. I do appreciate people taking the time to try to help.

 - dan

---


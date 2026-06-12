---
title: "Upgraded CPU and GPU, no video playback."
date: 2013-01-09
forum: Multimedia Software
---

### Post by groverj3 on 2013-01-09
Hello all,

I try to avoid posting about problems as much as possible, but I'm out of ideas.

I recently upgraded my aging Intel Atom and Nvidia ION-based HTPC to an i3 3225 with the integrated HD4000 graphics. To my surprise, my computer booted after that big of a hardware change (benefits of having intel graphics support in the kernel I suppose). Everything seems to be going well except video playback in xbmc and vlc.

I removed the Nvidia drivers and installed the va-api ones, but some videos crash either program immediately when they start playing. If I disable hardware acceleration then they play fine. I'd rather have the GPU core doing the work though, and I believe it should work, right?

Hardware:
Asus P8H77-I Motherboard
Intel i3-3225 with HD4000 gpu
4gb DDR3 1600 ram
LG Blu ray drive
430 watt corsair PSU

Running xubuntu 12.04

Pretty minimal hardware (and probably not at all helpful).

Any ideas on how to get this functioning correctly?

Edit: I have also removed my old xorg.conf as well.

---

### Post by UltimateCat on 2013-01-09
Hi:

You probably need flash.
[http://www.wikihow.com/Install-Flash-Player-on-Ubuntu](http://www.wikihow.com/Install-Flash-Player-on-Ubuntu)

Here is a video that should help.
[http://www.youtube.com/watch?v=3HAgUCh5qoM](http://www.youtube.com/watch?v=3HAgUCh5qoM)

[http://ubuntuforums.org/showthread.php?t=2083599](http://ubuntuforums.org/showthread.php?t=2083599)

Hope this helps

---

### Post by groverj3 on 2013-01-10
Thanks for the quick response, but I already have working flash since I was able to use my existing xubuntu install on my HD.

It seems to me that I have a system-wide problem with gpu acceleration-enabled programs still looking for my old Nvidia stuff. However, I don't know why... since I purged all the nvidia drivers, I believe.

Luckily the new CPU is fast enough to handle video decoding on it's own, but this isn't ideal.

---

### Post by groverj3 on 2013-01-10
Looking through synaptic reveals that I still have nvidia-common installed. When I try to remove it, it informs me that I then also need to remove xubuntu-desktop.

That sounds like a bad idea and something that would leave me without a desktop environment. Correct me if I'm wrong...

---

### Post by Yellow Pasque on 2013-01-10
> t informs me that I then also need to remove xubuntu-desktop. That sounds like a bad idea and something that would leave me without a desktop environment. Correct me if I'm wrong...
You're wrong. :P xubuntu-desktop is just a metapackage depending on all of the packages that make up a Xubuntu install. It's actually safe to remove, but nvidia-common is not the nvidia driver, so don't worry about it.

Post your /var/log/Xorg.0.log

---

### Post by groverj3 on 2013-01-10
> **Temüjin said:**
> You're wrong. :P xubuntu-desktop is just a metapackage depending on all of the packages that make up a Xubuntu install. It's actually safe to remove, but nvidia-common is not the nvidia driver, so don't worry about it.

Post your /var/log/Xorg.0.log

That's good to know.

Here's the Xorg.0.log you requested:

```
[    20.606] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    20.606] X Protocol Version 11, Revision 0
[    20.606] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[    20.606] Current Operating System: Linux jeff-htpc 3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:45:18 UTC 2012 i686
[    20.606] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-35-generic root=UUID=4a5f4e0b-bea1-4dd6-9fb4-9ca839e827ae ro quiet splash vt.handoff=7
[    20.606] Build Date: 29 August 2012  12:10:05AM
[    20.606] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[    20.606] Current version of pixman: 0.24.4
[    20.606] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    20.606] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.606] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan 10 16:47:01 2013
[    20.619] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.620] (==) No Layout section.  Using the first Screen section.
[    20.620] (==) No screen section available. Using defaults.
[    20.620] (**) |-->Screen "Default Screen Section" (0)
[    20.620] (**) |   |-->Monitor "<default monitor>"
[    20.620] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    20.620] (==) Automatically adding devices
[    20.620] (==) Automatically enabling devices
[    20.620] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.620] 	Entry deleted from font path.
[    20.620] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.620] 	Entry deleted from font path.
[    20.620] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.620] 	Entry deleted from font path.
[    20.620] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.620] 	Entry deleted from font path.
[    20.620] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.620] 	Entry deleted from font path.
[    20.620] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    20.620] 	Entry deleted from font path.
[    20.620] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    20.620] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.620] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.620] (II) Loader magic: 0xfd65a0
[    20.620] (II) Module ABI versions:
[    20.620] 	X.Org ANSI C Emulation: 0.4
[    20.620] 	X.Org Video Driver: 11.0
[    20.620] 	X.Org XInput driver : 16.0
[    20.620] 	X.Org Server Extension : 6.0
[    20.620] (--) PCI:*(0:0:2:0) 8086:0162:1043:84ca rev 9, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[    20.620] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.620] (II) LoadModule: "extmod"
[    20.639] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.639] (II) Module extmod: vendor="X.Org Foundation"
[    20.639] 	compiled for 1.11.3, module version = 1.0.0
[    20.639] 	Module class: X.Org Server Extension
[    20.639] 	ABI class: X.Org Server Extension, version 6.0
[    20.639] (II) Loading extension MIT-SCREEN-SAVER
[    20.639] (II) Loading extension XFree86-VidModeExtension
[    20.639] (II) Loading extension XFree86-DGA
[    20.639] (II) Loading extension DPMS
[    20.639] (II) Loading extension XVideo
[    20.639] (II) Loading extension XVideo-MotionCompensation
[    20.639] (II) Loading extension X-Resource
[    20.639] (II) LoadModule: "dbe"
[    20.639] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.639] (II) Module dbe: vendor="X.Org Foundation"
[    20.639] 	compiled for 1.11.3, module version = 1.0.0
[    20.639] 	Module class: X.Org Server Extension
[    20.639] 	ABI class: X.Org Server Extension, version 6.0
[    20.639] (II) Loading extension DOUBLE-BUFFER
[    20.639] (II) LoadModule: "glx"
[    20.640] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.663] (II) Module glx: vendor="X.Org Foundation"
[    20.663] 	compiled for 1.11.3, module version = 1.0.0
[    20.663] 	ABI class: X.Org Server Extension, version 6.0
[    20.663] (==) AIGLX enabled
[    20.663] (II) Loading extension GLX
[    20.663] (II) LoadModule: "record"
[    20.663] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    20.663] (II) Module record: vendor="X.Org Foundation"
[    20.663] 	compiled for 1.11.3, module version = 1.13.0
[    20.663] 	Module class: X.Org Server Extension
[    20.663] 	ABI class: X.Org Server Extension, version 6.0
[    20.663] (II) Loading extension RECORD
[    20.663] (II) LoadModule: "dri"
[    20.663] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    20.663] (II) Module dri: vendor="X.Org Foundation"
[    20.663] 	compiled for 1.11.3, module version = 1.0.0
[    20.663] 	ABI class: X.Org Server Extension, version 6.0
[    20.663] (II) Loading extension XFree86-DRI
[    20.663] (II) LoadModule: "dri2"
[    20.663] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.663] (II) Module dri2: vendor="X.Org Foundation"
[    20.663] 	compiled for 1.11.3, module version = 1.2.0
[    20.663] 	ABI class: X.Org Server Extension, version 6.0
[    20.663] (II) Loading extension DRI2
[    20.663] (==) Matched intel as autoconfigured driver 0
[    20.663] (==) Matched vesa as autoconfigured driver 1
[    20.663] (==) Matched fbdev as autoconfigured driver 2
[    20.663] (==) Assigned the driver to the xf86ConfigLayout
[    20.663] (II) LoadModule: "intel"
[    20.672] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    20.695] (II) Module intel: vendor="X.Org Foundation"
[    20.695] 	compiled for 1.11.3, module version = 2.17.0
[    20.695] 	Module class: X.Org Video Driver
[    20.695] 	ABI class: X.Org Video Driver, version 11.0
[    20.695] (II) LoadModule: "vesa"
[    20.695] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.714] (II) Module vesa: vendor="X.Org Foundation"
[    20.714] 	compiled for 1.11.3, module version = 2.3.0
[    20.714] 	Module class: X.Org Video Driver
[    20.714] 	ABI class: X.Org Video Driver, version 11.0
[    20.714] (II) LoadModule: "fbdev"
[    20.714] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.726] (II) Module fbdev: vendor="X.Org Foundation"
[    20.726] 	compiled for 1.11.3, module version = 0.4.2
[    20.726] 	ABI class: X.Org Video Driver, version 11.0
[    20.726] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    20.726] (II) VESA: driver for VESA chipsets: vesa
[    20.726] (II) FBDEV: driver for framebuffer: fbdev
[    20.726] (++) using VT number 7

[    20.727] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    20.727] (WW) Falling back to old probe method for vesa
[    20.727] (WW) Falling back to old probe method for fbdev
[    20.727] (II) Loading sub module "fbdevhw"
[    20.727] (II) LoadModule: "fbdevhw"
[    20.728] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.733] (II) Module fbdevhw: vendor="X.Org Foundation"
[    20.733] 	compiled for 1.11.3, module version = 0.0.2
[    20.733] 	ABI class: X.Org Video Driver, version 11.0
[    20.733] drmOpenDevice: node name is /dev/dri/card0
[    20.733] drmOpenDevice: open result is 9, (OK)
[    20.733] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    20.733] drmOpenDevice: node name is /dev/dri/card0
[    20.733] drmOpenDevice: open result is 9, (OK)
[    20.733] drmOpenByBusid: drmOpenMinor returns 9
[    20.733] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    20.733] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    20.733] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    20.733] (==) intel(0): RGB weight 888
[    20.734] (==) intel(0): Default visual is TrueColor
[    20.734] (II) intel(0): Integrated Graphics Chipset: Intel(R) Ivybridge Desktop (GT2)
[    20.734] (--) intel(0): Chipset: "Ivybridge Desktop (GT2)"
[    20.734] (**) intel(0): Relaxed fencing enabled
[    20.734] (**) intel(0): Wait on SwapBuffers? enabled
[    20.734] (**) intel(0): Triple buffering? enabled
[    20.734] (**) intel(0): Framebuffer tiled
[    20.734] (**) intel(0): Pixmaps tiled
[    20.734] (**) intel(0): 3D buffers tiled
[    20.734] (**) intel(0): SwapBuffers wait enabled
[    20.734] (==) intel(0): video overlay key set to 0x101fe
[    20.734] (II) intel(0): Output VGA1 has no monitor section
[    20.738] (II) intel(0): Output HDMI1 has no monitor section
[    20.968] (II) intel(0): Output HDMI2 has no monitor section
[    21.016] (II) intel(0): Output DP1 has no monitor section
[    21.064] (II) intel(0): Output DP2 has no monitor section
[    21.064] (II) intel(0): EDID for output VGA1
[    21.068] (II) intel(0): EDID for output HDMI1
[    21.299] (II) intel(0): EDID for output HDMI2
[    21.299] (II) intel(0): Manufacturer: ONK  Model: c33  Serial#: 0
[    21.299] (II) intel(0): Year: 2012  Week: 0
[    21.299] (II) intel(0): EDID Version: 1.3
[    21.299] (II) intel(0): Digital Display Input
[    21.299] (II) intel(0): Max Image Size [cm]: horiz.: 89  vert.: 50
[    21.299] (II) intel(0): Gamma: 2.20
[    21.299] (II) intel(0): No DPMS capabilities specified
[    21.299] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    21.299] (II) intel(0): First detailed timing is preferred mode
[    21.299] (II) intel(0): redX: 0.640 redY: 0.335   greenX: 0.285 greenY: 0.605
[    21.299] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.280 whiteY: 0.290
[    21.299] (II) intel(0): Supported established timings:
[    21.299] (II) intel(0): 640x480@60Hz
[    21.299] (II) intel(0): 800x600@60Hz
[    21.299] (II) intel(0): 1024x768@60Hz
[    21.299] (II) intel(0): Manufacturer's mask: 0
[    21.299] (II) intel(0): Supported standard timings:
[    21.300] (II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    21.300] (II) intel(0): #1: hsize: 1360  vsize 765  refresh: 60  vid: 49291
[    21.300] (II) intel(0): Supported detailed timing:
[    21.300] (II) intel(0): clock: 148.5 MHz   Image Size:  886 x 498 mm
[    21.300] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    21.300] (II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    21.300] (II) intel(0): Supported detailed timing:
[    21.300] (II) intel(0): clock: 85.5 MHz   Image Size:  886 x 498 mm
[    21.300] (II) intel(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
[    21.300] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
[    21.300] (II) intel(0): Monitor name: HT-R391
[    21.300] (II) intel(0): Ranges: V min: 23 V max: 61 Hz, H min: 15 H max: 68 kHz, PixClock max 155 MHz
[    21.300] (II) intel(0): Supported detailed timing:
[    21.300] (II) intel(0): clock: 74.2 MHz   Image Size:  886 x 498 mm
[    21.300] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    21.300] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    21.300] (II) intel(0): Supported detailed timing:
[    21.300] (II) intel(0): clock: 74.2 MHz   Image Size:  886 x 498 mm
[    21.300] (II) intel(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    21.300] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    21.300] (II) intel(0): Supported detailed timing:
[    21.300] (II) intel(0): clock: 27.0 MHz   Image Size:  886 x 498 mm
[    21.300] (II) intel(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    21.300] (II) intel(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    21.300] (II) intel(0): Number of EDID sections to follow: 1
[    21.300] (II) intel(0): EDID (in hex):
[    21.300] (II) intel(0): 	00ffffffffffff003dcb330c00000000
[    21.300] (II) intel(0): 	00160103805932780af09da355499b26
[    21.300] (II) intel(0): 	0f474a21080081808bc0010101010101
[    21.300] (II) intel(0): 	010101010101023a801871382d40582c
[    21.300] (II) intel(0): 	450076f23100001e662150b051001b30
[    21.300] (II) intel(0): 	4070360076f23100001e000000fc0048
[    21.300] (II) intel(0): 	542d523339310a2020202020000000fd
[    21.300] (II) intel(0): 	00173d0f440f000a2020202020200162
[    21.300] (II) intel(0): 	02033e714f9001020304050607200e0f
[    21.300] (II) intel(0): 	0a0b232438097f070d7f071707503f06
[    21.300] (II) intel(0): 	c04d02005706005f7e01675400830f00
[    21.300] (II) intel(0): 	006c030c0012008021c015151f1f011d
[    21.300] (II) intel(0): 	8018711c1620582c250076f23100009e
[    21.300] (II) intel(0): 	011d007251d01e206e28550076f23100
[    21.300] (II) intel(0): 	001e8c0ad08a20e02d10103e960076f2
[    21.300] (II) intel(0): 	31000018000000000000000000000012
[    21.300] (II) intel(0): Printing probed modes for output HDMI2
[    21.300] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    21.300] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    21.300] (II) intel(0): Modeline "1360x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    21.300] (II) intel(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    21.300] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    21.300] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    21.300] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    21.348] (II) intel(0): EDID for output DP1
[    21.396] (II) intel(0): EDID for output DP2
[    21.396] (II) intel(0): Output VGA1 disconnected
[    21.396] (II) intel(0): Output HDMI1 disconnected
[    21.396] (II) intel(0): Output HDMI2 connected
[    21.396] (II) intel(0): Output DP1 disconnected
[    21.396] (II) intel(0): Output DP2 disconnected
[    21.396] (II) intel(0): Using exact sizes for initial modes
[    21.396] (II) intel(0): Output HDMI2 using initial mode 1920x1080
[    21.396] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    21.396] (II) intel(0): Kernel page flipping support detected, enabling
[    21.396] (==) intel(0): DPI set to (96, 96)
[    21.396] (II) Loading sub module "fb"
[    21.396] (II) LoadModule: "fb"
[    21.396] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.412] (II) Module fb: vendor="X.Org Foundation"
[    21.412] 	compiled for 1.11.3, module version = 1.0.0
[    21.412] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.412] (II) Loading sub module "dri2"
[    21.412] (II) LoadModule: "dri2"
[    21.412] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.412] (II) Module dri2: vendor="X.Org Foundation"
[    21.412] 	compiled for 1.11.3, module version = 1.2.0
[    21.412] 	ABI class: X.Org Server Extension, version 6.0
[    21.412] (II) UnloadModule: "vesa"
[    21.412] (II) Unloading vesa
[    21.412] (II) UnloadModule: "fbdev"
[    21.412] (II) Unloading fbdev
[    21.412] (II) UnloadModule: "fbdevhw"
[    21.412] (II) Unloading fbdevhw
[    21.412] (==) Depth 24 pixmap format is 32 bpp
[    21.412] (II) intel(0): [DRI2] Setup complete
[    21.412] (II) intel(0): [DRI2]   DRI driver: i965
[    21.412] (II) intel(0): Allocated new frame buffer 1920x1080 stride 7680, tiled
[    21.413] (II) UXA(0): Driver registered support for the following operations:
[    21.413] (II)         solid
[    21.413] (II)         copy
[    21.413] (II)         composite (RENDER acceleration)
[    21.413] (II)         put_image
[    21.413] (II)         get_image
[    21.413] (==) intel(0): Backing store disabled
[    21.413] (==) intel(0): Silken mouse enabled
[    21.413] (II) intel(0): Initializing HW Cursor
[    21.472] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.472] (==) intel(0): DPMS enabled
[    21.472] (==) intel(0): Intel XvMC decoder enabled
[    21.472] (II) intel(0): Set up textured video
[    21.472] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    21.472] (II) intel(0): direct rendering: DRI2 Enabled
[    21.472] (==) intel(0): hotplug detection: "enabled"
[    21.472] (--) RandR disabled
[    21.472] (II) Initializing built-in extension Generic Event Extension
[    21.472] (II) Initializing built-in extension SHAPE
[    21.472] (II) Initializing built-in extension MIT-SHM
[    21.472] (II) Initializing built-in extension XInputExtension
[    21.472] (II) Initializing built-in extension XTEST
[    21.472] (II) Initializing built-in extension BIG-REQUESTS
[    21.472] (II) Initializing built-in extension SYNC
[    21.472] (II) Initializing built-in extension XKEYBOARD
[    21.472] (II) Initializing built-in extension XC-MISC
[    21.472] (II) Initializing built-in extension SECURITY
[    21.472] (II) Initializing built-in extension XINERAMA
[    21.472] (II) Initializing built-in extension XFIXES
[    21.472] (II) Initializing built-in extension RENDER
[    21.472] (II) Initializing built-in extension RANDR
[    21.472] (II) Initializing built-in extension COMPOSITE
[    21.472] (II) Initializing built-in extension DAMAGE
[    21.578] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    21.578] (II) AIGLX: enabled GLX_INTEL_swap_event
[    21.578] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    21.578] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    21.578] (II) AIGLX: Loaded and initialized i965
[    21.578] (II) GLX: Initialized DRI2 GL provider for screen 0
[    21.578] (II) intel(0): Setting screen physical size to 507 x 285
[    21.583] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.585] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    21.585] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.585] (II) LoadModule: "evdev"
[    21.585] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.585] (II) Module evdev: vendor="X.Org Foundation"
[    21.585] 	compiled for 1.11.3, module version = 2.7.0
[    21.585] 	Module class: X.Org XInput Driver
[    21.585] 	ABI class: X.Org XInput driver, version 16.0
[    21.585] (II) Using input driver 'evdev' for 'Power Button'
[    21.585] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.585] (**) Power Button: always reports core events
[    21.585] (**) evdev: Power Button: Device: "/dev/input/event1"
[    21.585] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.585] (--) evdev: Power Button: Found keys
[    21.585] (II) evdev: Power Button: Configuring as keyboard
[    21.585] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    21.585] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    21.585] (**) Option "xkb_rules" "evdev"
[    21.585] (**) Option "xkb_model" "pc105"
[    21.585] (**) Option "xkb_layout" "us"
[    21.585] (II) config/udev: Adding input device Video Bus (/dev/input/event11)
[    21.585] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    21.585] (II) Using input driver 'evdev' for 'Video Bus'
[    21.585] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.586] (**) Video Bus: always reports core events
[    21.586] (**) evdev: Video Bus: Device: "/dev/input/event11"
[    21.586] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    21.586] (--) evdev: Video Bus: Found keys
[    21.586] (II) evdev: Video Bus: Configuring as keyboard
[    21.586] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input11/event11"
[    21.586] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    21.586] (**) Option "xkb_rules" "evdev"
[    21.586] (**) Option "xkb_model" "pc105"
[    21.586] (**) Option "xkb_layout" "us"
[    21.586] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    21.586] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.586] (II) Using input driver 'evdev' for 'Power Button'
[    21.586] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.586] (**) Power Button: always reports core events
[    21.586] (**) evdev: Power Button: Device: "/dev/input/event0"
[    21.586] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.586] (--) evdev: Power Button: Found keys
[    21.586] (II) evdev: Power Button: Configuring as keyboard
[    21.586] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    21.586] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    21.586] (**) Option "xkb_rules" "evdev"
[    21.586] (**) Option "xkb_model" "pc105"
[    21.586] (**) Option "xkb_layout" "us"
[    21.586] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    21.586] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    21.586] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    21.586] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.586] (**) Logitech USB Receiver: always reports core events
[    21.586] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event2"
[    21.586] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc517
[    21.586] (--) evdev: Logitech USB Receiver: Found keys
[    21.586] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    21.587] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input2/event2"
[    21.587] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 9)
[    21.587] (**) Option "xkb_rules" "evdev"
[    21.587] (**) Option "xkb_model" "pc105"
[    21.587] (**) Option "xkb_layout" "us"
[    21.587] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    21.587] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    21.587] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    21.587] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    21.587] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.587] (**) Logitech USB Receiver: always reports core events
[    21.587] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event3"
[    21.587] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc517
[    21.587] (--) evdev: Logitech USB Receiver: Found 12 mouse buttons
[    21.587] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    21.587] (--) evdev: Logitech USB Receiver: Found relative axes
[    21.587] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[    21.587] (--) evdev: Logitech USB Receiver: Found absolute axes
[    21.587] (II) evdev: Logitech USB Receiver: Forcing absolute x/y axes to exist.
[    21.587] (--) evdev: Logitech USB Receiver: Found keys
[    21.587] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    21.587] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    21.587] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    21.587] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    21.587] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.587] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.1/input/input3/event3"
[    21.587] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 10)
[    21.587] (**) Option "xkb_rules" "evdev"
[    21.587] (**) Option "xkb_model" "pc105"
[    21.587] (**) Option "xkb_layout" "us"
[    21.587] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    21.587] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.
[    21.588] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    21.588] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    21.588] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    21.588] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    21.588] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    21.588] (II) No input driver specified, ignoring this device.
[    21.588] (II) This device may have been added with another device file.
[    21.588] (II) config/udev: Adding input device HDA Intel PCH Line-Out (/dev/input/event10)
[    21.588] (II) No input driver specified, ignoring this device.
[    21.588] (II) This device may have been added with another device file.
[    21.588] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event5)
[    21.588] (II) No input driver specified, ignoring this device.
[    21.588] (II) This device may have been added with another device file.
[    21.588] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event6)
[    21.588] (II) No input driver specified, ignoring this device.
[    21.588] (II) This device may have been added with another device file.
[    21.588] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event7)
[    21.588] (II) No input driver specified, ignoring this device.
[    21.588] (II) This device may have been added with another device file.
[    21.588] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event8)
[    21.588] (II) No input driver specified, ignoring this device.
[    21.588] (II) This device may have been added with another device file.
[    21.589] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event9)
[    21.589] (II) No input driver specified, ignoring this device.
[    21.589] (II) This device may have been added with another device file.
[    21.589] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event4)
[    21.589] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    21.589] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[    21.589] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.589] (**) Eee PC WMI hotkeys: always reports core events
[    21.589] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event4"
[    21.589] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[    21.589] (--) evdev: Eee PC WMI hotkeys: Found keys
[    21.589] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[    21.589] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input4/event4"
[    21.589] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 11)
[    21.589] (**) Option "xkb_rules" "evdev"
[    21.589] (**) Option "xkb_model" "pc105"
[    21.589] (**) Option "xkb_layout" "us"
[    27.164] (II) intel(0): EDID vendor "ONK", prod id 3123
[    27.164] (II) intel(0): Using EDID range info for horizontal sync
[    27.164] (II) intel(0): Using EDID range info for vertical refresh
[    27.164] (II) intel(0): Printing DDC gathered Modelines:
[    27.164] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    27.164] (II) intel(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    27.164] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    27.164] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    27.164] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    27.164] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    27.164] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.164] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.164] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    27.164] (II) intel(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    27.164] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    27.164] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    27.164] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    27.164] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    27.164] (II) intel(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz)
[    27.164] (II) intel(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    27.164] (II) intel(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz)
[    27.164] (II) intel(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz)
[    27.164] (II) intel(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz)
[    27.494] (II) intel(0): EDID vendor "ONK", prod id 3123
[    27.494] (II) intel(0): Using hsync ranges from config file
[    27.494] (II) intel(0): Using vrefresh ranges from config file
[    27.494] (II) intel(0): Printing DDC gathered Modelines:
[    27.494] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    27.494] (II) intel(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    27.494] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    27.494] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    27.494] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    27.494] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    27.494] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.494] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.494] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    27.494] (II) intel(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    27.494] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    27.494] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    27.494] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    27.494] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    27.494] (II) intel(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz)
[    27.494] (II) intel(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    27.494] (II) intel(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz)
[    27.494] (II) intel(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz)
[    27.494] (II) intel(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz)
[    27.877] (II) intel(0): EDID vendor "ONK", prod id 3123
[    27.918] (II) intel(0): Using hsync ranges from config file
[    27.918] (II) intel(0): Using vrefresh ranges from config file
[    27.918] (II) intel(0): Printing DDC gathered Modelines:
[    27.918] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    27.918] (II) intel(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    27.918] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    27.918] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    27.918] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    27.918] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    27.918] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.918] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.918] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    27.918] (II) intel(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    27.918] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    27.918] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    27.918] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    27.918] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    27.918] (II) intel(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz)
[    27.918] (II) intel(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    27.918] (II) intel(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz)
[    27.918] (II) intel(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz)
[    27.918] (II) intel(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz)
[    28.263] (II) intel(0): EDID vendor "ONK", prod id 3123
[    28.263] (II) intel(0): Using hsync ranges from config file
[    28.263] (II) intel(0): Using vrefresh ranges from config file
[    28.263] (II) intel(0): Printing DDC gathered Modelines:
[    28.263] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    28.263] (II) intel(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    28.263] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    28.263] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    28.263] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    28.263] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    28.263] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    28.263] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    28.263] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    28.263] (II) intel(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    28.263] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    28.263] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    28.263] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    28.263] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    28.263] (II) intel(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz)
[    28.263] (II) intel(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    28.263] (II) intel(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz)
[    28.263] (II) intel(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz)
[    28.263] (II) intel(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz)
[    28.597] (II) intel(0): EDID vendor "ONK", prod id 3123
[    28.597] (II) intel(0): Using hsync ranges from config file
[    28.597] (II) intel(0): Using vrefresh ranges from config file
[    28.598] (II) intel(0): Printing DDC gathered Modelines:
[    28.598] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    28.598] (II) intel(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    28.598] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    28.598] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    28.598] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    28.598] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    28.598] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    28.598] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    28.598] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    28.598] (II) intel(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    28.598] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    28.598] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    28.598] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    28.598] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    28.598] (II) intel(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz)
[    28.598] (II) intel(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    28.598] (II) intel(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz)
[    28.598] (II) intel(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz)
[    28.598] (II) intel(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz)

```

Hopefully that helps.

---

### Post by groverj3 on 2013-01-10
I should also add that I've narrowed the problem down a bit. As of right now, only 3 programs crash for me. XBMC, VLC, and PCSX2.

Everything else I've tried that seems to have gpu acceleration enabled runs fine.

I tried reinstalling those 3 programs as well, and no difference (not that I expected there to be). I'm stumped, but I'd rather not have to do a clean install of the OS to fix this, but I'm thinking of transitioning to a SSD for the OS and using the 1tb HDD for media. I suppose it wouldn't be the end of the world.

---

### Post by groverj3 on 2013-01-11
Did some digging.

I'm not the only one who can't get intel chips to work with hardware acceleration in xbmc. Apparently the package in both the ubuntu repos and xbmc ones is broken and doesn't support vaapi.

The VLC in 12.04 was quite outdated as well. That's now working with an update.

---


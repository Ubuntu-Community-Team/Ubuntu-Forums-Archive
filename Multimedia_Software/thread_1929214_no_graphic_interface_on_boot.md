---
title: "no graphic interface on boot"
date: 2012-02-21
forum: Multimedia Software
---

### Post by ADani on 2012-02-21
Hello, I am running kubuntu 11.04 on a ASUS X44H laptop. I can't get a graphic interface (can upgrading some packages have killed my configuration?). Now when I boot I go straight to command line. Trying to reset with ctrl+shift+f7 does nothing.
I would have changed from intel card to vesa but I have no xorg.conf, and I don't even know if that is the problem.

I've tried selecting the "graphic failsafe" option from boot but it does nothing, it returns me to the selection list.

I'm lost here, thanks

---

### Post by wyliecoyoteuk on 2012-02-21
What happens if you type
```

startx

```

---

### Post by ADani on 2012-02-21
Here's what i get:

```

X.Org X Server 1.10.1
Release Date: 2011-04-15
[    33.273] X Protocol Version 11, Revision 0
[    33.273] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    33.273] Current Operating System: Linux dani-K84L 2.6.38-13-generic #55-Ubuntu SMP Tue Jan 24 14:27:59 UTC 2012 i686
[    33.273] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-13-generic root=UUID=e6ded479-1dbf-464e-a7af-8a2044d5a1dd ro quiet splash vt.handoff=7
[    33.273] Build Date: 13 October 2011  05:38:22PM
[    33.273] xorg-server 2:1.10.1-1ubuntu1.3 (For technical support please see http://www.ubuntu.com/support) 
[    33.273] Current version of pixman: 0.20.2
[    33.273] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    33.273] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    33.274] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 21 18:12:01 2012
[    33.274] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    33.274] (==) No Layout section.  Using the first Screen section.
[    33.274] (==) No screen section available. Using defaults.
[    33.274] (**) |-->Screen "Default Screen Section" (0)
[    33.274] (**) |   |-->Monitor "<default monitor>"
[    33.274] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    33.274] (==) Automatically adding devices
[    33.274] (==) Automatically enabling devices
[    33.274] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    33.274] 	Entry deleted from font path.
[    33.274] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    33.274] 	Entry deleted from font path.
[    33.274] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    33.274] 	Entry deleted from font path.
[    33.274] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    33.274] 	Entry deleted from font path.
[    33.274] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    33.274] 	Entry deleted from font path.
[    33.274] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    33.274] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    33.274] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    33.274] (II) Loader magic: 0x8200ac0
[    33.275] (II) Module ABI versions:
[    33.275] 	X.Org ANSI C Emulation: 0.4
[    33.275] 	X.Org Video Driver: 10.0
[    33.275] 	X.Org XInput driver : 12.3
[    33.275] 	X.Org Server Extension : 5.0
[    33.275] (--) PCI:*(0:0:2:0) 8086:0106:1043:13d7 rev 9, Mem @ 0xdd000000/4194304, 0xc0000000/268435456, I/O @ 0x0000e000/64
[    33.275] (II) Open ACPI successful (/var/run/acpid.socket)
[    33.275] (II) LoadModule: "extmod"
[    33.275] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    33.276] (II) Module extmod: vendor="X.Org Foundation"
[    33.276] 	compiled for 1.10.1, module version = 1.0.0
[    33.276] 	Module class: X.Org Server Extension
[    33.276] 	ABI class: X.Org Server Extension, version 5.0
[    33.276] (II) Loading extension MIT-SCREEN-SAVER
[    33.276] (II) Loading extension XFree86-VidModeExtension
[    33.276] (II) Loading extension XFree86-DGA
[    33.276] (II) Loading extension DPMS
[    33.276] (II) Loading extension XVideo
[    33.276] (II) Loading extension XVideo-MotionCompensation
[    33.276] (II) Loading extension X-Resource
[    33.276] (II) LoadModule: "dbe"
[    33.276] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    33.276] (II) Module dbe: vendor="X.Org Foundation"
[    33.276] 	compiled for 1.10.1, module version = 1.0.0
[    33.276] 	Module class: X.Org Server Extension
[    33.276] 	ABI class: X.Org Server Extension, version 5.0
[    33.276] (II) Loading extension DOUBLE-BUFFER
[    33.276] (II) LoadModule: "glx"
[    33.276] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    33.276] (II) Module glx: vendor="X.Org Foundation"
[    33.276] 	compiled for 1.10.1, module version = 1.0.0
[    33.276] 	ABI class: X.Org Server Extension, version 5.0
[    33.276] (==) AIGLX enabled
[    33.276] (II) Loading extension GLX
[    33.276] (II) LoadModule: "record"
[    33.276] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    33.276] (II) Module record: vendor="X.Org Foundation"
[    33.276] 	compiled for 1.10.1, module version = 1.13.0
[    33.276] 	Module class: X.Org Server Extension
[    33.276] 	ABI class: X.Org Server Extension, version 5.0
[    33.276] (II) Loading extension RECORD
[    33.276] (II) LoadModule: "dri"
[    33.276] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    33.277] (II) Module dri: vendor="X.Org Foundation"
[    33.277] 	compiled for 1.10.1, module version = 1.0.0
[    33.277] 	ABI class: X.Org Server Extension, version 5.0
[    33.277] (II) Loading extension XFree86-DRI
[    33.277] (II) LoadModule: "dri2"
[    33.277] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    33.277] (II) Module dri2: vendor="X.Org Foundation"
[    33.277] 	compiled for 1.10.1, module version = 1.2.0
[    33.277] 	ABI class: X.Org Server Extension, version 5.0
[    33.277] (II) Loading extension DRI2
[    33.277] (==) Matched intel as autoconfigured driver 0
[    33.277] (==) Matched vesa as autoconfigured driver 1
[    33.277] (==) Matched fbdev as autoconfigured driver 2
[    33.277] (==) Assigned the driver to the xf86ConfigLayout
[    33.277] (II) LoadModule: "intel"
[    33.277] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    33.277] (II) Module intel: vendor="X.Org Foundation"
[    33.277] 	compiled for 1.10.1, module version = 2.14.0
[    33.277] 	Module class: X.Org Video Driver
[    33.277] 	ABI class: X.Org Video Driver, version 10.0
[    33.277] (II) LoadModule: "vesa"
[    33.278] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    33.278] (II) Module vesa: vendor="X.Org Foundation"
[    33.278] 	compiled for 1.10.0, module version = 2.3.0
[    33.278] 	Module class: X.Org Video Driver
[    33.278] 	ABI class: X.Org Video Driver, version 10.0
[    33.278] (II) LoadModule: "fbdev"
[    33.278] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    33.278] (II) Module fbdev: vendor="X.Org Foundation"
[    33.278] 	compiled for 1.10.0, module version = 0.4.2
[    33.278] 	ABI class: X.Org Video Driver, version 10.0
[    33.278] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    33.278] (II) VESA: driver for VESA chipsets: vesa
[    33.278] (II) FBDEV: driver for framebuffer: fbdev
[    33.278] (--) using VT number 7

[    33.284] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    33.284] (WW) Falling back to old probe method for vesa
[    33.284] (WW) Falling back to old probe method for fbdev
[    33.284] (II) Loading sub module "fbdevhw"
[    33.284] (II) LoadModule: "fbdevhw"
[    33.284] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    33.284] (II) Module fbdevhw: vendor="X.Org Foundation"
[    33.284] 	compiled for 1.10.1, module version = 0.0.2
[    33.284] 	ABI class: X.Org Video Driver, version 10.0
[    33.284] drmOpenDevice: node name is /dev/dri/card0
[    33.284] drmOpenDevice: open result is 9, (OK)
[    33.284] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    33.284] drmOpenDevice: node name is /dev/dri/card0
[    33.284] drmOpenDevice: open result is 9, (OK)
[    33.284] drmOpenByBusid: drmOpenMinor returns 9
[    33.284] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    33.284] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    33.284] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    33.284] (==) intel(0): RGB weight 888
[    33.284] (==) intel(0): Default visual is TrueColor
[    33.284] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge
[    33.284] (--) intel(0): Chipset: "Sandybridge"
[    33.284] (**) intel(0): Relaxed fencing enabled
[    33.284] (**) intel(0): Tiling enabled
[    33.284] (**) intel(0): SwapBuffers wait disabled
[    33.284] (==) intel(0): video overlay key set to 0x101fe
[    33.284] (II) intel(0): Output LVDS1 has no monitor section
[    33.284] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    33.284] (II) intel(0): Output VGA1 has no monitor section
[    33.289] (II) intel(0): Output HDMI1 has no monitor section
[    33.290] (II) intel(0): Output DP1 has no monitor section
[    33.290] (II) intel(0): EDID for output LVDS1
[    33.290] (II) intel(0): Manufacturer: CMI  Model: 1b  Serial#: 0
[    33.290] (II) intel(0): Year: 2010  Week: 0
[    33.290] (II) intel(0): EDID Version: 1.3
[    33.290] (II) intel(0): Digital Display Input
[    33.290] (II) intel(0): Max Image Size [cm]: horiz.: 31  vert.: 18
[    33.290] (II) intel(0): Gamma: 2.20
[    33.290] (II) intel(0): No DPMS capabilities specified
[    33.290] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    33.290] (II) intel(0): First detailed timing is preferred mode
[    33.290] (II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[    33.290] (II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[    33.290] (II) intel(0): Manufacturer's mask: 0
[    33.290] (II) intel(0): Supported detailed timing:
[    33.290] (II) intel(0): clock: 71.0 MHz   Image Size:  309 x 174 mm
[    33.290] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1498 h_border: 0
[    33.290] (II) intel(0): v_active: 768  v_sync: 769  v_sync_end 773 v_blanking: 790 v_border: 0
[    33.290] (II) intel(0): Unknown vendor-specific block 0
[    33.290] (II) intel(0):  CMI
[    33.290] (II) intel(0):  BT140GW01V9
[    33.290] (II) intel(0): EDID (in hex):
[    33.290] (II) intel(0): 	00ffffffffffff000da91b0000000000
[    33.290] (II) intel(0): 	00140103801f12780a87f594574f8c27
[    33.290] (II) intel(0): 	27505400000001010101010101010101
[    33.290] (II) intel(0): 	010101010101bc1b5684500016303020
[    33.290] (II) intel(0): 	140035ae100000180000000000202020
[    33.290] (II) intel(0): 	20202020202020202020000000fe0043
[    33.290] (II) intel(0): 	4d490a202020202020202020000000fe
[    33.290] (II) intel(0): 	0042543134304757303156390a20006e
[    33.291] (II) intel(0): EDID vendor "CMI", prod id 27
[    33.291] (II) intel(0): Printing DDC gathered Modelines:
[    33.291] (II) intel(0): Modeline "1366x768"x0.0   71.00  1366 1414 1446 1498  768 769 773 790 -hsync -vsync (47.4 kHz)
[    33.291] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    33.291] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    33.291] (II) intel(0): Printing probed modes for output LVDS1
[    33.291] (II) intel(0): Modeline "1366x768"x60.0   71.00  1366 1414 1446 1498  768 769 773 790 -hsync -vsync (47.4 kHz)
[    33.291] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    33.291] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    33.291] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    33.291] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    33.291] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    33.291] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    33.291] (II) intel(0): EDID for output VGA1
[    33.296] (II) intel(0): EDID for output HDMI1
[    33.297] (II) intel(0): EDID for output DP1
[    33.297] (II) intel(0): Output LVDS1 connected
[    33.297] (II) intel(0): Output VGA1 disconnected
[    33.297] (II) intel(0): Output HDMI1 disconnected
[    33.297] (II) intel(0): Output DP1 disconnected
[    33.297] (II) intel(0): Using exact sizes for initial modes
[    33.297] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    33.297] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    33.297] (II) intel(0): Kernel page flipping support detected, enabling
[    33.297] (**) intel(0): Display dimensions: (310, 180) mm
[    33.297] (**) intel(0): DPI set to (111, 108)
[    33.297] (II) Loading sub module "fb"
[    33.297] (II) LoadModule: "fb"
[    33.297] (II) Loading /usr/lib/xorg/modules/libfb.so
[    33.297] (II) Module fb: vendor="X.Org Foundation"
[    33.297] 	compiled for 1.10.1, module version = 1.0.0
[    33.297] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    33.297] (II) UnloadModule: "vesa"
[    33.297] (II) Unloading vesa
[    33.297] (II) UnloadModule: "fbdev"
[    33.297] (II) Unloading fbdev
[    33.297] (II) UnloadModule: "fbdevhw"
[    33.297] (II) Unloading fbdevhw
[    33.297] (==) Depth 24 pixmap format is 32 bpp
[    33.297] (==) intel(0): VideoRam: 262144 KB
[    33.297] (II) intel(0): [DRI2] Setup complete
[    33.297] (II) intel(0): [DRI2]   DRI driver: i965
[    33.297] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    33.298] (II) UXA(0): Driver registered support for the following operations:
[    33.298] (II)         solid
[    33.298] (II)         copy
[    33.298] (II)         composite (RENDER acceleration)
[    33.298] (II)         put_image
[    33.298] (II)         get_image
[    33.298] (==) intel(0): Backing store disabled
[    33.298] (==) intel(0): Silken mouse enabled
[    33.299] (II) intel(0): Initializing HW Cursor
[    33.360] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    33.361] (==) intel(0): DPMS enabled
[    33.361] (==) intel(0): Intel XvMC decoder enabled
[    33.361] (II) intel(0): Set up textured video
[    33.361] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    33.361] (II) intel(0): direct rendering: DRI2 Enabled
[    33.361] (==) intel(0): hotplug detection: "enabled"
[    33.361] (--) RandR disabled
[    33.361] (II) Initializing built-in extension Generic Event Extension
[    33.361] (II) Initializing built-in extension SHAPE
[    33.361] (II) Initializing built-in extension MIT-SHM
[    33.361] (II) Initializing built-in extension XInputExtension
[    33.361] (II) Initializing built-in extension XTEST
[    33.361] (II) Initializing built-in extension BIG-REQUESTS
[    33.361] (II) Initializing built-in extension SYNC
[    33.361] (II) Initializing built-in extension XKEYBOARD
[    33.361] (II) Initializing built-in extension XC-MISC
[    33.361] (II) Initializing built-in extension SECURITY
[    33.361] (II) Initializing built-in extension XINERAMA
[    33.361] (II) Initializing built-in extension XFIXES
[    33.361] (II) Initializing built-in extension RENDER
[    33.361] (II) Initializing built-in extension RANDR
[    33.361] (II) Initializing built-in extension COMPOSITE
[    33.361] (II) Initializing built-in extension DAMAGE
[    33.361] (II) Initializing built-in extension GESTURE
[    33.370] (II) AIGLX: Trying DRI driver /usr/lib/dri/i965_dri.so
[    33.373] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    33.373] (II) AIGLX: enabled GLX_INTEL_swap_event
[    33.373] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    33.373] (II) AIGLX: enabled GLX_SGI_make_current_read
[    33.373] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    33.373] (II) AIGLX: Loaded and initialized i965
[    33.373] (II) GLX: Initialized DRI2 GL provider for screen 0
[    33.374] (II) intel(0): Setting screen physical size to 361 x 203
[    33.382] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    33.503] (EE) Error compiling keymap (-)
[    33.504] (EE) XKB: Couldn't compile keymap
[    33.504] (EE) XKB: Failed to load keymap. Loading default keymap instead.
[    33.506] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    33.523] (EE) Error compiling keymap (-)
[    33.523] (EE) XKB: Couldn't compile keymap
[    33.523] XKB: Failed to compile keymap
[    33.523] Keyboard initialization failed. This could be a missing or incorrect setup of xkeyboard-config.
[    33.523] 
Fatal server error:
[    33.523] Failed to activate core devices.
[    33.523] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    33.523] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    33.523] 
[    33.523] (II) AIGLX: Suspending AIGLX clients for VT switch
[    33.582]  ddxSigGiveUp: Closing log
```

thank you for the fast reply

---

### Post by wyliecoyoteuk on 2012-02-27
Sorry to take so long replying.
Looks like the Xserver is failing at the keyboard stage, which might suggest a lightDM problem. I'm no X expert,I'm afraid.
In a similar situation, I ended up copying my files off with a liveCD and reinstalling.

---

### Post by ADani on 2012-02-27
Thanks for taking a look. It's weird because the keyboard works just fine.
I'm going to mess with xorg.conf.d before giving in to reinstalling.
thanks

---

### Post by ADani on 2012-02-27
I tried forcing vesa with a new conf file in usr/share/X11/xorg.conf.d that had:
Section "Device"
	Identifier "Device0"
	Driver "vesa"
EndSection


The result is the same, but now it says it can't find the screen :confused:

```
[    57.250] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    57.250] X Protocol Version 11, Revision 0
[    57.250] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    57.250] Current Operating System: Linux dani-K84L 2.6.38-13-generic #55-Ubuntu SMP Tue Jan 24 14:27:59 UTC 2012 i686
[    57.250] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-13-generic root=UUID=e6ded479-1dbf-464e-a7af-8a2044d5a1dd ro quiet splash vt.handoff=7
[    57.250] Build Date: 13 October 2011  05:38:22PM
[    57.250] xorg-server 2:1.10.1-1ubuntu1.3 (For technical support please see http://www.ubuntu.com/support) 
[    57.250] Current version of pixman: 0.20.2
[    57.250] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    57.250] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    57.251] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb 27 18:49:09 2012
[    57.251] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    57.251] (==) No Layout section.  Using the first Screen section.
[    57.251] (==) No screen section available. Using defaults.
[    57.251] (**) |-->Screen "Default Screen Section" (0)
[    57.251] (**) |   |-->Monitor "<default monitor>"
[    57.251] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    57.251] (**) |   |-->Device "Device0"
[    57.251] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    57.251] (==) Automatically adding devices
[    57.251] (==) Automatically enabling devices
[    57.251] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    57.251] 	Entry deleted from font path.
[    57.251] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    57.251] 	Entry deleted from font path.
[    57.251] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    57.251] 	Entry deleted from font path.
[    57.251] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    57.251] 	Entry deleted from font path.
[    57.251] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    57.251] 	Entry deleted from font path.
[    57.251] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    57.251] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    57.251] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    57.251] (II) Loader magic: 0x8200ac0
[    57.251] (II) Module ABI versions:
[    57.251] 	X.Org ANSI C Emulation: 0.4
[    57.251] 	X.Org Video Driver: 10.0
[    57.251] 	X.Org XInput driver : 12.3
[    57.251] 	X.Org Server Extension : 5.0
[    57.252] (--) PCI:*(0:0:2:0) 8086:0106:1043:13d7 rev 9, Mem @ 0xdd000000/4194304, 0xc0000000/268435456, I/O @ 0x0000e000/64
[    57.252] (II) Open ACPI successful (/var/run/acpid.socket)
[    57.252] (II) LoadModule: "extmod"
[    57.253] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    57.253] (II) Module extmod: vendor="X.Org Foundation"
[    57.253] 	compiled for 1.10.1, module version = 1.0.0
[    57.253] 	Module class: X.Org Server Extension
[    57.253] 	ABI class: X.Org Server Extension, version 5.0
[    57.253] (II) Loading extension MIT-SCREEN-SAVER
[    57.253] (II) Loading extension XFree86-VidModeExtension
[    57.253] (II) Loading extension XFree86-DGA
[    57.253] (II) Loading extension DPMS
[    57.253] (II) Loading extension XVideo
[    57.253] (II) Loading extension XVideo-MotionCompensation
[    57.253] (II) Loading extension X-Resource
[    57.253] (II) LoadModule: "dbe"
[    57.253] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    57.253] (II) Module dbe: vendor="X.Org Foundation"
[    57.253] 	compiled for 1.10.1, module version = 1.0.0
[    57.253] 	Module class: X.Org Server Extension
[    57.253] 	ABI class: X.Org Server Extension, version 5.0
[    57.253] (II) Loading extension DOUBLE-BUFFER
[    57.253] (II) LoadModule: "glx"
[    57.253] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    57.253] (II) Module glx: vendor="X.Org Foundation"
[    57.253] 	compiled for 1.10.1, module version = 1.0.0
[    57.253] 	ABI class: X.Org Server Extension, version 5.0
[    57.253] (==) AIGLX enabled
[    57.253] (II) Loading extension GLX
[    57.253] (II) LoadModule: "record"
[    57.253] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    57.253] (II) Module record: vendor="X.Org Foundation"
[    57.253] 	compiled for 1.10.1, module version = 1.13.0
[    57.253] 	Module class: X.Org Server Extension
[    57.253] 	ABI class: X.Org Server Extension, version 5.0
[    57.253] (II) Loading extension RECORD
[    57.253] (II) LoadModule: "dri"
[    57.254] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    57.254] (II) Module dri: vendor="X.Org Foundation"
[    57.254] 	compiled for 1.10.1, module version = 1.0.0
[    57.254] 	ABI class: X.Org Server Extension, version 5.0
[    57.254] (II) Loading extension XFree86-DRI
[    57.254] (II) LoadModule: "dri2"
[    57.254] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    57.254] (II) Module dri2: vendor="X.Org Foundation"
[    57.254] 	compiled for 1.10.1, module version = 1.2.0
[    57.254] 	ABI class: X.Org Server Extension, version 5.0
[    57.254] (II) Loading extension DRI2
[    57.254] (II) LoadModule: "vesa"
[    57.254] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    57.254] (II) Module vesa: vendor="X.Org Foundation"
[    57.254] 	compiled for 1.10.0, module version = 2.3.0
[    57.254] 	Module class: X.Org Video Driver
[    57.254] 	ABI class: X.Org Video Driver, version 10.0
[    57.254] (II) VESA: driver for VESA chipsets: vesa
[    57.254] (--) using VT number 7

[    57.258] (EE) VESA: Kernel modesetting driver in use, refusing to load
[    57.258] (WW) Falling back to old probe method for vesa
[    57.258] (EE) No devices detected.
[    57.258] 
Fatal server error:
[    57.258] no screens found
```

---

### Post by wyliecoyoteuk on 2012-02-27
The keyboard works fine in the CLI, but it is not being correctly configured for X.
I think that causes a failure in the display manager when you try to log in.

---

### Post by ADani on 2012-02-27
I solved it!
Changing from vesa to intel driver in .config gave me some new errors, and searching those errors on google eventually led me to the problem: / was out of space.

I can't understand why it never actually told me it was full and why that caused me to loose my graphics, but it was that.
I traced the problem to some very oversized printer log files, deleted them, rebooted and problem solved.


thank you wyliecoyoteuk for your support and for being on the other side of the line!

---

### Post by wyliecoyoteuk on 2012-02-28
Good news :)
/ being full can cause all sorts of odd problems, usually when a file can't be written.Loga are a common cause.
Some programs cache stuff in /var which can also fill up /.

---

### Post by karlhutt on 2012-03-01
i need help. i have a similar problem: 

i use ubuntu 11.04, 
i changed the option on the ACCESS screen, where you can choose from loading classic ubuntu, or the nicer ubuntu, or recovery console. 
i chose recovery console just to see what happens. 
now my computer turns on directly to the recovery console, and i CANNOT open the grapic mode! 

i tried startx and it tells me 
'fatal IO error 11 (Resource temporarily unavailable) on X server'

i tried alt-shift-f7, and nothing happens..

how can i go back to my graphic mode?
somebody help!!!

thanks.

---

### Post by ADani on 2012-03-02
Hi karlhutt, as you can see I'm hardly an expert here, but in my case the / (root) was full so it showed me only the command line.
I cleared space there by booting from a live CD, so it would let me find the problematic files in my hdd and delete them. That solved my problem. I don't know if it's yours.
You can find out how much free space you have on your partitions by typing
```
df -h
```
and you get somenthing like
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              40G  5.7G   32G  15% /
none                  1.5G  696K  1.5G   1% /dev
none                  1.5G  6.1M  1.5G   1% /dev/shm
none                  1.5G   88K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
/dev/sda8              63G   58G  1.7G  98% /home

```

in my case almost all 40G were being used by some residual printer log files wich I tracked and deleted.

If this is not your case, I would try connecting to the internet by cable and upgrading your system, with the commands
```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```

hope this helps

---


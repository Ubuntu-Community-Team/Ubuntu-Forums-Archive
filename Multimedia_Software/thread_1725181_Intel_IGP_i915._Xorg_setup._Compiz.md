---
title: "Intel IGP i915. Xorg setup. Compiz ?"
date: 2011-04-09
forum: Multimedia Software
---

### Post by komasoftware on 2011-04-09
Hi,

I am yet another poor sucker that bought a Optimus enabled laptop : ASUS N53SV, hybrid graphics Nvidia GT540M and intel IGP i915.
First round, I installed restricted drivers from NVIDIA and lost my GUI. Had to come back in recovery mode.

Next, been reading all info on vga_switcheroo (never got it working), hybrid graphics and so on and son. I already know that the NVIDIA card will be useless for the time being (and long after that). I cannot switch to Nvidia in BIOS and moreover, the Nvidia GPU is writing back to the IGP so only true hybrid support can make this ever work for this hardware.

So I am settling for getting the best out of the IGP. Or at least decent graphics. At the moment, graphics are horrible. Dragging a window on the desktop resutls in painful stuttering with slow redraws.

I don't seem to have an Xorg.conf file. I guess that's where things already go wrong.

Can somebody help me setup my IGP to work properly and maybe even have compiz ?
How do I create a good working xorg configuration for the i915 IGP ?

I'm on Ubuntu 10.10, Linux N53SV 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux

Relevant part of lspci below

thx !!!


Koen

00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 1642
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 48
	Region 0: Memory at dc400000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at e000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 1642
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at db000000 (32-bit, non-prefetchable) [disabled] [size=16M]
	Region 1: Memory at c0000000 (64-bit, prefetchable) [disabled] [size=256M]
	Region 3: Memory at d0000000 (64-bit, prefetchable) [disabled] [size=32M]
	Region 5: I/O ports at d000 [disabled] [size=128]
	Expansion ROM at dc000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel modules: nouveau, nvidiafb

---

### Post by komasoftware on 2011-04-09
created a Xorg file using Xorg -configure
but still lousy graphic performance :


Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "extmod"
	Load  "dri2"
	Load  "record"
	Load  "dbe"
	Load  "glx"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "VideoKey"           	# <i>
	Identifier  "Card0"
	Driver      "nouveau"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card1"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by Yellow Pasque on 2011-04-09
You shouldn't need any xorg.conf for working 3D on i915 (you can verify this by using the LiveCD and seeing if effects work). I'm guessing you never completely removed the nvidia binary driver. Look at /var/log/Xorg.0.log and see if  vendor=NVIDIA for libglx:
```
[ 24.049] (II) Module glx: vendor="NVIDIA Corporation"
[ 24.049] compiled for 4.0.2, module version = 1.0.0
[ 24.049] Module class: X.Org Server Extension
[ 24.049] (II) NVIDIA GLX Module 270.29 Wed Feb 23 16:34:38 PST 2011
```

If so, make sure you completely purge nvidia packages, reinstall libgl and libglx for good measure, and backup/remove the old xorg.conf:
```
sudo apt-get remove --purge nvidia*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

vga_switcheroo should theoretically work with open-source intel and nvidia driver, though the version of nouveau in Maverick is relatively old and doesn't have a lot of acceleration for newer GPU's. The situation should improve in Natty.

---

### Post by komasoftware on 2011-04-09
Thx, tried that, restarted gdm.
Dont see any improvement and desktop effects wont work unfort.

thx for your help anyway

---

### Post by Yellow Pasque on 2011-04-09
Post /var/log/Xorg.0.log

---

### Post by komasoftware on 2011-04-09
```
[ 17293.645] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[ 17293.645] X Protocol Version 11, Revision 0
[ 17293.645] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[ 17293.645] Current Operating System: Linux N53SV 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64
[ 17293.645] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=395a1e3a-3ffc-45c7-b2b1-14c8fdcd46d7 ro quiet splash
[ 17293.646] Build Date: 09 January 2011  12:14:27PM
[ 17293.646] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[ 17293.646] Current version of pixman: 0.18.4
[ 17293.646] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[ 17293.646] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 17293.646] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr  9 21:26:36 2011
[ 17293.646] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 17293.647] (==) No Layout section.  Using the first Screen section.
[ 17293.647] (==) No screen section available. Using defaults.
[ 17293.647] (**) |-->Screen "Default Screen Section" (0)
[ 17293.647] (**) |   |-->Monitor "<default monitor>"
[ 17293.647] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[ 17293.647] (==) Automatically adding devices
[ 17293.647] (==) Automatically enabling devices
[ 17293.647] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 17293.647] 	Entry deleted from font path.
[ 17293.647] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[ 17293.648] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 17293.648] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[ 17293.648] (II) Loader magic: 0x7d17a0
[ 17293.648] (II) Module ABI versions:
[ 17293.648] 	X.Org ANSI C Emulation: 0.4
[ 17293.648] 	X.Org Video Driver: 8.0
[ 17293.648] 	X.Org XInput driver : 11.0
[ 17293.648] 	X.Org Server Extension : 4.0
[ 17293.649] (--) PCI:*(0:0:2:0) 8086:0116:1043:1642 rev 9, Mem @ 0xdc400000/4194304, 0xb0000000/268435456, I/O @ 0x0000e000/64
[ 17293.649] (--) PCI: (0:1:0:0) 10de:0df4:1043:1642 rev 161, Mem @ 0xdb000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[ 17293.649] (II) Open ACPI successful (/var/run/acpid.socket)
[ 17293.650] (II) LoadModule: "extmod"
[ 17293.658] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[ 17293.659] (II) Module extmod: vendor="X.Org Foundation"
[ 17293.659] 	compiled for 1.9.0, module version = 1.0.0
[ 17293.659] 	Module class: X.Org Server Extension
[ 17293.659] 	ABI class: X.Org Server Extension, version 4.0
[ 17293.659] (II) Loading extension MIT-SCREEN-SAVER
[ 17293.659] (II) Loading extension XFree86-VidModeExtension
[ 17293.659] (II) Loading extension XFree86-DGA
[ 17293.659] (II) Loading extension DPMS
[ 17293.659] (II) Loading extension XVideo
[ 17293.659] (II) Loading extension XVideo-MotionCompensation
[ 17293.659] (II) Loading extension X-Resource
[ 17293.659] (II) LoadModule: "dbe"
[ 17293.659] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[ 17293.659] (II) Module dbe: vendor="X.Org Foundation"
[ 17293.659] 	compiled for 1.9.0, module version = 1.0.0
[ 17293.659] 	Module class: X.Org Server Extension
[ 17293.659] 	ABI class: X.Org Server Extension, version 4.0
[ 17293.660] (II) Loading extension DOUBLE-BUFFER
[ 17293.660] (II) LoadModule: "glx"
[ 17293.660] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[ 17293.660] (II) Module glx: vendor="X.Org Foundation"
[ 17293.660] 	compiled for 1.9.0, module version = 1.0.0
[ 17293.660] 	ABI class: X.Org Server Extension, version 4.0
[ 17293.660] (==) AIGLX enabled
[ 17293.660] (II) Loading extension GLX
[ 17293.660] (II) LoadModule: "record"
[ 17293.661] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[ 17293.661] (II) Module record: vendor="X.Org Foundation"
[ 17293.661] 	compiled for 1.9.0, module version = 1.13.0
[ 17293.661] 	Module class: X.Org Server Extension
[ 17293.661] 	ABI class: X.Org Server Extension, version 4.0
[ 17293.661] (II) Loading extension RECORD
[ 17293.661] (II) LoadModule: "dri"
[ 17293.662] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[ 17293.662] (II) Module dri: vendor="X.Org Foundation"
[ 17293.662] 	compiled for 1.9.0, module version = 1.0.0
[ 17293.662] 	ABI class: X.Org Server Extension, version 4.0
[ 17293.662] (II) Loading extension XFree86-DRI
[ 17293.662] (II) LoadModule: "dri2"
[ 17293.662] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 17293.663] (II) Module dri2: vendor="X.Org Foundation"
[ 17293.663] 	compiled for 1.9.0, module version = 1.2.0
[ 17293.663] 	ABI class: X.Org Server Extension, version 4.0
[ 17293.663] (II) Loading extension DRI2
[ 17293.663] (==) Matched intel as autoconfigured driver 0
[ 17293.663] (==) Matched vesa as autoconfigured driver 1
[ 17293.663] (==) Matched fbdev as autoconfigured driver 2
[ 17293.663] (==) Assigned the driver to the xf86ConfigLayout
[ 17293.663] (II) LoadModule: "intel"
[ 17293.663] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[ 17293.664] (II) Module intel: vendor="X.Org Foundation"
[ 17293.664] 	compiled for 1.9.0, module version = 2.14.902
[ 17293.664] 	Module class: X.Org Video Driver
[ 17293.664] 	ABI class: X.Org Video Driver, version 8.0
[ 17293.664] (II) LoadModule: "vesa"
[ 17293.665] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 17293.675] (II) Module vesa: vendor="X.Org Foundation"
[ 17293.675] 	compiled for 1.8.99.905, module version = 2.3.0
[ 17293.675] 	Module class: X.Org Video Driver
[ 17293.675] 	ABI class: X.Org Video Driver, version 8.0
[ 17293.675] (II) LoadModule: "fbdev"
[ 17293.675] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 17293.687] (II) Module fbdev: vendor="X.Org Foundation"
[ 17293.687] 	compiled for 1.8.99.905, module version = 0.4.2
[ 17293.687] 	ABI class: X.Org Video Driver, version 8.0
[ 17293.687] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[ 17293.688] (II) VESA: driver for VESA chipsets: vesa
[ 17293.688] (II) FBDEV: driver for framebuffer: fbdev
[ 17293.688] (--) using VT number 7

[ 17293.695] (WW) Falling back to old probe method for vesa
[ 17293.695] (WW) Falling back to old probe method for fbdev
[ 17293.695] (II) Loading sub module "fbdevhw"
[ 17293.695] (II) LoadModule: "fbdevhw"
[ 17293.696] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[ 17293.696] (II) Module fbdevhw: vendor="X.Org Foundation"
[ 17293.696] 	compiled for 1.9.0, module version = 0.0.2
[ 17293.696] 	ABI class: X.Org Video Driver, version 8.0
[ 17293.696] drmOpenDevice: node name is /dev/dri/card0
[ 17293.696] drmOpenDevice: open result is 9, (OK)
[ 17293.696] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[ 17293.696] drmOpenDevice: node name is /dev/dri/card0
[ 17293.696] drmOpenDevice: open result is 9, (OK)
[ 17293.696] drmOpenByBusid: drmOpenMinor returns 9
[ 17293.696] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[ 17293.696] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[ 17293.696] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[ 17293.696] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[ 17293.696] (==) intel(0): RGB weight 888
[ 17293.696] (==) intel(0): Default visual is TrueColor
[ 17293.697] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge
[ 17293.697] (--) intel(0): Chipset: "Sandybridge"
[ 17293.697] (**) intel(0): Shadow buffer enabled, 2D GPU acceleration disabled.
[ 17293.697] (**) intel(0): Framebuffer tiled
[ 17293.697] (**) intel(0): Pixmaps tiled
[ 17293.697] (**) intel(0): 3D buffers tiled
[ 17293.697] (**) intel(0): SwapBuffers wait disabled
[ 17293.697] (==) intel(0): video overlay key set to 0x101fe
[ 17293.714] (II) intel(0): Output VGA1 has no monitor section
[ 17293.714] (II) intel(0): Output LVDS1 has no monitor section
[ 17293.714] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video1
[ 17293.723] (II) intel(0): Output HDMI1 has no monitor section
[ 17293.724] (II) intel(0): Output DP1 has no monitor section
[ 17293.741] (II) intel(0): EDID for output VGA1
[ 17293.741] (II) intel(0): EDID for output LVDS1
[ 17293.741] (II) intel(0): Manufacturer: AUO  Model: 15ed  Serial#: 0
[ 17293.741] (II) intel(0): Year: 2008  Week: 1
[ 17293.741] (II) intel(0): EDID Version: 1.3
[ 17293.741] (II) intel(0): Digital Display Input
[ 17293.741] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[ 17293.741] (II) intel(0): Gamma: 2.20
[ 17293.741] (II) intel(0): No DPMS capabilities specified
[ 17293.741] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[ 17293.741] (II) intel(0): First detailed timing is preferred mode
[ 17293.741] (II) intel(0): redX: 0.620 redY: 0.340   greenX: 0.330 greenY: 0.570
[ 17293.741] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[ 17293.741] (II) intel(0): Manufacturer's mask: 0
[ 17293.741] (II) intel(0): Supported detailed timing:
[ 17293.741] (II) intel(0): clock: 142.4 MHz   Image Size:  344 x 193 mm
[ 17293.741] (II) intel(0): h_active: 1920  h_sync: 2028  h_sync_end 2076 h_blank_end 2100 h_border: 0
[ 17293.742] (II) intel(0): v_active: 1080  v_sync: 1090  v_sync_end 1100 v_blanking: 1130 v_border: 0
[ 17293.742] (II) intel(0): Unknown vendor-specific block f
[ 17293.742] (II) intel(0):  AUO
[ 17293.742] (II) intel(0):  B156HW01 V5
[ 17293.742] (II) intel(0): EDID (in hex):
[ 17293.742] (II) intel(0): 	00ffffffffffff0006afed1500000000
[ 17293.742] (II) intel(0): 	01120103802213780ac8959e57549226
[ 17293.742] (II) intel(0): 	0f505400000001010101010101010101
[ 17293.742] (II) intel(0): 	010101010101a03780b4703832406c30
[ 17293.742] (II) intel(0): 	aa0058c1100000180000000f00000000
[ 17293.742] (II) intel(0): 	00000000000000000020000000fe0041
[ 17293.742] (II) intel(0): 	554f0a202020202020202020000000fe
[ 17293.742] (II) intel(0): 	004231353648573031205635200a0047
[ 17293.742] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[ 17293.742] (II) intel(0): Printing probed modes for output LVDS1
[ 17293.742] (II) intel(0): Modeline "1920x1080"x60.0  142.40  1920 2028 2076 2100  1080 1090 1100 1130 -hsync -vsync (67.8 kHz)
[ 17293.742] (II) intel(0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz)
[ 17293.742] (II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[ 17293.742] (II) intel(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[ 17293.742] (II) intel(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
[ 17293.742] (II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
[ 17293.742] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[ 17293.742] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[ 17293.742] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[ 17293.742] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[ 17293.742] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[ 17293.742] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[ 17293.742] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[ 17293.742] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[ 17293.742] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[ 17293.742] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[ 17293.751] (II) intel(0): EDID for output HDMI1
[ 17293.752] (II) intel(0): EDID for output DP1
[ 17293.752] (II) intel(0): Output VGA1 disconnected
[ 17293.752] (II) intel(0): Output LVDS1 connected
[ 17293.752] (II) intel(0): Output HDMI1 disconnected
[ 17293.752] (II) intel(0): Output DP1 disconnected
[ 17293.752] (II) intel(0): Using exact sizes for initial modes
[ 17293.752] (II) intel(0): Output LVDS1 using initial mode 1920x1080
[ 17293.752] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[ 17293.752] (II) intel(0): Kernel page flipping support detected, enabling
[ 17293.752] (==) intel(0): DPI set to (96, 96)
[ 17293.752] (II) Loading sub module "fb"
[ 17293.752] (II) LoadModule: "fb"
[ 17293.753] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 17293.753] (II) Module fb: vendor="X.Org Foundation"
[ 17293.753] 	compiled for 1.9.0, module version = 1.0.0
[ 17293.753] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 17293.753] (II) Loading sub module "dri2"
[ 17293.753] (II) LoadModule: "dri2"
[ 17293.753] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[ 17293.753] (II) UnloadModule: "vesa"
[ 17293.753] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 17293.753] (II) UnloadModule: "fbdev"
[ 17293.753] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 17293.753] (II) UnloadModule: "fbdevhw"
[ 17293.753] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[ 17293.753] (==) Depth 24 pixmap format is 32 bpp
[ 17293.753] (II) intel(0): [DRI2] Setup complete
[ 17293.753] (II) intel(0): [DRI2]   DRI driver: i965
[ 17293.753] (II) intel(0): Allocated new frame buffer 1920x1080 stride 7680, tiled
[ 17293.754] (II) UXA(0): Driver registered support for the following operations:
[ 17293.754] (II)         solid
[ 17293.754] (II)         copy
[ 17293.754] (II)         composite (RENDER acceleration)
[ 17293.754] (II)         put_image
[ 17293.754] (II)         get_image
[ 17293.754] (==) intel(0): Backing store disabled
[ 17293.754] (==) intel(0): Silken mouse enabled
[ 17293.754] (II) intel(0): Initializing HW Cursor
[ 17293.754] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[ 17293.790] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[ 17293.793] (==) intel(0): DPMS enabled
[ 17293.793] (==) intel(0): Intel XvMC decoder enabled
[ 17293.793] (WW) intel(0): Disabling Xv because no adaptors could be initialized.
[ 17293.793] (II) intel(0): direct rendering: DRI2 Enabled
[ 17293.793] (==) intel(0): hotplug detection: "enabled"
[ 17293.793] (--) RandR disabled
[ 17293.793] (II) Initializing built-in extension Generic Event Extension
[ 17293.793] (II) Initializing built-in extension SHAPE
[ 17293.793] (II) Initializing built-in extension MIT-SHM
[ 17293.793] (II) Initializing built-in extension XInputExtension
[ 17293.793] (II) Initializing built-in extension XTEST
[ 17293.793] (II) Initializing built-in extension BIG-REQUESTS
[ 17293.793] (II) Initializing built-in extension SYNC
[ 17293.793] (II) Initializing built-in extension XKEYBOARD
[ 17293.793] (II) Initializing built-in extension XC-MISC
[ 17293.793] (II) Initializing built-in extension SECURITY
[ 17293.794] (II) Initializing built-in extension XINERAMA
[ 17293.794] (II) Initializing built-in extension XFIXES
[ 17293.794] (II) Initializing built-in extension RENDER
[ 17293.794] (II) Initializing built-in extension RANDR
[ 17293.794] (II) Initializing built-in extension COMPOSITE
[ 17293.794] (II) Initializing built-in extension DAMAGE
[ 17293.794] (II) Initializing built-in extension GESTURE
[ 17293.804] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[ 17293.804] (II) AIGLX: enabled GLX_INTEL_swap_event
[ 17293.804] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[ 17293.804] (II) AIGLX: enabled GLX_SGI_make_current_read
[ 17293.804] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[ 17293.804] (II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
[ 17293.804] (II) GLX: Initialized DRI2 GL provider for screen 0
[ 17293.804] (II) intel(0): Setting screen physical size to 508 x 285
[ 17293.817] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 17293.822] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[ 17293.822] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 17293.822] (II) LoadModule: "evdev"
[ 17293.822] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 17293.822] (II) Module evdev: vendor="X.Org Foundation"
[ 17293.822] 	compiled for 1.9.0, module version = 2.3.2
[ 17293.822] 	Module class: X.Org XInput Driver
[ 17293.822] 	ABI class: X.Org XInput driver, version 11.0
[ 17293.822] (**) Power Button: always reports core events
[ 17293.822] (**) Power Button: Device: "/dev/input/event2"
[ 17293.910] (II) Power Button: Found keys
[ 17293.910] (II) Power Button: Configuring as keyboard
[ 17293.910] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[ 17293.910] (**) Option "xkb_rules" "evdev"
[ 17293.910] (**) Option "xkb_model" "pc105"
[ 17293.910] (**) Option "xkb_layout" "us"
[ 17293.912] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[ 17293.912] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[ 17293.912] (**) Video Bus: always reports core events
[ 17293.912] (**) Video Bus: Device: "/dev/input/event8"
[ 17293.961] (II) Video Bus: Found keys
[ 17293.961] (II) Video Bus: Configuring as keyboard
[ 17293.961] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[ 17293.961] (**) Option "xkb_rules" "evdev"
[ 17293.961] (**) Option "xkb_model" "pc105"
[ 17293.961] (**) Option "xkb_layout" "us"
[ 17293.963] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[ 17293.963] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[ 17293.963] (**) Video Bus: always reports core events
[ 17293.963] (**) Video Bus: Device: "/dev/input/event7"
[ 17294.041] (II) Video Bus: Found keys
[ 17294.041] (II) Video Bus: Configuring as keyboard
[ 17294.041] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[ 17294.041] (**) Option "xkb_rules" "evdev"
[ 17294.041] (**) Option "xkb_model" "pc105"
[ 17294.041] (**) Option "xkb_layout" "us"
[ 17294.046] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[ 17294.046] (II) No input driver/identifier specified (ignoring)
[ 17294.046] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[ 17294.046] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[ 17294.046] (**) Sleep Button: always reports core events
[ 17294.046] (**) Sleep Button: Device: "/dev/input/event1"
[ 17294.121] (II) Sleep Button: Found keys
[ 17294.121] (II) Sleep Button: Configuring as keyboard
[ 17294.121] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[ 17294.121] (**) Option "xkb_rules" "evdev"
[ 17294.121] (**) Option "xkb_model" "pc105"
[ 17294.121] (**) Option "xkb_layout" "us"
[ 17294.125] (II) config/udev: Adding input device USB2.0 2.0M UVC WebCam (/dev/input/event4)
[ 17294.125] (**) USB2.0 2.0M UVC WebCam: Applying InputClass "evdev keyboard catchall"
[ 17294.125] (**) USB2.0 2.0M UVC WebCam: always reports core events
[ 17294.125] (**) USB2.0 2.0M UVC WebCam: Device: "/dev/input/event4"
[ 17294.201] (II) USB2.0 2.0M UVC WebCam: Found keys
[ 17294.201] (II) USB2.0 2.0M UVC WebCam: Configuring as keyboard
[ 17294.201] (II) XINPUT: Adding extended input device "USB2.0 2.0M UVC WebCam" (type: KEYBOARD)
[ 17294.201] (**) Option "xkb_rules" "evdev"
[ 17294.201] (**) Option "xkb_model" "pc105"
[ 17294.201] (**) Option "xkb_layout" "us"
[ 17294.206] (II) config/udev: Adding input device Microsoft  Microsoft Basic Optical Mouse v2.0  (/dev/input/event5)
[ 17294.206] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : Applying InputClass "evdev pointer catchall"
[ 17294.206] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : always reports core events
[ 17294.206] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : Device: "/dev/input/event5"
[ 17294.291] (II) Microsoft  Microsoft Basic Optical Mouse v2.0 : Found 3 mouse buttons
[ 17294.291] (II) Microsoft  Microsoft Basic Optical Mouse v2.0 : Found scroll wheel(s)
[ 17294.291] (II) Microsoft  Microsoft Basic Optical Mouse v2.0 : Found relative axes
[ 17294.291] (II) Microsoft  Microsoft Basic Optical Mouse v2.0 : Found x and y relative axes
[ 17294.291] (II) Microsoft  Microsoft Basic Optical Mouse v2.0 : Configuring as mouse
[ 17294.291] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : YAxisMapping: buttons 4 and 5
[ 17294.291] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 17294.292] (II) XINPUT: Adding extended input device "Microsoft  Microsoft Basic Optical Mouse v2.0 " (type: MOUSE)
[ 17294.292] (II) Microsoft  Microsoft Basic Optical Mouse v2.0 : initialized for relative axes.
[ 17294.293] (II) config/udev: Adding input device Microsoft  Microsoft Basic Optical Mouse v2.0  (/dev/input/mouse0)
[ 17294.293] (II) No input driver/identifier specified (ignoring)
[ 17294.297] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[ 17294.297] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[ 17294.297] (**) AT Translated Set 2 keyboard: always reports core events
[ 17294.297] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[ 17294.401] (II) AT Translated Set 2 keyboard: Found keys
[ 17294.401] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[ 17294.401] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[ 17294.401] (**) Option "xkb_rules" "evdev"
[ 17294.401] (**) Option "xkb_model" "pc105"
[ 17294.401] (**) Option "xkb_layout" "us"
[ 17294.403] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[ 17294.403] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[ 17294.403] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[ 17294.403] (II) LoadModule: "synaptics"
[ 17294.403] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[ 17294.403] (II) Module synaptics: vendor="X.Org Foundation"
[ 17294.403] 	compiled for 1.9.0, module version = 1.2.2
[ 17294.404] 	Module class: X.Org XInput Driver
[ 17294.404] 	ABI class: X.Org XInput driver, version 11.0
[ 17294.404] (II) Synaptics touchpad driver version 1.2.2
[ 17294.404] (**) Option "Device" "/dev/input/event6"
[ 17294.831] (II) ETPS/2 Elantech Touchpad: x-axis range 8 - 1144
[ 17294.831] (II) ETPS/2 Elantech Touchpad: y-axis range 8 - 760
[ 17294.831] (II) ETPS/2 Elantech Touchpad: device does not report pressure, will use touch data.
[ 17294.831] (II) ETPS/2 Elantech Touchpad: finger width range 0 - 0
[ 17294.831] (II) ETPS/2 Elantech Touchpad: buttons: left right double triple
[ 17295.151] (--) ETPS/2 Elantech Touchpad: touchpad found
[ 17295.151] (**) ETPS/2 Elantech Touchpad: always reports core events
[ 17295.311] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD)
[ 17295.312] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[ 17295.312] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 0
[ 17295.312] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[ 17295.312] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[ 17295.591] (--) ETPS/2 Elantech Touchpad: touchpad found
[ 17295.592] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[ 17295.592] (II) No input driver/identifier specified (ignoring)
[ 17295.889] (II) intel(0): EDID vendor "AUO", prod id 5613
[ 17295.889] (II) intel(0): Printing DDC gathered Modelines:
[ 17295.889] (II) intel(0): Modeline "1920x1080"x0.0  142.40  1920 2028 2076 2100  1080 1090 1100 1130 -hsync -vsync (67.8 kHz)
[ 17295.918] (II) intel(0): EDID vendor "AUO", prod id 5613
[ 17295.918] (II) intel(0): Printing DDC gathered Modelines:
[ 17295.918] (II) intel(0): Modeline "1920x1080"x0.0  142.40  1920 2028 2076 2100  1080 1090 1100 1130 -hsync -vsync (67.8 kHz)
[ 17295.946] (II) intel(0): EDID vendor "AUO", prod id 5613
[ 17295.946] (II) intel(0): Printing DDC gathered Modelines:
[ 17295.946] (II) intel(0): Modeline "1920x1080"x0.0  142.40  1920 2028 2076 2100  1080 1090 1100 1130 -hsync -vsync (67.8 kHz)
[ 17295.974] (II) intel(0): EDID vendor "AUO", prod id 5613
[ 17295.974] (II) intel(0): Printing DDC gathered Modelines:
[ 17295.974] (II) intel(0): Modeline "1920x1080"x0.0  142.40  1920 2028 2076 2100  1080 1090 1100 1130 -hsync -vsync (67.8 kHz)
[ 17303.088] (II) intel(0): EDID vendor "AUO", prod id 5613
[ 17303.088] (II) intel(0): Printing DDC gathered Modelines:
[ 17303.088] (II) intel(0): Modeline "1920x1080"x0.0  142.40  1920 2028 2076 2100  1080 1090 1100 1130 -hsync -vsync (67.8 kHz)
[ 17303.118] (II) intel(0): EDID vendor "AUO", prod id 5613
[ 17303.118] (II) intel(0): Printing DDC gathered Modelines:
[ 17303.118] (II) intel(0): Modeline "1920x1080"x0.0  142.40  1920 2028 2076 2100  1080 1090 1100 1130 -hsync -vsync (67.8 kHz)
[ 17303.147] (II) intel(0): EDID vendor "AUO", prod id 5613
[ 17303.147] (II) intel(0): Printing DDC gathered Modelines:
[ 17303.147] (II) intel(0): Modeline "1920x1080"x0.0  142.40  1920 2028 2076 2100  1080 1090 1100 1130 -hsync -vsync (67.8 kHz)
[ 17303.177] (II) intel(0): EDID vendor "AUO", prod id 5613
[ 17303.177] (II) intel(0): Printing DDC gathered Modelines:
[ 17303.177] (II) intel(0): Modeline "1920x1080"x0.0  142.40  1920 2028 2076 2100  1080 1090 1100 1130 -hsync -vsync (67.8 kHz)
[ 17308.387] (II) intel(0): EDID vendor "AUO", prod id 5613
[ 17308.387] (II) intel(0): Printing DDC gathered Modelines:
[ 17308.387] (II) intel(0): Modeline "1920x1080"x0.0  142.40  1920 2028 2076 2100  1080 1090 1100 1130 -hsync -vsync (67.8 kHz)
[ 18563.378] (II) intel(0): EDID vendor "AUO", prod id 5613
[ 18563.378] (II) intel(0): Printing DDC gathered Modelines:
[ 18563.378] (II) intel(0): Modeline "1920x1080"x0.0  142.40  1920 2028 2076 2100  1080 1090 1100 1130 -hsync -vsync (67.8 kHz)
```

---

### Post by Yellow Pasque on 2011-04-09
Nothing stands out to me except:
```
(EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
```
Googling, I see some reports of freezing or crashed X server for that, but nothing about performance.

---

### Post by komasoftware on 2011-04-09
googling the same, no luck for me.
thx for your help anyway.

---

### Post by komasoftware on 2011-04-09
NOne of the GL screen savers is showing anything... any idea ?
must be related imo.

---

### Post by komasoftware on 2011-04-09
koen@N53SV:/var/log$ glxinfo 
name of display: :0.0
Unrecognized deviceID 116
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  21
  Current serial number in output stream:  24

---

### Post by Yellow Pasque on 2011-04-09
Sorry, I just noticed you had Sandy Bridge graphics. Getting 3D to work will require more recent graphics components (you can try xorg-edgers PPA)  [http://www.phoronix.com/scan.php?page=news_item&px=ODk5OA](http://www.phoronix.com/scan.php?page=news_item&px=ODk5OA)

---

### Post by RavanH on 2011-04-28
Have you tried [http://www.downloadatoz.com/driver/articles/how-to-enable-intel-graphics-driver-for-ubuntu-10-10.html](http://www.downloadatoz.com/driver/articles/how-to-enable-intel-graphics-driver-for-ubuntu-10-10.html) ?

---

### Post by akatrevorj on 2011-06-10
I got bumblebee working in Natty with GL accel from both the i965 card and the nvidia card (via modified optirun). It's surprising how well this method of using the nvidia card works (virtualgl using a second xorg server for the nvidia card in the background)!

Manually do the install using debian.install from debumblebee on github as a loose guide, know what you're doing before you do it and if it applies to Ubuntu or just debian.

For those interested, here's some quick notes:

1. Use xorg-edgers PPA, install libgl1-mesa-dri-experimental
2. Modify paths in optirun scripts for Ubuntu's nvidia-current path.
3. Link mesa's ld.so.conf gl_conf alternative in /etc/ld.so.conf.d as something that loads before nvidia's, like /etc/ld.so.conf.d/00_GL_mesa.conf

Viola, GL accel on either card on demand per application =D

---

### Post by iMPR3SSiON on 2011-09-28
Could you be a bit more specific about that? I have the same idiotic problem and I'd like to have both graphics devices working. Thank you!

---


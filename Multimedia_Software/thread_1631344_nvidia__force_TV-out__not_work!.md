---
title: "nvidia  force TV-out  not work!"
date: 2010-11-26
forum: Multimedia Software
---

### Post by david_sale on 2010-11-26
hi, all
i used Gefoce9400GT , 190.53 nvidia driver, configuring Mulitiple X screen
both CRT and TV, work fine if CRT and TV connected to card,
but i hope foce TV-out output signal, means that if not connected to TV, the SVIDEO can output signal. 

because the line too far, can not decect TV connection, so i think foce output TV-out signal.
i used [COLOR="Red"][Option "ConnectedMonitor" "CRT, TV"]("http://us.download.nvidia.com/XFree86/Linux-x86/190.53/README/appendix-b.html") [/COLOR] can force found 2 display device, have 2 screen ok, but not display at TV if not connected TV.   

I do not understand why the TV has been forced output signal does not display images, they can be connected to the TV show?
:-(

Someone can help me?

---

### Post by david_sale on 2010-11-26
now i used xorg.conf

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
    FontPath        "/usr/lib/X11/fonts/misc/:unscaled"
    FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/lib/X11/fonts/misc/"
    FontPath        "/usr/lib/X11/fonts/Type1/"
    FontPath        "/usr/lib/X11/fonts/Speedo/"
    FontPath        "/usr/lib/X11/fonts/100dpi/"
    FontPath        "/usr/lib/X11/fonts/75dpi/"
    FontPath        "/usr/lib/X11/fonts/cyrillic/"
    FontPath        "/usr/lib/X11/fonts/TTF/"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    #Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
# Removed Option "metamodes" "1024x768_75 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TVStandard" "NTSC-M"
    #Option         "TVOutFormat" "SVIDEO"
    Option         "ConnectedMonitor" "CRT,TV"
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0,TV-0"
    Option         "metamodes" "CRT: 1024x768_75 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "nvidia-auto-select +0+0"
# Removed Option "metamodes" "TV: 800x600 +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 512x384 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSectio

---

### Post by david_sale on 2010-11-26
Xorg.0.log

	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 23 12:41:50 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Device1"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/local" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/CID" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/lib/X11/fonts/misc/:unscaled,
	/usr/lib/X11/fonts/100dpi/:unscaled,
	/usr/lib/X11/fonts/75dpi/:unscaled,
	/usr/lib/X11/fonts/misc/,
	/usr/lib/X11/fonts/Type1/,
	/usr/lib/X11/fonts/Speedo/,
	/usr/lib/X11/fonts/100dpi/,
	/usr/lib/X11/fonts/75dpi/,
	/usr/lib/X11/fonts/cyrillic/,
	/usr/lib/X11/fonts/TTF/,
	/usr/share/fonts/TTF,
	/usr/share/fonts/OTF,
	/usr/share/fonts/Type1,
	/usr/share/fonts/misc,
	/usr/share/fonts/75dpi/:unscaled,
	/usr/share/fonts/100dpi/:unscaled,
	/usr/share/fonts/75dpi,
	/usr/share/fonts/100dpi,
	/usr/share/fonts/cyrillic,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x1de0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:1:0:0) 10de:042c:0000:0000 rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cf00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  190.53  Tue Dec  8 20:47:42 PST 2009
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  190.53  Tue Dec  8 19:16:02 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ConnectedMonitor" "CRT,TV"
(**) NVIDIA(0): Option "TVStandard" "NTSC-M"
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "CRT: 1024x768_75 +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0,TV-0"
(**) Jul 23 12:41:50 NVIDIA(0): Enabling RENDER acceleration
(**) Jul 23 12:41:50 NVIDIA(0): TV Standard string: "NTSC-M"
(**) Jul 23 12:41:50 NVIDIA(0): ConnectedMonitor string: "CRT,TV"
(II) Jul 23 12:41:50 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Jul 23 12:41:50 NVIDIA(0):     enabled.
(WW) Jul 23 12:41:51 NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) Jul 23 12:41:51 NVIDIA(0): NVIDIA GPU GeForce 9400 GT (G86) at PCI:1:0:0 (GPU-0)
(--) Jul 23 12:41:51 NVIDIA(0): Memory: 262144 kBytes
(--) Jul 23 12:41:51 NVIDIA(0): VideoBIOS: 60.86.45.00.00
(II) Jul 23 12:41:51 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Jul 23 12:41:51 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Jul 23 12:41:51 NVIDIA(0): Connected display device(s) on GeForce 9400 GT at PCI:1:0:0:
(--) Jul 23 12:41:51 NVIDIA(0):     CRT-0
(--) Jul 23 12:41:51 NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) Jul 23 12:41:51 NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(--) Jul 23 12:41:51 NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) Jul 23 12:41:51 NVIDIA(0): TV encoder: NVIDIA
(II) Jul 23 12:41:51 NVIDIA(0): Display Device found referenced in MetaMode: CRT-0
(II) Jul 23 12:41:51 NVIDIA(0): Assigned Display Device: CRT-0
(II) Jul 23 12:41:51 NVIDIA(0): Validated modes:
(II) Jul 23 12:41:51 NVIDIA(0):     "CRT:1024x768_75+0+0"
(II) Jul 23 12:41:51 NVIDIA(0): Virtual screen size determined to be 1024 x 768
(WW) Jul 23 12:41:51 NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) Jul 23 12:41:51 NVIDIA(0):     from CRT-0's EDID.
(==) Jul 23 12:41:51 NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) Jul 23 12:41:51 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "TV: 512x384 +0+0"
(**) Jul 23 12:41:51 NVIDIA(1): Enabling RENDER acceleration
(II) Jul 23 12:41:51 NVIDIA(1): NVIDIA GPU GeForce 9400 GT (G86) at PCI:1:0:0 (GPU-0)
(--) Jul 23 12:41:51 NVIDIA(1): Memory: 262144 kBytes
(--) Jul 23 12:41:51 NVIDIA(1): VideoBIOS: 60.86.45.00.00
(II) Jul 23 12:41:51 NVIDIA(1): Detected PCI Express Link width: 16X
(--) Jul 23 12:41:51 NVIDIA(1): Interlaced video modes are supported on this GPU
(--) Jul 23 12:41:51 NVIDIA(1): Connected display device(s) on GeForce 9400 GT at PCI:1:0:0:
(--) Jul 23 12:41:51 NVIDIA(1):     CRT-0
(--) Jul 23 12:41:51 NVIDIA(1):     NVIDIA TV Encoder (TV-0)
(--) Jul 23 12:41:51 NVIDIA(1): CRT-0: 400.0 MHz maximum pixel clock
(--) Jul 23 12:41:51 NVIDIA(1): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) Jul 23 12:41:51 NVIDIA(1): TV encoder: NVIDIA
(II) Jul 23 12:41:51 NVIDIA(1): Display Device found referenced in MetaMode: TV-0
(II) Jul 23 12:41:51 NVIDIA(1): Assigned Display Device: TV-0
(II) Jul 23 12:41:51 NVIDIA(1): Validated modes:
(II) Jul 23 12:41:51 NVIDIA(1):     "TV:512x384+0+0"
(II) Jul 23 12:41:51 NVIDIA(1): Virtual screen size determined to be 512 x 384
(==) Jul 23 12:41:51 NVIDIA(1): DPI set to (75, 75); computed from built-in default
(==) Jul 23 12:41:51 NVIDIA(1): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Jul 23 12:41:51 NVIDIA(0): Initialized GPU GART.
(II) Jul 23 12:41:51 NVIDIA(0): Setting mode "CRT:1024x768_75+0+0"
(II) Loading extension NV-GLX
(II) Jul 23 12:41:51 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Jul 23 12:41:51 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Jul 23 12:41:51 NVIDIA(1): Initialized GPU GART.
(II) Jul 23 12:41:51 NVIDIA(1): Setting mode "TV:512x384+0+0"
(II) Jul 23 12:41:51 NVIDIA(1): Built-in logo is bigger than the screen.
(II) Jul 23 12:41:51 NVIDIA(1): Initialized OpenGL Acceleration
(==) NVIDIA(1): Disabling shared memory pixmaps
(II) Jul 23 12:41:51 NVIDIA(1): Initialized X Rendering Acceleration
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(II) NVIDIA(1): DPMS enabled
(==) RandR enabled

---


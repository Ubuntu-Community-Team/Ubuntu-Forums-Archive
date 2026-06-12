---
title: "Enable monitor out with TV out"
date: 2009-01-09
forum: Mythbuntu
---

### Post by fenx7 on 2009-01-09
My goal is to have mythbuntu as currently working on my tv and a seperate xscreen on my monitor to browse the web, etc. nvidia-settings even with sudo do not detect the monitor - only the TV.

I have mythbuntu installed with tv out working. I have a nvidia 8500GT and am using an svideo cable as my TV set is a CRT. Besides some overscan which I can not seem to fix it is working...

I now have my CRT Monitor plugged into the VGA port of the video card, but when I boot my mythbuntu box my bios and mythbuntu loading screens are displayed on the monitor (instead of the TV if the monitor were not plugged in), but as soon as X loads the monitor goes to sleep and the TV displays mythbuntu as normal.

My original xorg.conf is 

```

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen" 0 0
# commented out by update-manager, HAL is now used
#       Inputdevice     "Generic Keyboard"
# commented out by update-manager, HAL is now used
#       Inputdevice     "Configured Mouse"
EndSection

Section "Module"
        Load            "glx"
EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#       Identifier      "Generic Keyboard"
#       Driver          "kbd"
#       Option          "CoreKeyboard"
#       Option          "XkbRules"      "xorg"
#       Option          "XkbModel"      "pc105"
#       Option          "XkbLayout"     "us"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#       Identifier      "Configured Mouse"
#       Driver          "mouse"
#       Option          "CorePointer"
#       Option          "Device"        "/dev/input/mice"
#       Option          "Protocol"      "ImPS/2"
#       Option          "ZAxisMapping"  "4 5"
#       Option          "Emulate3Buttons"       "true"
#EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        Option          "DPI"   "100x100"
        Option          "UseEvents"     "1"
        Option          "AddARGBVisuals"        "1"
        Option          "AddARGBGLXVisuals"     "1"
        Option          "NoLogo"        "1"
        Option          "ConnectedMonitor"      "TV"
        Option          "TVOutFormat"   "SVIDEO"
        Option          "TVStandard"    "PAL-B"
        #Option         "UseDisplayDevice" "TV"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "nvidia-auto-select"    "1920x1080"     "1280x720"      "1024x768"      "720x480"       "800x600"       "640x480"
        EndSubSection
EndSection


```

I have followed [http://ubuntuforums.org/showthread.php?t=850650&highlight=nvidia+svideo+monitor](http://ubuntuforums.org/showthread.php?t=850650&highlight=nvidia+svideo+monitor) and made my xorg.conf

```

Section "ServerLayout"
        Identifier      "Default Layout"
#  screen "Default Screen" 0 0
        Screen      0  "Screen[0]" 0 0
        Screen      1  "Screen[1]" RightOf "Screen[0]"
# commented out by update-manager, HAL is now used
#       Inputdevice     "Generic Keyboard"
# commented out by update-manager, HAL is now used
#       Inputdevice     "Configured Mouse"
EndSection

Section "Module"
        Load            "glx"
EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#       Identifier      "Generic Keyboard"
#       Driver          "kbd"
#       Option          "CoreKeyboard"
#       Option          "XkbRules"      "xorg"
#       Option          "XkbModel"      "pc105"
#       Option          "XkbLayout"     "us"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#       Identifier      "Configured Mouse"
#       Driver          "mouse"
#       Option          "CorePointer"
#       Option          "Device"        "/dev/input/mice"
#       Option          "Protocol"      "ImPS/2"
#       Option          "ZAxisMapping"  "4 5"
#       Option          "Emulate3Buttons"       "true"
#EndSection

Section "Monitor"
# TV
        Identifier      "Monitor[0]"
        Option          "DPMS"
EndSection

Section "Monitor"
#CRT
    Identifier     "Monitor[1]"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0 - 60.0
    Option          "DPMS"
EndSection

Section "Device"
        Identifier      "Video[0]"
        Driver          "nvidia"
        Option          "DPI"   "100x100"
        Option          "UseEvents"     "1"
        Option          "AddARGBVisuals"        "1"
        Option          "AddARGBGLXVisuals"     "1"
        Option          "NoLogo"        "1"
        Option          "ConnectedMonitor"      "TV"
        Option          "TVOutFormat"   "SVIDEO"
        Option          "TVStandard"    "PAL-B"
        #Option         "UseDisplayDevice" "TV"
EndSection

Section "Device"
        Identifier      "Video[1]"
        Driver          "nvidia"
        Option          "DPI"   "100x100"
        Option          "UseEvents"     "1"
        Option          "AddARGBVisuals"        "1"
        Option          "AddARGBGLXVisuals"     "1"
        Option          "NoLogo"        "1"
        #Option         "UseDisplayDevice" "TV"
EndSection


Section "Screen"
        Identifier      "Screen[0]"
        Device          "Video[0]"
        Monitor         "Monitor[0]"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "nvidia-auto-select"    "1920x1080"     "1280x720"      "1024x768"      "720x480"       "800x600"       "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen[1]"
        Device          "Video[1]"
        Monitor         "Monitor[1]"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "nvidia-auto-select"    "1920x1080"     "1280x720"      "1024x768"      "720x480"       "800x600"       "640x$
        EndSubSection
EndSection

```

I have rebooted my box to get the new xorg settings, but pc behaves as normal - as in only the TV works - monitor is asleep.

---

### Post by EasyRiderOnTheStorm on 2009-01-09
You may have missed something. According to the xorg.conf docs, regarding "Device" sections:

> Screen — An optional entry which specifies which monitor connector or head on the video card the Device section configures. This option is only useful for video cards with multiple heads.

If multiple monitors are connected to different heads on the same video card, separate Device sections must exist and **each of these sections must have a different Screen value**.

Values for the Screen entry must be an integer. The first head on the video card has a value of 0. The value for each additional head increments this value by one. 

Indeed, in the thread you linked, such entries exist...

> Section "Device"
[INDENT]    Identifier     "Device[0]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen          0[/INDENT]
EndSection

...but your config seems to lack them.

---

### Post by newlinux on 2009-01-09
Just as another data point... This is how one of my setups work (S-video to TV, VGA to CRT monitor, Mythtv on the TV). What I did was start of with no xorg.conf file (in your case you could simply rename your current xorg.conf). Then I went into nvidia-settings, setup two separate screens from on X server (not using twinview/xinerama) and then had nvidia-settings save the settings in the xorg.conf and it worked thereafter (I have since tweaked the resulting xorg.conf file for other reasons). In case it helps, here is my xorg.conf:

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Thu Jun  5 09:26:53 UTC 2008


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" LeftOf "Screen1"
    Screen      1  "Screen1" 1024 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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

    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic E90fb"
    HorizSync       30.0 - 86.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7100 GS"
    BusID          "PCI:4:0:0"
    Screen          0
    Option 	   "UseEvents" "on"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7100 GS"
    BusID          "PCI:4:0:0"
    Screen          1
    Option	   "UseEvents" "on"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "TV-0"
    Option         "metamodes" "TV: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard1"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by fenx7 on 2009-01-09
Thank you for your help it is much appreciated. I found that I had to use the "connected monitor" option in the screen section to get this to work.

Now my xorg.conf is 

```

Section "ServerLayout"
	Identifier	"Default Layout"
#  screen "Default Screen" 0 0
        Screen      0  "Screen[0]" 0 0
        Screen      1  "Screen[1]" LeftOf "Screen[0]"
# commented out by update-manager, HAL is now used
#	Inputdevice	"Generic Keyboard"
# commented out by update-manager, HAL is now used
#	Inputdevice	"Configured Mouse"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"CoreKeyboard"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"	"/dev/input/mice"
#	Option		"Protocol"	"ImPS/2"
#	Option		"ZAxisMapping"	"4 5"
#	Option		"Emulate3Buttons"	"true"
#EndSection

Section "Monitor"
# TV
	Identifier	"Monitor[0]"
	Option		"DPMS"
EndSection

Section "Monitor"
#CRT
    Identifier     "Monitor[1]"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0 - 60.0
    Option          "DPMS"
EndSection

Section "Device"
	Identifier	"Video[0]"
	Driver		"nvidia"
        BusID           "PCI:1:0:0"
        Screen		0
	#Option         "UseDisplayDevice" "TV"
EndSection

Section "Device"
        Identifier      "Video[1]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Screen		1
	Option		"DPI"	"100x100"
	Option		"UseEvents"	"1"
	Option		"AddARGBGLXVisuals"	"1"
	Option		"AddARGBVisuals"	"1"
	Option		"NoLogo"	"1"
EndSection


Section "Screen"
	Identifier	"Screen[0]"
	Device		"Video[0]"
	Monitor		"Monitor[0]"
	Option		"ConnectedMonitor"	"Monitor[0]"
	Option		"TVOutFormat"	"SVIDEO"
	Option		"TVStandard"	"PAL-B"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"nvidia-auto-select"	"1920x1080"	"1280x720"	"1024x768"	"720x480"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen[1]"
        Device          "Video[1]"
        Monitor         "Monitor[1]"
	Option		"ConnectedMonitor"	"Monitor[1]"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "nvidia-auto-select"    "1920x1080"     "1280x720"      "1024x768"      "720x480"       "800x600"       "640x480"
        EndSubSection
EndSection

```

My problem is now all of the default mythbuntu stuff opens on my monitor instead of my TV??? I have tried changing the values (inside the square brackets in my case), but that did not work. Any ideas?

I also tried to find out how to autstart in xfce4 - .confing/autostart/mythtv.desktop - but could not fins where or how a display variable could be used to get mythbuntu to start on the TV if I can not switch my displays.

my xorg log is
```


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux adam-desktop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan 10 11:54:36 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen[0]" (0)
(**) |   |-->Monitor "Monitor[0]"
(**) |   |-->Device "Video[0]"
(**) |-->Screen "Screen[1]" (1)
(**) |   |-->Monitor "Monitor[1]"
(**) |   |-->Device "Video[1]"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 8500 GT rev 161, Mem @ 0xfd000000/0, 0xe0000000/0, 0xfa000000/0, I/O @ 0x0000dc00/0, BIOS @ 0x????????/131072
(--) PCI: (0@2:1:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xf8ffe000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  177.82  Tue Nov  4 14:03:48 PST 2008
(II) Loading extension GLX
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
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
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  177.82  Tue Nov  4 13:42:45 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
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
(**) NVIDIA(0): Option "ConnectedMonitor" "Monitor[0]"
(**) NVIDIA(0): Option "TVStandard" "PAL-B"
(**) NVIDIA(0): Option "TVOutFormat" "SVIDEO"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Forcing SVIDEO output
(**) NVIDIA(0): TV Standard string: "PAL-B"
(**) NVIDIA(0): ConnectedMonitor string: "Monitor[0]"
(WW) NVIDIA(0): Invalid ConnectedMonitor string token: "Monitor[0]";
(WW) NVIDIA(0):     discarding token.
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8500 GT (G86) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.86.39.00.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8500 GT at PCI:1:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (CRT-1)
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): Samsung SyncMaster (CRT-1): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: CRT-1
(WW) NVIDIA(0): No valid modes for "1920x1080"; removing.
(WW) NVIDIA(0): No valid modes for "1280x720"; removing.
(WW) NVIDIA(0): No valid modes for "720x480"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "NoLogo" "1"
(**) NVIDIA(1): Option "ConnectedMonitor" "Monitor[1]"
(**) NVIDIA(1): Option "DPI" "100x100"
(**) NVIDIA(1): Option "UseEvents" "1"
(**) NVIDIA(1): Option "AddARGBGLXVisuals" "1"
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU GeForce 8500 GT (G86) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 524288 kBytes
(--) NVIDIA(1): VideoBIOS: 60.86.39.00.00
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 8500 GT at PCI:1:0:0:
(--) NVIDIA(1):     Samsung SyncMaster (CRT-1)
(--) NVIDIA(1):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(1): Samsung SyncMaster (CRT-1): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): TV encoder: NVIDIA
(II) NVIDIA(1): Assigned Display Device: TV-0
(WW) NVIDIA(1): No valid modes for "1920x1080"; removing.
(WW) NVIDIA(1): No valid modes for "1280x720"; removing.
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "nvidia-auto-select"
(II) NVIDIA(1):     "1024x768"
(II) NVIDIA(1):     "720x480"
(II) NVIDIA(1):     "800x600"
(II) NVIDIA(1):     "640x480"
(II) NVIDIA(1): Virtual screen size determined to be 1024 x 768
(++) NVIDIA(1): DPI set to (100, 100); computed from -dpi X commandline option
(**) NVIDIA(1): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) NVIDIA(1): Initialized GPU GART.
(II) NVIDIA(1): Setting mode "nvidia-auto-select"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(1): DPMS enabled
(WW) NVIDIA(1): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(II) config/hal: Adding input device Logitech Logitech BT Mini-Receiver
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Logitech Logitech BT Mini-Receiver: always reports core events
(**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event5"
(II) Logitech Logitech BT Mini-Receiver: Found x and y relative axes
(II) Logitech Logitech BT Mini-Receiver: Found 13 mouse buttons
(II) Logitech Logitech BT Mini-Receiver: Found keys
(II) Logitech Logitech BT Mini-Receiver: Configuring as mouse
(II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech Logitech BT Mini-Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech Logitech BT Mini-Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech Logitech BT Mini-Receiver: xkb_layout: "us"
(**) Logitech Logitech BT Mini-Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech Logitech BT Mini-Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Logitech Logitech BT Mini-Receiver
(**) Logitech Logitech BT Mini-Receiver: always reports core events
(**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event4"
(II) Logitech Logitech BT Mini-Receiver: Found keys
(II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech Logitech BT Mini-Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech Logitech BT Mini-Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech Logitech BT Mini-Receiver: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200

```

---


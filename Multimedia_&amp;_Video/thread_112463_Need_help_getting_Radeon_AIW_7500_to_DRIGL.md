---
title: "Need help getting Radeon AIW 7500 to DRI/GL"
date: 2006-01-04
forum: Multimedia &amp; Video
---

### Post by KamakazieX on 2006-01-04
Having trouble getting my Raden AIW 7500 working in opengl, glxgears gets about 183fps right now, using Mesa SW mode. Here is my xorg.conf, ive tried forcing fglrx to be used as the driver, not having any luck.


====

Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the font modules
    Load        "type1"
#    Load        "speedo"
    Load        "freetype"
#    Load        "xtt"

# This loads the GLX module
    Load       "glx"
# This loads the DRI module
    Load       "dri"

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R6/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# 

    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/TTF/"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/CID/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/TrueType/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/freefont/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
    Option "AutoRepeat" "500 30"
    Option "XkbRules"	"xorg"
    Option "XkbModel"	"pc104"
    Option "XkbLayout"	"us"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Mouse1"
    Driver	"mouse"
    Option "Protocol"    "Auto"
    Option "Device"      "/dev/psaux"
    Option "SampleRate"	"150"

EndSection


# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"

    Identifier  "SyncMaster997DF"

# HorizSync is in kHz unless units are specified.
# HorizSync may be a comma separated list of discrete values, or a
# comma separated list of ranges of values.
# NOTE: THE VALUES HERE ARE EXAMPLES ONLY.  REFER TO YOUR MONITOR'S
# USER MANUAL FOR THE CORRECT NUMBERS.

    HorizSync   30 - 96

# VertRefresh is in Hz unless units are specified.
# VertRefresh may be a comma separated list of discrete values, or a
# comma separated list of ranges of values.
# NOTE: THE VALUES HERE ARE EXAMPLES ONLY.  REFER TO YOUR MONITOR'S
# USER MANUAL FOR THE CORRECT NUMBERS.

    VertRefresh 50- 160

EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier	"Standard VGA"
    VendorName	"Unknown"
    BoardName	"Unknown"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset	"generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

    Driver     "vga"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# intalled.

#    BusID      "PCI:0:10:0"

#    VideoRam	256

#    Clocks	25.2 28.3

EndSection

# Device configured by xorgconfig:

Section "Device"
    Identifier  "Radeon7500"
    Driver      "radeon"
    VideoRam    65536
    # Insert Clocks lines here if appropriate
EndSection


# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen 1"
    Device      "Radeon7500"
    Monitor     "SyncMaster997DF"
    DefaultDepth 16

    Subsection "Display"
        Depth       8
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Simple Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.  In this example, screen 2 is located to the
# right of screen 1.

    Screen "Screen 1"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

 Section "DRI"
    Mode 0666
 EndSection

====

---

### Post by KamakazieX on 2006-01-04
bump.

Should I give up and go back to the nv MX400 setup?.. never had a problem with that card. Wanted to get the all in wonder working. If anyones done it, it would be a big help.

---

### Post by DrBair on 2006-01-04
Were you using nvidia's glx drivers previously? If so you need to remove those first or jump through flaming hoops (which I am trying to do).  

Might also want to get rid of that generic svga device if its not doing anything.  It shouldn't hurt it at all, but its always best to simplify when finding issues.  

Also, do you have the radeon kernel module loaded?

And lastly, could you post your xorg log file?

---

### Post by KamakazieX on 2006-01-05
I've tried removing the nvidia drivers built into the ubuntu 5.04 distro, synaptic wants to trash the whole ubuntu-base if the drivers are removed, is there a workaround to remove the link between these two?

I'll see if removing the generic video code has any effect.. trying it out right now.

---

### Post by KamakazieX on 2006-01-05
X Window System Version 6.8.2 (Ubuntu 6.8.2-10.1 20050831033957 root@)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux rivers 2.6.10-6-k7 #1 Thu Dec 22 11:33:26 UTC 2005 i686
Build Date: 31 August 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-6-k7 (buildd@vernadsky) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Thu Dec 22 11:33:26 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan  5 03:26:59 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Simple Layout"
(**) |-->Screen "Screen 1" (0)
(**) |   |-->Monitor "SyncMaster997DF"
(**) |   |-->Device "Radeon7500"
(**) |-->Input Device "Mouse1"
(**) |-->Input Device "Keyboard1"
(**) FontPath set to "/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/Type1/,/usr/X11R6/lib/X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/"
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1022,7006 card 0000,0000 rev 25 class 06,00,00 hdr 80
(II) PCI: 00:01:0: chip 1022,7007 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:07:0: chip 1022,7408 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 1022,7409 card 0000,0000 rev 07 class 01,01,8a hdr 00
(II) PCI: 00:07:3: chip 1022,740b card 0000,0000 rev 03 class 06,80,00 hdr 00
(II) PCI: 00:07:4: chip 1022,740c card 0000,0000 rev 06 class 0c,03,10 hdr 00
(II) PCI: 00:08:0: chip 10b7,9050 card 0000,0000 rev 00 class 02,00,00 hdr 00
(II) PCI: 01:05:0: chip 1002,5157 card 1002,0f2a rev 00 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000cfff (0x2000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xefe00000 - 0xefefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd7c00000 - 0xe7cfffff (0x10100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:5:0) ATI Technologies Inc Radeon RV200 QW [Radeon 7500] rev 0, Mem @ 0xd8000000/27, 0xefef0000/16, I/O @ 0xc800/8, BIOS @ 0xefec0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe8000000 from 0xebffffff to 0xe7ffffff
(II) PCI Memory resource overlap reduced 0xefdff000 from 0xefdfffff to 0xefdfefff
(II) PCI I/O resource overlap reduced 0x0000dc00 from 0x0000dc03 to 0x0000dbff
(II) Active PCI resource ranges:
	[0] -1	0	0xeffff000 - 0xefffffff (0x1000) MX[B]
	[1] -1	0	0xefdff000 - 0xefdfefff (0x0) MX[B]O
	[2] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[3] -1	0	0xefec0000 - 0xefedffff (0x20000) MX[B](B)
	[4] -1	0	0xefef0000 - 0xefefffff (0x10000) MX[B](B)
	[5] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[6] -1	0	0x0000de00 - 0x0000de3f (0x40) IX[B]
	[7] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[8] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0x0000dc00 - 0x0000dbff (0x0) IX[B]O
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xeffff000 - 0xefffffff (0x1000) MX[B]
	[1] -1	0	0xefdff000 - 0xefdfefff (0x0) MX[B]O
	[2] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[3] -1	0	0xefec0000 - 0xefedffff (0x20000) MX[B](B)
	[4] -1	0	0xefef0000 - 0xefefffff (0x10000) MX[B](B)
	[5] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[6] -1	0	0x0000de00 - 0x0000de3f (0x40) IX[B]
	[7] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[8] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x0000dc00 - 0x0000dbff (0x0) IX[B]O
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xeffff000 - 0xefffffff (0x1000) MX[B]
	[6] -1	0	0xefdff000 - 0xefdfefff (0x0) MX[B]O
	[7] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[8] -1	0	0xefec0000 - 0xefedffff (0x20000) MX[B](B)
	[9] -1	0	0xefef0000 - 0xefefffff (0x10000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000de00 - 0x0000de3f (0x40) IX[B]
	[14] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[16] -1	0	0x0000dc00 - 0x0000dbff (0x0) IX[B]O
(II) LoadModule: "radeon"
(II) Loading /usr/X11R6/lib/modules/drivers/radeon_drv.o
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 4.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "ati"
(II) Loading /usr/X11R6/lib/modules/drivers/ati_drv.o
(II) Module ati: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 6.5.6
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension DPMS
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "radeon"
(II) Reloading /usr/X11R6/lib/modules/drivers/radeon_drv.o
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) ATI: ATI driver (version 6.5.6) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9200PRO 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9700 NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI RADEON 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireGL D1100 (RV370) 5B65 (PCIE),
	ATI Radeon Mobility M300 (M22) 5460 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI FireGL V5000,
	ATI MOBILITY FireGL V5000, ATI MOBILITY FireGL V5000,
	ATI MOBILITY RADEON X700, ATI MOBILITY RADEON X700,
	ATI RADEON X700 PRO, ATI RADEON X700 XT, ATI RADEON X700,
	ATI RADEON X700 SE, ATI RADEON X700 SE,
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI RADEON X800 SE,
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V7200 (R423) UQ (PCIE), ATI FireGL V5100 (R423) UR (PCIE),
	ATI FireGL V7100 (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100,
	ATI MOBILITY FireGL V5100, ATI MOBILITY RADEON X800,
	ATI MOBILITY RADEON X800 XT, ATI RADEON X800, ATI RADEON X800 XL,
	ATI RADEON R430 SE, ATI RADEON R430 XTP, ATI RADEON R480 4P,
	ATI RADEON R480 GL 16P, ATI RADEON R480 SE, ATI RADEON X850 PRO,
	ATI RADEON X850 XT, ATI RADEON X850 XT Platinum Edition,
	ATI RADEON X850 PRO, ATI RADEON X850 SE, ATI RADEON X850 XT,
	ATI RADEON X850 XT Platinum Edition
(II) Primary Device is: PCI 01:05:0
(--) Assigning device section with no busID to primary device
(--) Chipset ATI Radeon 7500 QW (AGP/PCI) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xeffff000 - 0xefffffff (0x1000) MX[B]
	[6] -1	0	0xefdff000 - 0xefdfefff (0x0) MX[B]O
	[7] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[8] -1	0	0xefec0000 - 0xefedffff (0x20000) MX[B](B)
	[9] -1	0	0xefef0000 - 0xefefffff (0x10000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000de00 - 0x0000de3f (0x40) IX[B]
	[14] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[16] -1	0	0x0000dc00 - 0x0000dbff (0x0) IX[B]O
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Reloading /usr/X11R6/lib/modules/drivers/radeon_drv.o
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xeffff000 - 0xefffffff (0x1000) MX[B]
	[6] -1	0	0xefdff000 - 0xefdfefff (0x0) MX[B]O
	[7] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[8] -1	0	0xefec0000 - 0xefedffff (0x20000) MX[B](B)
	[9] -1	0	0xefef0000 - 0xefefffff (0x10000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000de00 - 0x0000de3f (0x40) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[19] -1	0	0x0000dc00 - 0x0000dbff (0x0) IX[B]O
	[20] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[21] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0xefef0000
(II) RADEON(0): PCI bus 1 card 5 func 0
(**) RADEON(0): Depth 16, (--) framebuffer bpp 16
(II) RADEON(0): Pixel depth = 16 bits stored in 2 bytes (16 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(**) RADEON(0): Option "AGPMode" "4"
(**) RADEON(0): Option "AGPFastWrite" "true"
(**) RADEON(0): Option "RenderAccel" "true"
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 565
(II) RADEON(0): Using 6 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 7500 QW (AGP/PCI)" (ChipID = 0x5157)
(--) RADEON(0): Linear framebuffer at 0xd8000000
(--) RADEON(0): BIOS at 0xefec0000
(II) RADEON(0): Video RAM override, using 65536 kB instead of 65536 kB
(**) RADEON(0): VideoRAM: 65536 kByte (128 bit DDR SDRAM)
(II) RADEON(0): AGP card detected
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Connector0: DDCType-2, DACType-0, TMDSType-0, ConnectorType-3
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Type: 1
(II) RADEON(0): EDID data from the display on port 1 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 109  Serial#: 1279603001
(II) RADEON(0): Year: 2005  Week: 12
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 35  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): #5: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #6: hsize: 2048  vsize 1536  refresh: 60  vid: 16609
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 96 kHz, PixClock max 250 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HCGY311232
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- CRT
 Connector -- DVI-I
 DAC Type  -- Primary
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- None
 DAC Type  -- Unknown
 TMDS Type -- NONE
 DDC Type  -- NONE

---

### Post by KamakazieX on 2006-01-05
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=35000; xclk=18000
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): SyncMaster997DF: Using hsync range of 30.00-96.00 kHz
(II) RADEON(0): SyncMaster997DF: Using vrefresh range of 50.00-160.00 Hz
(II) RADEON(0): Clock range:  20.00 to 350.00 MHz
(II) RADEON(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(WW) (2048x1536,SyncMaster997DF) mode clock 266.95MHz exceeds DDC maximum 250MHz
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(--) RADEON(0): Virtual size is 1280x1024 (pitch 1280)
(**) RADEON(0): *Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1280x1024"  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync
(**) RADEON(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) RADEON(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) RADEON(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) RADEON(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) RADEON(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) RADEON(0):  Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) RADEON(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) RADEON(0):  Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) RADEON(0):  Default mode "1280x960": 148.5 MHz, 85.9 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1280x960"  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync
(**) RADEON(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) RADEON(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
(**) RADEON(0):  Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
(II) RADEON(0): Modeline "1152x864"  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync
(**) RADEON(0):  Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) RADEON(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) RADEON(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) RADEON(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) RADEON(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) RADEON(0):  Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) RADEON(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) RADEON(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) RADEON(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) RADEON(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.1 Hz (I)
(II) RADEON(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) RADEON(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) RADEON(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) RADEON(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) RADEON(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) RADEON(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) RADEON(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) RADEON(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) RADEON(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) RADEON(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) RADEON(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) RADEON(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) RADEON(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) RADEON(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) RADEON(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 87.1 Hz (D)
(II) RADEON(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) RADEON(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) RADEON(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) RADEON(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) RADEON(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) RADEON(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) RADEON(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) RADEON(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(++) RADEON(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(**) RADEON(0): Using AGP 4x mode
(**) RADEON(0): Enabling AGP Fast Write
(II) RADEON(0): Depth moves disabled by default
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/X11R6/lib/modules/libshadowfb.a
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) RADEON(0): Page flipping disabled
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xefef0000 - 0xefefffff (0x10000) MX[B]
	[1] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xeffff000 - 0xefffffff (0x1000) MX[B]
	[8] -1	0	0xefdff000 - 0xefdfefff (0x0) MX[B]O
	[9] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[10] -1	0	0xefec0000 - 0xefedffff (0x20000) MX[B](B)
	[11] -1	0	0xefef0000 - 0xefefffff (0x10000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[16] 0	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000de00 - 0x0000de3f (0x40) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[22] -1	0	0x0000dc00 - 0x0000dbff (0x0) IX[B]O
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) RADEON(0): Write-combining range (0xd8000000,0x4000000)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) RADEON(0): [drm] DRM interface version 1.2
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:05.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xc8a6a000
(II) RADEON(0): [drm] mapped SAREA 0xc8a6a000 to 0xb3d90000
(II) RADEON(0): [drm] framebuffer handle = 0xd8000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): [agp] Mode 0x0f000217 [AGP 0x1022/0x7006; Card 0x1002/0x5157]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xe8000000
(II) RADEON(0): [agp] Ring mapped at 0xb3c8f000
(II) RADEON(0): [agp] ring read ptr handle = 0xe8101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb3c8e000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xe8102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb3a8e000
(II) RADEON(0): [agp] GART texture map handle = 0xe8302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xb35ae000
(II) RADEON(0): [drm] register handle = 0xefef0000
(II) RADEON(0): [dri] Visual configs initialized
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
(II) RADEON(0): Reserved area from (0,1024) to (1280,1026)
(II) RADEON(0): Largest offscreen area available: 1280 x 7165
(II) RADEON(0): Will use back buffer at offset 0xa00000
(II) RADEON(0): Will use depth buffer at offset 0xc80000
(II) RADEON(0): Will use 50176 kb for textures at offset 0xf00000
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(==) RADEON(0): Backing store disabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 1026)
(II) RADEON(0): Largest offscreen area available: 1280 x 7158
(WW) RADEON(0): Option "UseInternalAGPGART" is not used
(II) RADEON(0): X context handle = 0x00000001
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 11
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(II) RADEON(0): Direct rendering enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
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
(**) Option "Protocol" "Auto"
(**) Mouse1: Device: "/dev/psaux"
(**) Mouse1: Protocol: "Auto"
(**) Option "CorePointer"
(**) Mouse1: Core Pointer
(**) Option "Device" "/dev/psaux"
(==) Mouse1: Emulate3Buttons, Emulate3Timeout: 50
(==) Mouse1: Buttons: 3
(**) Option "SampleRate" "150"
(**) Mouse1: SampleRate: 150
(**) Option "CoreKeyboard"
(**) Keyboard1: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard1: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard1: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Keyboard1: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Keyboard1: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard1: CustomKeycodes disabled
(II) XINPUT: Adding extended input device "Keyboard1" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "Mouse1" (type: MOUSE)
(--) Mouse1: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse1: ps2EnableDataReporting: succeeded

---

### Post by KamakazieX on 2006-01-05
i also know i need the framebuffer off, its a waste of system resources on my 750mhz k7

---

### Post by KamakazieX on 2006-01-05
# glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  1 0 None
0x24 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  1 0 Slow
0x25 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  1 0 Slow
0x26 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  1 0 Slow
0x27 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  1 0 None
0x28 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  1 0 Slow
0x29 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  1 0 Slow
0x2a 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  1 0 Slow
0x2b 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  1 0 None
0x2c 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  1 0 Slow
0x2d 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  1 0 Slow
0x2e 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  1 0 Slow
0x2f 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  1 0 None
0x30 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  1 0 Slow
0x31 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  1 0 Slow
0x32 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  1 0 Slow



===

Anyone notice the descrepincies? The "radeon" driver claims direct rendering, where mesa renders once x is loaded?

---

### Post by jwmislan on 2006-01-05
Hi
fglrx only supports radeon 9200 and up . At least that's what the ati website says.
just use the radeon xorg driver & kernel radeon.ko module
The ATI AIW-7500 was supported by gatos in 2.4 kernels but not in 2.6 
 TV tuner, or capture Not Supported. 
accell should work,  you get about 1200-1400 fps
You need your motherboard agp controler chip eg. (via-agp), module loaded with 
apgart module, radeon, and drm,  to get acceleration working.

I'm using AIW 7500  - here's  my mods loaded from lsmod.
radeon                 68352  1
drm                    58004  2 radeon
via_agp                 9472  1
agpgart                32328  2 drm,via_agp

Should work  - give it a try

Johnwm

---

### Post by KamakazieX on 2006-01-06
I just compiled the kernel, AMD756 chipset K6 optimized (early K7 slot A) Radeon driver built, all in kernel. Im actually seeing lower framerates now..

Instead of the generic 686 kernel which puts out 204/183 im getting 84/78 and still no opengl????... anyone got any ideas?

---

### Post by KamakazieX on 2006-01-06
I ALWAYS had running opengl in mandrake, accelerated x came as a basic package, i dont get how its so hard to kill the framebuffer and build in this. Anyone?

---


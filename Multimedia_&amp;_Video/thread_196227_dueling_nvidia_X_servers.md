---
title: "dueling nvidia X servers"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by HankB on 2006-06-13
Backstory: I have put a second nvidia card in my PC so I could drive an HDTV monitor. Basically, I want to be able to play video material from my PC. At first I configured it as a two headed (monster :eek: ), but I ran into permissioning problems because the second head is tied to whoever logs into the primary screen. I found a better way to to that is to run a second X server on the other head. Rather than having it start from init, I can execute the command to start it with whatever comands (xine) I want run on that screen. 

And it works. To a point. When I start up the second server (:1), the screen on the first one (:0) shuts off. The server does not stop, but the screen goes dark and the monitor goes into low power mode. When I shut down server :1, server :0 turns back on line and everything is as it was.

I'd like to know how to decouple these servers. They're both driven by nvidia cards and I'm using the 'nvidia' driver.

The gritty details: Here's my config file for server :1 :
(HDTVxorg.conf)
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "HDTV Screen" 0 0
    Option 	   "AllowMouseOpenFail"  "yes"

EndSection

Section "Files"

        # paths to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/CID"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
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
EndSection

Section "Monitor"
    Identifier     "HDTV"
#    Option         "DPMS"
#	DisplaySize	852 480
#	HorizSync	31-89
#	VertRefresh	50-85
	# for GTW-P42M403 Plasma TV
	# what we really want is the native resolution:
	#     852x480 (mode 23)
	# Mode 	Horizontal 	Vertical 	Format 		Refresh
	# 23 	31.4 KHz 	60.0 Hz 	852 × 480 (WVGA) 	60
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
    BusID          "PCI:0:10:0"
EndSection

Section "Screen"
    Identifier     "HDTV Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "HDTV"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "920x520" "852x480"
    EndSubSection
EndSection

```

The script I run on startup:
HDTV.sh
```
#!/bin/sh
xine -f -g <path to video file to play>
```

Command I use to run it (as root, at the moment):
```
xinit ./HDTV.sh  -- :1 -config HDTVxorg.conf
```

Resulting log (Xorg.1.log):
```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux toonsinator 2.6.15-23-k7 #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Tue Jun 13 21:26:46 2006
(++) Using config file: "HDTVxorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "HDTV Screen" (0)
(**) |   |-->Monitor "HDTV"
(**) |   |-->Device "NVIDIA Corporation NV34 [GeForce FX 5200]"
(==) |-->Input Device "<default pointer>"
(==) |-->Input Device "<default keyboard>"
(WW) The core pointer device wasn't specified explicitly in the layout.
	Using the default mouse configuration.
(WW) The core keyboard device wasn't specified explicitly in the layout.
	Using the default keyboard configuration.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "AllowMouseOpenFail" "yes"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(--) using VT number 8

(II) PCI: PCI scan (all values are in hex)
<...>
(II) PCI: 01:00:0: chip 10de,0185 card 270f,1951 rev c1 class 03,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf9000000 - 0xfaffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:10:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xf8000000/24, 0xf0000000/27
(--) PCI:*(1:0:0) nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] rev 193, Mem @ 0xf9000000/24, 0xe8000000/27
(II) Addressable bus resource ranges are
<...>
	[29] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
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
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Video Driver
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:1:0:0) found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
<...>
	[34] 0	0	0x500203c0 - 0x500203df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:0:10:0
(--) NVIDIA(0): VideoRAM: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.27.02
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:0:10:0:
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0):     Gateway GatewayGTW-P42M403 (DFP-0)
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "920x520"; removing.
(WW) NVIDIA(0): No valid modes for "852x480"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 800 x 600
(--) NVIDIA(0): DPI set to (22, 29); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
<...>
	[36] 0	0	0x500203c0 - 0x500203df (0x20) IS[B]
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
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
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/psaux"
(--) <default pointer>: Device: "/dev/psaux"
(==) <default pointer>: Protocol: "Auto"
(**) Option "CorePointer"
(**) <default pointer>: Core Pointer
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(**) <default pointer>: ZAxisMapping: buttons 4, 5, 6 and 7
(**) <default pointer>: Buttons: 11
(**) Option "CoreKeyboard"
(**) <default keyboard>: Core Keyboard
(**) Option "Protocol" "standard"
(**) <default keyboard>: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) <default keyboard>: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) <default keyboard>: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) <default keyboard>: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) <default keyboard>: CustomKeycodes disabled
(II) XINPUT: Adding extended input device "<default keyboard>" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(--) <default pointer>: PnP-detected protocol: "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded
FreeFontPath: FPE "/usr/share/X11/fonts/misc" refcount is 2, should be 1; fixing.

```

(Note, some voluminous information was replaced by <...> If such things as address ranges are important, let me know and I'll attach a complete log.)

---

### Post by HankB on 2006-06-14
The key to this is "multiseat". (That was pointed out by someone on the nvidia support forums.) Ordinarily (I guess) the various X servers are coded to interact with each other. That behavior is Bad if different users are using different heads. ;) I dug around in the multiseat page in the official Wiki and found a link to a blog that showed starting the X server with the command line arguments 

```
-novtswitch -sharevts 
```

I added that to my command:
```
xinit ./HDTV.sh  -- :1  -novtswitch -sharevts  -config HDTVxorg.conf
```

Problem solved.

---

### Post by HankB on 2006-06-15
[QUOTE=HankB]
Problem solved.[/QUOTE]

Not quite. The video portion works, but now when I start the second server, it causes problems with the keyboard for the first server. It causes some keystrokes to be dropped and then picks one it likes and autorepeats it until the server is restarted. Shutting down the second server doesn;t even help.

I'm trying to figure out how to get the second X server to start without trying to commandeer the system keyboard.

thanks,
hank

---

### Post by HankB on 2006-06-17
[QUOTE=HankB]I'm trying to figure out how to get the second X server to start without trying to commandeer the system keyboard.[/QUOTE]

I sorted out this last part. There is a way to specifu a null keyboard and mouse and I did so using:

```
Section "InputDevice"
    Identifier  "NoKeyboard"
    Option         "CoreKeyboard"
    Driver "void"
EndSection

Section "InputDevice"
    Identifier  "NoMouse"
    Option         "CorePointer"
    Driver "void"
EndSection


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "HDTV Screen" 0 0
    Option         "AllowMouseOpenFail"  "yes"
        Option "SingleCard" "true"
       Option "IsolateDevice"  "PCI:0:10:0"
    InputDevice    "NoKeyboard"
    InputDevice    "NoMouse"
EndSection

```

Now my two X servers peacefully coexist. :D

---

### Post by hesoez on 2006-08-19
Hi,

I was having a similar idea.
A desktop(monitor with keyboard, mouse and first soundcard running gdm/gnome) and a settopbox(tv with remote and second soundcard running mythtv) on one pc simultaneously.
This is just what i was looking for to configure the x-servers, thank you.

grtz

---

### Post by HankB on 2007-12-28
I'm revisiting this. The option to direct mouse and keyboard to a "void" driver no longer seems to work:
```

...
(EE) No Input driver matching `void'
(EE) No Input driver matching `void'
No core keyboard

Fatal server error:
failed to initialize core devices
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":1.0"
      after 0 requests (0 known processed) with 0 events remaining.
```

:confused:

So any suggestions on how to configure an X server on a card separate from the console X server (both using nVidia chips) would be highly appreciated.

thanks
hank

---


---
title: "Boot with intel graphics without monitor switched on"
date: 2010-05-12
forum: Multimedia Software
---

### Post by tnat on 2010-05-12
Hi,

i'm trying since ubuntu karmic to set up a xorg.conf for a special purpose. I've a htpc connected to my tv. Intel GMA 4500, DVI->HDMI-cable connected, Lucid Lynx installed.

When the machine boots with the TV powered on, everything is perfect. xrandr reports all valid modes on output "DP2".
Without the TV powerd on, Lucid starts in the low graphics mode, with the funny zenity-message.

So far, i managed to disable all useless outputs (VGA1, HDMI1, DP1, HDMI2), leaving DP2 enabled. I managed this by assigning outputs to monitors and adding Option "Ignore" "True" to the corresponding monitor-sections.
My only remaining problem is, that the intel-driver reports no connected monitor on output DP2. The TV is connected, but shut off. :(

Has anyone got a hint to tell the driver to ignore the presence of a monitor?
If so, i'm a very happy guy. :)

xorg.conf
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
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
	Load  "glx"
	Load  "dri"
	Load  "record"
	Load  "dbe"
	Load  "dri2"
	Load  "extmod"
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
	Identifier   "DP2"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	Modeline "1280x720@50" 74.25 1216 1690 1730 1980 670 705 710 750 +hsync +vsync
EndSection

Section "Monitor"
        Identifier   "VGA1"
	Option	"Ignore" "True"
EndSection

Section "Monitor"
        Identifier   "HDMI1"
        Option  "Ignore" "True"
EndSection

Section "Monitor"
        Identifier   "DP1"
        Option  "Ignore" "True"
EndSection

Section "Monitor"
        Identifier   "HDMI2"
        Option  "Ignore" "True"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
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
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "4 Series Chipset Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
	Option	"ConnectedMonitor" "DP2"
	Option	"monitor-DP2" "DP2"
	Option	"monitor-VGA1" "VGA1"
        Option  "monitor-HDMI1" "HDMI1"
        Option  "monitor-DP1" "DP1"
        Option  "monitor-HDMI2" "HDMI2"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "DP2"
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes "1280x720@50"
	EndSubSection
EndSection

```

Xorg.*.log
```
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) G41
(--) intel(0): Chipset: "G41"
(II) intel(0): Output VGA1 using monitor section VGA1
(**) intel(0): Option "Ignore" "True"
(II) intel(0): Output HDMI1 using monitor section HDMI1
(**) intel(0): Option "Ignore" "True"
(II) intel(0): Output DP1 using monitor section DP1
(**) intel(0): Option "Ignore" "True"
(II) intel(0): Output HDMI2 using monitor section HDMI2
(**) intel(0): Option "Ignore" "True"
(II) intel(0): Output DP2 using monitor section DP2
(II) intel(0): EDID for output DP2
(II) intel(0): Output DP2 disconnected
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output DP2 disconnected
(WW) intel(0): Unable to find initial modes
(==) intel(0): video overlay key set to 0x101fe
(EE) intel(0): No modes.
(II) UnloadModule: "intel"
(EE) Screen(s) found, but none have a usable configuration.

```

```
Linux tv 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
```

xrandr output, when restart gdm with connected TV
```
Screen 0: minimum 320 x 200, current 1216 x 670, maximum 8192 x 8192
DP2 connected 1216x670+0+0 (normal left inverted right x axis y axis) 708mm x 398mm
   1280x720@50    50.0*+
   1920x1080      50.0 +   60.0  
   1280x720       50.0  
   720x576        50.0  
   640x480        60.0  

```

---

### Post by tnat on 2010-05-12
In the meantime i found out, that i messed up the outputs. My TV is connected to HDMI2, not DP2.
I've corrected this in the xorg.conf.

What i also have tried:
- i915.modeset=0 in the kernel-parameter-line
- Option "NoDDC" "True"
- Option "IgnoreEDID" "True"
- Option "DDCMode" "off"

No luck so far.

Xorg.*.log for my latest tests:
```
(II) intel(0): Output VGA using monitor section VGA1
(**) intel(0): Option "Ignore" "True"
xf86TokenToOptinfo: table is NULL
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): Output HDMI-1 using monitor section HDMI1
(**) intel(0): Option "Ignore" "True"
xf86TokenToOptinfo: table is NULL
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output HDMI-2 using monitor section HDMI2
(**) intel(0): Option "PreferredMode" "1280x720@50"
(**) intel(0): Option "Enable" "True"
(II) intel(0): I2C bus "HDMIDDC_C" initialized.
(II) intel(0): HDMI output 2 detected
(**) intel(0): Option "NoDDC"
(II) intel(0): DVI monitor detected on HDMI-2
(II) intel(0): EDID for output HDMI-2
(II) intel(0): Output HDMI-2 enabled by config file
(WW) intel(0): Unable to find initial modes
(EE) intel(0): Output HDMI-2 enabled but has no modes
(EE) intel(0): No valid modes.
(II) UnloadModule: "intel"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules/libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

```

"Output HDMI-2 enabled but has no modes" is really a shame, since i've added a valid modeline and set a "PreferredMode".

Is it really so complicated to tell the intel driver, it should ignore all, an to do what the xorg.conf is configured to?

---

### Post by tnat on 2010-05-14
Hello again,

i gave up, ... again. Nothing i tried was working. It seems, that the intel-driver is unable to work, without a connected Monitor.
I'm wondering about nobody had any hint. Am i the only one with a monitor not connected at boot? Does nobody use Ubuntu as a media-center? Since MyhtTV will not run long time until problems appear, its absolute necessary to reboot, when no recordings are scheduled!

Cheers,
Tom

---

### Post by jakobengdahl on 2010-05-16
I have pretty much the same problem with similar setup. I'm using Ubuntu installation as a MediaPC. I've tried googleing the problem, but all I can find is HDMI-sound-problems. 

Hope to find a real solution instead of rebooting every time the picture is gone.

---

### Post by Peter Jenkins on 2010-08-11
Hi,

Have you tried the xrandr tool?
I'm not sure if it is intended to do what you need, but playing a while with it I got my TV output status back to "connected" even after turning it off/unplugging the cable...

---

### Post by XabiX on 2010-10-11
I have exactly the same setup and i am able to boot with no TV. We have almost the same configuration so it's maybe on the kernel 2.6.35-22 and intel linux drivers 2.12.0 versions used.

Here is my setup:
> Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "TV"
EndSection

Section "Device"
        Identifier      "Intel HD Graphics"
        Driver          "intel"
        BusID           "PCI:0:2:0"

        Option          "monitor-VGA1" "none"
        Option          "monitor-DP1" "none"
        Option          "monitor-HDMI1" "none"
        Option          "monitor-HDMI2" "TSB-TV"

        Option         "ModeDebug" "true"
EndSection

Section "Monitor"
        Identifier      "TSB-TV"
        VendorName      "Toshiba"
        ModelName       "42WLG66"
        HorizSync       15.0 - 46.0
        VertRefresh     49.0 - 122.0
#        Option         "Enable"  "true"

#        Modeline "1920x1080i"   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync
#        Modeline "1920x1080i_28.00"  73.79  1920 1968 2160 2400  1080 1081 1084 1098 interlace -HSync +Vsync
#       Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
        Modeline "1280x720_50.0"   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync

#       Option "PreferredMode"  "1280x720_50"
EndSection

Section "Monitor"
        Identifier      "none"
        Option          "Ignore" "true"
EndSection

Section "Screen"
        Identifier      "TV"
        Device          "Intel HD Graphics"
        Monitor         "TSB-TV"
        DefaultDepth  24
        SubSection "Display"
                Depth          24              
                Modes         "1280x720_50.0"
#               Modes         "1920x1080i" "1920x1080i_28.00" "1366x768" "1280x720_50.0"
                #Virtual                1920 1080
        EndSubSection
EndSection

My Xorg.log:
```
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    35.878] X Protocol Version 11, Revision 0
[    35.878] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    35.878] Current Operating System: Linux xabix-desktop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64
[    35.878] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.35-22-generic root=UUID=0785fb3c-6674-41e4-a48e-73c3a8c7ed25 ro vga=791 quiet splash
[    35.878] Build Date: 16 September 2010  06:18:41PM
[    35.878] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    35.878] Current version of pixman: 0.18.4
[    35.878]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[    35.878] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    35.878] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 11 22:02:21 2010
[    35.879] (==) Using config file: "/etc/X11/xorg.conf"
[    35.879] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    35.879] (==) ServerLayout "Default Layout"
[    35.879] (**) |-->Screen "TV" (0)
[    35.879] (**) |   |-->Monitor "TSB-TV"
[    35.879] (**) |   |-->Device "Intel HD Graphics"
[    35.879] (==) Automatically adding devices
[    35.879] (==) Automatically enabling devices
[    35.880] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/cyrillic,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[    35.880] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    35.880] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    35.880] (II) Loader magic: 0x7d0200
[    35.880] (II) Module ABI versions:
[    35.880]    X.Org ANSI C Emulation: 0.4
[    35.880]    X.Org Video Driver: 8.0
[    35.880]    X.Org XInput driver : 11.0
[    35.880]    X.Org Server Extension : 4.0
[    35.880] (--) PCI:*(0:0:2:0) 8086:0042:1458:d000 rev 18, Mem @ 0xfb400000/4194304, 0xe0000000/268435456, I/O @ 0x0000ff00/8
[    35.881] (--) PCI: (0:4:0:0) 14f1:8852:d470:9022 rev 2, Mem @ 0xfb800000/2097152
[    35.881] (II) Open ACPI successful (/var/run/acpid.socket)
[    35.881] (II) LoadModule: "extmod"
[    35.881] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    35.881] (II) Module extmod: vendor="X.Org Foundation"
[    35.882]    compiled for 1.9.0, module version = 1.0.0
[    35.882]    Module class: X.Org Server Extension
[    35.882]    ABI class: X.Org Server Extension, version 4.0
[    35.882] (II) Loading extension MIT-SCREEN-SAVER
[    35.882] (II) Loading extension XFree86-VidModeExtension
[    35.882] (II) Loading extension XFree86-DGA
[    35.882] (II) Loading extension DPMS
[    35.882] (II) Loading extension XVideo
[    35.882] (II) Loading extension XVideo-MotionCompensation
[    35.882] (II) Loading extension X-Resource
[    35.882] (II) LoadModule: "dbe"
[    35.882] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    35.882] (II) Module dbe: vendor="X.Org Foundation"
[    35.882]    compiled for 1.9.0, module version = 1.0.0
[    35.882]    Module class: X.Org Server Extension
[    35.882]    ABI class: X.Org Server Extension, version 4.0
[    35.882] (II) Loading extension DOUBLE-BUFFER
[    35.882] (II) LoadModule: "glx"
[    35.882] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    35.882] (II) Module glx: vendor="X.Org Foundation"
[    35.882]    compiled for 1.9.0, module version = 1.0.0
[    35.882]    ABI class: X.Org Server Extension, version 4.0
[    35.882] (==) AIGLX enabled
[    35.882] (II) Loading extension GLX
[    35.882] (II) LoadModule: "record"
[    35.882] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    35.882] (II) Module record: vendor="X.Org Foundation"
[    35.882]    compiled for 1.9.0, module version = 1.13.0
[    35.882]    Module class: X.Org Server Extension
[    35.882]    ABI class: X.Org Server Extension, version 4.0
[    35.882] (II) Loading extension RECORD
[    35.882] (II) LoadModule: "dri"
[    35.883] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    35.883] (II) Module dri: vendor="X.Org Foundation"
[    35.883]    compiled for 1.9.0, module version = 1.0.0
[    35.883]    ABI class: X.Org Server Extension, version 4.0
[    35.883] (II) Loading extension XFree86-DRI
[    35.883] (II) LoadModule: "dri2"
[    35.883] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    35.883] (II) Module dri2: vendor="X.Org Foundation"
[    35.883]    compiled for 1.9.0, module version = 1.2.0
[    35.883]    ABI class: X.Org Server Extension, version 4.0
[    35.883] (II) Loading extension DRI2
[    35.883] (II) LoadModule: "intel"
[    35.883] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    35.883] (II) Module intel: vendor="X.Org Foundation"
[    35.883]    compiled for 1.9.0, module version = 2.12.0
[    35.883]    Module class: X.Org Video Driver
[    35.883]    ABI class: X.Org Video Driver, version 8.0
[    35.883] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
        Sandybridge, Sandybridge
[    35.884] (++) using VT number 7

[    35.886] drmOpenDevice: node name is /dev/dri/card0
[    35.886] drmOpenDevice: open result is 9, (OK)
[    35.888] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    35.888] drmOpenDevice: node name is /dev/dri/card0
[    35.888] drmOpenDevice: open result is 9, (OK)
[    35.888] drmOpenByBusid: drmOpenMinor returns 9
[    35.888] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    35.888] (**) intel(0): Depth 24, (--) framebuffer bpp 32
[    35.888] (==) intel(0): RGB weight 888
[    35.888] (==) intel(0): Default visual is TrueColor
[    35.888] (II) intel(0): Integrated Graphics Chipset: Intel(R) Clarkdale
[    35.888] (--) intel(0): Chipset: "Clarkdale"
[    35.888] (==) intel(0): video overlay key set to 0x101fe
[    35.905] (II) intel(0): Output VGA1 using monitor section none
[    35.905] (**) intel(0): Option "Ignore" "true"
[    35.915] (II) intel(0): Output HDMI1 using monitor section none
[    35.920] (II) intel(0): Output DP1 using monitor section none
[    35.929] (II) intel(0): Output HDMI2 using monitor section TSB-TV
[    35.938] (II) intel(0): Output HDMI3 has no monitor section
[    35.943] (II) intel(0): Output DP2 has no monitor section
[    35.948] (II) intel(0): Output DP3 has no monitor section
[    35.948] (**) intel(0): Option "ModeDebug" "true"
[    35.957] (II) intel(0): EDID for output HDMI2
[    35.966] (II) intel(0): EDID for output HDMI3
[    35.971] (II) intel(0): EDID for output DP2
[    35.977] (II) intel(0): EDID for output DP3
[    35.977] (II) intel(0): Output HDMI2 disconnected
[    35.977] (II) intel(0): Output HDMI3 disconnected
[    35.977] (II) intel(0): Output DP2 disconnected
[    35.977] (II) intel(0): Output DP3 disconnected
[    35.977] (WW) intel(0): No outputs definitely connected, trying again...
[    35.977] (II) intel(0): Output HDMI2 disconnected
[    35.977] (II) intel(0): Output HDMI3 disconnected
[    35.977] (II) intel(0): Output DP2 disconnected
[    35.977] (II) intel(0): Output DP3 disconnected
[    35.977] (WW) intel(0): Unable to find connected outputs - setting 1024x768 initial framebuffer
[    35.977] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    35.977] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    35.977] (==) intel(0): DPI set to (96, 96)
[    35.977] (II) Loading sub module "fb"
[    35.977] (II) LoadModule: "fb"
[    35.977] (II) Loading /usr/lib/xorg/modules/libfb.so
[    35.977] (II) Module fb: vendor="X.Org Foundation"
[    35.977]    compiled for 1.9.0, module version = 1.0.0
[    35.977]    ABI class: X.Org ANSI C Emulation, version 0.4
[    35.977] (==) Depth 24 pixmap format is 32 bpp
[    35.977] (II) intel(0): [DRI2] Setup complete
[    35.977] (II) intel(0): [DRI2]   DRI driver: i965
[    35.977] (**) intel(0): Tiling enabled
[    35.977] (**) intel(0): SwapBuffers wait enabled
[    35.977] (==) intel(0): VideoRam: 262144 KB
[    35.977] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    35.982] (II) UXA(0): Driver registered support for the following operations:
[    35.982] (II)         solid
[    35.982] (II)         copy
[    35.982] (II)         composite (RENDER acceleration)
[    35.982] (II)         put_image
[    35.982] (II)         get_image
[    35.982] (==) intel(0): Backing store disabled
[    35.982] (==) intel(0): Silken mouse enabled
[    35.982] (II) intel(0): Initializing HW Cursor
[    35.982] (EE) intel(0): Couldn't create pixmap for fbcon
[    35.982] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    35.983] (==) intel(0): DPMS enabled
[    35.983] (==) intel(0): Intel XvMC decoder enabled
[    35.983] (II) intel(0): Set up textured video
[    35.983] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    35.983] (II) intel(0): direct rendering: DRI2 Enabled
[    35.983] (--) RandR disabled
[    35.983] (II) Initializing built-in extension Generic Event Extension
[    35.983] (II) Initializing built-in extension SHAPE
[    35.983] (II) Initializing built-in extension MIT-SHM
[    35.983] (II) Initializing built-in extension XInputExtension
[    35.983] (II) Initializing built-in extension XTEST
[    35.983] (II) Initializing built-in extension BIG-REQUESTS
[    35.983] (II) Initializing built-in extension SYNC
[    35.983] (II) Initializing built-in extension XKEYBOARD
[    35.983] (II) Initializing built-in extension XC-MISC
[    35.983] (II) Initializing built-in extension SECURITY
[    35.983] (II) Initializing built-in extension XINERAMA
[    35.983] (II) Initializing built-in extension XFIXES
[    35.983] (II) Initializing built-in extension RENDER
[    35.983] (II) Initializing built-in extension RANDR
[    35.983] (II) Initializing built-in extension COMPOSITE
[    35.983] (II) Initializing built-in extension DAMAGE
[    35.983] (II) Initializing built-in extension GESTURE
[    35.989] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    35.989] (II) AIGLX: enabled GLX_INTEL_swap_event
[    35.989] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    35.989] (II) AIGLX: enabled GLX_SGI_make_current_read
[    35.989] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    35.989] (II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
[    35.989] (II) GLX: Initialized DRI2 GL provider for screen 0
[    36.003] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    36.008] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    36.008] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    36.008] (II) LoadModule: "evdev"
[    36.008] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.009] (II) Module evdev: vendor="X.Org Foundation"
[    36.009]    compiled for 1.9.0, module version = 2.3.2
[    36.009]    Module class: X.Org XInput Driver
[    36.009]    ABI class: X.Org XInput driver, version 11.0
[    36.009] (**) Power Button: always reports core events
[    36.009] (**) Power Button: Device: "/dev/input/event1"
[    36.030] (II) Power Button: Found keys
[    36.030] (II) Power Button: Configuring as keyboard
[    36.030] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    36.030] (**) Option "xkb_rules" "evdev"
[    36.030] (**) Option "xkb_model" "evdev"
[    36.030] (**) Option "xkb_layout" "fr"
[    36.032] (II) XKB: reuse xkmfile /var/lib/xkb/server-1773A72ADF3912178EB836318CC241E672AD6AB1.xkm
[    36.033] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    36.033] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    36.033] (**) Power Button: always reports core events
[    36.033] (**) Power Button: Device: "/dev/input/event0"
[    36.051] (II) Power Button: Found keys
[    36.051] (II) Power Button: Configuring as keyboard
[    36.051] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    36.051] (**) Option "xkb_rules" "evdev"
[    36.051] (**) Option "xkb_model" "evdev"
[    36.051] (**) Option "xkb_layout" "fr"
[    36.054] (II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event2)
[    36.054] (**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    36.054] (**) Dell Dell USB Keyboard: always reports core events
[    36.054] (**) Dell Dell USB Keyboard: Device: "/dev/input/event2"
[    36.092] (II) Dell Dell USB Keyboard: Found keys
[    36.092] (II) Dell Dell USB Keyboard: Configuring as keyboard
[    36.092] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
[    36.092] (**) Option "xkb_rules" "evdev"
[    36.092] (**) Option "xkb_model" "evdev"
[    36.092] (**) Option "xkb_layout" "fr"
[    36.092] (II) config/udev: Adding input device iMON Remote (15c2:0038) (/dev/input/event3)
[    36.092] (**) iMON Remote (15c2:0038): Applying InputClass "evdev pointer catchall"
[    36.092] (**) iMON Remote (15c2:0038): Applying InputClass "evdev keyboard catchall"
[    36.092] (**) iMON Remote (15c2:0038): always reports core events
[    36.092] (**) iMON Remote (15c2:0038): Device: "/dev/input/event3"
[    36.120] (II) iMON Remote (15c2:0038): Found 3 mouse buttons
[    36.120] (II) iMON Remote (15c2:0038): Found scroll wheel(s)
[    36.120] (II) iMON Remote (15c2:0038): Found relative axes
[    36.120] (II) iMON Remote (15c2:0038): Found x and y relative axes
[    36.120] (II) iMON Remote (15c2:0038): Found keys
[    36.120] (II) iMON Remote (15c2:0038): Configuring as mouse
[    36.120] (II) iMON Remote (15c2:0038): Configuring as keyboard
[    36.120] (**) iMON Remote (15c2:0038): YAxisMapping: buttons 4 and 5
[    36.120] (**) iMON Remote (15c2:0038): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    36.120] (II) XINPUT: Adding extended input device "iMON Remote (15c2:0038)" (type: KEYBOARD)
[    36.120] (**) Option "xkb_rules" "evdev"
[    36.120] (**) Option "xkb_model" "evdev"
[    36.120] (**) Option "xkb_layout" "fr"
[    36.120] (II) iMON Remote (15c2:0038): initialized for relative axes.
[    36.121] (II) config/udev: Adding input device iMON Remote (15c2:0038) (/dev/input/mouse0)
[    36.121] (II) No input driver/identifier specified (ignoring)
[    36.122] (II) config/udev: Adding input device IR-receiver inside an USB DVB receiver (/dev/input/event4)
[    36.122] (**) IR-receiver inside an USB DVB receiver: Applying InputClass "evdev keyboard catchall"
[    36.122] (**) IR-receiver inside an USB DVB receiver: always reports core events
[    36.122] (**) IR-receiver inside an USB DVB receiver: Device: "/dev/input/event4"
[    36.160] (II) IR-receiver inside an USB DVB receiver: Found keys
[    36.160] (II) IR-receiver inside an USB DVB receiver: Configuring as keyboard
[    36.160] (II) XINPUT: Adding extended input device "IR-receiver inside an USB DVB receiver" (type: KEYBOARD)
[    36.160] (**) Option "xkb_rules" "evdev"
[    36.160] (**) Option "xkb_model" "evdev"
[    36.160] (**) Option "xkb_layout" "fr"
[    36.471] (II) intel(0): EDID for output HDMI2
[    36.480] (II) intel(0): EDID for output HDMI3
[    36.485] (II) intel(0): EDID for output DP2
[    36.490] (II) intel(0): EDID for output DP3
[    36.501] (II) intel(0): EDID for output HDMI2
[    36.510] (II) intel(0): EDID for output HDMI3
[    36.515] (II) intel(0): EDID for output DP2
[    36.520] (II) intel(0): EDID for output DP3
[    36.530] (II) intel(0): EDID for output HDMI2
[    36.539] (II) intel(0): EDID for output HDMI3
[    36.544] (II) intel(0): EDID for output DP2
[    36.549] (II) intel(0): EDID for output DP3
[    42.073] (II) intel(0): EDID for output HDMI2
[    42.082] (II) intel(0): EDID for output HDMI3
[    42.087] (II) intel(0): EDID for output DP2
[    42.092] (II) intel(0): EDID for output DP3
```


My issue is that the screen boot with 1024x768 instead of 1280x720:
> xabix@xabix-desktop:~$ xrandr 
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)

If anyone knows what I am missing to have the right resolution plz let me know !

Thanks
XabiX

---

### Post by tnat on 2010-11-12
Hi,

i did not invest more time on this. But if you get the wrong resolution, it may be a similar problem. It's possible, that you get X running without any device connected. But without EDID the resolution cannot be verfied to be valid.

Tom

---

### Post by XabiX on 2010-11-12
Hi,
 
So there is no way to skip the EDID and force a resolution?
 
The doc for the Xorg config on Intel needs some refresh/update so we know what we can or cannot do.
 
The other solution is to load an EDID in a file to simulate that the TV is on. Is this supposed to work on intel drivers?
I tried but was not successfull.
 
Merci
XabiX

---

### Post by Mr Fat Bat on 2012-01-23
Was there ever a solution for this?

I've got an ATI (HDMI) -> TV setup.  It also fails to load the display if the monitor is switched off.

I've seen a few posts around that involve editing the EDID info, which I'm not big on.

---

### Post by tez1982 on 2013-01-03
I've got exactly the same problem a mythbuntu 12.04 htpc 
Radeon HD3000 with fglrx driver

It's connected to the TV by DVI but if the TV is off at boot then I can't get it to output a signal. Would vbe great if someone figured out how to force an output if the monitor is connected or not

---


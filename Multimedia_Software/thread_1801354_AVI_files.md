---
title: "AVI files"
date: 2011-07-10
forum: Multimedia Software
---

### Post by etrevio on 2011-07-10
Well, here it goes my first post in this forum ;)

After exhaustive searching, I wasn't able to find a solution to my problem with .avi files ](*,) . 

I now even don't know how to troubleshoot it now, there it go the sympthoms:

- When watching SOME (not all AVI files) after the first minute and a half  of perfect display and sound the video starts to distort a lot (like if it had delayed pixels) but de audio continues quite well.

- This happends regardless of the player used (Totem, GNOME Player, or VLC)

- The cause is not in the avi files (as far as I can tell) because I am able to see the same file inside a W7 virtual machine inside linux without any of this issues and it plays smoothly.

I don't know what to do now and it's so frustrating because it doesn't happend with every avi file :confused:. I did install the essential packages **faac faad lame non-free-codecs ubuntu-restricted-extras, **(according to this how-to: **[COLOR=#008C00][B][all variants]**[/COLOR] Comprehensive Multimedia & Video Howto*  [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)*[/B])but still the problem continues :([B].
[/B]
I don't know if someone has an idea of some other codec that I may be still missing or something else, but I really want to have this fixed :(

The specs of my system:
[I]LinuxMint 10 64-bits (Ubuntu 10.10 64-bits)
Intel HD Graphics
3GB Ram
Intel Core i3-350M[/I]

---

### Post by lidex on 2011-07-10
Is this using compiz? If so try disabing it. What are these outputs:
```
cat /var/log/Xorg.0.log
```
```
sudo lshw -C display
```

---

### Post by etrevio on 2011-07-10
lidex tank you so much for your reply :), and yes I have compiz effects enabled, I didn't know that could be an issue :???:

The output from those to codes is quite large, hope is right:

```
erick@erick-NV59C ~ $ cat /var/log/Xorg.0.log
[    20.985] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    20.985] X Protocol Version 11, Revision 0
[    20.985] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    20.985] Current Operating System: Linux erick-NV59C 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64
[    20.985] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=3ee7afc0-6e8d-4c46-b56e-440edc88181a ro vga=792 splash quiet splash
[    20.985] Build Date: 16 September 2010  06:18:41PM
[    20.985] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    20.985] Current version of pixman: 0.18.4
[    20.985]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    20.985] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.985] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 10 16:55:12 2011
[    21.004] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.004] (==) No Layout section.  Using the first Screen section.
[    21.004] (==) No screen section available. Using defaults.
[    21.004] (**) |-->Screen "Default Screen Section" (0)
[    21.004] (**) |   |-->Monitor "<default monitor>"
[    21.004] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    21.004] (==) Automatically adding devices
[    21.004] (==) Automatically enabling devices
[    21.005] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.005]     Entry deleted from font path.
[    21.005] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    21.005] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.005] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.005] (II) Loader magic: 0x7d0200
[    21.005] (II) Module ABI versions:
[    21.005]     X.Org ANSI C Emulation: 0.4
[    21.005]     X.Org Video Driver: 8.0
[    21.005]     X.Org XInput driver : 11.0
[    21.005]     X.Org Server Extension : 4.0
[    21.005] (--) PCI:*(0:0:2:0) 8086:0046:1025:036d rev 2, Mem @ 0xb0000000/4194304, 0xa0000000/268435456, I/O @ 0x00003050/8
[    21.005] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    21.005] (II) LoadModule: "extmod"
[    21.035] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.035] (II) Module extmod: vendor="X.Org Foundation"
[    21.035]     compiled for 1.9.0, module version = 1.0.0
[    21.035]     Module class: X.Org Server Extension
[    21.035]     ABI class: X.Org Server Extension, version 4.0
[    21.035] (II) Loading extension MIT-SCREEN-SAVER
[    21.035] (II) Loading extension XFree86-VidModeExtension
[    21.035] (II) Loading extension XFree86-DGA
[    21.035] (II) Loading extension DPMS
[    21.035] (II) Loading extension XVideo
[    21.035] (II) Loading extension XVideo-MotionCompensation
[    21.035] (II) Loading extension X-Resource
[    21.035] (II) LoadModule: "dbe"
[    21.036] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.036] (II) Module dbe: vendor="X.Org Foundation"
[    21.036]     compiled for 1.9.0, module version = 1.0.0
[    21.036]     Module class: X.Org Server Extension
[    21.036]     ABI class: X.Org Server Extension, version 4.0
[    21.036] (II) Loading extension DOUBLE-BUFFER
[    21.036] (II) LoadModule: "glx"
[    21.036] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.036] (II) Module glx: vendor="X.Org Foundation"
[    21.036]     compiled for 1.9.0, module version = 1.0.0
[    21.036]     ABI class: X.Org Server Extension, version 4.0
[    21.036] (==) AIGLX enabled
[    21.036] (II) Loading extension GLX
[    21.036] (II) LoadModule: "record"
[    21.036] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.036] (II) Module record: vendor="X.Org Foundation"
[    21.036]     compiled for 1.9.0, module version = 1.13.0
[    21.036]     Module class: X.Org Server Extension
[    21.036]     ABI class: X.Org Server Extension, version 4.0
[    21.036] (II) Loading extension RECORD
[    21.036] (II) LoadModule: "dri"
[    21.036] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.036] (II) Module dri: vendor="X.Org Foundation"
[    21.036]     compiled for 1.9.0, module version = 1.0.0
[    21.036]     ABI class: X.Org Server Extension, version 4.0
[    21.036] (II) Loading extension XFree86-DRI
[    21.036] (II) LoadModule: "dri2"
[    21.037] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.037] (II) Module dri2: vendor="X.Org Foundation"
[    21.037]     compiled for 1.9.0, module version = 1.2.0
[    21.037]     ABI class: X.Org Server Extension, version 4.0
[    21.037] (II) Loading extension DRI2
[    21.037] (==) Matched intel as autoconfigured driver 0
[    21.037] (==) Matched vesa as autoconfigured driver 1
[    21.037] (==) Matched fbdev as autoconfigured driver 2
[    21.037] (==) Assigned the driver to the xf86ConfigLayout
[    21.037] (II) LoadModule: "intel"
[    21.037] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    21.037] (II) Module intel: vendor="X.Org Foundation"
[    21.037]     compiled for 1.9.0, module version = 2.12.0
[    21.037]     Module class: X.Org Video Driver
[    21.037]     ABI class: X.Org Video Driver, version 8.0
[    21.037] (II) LoadModule: "vesa"
[    21.037] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.038] (II) Module vesa: vendor="X.Org Foundation"
[    21.038]     compiled for 1.8.99.905, module version = 2.3.0
[    21.038]     Module class: X.Org Video Driver
[    21.038]     ABI class: X.Org Video Driver, version 8.0
[    21.038] (II) LoadModule: "fbdev"
[    21.038] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.038] (II) Module fbdev: vendor="X.Org Foundation"
[    21.038]     compiled for 1.8.99.905, module version = 0.4.2
[    21.038]     ABI class: X.Org Video Driver, version 8.0
[    21.038] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    21.038] (II) VESA: driver for VESA chipsets: vesa
[    21.038] (II) FBDEV: driver for framebuffer: fbdev
[    21.038] (++) using VT number 7

[    21.038] (WW) Falling back to old probe method for vesa
[    21.038] (WW) Falling back to old probe method for fbdev
[    21.038] (II) Loading sub module "fbdevhw"
[    21.038] (II) LoadModule: "fbdevhw"
[    21.046] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.047] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.047]     compiled for 1.9.0, module version = 0.0.2
[    21.047]     ABI class: X.Org Video Driver, version 8.0
[    21.048] drmOpenDevice: node name is /dev/dri/card0
[    21.048] drmOpenDevice: open result is 8, (OK)
[    21.048] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    21.048] drmOpenDevice: node name is /dev/dri/card0
[    21.048] drmOpenDevice: open result is 8, (OK)
[    21.048] drmOpenByBusid: drmOpenMinor returns 8
[    21.048] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    21.048] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    21.048] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    21.048] (==) intel(0): RGB weight 888
[    21.048] (==) intel(0): Default visual is TrueColor
[    21.048] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[    21.049] (--) intel(0): Chipset: "Arrandale"
[    21.049] (==) intel(0): video overlay key set to 0x101fe
[    21.065] (II) intel(0): Output VGA1 has no monitor section
[    21.066] (II) intel(0): Output LVDS1 has no monitor section
[    21.066] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    21.169] (II) intel(0): Output HDMI1 has no monitor section
[    21.174] (II) intel(0): Output DP1 has no monitor section
[    21.191] (II) intel(0): EDID for output VGA1
[    21.191] (II) intel(0): EDID for output LVDS1
[    21.191] (II) intel(0): Manufacturer: LGD  Model: 250  Serial#: 0
[    21.191] (II) intel(0): Year: 2010  Week: 0
[    21.191] (II) intel(0): EDID Version: 1.3
[    21.191] (II) intel(0): Digital Display Input
[    21.191] (II) intel(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[    21.191] (II) intel(0): Gamma: 2.20
[    21.191] (II) intel(0): No DPMS capabilities specified
[    21.191] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    21.191] (II) intel(0): First detailed timing is preferred mode
[    21.191] (II) intel(0): redX: 0.612 redY: 0.375   greenX: 0.332 greenY: 0.619
[    21.191] (II) intel(0): blueX: 0.151 blueY: 0.099   whiteX: 0.313 whiteY: 0.329
[    21.192] (II) intel(0): Manufacturer's mask: 0
[    21.192] (II) intel(0): Supported detailed timing:
[    21.192] (II) intel(0): clock: 72.3 MHz   Image Size:  345 x 194 mm
[    21.192] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[    21.192] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    21.192] (II) intel(0):  LG Display
[    21.192] (II) intel(0):  LP156WH2-TLEA
[    21.192] (II) intel(0): EDID (in hex):
[    21.192] (II) intel(0):     00ffffffffffff0030e4500200000000
[    21.192] (II) intel(0):     00140103802313780ac2d59c60559e26
[    21.192] (II) intel(0):     19505400000001010101010101010101
[    21.192] (II) intel(0):     0101010101013e1c56a0500016303020
[    21.192] (II) intel(0):     350059c2100000190000000000000000
[    21.192] (II) intel(0):     00000000000000000000000000fe004c
[    21.192] (II) intel(0):     4720446973706c61790a2020000000fe
[    21.192] (II) intel(0):     004c503135365748322d544c454100fd
[    21.192] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    21.192] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    21.192] (II) intel(0): Printing probed modes for output LVDS1
[    21.192] (II) intel(0): Modeline "1366x768"x60.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    21.192] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    21.192] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    21.192] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    21.192] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    21.192] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    21.192] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    21.201] (II) intel(0): EDID for output HDMI1
[    21.207] (II) intel(0): EDID for output DP1
[    21.207] (II) intel(0): Output VGA1 disconnected
[    21.207] (II) intel(0): Output LVDS1 connected
[    21.207] (II) intel(0): Output HDMI1 disconnected
[    21.207] (II) intel(0): Output DP1 disconnected
[    21.207] (II) intel(0): Using exact sizes for initial modes
[    21.207] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    21.207] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    21.207] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    21.207] (==) intel(0): DPI set to (96, 96)
[    21.207] (II) Loading sub module "fb"
[    21.207] (II) LoadModule: "fb"
[    21.207] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.207] (II) Module fb: vendor="X.Org Foundation"
[    21.207]     compiled for 1.9.0, module version = 1.0.0
[    21.207]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.207] (II) UnloadModule: "vesa"
[    21.207] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.207] (II) UnloadModule: "fbdev"
[    21.207] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.207] (II) UnloadModule: "fbdevhw"
[    21.207] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    21.207] (==) Depth 24 pixmap format is 32 bpp
[    21.207] (II) intel(0): [DRI2] Setup complete
[    21.207] (II) intel(0): [DRI2]   DRI driver: i965
[    21.207] (**) intel(0): Tiling enabled
[    21.207] (**) intel(0): SwapBuffers wait enabled
[    21.207] (==) intel(0): VideoRam: 262144 KB
[    21.207] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    21.214] (II) UXA(0): Driver registered support for the following operations:
[    21.214] (II)         solid
[    21.214] (II)         copy
[    21.214] (II)         composite (RENDER acceleration)
[    21.214] (II)         put_image
[    21.214] (II)         get_image
[    21.214] (==) intel(0): Backing store disabled
[    21.214] (==) intel(0): Silken mouse enabled
[    21.214] (II) intel(0): Initializing HW Cursor
[    21.251] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.258] (==) intel(0): DPMS enabled
[    21.258] (==) intel(0): Intel XvMC decoder enabled
[    21.258] (II) intel(0): Set up textured video
[    21.258] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    21.258] (II) intel(0): direct rendering: DRI2 Enabled
[    21.258] (--) RandR disabled
[    21.258] (II) Initializing built-in extension Generic Event Extension
[    21.258] (II) Initializing built-in extension SHAPE
[    21.258] (II) Initializing built-in extension MIT-SHM
[    21.258] (II) Initializing built-in extension XInputExtension
[    21.258] (II) Initializing built-in extension XTEST
[    21.258] (II) Initializing built-in extension BIG-REQUESTS
[    21.258] (II) Initializing built-in extension SYNC
[    21.258] (II) Initializing built-in extension XKEYBOARD
[    21.258] (II) Initializing built-in extension XC-MISC
[    21.258] (II) Initializing built-in extension SECURITY
[    21.258] (II) Initializing built-in extension XINERAMA
[    21.258] (II) Initializing built-in extension XFIXES
[    21.258] (II) Initializing built-in extension RENDER
[    21.258] (II) Initializing built-in extension RANDR
[    21.258] (II) Initializing built-in extension COMPOSITE
[    21.258] (II) Initializing built-in extension DAMAGE
[    21.258] (II) Initializing built-in extension GESTURE
[    21.267] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    21.267] (II) AIGLX: enabled GLX_INTEL_swap_event
[    21.267] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    21.267] (II) AIGLX: enabled GLX_SGI_make_current_read
[    21.267] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    21.268] (II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
[    21.268] (II) GLX: Initialized DRI2 GL provider for screen 0
[    21.268] (II) intel(0): Setting screen physical size to 361 x 203
[    21.284] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.292] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    21.292] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.292] (II) LoadModule: "evdev"
[    21.292] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.292] (II) Module evdev: vendor="X.Org Foundation"
[    21.292]     compiled for 1.9.0, module version = 2.3.2
[    21.292]     Module class: X.Org XInput Driver
[    21.292]     ABI class: X.Org XInput driver, version 11.0
[    21.292] (**) Power Button: always reports core events
[    21.292] (**) Power Button: Device: "/dev/input/event3"
[    21.321] (II) Power Button: Found keys
[    21.321] (II) Power Button: Configuring as keyboard
[    21.321] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    21.321] (**) Option "xkb_rules" "evdev"
[    21.321] (**) Option "xkb_model" "pc105"
[    21.321] (**) Option "xkb_layout" "latam"
[    21.323] (II) XKB: reuse xkmfile /var/lib/xkb/server-D39A7DF07EFAADA1B152E688CBEB9ED49E8BFDBB.xkm
[    21.324] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    21.324] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    21.324] (**) Video Bus: always reports core events
[    21.324] (**) Video Bus: Device: "/dev/input/event5"
[    21.361] (II) Video Bus: Found keys
[    21.361] (II) Video Bus: Configuring as keyboard
[    21.362] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    21.362] (**) Option "xkb_rules" "evdev"
[    21.362] (**) Option "xkb_model" "pc105"
[    21.362] (**) Option "xkb_layout" "latam"
[    21.363] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    21.363] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.363] (**) Power Button: always reports core events
[    21.363] (**) Power Button: Device: "/dev/input/event0"
[    21.391] (II) Power Button: Found keys
[    21.391] (II) Power Button: Configuring as keyboard
[    21.391] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    21.392] (**) Option "xkb_rules" "evdev"
[    21.392] (**) Option "xkb_model" "pc105"
[    21.392] (**) Option "xkb_layout" "latam"
[    21.392] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    21.392] (II) No input driver/identifier specified (ignoring)
[    21.392] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    21.392] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    21.392] (**) Sleep Button: always reports core events
[    21.392] (**) Sleep Button: Device: "/dev/input/event2"
[    21.421] (II) Sleep Button: Found keys
[    21.421] (II) Sleep Button: Configuring as keyboard
[    21.421] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    21.422] (**) Option "xkb_rules" "evdev"
[    21.422] (**) Option "xkb_model" "pc105"
[    21.422] (**) Option "xkb_layout" "latam"
[    21.424] (II) config/udev: Adding input device 1.3M WebCam (/dev/input/event6)
[    21.424] (**) 1.3M WebCam: Applying InputClass "evdev keyboard catchall"
[    21.424] (**) 1.3M WebCam: always reports core events
[    21.424] (**) 1.3M WebCam: Device: "/dev/input/event6"
[    21.451] (II) 1.3M WebCam: Found keys
[    21.451] (II) 1.3M WebCam: Configuring as keyboard
[    21.451] (II) XINPUT: Adding extended input device "1.3M WebCam" (type: KEYBOARD)
[    21.451] (**) Option "xkb_rules" "evdev"
[    21.451] (**) Option "xkb_model" "pc105"
[    21.452] (**) Option "xkb_layout" "latam"
[    21.456] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    21.456] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    21.456] (**) AT Translated Set 2 keyboard: always reports core events
[    21.456] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    21.481] (II) AT Translated Set 2 keyboard: Found keys
[    21.481] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    21.481] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    21.481] (**) Option "xkb_rules" "evdev"
[    21.481] (**) Option "xkb_model" "pc105"
[    21.481] (**) Option "xkb_layout" "latam"
[    21.481] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    21.481] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    21.481] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    21.481] (II) LoadModule: "synaptics"
[    21.482] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    21.482] (II) Module synaptics: vendor="X.Org Foundation"
[    21.482]     compiled for 1.9.0, module version = 1.2.2
[    21.482]     Module class: X.Org XInput Driver
[    21.482]     ABI class: X.Org XInput driver, version 11.0
[    21.482] (II) Synaptics touchpad driver version 1.2.2
[    21.482] (**) Option "Device" "/dev/input/event7"
[    21.651] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5772
[    21.652] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5086
[    21.652] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    21.652] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    21.652] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[    21.891] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    21.892] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    21.951] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    21.951] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    21.951] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    21.951] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    21.951] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    22.060] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    22.061] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    22.061] (II) No input driver/identifier specified (ignoring)
[    22.959] (II) intel(0): EDID vendor "LGD", prod id 592
[    22.959] (II) intel(0): Printing DDC gathered Modelines:
[    22.959] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    22.991] (II) intel(0): EDID vendor "LGD", prod id 592
[    22.992] (II) intel(0): Printing DDC gathered Modelines:
[    22.992] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    23.057] (II) intel(0): EDID vendor "LGD", prod id 592
[    23.057] (II) intel(0): Printing DDC gathered Modelines:
[    23.057] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    23.089] (II) intel(0): EDID vendor "LGD", prod id 592
[    23.089] (II) intel(0): Printing DDC gathered Modelines:
[    23.090] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    33.020] (II) intel(0): EDID vendor "LGD", prod id 592
[    33.020] (II) intel(0): Printing DDC gathered Modelines:
[    33.020] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    33.080] (II) intel(0): EDID vendor "LGD", prod id 592
[    33.080] (II) intel(0): Printing DDC gathered Modelines:
[    33.080] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    33.112] (II) intel(0): EDID vendor "LGD", prod id 592
[    33.112] (II) intel(0): Printing DDC gathered Modelines:
[    33.112] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    33.529] (II) intel(0): EDID vendor "LGD", prod id 592
[    33.529] (II) intel(0): Printing DDC gathered Modelines:
[    33.529] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    38.232] (II) intel(0): EDID vendor "LGD", prod id 592
[    38.232] (II) intel(0): Printing DDC gathered Modelines:
[    38.232] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    53.633] (II) intel(0): EDID vendor "LGD", prod id 592
[    53.633] (II) intel(0): Printing DDC gathered Modelines:
[    53.633] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  1757.309] (II) intel(0): EDID vendor "LGD", prod id 592
[  1757.309] (II) intel(0): Printing DDC gathered Modelines:
[  1757.309] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2746.849] (II) intel(0): EDID vendor "LGD", prod id 592
[  2746.849] (II) intel(0): Printing DDC gathered Modelines:
[  2746.849] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2768.584] (II) intel(0): EDID vendor "LGD", prod id 592
[  2768.585] (II) intel(0): Printing DDC gathered Modelines:
[  2768.585] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2792.086] (II) intel(0): EDID vendor "LGD", prod id 592
[  2792.086] (II) intel(0): Printing DDC gathered Modelines:
[  2792.086] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2815.948] (II) intel(0): EDID vendor "LGD", prod id 592
[  2815.948] (II) intel(0): Printing DDC gathered Modelines:
[  2815.948] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  6383.335] (II) intel(0): EDID vendor "LGD", prod id 592
[  6383.335] (II) intel(0): Printing DDC gathered Modelines:
[  6383.335] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[ 11236.083] (II) intel(0): EDID vendor "LGD", prod id 592
[ 11236.083] (II) intel(0): Printing DDC gathered Modelines:
[ 11236.083] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[ 12577.453] (II) XKB: reuse xkmfile /var/lib/xkb/server-667046A4732C57734752CD3FFC65583835FBA83D.xkm
[ 14299.362] (II) intel(0): EDID vendor "LGD", prod id 592
[ 14299.433] (II) intel(0): Printing DDC gathered Modelines:
[ 14299.442] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[ 14619.357] (II) intel(0): EDID vendor "LGD", prod id 592
[ 14619.384] (II) intel(0): Printing DDC gathered Modelines:
[ 14619.393] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[ 15365.603] (II) intel(0): EDID vendor "LGD", prod id 592
[ 15365.654] (II) intel(0): Printing DDC gathered Modelines:
[ 15365.656] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[ 16148.373] (II) intel(0): EDID vendor "LGD", prod id 592
[ 16148.377] (II) intel(0): Printing DDC gathered Modelines:
[ 16148.377] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[ 16958.748] (II) intel(0): EDID vendor "LGD", prod id 592
[ 16958.797] (II) intel(0): Printing DDC gathered Modelines:
[ 16958.799] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[ 17446.257] (II) intel(0): EDID vendor "LGD", prod id 592
[ 17446.257] (II) intel(0): Printing DDC gathered Modelines:
[ 17446.257] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[ 18539.203] (II) intel(0): EDID vendor "LGD", prod id 592
[ 18539.230] (II) intel(0): Printing DDC gathered Modelines:
[ 18539.239] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[ 19105.249] (II) intel(0): EDID vendor "LGD", prod id 592
[ 19105.249] (II) intel(0): Printing DDC gathered Modelines:
[ 19105.249] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[ 19412.505] (II) intel(0): EDID vendor "LGD", prod id 592
[ 19412.505] (II) intel(0): Printing DDC gathered Modelines:
[ 19412.505] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[ 19717.684] (II) intel(0): EDID vendor "LGD", prod id 592
[ 19717.684] (II) intel(0): Printing DDC gathered Modelines:
[ 19717.684] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[ 20636.744] (II) intel(0): EDID vendor "LGD", prod id 592
[ 20636.744] (II) intel(0): Printing DDC gathered Modelines:
[ 20636.744] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[ 20940.249] (II) intel(0): EDID vendor "LGD", prod id 592
[ 20940.249] (II) intel(0): Printing DDC gathered Modelines:
[ 20940.249] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[ 22150.855] (II) intel(0): EDID vendor "LGD", prod id 592
[ 22150.855] (II) intel(0): Printing DDC gathered Modelines:
[ 22150.855] (II) intel(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[ 22327.196] (EE) intel(0): [DRI2] DRI2SwapComplete: bad drawable
[ 22544.364] (EE) intel(0): [DRI2] DRI2SwapComplete: bad drawable

```And for the second comand is:

```
erick@erick-NV59C ~ $ sudo lshw -C display
[sudo] password for erick: 
  *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:b0000000-b03fffff memory:a0000000-afffffff ioport:3050(size=8)

```I will post back after testing without compiz ;)

---

### Post by etrevio on 2011-07-10
Bad news ): , disabling compiz from **System -> Preferences -> Appearance -> Vissual Effects -> None ** makes no difference with the videos ):

---

### Post by Mark Phelps on 2011-07-11
I believe that AVI is just a "container" for files and not an actual codec.  The link below is to the fourcc site that talks about the real codes that are used to determine the video codec you need:

[http://www.fourcc.org/]("http://www.fourcc.org/")

---

### Post by lazii on 2011-07-11
You might want to try [http://medibuntu.org](http://medibuntu.org)

This will install some necessary codecs to your system if you don't already have them.

You may also want to try smplayer. After install you will also want to go to the website and update the player since ubuntu 10 is a little outdated.

Unfortunately, it sounds like the avi's are corrupted. From my expreience, windows players overlook the corrupted parts of vid files while in linux systems those same files will cause a crash.

Good luck.

---

### Post by etrevio on 2011-07-11
Thanks to Mark Phelps and lazii for your replies :D ...

With the suggestion of Mark I checked the AVI files with a Fourcc codec identifier (called "AVIcodec") and all of them are Xvid MPEG-4 video and MPEG Layer-3 audio, so there is no difference with this between tha ones that work and the ones that the video looks choppy :confused:

And for your approach lazii I have already those packages from medibuntu (faac, faad, lame, non-free-codecs and ubuntu-restricted-extras) but I will give the smplayer a try ;)

---

### Post by etrevio on 2011-07-11
I can't believe it but using smplayer give me a clue of where could be the problem!!! :D

I think it has to do with the interlace of the video because tweaking  some options in smplayer to see if it helped with anything (at first  smplayer didn't work neither), I founded that changing the option in  "Deinterlace" to any other (either "none", "linear blending", etc) made  the video look fine!!! :D

But this didn't solved the whole problem because whenever I start to see  the AVI video again from the begining, exactly at the same point gets  crappy again regardless of the "Deinterlace" option that was selected :(  (although changing again this option to any other makes the video look  fine again)

Does anyone have any idea to what could be the problem with this  interlace thing? Could it really be the files that are corrupted  regardless thet I am able to watch them flawlessly in a W7 VM?

EDIT: Forget the "Deinterlace" " thing I just tried it in VLC player and nothing ): ... Actually what seems to do the trick in SMplayer is to change any "Video" setting (Deinterlace, Filters, Rotate) but changing any of this in VLC player doesn't work :confused:

---

### Post by etrevio on 2011-07-12
New update... actually I found that the only option in VLC player that seems to do the same "workaround" as in SMPLayer is to disable the video track and then enabling it again (Video -> Video track -> Disable) when the video gets crappy :?

I hope that this info could be more useful to you since I think that people are more used to deal with VLC player issues now ;)

P.S. as extra info... when watching the videos in VLC player on a W7 VM the video seems crappy too after exactly the same second (not the audio as usual)!!! :o. Apparently the only player that seems to stream this files flawlessly up to now is WMedia Player on the VM.

Thank you for your insights and help to try to find where lays the problem here, and we are getting closer!!! :)

---


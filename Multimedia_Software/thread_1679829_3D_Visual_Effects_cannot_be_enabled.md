---
title: "3D Visual Effects cannot be enabled"
date: 2011-02-01
forum: Multimedia Software
---

### Post by iokara08 on 2011-02-01
Goodevening,

Yesterday I installed the Netbook edition of Ubuntu 10.10 on my Advent Netbook.
The visual effects cannot be activated since no option is available in the "Appearance" application.

I also tried to enter using the desktop edition environment but again it did not work.

My laptop contains the following graphic card:
*00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)*

Thank you in advance!:idea:

---

### Post by Yellow Pasque on 2011-02-01
Post or pastebin your /var/log/Xorg.0 file

---

### Post by iokara08 on 2011-02-01
Hi Temüjin,

Thanks for your reply,

I think that I have located the file that you are asking me to post but I really wonder if I can post it here since it seems to be very large.

I have found only the following files:
Xorg.0.log
Xorg.0.log.old

Is this one what you asked?

---

### Post by Yellow Pasque on 2011-02-01
Yes, Xorg.0.log

---

### Post by iokara08 on 2011-02-02
```
[I]
[    17.099] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    17.099] X Protocol Version 11, Revision 0
[    17.099] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    17.099] Current Operating System: Linux Adventukas 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686
[    17.099] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=34fb941e-596a-450a-82c2-374e89d90db0 ro quiet splash
[    17.099] Build Date: 09 January 2011  12:14:58PM
[    17.099] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    17.099] Current version of pixman: 0.18.4
[    17.099]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    17.099] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.100] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb  2 15:11:59 2011
[    17.120] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.121] (==) No Layout section.  Using the first Screen section.
[    17.121] (==) No screen section available. Using defaults.
[    17.121] (**) |-->Screen "Default Screen Section" (0)
[    17.121] (**) |   |-->Monitor "<default monitor>"
[    17.122] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    17.122] (==) Automatically adding devices
[    17.122] (==) Automatically enabling devices
[    17.123] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.123]     Entry deleted from font path.
[    17.123] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    17.123] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.123] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    17.123] (II) Loader magic: 0x81f9b00
[    17.123] (II) Module ABI versions:
[    17.124]     X.Org ANSI C Emulation: 0.4
[    17.124]     X.Org Video Driver: 8.0
[    17.124]     X.Org XInput driver : 11.0
[    17.124]     X.Org Server Extension : 4.0
[    17.126] (--) PCI:*(0:0:2:0) 8086:27ae:1462:0110 rev 3, Mem @ 0xdfe80000/524288, 0xc0000000/268435456, 0xdff00000/262144, I/O @ 0x0000d0f0/8
[    17.126] (--) PCI: (0:0:2:1) 8086:27a6:1462:0110 rev 3, Mem @ 0xdfe00000/524288
[    17.127] (II) Open ACPI successful (/var/run/acpid.socket)
[    17.127] (II) LoadModule: "extmod"
[    17.215] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.216] (II) Module extmod: vendor="X.Org Foundation"
[    17.216]     compiled for 1.9.0, module version = 1.0.0
[    17.216]     Module class: X.Org Server Extension
[    17.216]     ABI class: X.Org Server Extension, version 4.0
[    17.216] (II) Loading extension MIT-SCREEN-SAVER
[    17.216] (II) Loading extension XFree86-VidModeExtension
[    17.216] (II) Loading extension XFree86-DGA
[    17.216] (II) Loading extension DPMS
[    17.216] (II) Loading extension XVideo
[    17.216] (II) Loading extension XVideo-MotionCompensation
[    17.216] (II) Loading extension X-Resource
[    17.216] (II) LoadModule: "dbe"
[    17.217] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.218] (II) Module dbe: vendor="X.Org Foundation"
[    17.218]     compiled for 1.9.0, module version = 1.0.0
[    17.218]     Module class: X.Org Server Extension
[    17.218]     ABI class: X.Org Server Extension, version 4.0
[    17.218] (II) Loading extension DOUBLE-BUFFER
[    17.218] (II) LoadModule: "glx"
[    17.219] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    17.219] (II) Module glx: vendor="X.Org Foundation"
[    17.219]     compiled for 1.9.0, module version = 1.0.0
[    17.219]     ABI class: X.Org Server Extension, version 4.0
[    17.219] (==) AIGLX enabled
[    17.219] (II) Loading extension GLX
[    17.219] (II) LoadModule: "record"
[    17.220] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.220] (II) Module record: vendor="X.Org Foundation"
[    17.220]     compiled for 1.9.0, module version = 1.13.0
[    17.220]     Module class: X.Org Server Extension
[    17.221]     ABI class: X.Org Server Extension, version 4.0
[    17.221] (II) Loading extension RECORD
[    17.221] (II) LoadModule: "dri"
[    17.221] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.222] (II) Module dri: vendor="X.Org Foundation"
[    17.222]     compiled for 1.9.0, module version = 1.0.0
[    17.222]     ABI class: X.Org Server Extension, version 4.0
[    17.222] (II) Loading extension XFree86-DRI
[    17.222] (II) LoadModule: "dri2"
[    17.223] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.223] (II) Module dri2: vendor="X.Org Foundation"
[    17.223]     compiled for 1.9.0, module version = 1.2.0
[    17.223]     ABI class: X.Org Server Extension, version 4.0
[    17.223] (II) Loading extension DRI2
[    17.223] (==) Matched intel as autoconfigured driver 0
[    17.223] (==) Matched vesa as autoconfigured driver 1
[    17.224] (==) Matched fbdev as autoconfigured driver 2
[    17.224] (==) Assigned the driver to the xf86ConfigLayout
[    17.224] (II) LoadModule: "intel"
[    17.225] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    17.225] (II) Module intel: vendor="X.Org Foundation"
[    17.225]     compiled for 1.9.0, module version = 2.12.0
[    17.225]     Module class: X.Org Video Driver
[    17.225]     ABI class: X.Org Video Driver, version 8.0
[    17.226] (II) LoadModule: "vesa"
[    17.226] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.227] (II) Module vesa: vendor="X.Org Foundation"
[    17.227]     compiled for 1.8.99.905, module version = 2.3.0
[    17.227]     Module class: X.Org Video Driver
[    17.227]     ABI class: X.Org Video Driver, version 8.0
[    17.227] (II) LoadModule: "fbdev"
[    17.228] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.228] (II) Module fbdev: vendor="X.Org Foundation"
[    17.228]     compiled for 1.8.99.905, module version = 0.4.2
[    17.228]     ABI class: X.Org Video Driver, version 8.0
[    17.228] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    17.231] (II) VESA: driver for VESA chipsets: vesa
[    17.231] (II) FBDEV: driver for framebuffer: fbdev
[    17.231] (++) using VT number 7

[    17.231] (WW) Falling back to old probe method for vesa
[    17.231] (WW) Falling back to old probe method for fbdev
[    17.231] (II) Loading sub module "fbdevhw"
[    17.231] (II) LoadModule: "fbdevhw"
[    17.233] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    17.233] (II) Module fbdevhw: vendor="X.Org Foundation"
[    17.233]     compiled for 1.9.0, module version = 0.0.2
[    17.233]     ABI class: X.Org Video Driver, version 8.0
[    17.237] drmOpenDevice: node name is /dev/dri/card0
[    17.237] drmOpenDevice: open result is 9, (OK)
[    17.237] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    17.237] drmOpenDevice: node name is /dev/dri/card0
[    17.237] drmOpenDevice: open result is 9, (OK)
[    17.237] drmOpenByBusid: drmOpenMinor returns 9
[    17.238] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    17.238] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    17.238] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    17.238] (==) intel(0): RGB weight 888
[    17.238] (==) intel(0): Default visual is TrueColor
[    17.238] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945GME
[    17.238] (--) intel(0): Chipset: "945GME"
[    17.238] (==) intel(0): video overlay key set to 0x101fe
[    17.269] (II) intel(0): Output VGA1 has no monitor section
[    17.269] (II) intel(0): Output LVDS1 has no monitor section
[    17.269] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    17.301] (II) intel(0): EDID for output VGA1
[    17.301] (II) intel(0): EDID for output LVDS1
[    17.301] (II) intel(0): Manufacturer: HSD  Model: 3e9  Serial#: 164401
[    17.301] (II) intel(0): Year: 2008  Week: 46
[    17.301] (II) intel(0): EDID Version: 1.3
[    17.301] (II) intel(0): Digital Display Input
[    17.301] (II) intel(0): Max Image Size [cm]: horiz.: 22  vert.: 13
[    17.301] (II) intel(0): Gamma: 2.20
[    17.301] (II) intel(0): No DPMS capabilities specified
[    17.301] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    17.302] (II) intel(0): First detailed timing is preferred mode
[    17.302] (II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.317 greenY: 0.564
[    17.302] (II) intel(0): blueX: 0.152 blueY: 0.131   whiteX: 0.310 whiteY: 0.330
[    17.302] (II) intel(0): Manufacturer's mask: 0
[    17.302] (II) intel(0): Supported detailed timing:
[    17.302] (II) intel(0): clock: 45.0 MHz   Image Size:  220 x 129 mm
[    17.302] (II) intel(0): h_active: 1024  h_sync: 1077  h_sync_end 1112 h_blank_end 1200 h_border: 0
[    17.302] (II) intel(0): v_active: 600  v_sync: 604  v_sync_end 609 v_blanking: 625 v_border: 0
[    17.302] (II) intel(0): Supported detailed timing:
[    17.302] (II) intel(0): clock: 51.4 MHz   Image Size:  220 x 129 mm
[    17.302] (II) intel(0): h_active: 1024  h_sync: 1117  h_sync_end 1152 h_blank_end 1240 h_border: 0
[    17.302] (II) intel(0): v_active: 600  v_sync: 617  v_sync_end 622 v_blanking: 638 v_border: 0
[    17.302] (II) intel(0):  
[    17.302] (II) intel(0):  
[    17.303] (II) intel(0): EDID (in hex):
[    17.303] (II) intel(0):     00ffffffffffff002264e90331820200
[    17.303] (II) intel(0):     2e12010380160d780a86269457519027
[    17.303] (II) intel(0):     214f5400000001010101010101010101
[    17.303] (II) intel(0):     010101010101941100b0405819203523
[    17.303] (II) intel(0):     4500dc8100000019161400d840582620
[    17.303] (II) intel(0):     5d231504dc8100000000000000fe0000
[    17.303] (II) intel(0):     000000000000000000000000000000fe
[    17.303] (II) intel(0):     000000000000000000010000000000f7
[    17.304] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    17.304] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    17.304] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    17.304] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    17.304] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    17.304] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    17.304] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    17.304] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    17.304] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    17.304] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    17.304] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    17.304] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    17.304] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    17.304] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    17.304] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    17.304] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    17.304] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    17.305] (II) intel(0): Printing probed modes for output LVDS1
[    17.305] (II) intel(0): Modeline "1024x600"x60.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    17.305] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.305] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    17.305] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.305] (II) intel(0): Output VGA1 disconnected
[    17.305] (II) intel(0): Output LVDS1 connected
[    17.305] (II) intel(0): Using exact sizes for initial modes
[    17.305] (II) intel(0): Output LVDS1 using initial mode 1024x600
[    17.305] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    17.305] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    17.305] (==) intel(0): DPI set to (96, 96)
[    17.305] (II) Loading sub module "fb"
[    17.305] (II) LoadModule: "fb"
[    17.307] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.307] (II) Module fb: vendor="X.Org Foundation"
[    17.307]     compiled for 1.9.0, module version = 1.0.0
[    17.307]     ABI class: X.Org ANSI C Emulation, version 0.4
[    17.307] (II) UnloadModule: "vesa"
[    17.307] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.307] (II) UnloadModule: "fbdev"
[    17.308] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.308] (II) UnloadModule: "fbdevhw"
[    17.308] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    17.308] (==) Depth 24 pixmap format is 32 bpp
[    17.308] (II) intel(0): [DRI2] Setup complete
[    17.308] (II) intel(0): [DRI2]   DRI driver: i915
[    17.308] (**) intel(0): Tiling enabled
[    17.308] (**) intel(0): SwapBuffers wait enabled
[    17.308] (==) intel(0): VideoRam: 262144 KB
[    17.308] (II) intel(0): Allocated new frame buffer 1024x600 stride 4096, tiled
[    17.309] (II) UXA(0): Driver registered support for the following operations:
[    17.309] (II)         solid
[    17.309] (II)         copy
[    17.309] (II)         composite (RENDER acceleration)
[    17.309] (II)         put_image
[    17.309] (II)         get_image
[    17.309] (==) intel(0): Backing store disabled
[    17.309] (==) intel(0): Silken mouse enabled
[    17.309] (II) intel(0): Initializing HW Cursor
[    17.344] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    17.385] (==) intel(0): DPMS enabled
[    17.385] (==) intel(0): Intel XvMC decoder disabled
[    17.385] (II) intel(0): Set up textured video
[    17.386] (II) intel(0): Set up overlay video
[    17.386] (II) intel(0): direct rendering: DRI2 Enabled
[    17.386] (--) RandR disabled
[    17.386] (II) Initializing built-in extension Generic Event Extension
[    17.386] (II) Initializing built-in extension SHAPE
[    17.386] (II) Initializing built-in extension MIT-SHM
[    17.386] (II) Initializing built-in extension XInputExtension
[    17.386] (II) Initializing built-in extension XTEST
[    17.387] (II) Initializing built-in extension BIG-REQUESTS
[    17.387] (II) Initializing built-in extension SYNC
[    17.387] (II) Initializing built-in extension XKEYBOARD
[    17.387] (II) Initializing built-in extension XC-MISC
[    17.387] (II) Initializing built-in extension SECURITY
[    17.387] (II) Initializing built-in extension XINERAMA
[    17.387] (II) Initializing built-in extension XFIXES
[    17.387] (II) Initializing built-in extension RENDER
[    17.387] (II) Initializing built-in extension RANDR
[    17.387] (II) Initializing built-in extension COMPOSITE
[    17.387] (II) Initializing built-in extension DAMAGE
[    17.387] (II) Initializing built-in extension GESTURE
[    17.437] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    17.437] (II) AIGLX: enabled GLX_INTEL_swap_event
[    17.437] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    17.437] (II) AIGLX: enabled GLX_SGI_make_current_read
[    17.437] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    17.438] (II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
[    17.438] (II) GLX: Initialized DRI2 GL provider for screen 0
[    17.439] (II) intel(0): Setting screen physical size to 270 x 158
[    17.515] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.539] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    17.540] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.540] (II) LoadModule: "evdev"
[    17.541] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.542] (II) Module evdev: vendor="X.Org Foundation"
[    17.542]     compiled for 1.9.0, module version = 2.3.2
[    17.542]     Module class: X.Org XInput Driver
[    17.542]     ABI class: X.Org XInput driver, version 11.0
[    17.542] (**) Power Button: always reports core events
[    17.542] (**) Power Button: Device: "/dev/input/event3"
[    17.561] (II) Power Button: Found keys
[    17.561] (II) Power Button: Configuring as keyboard
[    17.561] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    17.561] (**) Option "xkb_rules" "evdev"
[    17.561] (**) Option "xkb_model" "pc105"
[    17.561] (**) Option "xkb_layout" "us,gr"
[    17.561] (**) Option "xkb_variant" ","
[    17.561] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    17.572] (II) XKB: reuse xkmfile /var/lib/xkb/server-9078D1F245FADE3CB4AD835262E1036C04792E56.xkm
[    17.576] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    17.576] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    17.576] (**) Video Bus: always reports core events
[    17.576] (**) Video Bus: Device: "/dev/input/event5"
[    17.585] (II) Video Bus: Found keys
[    17.585] (II) Video Bus: Configuring as keyboard
[    17.585] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    17.585] (**) Option "xkb_rules" "evdev"
[    17.585] (**) Option "xkb_model" "pc105"
[    17.585] (**) Option "xkb_layout" "us,gr"
[    17.585] (**) Option "xkb_variant" ","
[    17.585] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    17.590] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    17.590] (II) No input driver/identifier specified (ignoring)
[    17.593] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    17.593] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.593] (**) Power Button: always reports core events
[    17.593] (**) Power Button: Device: "/dev/input/event1"
[    17.604] (II) Power Button: Found keys
[    17.604] (II) Power Button: Configuring as keyboard
[    17.604] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    17.604] (**) Option "xkb_rules" "evdev"
[    17.604] (**) Option "xkb_model" "pc105"
[    17.604] (**) Option "xkb_layout" "us,gr"
[    17.604] (**) Option "xkb_variant" ","
[    17.604] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    17.606] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    17.606] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    17.607] (**) Sleep Button: always reports core events
[    17.607] (**) Sleep Button: Device: "/dev/input/event2"
[    17.620] (II) Sleep Button: Found keys
[    17.620] (II) Sleep Button: Configuring as keyboard
[    17.620] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    17.620] (**) Option "xkb_rules" "evdev"
[    17.620] (**) Option "xkb_model" "pc105"
[    17.620] (**) Option "xkb_layout" "us,gr"
[    17.620] (**) Option "xkb_variant" ","
[    17.620] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    17.638] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    17.638] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    17.639] (**) AT Translated Set 2 keyboard: always reports core events
[    17.639] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    17.649] (II) AT Translated Set 2 keyboard: Found keys
[    17.649] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    17.649] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    17.649] (**) Option "xkb_rules" "evdev"
[    17.649] (**) Option "xkb_model" "pc105"
[    17.649] (**) Option "xkb_layout" "us,gr"
[    17.649] (**) Option "xkb_variant" ","
[    17.649] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    17.651] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    17.651] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    17.651] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    17.652] (II) LoadModule: "synaptics"
[    17.653] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    17.653] (II) Module synaptics: vendor="X.Org Foundation"
[    17.654]     compiled for 1.9.0, module version = 1.2.2
[    17.654]     Module class: X.Org XInput Driver
[    17.654]     ABI class: X.Org XInput driver, version 11.0
[    17.654] (II) Synaptics touchpad driver version 1.2.2
[    17.654] (**) Option "Device" "/dev/input/event6"
[    17.713] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    17.713] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    17.713] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    17.713] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    17.713] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[    17.745] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    17.745] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    17.761] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    17.761] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    17.761] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    17.761] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    17.761] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    17.797] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    17.798] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    17.798] (II) No input driver/identifier specified (ignoring)
[    19.192] (II) intel(0): EDID vendor "HSD", prod id 1001
[    19.192] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    19.192] (II) intel(0): Printing DDC gathered Modelines:
[    19.192] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    19.192] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    19.232] (II) intel(0): EDID vendor "HSD", prod id 1001
[    19.232] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    19.232] (II) intel(0): Printing DDC gathered Modelines:
[    19.232] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    19.232] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    19.272] (II) intel(0): EDID vendor "HSD", prod id 1001
[    19.272] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    19.272] (II) intel(0): Printing DDC gathered Modelines:
[    19.272] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    19.272] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    19.304] (II) intel(0): EDID vendor "HSD", prod id 1001
[    19.304] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    19.304] (II) intel(0): Printing DDC gathered Modelines:
[    19.304] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    19.304] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    94.541] (II) intel(0): EDID vendor "HSD", prod id 1001
[    94.541] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    94.541] (II) intel(0): Printing DDC gathered Modelines:
[    94.541] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    94.541] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    94.580] (II) intel(0): EDID vendor "HSD", prod id 1001
[    94.580] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    94.580] (II) intel(0): Printing DDC gathered Modelines:
[    94.580] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    94.581] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    94.620] (II) intel(0): EDID vendor "HSD", prod id 1001
[    94.620] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    94.620] (II) intel(0): Printing DDC gathered Modelines:
[    94.620] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    94.620] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    96.640] (II) intel(0): EDID vendor "HSD", prod id 1001
[    96.640] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    96.640] (II) intel(0): Printing DDC gathered Modelines:
[    96.640] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    96.640] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[   101.376] (II) intel(0): EDID vendor "HSD", prod id 1001
[   101.376] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   101.376] (II) intel(0): Printing DDC gathered Modelines:
[   101.376] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[   101.376] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[   425.612] (II) intel(0): EDID vendor "HSD", prod id 1001
[   425.612] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   425.612] (II) intel(0): Printing DDC gathered Modelines:
[   425.612] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[   425.612] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[  2674.168] (II) intel(0): EDID vendor "HSD", prod id 1001
[  2674.168] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[  2674.168] (II) intel(0): Printing DDC gathered Modelines:
[  2674.168] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[  2674.168] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[  3312.014] (EE) intel(0): [DRI2] DRI2SwapComplete: bad drawable
[  3615.844] (II) intel(0): EDID vendor "HSD", prod id 1001
[  3615.844] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[  3615.844] (II) intel(0): Printing DDC gathered Modelines:
[  3615.844] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[  3615.844] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[  7220.056] (II) AIGLX: Suspending AIGLX clients for VT switch
[  7223.025] (II) Open ACPI successful (/var/run/acpid.socket)
[  7223.025] (II) AIGLX: Resuming AIGLX clients after VT switch
[  7223.025] (EE) intel(0): Couldn't create pixmap for fbcon
[  7223.081] (II) intel(0): EDID vendor "HSD", prod id 1001
[  7223.081] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[  7223.081] (II) intel(0): Printing DDC gathered Modelines:
[  7223.081] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[  7223.081] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[  7223.120] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  7223.196] (II) Power Button: Device reopened after 1 attempts.
[  7223.204] (II) Video Bus: Device reopened after 1 attempts.
[  7223.216] (II) Power Button: Device reopened after 1 attempts.
[  7223.228] (II) Sleep Button: Device reopened after 1 attempts.
[  7223.240] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.

[/I]
```

---

### Post by Kirboosy on 2011-02-02
Did you install the compiz package? Ubuntu Netbook Remix doesn't include compiz so you have to install it yourself.

Synaptic Package Manager  -- System-->Admin-->Synaptic

in the quick search box type "compiz" 

check the package that appears. Also scroll through until you find one called "compiz-settings-manager" install that one as well. Allow it to mark any additional dependancies then hit Apply. Give it a minute or so to download and install. Reboot and you should be able to turn on Compiz. (unless you have a video card issue, but yours is an Intel which seems to be supported better than ATI)

---

### Post by iokara08 on 2011-02-02
Good evening Caboose885,

What you proposed worked! Thank you very much for your time.

My mistake was that I thought that I had installed Compiz....

I had done it from the "Ubuntu Software Center" but as I now understood I had installed only the settings manager.

But now the question is if I am able to use the 3D effects also in the Netbook edition? I always get the message that the mutter is running and that it is not possible to switch to any effects. Is there something that I can do about it?

Thank you again.

---

### Post by Kirboosy on 2011-02-02
Afternoon [iokara08]("http://ubuntuforums.org/member.php?u=942312"), (Its afternoon here ;)) 

Glad that was an easy fix. 

I'm not entirely sure how you would change it while running Unity. I know you can't just kill mutter. I don't think its a simple process to run compiz and unity, however, I'm not an authority on it because I have never tried. Maybe a quick Google search will return some positive results.


Good Luck!

---

### Post by Kirboosy on 2011-02-03
iokara08,

I discovered that if you have Unity 2D installed you can use compiz with it. Normal Unity (the one that came with Ubuntu Netbook Remix) does not support compiz.

Hope that clears some things up for you. :)

Here is a [link for Unity 2D]("http://www.webupd8.org/2011/01/unity-2d-qt-now-available-in-ppa-for.html")

---


---
title: "HDMI resolution 640x480, nVidia ION chip on Zotac ZBOX HD-ID11"
date: 2011-10-23
forum: Multimedia Software
---

### Post by bArrin_st on 2011-10-23
Hi all!

I recently installed Ubuntu (the latest version as of now - 11.10 x64 edition)on my Zotac ZBOX HD-ID11 HTPC, because I was fed up with the low performance I got on XP and W7.

So far, the computer is way quicker and more responsive on Ubuntu, so I would like to be able to continue using this OS.

The biggest problem I have at the moment is that the greatest resolution i get when I use the HDMI-connection is 640x480 pixels, as opposed to 720p resolution when running Windows (my TV is only capable of 720p).

If I connect to the TV with a VGA-cable, I get some higher resolutions (680x384, 800x400, 1024x768 - which it defaults to, 1152x864 and 1360x768). The 1360x768 resolution overscans horribly, so much infact, that even with the Overscan Compensation in NVIDIA X Settings set to max (200), i still can't se the leftmost part of the picture. But I would rather not use the VGA-cable, because I need that for my other computer.

I have been googling and reading differnet posts on resolution problems for over a week now, and I am not any closer to a solution.

I have tried to use xrandr to both add new modes and change to these new modes - nothing happens, except for the "xrandr: Configure crtc 0 failed"-error.

I've tried editing the xorg.conf multiple times, usually with no discernible results, but sometimes I lose all resolutions over 640x480 on the VGA-connection as well.

I have added the modes I would like to display to xorg.conf (Section "Screen", Subsection "Display") and I have tried to make it ignore the TV's EDID using Option "IgnoreEDID" "true" and Option "UseEDID" "false". Nothing changes.

I have edited the xorg.conf manually, I've let ubuntu create one for me, I've created one using the nVidia X Settings and I've tried running without an xorg.conf file. The results are always the same, I am never left with any other resolutions available than the ones I had to begin with.

I am starting to think that maybe I have to reinstall Windows in order to be able to use my ZBOX as a HTPC again, but I'd rather not, so I was hoping someone could point me in the right direction of how to force the resolution.

System info:
Zotac ZBOX HD-ID11 w/2GB RAM and 64GB SSD
([http://hothardware.com/Reviews/Zotac-ZBox-HDID11-and-Next-Gen-ION/](http://hothardware.com/Reviews/Zotac-ZBox-HDID11-and-Next-Gen-ION/))
nVidia driver: 280.13
OS: Ubuntu 11.10 x64
TV: Samsung LE37A436

/bArrin

---

### Post by BicyclerBoy on 2011-10-23
Post the /var/log/Xorg.0.log before making any changes so can see what is wrong.

Can you comment out the EDID stuff in xorg.conf & reconnect via HDMI & then restart X server then post:

/var/log/Xorg.0.log

(the TV needs to be on before X server loads)

This could be handy to get more (lots) info:
Option "ModeDubug"  "True"

---

### Post by bArrin_st on 2011-10-24
Ok, I will post the log file soon - I did too much tinkering so now I can't get it to start, so I am reinstalling now. Will post the log file as soon as I get it up and running again, and without any modifications to xorg.conf or any other files.

/bArrin

---

### Post by bArrin_st on 2011-10-24
Here is my clean Xorg.0.log file - just reinstalled Ubuntu.

```
[     6.313] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[     6.313] X Protocol Version 11, Revision 0
[     6.313] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[     6.313] Current Operating System: Linux ZBOX 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64
[     6.314] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=825df985-079f-4558-af76-536873d6e34b ro quiet splash vt.handoff=7
[     6.314] Build Date: 29 September 2011  02:45:13AM
[     6.314] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[     6.314] Current version of pixman: 0.22.2
[     6.314]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     6.314] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     6.315] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 24 11:51:19 2011
[     6.315] (==) Using config file: "/etc/X11/xorg.conf"
[     6.315] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     6.316] (==) No Layout section.  Using the first Screen section.
[     6.316] (==) No screen section available. Using defaults.
[     6.316] (**) |-->Screen "Default Screen Section" (0)
[     6.317] (**) |   |-->Monitor "<default monitor>"
[     6.317] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[     6.317] (**) |   |-->Device "Default Device"
[     6.317] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     6.317] (==) Automatically adding devices
[     6.317] (==) Automatically enabling devices
[     6.318] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     6.318]     Entry deleted from font path.
[     6.318] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     6.318]     Entry deleted from font path.
[     6.318] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     6.318]     Entry deleted from font path.
[     6.318] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     6.318]     Entry deleted from font path.
[     6.318] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     6.318]     Entry deleted from font path.
[     6.318] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[     6.318] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     6.319] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     6.319] (II) Loader magic: 0x7e0220
[     6.319] (II) Module ABI versions:
[     6.319]     X.Org ANSI C Emulation: 0.4
[     6.319]     X.Org Video Driver: 10.0
[     6.319]     X.Org XInput driver : 12.3
[     6.319]     X.Org Server Extension : 5.0
[     6.322] (--) PCI:*(0:3:0:0) 10de:0a64:19da:3100 rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/524288
[     6.323] (II) Open ACPI successful (/var/run/acpid.socket)
[     6.323] (II) LoadModule: "extmod"
[     6.325] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     6.326] (II) Module extmod: vendor="X.Org Foundation"
[     6.326]     compiled for 1.10.4, module version = 1.0.0
[     6.326]     Module class: X.Org Server Extension
[     6.326]     ABI class: X.Org Server Extension, version 5.0
[     6.326] (II) Loading extension MIT-SCREEN-SAVER
[     6.326] (II) Loading extension XFree86-VidModeExtension
[     6.326] (II) Loading extension XFree86-DGA
[     6.326] (II) Loading extension DPMS
[     6.326] (II) Loading extension XVideo
[     6.326] (II) Loading extension XVideo-MotionCompensation
[     6.326] (II) Loading extension X-Resource
[     6.326] (II) LoadModule: "dbe"
[     6.328] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     6.331] (II) Module dbe: vendor="X.Org Foundation"
[     6.332]     compiled for 1.10.4, module version = 1.0.0
[     6.332]     Module class: X.Org Server Extension
[     6.332]     ABI class: X.Org Server Extension, version 5.0
[     6.332] (II) Loading extension DOUBLE-BUFFER
[     6.332] (II) LoadModule: "glx"
[     6.332] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     6.360] (II) Module glx: vendor="NVIDIA Corporation"
[     6.360]     compiled for 4.0.2, module version = 1.0.0
[     6.360]     Module class: X.Org Server Extension
[     6.360] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:12:07 PDT 2011
[     6.360] (II) Loading extension GLX
[     6.360] (II) LoadModule: "record"
[     6.361] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     6.361] (II) Module record: vendor="X.Org Foundation"
[     6.362]     compiled for 1.10.4, module version = 1.13.0
[     6.362]     Module class: X.Org Server Extension
[     6.362]     ABI class: X.Org Server Extension, version 5.0
[     6.362] (II) Loading extension RECORD
[     6.362] (II) LoadModule: "dri"
[     6.363] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     6.364] (II) Module dri: vendor="X.Org Foundation"
[     6.364]     compiled for 1.10.4, module version = 1.0.0
[     6.364]     ABI class: X.Org Server Extension, version 5.0
[     6.364] (II) Loading extension XFree86-DRI
[     6.364] (II) LoadModule: "dri2"
[     6.365] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     6.365] (II) Module dri2: vendor="X.Org Foundation"
[     6.366]     compiled for 1.10.4, module version = 1.2.0
[     6.366]     ABI class: X.Org Server Extension, version 5.0
[     6.366] (II) Loading extension DRI2
[     6.366] (==) Matched nvidia as autoconfigured driver 0
[     6.366] (==) Matched nouveau as autoconfigured driver 1
[     6.366] (==) Matched nv as autoconfigured driver 2
[     6.366] (==) Matched vesa as autoconfigured driver 3
[     6.366] (==) Matched fbdev as autoconfigured driver 4
[     6.366] (==) Assigned the driver to the xf86ConfigLayout
[     6.366] (II) LoadModule: "nvidia"
[     6.366] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     6.368] (II) Module nvidia: vendor="NVIDIA Corporation"
[     6.368]     compiled for 4.0.2, module version = 1.0.0
[     6.368]     Module class: X.Org Video Driver
[     6.369] (II) LoadModule: "nouveau"
[     6.371] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     6.372] (II) Module nouveau: vendor="X.Org Foundation"
[     6.372]     compiled for 1.10.1, module version = 0.0.16
[     6.372]     Module class: X.Org Video Driver
[     6.372]     ABI class: X.Org Video Driver, version 10.0
[     6.372] (II) LoadModule: "nv"
[     6.375] (WW) Warning, couldn't open module nv
[     6.375] (II) UnloadModule: "nv"
[     6.375] (II) Unloading nv
[     6.375] (EE) Failed to load module "nv" (module does not exist, 0)
[     6.375] (II) LoadModule: "vesa"
[     6.377] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     6.377] (II) Module vesa: vendor="X.Org Foundation"
[     6.377]     compiled for 1.10.2, module version = 2.3.0
[     6.377]     Module class: X.Org Video Driver
[     6.377]     ABI class: X.Org Video Driver, version 10.0
[     6.377] (II) LoadModule: "fbdev"
[     6.378] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     6.378] (II) Module fbdev: vendor="X.Org Foundation"
[     6.378]     compiled for 1.10.0, module version = 0.4.2
[     6.378]     ABI class: X.Org Video Driver, version 10.0
[     6.379] (II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:55:26 PDT 2011
[     6.379] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     6.379] (II) NOUVEAU driver Date:   Thu Mar 24 02:13:12 2011 +1000
[     6.379] (II) NOUVEAU driver for NVIDIA chipset families :
[     6.379]     RIVA TNT        (NV04)
[     6.379]     RIVA TNT2       (NV05)
[     6.379]     GeForce 256     (NV10)
[     6.379]     GeForce 2       (NV11, NV15)
[     6.379]     GeForce 4MX     (NV17, NV18)
[     6.379]     GeForce 3       (NV20)
[     6.379]     GeForce 4Ti     (NV25, NV28)
[     6.379]     GeForce FX      (NV3x)
[     6.379]     GeForce 6       (NV4x)
[     6.380]     GeForce 7       (G7x)
[     6.380]     GeForce 8       (G8x)
[     6.380]     GeForce GTX 200 (NVA0)
[     6.380]     GeForce GTX 400 (NVC0)
[     6.380] (II) VESA: driver for VESA chipsets: vesa
[     6.380] (II) FBDEV: driver for framebuffer: fbdev
[     6.380] (++) using VT number 7

[     6.380] (II) Loading sub module "fb"
[     6.380] (II) LoadModule: "fb"
[     6.381] (II) Loading /usr/lib/xorg/modules/libfb.so
[     6.382] (II) Module fb: vendor="X.Org Foundation"
[     6.382]     compiled for 1.10.4, module version = 1.0.0
[     6.382]     ABI class: X.Org ANSI C Emulation, version 0.4
[     6.382] (II) Loading sub module "wfb"
[     6.382] (II) LoadModule: "wfb"
[     6.383] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     6.383] (II) Module wfb: vendor="X.Org Foundation"
[     6.383]     compiled for 1.10.4, module version = 1.0.0
[     6.383]     ABI class: X.Org ANSI C Emulation, version 0.4
[     6.383] (II) Loading sub module "ramdac"
[     6.383] (II) LoadModule: "ramdac"
[     6.383] (II) Module "ramdac" already built-in
[     6.383] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     6.383] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     6.383] (II) Loading /usr/lib/xorg/modules/libfb.so
[     6.384] (WW) Falling back to old probe method for vesa
[     6.384] (WW) Falling back to old probe method for fbdev
[     6.384] (II) Loading sub module "fbdevhw"
[     6.384] (II) LoadModule: "fbdevhw"
[     6.385] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     6.385] (II) Module fbdevhw: vendor="X.Org Foundation"
[     6.385]     compiled for 1.10.4, module version = 0.0.2
[     6.385]     ABI class: X.Org Video Driver, version 10.0
[     6.386] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     6.386] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     6.386] (==) NVIDIA(0): RGB weight 888
[     6.386] (==) NVIDIA(0): Default visual is TrueColor
[     6.386] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     6.386] (**) NVIDIA(0): Option "NoLogo" "True"
[     7.634] (WW) NVIDIA(GPU-0): The EDID read for display device CRT-0 is invalid:
[     7.634] (WW) NVIDIA(GPU-0):     unrecognized EDID Header.
[     7.668] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-1 is invalid:
[     7.668] (WW) NVIDIA(GPU-0):     unrecognized EDID Header.
[     7.672] (II) NVIDIA(0): NVIDIA GPU ION (GT218) at PCI:3:0:0 (GPU-0)
[     7.672] (--) NVIDIA(0): Memory: 524288 kBytes
[     7.672] (--) NVIDIA(0): VideoBIOS: 70.18.45.00.00
[     7.672] (II) NVIDIA(0): Detected PCI Express Link width: 1X
[     7.672] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[     7.672] (--) NVIDIA(0): Connected display device(s) on ION at PCI:3:0:0
[     7.672] (--) NVIDIA(0):     CRT-0
[     7.672] (--) NVIDIA(0):     DFP-1
[     7.672] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[     7.672] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[     7.672] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[     7.716] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
[     7.716] (**) NVIDIA(0):     enabled on all display devices.
[     7.727] (II) NVIDIA(0): Assigned Display Device: CRT-0
[     7.727] (==) NVIDIA(0): 
[     7.727] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     7.727] (==) NVIDIA(0):     will be used as the requested mode.
[     7.727] (==) NVIDIA(0): 
[     7.728] (II) NVIDIA(0): Validated modes:
[     7.728] (II) NVIDIA(0):     "nvidia-auto-select"
[     7.728] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[     7.750] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[     7.750] (WW) NVIDIA(0):     from CRT-0's EDID.
[     7.750] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[     7.750] (II) UnloadModule: "nouveau"
[     7.750] (II) Unloading nouveau
[     7.750] (II) UnloadModule: "vesa"
[     7.750] (II) Unloading vesa
[     7.750] (II) UnloadModule: "fbdev"
[     7.750] (II) Unloading fbdev
[     7.750] (II) UnloadModule: "fbdevhw"
[     7.750] (II) Unloading fbdevhw
[     7.750] (--) Depth 24 pixmap format is 32 bpp
[     7.751] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[     7.761] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[     7.797] (II) Loading extension NV-GLX
[     7.831] (==) NVIDIA(0): Disabling shared memory pixmaps
[     7.831] (==) NVIDIA(0): Backing store disabled
[     7.831] (==) NVIDIA(0): Silken mouse enabled
[     7.832] (==) NVIDIA(0): DPMS enabled
[     7.832] (II) Loading extension NV-CONTROL
[     7.833] (II) Loading extension XINERAMA
[     7.833] (II) Loading sub module "dri2"
[     7.833] (II) LoadModule: "dri2"
[     7.833] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     7.834] (II) Module dri2: vendor="X.Org Foundation"
[     7.834]     compiled for 1.10.4, module version = 1.2.0
[     7.834]     ABI class: X.Org Server Extension, version 5.0
[     7.834] (II) NVIDIA(0): [DRI2] Setup complete
[     7.834] (==) RandR enabled
[     7.834] (II) Initializing built-in extension Generic Event Extension
[     7.834] (II) Initializing built-in extension SHAPE
[     7.834] (II) Initializing built-in extension MIT-SHM
[     7.834] (II) Initializing built-in extension XInputExtension
[     7.834] (II) Initializing built-in extension XTEST
[     7.834] (II) Initializing built-in extension BIG-REQUESTS
[     7.834] (II) Initializing built-in extension SYNC
[     7.834] (II) Initializing built-in extension XKEYBOARD
[     7.834] (II) Initializing built-in extension XC-MISC
[     7.834] (II) Initializing built-in extension SECURITY
[     7.834] (II) Initializing built-in extension XINERAMA
[     7.834] (II) Initializing built-in extension XFIXES
[     7.834] (II) Initializing built-in extension RENDER
[     7.834] (II) Initializing built-in extension RANDR
[     7.834] (II) Initializing built-in extension COMPOSITE
[     7.834] (II) Initializing built-in extension DAMAGE
[     7.834] (II) Initializing built-in extension GESTURE
[     7.840] (II) Initializing extension GLX
[     7.896] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     7.923] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     7.923] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.923] (II) LoadModule: "evdev"
[     7.923] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.926] (II) Module evdev: vendor="X.Org Foundation"
[     7.926]     compiled for 1.10.2, module version = 2.6.0
[     7.926]     Module class: X.Org XInput Driver
[     7.926]     ABI class: X.Org XInput driver, version 12.3
[     7.926] (II) Using input driver 'evdev' for 'Power Button'
[     7.926] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.926] (**) Power Button: always reports core events
[     7.926] (**) Power Button: Device: "/dev/input/event1"
[     7.926] (--) Power Button: Found keys
[     7.926] (II) Power Button: Configuring as keyboard
[     7.926] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     7.926] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[     7.927] (**) Option "xkb_rules" "evdev"
[     7.927] (**) Option "xkb_model" "pc105"
[     7.927] (**) Option "xkb_layout" "no"
[     7.935] (II) XKB: reuse xkmfile /var/lib/xkb/server-5F8E417E6ED2D276BE32A8CA0E3DB916C21A8CA2.xkm
[     7.942] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     7.942] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.942] (II) Using input driver 'evdev' for 'Power Button'
[     7.942] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.942] (**) Power Button: always reports core events
[     7.942] (**) Power Button: Device: "/dev/input/event0"
[     7.942] (--) Power Button: Found keys
[     7.942] (II) Power Button: Configuring as keyboard
[     7.943] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     7.943] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[     7.943] (**) Option "xkb_rules" "evdev"
[     7.943] (**) Option "xkb_model" "pc105"
[     7.943] (**) Option "xkb_layout" "no"
[     7.952] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event4)
[     7.952] (II) No input driver/identifier specified (ignoring)
[     7.953] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event5)
[     7.953] (II) No input driver/identifier specified (ignoring)
[     7.954] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event6)
[     7.954] (II) No input driver/identifier specified (ignoring)
[     7.955] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event7)
[     7.955] (II) No input driver/identifier specified (ignoring)
[     7.963] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event2)
[     7.963] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
[     7.963] (II) Using input driver 'evdev' for 'Logitech Logitech BT Mini-Receiver'
[     7.963] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.963] (**) Logitech Logitech BT Mini-Receiver: always reports core events
[     7.963] (**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event2"
[     7.963] (--) Logitech Logitech BT Mini-Receiver: Found keys
[     7.963] (II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
[     7.963] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.2/1-5.2.2/1-5.2.2:1.0/input/input2/event2"
[     7.963] (II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
[     7.963] (**) Option "xkb_rules" "evdev"
[     7.963] (**) Option "xkb_model" "pc105"
[     7.964] (**) Option "xkb_layout" "no"
[     7.966] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event3)
[     7.966] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev pointer catchall"
[     7.966] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
[     7.966] (II) Using input driver 'evdev' for 'Logitech Logitech BT Mini-Receiver'
[     7.966] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.966] (**) Logitech Logitech BT Mini-Receiver: always reports core events
[     7.966] (**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event3"
[     7.967] (--) Logitech Logitech BT Mini-Receiver: Found 16 mouse buttons
[     7.967] (--) Logitech Logitech BT Mini-Receiver: Found scroll wheel(s)
[     7.967] (--) Logitech Logitech BT Mini-Receiver: Found relative axes
[     7.967] (--) Logitech Logitech BT Mini-Receiver: Found x and y relative axes
[     7.967] (--) Logitech Logitech BT Mini-Receiver: Found absolute axes
[     7.967] (II) evdev-grail: failed to open grail, no gesture support
[     7.967] (--) Logitech Logitech BT Mini-Receiver: Found keys
[     7.967] (II) Logitech Logitech BT Mini-Receiver: Configuring as mouse
[     7.967] (II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
[     7.967] (II) Logitech Logitech BT Mini-Receiver: Adding scrollwheel support
[     7.967] (**) Logitech Logitech BT Mini-Receiver: YAxisMapping: buttons 4 and 5
[     7.967] (**) Logitech Logitech BT Mini-Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     7.967] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.2/1-5.2.3/1-5.2.3:1.0/input/input3/event3"
[     7.967] (II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
[     7.967] (**) Option "xkb_rules" "evdev"
[     7.967] (**) Option "xkb_model" "pc105"
[     7.967] (**) Option "xkb_layout" "no"
[     7.968] (II) Logitech Logitech BT Mini-Receiver: initialized for relative axes.
[     7.968] (WW) Logitech Logitech BT Mini-Receiver: ignoring absolute axes.
[     7.969] (**) Logitech Logitech BT Mini-Receiver: (accel) keeping acceleration scheme 1
[     7.969] (**) Logitech Logitech BT Mini-Receiver: (accel) acceleration profile 0
[     7.969] (**) Logitech Logitech BT Mini-Receiver: (accel) acceleration factor: 2.000
[     7.969] (**) Logitech Logitech BT Mini-Receiver: (accel) acceleration threshold: 4
[     7.970] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/mouse0)
[     7.970] (II) No input driver/identifier specified (ignoring)
[    13.930] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[    65.755] (II) config/udev: Adding input device Logitech diNovo Edge (/dev/input/mouse1)
[    65.755] (II) No input driver/identifier specified (ignoring)
[    65.757] (II) config/udev: Adding input device Logitech diNovo Edge (/dev/input/event8)
[    65.757] (**) Logitech diNovo Edge: Applying InputClass "evdev pointer catchall"
[    65.757] (**) Logitech diNovo Edge: Applying InputClass "evdev keyboard catchall"
[    65.757] (II) Using input driver 'evdev' for 'Logitech diNovo Edge'
[    65.758] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    65.758] (**) Logitech diNovo Edge: always reports core events
[    65.758] (**) Logitech diNovo Edge: Device: "/dev/input/event8"
[    65.758] (--) Logitech diNovo Edge: Found 20 mouse buttons
[    65.758] (--) Logitech diNovo Edge: Found scroll wheel(s)
[    65.758] (--) Logitech diNovo Edge: Found relative axes
[    65.758] (--) Logitech diNovo Edge: Found x and y relative axes
[    65.758] (--) Logitech diNovo Edge: Found absolute axes
[    65.758] (II) evdev-grail: failed to open grail, no gesture support
[    65.758] (--) Logitech diNovo Edge: Found keys
[    65.758] (II) Logitech diNovo Edge: Configuring as mouse
[    65.758] (II) Logitech diNovo Edge: Configuring as keyboard
[    65.758] (II) Logitech diNovo Edge: Adding scrollwheel support
[    65.758] (**) Logitech diNovo Edge: YAxisMapping: buttons 4 and 5
[    65.758] (**) Logitech diNovo Edge: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    65.758] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.2/1-5.2.1/1-5.2.1:1.0/bluetooth/hci0/hci0:11/input8/event8"
[    65.759] (II) XINPUT: Adding extended input device "Logitech diNovo Edge" (type: KEYBOARD)
[    65.759] (**) Option "xkb_rules" "evdev"
[    65.759] (**) Option "xkb_model" "pc105"
[    65.759] (**) Option "xkb_layout" "no"
[    65.759] (II) Logitech diNovo Edge: initialized for relative axes.
[    65.759] (WW) Logitech diNovo Edge: ignoring absolute axes.
[    65.760] (**) Logitech diNovo Edge: (accel) keeping acceleration scheme 1
[    65.760] (**) Logitech diNovo Edge: (accel) acceleration profile 0
[    65.760] (**) Logitech diNovo Edge: (accel) acceleration factor: 2.000
[    65.760] (**) Logitech diNovo Edge: (accel) acceleration threshold: 4
[   113.628] (II) NVIDIA(0): Setting mode "CRT-0:1152x864@1152x864+0+0"
[   422.566] (II) XKB: reuse xkmfile /var/lib/xkb/server-5F8E417E6ED2D276BE32A8CA0E3DB916C21A8CA2.xkm
```

Also, here is my (pretty small) xorg.conf file - I have not edited anything in this after install either.

```

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection
```

/bArrin

---

### Post by bArrin_st on 2011-10-24
I didn't see your edit at first, so the Xorg.0.log file I posted is without the extra debug info. So I opened up xorg.conf and added the line ```
Option "ModeDebug" "True"
``` to the Device section. So now my xorg.conf looks like this: 

```
Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
    Option "ModeDebug" "True"
EndSection
```

and the Xorg.0.log looks like this:

```
[     6.742] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[     6.743] X Protocol Version 11, Revision 0
[     6.743] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[     6.743] Current Operating System: Linux ZBOX 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64
[     6.743] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=825df985-079f-4558-af76-536873d6e34b ro quiet splash vt.handoff=7
[     6.743] Build Date: 29 September 2011  02:45:13AM
[     6.743] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[     6.743] Current version of pixman: 0.22.2
[     6.743]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     6.743] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     6.744] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 24 14:22:16 2011
[     6.745] (==) Using config file: "/etc/X11/xorg.conf"
[     6.745] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     6.746] (==) No Layout section.  Using the first Screen section.
[     6.746] (==) No screen section available. Using defaults.
[     6.746] (**) |-->Screen "Default Screen Section" (0)
[     6.746] (**) |   |-->Monitor "<default monitor>"
[     6.747] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[     6.747] (**) |   |-->Device "Default Device"
[     6.747] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     6.747] (==) Automatically adding devices
[     6.747] (==) Automatically enabling devices
[     6.747] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     6.747]     Entry deleted from font path.
[     6.747] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     6.747]     Entry deleted from font path.
[     6.748] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     6.748]     Entry deleted from font path.
[     6.748] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     6.748]     Entry deleted from font path.
[     6.748] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     6.748]     Entry deleted from font path.
[     6.748] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[     6.748] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     6.748] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     6.748] (II) Loader magic: 0x7e0220
[     6.748] (II) Module ABI versions:
[     6.748]     X.Org ANSI C Emulation: 0.4
[     6.748]     X.Org Video Driver: 10.0
[     6.748]     X.Org XInput driver : 12.3
[     6.748]     X.Org Server Extension : 5.0
[     6.750] (--) PCI:*(0:3:0:0) 10de:0a64:19da:3100 rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/524288
[     6.751] (II) Open ACPI successful (/var/run/acpid.socket)
[     6.751] (II) LoadModule: "extmod"
[     6.752] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     6.752] (II) Module extmod: vendor="X.Org Foundation"
[     6.753]     compiled for 1.10.4, module version = 1.0.0
[     6.753]     Module class: X.Org Server Extension
[     6.753]     ABI class: X.Org Server Extension, version 5.0
[     6.753] (II) Loading extension MIT-SCREEN-SAVER
[     6.753] (II) Loading extension XFree86-VidModeExtension
[     6.753] (II) Loading extension XFree86-DGA
[     6.753] (II) Loading extension DPMS
[     6.753] (II) Loading extension XVideo
[     6.753] (II) Loading extension XVideo-MotionCompensation
[     6.753] (II) Loading extension X-Resource
[     6.753] (II) LoadModule: "dbe"
[     6.753] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     6.754] (II) Module dbe: vendor="X.Org Foundation"
[     6.754]     compiled for 1.10.4, module version = 1.0.0
[     6.754]     Module class: X.Org Server Extension
[     6.754]     ABI class: X.Org Server Extension, version 5.0
[     6.754] (II) Loading extension DOUBLE-BUFFER
[     6.754] (II) LoadModule: "glx"
[     6.754] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     6.775] (II) Module glx: vendor="NVIDIA Corporation"
[     6.775]     compiled for 4.0.2, module version = 1.0.0
[     6.775]     Module class: X.Org Server Extension
[     6.775] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:12:07 PDT 2011
[     6.775] (II) Loading extension GLX
[     6.775] (II) LoadModule: "record"
[     6.776] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     6.776] (II) Module record: vendor="X.Org Foundation"
[     6.776]     compiled for 1.10.4, module version = 1.13.0
[     6.776]     Module class: X.Org Server Extension
[     6.776]     ABI class: X.Org Server Extension, version 5.0
[     6.776] (II) Loading extension RECORD
[     6.776] (II) LoadModule: "dri"
[     6.777] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     6.777] (II) Module dri: vendor="X.Org Foundation"
[     6.777]     compiled for 1.10.4, module version = 1.0.0
[     6.777]     ABI class: X.Org Server Extension, version 5.0
[     6.777] (II) Loading extension XFree86-DRI
[     6.777] (II) LoadModule: "dri2"
[     6.778] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     6.778] (II) Module dri2: vendor="X.Org Foundation"
[     6.778]     compiled for 1.10.4, module version = 1.2.0
[     6.778]     ABI class: X.Org Server Extension, version 5.0
[     6.778] (II) Loading extension DRI2
[     6.778] (==) Matched nvidia as autoconfigured driver 0
[     6.779] (==) Matched nouveau as autoconfigured driver 1
[     6.779] (==) Matched nv as autoconfigured driver 2
[     6.779] (==) Matched vesa as autoconfigured driver 3
[     6.779] (==) Matched fbdev as autoconfigured driver 4
[     6.779] (==) Assigned the driver to the xf86ConfigLayout
[     6.779] (II) LoadModule: "nvidia"
[     6.779] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     6.780] (II) Module nvidia: vendor="NVIDIA Corporation"
[     6.780]     compiled for 4.0.2, module version = 1.0.0
[     6.780]     Module class: X.Org Video Driver
[     6.780] (II) LoadModule: "nouveau"
[     6.782] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     6.782] (II) Module nouveau: vendor="X.Org Foundation"
[     6.782]     compiled for 1.10.1, module version = 0.0.16
[     6.782]     Module class: X.Org Video Driver
[     6.782]     ABI class: X.Org Video Driver, version 10.0
[     6.783] (II) LoadModule: "nv"
[     6.787] (WW) Warning, couldn't open module nv
[     6.787] (II) UnloadModule: "nv"
[     6.787] (II) Unloading nv
[     6.788] (EE) Failed to load module "nv" (module does not exist, 0)
[     6.788] (II) LoadModule: "vesa"
[     6.789] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     6.790] (II) Module vesa: vendor="X.Org Foundation"
[     6.790]     compiled for 1.10.2, module version = 2.3.0
[     6.790]     Module class: X.Org Video Driver
[     6.790]     ABI class: X.Org Video Driver, version 10.0
[     6.790] (II) LoadModule: "fbdev"
[     6.791] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     6.792] (II) Module fbdev: vendor="X.Org Foundation"
[     6.792]     compiled for 1.10.0, module version = 0.4.2
[     6.792]     ABI class: X.Org Video Driver, version 10.0
[     6.792] (II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:55:26 PDT 2011
[     6.792] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     6.792] (II) NOUVEAU driver Date:   Thu Mar 24 02:13:12 2011 +1000
[     6.792] (II) NOUVEAU driver for NVIDIA chipset families :
[     6.792]     RIVA TNT        (NV04)
[     6.792]     RIVA TNT2       (NV05)
[     6.792]     GeForce 256     (NV10)
[     6.793]     GeForce 2       (NV11, NV15)
[     6.793]     GeForce 4MX     (NV17, NV18)
[     6.793]     GeForce 3       (NV20)
[     6.793]     GeForce 4Ti     (NV25, NV28)
[     6.793]     GeForce FX      (NV3x)
[     6.793]     GeForce 6       (NV4x)
[     6.793]     GeForce 7       (G7x)
[     6.794]     GeForce 8       (G8x)
[     6.794]     GeForce GTX 200 (NVA0)
[     6.794]     GeForce GTX 400 (NVC0)
[     6.794] (II) VESA: driver for VESA chipsets: vesa
[     6.794] (II) FBDEV: driver for framebuffer: fbdev
[     6.794] (++) using VT number 7

[     6.794] (II) Loading sub module "fb"
[     6.795] (II) LoadModule: "fb"
[     6.796] (II) Loading /usr/lib/xorg/modules/libfb.so
[     6.797] (II) Module fb: vendor="X.Org Foundation"
[     6.797]     compiled for 1.10.4, module version = 1.0.0
[     6.797]     ABI class: X.Org ANSI C Emulation, version 0.4
[     6.797] (II) Loading sub module "wfb"
[     6.797] (II) LoadModule: "wfb"
[     6.798] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     6.798] (II) Module wfb: vendor="X.Org Foundation"
[     6.798]     compiled for 1.10.4, module version = 1.0.0
[     6.798]     ABI class: X.Org ANSI C Emulation, version 0.4
[     6.798] (II) Loading sub module "ramdac"
[     6.798] (II) LoadModule: "ramdac"
[     6.799] (II) Module "ramdac" already built-in
[     6.799] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     6.799] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     6.799] (II) Loading /usr/lib/xorg/modules/libfb.so
[     6.799] (WW) Falling back to old probe method for vesa
[     6.799] (WW) Falling back to old probe method for fbdev
[     6.799] (II) Loading sub module "fbdevhw"
[     6.799] (II) LoadModule: "fbdevhw"
[     6.801] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     6.801] (II) Module fbdevhw: vendor="X.Org Foundation"
[     6.802]     compiled for 1.10.4, module version = 0.0.2
[     6.802]     ABI class: X.Org Video Driver, version 10.0
[     6.802] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     6.802] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     6.802] (==) NVIDIA(0): RGB weight 888
[     6.802] (==) NVIDIA(0): Default visual is TrueColor
[     6.802] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     6.802] (**) NVIDIA(0): Option "NoLogo" "True"
[     6.803] (**) NVIDIA(0): Option "ModeDebug" "True"
[     8.111] (WW) NVIDIA(GPU-0): The EDID read for display device CRT-0 is invalid:
[     8.111] (WW) NVIDIA(GPU-0):     unrecognized EDID Header.
[     8.145] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-1 is invalid:
[     8.146] (WW) NVIDIA(GPU-0):     unrecognized EDID Header.
[     8.149] (II) NVIDIA(0): NVIDIA GPU ION (GT218) at PCI:3:0:0 (GPU-0)
[     8.149] (--) NVIDIA(0): Memory: 524288 kBytes
[     8.149] (--) NVIDIA(0): VideoBIOS: 70.18.45.00.00
[     8.149] (II) NVIDIA(0): Detected PCI Express Link width: 1X
[     8.149] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[     8.149] (--) NVIDIA(0): Connected display device(s) on ION at PCI:3:0:0
[     8.149] (--) NVIDIA(0):     CRT-0
[     8.149] (--) NVIDIA(0):     DFP-1
[     8.149] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[     8.149] (--) NVIDIA(0): 
[     8.149] (--) NVIDIA(0): --- EDID for CRT-0 ---
[     8.149] (--) NVIDIA(0): 
[     8.149] (--) NVIDIA(0): No EDID Available.
[     8.149] (--) NVIDIA(0): 
[     8.150] (--) NVIDIA(0): --- End of EDID for CRT-0 ---
[     8.150] (--) NVIDIA(0): 
[     8.150] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[     8.150] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[     8.150] (--) NVIDIA(0): 
[     8.150] (--) NVIDIA(0): --- EDID for DFP-1 ---
[     8.150] (--) NVIDIA(0): 
[     8.150] (--) NVIDIA(0): No EDID Available.
[     8.150] (--) NVIDIA(0): 
[     8.150] (--) NVIDIA(0): --- End of EDID for DFP-1 ---
[     8.150] (--) NVIDIA(0): 
[     8.194] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
[     8.194] (**) NVIDIA(0):     enabled on all display devices.
[     8.194] (II) NVIDIA(0): Frequency information for CRT-0:
[     8.194] (II) NVIDIA(0):   HorizSync   : 28.000-55.000 kHz
[     8.194] (II) NVIDIA(0):   VertRefresh : 43.000-72.000 Hz
[     8.194] (II) NVIDIA(0):     (HorizSync from Conservative Defaults)
[     8.194] (II) NVIDIA(0):     (VertRefresh from Conservative Defaults)
[     8.194] (II) NVIDIA(0): 
[     8.194] (II) NVIDIA(0): --- Building ModePool for CRT-0 ---
[     8.194] (II) NVIDIA(0):   Validating Mode "640x350":
[     8.194] (II) NVIDIA(0):     640 x 350 @ 85 Hz
[     8.194] (II) NVIDIA(0):     Mode Source: X Server
[     8.194] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[     8.194] (II) NVIDIA(0):       HRes, HSyncStart :  640,  672
[     8.195] (II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
[     8.195] (II) NVIDIA(0):       VRes, VSyncStart :  350,  382
[     8.195] (II) NVIDIA(0):       VSyncEnd, VTotal :  385,  445
[     8.195] (II) NVIDIA(0):       H/V Polarity     : +/-
[     8.195] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
[     8.195] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.195] (II) NVIDIA(0): 
[     8.195] (II) NVIDIA(0):   Validating Mode "320x175":
[     8.195] (II) NVIDIA(0):     320 x 175 @ 85 Hz
[     8.195] (II) NVIDIA(0):     Mode Source: X Server
[     8.195] (II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
[     8.195] (II) NVIDIA(0):       HRes, HSyncStart :  320,  336
[     8.195] (II) NVIDIA(0):       HSyncEnd, HTotal :  368,  416
[     8.195] (II) NVIDIA(0):       VRes, VSyncStart :  175,  191
[     8.195] (II) NVIDIA(0):       VSyncEnd, VTotal :  192,  222
[     8.195] (II) NVIDIA(0):       H/V Polarity     : +/-
[     8.195] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.195] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
[     8.195] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.195] (II) NVIDIA(0): 
[     8.195] (II) NVIDIA(0):   Validating Mode "640x400":
[     8.195] (II) NVIDIA(0):     640 x 400 @ 85 Hz
[     8.195] (II) NVIDIA(0):     Mode Source: X Server
[     8.195] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[     8.195] (II) NVIDIA(0):       HRes, HSyncStart :  640,  672
[     8.195] (II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
[     8.195] (II) NVIDIA(0):       VRes, VSyncStart :  400,  401
[     8.195] (II) NVIDIA(0):       VSyncEnd, VTotal :  404,  445
[     8.195] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.196] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
[     8.196] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.196] (II) NVIDIA(0): 
[     8.196] (II) NVIDIA(0):   Validating Mode "320x200":
[     8.196] (II) NVIDIA(0):     320 x 200 @ 85 Hz
[     8.196] (II) NVIDIA(0):     Mode Source: X Server
[     8.196] (II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
[     8.196] (II) NVIDIA(0):       HRes, HSyncStart :  320,  336
[     8.196] (II) NVIDIA(0):       HSyncEnd, HTotal :  368,  416
[     8.196] (II) NVIDIA(0):       VRes, VSyncStart :  200,  200
[     8.196] (II) NVIDIA(0):       VSyncEnd, VTotal :  202,  222
[     8.196] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.196] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.196] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
[     8.196] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.196] (II) NVIDIA(0): 
[     8.196] (II) NVIDIA(0):   Validating Mode "720x400":
[     8.196] (II) NVIDIA(0):     720 x 400 @ 85 Hz
[     8.196] (II) NVIDIA(0):     Mode Source: X Server
[     8.196] (II) NVIDIA(0):       Pixel Clock      : 35.50 MHz
[     8.196] (II) NVIDIA(0):       HRes, HSyncStart :  720,  756
[     8.196] (II) NVIDIA(0):       HSyncEnd, HTotal :  828,  936
[     8.196] (II) NVIDIA(0):       VRes, VSyncStart :  400,  401
[     8.196] (II) NVIDIA(0):       VSyncEnd, VTotal :  404,  446
[     8.196] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.196] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
[     8.196] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.196] (II) NVIDIA(0): 
[     8.196] (II) NVIDIA(0):   Validating Mode "360x200":
[     8.197] (II) NVIDIA(0):     360 x 200 @ 85 Hz
[     8.197] (II) NVIDIA(0):     Mode Source: X Server
[     8.197] (II) NVIDIA(0):       Pixel Clock      : 17.75 MHz
[     8.197] (II) NVIDIA(0):       HRes, HSyncStart :  360,  378
[     8.197] (II) NVIDIA(0):       HSyncEnd, HTotal :  414,  468
[     8.197] (II) NVIDIA(0):       VRes, VSyncStart :  200,  200
[     8.197] (II) NVIDIA(0):       VSyncEnd, VTotal :  202,  223
[     8.197] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.197] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.197] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
[     8.197] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.197] (II) NVIDIA(0): 
[     8.197] (II) NVIDIA(0):   Validating Mode "640x480":
[     8.197] (II) NVIDIA(0):     640 x 480 @ 60 Hz
[     8.197] (II) NVIDIA(0):     Mode Source: X Server
[     8.197] (II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
[     8.197] (II) NVIDIA(0):       HRes, HSyncStart :  640,  656
[     8.197] (II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
[     8.197] (II) NVIDIA(0):       VRes, VSyncStart :  480,  490
[     8.197] (II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
[     8.197] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.198] (II) NVIDIA(GPU-0):     BestFit Centered         640x480
[     8.198] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[     8.198] (II) NVIDIA(GPU-0):       Vertical Taps          0
[     8.198] (II) NVIDIA(GPU-0):       Base SuperSample       x4
[     8.198] (II) NVIDIA(GPU-0):       Base Depth             32
[     8.198] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[     8.198] (II) NVIDIA(GPU-0):       Overlay Depth          32
[     8.198] (II) NVIDIA(0):     Mode is valid.
[     8.198] (II) NVIDIA(0): 
[     8.198] (II) NVIDIA(0):   Validating Mode "320x240":
[     8.198] (II) NVIDIA(0):     320 x 240 @ 60 Hz
[     8.198] (II) NVIDIA(0):     Mode Source: X Server
[     8.198] (II) NVIDIA(0):       Pixel Clock      : 12.59 MHz
[     8.198] (II) NVIDIA(0):       HRes, HSyncStart :  320,  328
[     8.198] (II) NVIDIA(0):       HSyncEnd, HTotal :  376,  400
[     8.198] (II) NVIDIA(0):       VRes, VSyncStart :  240,  245
[     8.198] (II) NVIDIA(0):       VSyncEnd, VTotal :  246,  262
[     8.198] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.198] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.199] (II) NVIDIA(GPU-0):     BestFit Centered         320x480
[     8.199] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[     8.199] (II) NVIDIA(GPU-0):       Vertical Taps          1
[     8.199] (II) NVIDIA(GPU-0):       Base SuperSample       x4
[     8.199] (II) NVIDIA(GPU-0):       Base Depth             32
[     8.199] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[     8.199] (II) NVIDIA(GPU-0):       Overlay Depth          32
[     8.199] (II) NVIDIA(0):     Mode is valid.
[     8.199] (II) NVIDIA(0): 
[     8.199] (II) NVIDIA(0):   Validating Mode "640x480":
[     8.199] (II) NVIDIA(0):     640 x 480 @ 73 Hz
[     8.199] (II) NVIDIA(0):     Mode Source: X Server
[     8.199] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[     8.199] (II) NVIDIA(0):       HRes, HSyncStart :  640,  664
[     8.199] (II) NVIDIA(0):       HSyncEnd, HTotal :  704,  832
[     8.199] (II) NVIDIA(0):       VRes, VSyncStart :  480,  489
[     8.199] (II) NVIDIA(0):       VSyncEnd, VTotal :  492,  520
[     8.200] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.200] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (72.8 Hz) out of range
[     8.200] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.200] (II) NVIDIA(0): 
[     8.200] (II) NVIDIA(0):   Validating Mode "320x240":
[     8.200] (II) NVIDIA(0):     320 x 240 @ 73 Hz
[     8.200] (II) NVIDIA(0):     Mode Source: X Server
[     8.200] (II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
[     8.200] (II) NVIDIA(0):       HRes, HSyncStart :  320,  332
[     8.200] (II) NVIDIA(0):       HSyncEnd, HTotal :  352,  416
[     8.200] (II) NVIDIA(0):       VRes, VSyncStart :  240,  244
[     8.200] (II) NVIDIA(0):       VSyncEnd, VTotal :  246,  260
[     8.200] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.200] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.200] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (72.8 Hz) out of range
[     8.200] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.200] (II) NVIDIA(0): 
[     8.200] (II) NVIDIA(0):   Validating Mode "640x480":
[     8.200] (II) NVIDIA(0):     640 x 480 @ 75 Hz
[     8.200] (II) NVIDIA(0):     Mode Source: X Server
[     8.200] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[     8.200] (II) NVIDIA(0):       HRes, HSyncStart :  640,  656
[     8.200] (II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
[     8.200] (II) NVIDIA(0):       VRes, VSyncStart :  480,  481
[     8.200] (II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
[     8.200] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.200] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
[     8.201] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.201] (II) NVIDIA(0): 
[     8.201] (II) NVIDIA(0):   Validating Mode "320x240":
[     8.201] (II) NVIDIA(0):     320 x 240 @ 75 Hz
[     8.201] (II) NVIDIA(0):     Mode Source: X Server
[     8.201] (II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
[     8.201] (II) NVIDIA(0):       HRes, HSyncStart :  320,  328
[     8.201] (II) NVIDIA(0):       HSyncEnd, HTotal :  360,  420
[     8.201] (II) NVIDIA(0):       VRes, VSyncStart :  240,  240
[     8.201] (II) NVIDIA(0):       VSyncEnd, VTotal :  242,  250
[     8.201] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.201] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.201] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
[     8.201] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.201] (II) NVIDIA(0): 
[     8.201] (II) NVIDIA(0):   Validating Mode "640x480":
[     8.201] (II) NVIDIA(0):     640 x 480 @ 85 Hz
[     8.201] (II) NVIDIA(0):     Mode Source: X Server
[     8.201] (II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
[     8.201] (II) NVIDIA(0):       HRes, HSyncStart :  640,  696
[     8.201] (II) NVIDIA(0):       HSyncEnd, HTotal :  752,  832
[     8.201] (II) NVIDIA(0):       VRes, VSyncStart :  480,  481
[     8.201] (II) NVIDIA(0):       VSyncEnd, VTotal :  484,  509
[     8.201] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.201] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
[     8.201] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.201] (II) NVIDIA(0): 
[     8.201] (II) NVIDIA(0):   Validating Mode "320x240":
[     8.201] (II) NVIDIA(0):     320 x 240 @ 85 Hz
[     8.201] (II) NVIDIA(0):     Mode Source: X Server
[     8.202] (II) NVIDIA(0):       Pixel Clock      : 18.00 MHz
[     8.202] (II) NVIDIA(0):       HRes, HSyncStart :  320,  348
[     8.202] (II) NVIDIA(0):       HSyncEnd, HTotal :  376,  416
[     8.202] (II) NVIDIA(0):       VRes, VSyncStart :  240,  240
[     8.202] (II) NVIDIA(0):       VSyncEnd, VTotal :  242,  254
[     8.202] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.202] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.202] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.2 Hz) out of range
[     8.202] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.202] (II) NVIDIA(0): 
[     8.202] (II) NVIDIA(0):   Validating Mode "800x600":
[     8.202] (II) NVIDIA(0):     800 x 600 @ 56 Hz
[     8.202] (II) NVIDIA(0):     Mode Source: X Server
[     8.202] (II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
[     8.202] (II) NVIDIA(0):       HRes, HSyncStart :  800,  824
[     8.202] (II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1024
[     8.202] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[     8.202] (II) NVIDIA(0):       VSyncEnd, VTotal :  603,  625
[     8.202] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.203] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[     8.203] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[     8.203] (II) NVIDIA(GPU-0):       Vertical Taps          0
[     8.203] (II) NVIDIA(GPU-0):       Base SuperSample       x4
[     8.203] (II) NVIDIA(GPU-0):       Base Depth             32
[     8.203] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[     8.203] (II) NVIDIA(GPU-0):       Overlay Depth          32
[     8.203] (II) NVIDIA(0):     Mode is valid.
[     8.203] (II) NVIDIA(0): 
[     8.203] (II) NVIDIA(0):   Validating Mode "400x300":
[     8.203] (II) NVIDIA(0):     400 x 300 @ 56 Hz
[     8.203] (II) NVIDIA(0):     Mode Source: X Server
[     8.203] (II) NVIDIA(0):       Pixel Clock      : 18.00 MHz
[     8.203] (II) NVIDIA(0):       HRes, HSyncStart :  400,  412
[     8.203] (II) NVIDIA(0):       HSyncEnd, HTotal :  448,  512
[     8.203] (II) NVIDIA(0):       VRes, VSyncStart :  300,  300
[     8.203] (II) NVIDIA(0):       VSyncEnd, VTotal :  301,  312
[     8.203] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.203] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.204] (WW) NVIDIA(GPU-0):     BestFit Centered ViewPort 400x600 exceeds hardware
[     8.204] (WW) NVIDIA(GPU-0):         capabilities.
[     8.204] (WW) NVIDIA(0):     Mode is rejected: Unable to construct hardware-specific
[     8.204] (WW) NVIDIA(0):     mode timings.
[     8.204] (II) NVIDIA(0): 
[     8.204] (II) NVIDIA(0):   Validating Mode "800x600":
[     8.204] (II) NVIDIA(0):     800 x 600 @ 60 Hz
[     8.204] (II) NVIDIA(0):     Mode Source: X Server
[     8.204] (II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
[     8.204] (II) NVIDIA(0):       HRes, HSyncStart :  800,  840
[     8.204] (II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
[     8.204] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[     8.204] (II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
[     8.204] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.205] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[     8.205] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[     8.205] (II) NVIDIA(GPU-0):       Vertical Taps          0
[     8.205] (II) NVIDIA(GPU-0):       Base SuperSample       x4
[     8.205] (II) NVIDIA(GPU-0):       Base Depth             32
[     8.205] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[     8.205] (II) NVIDIA(GPU-0):       Overlay Depth          32
[     8.205] (II) NVIDIA(0):     Mode is valid.
[     8.205] (II) NVIDIA(0): 
[     8.205] (II) NVIDIA(0):   Validating Mode "400x300":
[     8.205] (II) NVIDIA(0):     400 x 300 @ 60 Hz
[     8.205] (II) NVIDIA(0):     Mode Source: X Server
[     8.205] (II) NVIDIA(0):       Pixel Clock      : 20.00 MHz
[     8.205] (II) NVIDIA(0):       HRes, HSyncStart :  400,  420
[     8.205] (II) NVIDIA(0):       HSyncEnd, HTotal :  484,  528
[     8.205] (II) NVIDIA(0):       VRes, VSyncStart :  300,  300
[     8.205] (II) NVIDIA(0):       VSyncEnd, VTotal :  302,  314
[     8.205] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.205] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.206] (WW) NVIDIA(GPU-0):     BestFit Centered ViewPort 400x600 exceeds hardware
[     8.206] (WW) NVIDIA(GPU-0):         capabilities.
[     8.206] (WW) NVIDIA(0):     Mode is rejected: Unable to construct hardware-specific
[     8.206] (WW) NVIDIA(0):     mode timings.
[     8.206] (II) NVIDIA(0): 
[     8.206] (II) NVIDIA(0):   Validating Mode "800x600":
[     8.206] (II) NVIDIA(0):     800 x 600 @ 72 Hz
[     8.206] (II) NVIDIA(0):     Mode Source: X Server
[     8.206] (II) NVIDIA(0):       Pixel Clock      : 50.00 MHz
[     8.206] (II) NVIDIA(0):       HRes, HSyncStart :  800,  856
[     8.206] (II) NVIDIA(0):       HSyncEnd, HTotal :  976, 1040
[     8.206] (II) NVIDIA(0):       VRes, VSyncStart :  600,  637
[     8.206] (II) NVIDIA(0):       VSyncEnd, VTotal :  643,  666
[     8.206] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.207] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[     8.207] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[     8.207] (II) NVIDIA(GPU-0):       Vertical Taps          0
[     8.207] (II) NVIDIA(GPU-0):       Base SuperSample       x4
[     8.207] (II) NVIDIA(GPU-0):       Base Depth             32
[     8.207] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[     8.207] (II) NVIDIA(GPU-0):       Overlay Depth          32
[     8.207] (II) NVIDIA(0):     Mode is valid.
[     8.207] (II) NVIDIA(0): 
[     8.207] (II) NVIDIA(0):   Validating Mode "400x300":
[     8.207] (II) NVIDIA(0):     400 x 300 @ 72 Hz
[     8.207] (II) NVIDIA(0):     Mode Source: X Server
[     8.207] (II) NVIDIA(0):       Pixel Clock      : 25.00 MHz
[     8.207] (II) NVIDIA(0):       HRes, HSyncStart :  400,  428
[     8.207] (II) NVIDIA(0):       HSyncEnd, HTotal :  488,  520
[     8.207] (II) NVIDIA(0):       VRes, VSyncStart :  300,  318
[     8.207] (II) NVIDIA(0):       VSyncEnd, VTotal :  321,  333
[     8.208] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.208] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.208] (II) NVIDIA(GPU-0):     BestFit Centered         400x600
[     8.208] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[     8.208] (II) NVIDIA(GPU-0):       Vertical Taps          1
[     8.208] (II) NVIDIA(GPU-0):       Base SuperSample       x4
[     8.208] (II) NVIDIA(GPU-0):       Base Depth             32
[     8.208] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[     8.208] (II) NVIDIA(GPU-0):       Overlay Depth          32
[     8.208] (II) NVIDIA(0):     Mode is valid.
[     8.208] (II) NVIDIA(0): 
[     8.208] (II) NVIDIA(0):   Validating Mode "800x600":
[     8.208] (II) NVIDIA(0):     800 x 600 @ 75 Hz
[     8.208] (II) NVIDIA(0):     Mode Source: X Server
[     8.209] (II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
[     8.209] (II) NVIDIA(0):       HRes, HSyncStart :  800,  816
[     8.209] (II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
[     8.209] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[     8.209] (II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
[     8.209] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.209] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
[     8.209] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.209] (II) NVIDIA(0): 
[     8.209] (II) NVIDIA(0):   Validating Mode "400x300":
[     8.209] (II) NVIDIA(0):     400 x 300 @ 75 Hz
[     8.209] (II) NVIDIA(0):     Mode Source: X Server
[     8.209] (II) NVIDIA(0):       Pixel Clock      : 24.75 MHz
[     8.209] (II) NVIDIA(0):       HRes, HSyncStart :  400,  408
[     8.209] (II) NVIDIA(0):       HSyncEnd, HTotal :  448,  528
[     8.209] (II) NVIDIA(0):       VRes, VSyncStart :  300,  300
[     8.209] (II) NVIDIA(0):       VSyncEnd, VTotal :  302,  312
[     8.209] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.209] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.209] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.1 Hz) out of range
[     8.209] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.209] (II) NVIDIA(0): 
[     8.209] (II) NVIDIA(0):   Validating Mode "800x600":
[     8.209] (II) NVIDIA(0):     800 x 600 @ 85 Hz
[     8.209] (II) NVIDIA(0):     Mode Source: X Server
[     8.209] (II) NVIDIA(0):       Pixel Clock      : 56.30 MHz
[     8.209] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[     8.209] (II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1048
[     8.209] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[     8.209] (II) NVIDIA(0):       VSyncEnd, VTotal :  604,  631
[     8.210] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.210] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
[     8.210] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.210] (II) NVIDIA(0): 
[     8.210] (II) NVIDIA(0):   Validating Mode "400x300":
[     8.210] (II) NVIDIA(0):     400 x 300 @ 85 Hz
[     8.210] (II) NVIDIA(0):     Mode Source: X Server
[     8.210] (II) NVIDIA(0):       Pixel Clock      : 28.15 MHz
[     8.210] (II) NVIDIA(0):       HRes, HSyncStart :  400,  416
[     8.210] (II) NVIDIA(0):       HSyncEnd, HTotal :  448,  524
[     8.210] (II) NVIDIA(0):       VRes, VSyncStart :  300,  300
[     8.210] (II) NVIDIA(0):       VSyncEnd, VTotal :  302,  315
[     8.210] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.210] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.210] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
[     8.210] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.210] (II) NVIDIA(0): 
[     8.210] (II) NVIDIA(0):   Validating Mode "1024x768i":
[     8.210] (II) NVIDIA(0):     1024 x 768 @ 87 Hz
[     8.210] (II) NVIDIA(0):     Mode Source: X Server
[     8.210] (II) NVIDIA(0):       Pixel Clock      : 44.90 MHz
[     8.210] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1032
[     8.210] (II) NVIDIA(0):       HSyncEnd, HTotal : 1208, 1264
[     8.210] (II) NVIDIA(0):       VRes, VSyncStart :  768,  768
[     8.210] (II) NVIDIA(0):       VSyncEnd, VTotal :  776,  817
[     8.210] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.210] (II) NVIDIA(0):       Extra            : Interlace
[     8.210] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.0 Hz) out of range
[     8.210] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.211] (II) NVIDIA(0): 
[     8.211] (II) NVIDIA(0):   Validating Mode "512x384i":
[     8.211] (II) NVIDIA(0):     512 x 384 @ 87 Hz
[     8.211] (II) NVIDIA(0):     Mode Source: X Server
[     8.211] (II) NVIDIA(0):       Pixel Clock      : 22.45 MHz
[     8.211] (II) NVIDIA(0):       HRes, HSyncStart :  512,  516
[     8.211] (II) NVIDIA(0):       HSyncEnd, HTotal :  604,  632
[     8.211] (II) NVIDIA(0):       VRes, VSyncStart :  384,  384
[     8.211] (II) NVIDIA(0):       VSyncEnd, VTotal :  388,  408
[     8.211] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.211] (II) NVIDIA(0):       Extra            : Interlace DoubleScan
[     8.211] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.1 Hz) out of range
[     8.211] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.211] (II) NVIDIA(0): 
[     8.211] (II) NVIDIA(0):   Validating Mode "1024x768":
[     8.211] (II) NVIDIA(0):     1024 x 768 @ 60 Hz
[     8.211] (II) NVIDIA(0):     Mode Source: X Server
[     8.211] (II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
[     8.211] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
[     8.211] (II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
[     8.211] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[     8.211] (II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
[     8.211] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.212] (II) NVIDIA(GPU-0):     BestFit Centered         1024x768
[     8.212] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[     8.212] (II) NVIDIA(GPU-0):       Vertical Taps          0
[     8.212] (II) NVIDIA(GPU-0):       Base SuperSample       x4
[     8.212] (II) NVIDIA(GPU-0):       Base Depth             32
[     8.212] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[     8.212] (II) NVIDIA(GPU-0):       Overlay Depth          32
[     8.212] (II) NVIDIA(0):     Mode is valid.
[     8.212] (II) NVIDIA(0): 
[     8.212] (II) NVIDIA(0):   Validating Mode "512x384":
[     8.212] (II) NVIDIA(0):     512 x 384 @ 60 Hz
[     8.212] (II) NVIDIA(0):     Mode Source: X Server
[     8.212] (II) NVIDIA(0):       Pixel Clock      : 32.50 MHz
[     8.212] (II) NVIDIA(0):       HRes, HSyncStart :  512,  524
[     8.212] (II) NVIDIA(0):       HSyncEnd, HTotal :  592,  672
[     8.212] (II) NVIDIA(0):       VRes, VSyncStart :  384,  385
[     8.212] (II) NVIDIA(0):       VSyncEnd, VTotal :  388,  403
[     8.212] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.212] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.213] (II) NVIDIA(GPU-0):     BestFit Centered         512x768
[     8.213] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[     8.213] (II) NVIDIA(GPU-0):       Vertical Taps          1
[     8.213] (II) NVIDIA(GPU-0):       Base SuperSample       x4
[     8.213] (II) NVIDIA(GPU-0):       Base Depth             32
[     8.213] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[     8.213] (II) NVIDIA(GPU-0):       Overlay Depth          32
[     8.213] (II) NVIDIA(0):     Mode is valid.
[     8.213] (II) NVIDIA(0): 
[     8.213] (II) NVIDIA(0):   Validating Mode "1024x768":
[     8.213] (II) NVIDIA(0):     1024 x 768 @ 70 Hz
[     8.213] (II) NVIDIA(0):     Mode Source: X Server
[     8.213] (II) NVIDIA(0):       Pixel Clock      : 75.00 MHz
[     8.213] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
[     8.213] (II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1328
[     8.213] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[     8.214] (II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
[     8.214] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.214] (WW) NVIDIA(0):     Mode is rejected: HorizSync (56.5 kHz) out of range
[     8.214] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.214] (II) NVIDIA(0): 
[     8.214] (II) NVIDIA(0):   Validating Mode "512x384":
[     8.214] (II) NVIDIA(0):     512 x 384 @ 70 Hz
[     8.214] (II) NVIDIA(0):     Mode Source: X Server
[     8.214] (II) NVIDIA(0):       Pixel Clock      : 37.50 MHz
[     8.214] (II) NVIDIA(0):       HRes, HSyncStart :  512,  524
[     8.214] (II) NVIDIA(0):       HSyncEnd, HTotal :  592,  664
[     8.214] (II) NVIDIA(0):       VRes, VSyncStart :  384,  385
[     8.214] (II) NVIDIA(0):       VSyncEnd, VTotal :  388,  403
[     8.214] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.214] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.214] (WW) NVIDIA(0):     Mode is rejected: HorizSync (56.5 kHz) out of range
[     8.214] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.214] (II) NVIDIA(0): 
[     8.214] (II) NVIDIA(0):   Validating Mode "1024x768":
[     8.214] (II) NVIDIA(0):     1024 x 768 @ 75 Hz
[     8.214] (II) NVIDIA(0):     Mode Source: X Server
[     8.214] (II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
[     8.214] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
[     8.214] (II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
[     8.214] (II) NVIDIA(0):       VRes, VSyncStart :  768,  769
[     8.214] (II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
[     8.214] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.214] (WW) NVIDIA(0):     Mode is rejected: HorizSync (60.0 kHz) out of range
[     8.214] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.215] (II) NVIDIA(0): 
[     8.215] (II) NVIDIA(0):   Validating Mode "512x384":
[     8.215] (II) NVIDIA(0):     512 x 384 @ 75 Hz
[     8.215] (II) NVIDIA(0):     Mode Source: X Server
[     8.215] (II) NVIDIA(0):       Pixel Clock      : 39.38 MHz
[     8.215] (II) NVIDIA(0):       HRes, HSyncStart :  512,  520
[     8.215] (II) NVIDIA(0):       HSyncEnd, HTotal :  568,  656
[     8.215] (II) NVIDIA(0):       VRes, VSyncStart :  384,  384
[     8.215] (II) NVIDIA(0):       VSyncEnd, VTotal :  386,  400
[     8.215] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.215] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.215] (WW) NVIDIA(0):     Mode is rejected: HorizSync (60.0 kHz) out of range
[     8.215] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.215] (II) NVIDIA(0): 
[     8.215] (II) NVIDIA(0):   Validating Mode "1024x768":
[     8.215] (II) NVIDIA(0):     1024 x 768 @ 85 Hz
[     8.215] (II) NVIDIA(0):     Mode Source: X Server
[     8.215] (II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
[     8.215] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1072
[     8.215] (II) NVIDIA(0):       HSyncEnd, HTotal : 1168, 1376
[     8.215] (II) NVIDIA(0):       VRes, VSyncStart :  768,  769
[     8.215] (II) NVIDIA(0):       VSyncEnd, VTotal :  772,  808
[     8.215] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.215] (WW) NVIDIA(0):     Mode is rejected: HorizSync (68.7 kHz) out of range
[     8.215] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.215] (II) NVIDIA(0): 
[     8.215] (II) NVIDIA(0):   Validating Mode "512x384":
[     8.215] (II) NVIDIA(0):     512 x 384 @ 85 Hz
[     8.215] (II) NVIDIA(0):     Mode Source: X Server
[     8.215] (II) NVIDIA(0):       Pixel Clock      : 47.25 MHz
[     8.216] (II) NVIDIA(0):       HRes, HSyncStart :  512,  536
[     8.216] (II) NVIDIA(0):       HSyncEnd, HTotal :  584,  688
[     8.216] (II) NVIDIA(0):       VRes, VSyncStart :  384,  384
[     8.216] (II) NVIDIA(0):       VSyncEnd, VTotal :  386,  404
[     8.216] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.216] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.216] (WW) NVIDIA(0):     Mode is rejected: HorizSync (68.7 kHz) out of range
[     8.216] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.216] (II) NVIDIA(0): 
[     8.216] (II) NVIDIA(0):   Validating Mode "1152x864":
[     8.216] (II) NVIDIA(0):     1152 x 864 @ 75 Hz
[     8.216] (II) NVIDIA(0):     Mode Source: X Server
[     8.216] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[     8.216] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
[     8.216] (II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
[     8.216] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[     8.216] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
[     8.216] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.216] (WW) NVIDIA(0):     Mode is rejected: HorizSync (67.5 kHz) out of range
[     8.216] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.216] (II) NVIDIA(0): 
[     8.216] (II) NVIDIA(0):   Validating Mode "576x432":
[     8.216] (II) NVIDIA(0):     576 x 432 @ 75 Hz
[     8.216] (II) NVIDIA(0):     Mode Source: X Server
[     8.216] (II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
[     8.216] (II) NVIDIA(0):       HRes, HSyncStart :  576,  608
[     8.216] (II) NVIDIA(0):       HSyncEnd, HTotal :  672,  800
[     8.216] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[     8.217] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  450
[     8.217] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.217] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.217] (WW) NVIDIA(0):     Mode is rejected: HorizSync (67.5 kHz) out of range
[     8.217] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.217] (II) NVIDIA(0): 
[     8.217] (II) NVIDIA(0):   Validating Mode "1280x960":
[     8.217] (II) NVIDIA(0):     1280 x 960 @ 60 Hz
[     8.217] (II) NVIDIA(0):     Mode Source: X Server
[     8.217] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[     8.217] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1376
[     8.217] (II) NVIDIA(0):       HSyncEnd, HTotal : 1488, 1800
[     8.217] (II) NVIDIA(0):       VRes, VSyncStart :  960,  961
[     8.217] (II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1000
[     8.217] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.217] (WW) NVIDIA(0):     Mode is rejected: HorizSync (60.0 kHz) out of range
[     8.217] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.217] (II) NVIDIA(0): 
[     8.217] (II) NVIDIA(0):   Validating Mode "640x480":
[     8.217] (II) NVIDIA(0):     640 x 480 @ 60 Hz
[     8.217] (II) NVIDIA(0):     Mode Source: X Server
[     8.217] (II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
[     8.217] (II) NVIDIA(0):       HRes, HSyncStart :  640,  688
[     8.217] (II) NVIDIA(0):       HSyncEnd, HTotal :  744,  900
[     8.217] (II) NVIDIA(0):       VRes, VSyncStart :  480,  480
[     8.217] (II) NVIDIA(0):       VSyncEnd, VTotal :  482,  500
[     8.217] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.217] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.217] (WW) NVIDIA(0):     Mode is rejected: HorizSync (60.0 kHz) out of range
[     8.217] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.218] (II) NVIDIA(0): 
[     8.218] (II) NVIDIA(0):   Validating Mode "1280x960":
[     8.218] (II) NVIDIA(0):     1280 x 960 @ 85 Hz
[     8.218] (II) NVIDIA(0):     Mode Source: X Server
[     8.218] (II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
[     8.218] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
[     8.218] (II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
[     8.218] (II) NVIDIA(0):       VRes, VSyncStart :  960,  961
[     8.218] (II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1011
[     8.218] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.218] (WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
[     8.218] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.218] (II) NVIDIA(0): 
[     8.218] (II) NVIDIA(0):   Validating Mode "640x480":
[     8.218] (II) NVIDIA(0):     640 x 480 @ 85 Hz
[     8.218] (II) NVIDIA(0):     Mode Source: X Server
[     8.218] (II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
[     8.218] (II) NVIDIA(0):       HRes, HSyncStart :  640,  672
[     8.218] (II) NVIDIA(0):       HSyncEnd, HTotal :  752,  864
[     8.218] (II) NVIDIA(0):       VRes, VSyncStart :  480,  480
[     8.218] (II) NVIDIA(0):       VSyncEnd, VTotal :  482,  505
[     8.218] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.218] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.218] (WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
[     8.218] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.218] (II) NVIDIA(0): 
[     8.218] (II) NVIDIA(0):   Validating Mode "1280x1024":
[     8.218] (II) NVIDIA(0):     1280 x 1024 @ 60 Hz
[     8.218] (II) NVIDIA(0):     Mode Source: X Server
[     8.219] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[     8.219] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
[     8.219] (II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
[     8.219] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[     8.219] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
[     8.219] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.219] (WW) NVIDIA(0):     Mode is rejected: HorizSync (64.0 kHz) out of range
[     8.219] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.219] (II) NVIDIA(0): 
[     8.219] (II) NVIDIA(0):   Validating Mode "640x512":
[     8.219] (II) NVIDIA(0):     640 x 512 @ 60 Hz
[     8.219] (II) NVIDIA(0):     Mode Source: X Server
[     8.219] (II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
[     8.219] (II) NVIDIA(0):       HRes, HSyncStart :  640,  664
[     8.219] (II) NVIDIA(0):       HSyncEnd, HTotal :  720,  844
[     8.219] (II) NVIDIA(0):       VRes, VSyncStart :  512,  512
[     8.219] (II) NVIDIA(0):       VSyncEnd, VTotal :  514,  533
[     8.219] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.219] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.219] (WW) NVIDIA(0):     Mode is rejected: HorizSync (64.0 kHz) out of range
[     8.219] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.219] (II) NVIDIA(0): 
[     8.219] (II) NVIDIA(0):   Validating Mode "1280x1024":
[     8.219] (II) NVIDIA(0):     1280 x 1024 @ 75 Hz
[     8.219] (II) NVIDIA(0):     Mode Source: X Server
[     8.219] (II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
[     8.219] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
[     8.219] (II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
[     8.219] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[     8.219] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
[     8.220] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.220] (WW) NVIDIA(0):     Mode is rejected: HorizSync (80.0 kHz) out of range
[     8.220] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.220] (II) NVIDIA(0): 
[     8.220] (II) NVIDIA(0):   Validating Mode "640x512":
[     8.220] (II) NVIDIA(0):     640 x 512 @ 75 Hz
[     8.220] (II) NVIDIA(0):     Mode Source: X Server
[     8.220] (II) NVIDIA(0):       Pixel Clock      : 67.50 MHz
[     8.220] (II) NVIDIA(0):       HRes, HSyncStart :  640,  648
[     8.220] (II) NVIDIA(0):       HSyncEnd, HTotal :  720,  844
[     8.220] (II) NVIDIA(0):       VRes, VSyncStart :  512,  512
[     8.220] (II) NVIDIA(0):       VSyncEnd, VTotal :  514,  533
[     8.220] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.220] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.220] (WW) NVIDIA(0):     Mode is rejected: HorizSync (80.0 kHz) out of range
[     8.220] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.220] (II) NVIDIA(0): 
[     8.220] (II) NVIDIA(0):   Validating Mode "1280x1024":
[     8.220] (II) NVIDIA(0):     1280 x 1024 @ 85 Hz
[     8.220] (II) NVIDIA(0):     Mode Source: X Server
[     8.220] (II) NVIDIA(0):       Pixel Clock      : 157.50 MHz
[     8.220] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
[     8.220] (II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
[     8.220] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[     8.220] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1072
[     8.220] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.220] (WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
[     8.220] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.221] (II) NVIDIA(0): 
[     8.221] (II) NVIDIA(0):   Validating Mode "640x512":
[     8.221] (II) NVIDIA(0):     640 x 512 @ 85 Hz
[     8.221] (II) NVIDIA(0):     Mode Source: X Server
[     8.221] (II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
[     8.221] (II) NVIDIA(0):       HRes, HSyncStart :  640,  672
[     8.221] (II) NVIDIA(0):       HSyncEnd, HTotal :  752,  864
[     8.221] (II) NVIDIA(0):       VRes, VSyncStart :  512,  512
[     8.221] (II) NVIDIA(0):       VSyncEnd, VTotal :  514,  536
[     8.221] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.221] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.221] (WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
[     8.221] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.221] (II) NVIDIA(0): 
[     8.221] (II) NVIDIA(0):   Validating Mode "1600x1200":
[     8.221] (II) NVIDIA(0):     1600 x 1200 @ 60 Hz
[     8.221] (II) NVIDIA(0):     Mode Source: X Server
[     8.221] (II) NVIDIA(0):       Pixel Clock      : 162.00 MHz
[     8.221] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[     8.221] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[     8.221] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[     8.221] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[     8.221] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.221] (WW) NVIDIA(0):     Mode is rejected: HorizSync (75.0 kHz) out of range
[     8.221] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.221] (II) NVIDIA(0): 
[     8.221] (II) NVIDIA(0):   Validating Mode "800x600":
[     8.221] (II) NVIDIA(0):     800 x 600 @ 60 Hz
[     8.221] (II) NVIDIA(0):     Mode Source: X Server
[     8.221] (II) NVIDIA(0):       Pixel Clock      : 81.00 MHz
[     8.222] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[     8.222] (II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
[     8.222] (II) NVIDIA(0):       VRes, VSyncStart :  600,  600
[     8.222] (II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
[     8.222] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.222] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.222] (WW) NVIDIA(0):     Mode is rejected: HorizSync (75.0 kHz) out of range
[     8.222] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.222] (II) NVIDIA(0): 
[     8.222] (II) NVIDIA(0):   Validating Mode "1600x1200":
[     8.222] (II) NVIDIA(0):     1600 x 1200 @ 65 Hz
[     8.222] (II) NVIDIA(0):     Mode Source: X Server
[     8.222] (II) NVIDIA(0):       Pixel Clock      : 175.50 MHz
[     8.222] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[     8.222] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[     8.222] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[     8.222] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[     8.222] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.222] (WW) NVIDIA(0):     Mode is rejected: HorizSync (81.2 kHz) out of range
[     8.222] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.222] (II) NVIDIA(0): 
[     8.222] (II) NVIDIA(0):   Validating Mode "800x600":
[     8.222] (II) NVIDIA(0):     800 x 600 @ 65 Hz
[     8.222] (II) NVIDIA(0):     Mode Source: X Server
[     8.222] (II) NVIDIA(0):       Pixel Clock      : 87.75 MHz
[     8.222] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[     8.222] (II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
[     8.222] (II) NVIDIA(0):       VRes, VSyncStart :  600,  600
[     8.222] (II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
[     8.222] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.223] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.223] (WW) NVIDIA(0):     Mode is rejected: HorizSync (81.2 kHz) out of range
[     8.223] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.223] (II) NVIDIA(0): 
[     8.223] (II) NVIDIA(0):   Validating Mode "1600x1200":
[     8.223] (II) NVIDIA(0):     1600 x 1200 @ 70 Hz
[     8.223] (II) NVIDIA(0):     Mode Source: X Server
[     8.223] (II) NVIDIA(0):       Pixel Clock      : 189.00 MHz
[     8.223] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[     8.223] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[     8.223] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[     8.223] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[     8.223] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.223] (WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
[     8.223] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.223] (II) NVIDIA(0): 
[     8.223] (II) NVIDIA(0):   Validating Mode "800x600":
[     8.223] (II) NVIDIA(0):     800 x 600 @ 70 Hz
[     8.223] (II) NVIDIA(0):     Mode Source: X Server
[     8.223] (II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
[     8.223] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[     8.223] (II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
[     8.223] (II) NVIDIA(0):       VRes, VSyncStart :  600,  600
[     8.223] (II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
[     8.223] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.223] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.223] (WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
[     8.223] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.223] (II) NVIDIA(0): 
[     8.224] (II) NVIDIA(0):   Validating Mode "1600x1200":
[     8.224] (II) NVIDIA(0):     1600 x 1200 @ 75 Hz
[     8.224] (II) NVIDIA(0):     Mode Source: X Server
[     8.224] (II) NVIDIA(0):       Pixel Clock      : 202.50 MHz
[     8.224] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[     8.224] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[     8.224] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[     8.224] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[     8.224] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.224] (WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
[     8.224] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.224] (II) NVIDIA(0): 
[     8.224] (II) NVIDIA(0):   Validating Mode "800x600":
[     8.224] (II) NVIDIA(0):     800 x 600 @ 75 Hz
[     8.224] (II) NVIDIA(0):     Mode Source: X Server
[     8.224] (II) NVIDIA(0):       Pixel Clock      : 101.25 MHz
[     8.224] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[     8.224] (II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
[     8.224] (II) NVIDIA(0):       VRes, VSyncStart :  600,  600
[     8.224] (II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
[     8.224] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.224] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.224] (WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
[     8.224] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.224] (II) NVIDIA(0): 
[     8.224] (II) NVIDIA(0):   Validating Mode "1600x1200":
[     8.224] (II) NVIDIA(0):     1600 x 1200 @ 85 Hz
[     8.224] (II) NVIDIA(0):     Mode Source: X Server
[     8.224] (II) NVIDIA(0):       Pixel Clock      : 229.50 MHz
[     8.225] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[     8.225] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[     8.225] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[     8.225] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[     8.225] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.225] (WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
[     8.225] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.225] (II) NVIDIA(0): 
[     8.225] (II) NVIDIA(0):   Validating Mode "800x600":
[     8.225] (II) NVIDIA(0):     800 x 600 @ 85 Hz
[     8.225] (II) NVIDIA(0):     Mode Source: X Server
[     8.225] (II) NVIDIA(0):       Pixel Clock      : 114.75 MHz
[     8.225] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[     8.225] (II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
[     8.225] (II) NVIDIA(0):       VRes, VSyncStart :  600,  600
[     8.225] (II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
[     8.225] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.225] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.225] (WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
[     8.225] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.225] (II) NVIDIA(0): 
[     8.225] (II) NVIDIA(0):   Validating Mode "1792x1344":
[     8.225] (II) NVIDIA(0):     1792 x 1344 @ 60 Hz
[     8.225] (II) NVIDIA(0):     Mode Source: X Server
[     8.225] (II) NVIDIA(0):       Pixel Clock      : 204.80 MHz
[     8.225] (II) NVIDIA(0):       HRes, HSyncStart : 1792, 1920
[     8.225] (II) NVIDIA(0):       HSyncEnd, HTotal : 2120, 2448
[     8.225] (II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
[     8.225] (II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1394
[     8.226] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.226] (WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
[     8.226] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.226] (II) NVIDIA(0): 
[     8.226] (II) NVIDIA(0):   Validating Mode "896x672":
[     8.226] (II) NVIDIA(0):     896 x 672 @ 60 Hz
[     8.226] (II) NVIDIA(0):     Mode Source: X Server
[     8.226] (II) NVIDIA(0):       Pixel Clock      : 102.40 MHz
[     8.226] (II) NVIDIA(0):       HRes, HSyncStart :  896,  960
[     8.226] (II) NVIDIA(0):       HSyncEnd, HTotal : 1060, 1224
[     8.226] (II) NVIDIA(0):       VRes, VSyncStart :  672,  672
[     8.226] (II) NVIDIA(0):       VSyncEnd, VTotal :  674,  697
[     8.226] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.226] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.226] (WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
[     8.226] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.226] (II) NVIDIA(0): 
[     8.226] (II) NVIDIA(0):   Validating Mode "1792x1344":
[     8.226] (II) NVIDIA(0):     1792 x 1344 @ 75 Hz
[     8.226] (II) NVIDIA(0):     Mode Source: X Server
[     8.226] (II) NVIDIA(0):       Pixel Clock      : 261.00 MHz
[     8.226] (II) NVIDIA(0):       HRes, HSyncStart : 1792, 1888
[     8.226] (II) NVIDIA(0):       HSyncEnd, HTotal : 2104, 2456
[     8.226] (II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
[     8.226] (II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1417
[     8.226] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.226] (WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
[     8.226] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.226] (II) NVIDIA(0): 
[     8.226] (II) NVIDIA(0):   Validating Mode "896x672":
[     8.227] (II) NVIDIA(0):     896 x 672 @ 75 Hz
[     8.227] (II) NVIDIA(0):     Mode Source: X Server
[     8.227] (II) NVIDIA(0):       Pixel Clock      : 130.50 MHz
[     8.227] (II) NVIDIA(0):       HRes, HSyncStart :  896,  944
[     8.227] (II) NVIDIA(0):       HSyncEnd, HTotal : 1052, 1228
[     8.227] (II) NVIDIA(0):       VRes, VSyncStart :  672,  672
[     8.227] (II) NVIDIA(0):       VSyncEnd, VTotal :  674,  708
[     8.227] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.227] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.227] (WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
[     8.227] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.227] (II) NVIDIA(0): 
[     8.227] (II) NVIDIA(0):   Validating Mode "1856x1392":
[     8.227] (II) NVIDIA(0):     1856 x 1392 @ 60 Hz
[     8.227] (II) NVIDIA(0):     Mode Source: X Server
[     8.227] (II) NVIDIA(0):       Pixel Clock      : 218.30 MHz
[     8.227] (II) NVIDIA(0):       HRes, HSyncStart : 1856, 1952
[     8.227] (II) NVIDIA(0):       HSyncEnd, HTotal : 2176, 2528
[     8.227] (II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
[     8.227] (II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1439
[     8.227] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.227] (WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
[     8.227] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.227] (II) NVIDIA(0): 
[     8.227] (II) NVIDIA(0):   Validating Mode "928x696":
[     8.227] (II) NVIDIA(0):     928 x 696 @ 60 Hz
[     8.227] (II) NVIDIA(0):     Mode Source: X Server
[     8.227] (II) NVIDIA(0):       Pixel Clock      : 109.15 MHz
[     8.227] (II) NVIDIA(0):       HRes, HSyncStart :  928,  976
[     8.228] (II) NVIDIA(0):       HSyncEnd, HTotal : 1088, 1264
[     8.228] (II) NVIDIA(0):       VRes, VSyncStart :  696,  696
[     8.228] (II) NVIDIA(0):       VSyncEnd, VTotal :  698,  719
[     8.228] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.228] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.228] (WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
[     8.228] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.228] (II) NVIDIA(0): 
[     8.228] (II) NVIDIA(0):   Validating Mode "1856x1392":
[     8.228] (II) NVIDIA(0):     1856 x 1392 @ 75 Hz
[     8.228] (II) NVIDIA(0):     Mode Source: X Server
[     8.228] (II) NVIDIA(0):       Pixel Clock      : 288.00 MHz
[     8.228] (II) NVIDIA(0):       HRes, HSyncStart : 1856, 1984
[     8.228] (II) NVIDIA(0):       HSyncEnd, HTotal : 2208, 2560
[     8.228] (II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
[     8.228] (II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1500
[     8.228] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.228] (WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
[     8.228] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.228] (II) NVIDIA(0): 
[     8.228] (II) NVIDIA(0):   Validating Mode "928x696":
[     8.228] (II) NVIDIA(0):     928 x 696 @ 75 Hz
[     8.228] (II) NVIDIA(0):     Mode Source: X Server
[     8.228] (II) NVIDIA(0):       Pixel Clock      : 144.00 MHz
[     8.228] (II) NVIDIA(0):       HRes, HSyncStart :  928,  992
[     8.228] (II) NVIDIA(0):       HSyncEnd, HTotal : 1104, 1280
[     8.228] (II) NVIDIA(0):       VRes, VSyncStart :  696,  696
[     8.228] (II) NVIDIA(0):       VSyncEnd, VTotal :  698,  750
[     8.228] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.229] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.229] (WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
[     8.229] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.229] (II) NVIDIA(0): 
[     8.229] (II) NVIDIA(0):   Validating Mode "1920x1440":
[     8.229] (II) NVIDIA(0):     1920 x 1440 @ 60 Hz
[     8.229] (II) NVIDIA(0):     Mode Source: X Server
[     8.229] (II) NVIDIA(0):       Pixel Clock      : 234.00 MHz
[     8.229] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2048
[     8.229] (II) NVIDIA(0):       HSyncEnd, HTotal : 2256, 2600
[     8.229] (II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
[     8.229] (II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
[     8.229] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.229] (WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
[     8.229] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.229] (II) NVIDIA(0): 
[     8.229] (II) NVIDIA(0):   Validating Mode "960x720":
[     8.229] (II) NVIDIA(0):     960 x 720 @ 60 Hz
[     8.229] (II) NVIDIA(0):     Mode Source: X Server
[     8.229] (II) NVIDIA(0):       Pixel Clock      : 117.00 MHz
[     8.229] (II) NVIDIA(0):       HRes, HSyncStart :  960, 1024
[     8.229] (II) NVIDIA(0):       HSyncEnd, HTotal : 1128, 1300
[     8.229] (II) NVIDIA(0):       VRes, VSyncStart :  720,  720
[     8.229] (II) NVIDIA(0):       VSyncEnd, VTotal :  722,  750
[     8.229] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.229] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.229] (WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
[     8.229] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.229] (II) NVIDIA(0): 
[     8.230] (II) NVIDIA(0):   Validating Mode "1920x1440":
[     8.230] (II) NVIDIA(0):     1920 x 1440 @ 75 Hz
[     8.230] (II) NVIDIA(0):     Mode Source: X Server
[     8.230] (II) NVIDIA(0):       Pixel Clock      : 297.00 MHz
[     8.230] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2064
[     8.230] (II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2640
[     8.230] (II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
[     8.230] (II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
[     8.230] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.230] (WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
[     8.230] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.230] (II) NVIDIA(0): 
[     8.230] (II) NVIDIA(0):   Validating Mode "960x720":
[     8.230] (II) NVIDIA(0):     960 x 720 @ 75 Hz
[     8.230] (II) NVIDIA(0):     Mode Source: X Server
[     8.230] (II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
[     8.230] (II) NVIDIA(0):       HRes, HSyncStart :  960, 1032
[     8.230] (II) NVIDIA(0):       HSyncEnd, HTotal : 1144, 1320
[     8.230] (II) NVIDIA(0):       VRes, VSyncStart :  720,  720
[     8.230] (II) NVIDIA(0):       VSyncEnd, VTotal :  722,  750
[     8.230] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.230] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.230] (WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
[     8.230] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.230] (II) NVIDIA(0): 
[     8.230] (II) NVIDIA(0):   Validating Mode "832x624":
[     8.230] (II) NVIDIA(0):     832 x 624 @ 75 Hz
[     8.230] (II) NVIDIA(0):     Mode Source: X Server
[     8.230] (II) NVIDIA(0):       Pixel Clock      : 57.28 MHz
[     8.231] (II) NVIDIA(0):       HRes, HSyncStart :  832,  864
[     8.231] (II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1152
[     8.231] (II) NVIDIA(0):       VRes, VSyncStart :  624,  625
[     8.231] (II) NVIDIA(0):       VSyncEnd, VTotal :  628,  667
[     8.231] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.231] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (74.6 Hz) out of range
[     8.231] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.231] (II) NVIDIA(0): 
[     8.231] (II) NVIDIA(0):   Validating Mode "416x312":
[     8.231] (II) NVIDIA(0):     416 x 312 @ 75 Hz
[     8.231] (II) NVIDIA(0):     Mode Source: X Server
[     8.231] (II) NVIDIA(0):       Pixel Clock      : 28.64 MHz
[     8.231] (II) NVIDIA(0):       HRes, HSyncStart :  416,  432
[     8.231] (II) NVIDIA(0):       HSyncEnd, HTotal :  464,  576
[     8.231] (II) NVIDIA(0):       VRes, VSyncStart :  312,  312
[     8.231] (II) NVIDIA(0):       VSyncEnd, VTotal :  314,  333
[     8.231] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.231] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.231] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (74.7 Hz) out of range
[     8.231] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.231] (II) NVIDIA(0): 
[     8.231] (II) NVIDIA(0):   Validating Mode "1152x864":
[     8.231] (II) NVIDIA(0):     1152 x 864 @ 60 Hz
[     8.231] (II) NVIDIA(0):     Mode Source: X Server
[     8.231] (II) NVIDIA(0):       Pixel Clock      : 81.62 MHz
[     8.231] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
[     8.231] (II) NVIDIA(0):       HSyncEnd, HTotal : 1336, 1520
[     8.231] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[     8.231] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  895
[     8.231] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.232] (II) NVIDIA(GPU-0):     BestFit Centered         1152x864
[     8.232] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[     8.232] (II) NVIDIA(GPU-0):       Vertical Taps          0
[     8.232] (II) NVIDIA(GPU-0):       Base SuperSample       x4
[     8.232] (II) NVIDIA(GPU-0):       Base Depth             32
[     8.232] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[     8.232] (II) NVIDIA(GPU-0):       Overlay Depth          32
[     8.232] (II) NVIDIA(0):     Mode is valid.
[     8.232] (II) NVIDIA(0): 
[     8.232] (II) NVIDIA(0):   Validating Mode "576x432":
[     8.232] (II) NVIDIA(0):     576 x 432 @ 60 Hz
[     8.232] (II) NVIDIA(0):     Mode Source: X Server
[     8.232] (II) NVIDIA(0):       Pixel Clock      : 40.81 MHz
[     8.233] (II) NVIDIA(0):       HRes, HSyncStart :  576,  608
[     8.233] (II) NVIDIA(0):       HSyncEnd, HTotal :  668,  760
[     8.233] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[     8.233] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  447
[     8.233] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.233] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.233] (WW) NVIDIA(GPU-0):     BestFit Centered ViewPort 576x864 exceeds hardware
[     8.233] (WW) NVIDIA(GPU-0):         capabilities.
[     8.233] (WW) NVIDIA(0):     Mode is rejected: Unable to construct hardware-specific
[     8.233] (WW) NVIDIA(0):     mode timings.
[     8.233] (II) NVIDIA(0): 
[     8.233] (II) NVIDIA(0):   Validating Mode "1152x864":
[     8.233] (II) NVIDIA(0):     1152 x 864 @ 70 Hz
[     8.233] (II) NVIDIA(0):     Mode Source: X Server
[     8.233] (II) NVIDIA(0):       Pixel Clock      : 96.77 MHz
[     8.234] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
[     8.234] (II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1536
[     8.234] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[     8.234] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
[     8.234] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.234] (WW) NVIDIA(0):     Mode is rejected: HorizSync (63.0 kHz) out of range
[     8.234] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.234] (II) NVIDIA(0): 
[     8.234] (II) NVIDIA(0):   Validating Mode "576x432":
[     8.234] (II) NVIDIA(0):     576 x 432 @ 70 Hz
[     8.234] (II) NVIDIA(0):     Mode Source: X Server
[     8.234] (II) NVIDIA(0):       Pixel Clock      : 48.38 MHz
[     8.234] (II) NVIDIA(0):       HRes, HSyncStart :  576,  612
[     8.234] (II) NVIDIA(0):       HSyncEnd, HTotal :  672,  768
[     8.234] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[     8.234] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  450
[     8.234] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.234] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.234] (WW) NVIDIA(0):     Mode is rejected: HorizSync (63.0 kHz) out of range
[     8.234] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.234] (II) NVIDIA(0): 
[     8.234] (II) NVIDIA(0):   Validating Mode "1152x864":
[     8.234] (II) NVIDIA(0):     1152 x 864 @ 75 Hz
[     8.234] (II) NVIDIA(0):     Mode Source: X Server
[     8.234] (II) NVIDIA(0):       Pixel Clock      : 104.99 MHz
[     8.234] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
[     8.234] (II) NVIDIA(0):       HSyncEnd, HTotal : 1352, 1552
[     8.234] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[     8.234] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  902
[     8.235] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.235] (WW) NVIDIA(0):     Mode is rejected: HorizSync (67.6 kHz) out of range
[     8.235] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.235] (II) NVIDIA(0): 
[     8.235] (II) NVIDIA(0):   Validating Mode "576x432":
[     8.235] (II) NVIDIA(0):     576 x 432 @ 75 Hz
[     8.235] (II) NVIDIA(0):     Mode Source: X Server
[     8.235] (II) NVIDIA(0):       Pixel Clock      : 52.49 MHz
[     8.235] (II) NVIDIA(0):       HRes, HSyncStart :  576,  612
[     8.235] (II) NVIDIA(0):       HSyncEnd, HTotal :  676,  776
[     8.235] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[     8.235] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  451
[     8.235] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.235] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.235] (WW) NVIDIA(0):     Mode is rejected: HorizSync (67.6 kHz) out of range
[     8.235] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.235] (II) NVIDIA(0): 
[     8.235] (II) NVIDIA(0):   Validating Mode "1152x864":
[     8.235] (II) NVIDIA(0):     1152 x 864 @ 85 Hz
[     8.235] (II) NVIDIA(0):     Mode Source: X Server
[     8.235] (II) NVIDIA(0):       Pixel Clock      : 119.65 MHz
[     8.235] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
[     8.235] (II) NVIDIA(0):       HSyncEnd, HTotal : 1352, 1552
[     8.235] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[     8.235] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  907
[     8.235] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.235] (WW) NVIDIA(0):     Mode is rejected: HorizSync (77.1 kHz) out of range
[     8.235] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.235] (II) NVIDIA(0): 
[     8.236] (II) NVIDIA(0):   Validating Mode "576x432":
[     8.236] (II) NVIDIA(0):     576 x 432 @ 85 Hz
[     8.236] (II) NVIDIA(0):     Mode Source: X Server
[     8.236] (II) NVIDIA(0):       Pixel Clock      : 59.83 MHz
[     8.236] (II) NVIDIA(0):       HRes, HSyncStart :  576,  612
[     8.236] (II) NVIDIA(0):       HSyncEnd, HTotal :  676,  776
[     8.236] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[     8.236] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  453
[     8.236] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.236] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.236] (WW) NVIDIA(0):     Mode is rejected: HorizSync (77.1 kHz) out of range
[     8.236] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.236] (II) NVIDIA(0): 
[     8.236] (II) NVIDIA(0):   Validating Mode "1152x864":
[     8.236] (II) NVIDIA(0):     1152 x 864 @ 85 Hz
[     8.236] (II) NVIDIA(0):     Mode Source: X Server
[     8.236] (II) NVIDIA(0):       Pixel Clock      : 121.50 MHz
[     8.236] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
[     8.236] (II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1568
[     8.236] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[     8.236] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  911
[     8.236] (II) NVIDIA(0):       H/V Polarity     : +/-
[     8.236] (WW) NVIDIA(0):     Mode is rejected: HorizSync (77.5 kHz) out of range
[     8.236] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.236] (II) NVIDIA(0): 
[     8.236] (II) NVIDIA(0):   Validating Mode "576x432":
[     8.236] (II) NVIDIA(0):     576 x 432 @ 85 Hz
[     8.236] (II) NVIDIA(0):     Mode Source: X Server
[     8.236] (II) NVIDIA(0):       Pixel Clock      : 60.75 MHz
[     8.237] (II) NVIDIA(0):       HRes, HSyncStart :  576,  608
[     8.237] (II) NVIDIA(0):       HSyncEnd, HTotal :  672,  784
[     8.237] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[     8.237] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  455
[     8.237] (II) NVIDIA(0):       H/V Polarity     : +/-
[     8.237] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.237] (WW) NVIDIA(0):     Mode is rejected: HorizSync (77.5 kHz) out of range
[     8.237] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.237] (II) NVIDIA(0): 
[     8.237] (II) NVIDIA(0):   Validating Mode "1152x864":
[     8.237] (II) NVIDIA(0):     1152 x 864 @ 100 Hz
[     8.237] (II) NVIDIA(0):     Mode Source: X Server
[     8.237] (II) NVIDIA(0):       Pixel Clock      : 143.47 MHz
[     8.237] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1232
[     8.237] (II) NVIDIA(0):       HSyncEnd, HTotal : 1360, 1568
[     8.237] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[     8.237] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  915
[     8.237] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.237] (WW) NVIDIA(0):     Mode is rejected: HorizSync (91.5 kHz) out of range
[     8.237] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.237] (II) NVIDIA(0): 
[     8.237] (II) NVIDIA(0):   Validating Mode "576x432":
[     8.237] (II) NVIDIA(0):     576 x 432 @ 100 Hz
[     8.237] (II) NVIDIA(0):     Mode Source: X Server
[     8.237] (II) NVIDIA(0):       Pixel Clock      : 71.73 MHz
[     8.237] (II) NVIDIA(0):       HRes, HSyncStart :  576,  616
[     8.237] (II) NVIDIA(0):       HSyncEnd, HTotal :  680,  784
[     8.237] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[     8.237] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  457
[     8.237] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.238] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.238] (WW) NVIDIA(0):     Mode is rejected: HorizSync (91.5 kHz) out of range
[     8.238] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.238] (II) NVIDIA(0): 
[     8.238] (II) NVIDIA(0):   Validating Mode "1360x768":
[     8.238] (II) NVIDIA(0):     1360 x 768 @ 60 Hz
[     8.238] (II) NVIDIA(0):     Mode Source: X Server
[     8.238] (II) NVIDIA(0):       Pixel Clock      : 72.00 MHz
[     8.238] (II) NVIDIA(0):       HRes, HSyncStart : 1360, 1408
[     8.238] (II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1520
[     8.238] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[     8.238] (II) NVIDIA(0):       VSyncEnd, VTotal :  781,  790
[     8.238] (II) NVIDIA(0):       H/V Polarity     : +/-
[     8.238] (II) NVIDIA(GPU-0):     BestFit Centered         1360x768
[     8.239] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[     8.239] (II) NVIDIA(GPU-0):       Vertical Taps          0
[     8.239] (II) NVIDIA(GPU-0):       Base SuperSample       x4
[     8.239] (II) NVIDIA(GPU-0):       Base Depth             32
[     8.239] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[     8.239] (II) NVIDIA(GPU-0):       Overlay Depth          32
[     8.239] (II) NVIDIA(0):     Mode is valid.
[     8.239] (II) NVIDIA(0): 
[     8.239] (II) NVIDIA(0):   Validating Mode "680x384":
[     8.239] (II) NVIDIA(0):     680 x 384 @ 60 Hz
[     8.239] (II) NVIDIA(0):     Mode Source: X Server
[     8.239] (II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
[     8.239] (II) NVIDIA(0):       HRes, HSyncStart :  680,  704
[     8.239] (II) NVIDIA(0):       HSyncEnd, HTotal :  720,  760
[     8.239] (II) NVIDIA(0):       VRes, VSyncStart :  384,  385
[     8.239] (II) NVIDIA(0):       VSyncEnd, VTotal :  390,  395
[     8.239] (II) NVIDIA(0):       H/V Polarity     : +/-
[     8.239] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.240] (II) NVIDIA(GPU-0):     BestFit Centered         680x768
[     8.240] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[     8.240] (II) NVIDIA(GPU-0):       Vertical Taps          1
[     8.240] (II) NVIDIA(GPU-0):       Base SuperSample       x4
[     8.240] (II) NVIDIA(GPU-0):       Base Depth             32
[     8.240] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[     8.240] (II) NVIDIA(GPU-0):       Overlay Depth          32
[     8.240] (II) NVIDIA(0):     Mode is valid.
[     8.240] (II) NVIDIA(0): 
[     8.240] (II) NVIDIA(0):   Validating Mode "1360x768":
[     8.240] (II) NVIDIA(0):     1360 x 768 @ 60 Hz
[     8.240] (II) NVIDIA(0):     Mode Source: X Server
[     8.240] (II) NVIDIA(0):       Pixel Clock      : 84.75 MHz
[     8.240] (II) NVIDIA(0):       HRes, HSyncStart : 1360, 1432
[     8.240] (II) NVIDIA(0):       HSyncEnd, HTotal : 1568, 1776
[     8.240] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[     8.240] (II) NVIDIA(0):       VSyncEnd, VTotal :  781,  798
[     8.240] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.241] (II) NVIDIA(GPU-0):     BestFit Centered         1360x768
[     8.241] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[     8.241] (II) NVIDIA(GPU-0):       Vertical Taps          0
[     8.241] (II) NVIDIA(GPU-0):       Base SuperSample       x4
[     8.241] (II) NVIDIA(GPU-0):       Base Depth             32
[     8.241] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[     8.241] (II) NVIDIA(GPU-0):       Overlay Depth          32
[     8.241] (II) NVIDIA(0):     Mode is valid.
[     8.241] (II) NVIDIA(0): 
[     8.241] (II) NVIDIA(0):   Validating Mode "680x384":
[     8.241] (II) NVIDIA(0):     680 x 384 @ 60 Hz
[     8.241] (II) NVIDIA(0):     Mode Source: X Server
[     8.241] (II) NVIDIA(0):       Pixel Clock      : 42.38 MHz
[     8.241] (II) NVIDIA(0):       HRes, HSyncStart :  680,  716
[     8.241] (II) NVIDIA(0):       HSyncEnd, HTotal :  784,  888
[     8.241] (II) NVIDIA(0):       VRes, VSyncStart :  384,  385
[     8.241] (II) NVIDIA(0):       VSyncEnd, VTotal :  390,  399
[     8.241] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.241] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.242] (II) NVIDIA(GPU-0):     BestFit Centered         680x768
[     8.242] (II) NVIDIA(GPU-0):       Horizontal Taps        1
[     8.242] (II) NVIDIA(GPU-0):       Vertical Taps          1
[     8.242] (II) NVIDIA(GPU-0):       Base SuperSample       x4
[     8.242] (II) NVIDIA(GPU-0):       Base Depth             32
[     8.242] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[     8.242] (II) NVIDIA(GPU-0):       Overlay Depth          32
[     8.242] (II) NVIDIA(0):     Mode is valid.
[     8.242] (II) NVIDIA(0): 
[     8.242] (II) NVIDIA(0):   Validating Mode "1400x1050":
[     8.242] (II) NVIDIA(0):     1400 x 1050 @ 60 Hz
[     8.242] (II) NVIDIA(0):     Mode Source: X Server
[     8.242] (II) NVIDIA(0):       Pixel Clock      : 122.00 MHz
[     8.242] (II) NVIDIA(0):       HRes, HSyncStart : 1400, 1488
[     8.242] (II) NVIDIA(0):       HSyncEnd, HTotal : 1640, 1880
[     8.242] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1052
[     8.242] (II) NVIDIA(0):       VSyncEnd, VTotal : 1064, 1082
[     8.243] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.243] (WW) NVIDIA(0):     Mode is rejected: HorizSync (64.9 kHz) out of range
[     8.243] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.243] (II) NVIDIA(0): 
[     8.243] (II) NVIDIA(0):   Validating Mode "700x525":
[     8.243] (II) NVIDIA(0):     700 x 525 @ 60 Hz
[     8.243] (II) NVIDIA(0):     Mode Source: X Server
[     8.243] (II) NVIDIA(0):       Pixel Clock      : 61.00 MHz
[     8.243] (II) NVIDIA(0):       HRes, HSyncStart :  700,  744
[     8.243] (II) NVIDIA(0):       HSyncEnd, HTotal :  820,  940
[     8.243] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[     8.243] (II) NVIDIA(0):       VSyncEnd, VTotal :  532,  541
[     8.243] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.243] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.243] (WW) NVIDIA(0):     Mode is rejected: HorizSync (64.9 kHz) out of range
[     8.243] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.243] (II) NVIDIA(0): 
[     8.243] (II) NVIDIA(0):   Validating Mode "1400x1050":
[     8.243] (II) NVIDIA(0):     1400 x 1050 @ 70 Hz
[     8.243] (II) NVIDIA(0):     Mode Source: X Server
[     8.243] (II) NVIDIA(0):       Pixel Clock      : 145.06 MHz
[     8.243] (II) NVIDIA(0):       HRes, HSyncStart : 1400, 1496
[     8.243] (II) NVIDIA(0):       HSyncEnd, HTotal : 1648, 1896
[     8.243] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1051
[     8.243] (II) NVIDIA(0):       VSyncEnd, VTotal : 1054, 1093
[     8.243] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.243] (WW) NVIDIA(0):     Mode is rejected: HorizSync (76.5 kHz) out of range
[     8.243] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.243] (II) NVIDIA(0): 
[     8.244] (II) NVIDIA(0):   Validating Mode "700x525":
[     8.244] (II) NVIDIA(0):     700 x 525 @ 70 Hz
[     8.244] (II) NVIDIA(0):     Mode Source: X Server
[     8.244] (II) NVIDIA(0):       Pixel Clock      : 72.53 MHz
[     8.244] (II) NVIDIA(0):       HRes, HSyncStart :  700,  748
[     8.244] (II) NVIDIA(0):       HSyncEnd, HTotal :  824,  948
[     8.244] (II) NVIDIA(0):       VRes, VSyncStart :  525,  525
[     8.244] (II) NVIDIA(0):       VSyncEnd, VTotal :  527,  546
[     8.244] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.244] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.244] (WW) NVIDIA(0):     Mode is rejected: HorizSync (76.5 kHz) out of range
[     8.244] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.244] (II) NVIDIA(0): 
[     8.244] (II) NVIDIA(0):   Validating Mode "1400x1050":
[     8.244] (II) NVIDIA(0):     1400 x 1050 @ 75 Hz
[     8.244] (II) NVIDIA(0):     Mode Source: X Server
[     8.244] (II) NVIDIA(0):       Pixel Clock      : 155.80 MHz
[     8.244] (II) NVIDIA(0):       HRes, HSyncStart : 1400, 1464
[     8.244] (II) NVIDIA(0):       HSyncEnd, HTotal : 1784, 1912
[     8.244] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1052
[     8.244] (II) NVIDIA(0):       VSyncEnd, VTotal : 1064, 1090
[     8.244] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.244] (WW) NVIDIA(0):     Mode is rejected: HorizSync (81.5 kHz) out of range
[     8.244] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.244] (II) NVIDIA(0): 
[     8.244] (II) NVIDIA(0):   Validating Mode "700x525":
[     8.244] (II) NVIDIA(0):     700 x 525 @ 75 Hz
[     8.244] (II) NVIDIA(0):     Mode Source: X Server
[     8.244] (II) NVIDIA(0):       Pixel Clock      : 77.90 MHz
[     8.245] (II) NVIDIA(0):       HRes, HSyncStart :  700,  732
[     8.245] (II) NVIDIA(0):       HSyncEnd, HTotal :  892,  956
[     8.245] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[     8.245] (II) NVIDIA(0):       VSyncEnd, VTotal :  532,  545
[     8.245] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.245] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.245] (WW) NVIDIA(0):     Mode is rejected: HorizSync (81.5 kHz) out of range
[     8.245] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.245] (II) NVIDIA(0): 
[     8.245] (II) NVIDIA(0):   Validating Mode "1400x1050":
[     8.245] (II) NVIDIA(0):     1400 x 1050 @ 85 Hz
[     8.245] (II) NVIDIA(0):     Mode Source: X Server
[     8.245] (II) NVIDIA(0):       Pixel Clock      : 179.26 MHz
[     8.245] (II) NVIDIA(0):       HRes, HSyncStart : 1400, 1504
[     8.245] (II) NVIDIA(0):       HSyncEnd, HTotal : 1656, 1912
[     8.245] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1051
[     8.245] (II) NVIDIA(0):       VSyncEnd, VTotal : 1054, 1103
[     8.245] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.245] (WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
[     8.245] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.245] (II) NVIDIA(0): 
[     8.245] (II) NVIDIA(0):   Validating Mode "700x525":
[     8.245] (II) NVIDIA(0):     700 x 525 @ 85 Hz
[     8.245] (II) NVIDIA(0):     Mode Source: X Server
[     8.245] (II) NVIDIA(0):       Pixel Clock      : 89.63 MHz
[     8.245] (II) NVIDIA(0):       HRes, HSyncStart :  700,  752
[     8.245] (II) NVIDIA(0):       HSyncEnd, HTotal :  828,  956
[     8.245] (II) NVIDIA(0):       VRes, VSyncStart :  525,  525
[     8.245] (II) NVIDIA(0):       VSyncEnd, VTotal :  527,  551
[     8.246] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.246] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.246] (WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
[     8.246] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.246] (II) NVIDIA(0): 
[     8.246] (II) NVIDIA(0):   Validating Mode "1440x900":
[     8.246] (II) NVIDIA(0):     1440 x 900 @ 60 Hz
[     8.246] (II) NVIDIA(0):     Mode Source: X Server
[     8.246] (II) NVIDIA(0):       Pixel Clock      : 106.50 MHz
[     8.246] (II) NVIDIA(0):       HRes, HSyncStart : 1440, 1520
[     8.246] (II) NVIDIA(0):       HSyncEnd, HTotal : 1672, 1904
[     8.246] (II) NVIDIA(0):       VRes, VSyncStart :  900,  903
[     8.246] (II) NVIDIA(0):       VSyncEnd, VTotal :  909,  934
[     8.246] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.246] (WW) NVIDIA(0):     Mode is rejected: HorizSync (55.9 kHz) out of range
[     8.246] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.246] (II) NVIDIA(0): 
[     8.246] (II) NVIDIA(0):   Validating Mode "720x450":
[     8.246] (II) NVIDIA(0):     720 x 450 @ 60 Hz
[     8.246] (II) NVIDIA(0):     Mode Source: X Server
[     8.246] (II) NVIDIA(0):       Pixel Clock      : 53.25 MHz
[     8.246] (II) NVIDIA(0):       HRes, HSyncStart :  720,  760
[     8.246] (II) NVIDIA(0):       HSyncEnd, HTotal :  836,  952
[     8.246] (II) NVIDIA(0):       VRes, VSyncStart :  450,  451
[     8.246] (II) NVIDIA(0):       VSyncEnd, VTotal :  454,  467
[     8.246] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.246] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.246] (WW) NVIDIA(0):     Mode is rejected: HorizSync (55.9 kHz) out of range
[     8.246] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.246] (II) NVIDIA(0): 
[     8.247] (II) NVIDIA(0):   Validating Mode "1600x1024":
[     8.247] (II) NVIDIA(0):     1600 x 1024 @ 60 Hz
[     8.247] (II) NVIDIA(0):     Mode Source: X Server
[     8.247] (II) NVIDIA(0):       Pixel Clock      : 103.12 MHz
[     8.247] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1600
[     8.247] (II) NVIDIA(0):       HSyncEnd, HTotal : 1656, 1664
[     8.247] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1024
[     8.247] (II) NVIDIA(0):       VSyncEnd, VTotal : 1029, 1030
[     8.247] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.247] (WW) NVIDIA(0):     Mode is rejected: HorizSync (62.0 kHz) out of range
[     8.247] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.247] (II) NVIDIA(0): 
[     8.247] (II) NVIDIA(0):   Validating Mode "800x512":
[     8.247] (II) NVIDIA(0):     800 x 512 @ 60 Hz
[     8.247] (II) NVIDIA(0):     Mode Source: X Server
[     8.247] (II) NVIDIA(0):       Pixel Clock      : 51.56 MHz
[     8.247] (II) NVIDIA(0):       HRes, HSyncStart :  800,  800
[     8.247] (II) NVIDIA(0):       HSyncEnd, HTotal :  828,  832
[     8.247] (II) NVIDIA(0):       VRes, VSyncStart :  512,  512
[     8.247] (II) NVIDIA(0):       VSyncEnd, VTotal :  514,  515
[     8.247] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.247] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.247] (WW) NVIDIA(0):     Mode is rejected: HorizSync (62.0 kHz) out of range
[     8.247] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.247] (II) NVIDIA(0): 
[     8.247] (II) NVIDIA(0):   Validating Mode "1680x1050":
[     8.247] (II) NVIDIA(0):     1680 x 1050 @ 60 Hz
[     8.247] (II) NVIDIA(0):     Mode Source: X Server
[     8.247] (II) NVIDIA(0):       Pixel Clock      : 119.00 MHz
[     8.248] (II) NVIDIA(0):       HRes, HSyncStart : 1680, 1728
[     8.248] (II) NVIDIA(0):       HSyncEnd, HTotal : 1760, 1840
[     8.248] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
[     8.248] (II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1080
[     8.248] (II) NVIDIA(0):       H/V Polarity     : +/-
[     8.248] (WW) NVIDIA(0):     Mode is rejected: HorizSync (64.7 kHz) out of range
[     8.248] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.248] (II) NVIDIA(0): 
[     8.248] (II) NVIDIA(0):   Validating Mode "840x525":
[     8.248] (II) NVIDIA(0):     840 x 525 @ 60 Hz
[     8.248] (II) NVIDIA(0):     Mode Source: X Server
[     8.248] (II) NVIDIA(0):       Pixel Clock      : 59.50 MHz
[     8.248] (II) NVIDIA(0):       HRes, HSyncStart :  840,  864
[     8.248] (II) NVIDIA(0):       HSyncEnd, HTotal :  880,  920
[     8.248] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[     8.248] (II) NVIDIA(0):       VSyncEnd, VTotal :  529,  540
[     8.248] (II) NVIDIA(0):       H/V Polarity     : +/-
[     8.248] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.248] (WW) NVIDIA(0):     Mode is rejected: HorizSync (64.7 kHz) out of range
[     8.248] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.248] (II) NVIDIA(0): 
[     8.248] (II) NVIDIA(0):   Validating Mode "1680x1050":
[     8.248] (II) NVIDIA(0):     1680 x 1050 @ 60 Hz
[     8.248] (II) NVIDIA(0):     Mode Source: X Server
[     8.248] (II) NVIDIA(0):       Pixel Clock      : 146.25 MHz
[     8.248] (II) NVIDIA(0):       HRes, HSyncStart : 1680, 1784
[     8.248] (II) NVIDIA(0):       HSyncEnd, HTotal : 1960, 2240
[     8.248] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
[     8.248] (II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1089
[     8.249] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.249] (WW) NVIDIA(0):     Mode is rejected: HorizSync (65.3 kHz) out of range
[     8.249] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.249] (II) NVIDIA(0): 
[     8.249] (II) NVIDIA(0):   Validating Mode "840x525":
[     8.249] (II) NVIDIA(0):     840 x 525 @ 60 Hz
[     8.249] (II) NVIDIA(0):     Mode Source: X Server
[     8.249] (II) NVIDIA(0):       Pixel Clock      : 73.12 MHz
[     8.249] (II) NVIDIA(0):       HRes, HSyncStart :  840,  892
[     8.249] (II) NVIDIA(0):       HSyncEnd, HTotal :  980, 1120
[     8.249] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[     8.249] (II) NVIDIA(0):       VSyncEnd, VTotal :  529,  544
[     8.249] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.249] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.249] (WW) NVIDIA(0):     Mode is rejected: HorizSync (65.3 kHz) out of range
[     8.249] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.249] (II) NVIDIA(0): 
[     8.249] (II) NVIDIA(0):   Validating Mode "1680x1050":
[     8.249] (II) NVIDIA(0):     1680 x 1050 @ 70 Hz
[     8.249] (II) NVIDIA(0):     Mode Source: X Server
[     8.249] (II) NVIDIA(0):       Pixel Clock      : 174.00 MHz
[     8.249] (II) NVIDIA(0):       HRes, HSyncStart : 1680, 1800
[     8.249] (II) NVIDIA(0):       HSyncEnd, HTotal : 1976, 2272
[     8.249] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
[     8.249] (II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1096
[     8.249] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.249] (WW) NVIDIA(0):     Mode is rejected: HorizSync (76.6 kHz) out of range
[     8.249] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.249] (II) NVIDIA(0): 
[     8.250] (II) NVIDIA(0):   Validating Mode "840x525":
[     8.250] (II) NVIDIA(0):     840 x 525 @ 70 Hz
[     8.250] (II) NVIDIA(0):     Mode Source: X Server
[     8.250] (II) NVIDIA(0):       Pixel Clock      : 87.00 MHz
[     8.250] (II) NVIDIA(0):       HRes, HSyncStart :  840,  900
[     8.250] (II) NVIDIA(0):       HSyncEnd, HTotal :  988, 1136
[     8.250] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[     8.250] (II) NVIDIA(0):       VSyncEnd, VTotal :  529,  548
[     8.250] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.250] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.250] (WW) NVIDIA(0):     Mode is rejected: HorizSync (76.6 kHz) out of range
[     8.250] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.250] (II) NVIDIA(0): 
[     8.250] (II) NVIDIA(0):   Validating Mode "1680x1050":
[     8.250] (II) NVIDIA(0):     1680 x 1050 @ 75 Hz
[     8.250] (II) NVIDIA(0):     Mode Source: X Server
[     8.250] (II) NVIDIA(0):       Pixel Clock      : 187.00 MHz
[     8.250] (II) NVIDIA(0):       HRes, HSyncStart : 1680, 1800
[     8.250] (II) NVIDIA(0):       HSyncEnd, HTotal : 1976, 2272
[     8.250] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
[     8.250] (II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1099
[     8.250] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.250] (WW) NVIDIA(0):     Mode is rejected: HorizSync (82.3 kHz) out of range
[     8.250] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.250] (II) NVIDIA(0): 
[     8.250] (II) NVIDIA(0):   Validating Mode "840x525":
[     8.250] (II) NVIDIA(0):     840 x 525 @ 75 Hz
[     8.250] (II) NVIDIA(0):     Mode Source: X Server
[     8.250] (II) NVIDIA(0):       Pixel Clock      : 93.50 MHz
[     8.250] (II) NVIDIA(0):       HRes, HSyncStart :  840,  900
[     8.251] (II) NVIDIA(0):       HSyncEnd, HTotal :  988, 1136
[     8.251] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[     8.251] (II) NVIDIA(0):       VSyncEnd, VTotal :  529,  549
[     8.251] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.251] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.251] (WW) NVIDIA(0):     Mode is rejected: HorizSync (82.3 kHz) out of range
[     8.251] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.251] (II) NVIDIA(0): 
[     8.251] (II) NVIDIA(0):   Validating Mode "1680x1050":
[     8.251] (II) NVIDIA(0):     1680 x 1050 @ 85 Hz
[     8.251] (II) NVIDIA(0):     Mode Source: X Server
[     8.251] (II) NVIDIA(0):       Pixel Clock      : 214.75 MHz
[     8.251] (II) NVIDIA(0):       HRes, HSyncStart : 1680, 1808
[     8.251] (II) NVIDIA(0):       HSyncEnd, HTotal : 1984, 2288
[     8.251] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
[     8.251] (II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1105
[     8.251] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.251] (WW) NVIDIA(0):     Mode is rejected: HorizSync (93.9 kHz) out of range
[     8.251] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.251] (II) NVIDIA(0): 
[     8.251] (II) NVIDIA(0):   Validating Mode "840x525":
[     8.251] (II) NVIDIA(0):     840 x 525 @ 85 Hz
[     8.251] (II) NVIDIA(0):     Mode Source: X Server
[     8.251] (II) NVIDIA(0):       Pixel Clock      : 107.38 MHz
[     8.251] (II) NVIDIA(0):       HRes, HSyncStart :  840,  904
[     8.251] (II) NVIDIA(0):       HSyncEnd, HTotal :  992, 1144
[     8.251] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[     8.251] (II) NVIDIA(0):       VSyncEnd, VTotal :  529,  552
[     8.251] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.252] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.252] (WW) NVIDIA(0):     Mode is rejected: HorizSync (93.9 kHz) out of range
[     8.252] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.252] (II) NVIDIA(0): 
[     8.252] (II) NVIDIA(0):   Validating Mode "1920x1080":
[     8.252] (II) NVIDIA(0):     1920 x 1080 @ 60 Hz
[     8.252] (II) NVIDIA(0):     Mode Source: X Server
[     8.252] (II) NVIDIA(0):       Pixel Clock      : 138.50 MHz
[     8.252] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 1968
[     8.252] (II) NVIDIA(0):       HSyncEnd, HTotal : 2000, 2080
[     8.252] (II) NVIDIA(0):       VRes, VSyncStart : 1080, 1083
[     8.252] (II) NVIDIA(0):       VSyncEnd, VTotal : 1088, 1111
[     8.252] (II) NVIDIA(0):       H/V Polarity     : +/-
[     8.252] (WW) NVIDIA(0):     Mode is rejected: HorizSync (66.6 kHz) out of range
[     8.252] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.252] (II) NVIDIA(0): 
[     8.252] (II) NVIDIA(0):   Validating Mode "960x540":
[     8.252] (II) NVIDIA(0):     960 x 540 @ 60 Hz
[     8.252] (II) NVIDIA(0):     Mode Source: X Server
[     8.252] (II) NVIDIA(0):       Pixel Clock      : 69.25 MHz
[     8.252] (II) NVIDIA(0):       HRes, HSyncStart :  960,  984
[     8.252] (II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
[     8.252] (II) NVIDIA(0):       VRes, VSyncStart :  540,  541
[     8.252] (II) NVIDIA(0):       VSyncEnd, VTotal :  544,  555
[     8.252] (II) NVIDIA(0):       H/V Polarity     : +/-
[     8.252] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.252] (WW) NVIDIA(0):     Mode is rejected: HorizSync (66.6 kHz) out of range
[     8.252] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.252] (II) NVIDIA(0): 
[     8.253] (II) NVIDIA(0):   Validating Mode "1920x1200":
[     8.253] (II) NVIDIA(0):     1920 x 1200 @ 60 Hz
[     8.253] (II) NVIDIA(0):     Mode Source: X Server
[     8.253] (II) NVIDIA(0):       Pixel Clock      : 154.00 MHz
[     8.253] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 1968
[     8.253] (II) NVIDIA(0):       HSyncEnd, HTotal : 2000, 2080
[     8.253] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1203
[     8.253] (II) NVIDIA(0):       VSyncEnd, VTotal : 1209, 1235
[     8.253] (II) NVIDIA(0):       H/V Polarity     : +/-
[     8.253] (WW) NVIDIA(0):     Mode is rejected: HorizSync (74.0 kHz) out of range
[     8.253] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.253] (II) NVIDIA(0): 
[     8.253] (II) NVIDIA(0):   Validating Mode "960x600":
[     8.253] (II) NVIDIA(0):     960 x 600 @ 60 Hz
[     8.253] (II) NVIDIA(0):     Mode Source: X Server
[     8.253] (II) NVIDIA(0):       Pixel Clock      : 77.00 MHz
[     8.253] (II) NVIDIA(0):       HRes, HSyncStart :  960,  984
[     8.253] (II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
[     8.253] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[     8.253] (II) NVIDIA(0):       VSyncEnd, VTotal :  604,  617
[     8.253] (II) NVIDIA(0):       H/V Polarity     : +/-
[     8.253] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.253] (WW) NVIDIA(0):     Mode is rejected: HorizSync (74.0 kHz) out of range
[     8.253] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.253] (II) NVIDIA(0): 
[     8.253] (II) NVIDIA(0):   Validating Mode "1920x1440":
[     8.253] (II) NVIDIA(0):     1920 x 1440 @ 85 Hz
[     8.253] (II) NVIDIA(0):     Mode Source: X Server
[     8.253] (II) NVIDIA(0):       Pixel Clock      : 341.35 MHz
[     8.254] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2072
[     8.254] (II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2656
[     8.254] (II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
[     8.254] (II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1512
[     8.254] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.254] (WW) NVIDIA(0):     Mode is rejected: HorizSync (128.5 kHz) out of range
[     8.254] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.254] (II) NVIDIA(0): 
[     8.254] (II) NVIDIA(0):   Validating Mode "960x720":
[     8.254] (II) NVIDIA(0):     960 x 720 @ 85 Hz
[     8.254] (II) NVIDIA(0):     Mode Source: X Server
[     8.254] (II) NVIDIA(0):       Pixel Clock      : 170.68 MHz
[     8.254] (II) NVIDIA(0):       HRes, HSyncStart :  960, 1036
[     8.254] (II) NVIDIA(0):       HSyncEnd, HTotal : 1144, 1328
[     8.254] (II) NVIDIA(0):       VRes, VSyncStart :  720,  720
[     8.254] (II) NVIDIA(0):       VSyncEnd, VTotal :  722,  756
[     8.254] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.254] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.254] (WW) NVIDIA(0):     Mode is rejected: HorizSync (128.5 kHz) out of range
[     8.254] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.254] (II) NVIDIA(0): 
[     8.254] (II) NVIDIA(0):   Validating Mode "2048x1536":
[     8.254] (II) NVIDIA(0):     2048 x 1536 @ 60 Hz
[     8.254] (II) NVIDIA(0):     Mode Source: X Server
[     8.254] (II) NVIDIA(0):       Pixel Clock      : 266.95 MHz
[     8.254] (II) NVIDIA(0):       HRes, HSyncStart : 2048, 2200
[     8.254] (II) NVIDIA(0):       HSyncEnd, HTotal : 2424, 2800
[     8.254] (II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
[     8.254] (II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1589
[     8.254] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.255] (WW) NVIDIA(0):     Mode is rejected: HorizSync (95.3 kHz) out of range
[     8.255] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.255] (II) NVIDIA(0): 
[     8.255] (II) NVIDIA(0):   Validating Mode "1024x768":
[     8.255] (II) NVIDIA(0):     1024 x 768 @ 60 Hz
[     8.255] (II) NVIDIA(0):     Mode Source: X Server
[     8.255] (II) NVIDIA(0):       Pixel Clock      : 133.47 MHz
[     8.255] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1100
[     8.255] (II) NVIDIA(0):       HSyncEnd, HTotal : 1212, 1400
[     8.255] (II) NVIDIA(0):       VRes, VSyncStart :  768,  768
[     8.255] (II) NVIDIA(0):       VSyncEnd, VTotal :  770,  794
[     8.255] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.255] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.255] (WW) NVIDIA(0):     Mode is rejected: HorizSync (95.3 kHz) out of range
[     8.255] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.255] (II) NVIDIA(0): 
[     8.255] (II) NVIDIA(0):   Validating Mode "2048x1536":
[     8.255] (II) NVIDIA(0):     2048 x 1536 @ 75 Hz
[     8.255] (II) NVIDIA(0):     Mode Source: X Server
[     8.255] (II) NVIDIA(0):       Pixel Clock      : 340.48 MHz
[     8.255] (II) NVIDIA(0):       HRes, HSyncStart : 2048, 2216
[     8.255] (II) NVIDIA(0):       HSyncEnd, HTotal : 2440, 2832
[     8.255] (II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
[     8.255] (II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1603
[     8.255] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.255] (WW) NVIDIA(0):     Mode is rejected: HorizSync (120.2 kHz) out of range
[     8.255] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.255] (II) NVIDIA(0): 
[     8.255] (II) NVIDIA(0):   Validating Mode "1024x768":
[     8.256] (II) NVIDIA(0):     1024 x 768 @ 75 Hz
[     8.256] (II) NVIDIA(0):     Mode Source: X Server
[     8.256] (II) NVIDIA(0):       Pixel Clock      : 170.24 MHz
[     8.256] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1108
[     8.256] (II) NVIDIA(0):       HSyncEnd, HTotal : 1220, 1416
[     8.256] (II) NVIDIA(0):       VRes, VSyncStart :  768,  768
[     8.256] (II) NVIDIA(0):       VSyncEnd, VTotal :  770,  801
[     8.256] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.256] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.256] (WW) NVIDIA(0):     Mode is rejected: HorizSync (120.2 kHz) out of range
[     8.256] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.256] (II) NVIDIA(0): 
[     8.256] (II) NVIDIA(0):   Validating Mode "2048x1536":
[     8.256] (II) NVIDIA(0):     2048 x 1536 @ 85 Hz
[     8.256] (II) NVIDIA(0):     Mode Source: X Server
[     8.256] (II) NVIDIA(0):       Pixel Clock      : 388.04 MHz
[     8.256] (II) NVIDIA(0):       HRes, HSyncStart : 2048, 2216
[     8.256] (II) NVIDIA(0):       HSyncEnd, HTotal : 2440, 2832
[     8.256] (II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
[     8.256] (II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1612
[     8.256] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.256] (WW) NVIDIA(0):     Mode is rejected: HorizSync (137.0 kHz) out of range
[     8.256] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.256] (II) NVIDIA(0): 
[     8.256] (II) NVIDIA(0):   Validating Mode "1024x768":
[     8.256] (II) NVIDIA(0):     1024 x 768 @ 85 Hz
[     8.256] (II) NVIDIA(0):     Mode Source: X Server
[     8.256] (II) NVIDIA(0):       Pixel Clock      : 194.02 MHz
[     8.257] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1108
[     8.257] (II) NVIDIA(0):       HSyncEnd, HTotal : 1220, 1416
[     8.257] (II) NVIDIA(0):       VRes, VSyncStart :  768,  768
[     8.257] (II) NVIDIA(0):       VSyncEnd, VTotal :  770,  806
[     8.257] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.257] (II) NVIDIA(0):       Extra            : DoubleScan
[     8.257] (WW) NVIDIA(0):     Mode is rejected: HorizSync (137.0 kHz) out of range
[     8.257] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.257] (II) NVIDIA(0): 
[     8.257] (II) NVIDIA(0):   Validating Mode "640x350":
[     8.257] (II) NVIDIA(0):     640 x 350 @ 85 Hz
[     8.257] (II) NVIDIA(0):     Mode Source: VESA
[     8.257] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[     8.257] (II) NVIDIA(0):       HRes, HSyncStart :  640,  672
[     8.257] (II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
[     8.257] (II) NVIDIA(0):       VRes, VSyncStart :  350,  382
[     8.257] (II) NVIDIA(0):       VSyncEnd, VTotal :  385,  445
[     8.257] (II) NVIDIA(0):       H/V Polarity     : +/-
[     8.257] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
[     8.257] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.257] (II) NVIDIA(0): 
[     8.257] (II) NVIDIA(0):   Validating Mode "640x400":
[     8.257] (II) NVIDIA(0):     640 x 400 @ 85 Hz
[     8.257] (II) NVIDIA(0):     Mode Source: VESA
[     8.257] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[     8.257] (II) NVIDIA(0):       HRes, HSyncStart :  640,  672
[     8.257] (II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
[     8.257] (II) NVIDIA(0):       VRes, VSyncStart :  400,  401
[     8.257] (II) NVIDIA(0):       VSyncEnd, VTotal :  404,  445
[     8.257] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.258] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
[     8.258] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.258] (II) NVIDIA(0): 
[     8.258] (II) NVIDIA(0):   Validating Mode "720x400":
[     8.258] (II) NVIDIA(0):     720 x 400 @ 85 Hz
[     8.258] (II) NVIDIA(0):     Mode Source: VESA
[     8.258] (II) NVIDIA(0):       Pixel Clock      : 35.50 MHz
[     8.258] (II) NVIDIA(0):       HRes, HSyncStart :  720,  756
[     8.258] (II) NVIDIA(0):       HSyncEnd, HTotal :  828,  936
[     8.258] (II) NVIDIA(0):       VRes, VSyncStart :  400,  401
[     8.258] (II) NVIDIA(0):       VSyncEnd, VTotal :  404,  446
[     8.258] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.258] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
[     8.258] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.258] (II) NVIDIA(0): 
[     8.258] (II) NVIDIA(0):   Validating Mode "640x480":
[     8.258] (II) NVIDIA(0):     640 x 480 @ 60 Hz
[     8.258] (II) NVIDIA(0):     Mode Source: VESA
[     8.258] (II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
[     8.258] (II) NVIDIA(0):       HRes, HSyncStart :  640,  656
[     8.258] (II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
[     8.258] (II) NVIDIA(0):       VRes, VSyncStart :  480,  490
[     8.258] (II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
[     8.258] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.259] (II) NVIDIA(GPU-0):     BestFit Centered         640x480
[     8.259] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[     8.259] (II) NVIDIA(GPU-0):       Vertical Taps          0
[     8.259] (II) NVIDIA(GPU-0):       Base SuperSample       x4
[     8.259] (II) NVIDIA(GPU-0):       Base Depth             32
[     8.259] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[     8.259] (II) NVIDIA(GPU-0):       Overlay Depth          32
[     8.259] (II) NVIDIA(0):     Mode is valid.
[     8.259] (II) NVIDIA(0): 
[     8.259] (II) NVIDIA(0):   Validating Mode "640x480":
[     8.259] (II) NVIDIA(0):     640 x 480 @ 73 Hz
[     8.259] (II) NVIDIA(0):     Mode Source: VESA
[     8.259] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[     8.259] (II) NVIDIA(0):       HRes, HSyncStart :  640,  664
[     8.259] (II) NVIDIA(0):       HSyncEnd, HTotal :  704,  832
[     8.259] (II) NVIDIA(0):       VRes, VSyncStart :  480,  489
[     8.259] (II) NVIDIA(0):       VSyncEnd, VTotal :  492,  520
[     8.259] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.259] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (72.8 Hz) out of range
[     8.260] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.260] (II) NVIDIA(0): 
[     8.260] (II) NVIDIA(0):   Validating Mode "640x480":
[     8.260] (II) NVIDIA(0):     640 x 480 @ 75 Hz
[     8.260] (II) NVIDIA(0):     Mode Source: VESA
[     8.260] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[     8.260] (II) NVIDIA(0):       HRes, HSyncStart :  640,  656
[     8.260] (II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
[     8.260] (II) NVIDIA(0):       VRes, VSyncStart :  480,  481
[     8.260] (II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
[     8.260] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.260] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
[     8.260] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.260] (II) NVIDIA(0): 
[     8.260] (II) NVIDIA(0):   Validating Mode "640x480":
[     8.260] (II) NVIDIA(0):     640 x 480 @ 85 Hz
[     8.260] (II) NVIDIA(0):     Mode Source: VESA
[     8.260] (II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
[     8.260] (II) NVIDIA(0):       HRes, HSyncStart :  640,  696
[     8.260] (II) NVIDIA(0):       HSyncEnd, HTotal :  752,  832
[     8.260] (II) NVIDIA(0):       VRes, VSyncStart :  480,  481
[     8.260] (II) NVIDIA(0):       VSyncEnd, VTotal :  484,  509
[     8.260] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.260] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
[     8.260] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.260] (II) NVIDIA(0): 
[     8.260] (II) NVIDIA(0):   Validating Mode "800x600":
[     8.260] (II) NVIDIA(0):     800 x 600 @ 56 Hz
[     8.260] (II) NVIDIA(0):     Mode Source: VESA
[     8.261] (II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
[     8.261] (II) NVIDIA(0):       HRes, HSyncStart :  800,  824
[     8.261] (II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1024
[     8.261] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[     8.261] (II) NVIDIA(0):       VSyncEnd, VTotal :  603,  625
[     8.261] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.261] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[     8.261] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[     8.261] (II) NVIDIA(GPU-0):       Vertical Taps          0
[     8.261] (II) NVIDIA(GPU-0):       Base SuperSample       x4
[     8.261] (II) NVIDIA(GPU-0):       Base Depth             32
[     8.261] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[     8.261] (II) NVIDIA(GPU-0):       Overlay Depth          32
[     8.261] (II) NVIDIA(0):     Mode is valid.
[     8.261] (II) NVIDIA(0): 
[     8.262] (II) NVIDIA(0):   Validating Mode "800x600":
[     8.262] (II) NVIDIA(0):     800 x 600 @ 60 Hz
[     8.262] (II) NVIDIA(0):     Mode Source: VESA
[     8.262] (II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
[     8.262] (II) NVIDIA(0):       HRes, HSyncStart :  800,  840
[     8.262] (II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
[     8.262] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[     8.262] (II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
[     8.262] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.262] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[     8.262] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[     8.262] (II) NVIDIA(GPU-0):       Vertical Taps          0
[     8.262] (II) NVIDIA(GPU-0):       Base SuperSample       x4
[     8.262] (II) NVIDIA(GPU-0):       Base Depth             32
[     8.263] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[     8.263] (II) NVIDIA(GPU-0):       Overlay Depth          32
[     8.263] (II) NVIDIA(0):     Mode is valid.
[     8.263] (II) NVIDIA(0): 
[     8.263] (II) NVIDIA(0):   Validating Mode "800x600":
[     8.263] (II) NVIDIA(0):     800 x 600 @ 72 Hz
[     8.263] (II) NVIDIA(0):     Mode Source: VESA
[     8.263] (II) NVIDIA(0):       Pixel Clock      : 50.00 MHz
[     8.263] (II) NVIDIA(0):       HRes, HSyncStart :  800,  856
[     8.263] (II) NVIDIA(0):       HSyncEnd, HTotal :  976, 1040
[     8.263] (II) NVIDIA(0):       VRes, VSyncStart :  600,  637
[     8.263] (II) NVIDIA(0):       VSyncEnd, VTotal :  643,  666
[     8.263] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.263] (II) NVIDIA(GPU-0):     BestFit Centered         800x600
[     8.263] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[     8.264] (II) NVIDIA(GPU-0):       Vertical Taps          0
[     8.264] (II) NVIDIA(GPU-0):       Base SuperSample       x4
[     8.264] (II) NVIDIA(GPU-0):       Base Depth             32
[     8.264] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[     8.264] (II) NVIDIA(GPU-0):       Overlay Depth          32
[     8.264] (II) NVIDIA(0):     Mode is valid.
[     8.264] (II) NVIDIA(0): 
[     8.264] (II) NVIDIA(0):   Validating Mode "800x600":
[     8.264] (II) NVIDIA(0):     800 x 600 @ 75 Hz
[     8.264] (II) NVIDIA(0):     Mode Source: VESA
[     8.264] (II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
[     8.264] (II) NVIDIA(0):       HRes, HSyncStart :  800,  816
[     8.264] (II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
[     8.264] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[     8.264] (II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
[     8.264] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.264] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
[     8.264] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.264] (II) NVIDIA(0): 
[     8.264] (II) NVIDIA(0):   Validating Mode "800x600":
[     8.264] (II) NVIDIA(0):     800 x 600 @ 85 Hz
[     8.264] (II) NVIDIA(0):     Mode Source: VESA
[     8.264] (II) NVIDIA(0):       Pixel Clock      : 56.30 MHz
[     8.264] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[     8.264] (II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1048
[     8.264] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[     8.264] (II) NVIDIA(0):       VSyncEnd, VTotal :  604,  631
[     8.264] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.264] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
[     8.265] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.265] (II) NVIDIA(0): 
[     8.265] (II) NVIDIA(0):   Validating Mode "1024x768":
[     8.265] (II) NVIDIA(0):     1024 x 768 @ 87 Hz
[     8.265] (II) NVIDIA(0):     Mode Source: VESA
[     8.265] (II) NVIDIA(0):       Pixel Clock      : 44.90 MHz
[     8.265] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1032
[     8.265] (II) NVIDIA(0):       HSyncEnd, HTotal : 1208, 1264
[     8.265] (II) NVIDIA(0):       VRes, VSyncStart :  768,  768
[     8.265] (II) NVIDIA(0):       VSyncEnd, VTotal :  776,  817
[     8.265] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.265] (II) NVIDIA(0):       Extra            : Interlace
[     8.265] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.0 Hz) out of range
[     8.265] (WW) NVIDIA(0):     (43.000-72.000 Hz).
[     8.265] (II) NVIDIA(0): 
[     8.265] (II) NVIDIA(0):   Validating Mode "1024x768":
[     8.265] (II) NVIDIA(0):     1024 x 768 @ 60 Hz
[     8.265] (II) NVIDIA(0):     Mode Source: VESA
[     8.265] (II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
[     8.265] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
[     8.265] (II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
[     8.265] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[     8.265] (II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
[     8.265] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.266] (II) NVIDIA(GPU-0):     BestFit Centered         1024x768
[     8.266] (II) NVIDIA(GPU-0):       Horizontal Taps        0
[     8.266] (II) NVIDIA(GPU-0):       Vertical Taps          0
[     8.266] (II) NVIDIA(GPU-0):       Base SuperSample       x4
[     8.266] (II) NVIDIA(GPU-0):       Base Depth             32
[     8.266] (II) NVIDIA(GPU-0):       Distributed Rendering  1
[     8.266] (II) NVIDIA(GPU-0):       Overlay Depth          32
[     8.266] (II) NVIDIA(0):     Mode is valid.
[     8.266] (II) NVIDIA(0): 
[     8.266] (II) NVIDIA(0):   Validating Mode "1024x768":
[     8.266] (II) NVIDIA(0):     1024 x 768 @ 70 Hz
[     8.266] (II) NVIDIA(0):     Mode Source: VESA
[     8.266] (II) NVIDIA(0):       Pixel Clock      : 75.00 MHz
[     8.266] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
[     8.266] (II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1328
[     8.266] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[     8.266] (II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
[     8.266] (II) NVIDIA(0):       H/V Polarity     : -/-
[     8.266] (WW) NVIDIA(0):     Mode is rejected: HorizSync (56.5 kHz) out of range
[     8.266] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.267] (II) NVIDIA(0): 
[     8.267] (II) NVIDIA(0):   Validating Mode "1024x768":
[     8.267] (II) NVIDIA(0):     1024 x 768 @ 75 Hz
[     8.267] (II) NVIDIA(0):     Mode Source: VESA
[     8.267] (II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
[     8.267] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
[     8.267] (II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
[     8.267] (II) NVIDIA(0):       VRes, VSyncStart :  768,  769
[     8.267] (II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
[     8.267] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.267] (WW) NVIDIA(0):     Mode is rejected: HorizSync (60.0 kHz) out of range
[     8.267] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.267] (II) NVIDIA(0): 
[     8.267] (II) NVIDIA(0):   Validating Mode "1024x768":
[     8.267] (II) NVIDIA(0):     1024 x 768 @ 85 Hz
[     8.267] (II) NVIDIA(0):     Mode Source: VESA
[     8.267] (II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
[     8.267] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1072
[     8.267] (II) NVIDIA(0):       HSyncEnd, HTotal : 1168, 1376
[     8.267] (II) NVIDIA(0):       VRes, VSyncStart :  768,  769
[     8.267] (II) NVIDIA(0):       VSyncEnd, VTotal :  772,  808
[     8.267] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.267] (WW) NVIDIA(0):     Mode is rejected: HorizSync (68.7 kHz) out of range
[     8.267] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.267] (II) NVIDIA(0): 
[     8.267] (II) NVIDIA(0):   Validating Mode "1152x864":
[     8.267] (II) NVIDIA(0):     1152 x 864 @ 75 Hz
[     8.267] (II) NVIDIA(0):     Mode Source: VESA
[     8.267] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[     8.268] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
[     8.268] (II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
[     8.268] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[     8.268] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
[     8.268] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.268] (WW) NVIDIA(0):     Mode is rejected: HorizSync (67.5 kHz) out of range
[     8.268] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.268] (II) NVIDIA(0): 
[     8.268] (II) NVIDIA(0):   Validating Mode "1280x960":
[     8.268] (II) NVIDIA(0):     1280 x 960 @ 60 Hz
[     8.268] (II) NVIDIA(0):     Mode Source: VESA
[     8.268] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[     8.268] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1376
[     8.268] (II) NVIDIA(0):       HSyncEnd, HTotal : 1488, 1800
[     8.268] (II) NVIDIA(0):       VRes, VSyncStart :  960,  961
[     8.268] (II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1000
[     8.268] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.268] (WW) NVIDIA(0):     Mode is rejected: HorizSync (60.0 kHz) out of range
[     8.268] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.268] (II) NVIDIA(0): 
[     8.268] (II) NVIDIA(0):   Validating Mode "1280x960":
[     8.268] (II) NVIDIA(0):     1280 x 960 @ 85 Hz
[     8.268] (II) NVIDIA(0):     Mode Source: VESA
[     8.268] (II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
[     8.268] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
[     8.268] (II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
[     8.268] (II) NVIDIA(0):       VRes, VSyncStart :  960,  961
[     8.268] (II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1011
[     8.269] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.269] (WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
[     8.269] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.269] (II) NVIDIA(0): 
[     8.269] (II) NVIDIA(0):   Validating Mode "1280x1024":
[     8.269] (II) NVIDIA(0):     1280 x 1024 @ 60 Hz
[     8.269] (II) NVIDIA(0):     Mode Source: VESA
[     8.269] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[     8.269] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
[     8.269] (II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
[     8.269] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[     8.269] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
[     8.269] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.269] (WW) NVIDIA(0):     Mode is rejected: HorizSync (64.0 kHz) out of range
[     8.269] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.269] (II) NVIDIA(0): 
[     8.269] (II) NVIDIA(0):   Validating Mode "1280x1024":
[     8.269] (II) NVIDIA(0):     1280 x 1024 @ 75 Hz
[     8.269] (II) NVIDIA(0):     Mode Source: VESA
[     8.269] (II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
[     8.269] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
[     8.269] (II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
[     8.269] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[     8.269] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
[     8.269] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.269] (WW) NVIDIA(0):     Mode is rejected: HorizSync (80.0 kHz) out of range
[     8.269] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.269] (II) NVIDIA(0): 
[     8.269] (II) NVIDIA(0):   Validating Mode "1280x1024":
[     8.269] (II) NVIDIA(0):     1280 x 1024 @ 85 Hz
[     8.270] (II) NVIDIA(0):     Mode Source: VESA
[     8.270] (II) NVIDIA(0):       Pixel Clock      : 157.50 MHz
[     8.270] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
[     8.270] (II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
[     8.270] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[     8.270] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1072
[     8.270] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.270] (WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
[     8.270] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.270] (II) NVIDIA(0): 
[     8.270] (II) NVIDIA(0):   Validating Mode "1600x1200":
[     8.270] (II) NVIDIA(0):     1600 x 1200 @ 60 Hz
[     8.270] (II) NVIDIA(0):     Mode Source: VESA
[     8.270] (II) NVIDIA(0):       Pixel Clock      : 162.00 MHz
[     8.270] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[     8.270] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[     8.270] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[     8.270] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[     8.270] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.270] (WW) NVIDIA(0):     Mode is rejected: HorizSync (75.0 kHz) out of range
[     8.270] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.270] (II) NVIDIA(0): 
[     8.270] (II) NVIDIA(0):   Validating Mode "1600x1200":
[     8.270] (II) NVIDIA(0):     1600 x 1200 @ 65 Hz
[     8.270] (II) NVIDIA(0):     Mode Source: VESA
[     8.270] (II) NVIDIA(0):       Pixel Clock      : 175.50 MHz
[     8.270] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[     8.270] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[     8.270] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[     8.271] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[     8.271] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.271] (WW) NVIDIA(0):     Mode is rejected: HorizSync (81.2 kHz) out of range
[     8.271] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.271] (II) NVIDIA(0): 
[     8.271] (II) NVIDIA(0):   Validating Mode "1600x1200":
[     8.271] (II) NVIDIA(0):     1600 x 1200 @ 70 Hz
[     8.271] (II) NVIDIA(0):     Mode Source: VESA
[     8.271] (II) NVIDIA(0):       Pixel Clock      : 189.00 MHz
[     8.271] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[     8.271] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[     8.271] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[     8.271] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[     8.271] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.271] (WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
[     8.271] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.271] (II) NVIDIA(0): 
[     8.271] (II) NVIDIA(0):   Validating Mode "1600x1200":
[     8.271] (II) NVIDIA(0):     1600 x 1200 @ 75 Hz
[     8.271] (II) NVIDIA(0):     Mode Source: VESA
[     8.271] (II) NVIDIA(0):       Pixel Clock      : 202.50 MHz
[     8.271] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[     8.271] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[     8.271] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[     8.271] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[     8.271] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.271] (WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
[     8.271] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.271] (II) NVIDIA(0): 
[     8.271] (II) NVIDIA(0):   Validating Mode "1600x1200":
[     8.272] (II) NVIDIA(0):     1600 x 1200 @ 85 Hz
[     8.272] (II) NVIDIA(0):     Mode Source: VESA
[     8.272] (II) NVIDIA(0):       Pixel Clock      : 229.50 MHz
[     8.272] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[     8.272] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[     8.272] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[     8.272] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[     8.272] (II) NVIDIA(0):       H/V Polarity     : +/+
[     8.272] (WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
[     8.272] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.272] (II) NVIDIA(0): 
[     8.272] (II) NVIDIA(0):   Validating Mode "1792x1344":
[     8.272] (II) NVIDIA(0):     1792 x 1344 @ 60 Hz
[     8.272] (II) NVIDIA(0):     Mode Source: VESA
[     8.272] (II) NVIDIA(0):       Pixel Clock      : 204.80 MHz
[     8.272] (II) NVIDIA(0):       HRes, HSyncStart : 1792, 1920
[     8.272] (II) NVIDIA(0):       HSyncEnd, HTotal : 2120, 2448
[     8.272] (II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
[     8.272] (II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1394
[     8.272] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.272] (WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
[     8.272] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.272] (II) NVIDIA(0): 
[     8.272] (II) NVIDIA(0):   Validating Mode "1792x1344":
[     8.272] (II) NVIDIA(0):     1792 x 1344 @ 75 Hz
[     8.272] (II) NVIDIA(0):     Mode Source: VESA
[     8.272] (II) NVIDIA(0):       Pixel Clock      : 261.00 MHz
[     8.272] (II) NVIDIA(0):       HRes, HSyncStart : 1792, 1888
[     8.272] (II) NVIDIA(0):       HSyncEnd, HTotal : 2104, 2456
[     8.273] (II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
[     8.273] (II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1417
[     8.273] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.273] (WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
[     8.273] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.273] (II) NVIDIA(0): 
[     8.273] (II) NVIDIA(0):   Validating Mode "1856x1392":
[     8.273] (II) NVIDIA(0):     1856 x 1392 @ 60 Hz
[     8.273] (II) NVIDIA(0):     Mode Source: VESA
[     8.273] (II) NVIDIA(0):       Pixel Clock      : 218.30 MHz
[     8.273] (II) NVIDIA(0):       HRes, HSyncStart : 1856, 1952
[     8.273] (II) NVIDIA(0):       HSyncEnd, HTotal : 2176, 2528
[     8.273] (II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
[     8.273] (II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1439
[     8.273] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.273] (WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
[     8.273] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.273] (II) NVIDIA(0): 
[     8.273] (II) NVIDIA(0):   Validating Mode "1856x1392":
[     8.273] (II) NVIDIA(0):     1856 x 1392 @ 75 Hz
[     8.273] (II) NVIDIA(0):     Mode Source: VESA
[     8.273] (II) NVIDIA(0):       Pixel Clock      : 288.00 MHz
[     8.273] (II) NVIDIA(0):       HRes, HSyncStart : 1856, 1984
[     8.273] (II) NVIDIA(0):       HSyncEnd, HTotal : 2208, 2560
[     8.273] (II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
[     8.273] (II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1500
[     8.273] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.273] (WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
[     8.273] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.274] (II) NVIDIA(0): 
[     8.274] (II) NVIDIA(0):   Validating Mode "1920x1440":
[     8.274] (II) NVIDIA(0):     1920 x 1440 @ 60 Hz
[     8.274] (II) NVIDIA(0):     Mode Source: VESA
[     8.274] (II) NVIDIA(0):       Pixel Clock      : 234.00 MHz
[     8.274] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2048
[     8.274] (II) NVIDIA(0):       HSyncEnd, HTotal : 2256, 2600
[     8.274] (II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
[     8.274] (II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
[     8.274] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.274] (WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
[     8.274] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.274] (II) NVIDIA(0): 
[     8.274] (II) NVIDIA(0):   Validating Mode "1920x1440":
[     8.274] (II) NVIDIA(0):     1920 x 1440 @ 75 Hz
[     8.274] (II) NVIDIA(0):     Mode Source: VESA
[     8.274] (II) NVIDIA(0):       Pixel Clock      : 297.00 MHz
[     8.274] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2064
[     8.274] (II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2640
[     8.274] (II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
[     8.274] (II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
[     8.274] (II) NVIDIA(0):       H/V Polarity     : -/+
[     8.274] (WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
[     8.274] (WW) NVIDIA(0):     (28.000-55.000 kHz).
[     8.274] (II) NVIDIA(0): 
[     8.274] (II) NVIDIA(0): --- Done building ModePool for CRT-0 ---
[     8.274] (II) NVIDIA(0): 
[     8.275] (II) NVIDIA(0): 
[     8.275] (II) NVIDIA(0): --- Modes in ModePool for CRT-0 ---
[     8.275] (II) NVIDIA(0): "nvidia-auto-select" : 1024 x  768 @  60.0 Hz  (from: X Server, VESA)
[     8.275] (II) NVIDIA(0): "1360x768"           : 1360 x  768 @  60.0 Hz  (from: X Server)
[     8.275] (II) NVIDIA(0): "1360x768_60"        : 1360 x  768 @  60.0 Hz  (from: X Server)
[     8.275] (II) NVIDIA(0): "1360x768_60_0"      : 1360 x  768 @  59.8 Hz  (from: X Server)
[     8.275] (II) NVIDIA(0): "1152x864"           : 1152 x  864 @  60.0 Hz  (from: X Server)
[     8.275] (II) NVIDIA(0): "1152x864_60"        : 1152 x  864 @  60.0 Hz  (from: X Server)
[     8.275] (II) NVIDIA(0): "1024x768"           : 1024 x  768 @  60.0 Hz  (from: X Server, VESA)
[     8.275] (II) NVIDIA(0): "1024x768_60"        : 1024 x  768 @  60.0 Hz  (from: X Server, VESA)
[     8.275] (II) NVIDIA(0): "800x600"            :  800 x  600 @  72.2 Hz  (from: X Server, VESA)
[     8.275] (II) NVIDIA(0): "800x600_72"         :  800 x  600 @  72.2 Hz  (from: X Server, VESA)
[     8.275] (II) NVIDIA(0): "800x600_60"         :  800 x  600 @  60.3 Hz  (from: X Server, VESA)
[     8.275] (II) NVIDIA(0): "800x600_56"         :  800 x  600 @  56.2 Hz  (from: X Server, VESA)
[     8.275] (II) NVIDIA(0): "680x384"            :  680 x  384 @  60.0 Hz DoubleScan  (from: X Server)
[     8.275] (II) NVIDIA(0): "680x384d60"         :  680 x  384 @  60.0 Hz DoubleScan  (from: X Server)
[     8.275] (II) NVIDIA(0): "680x384d60_0"       :  680 x  384 @  59.8 Hz DoubleScan  (from: X Server)
[     8.275] (II) NVIDIA(0): "640x480"            :  640 x  480 @  59.9 Hz  (from: X Server, VESA)
[     8.275] (II) NVIDIA(0): "640x480_60"         :  640 x  480 @  59.9 Hz  (from: X Server, VESA)
[     8.275] (II) NVIDIA(0): "512x384"            :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
[     8.275] (II) NVIDIA(0): "512x384d60"         :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
[     8.275] (II) NVIDIA(0): "400x300"            :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
[     8.275] (II) NVIDIA(0): "400x300d72"         :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
[     8.276] (II) NVIDIA(0): "320x240"            :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
[     8.276] (II) NVIDIA(0): "320x240d60"         :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
[     8.276] (II) NVIDIA(0): --- End of ModePool for CRT-0: ---
[     8.276] (II) NVIDIA(0): 
[     8.276] (II) NVIDIA(0): Assigned Display Device: CRT-0
[     8.276] (==) NVIDIA(0): 
[     8.276] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     8.276] (==) NVIDIA(0):     will be used as the requested mode.
[     8.276] (==) NVIDIA(0): 
[     8.276] (II) NVIDIA(0): Validated modes:
[     8.276] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[     8.277] (II) NVIDIA(0): 
[     8.277] (II) NVIDIA(0): Implicitly adding the following modes to X Screen 0 (these
[     8.277] (II) NVIDIA(0):     will be available via XRandR and XF86VidMode):
[     8.277] (II) NVIDIA(0): 
[     8.277] (II) NVIDIA(0): "800x600"      :  800 x  600 @  72.2 Hz 
[     8.277] (II) NVIDIA(0): "800x600_60"   :  800 x  600 @  60.3 Hz 
[     8.277] (II) NVIDIA(0): "800x600_56"   :  800 x  600 @  56.2 Hz 
[     8.277] (II) NVIDIA(0): "680x384"      :  680 x  384 @  60.0 Hz DoubleScan 
[     8.277] (II) NVIDIA(0): "680x384d60_0" :  680 x  384 @  59.8 Hz DoubleScan 
[     8.277] (II) NVIDIA(0): "640x480"      :  640 x  480 @  59.9 Hz 
[     8.277] (II) NVIDIA(0): "512x384"      :  512 x  384 @  60.0 Hz DoubleScan 
[     8.277] (II) NVIDIA(0): "400x300"      :  400 x  300 @  72.2 Hz DoubleScan 
[     8.277] (II) NVIDIA(0): "320x240"      :  320 x  240 @  60.1 Hz DoubleScan 
[     8.277] (II) NVIDIA(0): 
[     8.311] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[     8.311] (WW) NVIDIA(0):     from CRT-0's EDID.
[     8.311] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[     8.311] (II) UnloadModule: "nouveau"
[     8.311] (II) Unloading nouveau
[     8.311] (II) UnloadModule: "vesa"
[     8.311] (II) Unloading vesa
[     8.311] (II) UnloadModule: "fbdev"
[     8.311] (II) Unloading fbdev
[     8.311] (II) UnloadModule: "fbdevhw"
[     8.311] (II) Unloading fbdevhw
[     8.311] (--) Depth 24 pixmap format is 32 bpp
[     8.312] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[     8.322] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[     8.357] (II) Loading extension NV-GLX
[     8.391] (==) NVIDIA(0): Disabling shared memory pixmaps
[     8.391] (==) NVIDIA(0): Backing store disabled
[     8.391] (==) NVIDIA(0): Silken mouse enabled
[     8.392] (==) NVIDIA(0): DPMS enabled
[     8.392] (II) Loading extension NV-CONTROL
[     8.393] (II) Loading extension XINERAMA
[     8.393] (II) Loading sub module "dri2"
[     8.393] (II) LoadModule: "dri2"
[     8.394] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     8.394] (II) Module dri2: vendor="X.Org Foundation"
[     8.394]     compiled for 1.10.4, module version = 1.2.0
[     8.394]     ABI class: X.Org Server Extension, version 5.0
[     8.394] (II) NVIDIA(0): [DRI2] Setup complete
[     8.394] (==) RandR enabled
[     8.394] (II) Initializing built-in extension Generic Event Extension
[     8.394] (II) Initializing built-in extension SHAPE
[     8.394] (II) Initializing built-in extension MIT-SHM
[     8.395] (II) Initializing built-in extension XInputExtension
[     8.395] (II) Initializing built-in extension XTEST
[     8.395] (II) Initializing built-in extension BIG-REQUESTS
[     8.395] (II) Initializing built-in extension SYNC
[     8.395] (II) Initializing built-in extension XKEYBOARD
[     8.395] (II) Initializing built-in extension XC-MISC
[     8.395] (II) Initializing built-in extension SECURITY
[     8.395] (II) Initializing built-in extension XINERAMA
[     8.395] (II) Initializing built-in extension XFIXES
[     8.395] (II) Initializing built-in extension RENDER
[     8.395] (II) Initializing built-in extension RANDR
[     8.395] (II) Initializing built-in extension COMPOSITE
[     8.395] (II) Initializing built-in extension DAMAGE
[     8.395] (II) Initializing built-in extension GESTURE
[     8.401] (II) Initializing extension GLX
[     8.456] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     8.483] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     8.483] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     8.483] (II) LoadModule: "evdev"
[     8.484] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.486] (II) Module evdev: vendor="X.Org Foundation"
[     8.486]     compiled for 1.10.2, module version = 2.6.0
[     8.486]     Module class: X.Org XInput Driver
[     8.486]     ABI class: X.Org XInput driver, version 12.3
[     8.486] (II) Using input driver 'evdev' for 'Power Button'
[     8.486] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.486] (**) Power Button: always reports core events
[     8.486] (**) Power Button: Device: "/dev/input/event1"
[     8.487] (--) Power Button: Found keys
[     8.487] (II) Power Button: Configuring as keyboard
[     8.487] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     8.487] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[     8.487] (**) Option "xkb_rules" "evdev"
[     8.487] (**) Option "xkb_model" "pc105"
[     8.487] (**) Option "xkb_layout" "no"
[     8.495] (II) XKB: reuse xkmfile /var/lib/xkb/server-5F8E417E6ED2D276BE32A8CA0E3DB916C21A8CA2.xkm
[     8.502] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     8.502] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     8.502] (II) Using input driver 'evdev' for 'Power Button'
[     8.502] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.503] (**) Power Button: always reports core events
[     8.503] (**) Power Button: Device: "/dev/input/event0"
[     8.503] (--) Power Button: Found keys
[     8.503] (II) Power Button: Configuring as keyboard
[     8.503] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     8.503] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[     8.503] (**) Option "xkb_rules" "evdev"
[     8.503] (**) Option "xkb_model" "pc105"
[     8.503] (**) Option "xkb_layout" "no"
[     8.512] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event6)
[     8.512] (II) No input driver/identifier specified (ignoring)
[     8.513] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event7)
[     8.513] (II) No input driver/identifier specified (ignoring)
[     8.514] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event8)
[     8.514] (II) No input driver/identifier specified (ignoring)
[     8.515] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event9)
[     8.515] (II) No input driver/identifier specified (ignoring)
[     8.519] (II) config/udev: Adding input device Logitech USB Gaming Mouse (/dev/input/event2)
[     8.519] (**) Logitech USB Gaming Mouse: Applying InputClass "evdev pointer catchall"
[     8.519] (II) Using input driver 'evdev' for 'Logitech USB Gaming Mouse'
[     8.519] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.519] (**) Logitech USB Gaming Mouse: always reports core events
[     8.519] (**) Logitech USB Gaming Mouse: Device: "/dev/input/event2"
[     8.519] (--) Logitech USB Gaming Mouse: Found 20 mouse buttons
[     8.519] (--) Logitech USB Gaming Mouse: Found scroll wheel(s)
[     8.519] (--) Logitech USB Gaming Mouse: Found relative axes
[     8.519] (--) Logitech USB Gaming Mouse: Found x and y relative axes
[     8.520] (II) Logitech USB Gaming Mouse: Configuring as mouse
[     8.520] (II) Logitech USB Gaming Mouse: Adding scrollwheel support
[     8.520] (**) Logitech USB Gaming Mouse: YAxisMapping: buttons 4 and 5
[     8.520] (**) Logitech USB Gaming Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     8.520] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input2/event2"
[     8.520] (II) XINPUT: Adding extended input device "Logitech USB Gaming Mouse" (type: MOUSE)
[     8.520] (II) Logitech USB Gaming Mouse: initialized for relative axes.
[     8.520] (**) Logitech USB Gaming Mouse: (accel) keeping acceleration scheme 1
[     8.520] (**) Logitech USB Gaming Mouse: (accel) acceleration profile 0
[     8.521] (**) Logitech USB Gaming Mouse: (accel) acceleration factor: 2.000
[     8.521] (**) Logitech USB Gaming Mouse: (accel) acceleration threshold: 4
[     8.521] (II) config/udev: Adding input device Logitech USB Gaming Mouse (/dev/input/mouse0)
[     8.522] (II) No input driver/identifier specified (ignoring)
[     8.524] (II) config/udev: Adding input device BTC USB Multimedia Keyboard (/dev/input/event3)
[     8.524] (**) BTC USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[     8.524] (II) Using input driver 'evdev' for 'BTC USB Multimedia Keyboard'
[     8.524] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.524] (**) BTC USB Multimedia Keyboard: always reports core events
[     8.524] (**) BTC USB Multimedia Keyboard: Device: "/dev/input/event3"
[     8.525] (--) BTC USB Multimedia Keyboard: Found keys
[     8.525] (II) BTC USB Multimedia Keyboard: Configuring as keyboard
[     8.525] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input3/event3"
[     8.525] (II) XINPUT: Adding extended input device "BTC USB Multimedia Keyboard" (type: KEYBOARD)
[     8.525] (**) Option "xkb_rules" "evdev"
[     8.525] (**) Option "xkb_model" "pc105"
[     8.525] (**) Option "xkb_layout" "no"
[     8.527] (II) config/udev: Adding input device BTC USB Multimedia Keyboard (/dev/input/event4)
[     8.527] (**) BTC USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[     8.527] (II) Using input driver 'evdev' for 'BTC USB Multimedia Keyboard'
[     8.527] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.527] (**) BTC USB Multimedia Keyboard: always reports core events
[     8.527] (**) BTC USB Multimedia Keyboard: Device: "/dev/input/event4"
[     8.527] (--) BTC USB Multimedia Keyboard: Found keys
[     8.528] (II) BTC USB Multimedia Keyboard: Configuring as keyboard
[     8.528] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input4/event4"
[     8.528] (II) XINPUT: Adding extended input device "BTC USB Multimedia Keyboard" (type: KEYBOARD)
[     8.528] (**) Option "xkb_rules" "evdev"
[     8.528] (**) Option "xkb_model" "pc105"
[     8.528] (**) Option "xkb_layout" "no"
[     8.534] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event5)
[     8.534] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
[     8.534] (II) Using input driver 'evdev' for 'Logitech Logitech BT Mini-Receiver'
[     8.534] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.534] (**) Logitech Logitech BT Mini-Receiver: always reports core events
[     8.535] (**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event5"
[     8.535] (--) Logitech Logitech BT Mini-Receiver: Found keys
[     8.535] (II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
[     8.535] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.2/1-5.2.2/1-5.2.2:1.0/input/input5/event5"
[     8.535] (II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
[     8.535] (**) Option "xkb_rules" "evdev"
[     8.535] (**) Option "xkb_model" "pc105"
[     8.535] (**) Option "xkb_layout" "no"
[     8.538] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event10)
[     8.538] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev pointer catchall"
[     8.538] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
[     8.538] (II) Using input driver 'evdev' for 'Logitech Logitech BT Mini-Receiver'
[     8.538] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.538] (**) Logitech Logitech BT Mini-Receiver: always reports core events
[     8.538] (**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event10"
[     8.538] (--) Logitech Logitech BT Mini-Receiver: Found 16 mouse buttons
[     8.538] (--) Logitech Logitech BT Mini-Receiver: Found scroll wheel(s)
[     8.538] (--) Logitech Logitech BT Mini-Receiver: Found relative axes
[     8.538] (--) Logitech Logitech BT Mini-Receiver: Found x and y relative axes
[     8.538] (--) Logitech Logitech BT Mini-Receiver: Found absolute axes
[     8.538] (II) evdev-grail: failed to open grail, no gesture support
[     8.539] (--) Logitech Logitech BT Mini-Receiver: Found keys
[     8.539] (II) Logitech Logitech BT Mini-Receiver: Configuring as mouse
[     8.539] (II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
[     8.539] (II) Logitech Logitech BT Mini-Receiver: Adding scrollwheel support
[     8.539] (**) Logitech Logitech BT Mini-Receiver: YAxisMapping: buttons 4 and 5
[     8.539] (**) Logitech Logitech BT Mini-Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     8.539] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.2/1-5.2.3/1-5.2.3:1.0/input/input10/event10"
[     8.539] (II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
[     8.539] (**) Option "xkb_rules" "evdev"
[     8.539] (**) Option "xkb_model" "pc105"
[     8.539] (**) Option "xkb_layout" "no"
[     8.540] (II) Logitech Logitech BT Mini-Receiver: initialized for relative axes.
[     8.540] (WW) Logitech Logitech BT Mini-Receiver: ignoring absolute axes.
[     8.540] (**) Logitech Logitech BT Mini-Receiver: (accel) keeping acceleration scheme 1
[     8.540] (**) Logitech Logitech BT Mini-Receiver: (accel) acceleration profile 0
[     8.540] (**) Logitech Logitech BT Mini-Receiver: (accel) acceleration factor: 2.000
[     8.540] (**) Logitech Logitech BT Mini-Receiver: (accel) acceleration threshold: 4
[     8.541] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/mouse1)
[     8.541] (II) No input driver/identifier specified (ignoring)
[    14.796] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[   103.664] (II) config/udev: Adding input device Logitech diNovo Edge (/dev/input/mouse2)
[   103.664] (II) No input driver/identifier specified (ignoring)
[   103.665] (II) config/udev: Adding input device Logitech diNovo Edge (/dev/input/event11)
[   103.665] (**) Logitech diNovo Edge: Applying InputClass "evdev pointer catchall"
[   103.665] (**) Logitech diNovo Edge: Applying InputClass "evdev keyboard catchall"
[   103.665] (II) Using input driver 'evdev' for 'Logitech diNovo Edge'
[   103.665] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   103.665] (**) Logitech diNovo Edge: always reports core events
[   103.666] (**) Logitech diNovo Edge: Device: "/dev/input/event11"
[   103.666] (--) Logitech diNovo Edge: Found 20 mouse buttons
[   103.666] (--) Logitech diNovo Edge: Found scroll wheel(s)
[   103.666] (--) Logitech diNovo Edge: Found relative axes
[   103.666] (--) Logitech diNovo Edge: Found x and y relative axes
[   103.666] (--) Logitech diNovo Edge: Found absolute axes
[   103.666] (II) evdev-grail: failed to open grail, no gesture support
[   103.666] (--) Logitech diNovo Edge: Found keys
[   103.666] (II) Logitech diNovo Edge: Configuring as mouse
[   103.666] (II) Logitech diNovo Edge: Configuring as keyboard
[   103.666] (II) Logitech diNovo Edge: Adding scrollwheel support
[   103.666] (**) Logitech diNovo Edge: YAxisMapping: buttons 4 and 5
[   103.666] (**) Logitech diNovo Edge: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   103.666] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.2/1-5.2.1/1-5.2.1:1.0/bluetooth/hci0/hci0:11/input11/event11"
[   103.666] (II) XINPUT: Adding extended input device "Logitech diNovo Edge" (type: KEYBOARD)
[   103.666] (**) Option "xkb_rules" "evdev"
[   103.666] (**) Option "xkb_model" "pc105"
[   103.666] (**) Option "xkb_layout" "no"
[   103.667] (II) Logitech diNovo Edge: initialized for relative axes.
[   103.667] (WW) Logitech diNovo Edge: ignoring absolute axes.
[   103.668] (**) Logitech diNovo Edge: (accel) keeping acceleration scheme 1
[   103.668] (**) Logitech diNovo Edge: (accel) acceleration profile 0
[   103.668] (**) Logitech diNovo Edge: (accel) acceleration factor: 2.000
[   103.668] (**) Logitech diNovo Edge: (accel) acceleration threshold: 4
[   271.007] (II) XKB: reuse xkmfile /var/lib/xkb/server-5F8E417E6ED2D276BE32A8CA0E3DB916C21A8CA2.xkm
```

/bArrin

---

### Post by bArrin_st on 2011-10-24
After even more searching and reading and tearing at my hair, I have solved the resolution issue! :D

I stumbled across an article in the [www.ypas.net](www.ypas.net) blog ([http://www.ypass.net/blog/2009/07/dvi-to-hdmi-overscan-screen-edge-cutoff-on-an-hdtv/](http://www.ypass.net/blog/2009/07/dvi-to-hdmi-overscan-screen-edge-cutoff-on-an-hdtv/)) and from there I reached the Modeline Generator at [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

I also dug out the manual for my TV, and entered the values from the manual in the generator and created a modeline for my xorg.conf.

My xorg.conf currentlry looks like this:
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 280.13  (buildd@yellow)  Fri Aug  5 12:31:28 UTC 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DFP-1"
    HorizSync       30.0 - 61.0
    VertRefresh     59.0 - 76.0
    Option         "DPMS"
    Modeline "1360x768@60" 84.52 1360 1392 1712 1744 768 783 791 807
    Option       "ExactModeTimingsDVI" "TRUE"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
    Option       "UseEDID" "FALSE"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    Modes       "1360x768@60"
    EndSubSection
EndSection
```

and when I restarted X i finally got 1360x768 on my HDMI-connection! :D

Now I'm off to actually begin using my HTPC with Ubuntu installed!

Thank you BicyclerBoy for trying to help me, and if you feel I could achieve this result in an other, possibly better, way - please tell me so =)

/bArrin

---

### Post by BicyclerBoy on 2011-10-24
Good for you..

If the X server does not start, you can always just delete/rename the xorg.conf file from console login <ctrl>+<alt>+<f1>.

You don't really need your modeline because the nVidia driver & Xorg have internal video modes available..
[     8.275] (II) NVIDIA(0): "1360x768"           : 1360 x  768 @  60.0 Hz  (from: X Server)
[     8.275] (II) NVIDIA(0): "1360x768_60"        : 1360 x  768 @  60.0 Hz  (from: X Server)
[     8.275] (II) NVIDIA(0): "1360x768_60_0"      : 1360 x  768 @  59.8 Hz  (from: X Server)

You just need to reference the named video mode in your xorg.conf
I would use "1360x768_60_0" as this is the correct TV video mode.

The cause of the problem is EDID read failure (corrupt header).
The root cause is unknown..cable or s/w ..

---

### Post by jintermeister on 2012-07-03
Hi, I just wanted to chime in here and say that I had the exact same problem as you did, but with a GeForce 9500GT card and standard 1280x1024 LCD monitor(s) connected by DVI. I had the invalid EDID and the same resultant xorg.conf file. Like you I was stuck with 640x480 and couldn't get anything higher without using VESA driver. I couldn't even use nouveau because to boot at all, you have to set 'nomodeset' which basically disables the driver. Me thinks Nvidia issue as my dual boot with Windows works fine, and VESA gets the resolution right as well.

Thanks for your posts about your success, as I copied your solution and it worked very well for me. I used the Modeline Generator you suggested and pretty much copied the rest of your xorg.conf file for monitor, device, screen. After I finally got the right resolution on one monitor, I configured for twinview and got both monitors working.

Then something interesting happened. I had both monitors in TwinView, but with wrong resolution and refresh. So I went into nvidia-settings and clicked "Detect Monitors" and for the first time, it actually worked!!! After that it seemed to auto-detect the available resolution and refresh rates (the standard rates that BicyclerBoy referred to). I was able to save it to the xorg.conf file and now I'm good even after reboot.

The interesting thing is that the standard rates were NOT available and monitor detection failed until forcing a Modeline and getting things halfway there. In my log file it had just thrown out standard modes as un-applicable.

So now I'm happy, and thought I'd share my story in case others have similar issues. BTW, I had installed Ubuntu Studio 12.04 x64. I'll reply back with my xorg.conf file in case it helps anyone (I don't have it on this computer).

---


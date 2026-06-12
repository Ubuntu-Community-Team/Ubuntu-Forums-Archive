---
title: "Can't set resolution to 1680x1050"
date: 2011-01-16
forum: Multimedia Software
---

### Post by dchalhub' on 2011-01-16
Hello,

The native resolution from my LCD monitor is 1680x1050, but the list of  "NVIDIA X Server Settings" only allow me to set it to maximum 1360x768.  The monitor is conected via VGA cable and it is recognized as CRT-0.  When I run the 'xrandr' command from terminal, it shows:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1680 x 1050
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   512x384        57.0  
   400x300        58.0  
   320x240        59.0

In Windows the monitor works fine with 1680x1050 and my video card is Geforce 9600GT

Please help me...

---

### Post by tjones00 on 2011-01-16
Post your /var/log/Xorg.0.log and /etc/X11/xorg.conf

---

### Post by dchalhub' on 2011-01-16
> **tjones00 said:**
> Post your /var/log/Xorg.0.log and /etc/X11/xorg.conf

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
     Subsection "Display"
         Modes      "1680x1050"
     EndSubSection
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection




[    20.136] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    20.136] X Protocol Version 11, Revision 0
[    20.136] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    20.136] Current Operating System: Linux Daniel 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64
[    20.137] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=848374c1-93d2-43b7-91a1-5bbd08e035d8 ro quiet splash
[    20.137] Build Date: 23 November 2010  11:54:56PM
[    20.137] xorg-server 2:1.9.0-0ubuntu7.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    20.137] Current version of pixman: 0.18.4
[    20.137]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    20.137] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.137] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 17 00:50:46 2011
[    20.137] (==) Using config file: "/etc/X11/xorg.conf"
[    20.137] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.137] (==) ServerLayout "Layout0"
[    20.137] (**) |-->Screen "Screen0" (0)
[    20.137] (**) |   |-->Monitor "Monitor0"
[    20.137] (**) |   |-->Device "Device0"
[    20.137] (**) |-->Input Device "Keyboard0"
[    20.137] (**) |-->Input Device "Mouse0"
[    20.137] (**) Option "Xinerama" "0"
[    20.137] (==) Automatically adding devices
[    20.137] (==) Automatically enabling devices
[    20.137] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.137]     Entry deleted from font path.
[    20.137] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    20.137] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.137] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    20.137] (WW) Disabling Keyboard0
[    20.137] (WW) Disabling Mouse0
[    20.137] (II) Loader magic: 0x7d17a0
[    20.137] (II) Module ABI versions:
[    20.137]     X.Org ANSI C Emulation: 0.4
[    20.137]     X.Org Video Driver: 8.0
[    20.137]     X.Org XInput driver : 11.0
[    20.137]     X.Org Server Extension : 4.0
[    20.138] (--) PCI:*(0:1:0:0) 10de:0622:19da:4057 rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
[    20.138] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    20.138] (II) LoadModule: "extmod"
[    20.158] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.159] (II) Module extmod: vendor="X.Org Foundation"
[    20.159]     compiled for 1.9.0, module version = 1.0.0
[    20.159]     Module class: X.Org Server Extension
[    20.159]     ABI class: X.Org Server Extension, version 4.0
[    20.159] (II) Loading extension MIT-SCREEN-SAVER
[    20.159] (II) Loading extension XFree86-VidModeExtension
[    20.159] (II) Loading extension XFree86-DGA
[    20.159] (II) Loading extension DPMS
[    20.159] (II) Loading extension XVideo
[    20.159] (II) Loading extension XVideo-MotionCompensation
[    20.159] (II) Loading extension X-Resource
[    20.159] (II) LoadModule: "dbe"
[    20.159] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.159] (II) Module dbe: vendor="X.Org Foundation"
[    20.159]     compiled for 1.9.0, module version = 1.0.0
[    20.159]     Module class: X.Org Server Extension
[    20.159]     ABI class: X.Org Server Extension, version 4.0
[    20.159] (II) Loading extension DOUBLE-BUFFER
[    20.159] (II) LoadModule: "glx"
[    20.159] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    20.166] (II) Module glx: vendor="NVIDIA Corporation"
[    20.166]     compiled for 4.0.2, module version = 1.0.0
[    20.166]     Module class: X.Org Server Extension
[    20.166] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
[    20.166] (II) Loading extension GLX
[    20.166] (II) LoadModule: "record"
[    20.166] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    20.167] (II) Module record: vendor="X.Org Foundation"
[    20.167]     compiled for 1.9.0, module version = 1.13.0
[    20.167]     Module class: X.Org Server Extension
[    20.167]     ABI class: X.Org Server Extension, version 4.0
[    20.167] (II) Loading extension RECORD
[    20.167] (II) LoadModule: "dri"
[    20.167] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    20.167] (II) Module dri: vendor="X.Org Foundation"
[    20.167]     compiled for 1.9.0, module version = 1.0.0
[    20.167]     ABI class: X.Org Server Extension, version 4.0
[    20.167] (II) Loading extension XFree86-DRI
[    20.167] (II) LoadModule: "dri2"
[    20.167] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.167] (II) Module dri2: vendor="X.Org Foundation"
[    20.167]     compiled for 1.9.0, module version = 1.2.0
[    20.167]     ABI class: X.Org Server Extension, version 4.0
[    20.167] (II) Loading extension DRI2
[    20.167] (II) LoadModule: "nvidia"
[    20.167] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    20.168] (II) Module nvidia: vendor="NVIDIA Corporation"
[    20.168]     compiled for 4.0.2, module version = 1.0.0
[    20.168]     Module class: X.Org Video Driver
[    20.168] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
[    20.168] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    20.168] (++) using VT number 7

[    20.169] (II) Loading sub module "fb"
[    20.169] (II) LoadModule: "fb"
[    20.169] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.169] (II) Module fb: vendor="X.Org Foundation"
[    20.169]     compiled for 1.9.0, module version = 1.0.0
[    20.169]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.169] (II) Loading sub module "wfb"
[    20.169] (II) LoadModule: "wfb"
[    20.169] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    20.169] (II) Module wfb: vendor="X.Org Foundation"
[    20.169]     compiled for 1.9.0, module version = 1.0.0
[    20.169]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.169] (II) Loading sub module "ramdac"
[    20.169] (II) LoadModule: "ramdac"
[    20.169] (II) Module "ramdac" already built-in
[    20.169] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    20.169] (==) NVIDIA(0): RGB weight 888
[    20.169] (==) NVIDIA(0): Default visual is TrueColor
[    20.169] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    20.169] (**) NVIDIA(0): Option "TwinView" "0"
[    20.169] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
[    20.169] (**) NVIDIA(0): Enabling RENDER acceleration
[    20.170] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    20.170] (II) NVIDIA(0):     enabled.
[    21.542] (WW) NVIDIA(GPU-0): The EDID read for display device CRT-0 is invalid:
[    21.570] (WW) NVIDIA(GPU-0):     unrecognized EDID Header.
[    21.571] (II) NVIDIA(0): NVIDIA GPU GeForce 9600 GT (G94) at PCI:1:0:0 (GPU-0)
[    21.571] (--) NVIDIA(0): Memory: 1048576 kBytes
[    21.571] (--) NVIDIA(0): VideoBIOS: 62.94.38.00.00
[    21.571] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    21.571] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    21.571] (--) NVIDIA(0): Connected display device(s) on GeForce 9600 GT at PCI:1:0:0
[    21.571] (--) NVIDIA(0):     CRT-0
[    21.571] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    21.649] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    21.649] (==) NVIDIA(0): 
[    21.649] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    21.649] (==) NVIDIA(0):     will be used as the requested mode.
[    21.649] (==) NVIDIA(0): 
[    21.649] (II) NVIDIA(0): Validated modes:
[    21.649] (II) NVIDIA(0):     "nvidia-auto-select"
[    21.649] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[    21.673] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[    21.673] (WW) NVIDIA(0):     from CRT-0's EDID.
[    21.673] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    21.673] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    21.673] (--) Depth 24 pixmap format is 32 bpp
[    21.673] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    21.674] (II) NVIDIA(0): Initialized GPU GART.
[    21.678] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    21.767] (II) Loading extension NV-GLX
[    21.786] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    21.787] (==) NVIDIA(0): Disabling shared memory pixmaps
[    21.787] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    21.787] (==) NVIDIA(0): Backing store disabled
[    21.788] (==) NVIDIA(0): Silken mouse enabled
[    21.792] (**) NVIDIA(0): DPMS enabled
[    21.792] (II) Loading extension NV-CONTROL
[    21.792] (II) Loading extension XINERAMA
[    21.792] (II) Loading sub module "dri2"
[    21.792] (II) LoadModule: "dri2"
[    21.792] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.792] (II) NVIDIA(0): [DRI2] Setup complete
[    21.792] (==) RandR enabled
[    21.792] (II) Initializing built-in extension Generic Event Extension
[    21.792] (II) Initializing built-in extension SHAPE
[    21.792] (II) Initializing built-in extension MIT-SHM
[    21.792] (II) Initializing built-in extension XInputExtension
[    21.792] (II) Initializing built-in extension XTEST
[    21.792] (II) Initializing built-in extension BIG-REQUESTS
[    21.792] (II) Initializing built-in extension SYNC
[    21.792] (II) Initializing built-in extension XKEYBOARD
[    21.792] (II) Initializing built-in extension XC-MISC
[    21.792] (II) Initializing built-in extension SECURITY
[    21.792] (II) Initializing built-in extension XINERAMA
[    21.792] (II) Initializing built-in extension XFIXES
[    21.792] (II) Initializing built-in extension RENDER
[    21.792] (II) Initializing built-in extension RANDR
[    21.792] (II) Initializing built-in extension COMPOSITE
[    21.793] (II) Initializing built-in extension DAMAGE
[    21.793] (II) Initializing built-in extension GESTURE
[    21.794] (II) Initializing extension GLX
[    21.814] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.820] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    21.820] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.820] (II) LoadModule: "evdev"
[    21.820] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.820] (II) Module evdev: vendor="X.Org Foundation"
[    21.820]     compiled for 1.9.0, module version = 2.3.2
[    21.820]     Module class: X.Org XInput Driver
[    21.820]     ABI class: X.Org XInput driver, version 11.0
[    21.820] (**) Power Button: always reports core events
[    21.820] (**) Power Button: Device: "/dev/input/event1"
[    21.892] (II) Power Button: Found keys
[    21.892] (II) Power Button: Configuring as keyboard
[    21.892] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    21.892] (**) Option "xkb_rules" "evdev"
[    21.892] (**) Option "xkb_model" "abnt2"
[    21.892] (**) Option "xkb_layout" "br"
[    21.894] (II) XKB: reuse xkmfile /var/lib/xkb/server-20278E27F1DC9FDDFD591DABFB86C7D7989CFCCF.xkm
[    21.895] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    21.895] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.895] (**) Power Button: always reports core events
[    21.895] (**) Power Button: Device: "/dev/input/event0"
[    21.972] (II) Power Button: Found keys
[    21.972] (II) Power Button: Configuring as keyboard
[    21.972] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    21.972] (**) Option "xkb_rules" "evdev"
[    21.972] (**) Option "xkb_model" "abnt2"
[    21.972] (**) Option "xkb_layout" "br"
[    21.975] (II) config/udev: Adding input device A4Tech USB Mouse (/dev/input/event2)
[    21.975] (**) A4Tech USB Mouse: Applying InputClass "evdev pointer catchall"
[    21.975] (**) A4Tech USB Mouse: always reports core events
[    21.975] (**) A4Tech USB Mouse: Device: "/dev/input/event2"
[    22.052] (II) A4Tech USB Mouse: Found 20 mouse buttons
[    22.052] (II) A4Tech USB Mouse: Found scroll wheel(s)
[    22.052] (II) A4Tech USB Mouse: Found relative axes
[    22.052] (II) A4Tech USB Mouse: Found x and y relative axes
[    22.052] (II) A4Tech USB Mouse: Configuring as mouse
[    22.052] (**) A4Tech USB Mouse: YAxisMapping: buttons 4 and 5
[    22.052] (**) A4Tech USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.052] (II) XINPUT: Adding extended input device "A4Tech USB Mouse" (type: MOUSE)
[    22.052] (II) A4Tech USB Mouse: initialized for relative axes.
[    22.052] (II) config/udev: Adding input device A4Tech USB Mouse (/dev/input/mouse0)
[    22.052] (II) No input driver/identifier specified (ignoring)
[    22.053] (II) config/udev: Adding input device LITEON Technology USB Keyboard (/dev/input/event3)
[    22.053] (**) LITEON Technology USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    22.053] (**) LITEON Technology USB Keyboard: always reports core events
[    22.053] (**) LITEON Technology USB Keyboard: Device: "/dev/input/event3"
[    22.133] (II) LITEON Technology USB Keyboard: Found keys
[    22.133] (II) LITEON Technology USB Keyboard: Configuring as keyboard
[    22.133] (II) XINPUT: Adding extended input device "LITEON Technology USB Keyboard" (type: KEYBOARD)
[    22.133] (**) Option "xkb_rules" "evdev"
[    22.133] (**) Option "xkb_model" "abnt2"
[    22.133] (**) Option "xkb_layout" "br"
[    96.803] (II) NVIDIA(0): Setting mode "CRT-0:1360x768@1360x768+0+0"
[   367.079] (II) NVIDIA(0): Setting mode "800x600_56"
[   371.754] (II) NVIDIA(0): Setting mode "CRT-0:1360x768@1360x768+0+0"

---

### Post by BicyclerBoy on 2011-01-16
More EDID problems...

What has gone so badly wrong with a simple scheme that worked for years ?

---

### Post by tjones00 on 2011-01-16
And shabang! another EDID error with nvidia. Edit: I'm noticing it's the 64b kernels.

[    21.542] (WW) NVIDIA(GPU-0): The EDID read for display device CRT-0 is invalid:
[    21.570] (WW) NVIDIA(GPU-0):     unrecognized EDID Header.

Your xorg.conf is fine.

I see you probably installed the nvidia drivers via System > Administration > Additional Drivers.  Nvidia 260.19.06.

So that means you're not running some apparently "unstable" driver and they were installed "properly". 

I really dunno who's at fault here but alot of this has been going on recently.

This is interesting.

[    20.136] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    20.136] Current Operating System: Linux Daniel 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64

So you're running a 64b kernel.

Since it failed to gather an EDID we don't have any viable modelines to use in linux from your Xorg.0.log.

You said you have a windows os and the resolution works fine in it.

I suggest you get a viable modeline or EDID.bin from windows.

You can use the EDID.bin file gathered in windows using various 3rd party tools the only one I know off the top of my head is called PowerStrip. Transfer that file to your linux install and use it in your xorg.conf with the CustomEDID option.

For a modeline you'd use a 3rd party tool in windows again and set one up in the Monitor section of your xorg.conf. 

[http://www.x.org/wiki/FAQVideoModes](http://www.x.org/wiki/FAQVideoModes) 

If you're feeling adventurous you could use some of the old school methods for determining a modeline.

[http://en.gentoo-wiki.com/wiki/X.Org/Modelines](http://en.gentoo-wiki.com/wiki/X.Org/Modelines)
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

---

### Post by BicyclerBoy on 2011-01-16
You do not need to create modelines except for exceptional circumstances.

All required timings/modelines for DFP (LCD etc) are created by nvidia driver internally.
Most CRTs can be driven from default internal modes .

I have had to use this modeline calculator for CRT HDTV .
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

The OP needs to generate an xorg.conf using the nvidia-settings utility

[gksudo] gedit /etc/X11/xorg.conf

and insert into the "Screen" section that's there:

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "ModeValidation" "NoEdidModes"
    Option         "ModeValidation" "AllowInterlacedModes"
    Option         "UseEDID" "FALSE"
    Option         "UseDisplayDevice" "CRT-0"
SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

save reboot/restart X server
run nvidia-settings & pick your video mode.
save it back to xorg.conf
(last 2 steps required because can not remember the exact video mode names/labels)


Please post the /var/log/Xorg.0.log after...
May need to change CRT-0 to CRT-1

---

### Post by BicyclerBoy on 2011-01-17
Just to make extra sure replace the previous post mode validation entries (2) with this one:

Option "ModeValidation" "NoDFPNativeResolutionCheck , NoVirtualSizeCheck , NoMaxPClkCheck , NoHorizSyncCheck , NoVertRefreshCheck , NoWidthAlignmentCheck , NoEdidModes , AllowInterlacedModes"


Might pay to leave out the "NoVertRefreshCheck" keyword.

But I have only needed to use
Option         "UseEDID" "FALSE"
with VGA HDTV no EDID (custom modeline) nvidia drivers 170 - 260.

---

### Post by BicyclerBoy on 2011-01-17
Have seen some discussion about whether the audio module & hdmi audio is causing EDID problems.

snd_hda_codec_nvhdmi

Someone suggested trying to blacklist the audio module..

---


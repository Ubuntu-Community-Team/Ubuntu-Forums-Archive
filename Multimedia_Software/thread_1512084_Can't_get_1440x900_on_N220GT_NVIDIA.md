---
title: "Can't get 1440x900 on N220GT NVIDIA"
date: 2010-06-17
forum: Multimedia Software
---

### Post by Piripe on 2010-06-17
Hi, im new on linux
Running-> Ubuntu 10.04
My "NVIDIA X SERVER SETTINGS" does not show the resolution 1440*900 as an option, so im unable to choose it, and im using a 19' lcd with 1440*900 recomended.
It say "monitor unknow"

Edit: Problem Solved
After a lot of googling, and making maches the important Errors were this:

Monitor Unknown -->EDID Failing

What to do? 

Disable Nvidia Edid
source [http://linux.die.net/man/1/nvidia-xconfig](http://linux.die.net/man/1/nvidia-xconfig)
Open a new terminal(if you are using ubuntu, wich i guess, you can open a new terminal on aplications>accesories>teminal, i didn't know this when i post this trouble lol) and use:
**sudo su**
(your pasword)
**nvidia-xconfig --no-use-edid**

(source [http://linux.die.net/man/1/nvidia-xconfig](http://linux.die.net/man/1/nvidia-xconfig) comands for nvidia and how to use them)
then, add a few resolutions on xorg.conf, to open and edit xorg.conf, you can use this comands on the same terminal:[B]
gedit [/B]**/etc/X11/****xorg.conf**
now here you must add the resolution you need
from this:
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "HP w1907"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1440x900 +0+0"
    Option         "UseEdid" "False"
    SubSection     "Display"
        Depth       24
EndSection

To this:

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "HP w1907"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1440x900 +0+0"
    Option         "UseEdid" "False"
    SubSection     "Display"
        Depth       24
    EndSubSection
    SubSection "Display"
        Depth 1
        Modes "1440x900"
    EndSubSection
    SubSection "Display"
        Depth 4
        Modes "1440x900"
    EndSubSection
    SubSection "Display"
        Depth 8
        Modes "1440x900"
    EndSubSection
    SubSection "Display"
        Depth 15
        Modes "1440x900"
    EndSubSection
    SubSection "Display"
        Depth 16
        Modes "1440x900"
    EndSubSection
    SubSection "Display"
        Depth 24
        Modes "1440x900"
    EndSubSection
EndSection
 
as i used 1440x900, you can use the resolution that YOU NEED

---

### Post by cbrunhaver on 2010-06-17
from the terminal, first, restart xorg by typing:

sudo service gdm restart

When Xorg is up and running again, bring up a terminal and run the following command to parse Xorg's log file and output a text file to your desktop with all the monitor's available modes:

sed -n '/- Modes/,/- End/p' /var/log/Xorg.0.log | sed 's/.*(0)://g' > $HOME/Desktop/modes.txt

Paste the results of the modes.txt into your reply. 

Basically, if you don't have 1440x900, we'll need to use a modeline in your xorg.conf.

FWIW, this was borrowed from a sticky on the xbmc.org linux support forum, where I had a similar issue with a TV.

---

### Post by Piripe on 2010-06-17
**sudo service gdm restart**(worked)



**sed -n '/- Modes/,/- End/p' /var/log/Xorg.0.log | sed 's/.*(0)://g' > $HOME/Desktop/modes.txt** (Failed: "*bash: /home/felipe/Desktop/modes.txt: No existe el fichero ó directorio*")


but i think i dont got 1440*900, got top of 1360*768

by the way, im from chile and got linux on spanish

---

### Post by Piripe on 2010-06-17
my xorg.2.log (last log)

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux felipe-desktop 2.6.32-22-generic-pae #36-Ubuntu SMP Thu Jun 3 23:14:23 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=d99ee761-bfe2-4c81-acf0-afae16d19a7c ro quiet splash
Build Date: 09 June 2010  10:55:28AM
xorg-server 2:1.7.6-2ubuntu7.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.2.log", Time: Thu Jun 17 20:05:49 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 10

(--) PCI:*(0:1:0:0) 10de:0a20:1462:1992 nVidia Corporation GT216 [GeForce GT 220] rev 162, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 10:38:29 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 09:34:29 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1152x864 +0+0"
(**) Jun 17 20:05:49 NVIDIA(0): Enabling RENDER acceleration
(II) Jun 17 20:05:49 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Jun 17 20:05:49 NVIDIA(0):     enabled.
(WW) Jun 17 20:05:49 NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
(II) Jun 17 20:05:49 NVIDIA(0): NVIDIA GPU GeForce GT 220 (GT216) at PCI:1:0:0 (GPU-0)
(--) Jun 17 20:05:49 NVIDIA(0): Memory: 1048576 kBytes
(--) Jun 17 20:05:49 NVIDIA(0): VideoBIOS: 70.16.2e.00.02
(II) Jun 17 20:05:49 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Jun 17 20:05:49 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Jun 17 20:05:49 NVIDIA(0): Connected display device(s) on GeForce GT 220 at PCI:1:0:0:
(--) Jun 17 20:05:49 NVIDIA(0):     CRT-1
(--) Jun 17 20:05:49 NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
(II) Jun 17 20:05:49 NVIDIA(0): Assigned Display Device: CRT-1
(II) Jun 17 20:05:49 NVIDIA(0): Validated modes:
(II) Jun 17 20:05:49 NVIDIA(0):     "1152x864+0+0"
(II) Jun 17 20:05:49 NVIDIA(0): Virtual screen size determined to be 1152 x 864
(WW) Jun 17 20:05:49 NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
(WW) Jun 17 20:05:49 NVIDIA(0):     from CRT-1's EDID.
(==) Jun 17 20:05:49 NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) Jun 17 20:05:49 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Jun 17 20:05:49 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Jun 17 20:05:49 NVIDIA(0): Initialized GPU GART.
(II) Jun 17 20:05:49 NVIDIA(0): Setting mode "1152x864+0+0"
(II) Loading extension NV-GLX
(II) Jun 17 20:05:49 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Jun 17 20:05:49 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "latam"
(II) XKB: reuse xkmfile /var/lib/xkb/server-6093290166A051D542CCE8F08557751EA3CDD75C.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "latam"
(II) config/udev: Adding input device Sleep Button (/dev/input/event0)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event0"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "latam"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "latam"
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event5)
(**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Found relative axes
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Jun 17 20:06:15 NVIDIA(0): Setting mode "1152x864+0+0"
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Sleep Button: Device reopened after 1 attempts.
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) ImPS/2 Generic Wheel Mouse: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Jun 17 20:07:23 NVIDIA(0): Setting mode "1152x864+0+0"
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Sleep Button: Device reopened after 1 attempts.
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) ImPS/2 Generic Wheel Mouse: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Jun 17 20:07:58 NVIDIA(0): Setting mode "1152x864+0+0"
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Sleep Button: Device reopened after 1 attempts.
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) ImPS/2 Generic Wheel Mouse: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) ImPS/2 Generic Wheel Mouse: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Sleep Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log

i guess the trouble is with the EDID =/

---

### Post by cbrunhaver on 2010-06-18
Yes, it cannot read the EDID

"(WW) Jun 17 20:05:49 NVIDIA(GPU-0): Unable to read EDID for display device CRT-1"

You will need to create a modeline.

[http://www.mythtv.org/wiki/Modeline_Database](http://www.mythtv.org/wiki/Modeline_Database)


You will need to add this sort of thing to your xorg.conf to forve the modeline:

Option          "ModeValidation" "NoEdidDFPMaxSizeCheck,NoDFPNativeResolutionCheck"
Option          "ExactModeTimingsDVI" "TRUE"
Monitor section
Option          "UseEDID" "FALSE"

---


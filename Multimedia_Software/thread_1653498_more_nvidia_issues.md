---
title: "more nvidia issues"
date: 2010-12-27
forum: Multimedia Software
---

### Post by jord1981 on 2010-12-27
You may remember me from this other recent thread - [http://ubuntuforums.org/showthread.php?t=1648734](http://ubuntuforums.org/showthread.php?t=1648734)

As you can see, I was able to get everything working properly.  Since then, I had a power outage and the system suffered a hard reboot.  Since them, I cannot fully boat to GDM with the nvidia drivers activated.

With the nvidia drivers on, I boot to the background image but then it hangs.  I am able to boot by deleting xorg.conf and allowing it to boot usually automatic settings.

I have tried removing and reinstalling the nvidia drivers (from their site) several different ways to no avail.

Can anyone help?

---

### Post by tjones00 on 2010-12-27
Did you try generating a new xorg.conf (not a merged one)

```
sudo rm /etc/X11/xorg.conf

sudo nvidia-xconfig
```If that doesn't work please post your xorg.conf (/etc/X11/xorg.conf) and Xorg.0.log (/var/log/Xorg.0.log) from when the driver fails to load. Set an xorg.conf and nvidia then boot. Reboot after it fails and look at Xorg.0.log.old it should have the information from the previous failed session.

If you just select minimal graphics when the desktop fails to load the Xorg.0.log we'd need should be Xorg.0.log just look at it before posting and make sure it attempts to use the nvidia driver.

Xorg.0.log = current
Xorg.0.log.old = last

---

### Post by jord1981 on 2010-12-27
Here is the log as requested.

```
[  9459.036] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[  9459.036] X Protocol Version 11, Revision 0
[  9459.036] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[  9459.036] Current Operating System: Linux jord02 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686
[  9459.036] Kernel command line: root=UUID=64e7da34-8d2b-47ab-85c7-5b7d8e1980a7 ro quiet splash 
[  9459.036] Build Date: 16 September 2010  05:39:22PM
[  9459.036] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[  9459.036] Current version of pixman: 0.18.4
[  9459.036] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[  9459.037] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  9459.037] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec 27 03:30:53 2010
[  9459.037] (==) Using config file: "/etc/X11/xorg.conf"
[  9459.037] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  9459.038] (==) ServerLayout "Layout0"
[  9459.038] (**) |-->Screen "Screen0" (0)
[  9459.038] (**) |   |-->Monitor "Monitor0"
[  9459.039] (**) |   |-->Device "Device0"
[  9459.039] (**) |-->Input Device "Keyboard0"
[  9459.039] (**) |-->Input Device "Mouse0"
[  9459.039] (==) Automatically adding devices
[  9459.039] (==) Automatically enabling devices
[  9459.039] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  9459.039] 	Entry deleted from font path.
[  9459.039] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  9459.039] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  9459.039] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[  9459.039] (WW) Disabling Keyboard0
[  9459.039] (WW) Disabling Mouse0
[  9459.039] (II) Loader magic: 0x81f8e00
[  9459.040] (II) Module ABI versions:
[  9459.040] 	X.Org ANSI C Emulation: 0.4
[  9459.040] 	X.Org Video Driver: 8.0
[  9459.040] 	X.Org XInput driver : 11.0
[  9459.040] 	X.Org Server Extension : 4.0
[  9459.041] (--) PCI:*(0:1:0:0) 10de:0185:0000:0000 rev 193, Mem @ 0xce000000/16777216, 0xc0000000/134217728, BIOS @ 0x????????/131072
[  9459.042] (II) Open ACPI successful (/var/run/acpid.socket)
[  9459.042] (II) LoadModule: "extmod"
[  9459.043] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  9459.043] (II) Module extmod: vendor="X.Org Foundation"
[  9459.043] 	compiled for 1.9.0, module version = 1.0.0
[  9459.043] 	Module class: X.Org Server Extension
[  9459.043] 	ABI class: X.Org Server Extension, version 4.0
[  9459.043] (II) Loading extension MIT-SCREEN-SAVER
[  9459.043] (II) Loading extension XFree86-VidModeExtension
[  9459.043] (II) Loading extension XFree86-DGA
[  9459.043] (II) Loading extension DPMS
[  9459.043] (II) Loading extension XVideo
[  9459.043] (II) Loading extension XVideo-MotionCompensation
[  9459.044] (II) Loading extension X-Resource
[  9459.044] (II) LoadModule: "dbe"
[  9459.044] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  9459.044] (II) Module dbe: vendor="X.Org Foundation"
[  9459.044] 	compiled for 1.9.0, module version = 1.0.0
[  9459.044] 	Module class: X.Org Server Extension
[  9459.044] 	ABI class: X.Org Server Extension, version 4.0
[  9459.044] (II) Loading extension DOUBLE-BUFFER
[  9459.044] (II) LoadModule: "glx"
[  9459.045] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  9459.097] (II) Module glx: vendor="NVIDIA Corporation"
[  9459.097] 	compiled for 4.0.2, module version = 1.0.0
[  9459.097] 	Module class: X.Org Server Extension
[  9459.097] (II) NVIDIA GLX Module  96.43.19  Wed Oct 27 19:20:11 PDT 2010
[  9459.097] (II) Loading extension GLX
[  9459.097] (II) LoadModule: "record"
[  9459.098] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  9459.098] (II) Module record: vendor="X.Org Foundation"
[  9459.098] 	compiled for 1.9.0, module version = 1.13.0
[  9459.098] 	Module class: X.Org Server Extension
[  9459.098] 	ABI class: X.Org Server Extension, version 4.0
[  9459.098] (II) Loading extension RECORD
[  9459.098] (II) LoadModule: "dri"
[  9459.099] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  9459.099] (II) Module dri: vendor="X.Org Foundation"
[  9459.099] 	compiled for 1.9.0, module version = 1.0.0
[  9459.099] 	ABI class: X.Org Server Extension, version 4.0
[  9459.099] (II) Loading extension XFree86-DRI
[  9459.099] (II) LoadModule: "dri2"
[  9459.099] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  9459.100] (II) Module dri2: vendor="X.Org Foundation"
[  9459.100] 	compiled for 1.9.0, module version = 1.2.0
[  9459.100] 	ABI class: X.Org Server Extension, version 4.0
[  9459.100] (II) Loading extension DRI2
[  9459.100] (II) LoadModule: "nvidia"
[  9459.101] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[  9459.102] (II) Module nvidia: vendor="NVIDIA Corporation"
[  9459.102] 	compiled for 4.0.2, module version = 1.0.0
[  9459.102] 	Module class: X.Org Video Driver
[  9459.102] (II) NVIDIA dlloader X Driver  96.43.19  Wed Oct 27 19:07:40 PDT 2010
[  9459.103] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  9459.103] (--) using VT number 8

[  9459.112] (II) Loading sub module "fb"
[  9459.112] (II) LoadModule: "fb"
[  9459.112] (II) Loading /usr/lib/xorg/modules/libfb.so
[  9459.113] (II) Module fb: vendor="X.Org Foundation"
[  9459.113] 	compiled for 1.9.0, module version = 1.0.0
[  9459.113] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  9459.113] (II) Loading sub module "ramdac"
[  9459.113] (II) LoadModule: "ramdac"
[  9459.113] (II) Module "ramdac" already built-in
[  9459.113] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[  9459.113] (==) NVIDIA(0): RGB weight 888
[  9459.113] (==) NVIDIA(0): Default visual is TrueColor
[  9459.113] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  9459.114] (**) NVIDIA(0): Enabling RENDER acceleration
[  9459.114] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[  9459.114] (II) NVIDIA(0):     enabled.
[  9460.258] (II) NVIDIA(0): NVIDIA GPU GeForce4 MX 4000 at PCI:1:0:0 (GPU-0)
[  9460.258] (--) NVIDIA(0): Memory: 131072 kBytes
[  9460.258] (--) NVIDIA(0): VideoBIOS: 04.18.20.36.00
[  9460.258] (II) NVIDIA(0): Detected AGP rate: 4X
[  9460.258] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[  9460.258] (--) NVIDIA(0): Connected display device(s) on GeForce4 MX 4000 at PCI:1:0:0:
[  9460.258] (--) NVIDIA(0):     LG TV (CRT-0)
[  9460.258] (--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
[  9460.258] (--) NVIDIA(0): LG TV (CRT-0): 350.0 MHz maximum pixel clock
[  9460.258] (--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 350.0 MHz maximum pixel clock
[  9460.258] (--) NVIDIA(0): TV encoder: NVIDIA
[  9460.261] (II) NVIDIA(0): Assigned Display Device: CRT-0
[  9460.261] (II) NVIDIA(0): Validated modes:
[  9460.261] (II) NVIDIA(0):     "1600x1200"
[  9460.261] (II) NVIDIA(0):     "1280x1024"
[  9460.261] (II) NVIDIA(0):     "1024x768"
[  9460.261] (II) NVIDIA(0):     "800x600"
[  9460.261] (II) NVIDIA(0):     "640x480"
[  9460.261] (II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
[  9460.266] (--) NVIDIA(0): DPI set to (35, 46); computed from "UseEdidDpi" X config
[  9460.266] (--) NVIDIA(0):     option
[  9460.266] (--) Depth 24 pixmap format is 32 bpp
[  9460.269] (II) NVIDIA(0): Initialized GART.
[  9460.356] (II) NVIDIA(0): Setting mode "1600x1200"
[  9460.459] (II) Loading extension NV-GLX
[  9460.474] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[  9460.492] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[  9460.492] (==) NVIDIA(0): Backing store disabled
[  9460.492] (==) NVIDIA(0): Silken mouse enabled
[  9460.493] (**) NVIDIA(0): DPMS enabled
[  9460.493] (II) Loading extension NV-CONTROL
[  9460.493] (==) RandR enabled
[  9460.493] (II) Initializing built-in extension Generic Event Extension
[  9460.493] (II) Initializing built-in extension SHAPE
[  9460.493] (II) Initializing built-in extension MIT-SHM
[  9460.493] (II) Initializing built-in extension XInputExtension
[  9460.493] (II) Initializing built-in extension XTEST
[  9460.493] (II) Initializing built-in extension BIG-REQUESTS
[  9460.493] (II) Initializing built-in extension SYNC
[  9460.493] (II) Initializing built-in extension XKEYBOARD
[  9460.493] (II) Initializing built-in extension XC-MISC
[  9460.493] (II) Initializing built-in extension SECURITY
[  9460.493] (II) Initializing built-in extension XINERAMA
[  9460.493] (II) Initializing built-in extension XFIXES
[  9460.493] (II) Initializing built-in extension RENDER
[  9460.494] (II) Initializing built-in extension RANDR
[  9460.494] (II) Initializing built-in extension COMPOSITE
[  9460.494] (II) Initializing built-in extension DAMAGE
[  9460.494] (II) Initializing built-in extension GESTURE
[  9460.501] (II) Initializing extension GLX
[  9460.579] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  9460.599] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  9460.599] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  9460.599] (II) LoadModule: "evdev"
[  9460.600] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  9460.601] (II) Module evdev: vendor="X.Org Foundation"
[  9460.601] 	compiled for 1.9.0, module version = 2.3.2
[  9460.601] 	Module class: X.Org XInput Driver
[  9460.601] 	ABI class: X.Org XInput driver, version 11.0
[  9460.601] (**) Power Button: always reports core events
[  9460.601] (**) Power Button: Device: "/dev/input/event1"
[  9460.601] (II) Power Button: Found keys
[  9460.602] (II) Power Button: Configuring as keyboard
[  9460.602] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  9460.602] (**) Option "xkb_rules" "evdev"
[  9460.602] (**) Option "xkb_model" "pc105"
[  9460.602] (**) Option "xkb_layout" "us"
[  9460.605] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[  9460.605] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  9460.605] (**) Sleep Button: always reports core events
[  9460.605] (**) Sleep Button: Device: "/dev/input/event0"
[  9460.605] (II) Sleep Button: Found keys
[  9460.605] (II) Sleep Button: Configuring as keyboard
[  9460.605] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[  9460.605] (**) Option "xkb_rules" "evdev"
[  9460.605] (**) Option "xkb_model" "pc105"
[  9460.605] (**) Option "xkb_layout" "us"
[  9460.615] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[  9460.616] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  9460.616] (**) AT Translated Set 2 keyboard: always reports core events
[  9460.616] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[  9460.616] (II) AT Translated Set 2 keyboard: Found keys
[  9460.616] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  9460.616] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  9460.616] (**) Option "xkb_rules" "evdev"
[  9460.616] (**) Option "xkb_model" "pc105"
[  9460.616] (**) Option "xkb_layout" "us"
[  9460.617] (II) config/udev: Adding input device ImExPS/2 Logitech Explorer Mouse (/dev/input/event3)
[  9460.617] (**) ImExPS/2 Logitech Explorer Mouse: Applying InputClass "evdev pointer catchall"
[  9460.618] (**) ImExPS/2 Logitech Explorer Mouse: always reports core events
[  9460.618] (**) ImExPS/2 Logitech Explorer Mouse: Device: "/dev/input/event3"
[  9460.618] (II) ImExPS/2 Logitech Explorer Mouse: Found 9 mouse buttons
[  9460.618] (II) ImExPS/2 Logitech Explorer Mouse: Found scroll wheel(s)
[  9460.618] (II) ImExPS/2 Logitech Explorer Mouse: Found relative axes
[  9460.618] (II) ImExPS/2 Logitech Explorer Mouse: Found x and y relative axes
[  9460.618] (II) ImExPS/2 Logitech Explorer Mouse: Configuring as mouse
[  9460.618] (**) ImExPS/2 Logitech Explorer Mouse: YAxisMapping: buttons 4 and 5
[  9460.618] (**) ImExPS/2 Logitech Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  9460.618] (II) XINPUT: Adding extended input device "ImExPS/2 Logitech Explorer Mouse" (type: MOUSE)
[  9460.618] (II) ImExPS/2 Logitech Explorer Mouse: initialized for relative axes.
[  9460.619] (II) config/udev: Adding input device ImExPS/2 Logitech Explorer Mouse (/dev/input/mouse0)
[  9460.619] (II) No input driver/identifier specified (ignoring)
[  9462.063] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[  9478.243] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[  9478.321] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
```

---

### Post by tjones00 on 2010-12-27
It looks like you have nvidia 96.43.17 installed.

[http://www.nvnews.net/vbulletin/showthread.php?t=156866](http://www.nvnews.net/vbulletin/showthread.php?t=156866)

Read the last post on that thread. Also see post #9 they're getting the Xalloc error that is also present in your log. From a posted logs in that thread they are using the exact same driver you are.

Unfortunately it doesn't look like they've found a solution.

Try the boot parameter nomodeset. At the grub bootloader edit the kernel (press e) and fine the line "quiet splash" replace it with "nomodeset noplymouth" and then boot. 

If that doesn't work post your xorg.conf and then reboot again with "quiet splash" then use pastebin.com to post the** last **300 lines or so of your kern.log in /var/log/kern.log and leave the link here.

---

### Post by jord1981 on 2010-12-27
> **tjones00 said:**
> Try the boot parameter nomodeset. At the grub bootloader edit the kernel (press e) and fine the line "quiet splash" replace it with "nomodeset noplymouth" and then boot.

No luck there.

> **tjones00 said:**
> If that doesn't work post your xorg.conf and then reboot again with "quiet splash" then use pastebin.com to post the** last **300 lines or so of your kern.log in /var/log/kern.log and leave the link here.

Here it is: [http://pastebin.com/DR64hFk3](http://pastebin.com/DR64hFk3)

Thanks for your help!

EDIT:

Sorry I forgot to post my xorg.conf, here it is:

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Wed Oct 27 19:20:23 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by tjones00 on 2010-12-27
My bad you have nvidia 96.43.19 installed not 96.43.17.

Anyway I don't see anything obvious in kern.log or your xorg.conf.

So that leaves the nvidia driver and x server. You said you've tried different nvidia drivers lets try a different x server. There is an updated one in the 10.10 release (current one had some bugs).

It's probably easiest to do a compete system update. 

System > Administration > Synaptic Package Manager

In Synaptic: Settings > Repositories > Updates -check Pre-released updates (maverick-proposed) and close. Then press reload in Synaptic a couple of times and close the program after it reloads.

Next: System > Administration > Update Manager it should now have a bunch of updates to install among these will be a new x server.

Reboot after updating and try it again.

If it still doesn't work at that point you'll probably have to bring the issue up on the nvidia forums and submit a bug report.

If you don't want to bother with that may I suggest Linux Mint Debian ([http://www.linuxmint.com/](http://www.linuxmint.com/)) that was released on the 24th and promises to be an excellent Ubuntu alternative. It should be friendlier with older hardware than the current version of Ubuntu.

---

### Post by jord1981 on 2010-12-27
Unfortunately updating to the newer (pre-release) xserver did not fix the problem.  What really frustrates me as that I had this driver working on this version of the OS on this box a week ago.  I can't for the life of me figure out what is different now.

I will take a stab over at the nvidia forum as you suggest.  Thanks for your help.

---


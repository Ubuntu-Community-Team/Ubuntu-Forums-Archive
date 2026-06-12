---
title: "nvidia with X loaded well, but cant see anything"
date: 2011-05-05
forum: Multimedia Software
---

### Post by shlomi on 2011-05-05
Hey,

I have a weird problem, just got a new laptop with two VGA components, as follows:
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df0 (rev a1)

```

After i installed (both 11.04 and 10.10) the screen loaded fine. I then installed the nvidia propriety drivers and xorg has failed to load, complaining that it cannot find the device (nvidia).

So i added a Busid as follows:
```
Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
       ** Busid  "PCI:1:0:0"**
        option  "NoLogo"        "True"
EndSection

```

Then i did services gdm restart, and X seemed to load up fine. here is /var/log/Xorg.0.log
```
[   684.576] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   684.576] X Protocol Version 11, Revision 0
[   684.576] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   684.577] Current Operating System: Linux shlomi-laptop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[   684.577] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=8ae8fa4a-466a-453a-ad18-1078f427e3f1 ro quiet splash
[   684.577] Build Date: 16 September 2010  05:39:22PM
[   684.577] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[   684.577] Current version of pixman: 0.18.4
[   684.577]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   684.577] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   684.577] (==) Log file: "/var/log/Xorg.0.log", Time: Fri May  6 02:22:03 2011
[   684.577] (==) Using config file: "/etc/X11/xorg.conf"
[   684.577] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   684.577] (==) No Layout section.  Using the first Screen section.
[   684.578] (**) |-->Screen "Default Screen" (0)
[   684.578] (**) |   |-->Monitor "<default monitor>"
[   684.578] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[   684.578] (**) |   |-->Device "Default Device"
[   684.578] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[   684.578] (==) Automatically adding devices
[   684.578] (==) Automatically enabling devices
[   684.579] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   684.579]     Entry deleted from font path.
[   684.579] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   684.579] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   684.579] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   684.579] (II) Loader magic: 0x81f8e00
[   684.579] (II) Module ABI versions:
[   684.579]     X.Org ANSI C Emulation: 0.4
[   684.579]     X.Org Video Driver: 8.0
[   684.579]     X.Org XInput driver : 11.0
[   684.579]     X.Org Server Extension : 4.0
[   684.581] (--) PCI:*(0:0:2:0) 8086:0046:1558:5130 rev 2, Mem @ 0xfd000000/4194304, 0xd0000000/268435456, I/O @ 0x00001800/8
[   684.581] (--) PCI: (0:1:0:0) 10de:0df0:1558:5130 rev 161, Mem @ 0xfb000000/16777216, 0xf0000000/134217728, 0xf8000000/33554432, I/O @ 0x00002000/128
[   684.581] (II) Open ACPI successful (/var/run/acpid.socket)
[   684.581] (II) "extmod" will be loaded by default.
[   684.581] (II) "dbe" will be loaded by default.
[   684.581] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[   684.581] (II) "record" will be loaded by default.
[   684.581] (II) "dri" will be loaded by default.
[   684.581] (II) "dri2" will be loaded by default.
[   684.581] (II) LoadModule: "glx"
[   684.581] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[   684.599] (II) Module glx: vendor="NVIDIA Corporation"
[   684.605]     compiled for 4.0.2, module version = 1.0.0
[   684.605]     Module class: X.Org Server Extension
[   684.605] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 07:01:31 PDT 2010
[   684.606] (II) Loading extension GLX
[   684.606] (II) LoadModule: "extmod"
[   684.606] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   684.606] (II) Module extmod: vendor="X.Org Foundation"
[   684.606]     compiled for 1.9.0, module version = 1.0.0
[   684.606]     Module class: X.Org Server Extension
[   684.606]     ABI class: X.Org Server Extension, version 4.0
[   684.606] (II) Loading extension MIT-SCREEN-SAVER
[   684.606] (II) Loading extension XFree86-VidModeExtension
[   684.606] (II) Loading extension XFree86-DGA
[   684.606] (II) Loading extension DPMS
[   684.606] (II) Loading extension XVideo
[   684.606] (II) Loading extension XVideo-MotionCompensation
[   684.606] (II) Loading extension X-Resource
[   684.606] (II) LoadModule: "dbe"
[   684.607] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   684.607] (II) Module dbe: vendor="X.Org Foundation"
[   684.607]     compiled for 1.9.0, module version = 1.0.0
[   684.607]     Module class: X.Org Server Extension
[   684.607]     ABI class: X.Org Server Extension, version 4.0
[   684.607] (II) Loading extension DOUBLE-BUFFER
[   684.607] (II) LoadModule: "record"
[   684.607] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   684.607] (II) Module record: vendor="X.Org Foundation"
[   684.607]     compiled for 1.9.0, module version = 1.13.0
[   684.607]     Module class: X.Org Server Extension
[   684.607]     ABI class: X.Org Server Extension, version 4.0
[   684.607] (II) Loading extension RECORD
[   684.607] (II) LoadModule: "dri"
[   684.607] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   684.608] (II) Module dri: vendor="X.Org Foundation"
[   684.608]     compiled for 1.9.0, module version = 1.0.0
[   684.608]     ABI class: X.Org Server Extension, version 4.0
[   684.608] (II) Loading extension XFree86-DRI
[   684.608] (II) LoadModule: "dri2"
[   684.608] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   684.608] (II) Module dri2: vendor="X.Org Foundation"
[   684.608]     compiled for 1.9.0, module version = 1.2.0
[   684.608]     ABI class: X.Org Server Extension, version 4.0
[   684.608] (II) Loading extension DRI2
[   684.608] (II) LoadModule: "nvidia"
[   684.608] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[   684.608] (II) Module nvidia: vendor="NVIDIA Corporation"
[   684.608]     compiled for 4.0.2, module version = 1.0.0
[   684.608]     Module class: X.Org Video Driver
[   684.609] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 06:37:13 PDT 2010
[   684.609] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   684.609] (--) using VT number 8

[   684.613] (II) Loading sub module "fb"
[   684.613] (II) LoadModule: "fb"
[   684.613] (II) Loading /usr/lib/xorg/modules/libfb.so
[   684.613] (II) Module fb: vendor="X.Org Foundation"
[   684.613]     compiled for 1.9.0, module version = 1.0.0
[   684.613]     ABI class: X.Org ANSI C Emulation, version 0.4
[   684.613] (II) Loading sub module "wfb"
[   684.613] (II) LoadModule: "wfb"
[   684.614] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   684.614] (II) Module wfb: vendor="X.Org Foundation"
[   684.614]     compiled for 1.9.0, module version = 1.0.0
[   684.614]     ABI class: X.Org ANSI C Emulation, version 0.4
[   684.614] (II) Loading sub module "ramdac"
[   684.614] (II) LoadModule: "ramdac"
[   684.614] (II) Module "ramdac" already built-in
[   684.614] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   684.614] (==) NVIDIA(0): RGB weight 888
[   684.614] (==) NVIDIA(0): Default visual is TrueColor
[   684.614] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   684.614] (**) NVIDIA(0): Option "NoLogo" "True"
[   684.614] (**) NVIDIA(0): Enabling RENDER acceleration
[   684.614] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[   684.614] (II) NVIDIA(0):     enabled.
[   684.820] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   684.821] (II) NVIDIA(0): NVIDIA GPU GeForce GT 425M (GF108) at PCI:1:0:0 (GPU-0)
[   684.821] (--) NVIDIA(0): Memory: 1048576 kBytes
[   684.821] (--) NVIDIA(0): VideoBIOS: 70.08.12.00.ff
[   684.821] (II) NVIDIA(0): Detected PCI Express Link width: 8X
[   684.821] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   684.821] (--) NVIDIA(0): Connected display device(s) on GeForce GT 425M at PCI:1:0:0
[   684.821] (--) NVIDIA(0):     CRT-0
[   684.821] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[   684.827] (II) NVIDIA(0): Assigned Display Device: CRT-0
[   684.827] (WW) NVIDIA(0): No valid modes for "1400x900"; removing.
[   684.827] (II) NVIDIA(0): Validated modes:
[   684.827] (II) NVIDIA(0):     "1024x768"
[   684.827] (II) NVIDIA(0):     "800x600"
[   684.827] (II) NVIDIA(0):     "640x480"
[   684.827] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[   684.829] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[   684.830] (WW) NVIDIA(0):     from CRT-0's EDID.
[   684.830] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[   684.830] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[   684.830] (--) Depth 24 pixmap format is 32 bpp
[   684.830] (II) NVIDIA: Using 1024.00 MB of virtual memory for indirect memory
[   684.830] (II) NVIDIA:     access.
[   684.831] (II) NVIDIA(0): Initialized GPU GART.
[   684.835] (II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
[   684.835] (II) NVIDIA(0):     enough to receive ACPI hotkey events.
[   684.836] (WW) NVIDIA(0): ACPI: Error: Unable to find the brightness file path under
[   684.836] (WW) NVIDIA(0):     /proc/acpi/video. The NVIDIA X driver will not be able to
[   684.836] (WW) NVIDIA(0):     respond to ACPI brightness change hotkey events.
[   684.838] (II) NVIDIA(0): Setting mode "1024x768"
[   684.860] (II) Loading extension NV-GLX
[   684.915] (II) NVIDIA(0): Initialized OpenGL Acceleration
[   684.917] (==) NVIDIA(0): Disabling shared memory pixmaps
[   684.917] (II) NVIDIA(0): Initialized X Rendering Acceleration
[   684.917] (==) NVIDIA(0): Backing store disabled
[   684.917] (==) NVIDIA(0): Silken mouse enabled
[   684.923] (==) NVIDIA(0): DPMS enabled
[   684.923] (II) Loading extension NV-CONTROL
[   684.923] (II) Loading extension XINERAMA
[   684.923] (II) Loading sub module "dri2"
[   684.923] (II) LoadModule: "dri2"
[   684.923] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[   684.924] (II) NVIDIA(0): [DRI2] Setup complete
[   684.924] (==) RandR enabled
[   684.924] (II) Initializing built-in extension Generic Event Extension
[   684.924] (II) Initializing built-in extension SHAPE
[   684.924] (II) Initializing built-in extension MIT-SHM
[   684.924] (II) Initializing built-in extension XInputExtension
[   684.924] (II) Initializing built-in extension XTEST
[   684.924] (II) Initializing built-in extension BIG-REQUESTS
[   684.924] (II) Initializing built-in extension SYNC
[   684.924] (II) Initializing built-in extension XKEYBOARD
[   684.924] (II) Initializing built-in extension XC-MISC
[   684.924] (II) Initializing built-in extension SECURITY
[   684.924] (II) Initializing built-in extension XINERAMA
[   684.924] (II) Initializing built-in extension XFIXES
[   684.924] (II) Initializing built-in extension RENDER
[   684.924] (II) Initializing built-in extension RANDR
[   684.924] (II) Initializing built-in extension COMPOSITE
[   684.924] (II) Initializing built-in extension DAMAGE
[   684.924] (II) Initializing built-in extension GESTURE
[   684.924] (II) Initializing extension GLX
[   684.953] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   684.959] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   684.959] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   684.959] (II) LoadModule: "evdev"
[   684.959] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   684.960] (II) Module evdev: vendor="X.Org Foundation"
[   684.960]     compiled for 1.9.0, module version = 2.3.2
[   684.960]     Module class: X.Org XInput Driver
[   684.960]     ABI class: X.Org XInput driver, version 11.0
[   684.960] (**) Power Button: always reports core events
[   684.960] (**) Power Button: Device: "/dev/input/event3"
[   684.984] (II) Power Button: Found keys
[   684.984] (II) Power Button: Configuring as keyboard
[   684.984] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   684.984] (**) Option "xkb_rules" "evdev"
[   684.984] (**) Option "xkb_model" "pc105"
[   684.984] (**) Option "xkb_layout" "us,il"
[   684.984] (**) Option "xkb_variant" ","
[   684.984] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[   684.987] (II) XKB: reuse xkmfile /var/lib/xkb/server-2CE46D2F8CCFAB6C1A4B498F695121C1147485D7.xkm
[   684.988] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[   684.988] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   684.988] (**) Video Bus: always reports core events
[   684.989] (**) Video Bus: Device: "/dev/input/event6"
[   685.017] (II) Video Bus: Found keys
[   685.017] (II) Video Bus: Configuring as keyboard
[   685.017] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   685.017] (**) Option "xkb_rules" "evdev"
[   685.017] (**) Option "xkb_model" "pc105"
[   685.017] (**) Option "xkb_layout" "us,il"
[   685.017] (**) Option "xkb_variant" ","
[   685.017] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[   685.018] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[   685.018] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   685.018] (**) Video Bus: always reports core events
[   685.018] (**) Video Bus: Device: "/dev/input/event5"
[   685.049] (II) Video Bus: Found keys
[   685.049] (II) Video Bus: Configuring as keyboard
[   685.049] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   685.049] (**) Option "xkb_rules" "evdev"
[   685.049] (**) Option "xkb_model" "pc105"
[   685.049] (**) Option "xkb_layout" "us,il"
[   685.049] (**) Option "xkb_variant" ","
[   685.049] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[   685.051] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   685.051] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   685.051] (**) Power Button: always reports core events
[   685.051] (**) Power Button: Device: "/dev/input/event0"
[   685.081] (II) Power Button: Found keys
[   685.081] (II) Power Button: Configuring as keyboard
[   685.081] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   685.081] (**) Option "xkb_rules" "evdev"
[   685.081] (**) Option "xkb_model" "pc105"
[   685.081] (**) Option "xkb_layout" "us,il"
[   685.081] (**) Option "xkb_variant" ","
[   685.081] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[   685.082] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[   685.082] (II) No input driver/identifier specified (ignoring)
[   685.082] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   685.082] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   685.082] (**) Sleep Button: always reports core events
[   685.082] (**) Sleep Button: Device: "/dev/input/event1"
[   685.113] (II) Sleep Button: Found keys
[   685.113] (II) Sleep Button: Configuring as keyboard
[   685.113] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[   685.113] (**) Option "xkb_rules" "evdev"
[   685.113] (**) Option "xkb_model" "pc105"
[   685.113] (**) Option "xkb_layout" "us,il"
[   685.113] (**) Option "xkb_variant" ","
[   685.113] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[   685.122] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[   685.122] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   685.122] (**) AT Translated Set 2 keyboard: always reports core events
[   685.122] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[   685.145] (II) AT Translated Set 2 keyboard: Found keys
[   685.145] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   685.145] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   685.145] (**) Option "xkb_rules" "evdev"
[   685.145] (**) Option "xkb_model" "pc105"
[   685.145] (**) Option "xkb_layout" "us,il"
[   685.145] (**) Option "xkb_variant" ","
[   685.145] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[   685.146] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[   685.146] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   685.146] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   685.146] (II) LoadModule: "synaptics"
[   685.146] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   685.147] (II) Module synaptics: vendor="X.Org Foundation"
[   685.147]     compiled for 1.9.0, module version = 1.2.2
[   685.147]     Module class: X.Org XInput Driver
[   685.147]     ABI class: X.Org XInput driver, version 11.0
[   685.147] (II) Synaptics touchpad driver version 1.2.2
[   685.147] (**) Option "Device" "/dev/input/event7"
[   685.304] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5692
[   685.304] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4680
[   685.304] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   685.304] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[   685.304] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[   685.432] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   685.432] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   685.496] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[   685.496] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   685.496] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[   685.496] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   685.496] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   685.592] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   685.592] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   685.592] (II) No input driver/identifier specified (ignoring)

```

so, as I said, it loaded up fine, i even heard the sound that plays when the login screen pops up, but the screen is completely blank. nothing on it. at all.

what could it possibly be?

thanks,
shlomi

---

### Post by shlomi on 2011-05-06
anyone? please?

---

### Post by BicyclerBoy on 2011-05-06
It could be the error
684.820] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0

The driver version you are using was not very good with EDID.
There are better/later pre-compiled driver packages.
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=natty](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=natty)

Can you use DVI or HDMI connection ?
It is possible to force a video mode that will work with your monitor but will need the model info.
Much easier to try a later driver first..

Reboot in safe-mode ..or edit the xorg.conf file from console login <Ctrl>+<Alt>+<F1> to disable the nvidia driver..

The real problem could be the hardware..is this an optimus laptop ?
Better post the full model name/number so we can find out...

---

### Post by shlomi on 2011-05-06
Hi BicyclerBoy, thanks for your reply,

I am using a laptop, so iam not so sure how the CRT line fits in.. My model is slightly strange, its an Olivetti laptop, which i believe is only sold around my region (Israel) so the maximum info i got on that was "LCD 15.6" HD (1366x768 ) LED" 

Ill try an HDMI cable soon, but since i cant use nvidia-settings, i am not sure what ill need to do in order to redirect it to it.. ill figure that out.

anyways, iam going to try the new driver first and let you know,
thanks!

Shlomi

---

### Post by shlomi on 2011-05-06
Hey, 
OK, i upgraded the driver using the link two posts up,
and also tried to use HDMI, but the weird problem persists. I can even log in the system, but without seeing my actions!

I managed to get the correct Modeline for my system (from the working intel card), and put it in my xorg.conf, although from the log file it seemed to accept it, i still see nothing on screen (both on the laptop lcd and an HDMI connected LCD), but the X is started..

here is the log file,
```
[   891.182] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   891.182] X Protocol Version 11, Revision 0
[   891.182] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   891.182] Current Operating System: Linux shlomi-laptop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[   891.182] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=8ae8fa4a-466a-453a-ad18-1078f427e3f1 ro quiet splash
[   891.182] Build Date: 16 September 2010  05:39:22PM
[   891.182] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[   891.182] Current version of pixman: 0.18.4
[   891.182] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   891.182] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   891.182] (==) Log file: "/var/log/Xorg.0.log", Time: Fri May  6 16:14:09 2011
[   891.182] (==) Using config file: "/etc/X11/xorg.conf"
[   891.182] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   891.183] (==) ServerLayout "Layout0"
[   891.183] (**) |-->Screen "Screen0" (0)
[   891.183] (**) |   |-->Monitor "Monitor0"
[   891.183] (**) |   |-->Device "Device0"
[   891.183] (**) |-->Input Device "Keyboard0"
[   891.183] (**) |-->Input Device "Mouse0"
[   891.183] (==) Automatically adding devices
[   891.183] (==) Automatically enabling devices
[   891.184] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   891.184] 	Entry deleted from font path.
[   891.184] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   891.184] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   891.184] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   891.184] (WW) Disabling Keyboard0
[   891.184] (WW) Disabling Mouse0
[   891.184] (II) Loader magic: 0x81f8e00
[   891.184] (II) Module ABI versions:
[   891.184] 	X.Org ANSI C Emulation: 0.4
[   891.184] 	X.Org Video Driver: 8.0
[   891.184] 	X.Org XInput driver : 11.0
[   891.184] 	X.Org Server Extension : 4.0
[   891.185] (--) PCI:*(0:0:2:0) 8086:0046:1558:5130 rev 2, Mem @ 0xfd000000/4194304, 0xd0000000/268435456, I/O @ 0x00001800/8
[   891.185] (--) PCI: (0:1:0:0) 10de:0df0:1558:5130 rev 161, Mem @ 0xfb000000/16777216, 0xf0000000/134217728, 0xf8000000/33554432, I/O @ 0x00002000/128
[   891.186] (II) Open ACPI successful (/var/run/acpid.socket)
[   891.186] (II) LoadModule: "extmod"
[   891.186] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   891.187] (II) Module extmod: vendor="X.Org Foundation"
[   891.187] 	compiled for 1.9.0, module version = 1.0.0
[   891.187] 	Module class: X.Org Server Extension
[   891.187] 	ABI class: X.Org Server Extension, version 4.0
[   891.187] (II) Loading extension MIT-SCREEN-SAVER
[   891.187] (II) Loading extension XFree86-VidModeExtension
[   891.187] (II) Loading extension XFree86-DGA
[   891.187] (II) Loading extension DPMS
[   891.187] (II) Loading extension XVideo
[   891.187] (II) Loading extension XVideo-MotionCompensation
[   891.187] (II) Loading extension X-Resource
[   891.187] (II) LoadModule: "dbe"
[   891.187] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   891.188] (II) Module dbe: vendor="X.Org Foundation"
[   891.188] 	compiled for 1.9.0, module version = 1.0.0
[   891.188] 	Module class: X.Org Server Extension
[   891.188] 	ABI class: X.Org Server Extension, version 4.0
[   891.188] (II) Loading extension DOUBLE-BUFFER
[   891.188] (II) LoadModule: "glx"
[   891.188] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[   891.207] (II) Module glx: vendor="NVIDIA Corporation"
[   891.207] 	compiled for 4.0.2, module version = 1.0.0
[   891.207] 	Module class: X.Org Server Extension
[   891.207] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[   891.207] (II) Loading extension GLX
[   891.207] (II) LoadModule: "record"
[   891.208] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   891.208] (II) Module record: vendor="X.Org Foundation"
[   891.208] 	compiled for 1.9.0, module version = 1.13.0
[   891.208] 	Module class: X.Org Server Extension
[   891.208] 	ABI class: X.Org Server Extension, version 4.0
[   891.208] (II) Loading extension RECORD
[   891.208] (II) LoadModule: "dri"
[   891.209] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   891.209] (II) Module dri: vendor="X.Org Foundation"
[   891.209] 	compiled for 1.9.0, module version = 1.0.0
[   891.209] 	ABI class: X.Org Server Extension, version 4.0
[   891.209] (II) Loading extension XFree86-DRI
[   891.209] (II) LoadModule: "dri2"
[   891.209] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   891.209] (II) Module dri2: vendor="X.Org Foundation"
[   891.209] 	compiled for 1.9.0, module version = 1.2.0
[   891.209] 	ABI class: X.Org Server Extension, version 4.0
[   891.209] (II) Loading extension DRI2
[   891.209] (II) LoadModule: "nvidia"
[   891.210] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[   891.210] (II) Module nvidia: vendor="NVIDIA Corporation"
[   891.210] 	compiled for 4.0.2, module version = 1.0.0
[   891.210] 	Module class: X.Org Video Driver
[   891.210] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[   891.210] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   891.210] (--) using VT number 8

[   891.215] (II) Loading sub module "fb"
[   891.215] (II) LoadModule: "fb"
[   891.216] (II) Loading /usr/lib/xorg/modules/libfb.so
[   891.216] (II) Module fb: vendor="X.Org Foundation"
[   891.216] 	compiled for 1.9.0, module version = 1.0.0
[   891.216] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   891.216] (II) Loading sub module "wfb"
[   891.216] (II) LoadModule: "wfb"
[   891.216] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   891.216] (II) Module wfb: vendor="X.Org Foundation"
[   891.216] 	compiled for 1.9.0, module version = 1.0.0
[   891.216] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   891.216] (II) Loading sub module "ramdac"
[   891.216] (II) LoadModule: "ramdac"
[   891.216] (II) Module "ramdac" already built-in
[   891.217] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   891.217] (==) NVIDIA(0): RGB weight 888
[   891.217] (==) NVIDIA(0): Default visual is TrueColor
[   891.217] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   891.458] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   891.461] (II) NVIDIA(0): NVIDIA GPU GeForce GT 425M (GF108) at PCI:1:0:0 (GPU-0)
[   891.461] (--) NVIDIA(0): Memory: 1048576 kBytes
[   891.461] (--) NVIDIA(0): VideoBIOS: 70.08.12.00.ff
[   891.461] (II) NVIDIA(0): Detected PCI Express Link width: 8X
[   891.461] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   891.461] (--) NVIDIA(0): Connected display device(s) on GeForce GT 425M at PCI:1:0:0
[   891.461] (--) NVIDIA(0):     CRT-0
[   891.461] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[   891.468] (II) NVIDIA(0): Assigned Display Device: CRT-0
[   891.468] (II) NVIDIA(0): Validated modes:
[   891.468] (II) NVIDIA(0):     "1366x768"
[   891.468] (II) NVIDIA(0):     "1024x768"
[   891.468] (II) NVIDIA(0): Virtual screen size determined to be 1366 x 768
[   891.471] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[   891.471] (WW) NVIDIA(0):     from CRT-0's EDID.
[   891.471] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[   891.471] (--) Depth 24 pixmap format is 32 bpp
[   891.471] (II) NVIDIA: Using 1024.00 MB of virtual memory for indirect memory
[   891.471] (II) NVIDIA:     access.
[   891.475] (II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
[   891.475] (II) NVIDIA(0):     enough to receive ACPI hotkey events.
[   891.475] (WW) NVIDIA(0): ACPI: Error: Unable to find the brightness file path under
[   891.475] (WW) NVIDIA(0):     /proc/acpi/video. The NVIDIA X driver will not be able to
[   891.475] (WW) NVIDIA(0):     respond to ACPI brightness change hotkey events.
[   891.477] (II) NVIDIA(0): Setting mode "1366x768"
[   891.525] (II) Loading extension NV-GLX
[   891.580] (==) NVIDIA(0): Disabling shared memory pixmaps
[   891.580] (==) NVIDIA(0): Backing store disabled
[   891.580] (==) NVIDIA(0): Silken mouse enabled
[   891.581] (**) NVIDIA(0): DPMS enabled
[   891.581] (II) Loading extension NV-CONTROL
[   891.581] (II) Loading extension XINERAMA
[   891.581] (II) Loading sub module "dri2"
[   891.581] (II) LoadModule: "dri2"
[   891.582] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[   891.582] (II) NVIDIA(0): [DRI2] Setup complete
[   891.582] (==) RandR enabled
[   891.582] (II) Initializing built-in extension Generic Event Extension
[   891.582] (II) Initializing built-in extension SHAPE
[   891.582] (II) Initializing built-in extension MIT-SHM
[   891.582] (II) Initializing built-in extension XInputExtension
[   891.582] (II) Initializing built-in extension XTEST
[   891.582] (II) Initializing built-in extension BIG-REQUESTS
[   891.582] (II) Initializing built-in extension SYNC
[   891.582] (II) Initializing built-in extension XKEYBOARD
[   891.582] (II) Initializing built-in extension XC-MISC
[   891.582] (II) Initializing built-in extension SECURITY
[   891.582] (II) Initializing built-in extension XINERAMA
[   891.582] (II) Initializing built-in extension XFIXES
[   891.582] (II) Initializing built-in extension RENDER
[   891.582] (II) Initializing built-in extension RANDR
[   891.582] (II) Initializing built-in extension COMPOSITE
[   891.582] (II) Initializing built-in extension DAMAGE
[   891.582] (II) Initializing built-in extension GESTURE
[   891.586] (II) Initializing extension GLX
[   891.624] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   891.633] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   891.633] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   891.633] (II) LoadModule: "evdev"
[   891.633] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   891.633] (II) Module evdev: vendor="X.Org Foundation"
[   891.633] 	compiled for 1.9.0, module version = 2.3.2
[   891.633] 	Module class: X.Org XInput Driver
[   891.633] 	ABI class: X.Org XInput driver, version 11.0
[   891.633] (**) Power Button: always reports core events
[   891.633] (**) Power Button: Device: "/dev/input/event3"
[   891.664] (II) Power Button: Found keys
[   891.664] (II) Power Button: Configuring as keyboard
[   891.664] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   891.664] (**) Option "xkb_rules" "evdev"
[   891.664] (**) Option "xkb_model" "pc105"
[   891.664] (**) Option "xkb_layout" "us,il"
[   891.664] (**) Option "xkb_variant" ","
[   891.664] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[   891.668] (II) XKB: reuse xkmfile /var/lib/xkb/server-2CE46D2F8CCFAB6C1A4B498F695121C1147485D7.xkm
[   891.670] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[   891.670] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   891.670] (**) Video Bus: always reports core events
[   891.670] (**) Video Bus: Device: "/dev/input/event6"
[   891.696] (II) Video Bus: Found keys
[   891.696] (II) Video Bus: Configuring as keyboard
[   891.696] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   891.696] (**) Option "xkb_rules" "evdev"
[   891.696] (**) Option "xkb_model" "pc105"
[   891.696] (**) Option "xkb_layout" "us,il"
[   891.696] (**) Option "xkb_variant" ","
[   891.696] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[   891.697] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[   891.697] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   891.697] (**) Video Bus: always reports core events
[   891.697] (**) Video Bus: Device: "/dev/input/event5"
[   891.728] (II) Video Bus: Found keys
[   891.728] (II) Video Bus: Configuring as keyboard
[   891.728] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   891.728] (**) Option "xkb_rules" "evdev"
[   891.728] (**) Option "xkb_model" "pc105"
[   891.728] (**) Option "xkb_layout" "us,il"
[   891.728] (**) Option "xkb_variant" ","
[   891.728] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[   891.730] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   891.730] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   891.730] (**) Power Button: always reports core events
[   891.730] (**) Power Button: Device: "/dev/input/event0"
[   891.760] (II) Power Button: Found keys
[   891.760] (II) Power Button: Configuring as keyboard
[   891.760] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   891.760] (**) Option "xkb_rules" "evdev"
[   891.760] (**) Option "xkb_model" "pc105"
[   891.760] (**) Option "xkb_layout" "us,il"
[   891.760] (**) Option "xkb_variant" ","
[   891.760] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[   891.761] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[   891.761] (II) No input driver/identifier specified (ignoring)
[   891.761] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   891.761] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   891.761] (**) Sleep Button: always reports core events
[   891.761] (**) Sleep Button: Device: "/dev/input/event1"
[   891.792] (II) Sleep Button: Found keys
[   891.792] (II) Sleep Button: Configuring as keyboard
[   891.792] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[   891.792] (**) Option "xkb_rules" "evdev"
[   891.792] (**) Option "xkb_model" "pc105"
[   891.792] (**) Option "xkb_layout" "us,il"
[   891.792] (**) Option "xkb_variant" ","
[   891.792] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[   891.800] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[   891.800] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   891.801] (**) AT Translated Set 2 keyboard: always reports core events
[   891.801] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[   891.824] (II) AT Translated Set 2 keyboard: Found keys
[   891.824] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   891.824] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   891.824] (**) Option "xkb_rules" "evdev"
[   891.824] (**) Option "xkb_model" "pc105"
[   891.824] (**) Option "xkb_layout" "us,il"
[   891.824] (**) Option "xkb_variant" ","
[   891.824] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[   891.825] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[   891.825] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   891.825] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   891.825] (II) LoadModule: "synaptics"
[   891.825] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   891.826] (II) Module synaptics: vendor="X.Org Foundation"
[   891.826] 	compiled for 1.9.0, module version = 1.2.2
[   891.826] 	Module class: X.Org XInput Driver
[   891.826] 	ABI class: X.Org XInput driver, version 11.0
[   891.826] (II) Synaptics touchpad driver version 1.2.2
[   891.826] (**) Option "Device" "/dev/input/event7"
[   891.985] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5692
[   891.985] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4680
[   891.985] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   891.985] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[   891.985] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[   892.113] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   892.113] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   892.177] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[   892.177] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   892.177] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[   892.177] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   892.177] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   892.273] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   892.273] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   892.273] (II) No input driver/identifier specified (ignoring)
[   940.498] (II) UnloadModule: "synaptics"
[   940.498] (II) AT Translated Set 2 keyboard: Close
[   940.498] (II) UnloadModule: "evdev"
[   940.499] (II) Sleep Button: Close
[   940.499] (II) UnloadModule: "evdev"
[   940.499] (II) Power Button: Close
[   940.499] (II) UnloadModule: "evdev"
[   940.499] (II) Video Bus: Close
[   940.499] (II) UnloadModule: "evdev"
[   940.499] (II) Video Bus: Close
[   940.499] (II) UnloadModule: "evdev"
[   940.499] (II) Power Button: Close
[   940.499] (II) UnloadModule: "evdev"
[   940.521]  ddxSigGiveUp: Closing log

``` 

i am also attaching my xorg.conf.. maybe it will help:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.06  (buildmeister@builder101)  Mon Sep 13 07:06:38 PDT 2010

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
    #VendorName     "Unknown"
    #ModelName      "Unknown"
Option "DPMS"
#HorizSync 130-167
#VertRefresh 150-175    
 Modeline "1366x768"   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync 
 Modeline "1360x768"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync 
 Modeline "1360x768"   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync
 Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync 
 Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync 
 Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
 Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Busid "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    	DefaultDepth 24
	SubSection "Display"
		Depth     8
		Modes     "1366x768"
	EndSubSection
	SubSection "Display"
		Depth     16
Modes     "1366x768"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes     "1366x768" "1024x768"
	EndSubSection

EndSection

```

what should we attempt next?

thanks,
Shlomi

---

### Post by BicyclerBoy on 2011-05-06
I think that your hardware is confusing the nvidia driver...it thinks you have a VGA connected not an internal LDVS or DFP panel..

You need to find out more about the hardware..I think you may have hybrid/optimus type graphics..
With Optimus the discrete GPU can output into the integrated graphics framebuffer or the discrete can be turned off.

There are a couple of variations of this. One sort of works with linux by using vgaswitcharoo.

You may be able to force a setting in the bios to make your laptop appear as normal discrete graphics (nvidia) or chipset/i3-i5 only...

Is there anything in the output from:
dmesg | more
related to fatal server, display not active ?


FYI
When the EDID is not read correctly, the video mode validation fails unless you use the 
Option    "UseEDID"   "False"
you also need to specify the horiz & vertical freq ranges for the monitor
Custom modelines are not normally needed as the internal video mode list is large..

---

### Post by shlomi on 2011-05-07
Hey man,

Thanks for your detailed response. it actually helped me to find my problem more closely.. it seems that i have (as you diagnosed) an optimus nvidia/intel GPUs, and after searching many threads, it seems that nvidia is not planning to support this.. I joined the hybrid-graphics-linux group, some of the devs there are making good progress, but doesnt seem like there is a simple solution just yet.

again, thanks again for your help!

Shlomi

---

### Post by BicyclerBoy on 2011-05-07
No problem...

Try to find out what form of optimus in in your laptop..
One form/version (IBM thinkpad) has a hardware framebuffer switch/mux & this version can be configured to be plain vanilla discrete graphics in the BIOS.

---


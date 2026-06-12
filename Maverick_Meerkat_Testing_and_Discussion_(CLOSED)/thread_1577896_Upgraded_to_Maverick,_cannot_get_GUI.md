---
title: "Upgraded to Maverick, cannot get GUI"
date: 2010-09-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by skymera on 2010-09-19
Hi,

I upgraded from Lucid to Maverick today through Update Manager, it all went well with zero errors.

Upon reboot I cannot get a GUI, it just hangs.
I must have rebooted 30-40 times now and only once did I get into a working desktop.

I have a 7600GS and reinstalled the nvidia driver but still no luck.

Any ideas?
Been using Ubuntu for nearly 4 years but it's been so long since something has gone wrong this has totally bewildered me!

Thanks all!

---

### Post by VinDSL on 2010-09-19
> **skymera said:**
> Any ideas?Everyone has a different experience -- nothing is set in stone, but...

I'm running a nVidia 7600 GT card.

Everytime there has been a kernel update (in 10.10) I've had to manually re-install the nVidia drivers.  Otherwise, Maverick sits at Plymouth forever.

Different ppl have different fixes for this, but re-installing the nVidia drivers, from a .run file, has worked every time, for me.  This allows the drivers to be built from the new kernel.

Basically, I boot into safemode (at grub) -- kill X-server -- login as root -- install the .run file -- and reboot.

Everything is golden, until the next kernel update...

---

### Post by cariboo on 2010-09-19
Start in recovery mode, after you have logged in, type:

```
startx
```

If X doesn't start. check /var/log/Xorg.0.log, it should tell you what the problem is.

---

### Post by skymera on 2010-09-19
Thanks for replies, i'll download the .run now.

Also X goes to start, but just hangs. 
I'll check logs, cheers.

---

### Post by skymera on 2010-09-19
Hi

Manually installed the .run file, but no luck. Just hangs and is unreponsive to keyboard inputs.

Checked the log but it was empty? I wonder if i disabled logging by mistake and forgot to enable again.

I'll fiddle a little more tomorrow and if I fail to succeed, i'll fresh install.

---

### Post by brydonhunter on 2010-09-19
If you have an ATI card, then we had the same problem.

from the CLI, 

sudo apt-get remove fglrx
sudo reboot

This should load the GUI in standard video driver. The ATI drivers are giving problems right now.

Hope this helps.

---

### Post by ktp on 2010-09-19
> **brydonhunter said:**
> If you have an ATI card, then we had the same problem.

from the CLI, 

sudo apt-get remove fglrx
sudo reboot

This should load the GUI in standard video driver. The ATI drivers are giving problems right now.

Hope this helps.

not going to help here since OP has nvidia.

---

### Post by VinDSL on 2010-09-19
> **ktp said:**
> not going to help here since OP has nvidia.Speaking of nVidia...

I lost my Compiz today.  LoL!

Purged Compiz (et al) and reinstalled.  No luck...

Googled Compiz & nVidia beta, and discovered they released [[COLOR="Red"]260.19.06 (beta)[/COLOR]]("http://www.nvnews.net/vbulletin/showthread.php?t=155137") a few days ago.

Installed it, and all is good again... for a while.

Aren't dev releases fun?!?!?!?

**EDIT**

w00t!  Just checked flash, and I'm able to run hardware acceleration again.

I lost that last week.  Flash would crash if I went fullscreen, with hardware accel enabled...

Anyway, back on topic.  :D

---

### Post by TBerk on 2010-09-19
He is not the only one.

- Nvidia AGP 5200 (I think...) , 

According to last night's investigation, this is the correct Nvidia supplied driver for my hardware:

[http://www.nvidia.com/object/linux-display-ia32-173.14.27-driver.html](http://www.nvidia.com/object/linux-display-ia32-173.14.27-driver.html)

My trouble began from an upgrade from 10.04 to 10.10 beta a week or so ago.

I lost the ability to auto-load the GUI interface, but I found if I chose the second GRUB entry (troubleshooting?, safemode?, something like that) I could get to a point where the system would tell me I don't seem to have any drivers loaded for my hardware and wouldn't I like to run in low graphics mode, at least one time.

(There are other choices too, like reconfigure your hardware, etc.)

Basically I can get the next time I restart to load into a X session, but video playback is choppy, the X-Server for Nvidia doesn't like me and I don't seem to have any hardware specific drivers loaded. (But I used to...)

Just now, as I check System:Administration:Hardware Drivers for specific descriptions to relate, and after a resart of which I didn't exactly document all the magical steps in the correct order, I now have two choices to choose from. I'm going to send this post and respond after a reboot to relate what took place...

---

### Post by ktp on 2010-09-19
> **VinDSL said:**
> Googled Compiz & nVidia beta, and discovered they released [[COLOR="Red"]260.19.06 (beta)[/COLOR]]("http://www.nvnews.net/vbulletin/showthread.php?t=155137") a few days ago.

All is good again... for a while.

Aren't dev releases fun?!?!?!?  :D

x-swat had deb for 260.19.06 the day or day after the release.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

yes dev releases are the best =)

---

### Post by cariboo on 2010-09-19
I know nvidia-current creates an /etc/X11/xorg.conf file, I don't know if the drivers for older graphics cards do. What happens if you type:

```
sudo nvidia-xconfig
```

at the prompt and reboot?

---

### Post by VinDSL on 2010-09-19
> **ktp said:**
> x-swat had deb for 260.19.06 the day or day after the release.[...]X-swat is being ignored, in my update requests.

It's been going on for a week, or so.

I haven't figured out a way to resurrect it yet...

---

### Post by skymera on 2010-09-20
Still no luck.
Just freezes still, even with the manually installed driver.

Going to try removing xorg.conf and then after try and use the beta driver someone posted.

Thanks for all replies! :)

---

### Post by skymera on 2010-09-20
ok managed to narrow it down to the xorg.conf file.

WITHOUT the xorg.conf file, i can get a GUI. Albeit it's unusable and extremely corrupted (see attached image)

If i run nvidia-xconfig and then startx, it freezes.

So, not sure what to do here :(

---

### Post by cariboo on 2010-09-20
What does you /etc/X11/xorg.conf file look like? It almost looks like a frequency issue.

---

### Post by 23dornot23d on 2010-09-20
I am still running the 256.53 .... and everything is working very well in that , with xorg.1.9

[LINK]("http://i56.tinypic.com/2djeyd.jpg")

I had issues too with 256.60 ... 
(if that is the Nvidia driver you are using ... mines a NVIDIA GPU GeForce 9300M GS)

This is all that I have in my xorg.conf ..... if it helps .... 

```


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```

```

[    24.811] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    24.811] X Protocol Version 11, Revision 0
[    24.811] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    24.811] Current Operating System: Linux keith-laptop 2.6.35-22-generic #32-Ubuntu SMP Wed Sep 15 23:39:25 UTC 2010 i686
[    24.811] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=16f79f1e-44c0-407d-a7e7-ef59fac8b4f2 ro quiet splash
[    24.811] Build Date: 16 September 2010  05:39:22PM
[    24.812] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    24.815] Current version of pixman: 0.18.4
[    24.815]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    24.815] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.815] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep 20 19:14:59 2010
[    24.860] (==) Using config file: "/etc/X11/xorg.conf"
[    24.861] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.951] (==) No Layout section.  Using the first Screen section.
[    24.951] (**) |-->Screen "Default Screen" (0)
[    24.951] (**) |   |-->Monitor "<default monitor>"
[    24.951] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    24.951] (**) |   |-->Device "Default Device"
[    24.951] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    24.951] (==) Automatically adding devices
[    24.951] (==) Automatically enabling devices
[    24.983] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.983]     Entry deleted from font path.
[    25.075] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    25.076] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    25.076] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    25.076] (II) Loader magic: 0x81f8e00
[    25.076] (II) Module ABI versions:
[    25.076]     X.Org ANSI C Emulation: 0.4
[    25.076]     X.Org Video Driver: 8.0
[    25.076]     X.Org XInput driver : 11.0
[    25.076]     X.Org Server Extension : 4.0
[    25.077] (--) PCI:*(0:1:0:0) 10de:06e9:1025:0142 rev 161, Mem @ 0xce000000/16777216, 0xd0000000/268435456, 0xcc000000/33554432, I/O @ 0x00002000/128
[    25.077] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    25.077] (II) "extmod" will be loaded by default.
[    25.077] (II) "dbe" will be loaded by default.
[    25.077] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    25.077] (II) "record" will be loaded by default.
[    25.077] (II) "dri" will be loaded by default.
[    25.077] (II) "dri2" will be loaded by default.
[    25.077] (II) LoadModule: "glx"
[    25.157] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    28.976] (II) Module glx: vendor="NVIDIA Corporation"
[    28.976]     compiled for 4.0.2, module version = 1.0.0
[    28.977]     Module class: X.Org Server Extension
[    29.010] (II) NVIDIA GLX Module  256.53  Fri Aug 27 21:28:41 PDT 2010
[    29.010] (II) Loading extension GLX
[    29.010] (II) LoadModule: "extmod"
[    29.055] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    29.065] (II) Module extmod: vendor="X.Org Foundation"
[    29.065]     compiled for 1.9.0, module version = 1.0.0
[    29.065]     Module class: X.Org Server Extension
[    29.065]     ABI class: X.Org Server Extension, version 4.0
[    29.066] (II) Loading extension MIT-SCREEN-SAVER
[    29.066] (II) Loading extension XFree86-VidModeExtension
[    29.066] (II) Loading extension XFree86-DGA
[    29.067] (II) Loading extension DPMS
[    29.067] (II) Loading extension XVideo
[    29.067] (II) Loading extension XVideo-MotionCompensation
[    29.067] (II) Loading extension X-Resource
[    29.067] (II) LoadModule: "dbe"
[    29.068] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    29.069] (II) Module dbe: vendor="X.Org Foundation"
[    29.070]     compiled for 1.9.0, module version = 1.0.0
[    29.070]     Module class: X.Org Server Extension
[    29.070]     ABI class: X.Org Server Extension, version 4.0
[    29.070] (II) Loading extension DOUBLE-BUFFER
[    29.070] (II) LoadModule: "record"
[    29.070] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    29.072] (II) Module record: vendor="X.Org Foundation"
[    29.072]     compiled for 1.9.0, module version = 1.13.0
[    29.072]     Module class: X.Org Server Extension
[    29.072]     ABI class: X.Org Server Extension, version 4.0
[    29.072] (II) Loading extension RECORD
[    29.072] (II) LoadModule: "dri"
[    29.072] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    29.217] (II) Module dri: vendor="X.Org Foundation"
[    29.217]     compiled for 1.9.0, module version = 1.0.0
[    29.217]     ABI class: X.Org Server Extension, version 4.0
[    29.217] (II) Loading extension XFree86-DRI
[    29.217] (II) LoadModule: "dri2"
[    29.217] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    29.220] (II) Module dri2: vendor="X.Org Foundation"
[    29.220]     compiled for 1.9.0, module version = 1.2.0
[    29.220]     ABI class: X.Org Server Extension, version 4.0
[    29.220] (II) Loading extension DRI2
[    29.220] (II) LoadModule: "nvidia"
[    29.221] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    29.267] (II) Module nvidia: vendor="NVIDIA Corporation"
[    29.599]     compiled for 4.0.2, module version = 1.0.0
[    29.599]     Module class: X.Org Video Driver
[    30.198] (II) NVIDIA dlloader X Driver  256.53  Fri Aug 27 21:05:55 PDT 2010
[    30.203] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.203] (++) using VT number 7

[    30.248] (II) Loading sub module "fb"
[    30.248] (II) LoadModule: "fb"
[    30.248] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.252] (II) Module fb: vendor="X.Org Foundation"
[    30.252]     compiled for 1.9.0, module version = 1.0.0
[    30.252]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.253] (II) Loading sub module "wfb"
[    30.253] (II) LoadModule: "wfb"
[    30.253] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.311] (II) Module wfb: vendor="X.Org Foundation"
[    30.311]     compiled for 1.9.0, module version = 1.0.0
[    30.312]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.312] (II) Loading sub module "ramdac"
[    30.312] (II) LoadModule: "ramdac"
[    30.312] (II) Module "ramdac" already built-in
[    30.437] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    30.437] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    30.437] (==) NVIDIA(0): RGB weight 888
[    30.437] (==) NVIDIA(0): Default visual is TrueColor
[    30.437] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.437] (**) NVIDIA(0): Option "NoLogo" "True"
[    30.437] (**) NVIDIA(0): Enabling RENDER acceleration
[    30.437] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    30.437] (II) NVIDIA(0):     enabled.
[    31.685] (II) NVIDIA(0): NVIDIA GPU GeForce 9300M GS (G98) at PCI:1:0:0 (GPU-0)
[    31.685] (--) NVIDIA(0): Memory: 524288 kBytes
[    31.685] (--) NVIDIA(0): VideoBIOS: 62.98.51.00.06
[    31.685] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    31.685] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    31.685] (--) NVIDIA(0): Connected display device(s) on GeForce 9300M GS at PCI:1:0:0:
[    31.685] (--) NVIDIA(0):     AUO (DFP-0)
[    31.685] (--) NVIDIA(0): AUO (DFP-0): 330.0 MHz maximum pixel clock
[    31.685] (--) NVIDIA(0): AUO (DFP-0): Internal Dual Link LVDS
[    31.765] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    31.765] (==) NVIDIA(0): 
[    31.765] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    31.765] (==) NVIDIA(0):     will be used as the requested mode.
[    31.765] (==) NVIDIA(0): 
[    31.765] (II) NVIDIA(0): Validated modes:
[    31.765] (II) NVIDIA(0):     "nvidia-auto-select"
[    31.765] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[    32.826] (--) NVIDIA(0): DPI set to (98, 99); computed from "UseEdidDpi" X config
[    32.841] (--) NVIDIA(0):     option
[    32.841] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    32.841] (--) Depth 24 pixmap format is 32 bpp
[    32.841] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    32.842] (II) NVIDIA(0): Initialized GPU GART.
[    32.850] (II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
[    32.850] (II) NVIDIA(0):     enough to receive ACPI hotkey events.
[    32.850] (II) NVIDIA(0): ACPI brightness change hotkey events enabled.
[    32.852] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    33.216] (II) Loading extension NV-GLX
[    33.472] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    33.528] (==) NVIDIA(0): Disabling shared memory pixmaps
[    33.528] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    33.528] (==) NVIDIA(0): Backing store disabled
[    33.528] (==) NVIDIA(0): Silken mouse enabled
[    33.543] (==) NVIDIA(0): DPMS enabled
[    33.543] (II) Loading extension NV-CONTROL
[    33.544] (II) Loading extension XINERAMA
[    33.544] (II) Loading sub module "dri2"
[    33.544] (II) LoadModule: "dri2"
[    33.544] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    33.544] (II) NVIDIA(0): [DRI2] Setup complete
[    33.544] (==) RandR enabled
[    33.544] (II) Initializing built-in extension Generic Event Extension
[    33.544] (II) Initializing built-in extension SHAPE
[    33.544] (II) Initializing built-in extension MIT-SHM
[    33.544] (II) Initializing built-in extension XInputExtension
[    33.544] (II) Initializing built-in extension XTEST
[    33.544] (II) Initializing built-in extension BIG-REQUESTS
[    33.544] (II) Initializing built-in extension SYNC
[    33.544] (II) Initializing built-in extension XKEYBOARD
[    33.544] (II) Initializing built-in extension XC-MISC
[    33.544] (II) Initializing built-in extension SECURITY
[    33.544] (II) Initializing built-in extension XINERAMA
[    33.544] (II) Initializing built-in extension XFIXES
[    33.544] (II) Initializing built-in extension RENDER
[    33.544] (II) Initializing built-in extension RANDR
[    33.544] (II) Initializing built-in extension COMPOSITE
[    33.544] (II) Initializing built-in extension DAMAGE
[    33.544] (II) Initializing built-in extension GESTURE
[    33.545] (II) Initializing extension GLX
[    33.764] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    33.809] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    33.809] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.809] (II) LoadModule: "evdev"
[    33.809] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.840] (II) Module evdev: vendor="X.Org Foundation"
[    33.840]     compiled for 1.9.0, module version = 2.3.2
[    33.840]     Module class: X.Org XInput Driver
[    33.840]     ABI class: X.Org XInput driver, version 11.0
[    33.840] (**) Power Button: always reports core events
[    33.840] (**) Power Button: Device: "/dev/input/event3"
[    33.852] (II) Power Button: Found keys
[    33.852] (II) Power Button: Configuring as keyboard
[    33.852] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    33.852] (**) Option "xkb_rules" "evdev"
[    33.852] (**) Option "xkb_model" "pc105"
[    33.852] (**) Option "xkb_layout" "gb"
[    33.854] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    33.877] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    33.877] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    33.877] (**) Video Bus: always reports core events
[    33.877] (**) Video Bus: Device: "/dev/input/event5"
[    33.889] (II) Video Bus: Found keys
[    33.889] (II) Video Bus: Configuring as keyboard
[    33.889] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    33.889] (**) Option "xkb_rules" "evdev"
[    33.889] (**) Option "xkb_model" "pc105"
[    33.889] (**) Option "xkb_layout" "gb"
[    33.890] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    33.890] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.890] (**) Power Button: always reports core events
[    33.890] (**) Power Button: Device: "/dev/input/event1"
[    33.901] (II) Power Button: Found keys
[    33.901] (II) Power Button: Configuring as keyboard
[    33.901] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    33.901] (**) Option "xkb_rules" "evdev"
[    33.901] (**) Option "xkb_model" "pc105"
[    33.901] (**) Option "xkb_layout" "gb"
[    33.901] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    33.901] (II) No input driver/identifier specified (ignoring)
[    33.902] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    33.902] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    33.902] (**) Sleep Button: always reports core events
[    33.902] (**) Sleep Button: Device: "/dev/input/event2"
[    33.913] (II) Sleep Button: Found keys
[    33.913] (II) Sleep Button: Configuring as keyboard
[    33.913] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    33.913] (**) Option "xkb_rules" "evdev"
[    33.913] (**) Option "xkb_model" "pc105"
[    33.913] (**) Option "xkb_layout" "gb"
[    33.917] (II) config/udev: Adding input device Acer Crystal Eye webcam (/dev/input/event9)
[    33.917] (**) Acer Crystal Eye webcam: Applying InputClass "evdev keyboard catchall"
[    33.917] (**) Acer Crystal Eye webcam: always reports core events
[    33.917] (**) Acer Crystal Eye webcam: Device: "/dev/input/event9"
[    33.929] (II) Acer Crystal Eye webcam: Found keys
[    33.929] (II) Acer Crystal Eye webcam: Configuring as keyboard
[    33.929] (II) XINPUT: Adding extended input device "Acer Crystal Eye webcam" (type: KEYBOARD)
[    33.929] (**) Option "xkb_rules" "evdev"
[    33.929] (**) Option "xkb_model" "pc105"
[    33.929] (**) Option "xkb_layout" "gb"
[    33.932] (II) config/udev: Adding input device CHESEN USB Keyboard (/dev/input/event6)
[    33.932] (**) CHESEN USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    33.932] (**) CHESEN USB Keyboard: always reports core events
[    33.932] (**) CHESEN USB Keyboard: Device: "/dev/input/event6"
[    33.941] (II) CHESEN USB Keyboard: Found keys
[    33.941] (II) CHESEN USB Keyboard: Configuring as keyboard
[    33.941] (II) XINPUT: Adding extended input device "CHESEN USB Keyboard" (type: KEYBOARD)
[    33.941] (**) Option "xkb_rules" "evdev"
[    33.941] (**) Option "xkb_model" "pc105"
[    33.941] (**) Option "xkb_layout" "gb"
[    33.941] (II) config/udev: Adding input device CHESEN USB Keyboard (/dev/input/event7)
[    33.941] (**) CHESEN USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    33.941] (**) CHESEN USB Keyboard: always reports core events
[    33.941] (**) CHESEN USB Keyboard: Device: "/dev/input/event7"
[    33.949] (II) CHESEN USB Keyboard: Found keys
[    33.949] (II) CHESEN USB Keyboard: Configuring as keyboard
[    33.949] (II) XINPUT: Adding extended input device "CHESEN USB Keyboard" (type: KEYBOARD)
[    33.949] (**) Option "xkb_rules" "evdev"
[    33.949] (**) Option "xkb_model" "pc105"
[    33.949] (**) Option "xkb_layout" "gb"
[    33.950] (II) config/udev: Adding input device HID 04d9:048e (/dev/input/event8)
[    33.950] (**) HID 04d9:048e: Applying InputClass "evdev pointer catchall"
[    33.950] (**) HID 04d9:048e: always reports core events
[    33.950] (**) HID 04d9:048e: Device: "/dev/input/event8"
[    33.961] (II) HID 04d9:048e: Found 9 mouse buttons
[    33.961] (II) HID 04d9:048e: Found scroll wheel(s)
[    33.961] (II) HID 04d9:048e: Found relative axes
[    33.961] (II) HID 04d9:048e: Found x and y relative axes
[    33.961] (II) HID 04d9:048e: Configuring as mouse
[    33.961] (**) HID 04d9:048e: YAxisMapping: buttons 4 and 5
[    33.961] (**) HID 04d9:048e: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    33.961] (II) XINPUT: Adding extended input device "HID 04d9:048e" (type: MOUSE)
[    33.961] (II) HID 04d9:048e: initialized for relative axes.
[    33.961] (II) config/udev: Adding input device HID 04d9:048e (/dev/input/mouse0)
[    33.961] (II) No input driver/identifier specified (ignoring)
[    33.964] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    33.965] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    33.965] (**) AT Translated Set 2 keyboard: always reports core events
[    33.965] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    33.977] (II) AT Translated Set 2 keyboard: Found keys
[    33.977] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    33.977] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    33.977] (**) Option "xkb_rules" "evdev"
[    33.977] (**) Option "xkb_model" "pc105"
[    33.977] (**) Option "xkb_layout" "gb"
[    33.977] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event10)
[    33.977] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    33.977] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    33.977] (II) LoadModule: "synaptics"
[    33.978] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    33.981] (II) Module synaptics: vendor="X.Org Foundation"
[    33.982]     compiled for 1.9.0, module version = 1.2.2
[    33.982]     Module class: X.Org XInput Driver
[    33.982]     ABI class: X.Org XInput driver, version 11.0
[    33.982] (II) Synaptics touchpad driver version 1.2.2
[    33.982] (**) Option "Device" "/dev/input/event10"
[    34.049] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    34.049] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    34.049] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    34.049] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    34.049] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[    34.060] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    34.060] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    34.072] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    34.072] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    34.072] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    34.072] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    34.072] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    34.108] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    34.108] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    34.108] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    34.108] (II) Synaptics touchpad driver version 1.2.2
[    34.765] SynPS/2 Synaptics TouchPad no synaptics event device found
[    34.765] (**) Option "Device" "/dev/input/mouse1"
[    34.793] Query no Synaptics: 6003C8
[    34.793] (--) SynPS/2 Synaptics TouchPad: no supported touchpad found
[    34.793] (EE) SynPS/2 Synaptics TouchPad Unable to query/initialize Synaptics hardware.
[    34.817] (EE) PreInit failed for input device "SynPS/2 Synaptics TouchPad"
[    34.817] (II) UnloadModule: "synaptics"
[  6349.117] (II) config/udev: removing device CHESEN USB Keyboard
[  6349.118] (II) CHESEN USB Keyboard: Close
[  6349.118] (II) UnloadModule: "evdev"
[  6349.141] (II) config/udev: removing device CHESEN USB Keyboard
[  6349.142] (II) CHESEN USB Keyboard: Close
[  6349.142] (II) UnloadModule: "evdev"
[  6349.469] (II) config/udev: Adding input device CHESEN USB Keyboard (/dev/input/event6)
[  6349.469] (**) CHESEN USB Keyboard: Applying InputClass "evdev keyboard catchall"
[  6349.469] (**) CHESEN USB Keyboard: always reports core events
[  6349.469] (**) CHESEN USB Keyboard: Device: "/dev/input/event6"
[  6349.480] (II) CHESEN USB Keyboard: Found keys
[  6349.480] (II) CHESEN USB Keyboard: Configuring as keyboard
[  6349.480] (II) XINPUT: Adding extended input device "CHESEN USB Keyboard" (type: KEYBOARD)
[  6349.480] (**) Option "xkb_rules" "evdev"
[  6349.480] (**) Option "xkb_model" "pc105"
[  6349.480] (**) Option "xkb_layout" "gb"
[  6349.481] (II) config/udev: Adding input device CHESEN USB Keyboard (/dev/input/event7)
[  6349.481] (**) CHESEN USB Keyboard: Applying InputClass "evdev keyboard catchall"
[  6349.481] (**) CHESEN USB Keyboard: always reports core events
[  6349.481] (**) CHESEN USB Keyboard: Device: "/dev/input/event7"
[  6349.492] (II) CHESEN USB Keyboard: Found keys
[  6349.492] (II) CHESEN USB Keyboard: Configuring as keyboard
[  6349.492] (II) XINPUT: Adding extended input device "CHESEN USB Keyboard" (type: KEYBOARD)
[  6349.492] (**) Option "xkb_rules" "evdev"
[  6349.492] (**) Option "xkb_model" "pc105"
[  6349.492] (**) Option "xkb_layout" "gb"


```Hope this helps in some way ....

---

### Post by purdurnr on 2010-09-20
Great post.  I ran this and my ATI/AMD 690 Graphics issue is gone in 10.10.  Able to boot successfully.

---

### Post by ktp on 2010-09-21
> **purdurnr said:**
> Great post.  I ran this and my ATI/AMD 690 Graphics issue is gone in 10.10.  Able to boot successfully.

wait what...adding "nvidia" xorg.conf fixed your ATI?

---

### Post by TBerk on 2010-09-21
> **ktp said:**
> wait what...adding "nvidia" xorg.conf fixed your ATI?

Yeah, I thought that sounded strange also.

I have a current thread going (although my NVidia card is an older model, still) it might help your (OP) situation.  It begins NVidia and contains the words root and canal...

TBerk
who doesn't have a handy URL to post quite yet...

---

### Post by skymera on 2010-09-22
With this in my Xorg.conf

```
Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```

I got a GUI when in single mode by typing "startx". After a reboot, starting up as normal, it froze again and i can#t get a GUI in single mode either anymore.

Hm.

---

### Post by skymera on 2010-09-29
Couldn't find a cure that worked for more than one or two reboots.

Resorted to fresh install, thanks anyway all! =)

---


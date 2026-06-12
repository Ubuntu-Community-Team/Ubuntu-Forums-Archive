---
title: "Unity won't start after fglrx install with Intel video card"
date: 2014-03-22
forum: Multimedia Software
---

### Post by qianian2 on 2014-03-22
To remedy dropped frames in movie playback I installed fglrx, then found out it stopped Unity from starting. I've tried uninstalling it but still can't recover Unity after checking CompizConfig, updating, and restarting many times. 

[EDIT 14:10] I also installed nvidia-current, nvidia-304, and nvidia-settings the previous day, though I didn't notice Unity breaking until after fglrx was installed. 

I see the bug and suggested workaround [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1069199](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1069199). I am not sure I've removed the fglrx package completely. I'm getting errors like this:

$ fmit
Free Music Instrument Tuner version 0.99.2 built at Jan  9 2012 16:34:42
Install directory '/usr'
Xlib:  extension "GLX" missing on display ":0.0".
freeglut (fmit): OpenGL GLX extension not supported by display ':0.0'

There doesn't seem to be an uninstall.sh. Here are all the files I can find in /usr/share:

$ ls -R /usr/share | grep fglrx
fglrx
fglrx-driver.desktop
source_fglrx-installer.py
fglrx-amdcccle-updates
fglrx-updates
fglrx-updates-dev
/usr/share/doc/fglrx-amdcccle-updates:
/usr/share/doc/fglrx-updates:
/usr/share/doc/fglrx-updates/articles:
/usr/share/doc/fglrx-updates/examples:
/usr/share/doc/fglrx-updates/examples/etc:
/usr/share/doc/fglrx-updates/examples/etc/acpi:
/usr/share/doc/fglrx-updates/examples/etc/acpi/events:
/usr/share/doc/fglrx-updates/examples/etc/init.d:
/usr/share/doc/fglrx-updates/user-manual:
/usr/share/doc/fglrx-updates-dev:
/usr/share/fglrx:
fglrx-updates.grub-gfxpayload
fglrx.py
fglrx-amdcccle-updates
fglrx-updates
fglrx-updates-dev


$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)

On 12.04

Any help would be greatly appreciated -- I'm still learning.

---

### Post by ajgreeny on 2014-03-22
You should not need to install any extra drivers for that Intel chipset of you VGA graphic card; it should be fully supported by the kernel in 12.04.

In any case there is absolutely no need to install any nvidia drivers unless you have an nvidia card, or fglrx unless you have a new AMD card of the 5000 upwards series of cards, so both of those drivers were likely to do nothing, or as a worst case, just cause you extra problems.

I suggest you purge fglrx with synaptic, using the "Remove completely" option, and the same for any nvidia packages you can find installed.  I can't now remember if synaptic is included in ubuntu 12.04, but it is always something I add if it's not part of the default as it is so much better a package manager than the software-centre, and I would recommend you do the same if you don't already have it available to you.  Synaptic allows you to search packages a lot easier than software-centre and see clearly what is and isn't installed, and also gives you a clear warning about packages that will alo be removed when you uninstall something.

You don't mention the rest of your hardware, but I begin to wonder if you would do better with a different OS using a lower resource dependent desktop, such as Xubuntu with xfce.

---

### Post by Yellow Pasque on 2014-03-22
Most likely, you did not completely remove one of the proprietary drivers and X is still using AMD's (or nvidia's) custom version of libglx, which breaks 3D for open-source drivers.

Post the contents of /var/log/Xorg.0.log file (use code tags!).

---

### Post by qianian2 on 2014-03-22
ajgreeny: Movie playback isn't always jerky but I'll look into another OS, thanks.

Temujin:

```
[    10.200] 
X.Org X Server 1.14.5
Release Date: 2013-12-12
[    10.200] X Protocol Version 11, Revision 0
[    10.200] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    10.200] Current Operating System: Linux Stonau 3.11.0-18-generic #32~precise1-Ubuntu SMP Thu Feb 20 17:54:21 UTC 2014 i686
[    10.200] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-18-generic root=UUID=a2720060-831e-4003-ad00-b448a945c9f2 ro quiet splash vt.handoff=7
[    10.200] Build Date: 06 January 2014  01:41:06PM
[    10.200] xorg-server 2:1.14.5-1ubuntu2~saucy1~precise2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    10.200] Current version of pixman: 0.30.2
[    10.200]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    10.200] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    10.200] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 22 15:55:34 2014
[    10.204] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    10.206] (==) No Layout section.  Using the first Screen section.
[    10.206] (==) No screen section available. Using defaults.
[    10.206] (**) |-->Screen "Default Screen Section" (0)
[    10.206] (**) |   |-->Monitor "<default monitor>"
[    10.207] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    10.208] (==) Automatically adding devices
[    10.208] (==) Automatically enabling devices
[    10.208] (==) Automatically adding GPU devices
[    10.208] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    10.208]     Entry deleted from font path.
[    10.208] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    10.208]     Entry deleted from font path.
[    10.208] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    10.208]     Entry deleted from font path.
[    10.208] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    10.208]     Entry deleted from font path.
[    10.208] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    10.208]     Entry deleted from font path.
[    10.208] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    10.208] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    10.208] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    10.209] (II) Loader magic: 0xb7759620
[    10.209] (II) Module ABI versions:
[    10.209]     X.Org ANSI C Emulation: 0.4
[    10.209]     X.Org Video Driver: 14.1
[    10.209]     X.Org XInput driver : 19.1
[    10.209]     X.Org Server Extension : 7.0
[    10.209] (II) xfree86: Adding drm device (/dev/dri/card0)
[    10.213] (--) PCI:*(0:0:2:0) 8086:2a02:17aa:20b5 rev 12, Mem @ 0xf8100000/1048576, 0xe0000000/268435456, I/O @ 0x00001800/8
[    10.213] (--) PCI: (0:0:2:1) 8086:2a03:17aa:20b5 rev 12, Mem @ 0xf8200000/1048576
[    10.213] (II) Open ACPI successful (/var/run/acpid.socket)
[    10.216] Initializing built-in extension Generic Event Extension
[    10.216] Initializing built-in extension SHAPE
[    10.216] Initializing built-in extension MIT-SHM
[    10.216] Initializing built-in extension XInputExtension
[    10.216] Initializing built-in extension XTEST
[    10.216] Initializing built-in extension BIG-REQUESTS
[    10.216] Initializing built-in extension SYNC
[    10.216] Initializing built-in extension XKEYBOARD
[    10.216] Initializing built-in extension XC-MISC
[    10.216] Initializing built-in extension SECURITY
[    10.216] Initializing built-in extension XINERAMA
[    10.216] Initializing built-in extension XFIXES
[    10.216] Initializing built-in extension RENDER
[    10.216] Initializing built-in extension RANDR
[    10.216] Initializing built-in extension COMPOSITE
[    10.216] Initializing built-in extension DAMAGE
[    10.216] Initializing built-in extension MIT-SCREEN-SAVER
[    10.216] Initializing built-in extension DOUBLE-BUFFER
[    10.216] Initializing built-in extension RECORD
[    10.216] Initializing built-in extension DPMS
[    10.217] Initializing built-in extension X-Resource
[    10.217] Initializing built-in extension XVideo
[    10.217] Initializing built-in extension XVideo-MotionCompensation
[    10.220] Initializing built-in extension XFree86-VidModeExtension
[    10.220] Initializing built-in extension XFree86-DGA
[    10.220] Initializing built-in extension XFree86-DRI
[    10.220] Initializing built-in extension DRI2
[    10.220] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    10.220] (II) "glx" will be loaded by default.
[    10.220] (II) LoadModule: "glx"
[    10.226] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    10.519] (II) Module glx: vendor="NVIDIA Corporation"
[    10.519]     compiled for 4.0.2, module version = 1.0.0
[    10.519]     Module class: X.Org Server Extension
[    10.519] (II) NVIDIA GLX Module  304.116  Mon Oct 28 21:03:59 PDT 2013
[    10.519] Loading extension GLX
[    10.519] (==) Matched intel as autoconfigured driver 0
[    10.519] (==) Matched intel as autoconfigured driver 1
[    10.519] (==) Matched vesa as autoconfigured driver 2
[    10.519] (==) Matched modesetting as autoconfigured driver 3
[    10.519] (==) Matched fbdev as autoconfigured driver 4
[    10.519] (==) Assigned the driver to the xf86ConfigLayout
[    10.519] (II) LoadModule: "intel"
[    10.522] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    10.526] (II) Module intel: vendor="X.Org Foundation"
[    10.526]     compiled for 1.14.5, module version = 2.99.904
[    10.526]     Module class: X.Org Video Driver
[    10.527]     ABI class: X.Org Video Driver, version 14.1
[    10.527] (II) LoadModule: "vesa"
[    10.527] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    10.528] (II) Module vesa: vendor="X.Org Foundation"
[    10.528]     compiled for 1.14.5, module version = 2.3.2
[    10.528]     Module class: X.Org Video Driver
[    10.528]     ABI class: X.Org Video Driver, version 14.1
[    10.528] (II) LoadModule: "modesetting"
[    10.528] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    10.529] (II) Module modesetting: vendor="X.Org Foundation"
[    10.529]     compiled for 1.14.5, module version = 0.8.0
[    10.529]     Module class: X.Org Video Driver
[    10.529]     ABI class: X.Org Video Driver, version 14.1
[    10.529] (II) LoadModule: "fbdev"
[    10.529] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    10.530] (II) Module fbdev: vendor="X.Org Foundation"
[    10.530]     compiled for 1.14.5, module version = 0.4.3
[    10.530]     Module class: X.Org Video Driver
[    10.530]     ABI class: X.Org Video Driver, version 14.1
[    10.530] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43, HD Graphics,
    HD Graphics 2000, HD Graphics 3000, HD Graphics 2500,
    HD Graphics 4000, HD Graphics P4000, HD Graphics 4600,
    HD Graphics 5000, HD Graphics P4600/P4700, Iris(TM) Graphics 5100,
    HD Graphics 4400, HD Graphics 4200, Iris(TM) Pro Graphics 5200
[    10.531] (II) VESA: driver for VESA chipsets: vesa
[    10.531] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    10.531] (II) FBDEV: driver for framebuffer: fbdev
[    10.531] (++) using VT number 7

[    10.532] (II) intel(0): SNA compiled: xserver-xorg-video-intel-lts-saucy 2:2.99.904-0ubuntu2.1~precise1 (Timo Aaltonen <tjaalton@ubuntu.com>)
[    10.534] (WW) Falling back to old probe method for vesa
[    10.534] (WW) Falling back to old probe method for modesetting
[    10.534] (WW) Falling back to old probe method for fbdev
[    10.534] (II) Loading sub module "fbdevhw"
[    10.535] (II) LoadModule: "fbdevhw"
[    10.535] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    10.536] (II) Module fbdevhw: vendor="X.Org Foundation"
[    10.536]     compiled for 1.14.5, module version = 0.0.2
[    10.536]     ABI class: X.Org Video Driver, version 14.1
[    10.538] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    10.538] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    10.538] (==) intel(0): RGB weight 888
[    10.538] (==) intel(0): Default visual is TrueColor
[    10.538] (--) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[    10.538] (--) intel(0): CPU: x86, sse2, sse3, ssse3
[    10.538] (**) intel(0): Framebuffer tiled
[    10.538] (**) intel(0): Pixmaps tiled
[    10.538] (**) intel(0): "Tear free" disabled
[    10.538] (**) intel(0): Forcing per-crtc-pixmaps? no
[    10.538] (II) intel(0): Output LVDS1 has no monitor section
[    10.539] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')
[    10.539] (II) intel(0): Output VGA1 has no monitor section
[    10.539] (II) intel(0): Output TV1 has no monitor section
[    10.539] (II) intel(0): Output VIRTUAL1 has no monitor section
[    10.539] (--) intel(0): Output LVDS1 using initial mode 1280x800 on pipe 0
[    10.539] (==) intel(0): DPI set to (96, 96)
[    10.539] (II) Loading sub module "dri2"
[    10.539] (II) LoadModule: "dri2"
[    10.539] (II) Module "dri2" already built-in
[    10.539] (II) UnloadModule: "vesa"
[    10.539] (II) Unloading vesa
[    10.539] (II) UnloadModule: "modesetting"
[    10.539] (II) Unloading modesetting
[    10.539] (II) UnloadModule: "fbdev"
[    10.539] (II) Unloading fbdev
[    10.540] (II) UnloadSubModule: "fbdevhw"
[    10.540] (II) Unloading fbdevhw
[    10.540] (==) Depth 24 pixmap format is 32 bpp
[    10.547] (II) intel(0): SNA initialized with Broadwater (gen4) backend
[    10.547] (==) intel(0): Backing store disabled
[    10.547] (==) intel(0): Silken mouse enabled
[    10.547] (II) intel(0): HW Cursor enabled
[    10.547] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    10.549] (==) intel(0): DPMS enabled
[    10.549] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    10.549] (II) intel(0): [DRI2] Setup complete
[    10.549] (II) intel(0): [DRI2]   DRI driver: i965
[    10.549] (II) intel(0): direct rendering: DRI2 Enabled
[    10.549] (==) intel(0): hotplug detection: "enabled"
[    10.549] (--) RandR disabled
[    10.572] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    10.580] (II) intel(0): switch to mode 1280x800@60.0 on pipe 0 using LVDS1, position (0, 0), rotation normal
[    10.593] (II) intel(0): Setting screen physical size to 338 x 211
[    10.723] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    10.730] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    10.730] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    10.730] (II) LoadModule: "evdev"
[    10.731] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.736] (II) Module evdev: vendor="X.Org Foundation"
[    10.736]     compiled for 1.14.5, module version = 2.7.3
[    10.736]     Module class: X.Org XInput Driver
[    10.736]     ABI class: X.Org XInput driver, version 19.1
[    10.736] (II) Using input driver 'evdev' for 'Power Button'
[    10.736] (**) Power Button: always reports core events
[    10.736] (**) evdev: Power Button: Device: "/dev/input/event2"
[    10.736] (--) evdev: Power Button: Vendor 0 Product 0x1
[    10.736] (--) evdev: Power Button: Found keys
[    10.736] (II) evdev: Power Button: Configuring as keyboard
[    10.736] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    10.736] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    10.736] (**) Option "xkb_rules" "evdev"
[    10.736] (**) Option "xkb_model" "pc105"
[    10.736] (**) Option "xkb_layout" "us"
[    10.737] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    10.737] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    10.737] (II) Using input driver 'evdev' for 'Video Bus'
[    10.737] (**) Video Bus: always reports core events
[    10.737] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    10.737] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    10.737] (--) evdev: Video Bus: Found keys
[    10.737] (II) evdev: Video Bus: Configuring as keyboard
[    10.737] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6/event6"
[    10.737] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    10.737] (**) Option "xkb_rules" "evdev"
[    10.737] (**) Option "xkb_model" "pc105"
[    10.737] (**) Option "xkb_layout" "us"
[    10.738] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    10.738] (II) No input driver specified, ignoring this device.
[    10.738] (II) This device may have been added with another device file.
[    10.739] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    10.739] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    10.739] (II) Using input driver 'evdev' for 'Sleep Button'
[    10.739] (**) Sleep Button: always reports core events
[    10.739] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    10.739] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    10.739] (--) evdev: Sleep Button: Found keys
[    10.739] (II) evdev: Sleep Button: Configuring as keyboard
[    10.739] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    10.739] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    10.739] (**) Option "xkb_rules" "evdev"
[    10.739] (**) Option "xkb_model" "pc105"
[    10.739] (**) Option "xkb_layout" "us"
[    10.740] (II) config/udev: Adding drm device (/dev/dri/card0)
[    10.740] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    10.740] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event7)
[    10.741] (II) No input driver specified, ignoring this device.
[    10.741] (II) This device may have been added with another device file.
[    10.741] (II) config/udev: Adding input device HDA Intel Dock Mic (/dev/input/event8)
[    10.741] (II) No input driver specified, ignoring this device.
[    10.741] (II) This device may have been added with another device file.
[    10.741] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event9)
[    10.741] (II) No input driver specified, ignoring this device.
[    10.741] (II) This device may have been added with another device file.
[    10.742] (II) config/udev: Adding input device Logitech USB Trackball (/dev/input/event4)
[    10.742] (**) Logitech USB Trackball: Applying InputClass "evdev pointer catchall"
[    10.742] (II) Using input driver 'evdev' for 'Logitech USB Trackball'
[    10.742] (**) Logitech USB Trackball: always reports core events
[    10.742] (**) evdev: Logitech USB Trackball: Device: "/dev/input/event4"
[    10.742] (--) evdev: Logitech USB Trackball: Vendor 0x46d Product 0xc408
[    10.742] (--) evdev: Logitech USB Trackball: Found 9 mouse buttons
[    10.742] (--) evdev: Logitech USB Trackball: Found relative axes
[    10.742] (--) evdev: Logitech USB Trackball: Found x and y relative axes
[    10.742] (II) evdev: Logitech USB Trackball: Configuring as mouse
[    10.742] (**) evdev: Logitech USB Trackball: YAxisMapping: buttons 4 and 5
[    10.742] (**) evdev: Logitech USB Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    10.742] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input4/event4"
[    10.742] (II) XINPUT: Adding extended input device "Logitech USB Trackball" (type: MOUSE, id 9)
[    10.743] (II) evdev: Logitech USB Trackball: initialized for relative axes.
[    10.743] (**) Logitech USB Trackball: (accel) keeping acceleration scheme 1
[    10.743] (**) Logitech USB Trackball: (accel) acceleration profile 0
[    10.743] (**) Logitech USB Trackball: (accel) acceleration factor: 2.000
[    10.743] (**) Logitech USB Trackball: (accel) acceleration threshold: 4
[    10.743] (II) config/udev: Adding input device Logitech USB Trackball (/dev/input/mouse0)
[    10.743] (II) No input driver specified, ignoring this device.
[    10.743] (II) This device may have been added with another device file.
[    10.744] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    10.744] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    10.744] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    10.744] (**) AT Translated Set 2 keyboard: always reports core events
[    10.744] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    10.744] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    10.744] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    10.744] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    10.744] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    10.744] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    10.744] (**) Option "xkb_rules" "evdev"
[    10.744] (**) Option "xkb_model" "pc105"
[    10.744] (**) Option "xkb_layout" "us"
[    10.745] (II) config/udev: Adding input device DualPoint Stick (/dev/input/event10)
[    10.745] (**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
[    10.745] (**) DualPoint Stick: Applying InputClass "trackpoint catchall"
[    10.745] (II) Using input driver 'evdev' for 'DualPoint Stick'
[    10.745] (**) DualPoint Stick: always reports core events
[    10.745] (**) evdev: DualPoint Stick: Device: "/dev/input/event10"
[    10.745] (--) evdev: DualPoint Stick: Vendor 0x2 Product 0x8
[    10.745] (--) evdev: DualPoint Stick: Found 3 mouse buttons
[    10.745] (--) evdev: DualPoint Stick: Found relative axes
[    10.745] (--) evdev: DualPoint Stick: Found x and y relative axes
[    10.745] (II) evdev: DualPoint Stick: Configuring as mouse
[    10.745] (**) Option "Emulate3Buttons" "true"
[    10.746] (**) Option "EmulateWheel" "true"
[    10.746] (**) Option "EmulateWheelButton" "2"
[    10.746] (**) Option "YAxisMapping" "4 5"
[    10.746] (**) evdev: DualPoint Stick: YAxisMapping: buttons 4 and 5
[    10.746] (**) Option "XAxisMapping" "6 7"
[    10.746] (**) evdev: DualPoint Stick: XAxisMapping: buttons 6 and 7
[    10.746] (**) evdev: DualPoint Stick: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    10.746] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input10/event10"
[    10.746] (II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE, id 11)
[    10.746] (II) evdev: DualPoint Stick: initialized for relative axes.
[    10.746] (**) DualPoint Stick: (accel) keeping acceleration scheme 1
[    10.746] (**) DualPoint Stick: (accel) acceleration profile 0
[    10.746] (**) DualPoint Stick: (accel) acceleration factor: 2.000
[    10.746] (**) DualPoint Stick: (accel) acceleration threshold: 4
[    10.746] (II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse1)
[    10.746] (II) No input driver specified, ignoring this device.
[    10.746] (II) This device may have been added with another device file.
[    10.747] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event11)
[    10.747] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
[    10.747] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
[    10.747] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "Default clickpad buttons"
[    10.747] (II) LoadModule: "synaptics"
[    10.748] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    10.752] (II) Module synaptics: vendor="X.Org Foundation"
[    10.752]     compiled for 1.14.5, module version = 1.7.1
[    10.752]     Module class: X.Org XInput Driver
[    10.752]     ABI class: X.Org XInput driver, version 19.1
[    10.752] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS DualPoint TouchPad'
[    10.752] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    10.752] (**) Option "Device" "/dev/input/event11"
[    10.828] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 1023 (res 0)
[    10.828] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 767 (res 0)
[    10.828] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
[    10.828] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: device does not report finger width.
[    10.828] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle
[    10.828] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: Vendor 0x2 Product 0x8
[    10.828] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: invalid finger width range.  defaulting to 0 - 15
[    10.828] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    10.828] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    10.880] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input11/event11"
[    10.880] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD, id 12)
[    10.880] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    10.880] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MaxSpeed is now 1.75
[    10.880] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) AccelFactor is now 0.156
[    10.880] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
[    10.880] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 1
[    10.880] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
[    10.880] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
[    10.880] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    10.881] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse2)
[    10.881] (**) AlpsPS/2 ALPS DualPoint TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    10.884] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event5)
[    10.884] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[    10.884] (II) Using input driver 'evdev' for 'ThinkPad Extra Buttons'
[    10.884] (**) ThinkPad Extra Buttons: always reports core events
[    10.884] (**) evdev: ThinkPad Extra Buttons: Device: "/dev/input/event5"
[    10.885] (--) evdev: ThinkPad Extra Buttons: Vendor 0x17aa Product 0x5054
[    10.885] (--) evdev: ThinkPad Extra Buttons: Found keys
[    10.885] (II) evdev: ThinkPad Extra Buttons: Configuring as keyboard
[    10.885] (**) Option "config_info" "udev:/sys/devices/platform/thinkpad_acpi/input/input5/event5"
[    10.885] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD, id 13)
[    10.885] (**) Option "xkb_rules" "evdev"
[    10.885] (**) Option "xkb_model" "pc105"
[    10.885] (**) Option "xkb_layout" "us"
[    11.989] (II) intel(0): EDID vendor "LEN", prod id 16464
[    11.989] (II) intel(0): Printing DDC gathered Modelines:
[    11.989] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[    11.989] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[    12.858] (II) XKB: reuse xkmfile /var/lib/xkb/server-06D88AAF5356C6CF875D73CED515513D3FEA00ED.xkm
[    19.187] (II) intel(0): EDID vendor "LEN", prod id 16464
[    19.187] (II) intel(0): Printing DDC gathered Modelines:
[    19.187] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[    19.187] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[    33.649] (II) intel(0): EDID vendor "LEN", prod id 16464
[    33.649] (II) intel(0): Printing DDC gathered Modelines:
[    33.649] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[    33.649] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[   116.860] (II) XKB: reuse xkmfile /var/lib/xkb/server-06D88AAF5356C6CF875D73CED515513D3FEA00ED.xkm
[  1857.592] (II) XKB: reuse xkmfile /var/lib/xkb/server-06D88AAF5356C6CF875D73CED515513D3FEA00ED.xkm
[  1896.158] (II) XKB: reuse xkmfile /var/lib/xkb/server-06D88AAF5356C6CF875D73CED515513D3FEA00ED.xkm
```

---

### Post by qianian2 on 2014-03-22
Complete removal of all nvidia and fglrx packages with Synaptic worked. Thanks ajgreeny!

---

### Post by Yellow Pasque on 2014-03-22
Yeah, one of the nvidia packages borked it:
```
[    10.226] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    10.519] (II) Module glx: vendor="NVIDIA Corporation"
[    10.519]     compiled for 4.0.2, module version = 1.0.0
```

Be more careful in the future..

---


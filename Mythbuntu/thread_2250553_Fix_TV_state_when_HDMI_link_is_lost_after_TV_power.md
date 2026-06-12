---
title: "Fix TV state when HDMI link is lost after TV power off/on"
date: 2014-10-29
forum: Mythbuntu
---

### Post by AlecJ on 2014-10-29
Have had to apply this fix just recently, after an update?

```
For people on mythbuntu who encounter this with a mceusb remote, here's how i'm working around it:

1) Save this file to /home/user/fix_tv_state.sh and make it executable
==============================
#!/bin/sh
#Fix TV state when HDMI link is lost.
#By Mario Limonciello <email address hidden>


OUTPUT="HDMI-0"
BAD_MODE="1280x720"
GOOD_MODE="1920x1080"


for MODE in $BAD_MODE $GOOD_MODE; do
 DISPLAY=:0 xrandr --output $OUTPUT --mode $MODE
 sleep 2
done
==============================


2) Create ~/.lirc/irexec and put these contents:
==============================
begin
     remote = mceusb
     button = KEY_POWER
     prog = irexec
     repeat = 0
     config = /home/user/fix_tv_state.sh
end
==============================


3) Add to ~/.lircrc this line:
include ~/.lirc/irexec


4) Restart machine, lightdm or log out/in


Now power button on your mceusb remote will fix the HTPC video output state.
```

My question is WHY? it worked before.
AND has this been fixed yet?

---

### Post by dannyboy79 on 2014-10-29
The X server is finicky at times, if a connected display is off X server may decide it won't start because it doesn't think a display is connected. This script forces X server to display by using RandR. If I were you I would look into using a "connectedmonitor" option in your Xorg.conf file. If you use that along with some other options your X server will always display whether the tv is on or not. Here's a thread discussing it: 
[http://www.phoronix.com/forums/showthread.php?26358-Forcing-a-resolution-when-no-TV-is-connected](http://www.phoronix.com/forums/showthread.php?26358-Forcing-a-resolution-when-no-TV-is-connected)
As to why it occurred to you recently I'm not sure and I'm not sure how it would be fixed unless some update modified your Xorg.conf file which I doubt mythbuntu does.

---

### Post by AlecJ on 2014-10-29
I believe it was a Nvidia update that cause the problem.

Thanks I will go look at that thread

---

### Post by Mike_Brown on 2014-10-29
I have the same problem, but am a Linux/Ubuntu noobi.

Please explain how to get to the Xorg.config file and how to modify that file.

Thanks

---

### Post by AlecJ on 2014-10-29
Open a terminal on your mythbox

you can use nano to edit the file or I like mousepad as a graphical notepad type thing.

install mousepad with 
```
sudo apt-get install mousepad
```

then open the file with 
```
sudo mousepad /etc/X11/xorg.conf
```


or
```
sudo nano /etc/X11/xorg.conf
```

However this has not fixed my problem.

I still have to use the power button

---

### Post by dannyboy79 on 2014-10-29
> **AlecJ said:**
> 
However this has not fixed my problem.

I still have to use the power buttonif you failed to properly identify what your tv shows up as then of course it wouldn't work. i can help you set this up correctly but i need you to ensure your tv is on, boot up your system and hopefully eveything is working, if so, please copy the contents of /var/log/Xorg.0.log to pastebin and then paste the link here. also post your xorg.conf as well

---

### Post by AlecJ on 2014-10-29
[COLOR=#000000]The xorg.conf file was like this

[/COLOR]```


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection


Section "Extensions"
    Option    "Composite"    "Disable"
EndSection


Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "DPI"    "100x100"
    Option    "NoLogo"    "1"
EndSection



```[COLOR=#000000]

but I used nvidia-setting to fill it in to the file file you see at the bottom

/var/log/Xorg.0.log[/COLOR]

```
[    19.924] X.Org X Server 1.11.3
Release Date: 2011-12-16
[    19.925] X Protocol Version 11, Revision 0
[    19.925] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    19.925] Current Operating System: Linux alectv 3.2.0-70-generic #105-Ubuntu SMP Wed Sep 24 19:49:16 UTC 2014 x86_64
[    19.925] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-70-generic root=UUID=a642cc20-2157-4e48-ad6c-1be3460ec138 ro quiet splash
[    19.925] Build Date: 16 October 2013  04:41:23PM
[    19.925] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see http://www.ubuntu.com/support) 
[    19.925] Current version of pixman: 0.30.2
[    19.925]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    19.925] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.925] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 29 16:42:57 2014
[    19.925] (==) Using config file: "/etc/X11/xorg.conf"
[    19.925] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.925] (==) ServerLayout "Layout0"
[    19.925] (**) |-->Screen "Screen0" (0)
[    19.925] (**) |   |-->Monitor "Monitor0"
[    19.925] (**) |   |-->Device "Device0"
[    19.926] (**) |-->Input Device "Keyboard0"
[    19.926] (**) |-->Input Device "Mouse0"
[    19.926] (**) Option "Xinerama" "0"
[    19.926] (==) Automatically adding devices
[    19.926] (==) Automatically enabling devices
[    19.926] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.926]     Entry deleted from font path.
[    19.926] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.926]     Entry deleted from font path.
[    19.926] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.926]     Entry deleted from font path.
[    19.926] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.926]     Entry deleted from font path.
[    19.926] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.926]     Entry deleted from font path.
[    19.926] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    19.926] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.926] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    19.926] (WW) Disabling Keyboard0
[    19.926] (WW) Disabling Mouse0
[    19.926] (II) Loader magic: 0x7f8924ea3b00
[    19.926] (II) Module ABI versions:
[    19.926]     X.Org ANSI C Emulation: 0.4
[    19.926]     X.Org Video Driver: 11.0
[    19.926]     X.Org XInput driver : 16.0
[    19.926]     X.Org Server Extension : 6.0
[    19.927] (--) PCI:*(0:1:0:0) 10de:1040:0000:0000 rev 161, Mem @ 0xfa000000/16777216, 0xd8000000/134217728, 0xd6000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
[    19.927] (--) PCI: (0:4:0:0) 14f1:8852:6981:8888 rev 4, Mem @ 0xfbe00000/2097152
[    19.927] (--) PCI: (0:5:5:0) 14f1:8800:8922:8888 rev 5, Mem @ 0xfd000000/16777216
[    19.927] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.927] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    19.927] (II) "extmod" will be loaded by default.
[    19.927] (II) "dbe" will be loaded by default.
[    19.927] (II) "glx" will be loaded by default.
[    19.927] (II) "record" will be loaded by default.
[    19.927] (II) "dri" will be loaded by default.
[    19.927] (II) "dri2" will be loaded by default.
[    19.927] (II) LoadModule: "extmod"
[    19.928] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.928] (II) Module extmod: vendor="X.Org Foundation"
[    19.928]     compiled for 1.11.3, module version = 1.0.0
[    19.928]     Module class: X.Org Server Extension
[    19.928]     ABI class: X.Org Server Extension, version 6.0
[    19.928] (II) Loading extension MIT-SCREEN-SAVER
[    19.928] (II) Loading extension XFree86-VidModeExtension
[    19.928] (II) Loading extension XFree86-DGA
[    19.928] (II) Loading extension DPMS
[    19.928] (II) Loading extension XVideo
[    19.928] (II) Loading extension XVideo-MotionCompensation
[    19.928] (II) Loading extension X-Resource
[    19.928] (II) LoadModule: "dbe"
[    19.928] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.928] (II) Module dbe: vendor="X.Org Foundation"
[    19.928]     compiled for 1.11.3, module version = 1.0.0
[    19.928]     Module class: X.Org Server Extension
[    19.928]     ABI class: X.Org Server Extension, version 6.0
[    19.928] (II) Loading extension DOUBLE-BUFFER
[    19.928] (II) LoadModule: "glx"
[    19.928] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    19.942] (II) Module glx: vendor="NVIDIA Corporation"
[    19.942]     compiled for 4.0.2, module version = 1.0.0
[    19.942]     Module class: X.Org Server Extension
[    19.942] (II) NVIDIA GLX Module  304.123  Wed Jul  2 11:19:55 PDT 2014
[    19.942] (II) Loading extension GLX
[    19.942] (II) LoadModule: "record"
[    19.942] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.942] (II) Module record: vendor="X.Org Foundation"
[    19.942]     compiled for 1.11.3, module version = 1.13.0
[    19.942]     Module class: X.Org Server Extension
[    19.942]     ABI class: X.Org Server Extension, version 6.0
[    19.942] (II) Loading extension RECORD
[    19.942] (II) LoadModule: "dri"
[    19.942] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.943] (II) Module dri: vendor="X.Org Foundation"
[    19.943]     compiled for 1.11.3, module version = 1.0.0
[    19.943]     ABI class: X.Org Server Extension, version 6.0
[    19.943] (II) Loading extension XFree86-DRI
[    19.943] (II) LoadModule: "dri2"
[    19.943] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.943] (II) Module dri2: vendor="X.Org Foundation"
[    19.943]     compiled for 1.11.3, module version = 1.2.0
[    19.943]     ABI class: X.Org Server Extension, version 6.0
[    19.943] (II) Loading extension DRI2
[    19.943] (II) LoadModule: "nvidia"
[    19.943] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    19.944] (II) Module nvidia: vendor="NVIDIA Corporation"
[    19.944]     compiled for 4.0.2, module version = 1.0.0
[    19.944]     Module class: X.Org Video Driver
[    19.944] (II) NVIDIA dlloader X Driver  304.123  Wed Jul  2 11:01:29 PDT 2014
[    19.944] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    19.944] (++) using VT number 7


[    19.946] (II) Loading sub module "fb"
[    19.946] (II) LoadModule: "fb"
[    19.947] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.947] (II) Module fb: vendor="X.Org Foundation"
[    19.947]     compiled for 1.11.3, module version = 1.0.0
[    19.947]     ABI class: X.Org ANSI C Emulation, version 0.4
[    19.947] (II) Loading sub module "wfb"
[    19.947] (II) LoadModule: "wfb"
[    19.947] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    19.947] (II) Module wfb: vendor="X.Org Foundation"
[    19.947]     compiled for 1.11.3, module version = 1.0.0
[    19.947]     ABI class: X.Org ANSI C Emulation, version 0.4
[    19.947] (II) Loading sub module "ramdac"
[    19.947] (II) LoadModule: "ramdac"
[    19.947] (II) Module "ramdac" already built-in
[    19.947] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    19.947] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    19.947] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.947] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    19.947] (==) NVIDIA(0): RGB weight 888
[    19.947] (==) NVIDIA(0): Default visual is TrueColor
[    19.947] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    19.947] (**) NVIDIA(0): Option "Stereo" "0"
[    19.948] (**) NVIDIA(0): Option "SLI" "Off"
[    19.948] (**) NVIDIA(0): Option "MultiGPU" "on"
[    19.948] (**) NVIDIA(0): Option "BaseMosaic" "off"
[    19.948] (**) NVIDIA(0): Stereo disabled by request
[    19.948] (**) NVIDIA(0): NVIDIA SLI disabled.
[    19.948] (**) NVIDIA(0): NVIDIA Multi-GPU auto-select rendering option.
[    19.948] (**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
[    19.948] (**) NVIDIA(0): Enabling 2D acceleration
[    19.948] (WW) NVIDIA(0): Failed to initialize Multi-GPU!  Reason: Only one GPU
[    19.948] (WW) NVIDIA(0):     detected.  Only one GPU will be used for this X screen.
[    21.036] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    21.036] (II) NVIDIA(GPU-0):     stereo.
[    21.038] (II) NVIDIA(0): NVIDIA GPU GeForce GT 520 (GF119) at PCI:1:0:0 (GPU-0)
[    21.038] (--) NVIDIA(0): Memory: 1048576 kBytes
[    21.038] (--) NVIDIA(0): VideoBIOS: 75.19.1b.00.00
[    21.038] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    21.038] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    21.048] (--) NVIDIA(0): Valid display device(s) on GeForce GT 520 at PCI:1:0:0
[    21.048] (--) NVIDIA(0):     CRT-0
[    21.048] (--) NVIDIA(0):     CRT-1
[    21.048] (--) NVIDIA(0):     DFP-0
[    21.048] (--) NVIDIA(0):     TOSHIBA-TV (DFP-1) (connected)
[    21.048] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    21.048] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    21.048] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    21.048] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    21.048] (--) NVIDIA(0): TOSHIBA-TV (DFP-1): 165.0 MHz maximum pixel clock
[    21.048] (--) NVIDIA(0): TOSHIBA-TV (DFP-1): Internal Single Link TMDS
[    21.048] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    21.048] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    21.048] (**) NVIDIA(0):     enabled on all display devices.)
[    21.050] (II) NVIDIA(0): Validated MetaModes:
[    21.050] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[    21.050] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    21.099] (--) NVIDIA(0): DPI set to (46, 46); computed from "UseEdidDpi" X config
[    21.099] (--) NVIDIA(0):     option
[    21.099] (--) Depth 24 pixmap format is 32 bpp
[    21.099] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    21.099] (II) NVIDIA:     access.
[    21.109] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[    21.185] (II) Loading extension NV-GLX
[    21.206] (==) NVIDIA(0): Disabling shared memory pixmaps
[    21.206] (==) NVIDIA(0): Backing store disabled
[    21.206] (==) NVIDIA(0): Silken mouse enabled
[    21.207] (**) NVIDIA(0): DPMS enabled
[    21.207] (II) Loading extension NV-CONTROL
[    21.207] (II) Loading extension XINERAMA
[    21.207] (II) Loading sub module "dri2"
[    21.207] (II) LoadModule: "dri2"
[    21.207] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.207] (II) Module dri2: vendor="X.Org Foundation"
[    21.207]     compiled for 1.11.3, module version = 1.2.0
[    21.207]     ABI class: X.Org Server Extension, version 6.0
[    21.207] (II) NVIDIA(0): [DRI2] Setup complete
[    21.207] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    21.207] (--) RandR disabled
[    21.207] (II) Initializing built-in extension Generic Event Extension
[    21.207] (II) Initializing built-in extension SHAPE
[    21.207] (II) Initializing built-in extension MIT-SHM
[    21.207] (II) Initializing built-in extension XInputExtension
[    21.207] (II) Initializing built-in extension XTEST
[    21.207] (II) Initializing built-in extension BIG-REQUESTS
[    21.207] (II) Initializing built-in extension SYNC
[    21.207] (II) Initializing built-in extension XKEYBOARD
[    21.207] (II) Initializing built-in extension XC-MISC
[    21.207] (II) Initializing built-in extension SECURITY
[    21.207] (II) Initializing built-in extension XINERAMA
[    21.207] (II) Initializing built-in extension XFIXES
[    21.207] (II) Initializing built-in extension RENDER
[    21.207] (II) Initializing built-in extension RANDR
[    21.207] (II) Initializing built-in extension COMPOSITE
[    21.207] (II) Initializing built-in extension DAMAGE
[    21.209] (II) Initializing extension GLX
[    21.231] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.233] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    21.233] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.233] (II) LoadModule: "evdev"
[    21.233] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.233] (II) Module evdev: vendor="X.Org Foundation"
[    21.233]     compiled for 1.11.3, module version = 2.7.0
[    21.233]     Module class: X.Org XInput Driver
[    21.233]     ABI class: X.Org XInput driver, version 16.0
[    21.233] (II) Using input driver 'evdev' for 'Power Button'
[    21.233] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.233] (**) Power Button: always reports core events
[    21.233] (**) evdev: Power Button: Device: "/dev/input/event1"
[    21.233] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.233] (--) evdev: Power Button: Found keys
[    21.233] (II) evdev: Power Button: Configuring as keyboard
[    21.233] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    21.233] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    21.233] (**) Option "xkb_rules" "evdev"
[    21.233] (**) Option "xkb_model" "pc105"
[    21.233] (**) Option "xkb_layout" "gb"
[    21.235] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    21.235] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    21.235] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.235] (II) Using input driver 'evdev' for 'Power Button'
[    21.235] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.235] (**) Power Button: always reports core events
[    21.235] (**) evdev: Power Button: Device: "/dev/input/event0"
[    21.235] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.235] (--) evdev: Power Button: Found keys
[    21.235] (II) evdev: Power Button: Configuring as keyboard
[    21.235] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    21.235] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    21.235] (**) Option "xkb_rules" "evdev"
[    21.235] (**) Option "xkb_model" "pc105"
[    21.235] (**) Option "xkb_layout" "gb"
[    21.236] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event10)
[    21.236] (II) No input driver specified, ignoring this device.
[    21.236] (II) This device may have been added with another device file.
[    21.236] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event11)
[    21.236] (II) No input driver specified, ignoring this device.
[    21.236] (II) This device may have been added with another device file.
[    21.236] (II) config/udev: Adding input device HOLTEK Wireless USB Device (/dev/input/event2)
[    21.236] (**) HOLTEK Wireless USB Device: Applying InputClass "evdev keyboard catchall"
[    21.236] (II) Using input driver 'evdev' for 'HOLTEK Wireless USB Device'
[    21.236] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.236] (**) HOLTEK Wireless USB Device: always reports core events
[    21.236] (**) evdev: HOLTEK Wireless USB Device: Device: "/dev/input/event2"
[    21.236] (--) evdev: HOLTEK Wireless USB Device: Vendor 0x4d9 Product 0xa01c
[    21.236] (--) evdev: HOLTEK Wireless USB Device: Found keys
[    21.236] (II) evdev: HOLTEK Wireless USB Device: Configuring as keyboard
[    21.236] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:07.0/0000:03:00.0/usb11/11-1/11-1:1.0/input/input2/event2"
[    21.236] (II) XINPUT: Adding extended input device "HOLTEK Wireless USB Device" (type: KEYBOARD, id 8)
[    21.236] (**) Option "xkb_rules" "evdev"
[    21.236] (**) Option "xkb_model" "pc105"
[    21.236] (**) Option "xkb_layout" "gb"
[    21.237] (II) config/udev: Adding input device HOLTEK Wireless USB Device (/dev/input/event3)
[    21.237] (**) HOLTEK Wireless USB Device: Applying InputClass "evdev pointer catchall"
[    21.237] (**) HOLTEK Wireless USB Device: Applying InputClass "evdev keyboard catchall"
[    21.237] (II) Using input driver 'evdev' for 'HOLTEK Wireless USB Device'
[    21.237] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.237] (**) HOLTEK Wireless USB Device: always reports core events
[    21.237] (**) evdev: HOLTEK Wireless USB Device: Device: "/dev/input/event3"
[    21.237] (--) evdev: HOLTEK Wireless USB Device: Vendor 0x4d9 Product 0xa01c
[    21.237] (--) evdev: HOLTEK Wireless USB Device: Found 9 mouse buttons
[    21.237] (--) evdev: HOLTEK Wireless USB Device: Found scroll wheel(s)
[    21.237] (--) evdev: HOLTEK Wireless USB Device: Found relative axes
[    21.237] (--) evdev: HOLTEK Wireless USB Device: Found x and y relative axes
[    21.237] (--) evdev: HOLTEK Wireless USB Device: Found keys
[    21.237] (II) evdev: HOLTEK Wireless USB Device: Configuring as mouse
[    21.237] (II) evdev: HOLTEK Wireless USB Device: Configuring as keyboard
[    21.237] (II) evdev: HOLTEK Wireless USB Device: Adding scrollwheel support
[    21.237] (**) evdev: HOLTEK Wireless USB Device: YAxisMapping: buttons 4 and 5
[    21.237] (**) evdev: HOLTEK Wireless USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.237] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:07.0/0000:03:00.0/usb11/11-1/11-1:1.1/input/input3/event3"
[    21.237] (II) XINPUT: Adding extended input device "HOLTEK Wireless USB Device" (type: KEYBOARD, id 9)
[    21.237] (**) Option "xkb_rules" "evdev"
[    21.237] (**) Option "xkb_model" "pc105"
[    21.237] (**) Option "xkb_layout" "gb"
[    21.237] (II) evdev: HOLTEK Wireless USB Device: initialized for relative axes.
[    21.237] (**) HOLTEK Wireless USB Device: (accel) keeping acceleration scheme 1
[    21.237] (**) HOLTEK Wireless USB Device: (accel) acceleration profile 0
[    21.237] (**) HOLTEK Wireless USB Device: (accel) acceleration factor: 2.000
[    21.237] (**) HOLTEK Wireless USB Device: (accel) acceleration threshold: 4
[    21.237] (II) config/udev: Adding input device HOLTEK Wireless USB Device (/dev/input/mouse0)
[    21.238] (II) No input driver specified, ignoring this device.
[    21.238] (II) This device may have been added with another device file.
[    21.238] (II) config/udev: Adding input device cx23885 IR (TurboSight TBS 6981) (/dev/input/event16)
[    21.238] (**) cx23885 IR (TurboSight TBS 6981): Applying InputClass "evdev keyboard catchall"
[    21.238] (II) Using input driver 'evdev' for 'cx23885 IR (TurboSight TBS 6981)'
[    21.238] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.238] (**) cx23885 IR (TurboSight TBS 6981): always reports core events
[    21.238] (**) evdev: cx23885 IR (TurboSight TBS 6981): Device: "/dev/input/event16"
[    21.238] (--) evdev: cx23885 IR (TurboSight TBS 6981): Vendor 0x6981 Product 0x8888
[    21.238] (--) evdev: cx23885 IR (TurboSight TBS 6981): Found keys
[    21.238] (II) evdev: cx23885 IR (TurboSight TBS 6981): Configuring as keyboard
[    21.238] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:09.0/0000:04:00.0/rc/rc3/input16/event16"
[    21.238] (II) XINPUT: Adding extended input device "cx23885 IR (TurboSight TBS 6981)" (type: KEYBOARD, id 10)
[    21.238] (**) Option "xkb_rules" "evdev"
[    21.238] (**) Option "xkb_model" "pc105"
[    21.238] (**) Option "xkb_layout" "gb"
[    21.238] (II) config/udev: Adding input device Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) (/dev/input/event4)
[    21.238] (**) Media Center Ed. eHome Infrared Remote Transceiver (0471:0815): Applying InputClass "evdev keyboard catchall"
[    21.238] (II) Using input driver 'evdev' for 'Media Center Ed. eHome Infrared Remote Transceiver (0471:0815)'
[    21.238] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.238] (**) Media Center Ed. eHome Infrared Remote Transceiver (0471:0815): always reports core events
[    21.238] (**) evdev: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815): Device: "/dev/input/event4"
[    21.238] (--) evdev: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815): Vendor 0x471 Product 0x815
[    21.238] (--) evdev: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815): Found keys
[    21.238] (II) evdev: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815): Configuring as keyboard
[    21.238] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/rc/rc0/input4/event4"
[    21.238] (II) XINPUT: Adding extended input device "Media Center Ed. eHome Infrared Remote Transceiver (0471:0815)" (type: KEYBOARD, id 11)
[    21.239] (**) Option "xkb_rules" "evdev"
[    21.239] (**) Option "xkb_model" "pc105"
[    21.239] (**) Option "xkb_layout" "gb"
[    21.239] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event5)
[    21.239] (II) No input driver specified, ignoring this device.
[    21.239] (II) This device may have been added with another device file.
[    21.239] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event6)
[    21.239] (II) No input driver specified, ignoring this device.
[    21.239] (II) This device may have been added with another device file.
[    21.239] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event7)
[    21.239] (II) No input driver specified, ignoring this device.
[    21.239] (II) This device may have been added with another device file.
[    21.240] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event8)
[    21.240] (II) No input driver specified, ignoring this device.
[    21.240] (II) This device may have been added with another device file.
[    21.240] (II) config/udev: Adding input device HDA ATI SB Line-Out (/dev/input/event9)
[    21.240] (II) No input driver specified, ignoring this device.
[    21.240] (II) This device may have been added with another device file.
[    21.240] (II) config/udev: Adding input device cx88 IR (TBS 8922 DVB-S/S2) (/dev/input/event13)
[    21.240] (**) cx88 IR (TBS 8922 DVB-S/S2): Applying InputClass "evdev keyboard catchall"
[    21.240] (II) Using input driver 'evdev' for 'cx88 IR (TBS 8922 DVB-S/S2)'
[    21.240] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.240] (**) cx88 IR (TBS 8922 DVB-S/S2): always reports core events
[    21.240] (**) evdev: cx88 IR (TBS 8922 DVB-S/S2): Device: "/dev/input/event13"
[    21.240] (--) evdev: cx88 IR (TBS 8922 DVB-S/S2): Vendor 0x8922 Product 0x8888
[    21.240] (--) evdev: cx88 IR (TBS 8922 DVB-S/S2): Found keys
[    21.240] (II) evdev: cx88 IR (TBS 8922 DVB-S/S2): Configuring as keyboard
[    21.240] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.4/0000:05:05.0/rc/rc1/input13/event13"
[    21.240] (II) XINPUT: Adding extended input device "cx88 IR (TBS 8922 DVB-S/S2)" (type: KEYBOARD, id 12)
[    21.240] (**) Option "xkb_rules" "evdev"
[    21.240] (**) Option "xkb_model" "pc105"
[    21.240] (**) Option "xkb_layout" "gb"
[    21.241] (II) config/udev: Adding input device Budget-CI dvb ir receiver saa7146 (0) (/dev/input/event15)
[    21.241] (**) Budget-CI dvb ir receiver saa7146 (0): Applying InputClass "evdev keyboard catchall"
[    21.241] (II) Using input driver 'evdev' for 'Budget-CI dvb ir receiver saa7146 (0)'
[    21.241] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.241] (**) Budget-CI dvb ir receiver saa7146 (0): always reports core events
[    21.241] (**) evdev: Budget-CI dvb ir receiver saa7146 (0): Device: "/dev/input/event15"
[    21.241] (--) evdev: Budget-CI dvb ir receiver saa7146 (0): Vendor 0x13c2 Product 0x100f
[    21.241] (--) evdev: Budget-CI dvb ir receiver saa7146 (0): Found keys
[    21.241] (II) evdev: Budget-CI dvb ir receiver saa7146 (0): Configuring as keyboard
[    21.241] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.4/0000:05:07.0/rc/rc2/input15/event15"
[    21.241] (II) XINPUT: Adding extended input device "Budget-CI dvb ir receiver saa7146 (0)" (type: KEYBOARD, id 13)
[    21.241] (**) Option "xkb_rules" "evdev"
[    21.241] (**) Option "xkb_model" "pc105"
[    21.241] (**) Option "xkb_layout" "gb"
[    21.243] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (mceusb) (/dev/input/event12)
[    21.243] (**) MCE IR Keyboard/Mouse (mceusb): Applying InputClass "evdev pointer catchall"
[    21.243] (**) MCE IR Keyboard/Mouse (mceusb): Applying InputClass "evdev keyboard catchall"
[    21.243] (II) Using input driver 'evdev' for 'MCE IR Keyboard/Mouse (mceusb)'
[    21.243] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.243] (**) MCE IR Keyboard/Mouse (mceusb): always reports core events
[    21.243] (**) evdev: MCE IR Keyboard/Mouse (mceusb): Device: "/dev/input/event12"
[    21.243] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Vendor 0 Product 0
[    21.243] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Found 3 mouse buttons
[    21.243] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Found relative axes
[    21.243] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Found x and y relative axes
[    21.243] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Found keys
[    21.243] (II) evdev: MCE IR Keyboard/Mouse (mceusb): Configuring as mouse
[    21.243] (II) evdev: MCE IR Keyboard/Mouse (mceusb): Configuring as keyboard
[    21.243] (**) evdev: MCE IR Keyboard/Mouse (mceusb): YAxisMapping: buttons 4 and 5
[    21.243] (**) evdev: MCE IR Keyboard/Mouse (mceusb): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.243] (**) Option "config_info" "udev:/sys/devices/virtual/input/input12/event12"
[    21.243] (II) XINPUT: Adding extended input device "MCE IR Keyboard/Mouse (mceusb)" (type: KEYBOARD, id 14)
[    21.243] (**) Option "xkb_rules" "evdev"
[    21.243] (**) Option "xkb_model" "pc105"
[    21.243] (**) Option "xkb_layout" "gb"
[    21.243] (II) evdev: MCE IR Keyboard/Mouse (mceusb): initialized for relative axes.
[    21.243] (**) MCE IR Keyboard/Mouse (mceusb): (accel) keeping acceleration scheme 1
[    21.243] (**) MCE IR Keyboard/Mouse (mceusb): (accel) acceleration profile 0
[    21.243] (**) MCE IR Keyboard/Mouse (mceusb): (accel) acceleration factor: 2.000
[    21.243] (**) MCE IR Keyboard/Mouse (mceusb): (accel) acceleration threshold: 4
[    21.243] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (mceusb) (/dev/input/mouse1)
[    21.243] (II) No input driver specified, ignoring this device.
[    21.243] (II) This device may have been added with another device file.
[    21.244] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (cx88xx) (/dev/input/event14)
[    21.244] (**) MCE IR Keyboard/Mouse (cx88xx): Applying InputClass "evdev pointer catchall"
[    21.244] (**) MCE IR Keyboard/Mouse (cx88xx): Applying InputClass "evdev keyboard catchall"
[    21.244] (II) Using input driver 'evdev' for 'MCE IR Keyboard/Mouse (cx88xx)'
[    21.244] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.244] (**) MCE IR Keyboard/Mouse (cx88xx): always reports core events
[    21.244] (**) evdev: MCE IR Keyboard/Mouse (cx88xx): Device: "/dev/input/event14"
[    21.244] (--) evdev: MCE IR Keyboard/Mouse (cx88xx): Vendor 0 Product 0
[    21.244] (--) evdev: MCE IR Keyboard/Mouse (cx88xx): Found 3 mouse buttons
[    21.244] (--) evdev: MCE IR Keyboard/Mouse (cx88xx): Found relative axes
[    21.244] (--) evdev: MCE IR Keyboard/Mouse (cx88xx): Found x and y relative axes
[    21.244] (--) evdev: MCE IR Keyboard/Mouse (cx88xx): Found keys
[    21.244] (II) evdev: MCE IR Keyboard/Mouse (cx88xx): Configuring as mouse
[    21.244] (II) evdev: MCE IR Keyboard/Mouse (cx88xx): Configuring as keyboard
[    21.244] (**) evdev: MCE IR Keyboard/Mouse (cx88xx): YAxisMapping: buttons 4 and 5
[    21.244] (**) evdev: MCE IR Keyboard/Mouse (cx88xx): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.244] (**) Option "config_info" "udev:/sys/devices/virtual/input/input14/event14"
[    21.244] (II) XINPUT: Adding extended input device "MCE IR Keyboard/Mouse (cx88xx)" (type: KEYBOARD, id 15)
[    21.244] (**) Option "xkb_rules" "evdev"
[    21.244] (**) Option "xkb_model" "pc105"
[    21.244] (**) Option "xkb_layout" "gb"
[    21.244] (II) evdev: MCE IR Keyboard/Mouse (cx88xx): initialized for relative axes.
[    21.244] (**) MCE IR Keyboard/Mouse (cx88xx): (accel) keeping acceleration scheme 1
[    21.244] (**) MCE IR Keyboard/Mouse (cx88xx): (accel) acceleration profile 0
[    21.244] (**) MCE IR Keyboard/Mouse (cx88xx): (accel) acceleration factor: 2.000
[    21.244] (**) MCE IR Keyboard/Mouse (cx88xx): (accel) acceleration threshold: 4
[    21.244] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (cx88xx) (/dev/input/mouse2)
[    21.244] (II) No input driver specified, ignoring this device.
[    21.244] (II) This device may have been added with another device file.
[    21.245] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (cx23885) (/dev/input/event17)
[    21.245] (**) MCE IR Keyboard/Mouse (cx23885): Applying InputClass "evdev pointer catchall"
[    21.245] (**) MCE IR Keyboard/Mouse (cx23885): Applying InputClass "evdev keyboard catchall"
[    21.245] (II) Using input driver 'evdev' for 'MCE IR Keyboard/Mouse (cx23885)'
[    21.245] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.245] (**) MCE IR Keyboard/Mouse (cx23885): always reports core events
[    21.245] (**) evdev: MCE IR Keyboard/Mouse (cx23885): Device: "/dev/input/event17"
[    21.245] (--) evdev: MCE IR Keyboard/Mouse (cx23885): Vendor 0 Product 0
[    21.245] (--) evdev: MCE IR Keyboard/Mouse (cx23885): Found 3 mouse buttons
[    21.245] (--) evdev: MCE IR Keyboard/Mouse (cx23885): Found relative axes
[    21.245] (--) evdev: MCE IR Keyboard/Mouse (cx23885): Found x and y relative axes
[    21.245] (--) evdev: MCE IR Keyboard/Mouse (cx23885): Found keys
[    21.245] (II) evdev: MCE IR Keyboard/Mouse (cx23885): Configuring as mouse
[    21.245] (II) evdev: MCE IR Keyboard/Mouse (cx23885): Configuring as keyboard
[    21.245] (**) evdev: MCE IR Keyboard/Mouse (cx23885): YAxisMapping: buttons 4 and 5
[    21.245] (**) evdev: MCE IR Keyboard/Mouse (cx23885): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.245] (**) Option "config_info" "udev:/sys/devices/virtual/input/input17/event17"
[    21.245] (II) XINPUT: Adding extended input device "MCE IR Keyboard/Mouse (cx23885)" (type: KEYBOARD, id 16)
[    21.245] (**) Option "xkb_rules" "evdev"
[    21.245] (**) Option "xkb_model" "pc105"
[    21.245] (**) Option "xkb_layout" "gb"
[    21.245] (II) evdev: MCE IR Keyboard/Mouse (cx23885): initialized for relative axes.
[    21.245] (**) MCE IR Keyboard/Mouse (cx23885): (accel) keeping acceleration scheme 1
[    21.245] (**) MCE IR Keyboard/Mouse (cx23885): (accel) acceleration profile 0
[    21.245] (**) MCE IR Keyboard/Mouse (cx23885): (accel) acceleration factor: 2.000
[    21.245] (**) MCE IR Keyboard/Mouse (cx23885): (accel) acceleration threshold: 4
[    21.245] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (cx23885) (/dev/input/mouse3)
[    21.245] (II) No input driver specified, ignoring this device.
[    21.245] (II) This device may have been added with another device file.
[    21.611] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    21.611] (II) NVIDIA(GPU-0):     stereo.
[    21.611] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    21.611] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    21.611] (**) NVIDIA(0):     enabled on all display devices.)
[    21.673] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    21.673] (II) NVIDIA(GPU-0):     stereo.
[    21.673] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    21.673] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    21.673] (**) NVIDIA(0):     enabled on all display devices.)
[    21.707] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    21.707] (II) NVIDIA(GPU-0):     stereo.
[    21.707] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    21.707] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    21.707] (**) NVIDIA(0):     enabled on all display devices.)
[    21.850] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    21.850] (II) NVIDIA(GPU-0):     stereo.
[    21.850] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    21.850] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    21.850] (**) NVIDIA(0):     enabled on all display devices.)
[    22.074] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    22.112] (II) NVIDIA(GPU-0):     stereo.
[    22.112] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    22.112] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    22.112] (**) NVIDIA(0):     enabled on all display devices.)
[    22.148] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    22.148] (II) NVIDIA(GPU-0):     stereo.
[    22.148] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    22.148] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    22.148] (**) NVIDIA(0):     enabled on all display devices.)
[    22.193] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    22.193] (II) NVIDIA(GPU-0):     stereo.
[    22.193] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    22.193] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    22.193] (**) NVIDIA(0):     enabled on all display devices.)
[    22.241] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    22.241] (II) NVIDIA(GPU-0):     stereo.
[    22.241] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    22.241] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    22.241] (**) NVIDIA(0):     enabled on all display devices.)
[    22.276] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    22.276] (II) NVIDIA(GPU-0):     stereo.
[    22.276] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    22.276] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    22.276] (**) NVIDIA(0):     enabled on all display devices.)
[    22.311] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    22.311] (II) NVIDIA(GPU-0):     stereo.
[    22.311] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    22.311] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    22.311] (**) NVIDIA(0):     enabled on all display devices.)
[    22.349] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    22.349] (II) NVIDIA(GPU-0):     stereo.
[    22.349] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    22.349] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    22.349] (**) NVIDIA(0):     enabled on all display devices.)
[    22.393] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    22.393] (II) NVIDIA(GPU-0):     stereo.
[    22.393] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    22.393] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    22.393] (**) NVIDIA(0):     enabled on all display devices.)
[    22.431] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    22.431] (II) NVIDIA(GPU-0):     stereo.
[    22.431] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    22.431] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    22.431] (**) NVIDIA(0):     enabled on all display devices.)
[    22.750] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    22.750] (II) NVIDIA(GPU-0):     stereo.
[    22.750] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    22.750] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    22.750] (**) NVIDIA(0):     enabled on all display devices.)
[    22.801] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    22.801] (II) NVIDIA(GPU-0):     stereo.
[    22.801] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    22.801] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    22.801] (**) NVIDIA(0):     enabled on all display devices.)
[    75.672] (II) NVIDIA(0): Setting mode "NULL"
[    88.194] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    88.194] (II) NVIDIA(GPU-0):     stereo.
[    88.194] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    88.194] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    88.194] (**) NVIDIA(0):     enabled on all display devices.)
[    88.230] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    88.230] (II) NVIDIA(GPU-0):     stereo.
[    88.230] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    88.230] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    88.230] (**) NVIDIA(0):     enabled on all display devices.)
[    88.267] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    88.267] (II) NVIDIA(GPU-0):     stereo.
[    88.267] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    88.267] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    88.267] (**) NVIDIA(0):     enabled on all display devices.)
[    88.302] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[    88.302] (II) NVIDIA(GPU-0):     stereo.
[    88.302] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    88.302] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[    88.302] (**) NVIDIA(0):     enabled on all display devices.)
[   100.050] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[   100.050] (II) NVIDIA(GPU-0):     stereo.
[   100.050] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   100.050] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[   100.050] (**) NVIDIA(0):     enabled on all display devices.)
[   100.078] (II) NVIDIA(0): Setting mode "HDMI-0: 1280x720 @1280x720 +0+0"
[   100.164] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[   100.164] (II) NVIDIA(GPU-0):     stereo.
[   100.164] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   100.164] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[   100.164] (**) NVIDIA(0):     enabled on all display devices.)
[   100.219] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[   100.219] (II) NVIDIA(GPU-0):     stereo.
[   100.219] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   100.219] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[   100.219] (**) NVIDIA(0):     enabled on all display devices.)
[   100.260] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[   100.260] (II) NVIDIA(GPU-0):     stereo.
[   100.260] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   100.261] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[   100.261] (**) NVIDIA(0):     enabled on all display devices.)
[   100.296] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[   100.296] (II) NVIDIA(GPU-0):     stereo.
[   100.296] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   100.296] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[   100.296] (**) NVIDIA(0):     enabled on all display devices.)
[   100.334] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[   100.334] (II) NVIDIA(GPU-0):     stereo.
[   100.334] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   100.334] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[   100.334] (**) NVIDIA(0):     enabled on all display devices.)
[   100.369] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[   100.369] (II) NVIDIA(GPU-0):     stereo.
[   100.369] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   100.369] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[   100.369] (**) NVIDIA(0):     enabled on all display devices.)
[   102.171] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[   102.171] (II) NVIDIA(GPU-0):     stereo.
[   102.171] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   102.171] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[   102.171] (**) NVIDIA(0):     enabled on all display devices.)
[   102.264] (II) NVIDIA(0): Setting mode "HDMI-0: nvidia-auto-select @1920x1080 +0+0"
[   102.388] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[   102.388] (II) NVIDIA(GPU-0):     stereo.
[   102.388] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   102.388] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[   102.388] (**) NVIDIA(0):     enabled on all display devices.)
[   102.457] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[   102.457] (II) NVIDIA(GPU-0):     stereo.
[   102.457] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   102.457] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[   102.457] (**) NVIDIA(0):     enabled on all display devices.)
[   102.492] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[   102.492] (II) NVIDIA(GPU-0):     stereo.
[   102.492] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   102.492] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[   102.492] (**) NVIDIA(0):     enabled on all display devices.)
[   102.527] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[   102.527] (II) NVIDIA(GPU-0):     stereo.
[   102.527] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   102.527] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[   102.527] (**) NVIDIA(0):     enabled on all display devices.)
[   102.566] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[   102.566] (II) NVIDIA(GPU-0):     stereo.
[   102.566] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   102.566] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[   102.566] (**) NVIDIA(0):     enabled on all display devices.)
[   102.602] (II) NVIDIA(GPU-0): Display (TOSHIBA-TV (DFP-1)) does not support NVIDIA 3D Vision
[   102.602] (II) NVIDIA(GPU-0):     stereo.
[   102.602] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   102.602] (**) NVIDIA(0):     device TOSHIBA-TV (DFP-1) (Using EDID frequencies has been
[   102.602] (**) NVIDIA(0):     enabled on all display devices.)



```

xorg.conf

```
# nvidia-settings: X configuration file generated by nvidia-settings# nvidia-settings:  version 331.20  (buildd@rhenium)  Wed Dec  4 16:24:23 UTC 2013


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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "unknown"
    ModelName      "TOSHIBA-TV"
    HorizSync       15.0 - 46.0
    VertRefresh     49.0 - 61.0
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 520"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "on"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



```

Thanks very much for you help

---

### Post by dannyboy79 on 2014-10-30
looking at your xorg.conf it doesn't appear that you followed the directions in the link i gave you.

make your Screen section look like this:
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
Option "ConnectedMonitor" "DFP-1"
Option "UseDisplayDevice" "DFP-1"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "on"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

the above should force your X server to output itself onto your TV which per your log is DFP-1 and this will occur whether the tv is on or not. you can read all about it reading nvidia's documentation. it explains many options and why we're doing what we're doing. here's the readme from nvidia driver version 173 but not much has changed [http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/appendix-b.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/appendix-b.html)

---

### Post by AlecJ on 2014-10-30
Great that worked thanks
I must have misread the file on that link.

Now I'm on a roll can you help me with [http://ubuntuforums.org/showthread.php?t=2250550](http://ubuntuforums.org/showthread.php?t=2250550)

Thanks again

---

### Post by dannyboy79 on 2014-10-30
mark this thread solved using the thread tool please. and no, sorry i can't help with your mythmusic database schema issue as i'm not a database person. i run mythtv but i don't use mythmusic. hopefully tgm will be able to assist you further. if it were me i would just google the problem or even log into the mythtv-users irc channel and ask there. there's normally someone on that irc channel willing to help.

---


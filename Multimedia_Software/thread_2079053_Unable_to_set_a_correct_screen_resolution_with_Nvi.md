---
title: "Unable to set a correct screen resolution with Nvidia Geforce 210"
date: 2012-11-01
forum: Multimedia Software
---

### Post by LucidOcelot on 2012-11-01
Hello,

I was previously using a ATI video card. But with release of 12.10, it seems that proprietary drivers becames not compatible with my too old card.

That is why i bought a brand new Geforce 210. Nvidia has a good reputation with linux.

For several days i try to set a correct screen resolution, looking for every post over the web... With no success at all.

When I use 

[LIST]
[*]nvidia-current all I can get is 640*480
[*]nv all I can get is 1280*1024
[/LIST]
Please help me, I am an Ubuntu user since Hoary Hedgehog, and now I have an ultimatum from my wife and I realy don't want to install anything else than linux...


apt-cache policy nvidia-current


```
nvidia-current:
  Installé : 304.51.really.304.43-0ubuntu1
  Candidat : 304.51.really.304.43-0ubuntu1
  Table de version :
 *** 304.51.really.304.43-0ubuntu1 0
        500 http://fr.archive.ubuntu.com/ubuntu/ quantal/restricted amd64 Packages
        100 /var/lib/dpkg/status
apt-cache policy nvidia-current

```and 



lshw -C display; lsb_release -a; uname -a; sudo dmidecode -t 1



```
 *-display               
       description: VGA compatible controller
       produit: GT218 [GeForce 210]
       fabriquant: NVIDIA Corporation
       identifiant matériel: 0
       information bus: pci@0000:01:00.0
       version: a2
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       ressources: irq:18 mémoire:fb000000-fbffffff mémoire:c0000000-cfffffff mémoire:de000000-dfffffff portE/S:ef00(taille=128) mémoire:d0000000-d007ffff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal
Linux Kafiland 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
# dmidecode 2.11
SMBIOS 2.4 present.

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Gigabyte Technology Co., Ltd.
    Product Name: GA-880GM-UD2H
    Version:  
    Serial Number:  
    UUID: 31433646-3635-4131-3339-4336FFFFFFFF
    Wake-up Type: Power Switch
    SKU Number:  
    Family:  

```

My screen is a M2BABW 22'' 1680*1050

Thank You !

---

### Post by LucidOcelot on 2012-11-01
Hello,

```
 xrandr --newmode "1680x1050" 147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
 xrandr --addmode VGA-1 "1680x1050"
xrandr -s "1680x1050"
```


partially did the trick for the nv driver, but 

[LIST]
[*]I have to repeat operation at each reboot.
[*]I have a black part on the right
[/LIST]


These operations return an error with nvidia-current

---

### Post by LucidOcelot on 2012-11-02
Hum! Anybody ? :(

---

### Post by |{urse on 2012-11-02
Yeah, sounds like all you need to do is add that command to a bash script 

cd ~ && echo 'xrandr --newmode "1680x1050" 147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync &&  xrandr --addmode VGA-1 "1680x1050" && xrandr -s "1680x1050"' > setres && chmod +x setres 

That command will create a script named setres with your commands in your Home directory, click the gear then click "Startup Applications" set the script you just made as a startup application.

I'd advise you to get a better card, but if that takes care of it, then whatevs ^^

---

### Post by BicyclerBoy on 2012-11-02
Your first post shows the nouveau driver has claimed the video card..

Normally the jockey install nvidia driver would have sorted that..

I would reinstall nvidia-current & reboot, then post the contains of
/var/log/Xorg.0.log


The GT210 is a poor choice unless it was almost free..
(5 yr old card too slow to do HD adv deinterlacing & incomplete HDA audio)

---

### Post by LucidOcelot on 2012-11-02
Many thanks for your help !!!

The content of the Xorg.0.log is

```
X.Org X Server 1.12.3
Release Date: 2012-07-09
[    46.322] X Protocol Version 11, Revision 0
[    46.322] Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu
[    46.322] Current Operating System: Linux Kafiland 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 x86_64
[    46.322] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-generic root=UUID=facb3325-8271-46db-b7db-29aa3e7e0fbd ro quiet splash
[    46.323] Build Date: 21 October 2012  07:08:05PM
[    46.323] xorg-server 3:1.12.3+git20120709~quantal2 (For technical support please see http://www.ubuntu.com/support) 
[    46.323] Current version of pixman: 0.26.0
[    46.323]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    46.323] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    46.323] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov  2 21:09:21 2012
[    46.323] (==) Using config file: "/etc/X11/xorg.conf"
[    46.323] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    46.323] (==) ServerLayout "Layout0"
[    46.323] (**) |-->Screen "Screen0" (0)
[    46.323] (**) |   |-->Monitor "Monitor0"
[    46.323] (**) |   |-->Device "Device0"
[    46.323] (**) |-->Input Device "Keyboard0"
[    46.323] (**) |-->Input Device "Mouse0"
[    46.323] (==) Automatically adding devices
[    46.323] (==) Automatically enabling devices
[    46.323] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    46.323]     Entry deleted from font path.
[    46.323] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    46.323]     Entry deleted from font path.
[    46.323] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    46.323]     Entry deleted from font path.
[    46.323] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    46.323]     Entry deleted from font path.
[    46.323] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    46.323]     Entry deleted from font path.
[    46.323] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    46.323] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    46.323] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    46.323] (WW) Disabling Keyboard0
[    46.323] (WW) Disabling Mouse0
[    46.323] (II) Loader magic: 0x7f6292fd2b20
[    46.323] (II) Module ABI versions:
[    46.323]     X.Org ANSI C Emulation: 0.4
[    46.323]     X.Org Video Driver: 12.0
[    46.323]     X.Org XInput driver : 16.0
[    46.323]     X.Org Server Extension : 6.0
[    46.324] (--) PCI:*(0:1:0:0) 10de:0a65:1462:8094 rev 162, Mem @ 0xfb000000/16777216, 0xc0000000/268435456, 0xde000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
[    46.324] (II) Open ACPI successful (/var/run/acpid.socket)
[    46.324] (II) LoadModule: "extmod"
[    46.370] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    46.370] (II) Module extmod: vendor="X.Org Foundation"
[    46.370]     compiled for 1.12.3, module version = 1.0.0
[    46.370]     Module class: X.Org Server Extension
[    46.370]     ABI class: X.Org Server Extension, version 6.0
[    46.370] (II) Loading extension MIT-SCREEN-SAVER
[    46.370] (II) Loading extension XFree86-VidModeExtension
[    46.370] (II) Loading extension XFree86-DGA
[    46.370] (II) Loading extension DPMS
[    46.370] (II) Loading extension XVideo
[    46.370] (II) Loading extension XVideo-MotionCompensation
[    46.370] (II) Loading extension X-Resource
[    46.370] (II) LoadModule: "dbe"
[    46.371] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    46.371] (II) Module dbe: vendor="X.Org Foundation"
[    46.371]     compiled for 1.12.3, module version = 1.0.0
[    46.371]     Module class: X.Org Server Extension
[    46.371]     ABI class: X.Org Server Extension, version 6.0
[    46.371] (II) Loading extension DOUBLE-BUFFER
[    46.371] (II) LoadModule: "glx"
[    46.371] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/libglx.so
[    47.429] (II) Module glx: vendor="NVIDIA Corporation"
[    47.429]     compiled for 4.0.2, module version = 1.0.0
[    47.429]     Module class: X.Org Server Extension
[    47.429] (II) NVIDIA GLX Module  304.43  Sun Aug 19 20:34:01 PDT 2012
[    47.429] (II) Loading extension GLX
[    47.429] (II) LoadModule: "record"
[    47.429] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    47.429] (II) Module record: vendor="X.Org Foundation"
[    47.429]     compiled for 1.12.3, module version = 1.13.0
[    47.429]     Module class: X.Org Server Extension
[    47.429]     ABI class: X.Org Server Extension, version 6.0
[    47.429] (II) Loading extension RECORD
[    47.429] (II) LoadModule: "dri"
[    47.440] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    47.441] (II) Module dri: vendor="X.Org Foundation"
[    47.441]     compiled for 1.12.3, module version = 1.0.0
[    47.441]     ABI class: X.Org Server Extension, version 6.0
[    47.441] (II) Loading extension XFree86-DRI
[    47.441] (II) LoadModule: "dri2"
[    47.441] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    47.441] (II) Module dri2: vendor="X.Org Foundation"
[    47.441]     compiled for 1.12.3, module version = 1.2.0
[    47.441]     ABI class: X.Org Server Extension, version 6.0
[    47.441] (II) Loading extension DRI2
[    47.441] (II) LoadModule: "nvidia"
[    47.441] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/nvidia_drv.so
[    47.529] (II) Module nvidia: vendor="NVIDIA Corporation"
[    47.530]     compiled for 4.0.2, module version = 1.0.0
[    47.530]     Module class: X.Org Video Driver
[    47.556] (II) NVIDIA dlloader X Driver  304.43  Sun Aug 19 20:15:32 PDT 2012
[    47.556] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    47.557] (++) using VT number 7

[    47.559] (II) Loading sub module "fb"
[    47.559] (II) LoadModule: "fb"
[    47.559] (II) Loading /usr/lib/xorg/modules/libfb.so
[    47.559] (II) Module fb: vendor="X.Org Foundation"
[    47.559]     compiled for 1.12.3, module version = 1.0.0
[    47.559]     ABI class: X.Org ANSI C Emulation, version 0.4
[    47.559] (II) Loading sub module "wfb"
[    47.559] (II) LoadModule: "wfb"
[    47.559] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    47.572] (II) Module wfb: vendor="X.Org Foundation"
[    47.572]     compiled for 1.12.3, module version = 1.0.0
[    47.572]     ABI class: X.Org ANSI C Emulation, version 0.4
[    47.572] (II) Loading sub module "ramdac"
[    47.572] (II) LoadModule: "ramdac"
[    47.573] (II) Module "ramdac" already built-in
[    47.608] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    47.608] (==) NVIDIA(0): RGB weight 888
[    47.608] (==) NVIDIA(0): Default visual is TrueColor
[    47.608] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    47.608] (**) NVIDIA(0): Enabling 2D acceleration
[    48.506] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
[    48.521] (II) NVIDIA(0): NVIDIA GPU GeForce 210 (GT218) at PCI:1:0:0 (GPU-0)
[    48.521] (--) NVIDIA(0): Memory: 1048576 kBytes
[    48.521] (--) NVIDIA(0): VideoBIOS: 70.18.49.00.03
[    48.521] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    48.521] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    48.522] (--) NVIDIA(0): Valid display device(s) on GeForce 210 at PCI:1:0:0
[    48.522] (--) NVIDIA(0):     CRT-0
[    48.522] (--) NVIDIA(0):     CRT-1 (connected)
[    48.522] (--) NVIDIA(0):     DFP-0
[    48.522] (--) NVIDIA(0):     DFP-1
[    48.522] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    48.522] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    48.522] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    48.522] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    48.522] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    48.522] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    48.522] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    48.522] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies has been enabled on
[    48.522] (**) NVIDIA(0):     all display devices.)
[    48.523] (WW) NVIDIA(0): No valid modes for "CRT-1:1680x1050"; removing.
[    48.523] (WW) NVIDIA(0): No valid modes for "CRT-1:1024x768"; removing.
[    48.523] (WW) NVIDIA(0): No valid modes for "CRT-1:800x600"; removing.
[    48.523] (WW) NVIDIA(0): 
[    48.523] (WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
[    48.523] (WW) NVIDIA(0):     "nvidia-auto-select".
[    48.523] (WW) NVIDIA(0): 
[    48.523] (II) NVIDIA(0): Validated MetaModes:
[    48.523] (II) NVIDIA(0):     "CRT-1:nvidia-auto-select"
[    48.523] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    48.549] (WW) NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
[    48.549] (WW) NVIDIA(0):     from CRT-1's EDID.
[    48.549] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    48.549] (--) Depth 24 pixmap format is 32 bpp
[    48.549] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    48.552] (II) NVIDIA(0): Setting mode "CRT-1:nvidia-auto-select"
[    48.574] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[    48.575] (II) Loading extension NV-GLX
[    48.596] (==) NVIDIA(0): Disabling shared memory pixmaps
[    48.596] (==) NVIDIA(0): Backing store disabled
[    48.596] (==) NVIDIA(0): Silken mouse enabled
[    48.596] (**) NVIDIA(0): DPMS enabled
[    48.596] (II) Loading extension NV-CONTROL
[    48.597] (II) Loading extension XINERAMA
[    48.597] (II) Loading sub module "dri2"
[    48.597] (II) LoadModule: "dri2"
[    48.597] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    48.597] (II) Module dri2: vendor="X.Org Foundation"
[    48.597]     compiled for 1.12.3, module version = 1.2.0
[    48.597]     ABI class: X.Org Server Extension, version 6.0
[    48.597] (II) NVIDIA(0): [DRI2] Setup complete
[    48.597] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    48.597] (--) RandR disabled
[    48.597] (II) Initializing built-in extension Generic Event Extension
[    48.597] (II) Initializing built-in extension SHAPE
[    48.597] (II) Initializing built-in extension MIT-SHM
[    48.597] (II) Initializing built-in extension XInputExtension
[    48.597] (II) Initializing built-in extension XTEST
[    48.597] (II) Initializing built-in extension BIG-REQUESTS
[    48.597] (II) Initializing built-in extension SYNC
[    48.597] (II) Initializing built-in extension XKEYBOARD
[    48.597] (II) Initializing built-in extension XC-MISC
[    48.597] (II) Initializing built-in extension SECURITY
[    48.597] (II) Initializing built-in extension XINERAMA
[    48.597] (II) Initializing built-in extension XFIXES
[    48.597] (II) Initializing built-in extension RENDER
[    48.597] (II) Initializing built-in extension RANDR
[    48.597] (II) Initializing built-in extension COMPOSITE
[    48.597] (II) Initializing built-in extension DAMAGE
[    48.598] (II) Initializing extension GLX
[    48.676] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    48.678] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    48.678] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    48.678] (II) LoadModule: "evdev"
[    48.679] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.679] (II) Module evdev: vendor="X.Org Foundation"
[    48.679]     compiled for 1.12.3, module version = 2.7.0
[    48.679]     Module class: X.Org XInput Driver
[    48.679]     ABI class: X.Org XInput driver, version 16.0
[    48.679] (II) Using input driver 'evdev' for 'Power Button'
[    48.679] (**) Power Button: always reports core events
[    48.679] (**) evdev: Power Button: Device: "/dev/input/event1"
[    48.679] (--) evdev: Power Button: Vendor 0 Product 0x1
[    48.679] (--) evdev: Power Button: Found keys
[    48.679] (II) evdev: Power Button: Configuring as keyboard
[    48.679] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    48.679] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    48.679] (**) Option "xkb_rules" "evdev"
[    48.679] (**) Option "xkb_model" "pc105"
[    48.679] (**) Option "xkb_layout" "fr"
[    48.680] (II) XKB: reuse xkmfile /var/lib/xkb/server-1CA37FD61409D6C1EDB80880DF2DB1A574556A6A.xkm
[    48.681] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    48.681] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    48.681] (II) Using input driver 'evdev' for 'Power Button'
[    48.681] (**) Power Button: always reports core events
[    48.681] (**) evdev: Power Button: Device: "/dev/input/event0"
[    48.681] (--) evdev: Power Button: Vendor 0 Product 0x1
[    48.681] (--) evdev: Power Button: Found keys
[    48.681] (II) evdev: Power Button: Configuring as keyboard
[    48.681] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    48.681] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    48.681] (**) Option "xkb_rules" "evdev"
[    48.681] (**) Option "xkb_model" "pc105"
[    48.681] (**) Option "xkb_layout" "fr"
[    48.682] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event14)
[    48.682] (II) No input driver specified, ignoring this device.
[    48.682] (II) This device may have been added with another device file.
[    48.682] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event15)
[    48.682] (II) No input driver specified, ignoring this device.
[    48.682] (II) This device may have been added with another device file.
[    48.682] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event16)
[    48.682] (II) No input driver specified, ignoring this device.
[    48.682] (II) This device may have been added with another device file.
[    48.682] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event17)
[    48.682] (II) No input driver specified, ignoring this device.
[    48.682] (II) This device may have been added with another device file.
[    48.683] (II) config/udev: Adding input device NOVATEK USB Keyboard (/dev/input/event2)
[    48.683] (**) NOVATEK USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    48.683] (II) Using input driver 'evdev' for 'NOVATEK USB Keyboard'
[    48.683] (**) NOVATEK USB Keyboard: always reports core events
[    48.683] (**) evdev: NOVATEK USB Keyboard: Device: "/dev/input/event2"
[    48.683] (--) evdev: NOVATEK USB Keyboard: Vendor 0x603 Product 0xf1
[    48.683] (--) evdev: NOVATEK USB Keyboard: Found keys
[    48.683] (II) evdev: NOVATEK USB Keyboard: Configuring as keyboard
[    48.683] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input2/event2"
[    48.683] (II) XINPUT: Adding extended input device "NOVATEK USB Keyboard" (type: KEYBOARD, id 8)
[    48.683] (**) Option "xkb_rules" "evdev"
[    48.683] (**) Option "xkb_model" "pc105"
[    48.683] (**) Option "xkb_layout" "fr"
[    48.683] (II) config/udev: Adding input device NOVATEK USB Keyboard (/dev/input/event3)
[    48.683] (**) NOVATEK USB Keyboard: Applying InputClass "evdev pointer catchall"
[    48.683] (**) NOVATEK USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    48.683] (II) Using input driver 'evdev' for 'NOVATEK USB Keyboard'
[    48.683] (**) NOVATEK USB Keyboard: always reports core events
[    48.683] (**) evdev: NOVATEK USB Keyboard: Device: "/dev/input/event3"
[    48.683] (--) evdev: NOVATEK USB Keyboard: Vendor 0x603 Product 0xf1
[    48.683] (--) evdev: NOVATEK USB Keyboard: Found 20 mouse buttons
[    48.683] (--) evdev: NOVATEK USB Keyboard: Found scroll wheel(s)
[    48.683] (--) evdev: NOVATEK USB Keyboard: Found relative axes
[    48.683] (--) evdev: NOVATEK USB Keyboard: Found x and y relative axes
[    48.683] (--) evdev: NOVATEK USB Keyboard: Found keys
[    48.683] (II) evdev: NOVATEK USB Keyboard: Configuring as mouse
[    48.683] (II) evdev: NOVATEK USB Keyboard: Configuring as keyboard
[    48.683] (II) evdev: NOVATEK USB Keyboard: Adding scrollwheel support
[    48.683] (**) evdev: NOVATEK USB Keyboard: YAxisMapping: buttons 4 and 5
[    48.683] (**) evdev: NOVATEK USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    48.683] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.1/input/input3/event3"
[    48.683] (II) XINPUT: Adding extended input device "NOVATEK USB Keyboard" (type: KEYBOARD, id 9)
[    48.683] (**) Option "xkb_rules" "evdev"
[    48.683] (**) Option "xkb_model" "pc105"
[    48.683] (**) Option "xkb_layout" "fr"
[    48.684] (II) evdev: NOVATEK USB Keyboard: initialized for relative axes.
[    48.684] (**) NOVATEK USB Keyboard: (accel) keeping acceleration scheme 1
[    48.684] (**) NOVATEK USB Keyboard: (accel) acceleration profile 0
[    48.684] (**) NOVATEK USB Keyboard: (accel) acceleration factor: 2.000
[    48.684] (**) NOVATEK USB Keyboard: (accel) acceleration threshold: 4
[    48.684] (II) config/udev: Adding input device NOVATEK USB Keyboard (/dev/input/mouse0)
[    48.684] (II) No input driver specified, ignoring this device.
[    48.684] (II) This device may have been added with another device file.
[    48.684] (II) config/udev: Adding input device 2.4GHZ Mouse (/dev/input/event4)
[    48.684] (**) 2.4GHZ Mouse: Applying InputClass "evdev keyboard catchall"
[    48.684] (II) Using input driver 'evdev' for '2.4GHZ Mouse'
[    48.684] (**) 2.4GHZ Mouse: always reports core events
[    48.684] (**) evdev: 2.4GHZ Mouse: Device: "/dev/input/event4"
[    48.684] (--) evdev: 2.4GHZ Mouse: Vendor 0x1ea7 Product 0x2
[    48.684] (--) evdev: 2.4GHZ Mouse: Found keys
[    48.684] (II) evdev: 2.4GHZ Mouse: Configuring as keyboard
[    48.684] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.0/input/input4/event4"
[    48.684] (II) XINPUT: Adding extended input device "2.4GHZ Mouse" (type: KEYBOARD, id 10)
[    48.684] (**) Option "xkb_rules" "evdev"
[    48.684] (**) Option "xkb_model" "pc105"
[    48.684] (**) Option "xkb_layout" "fr"
[    48.685] (II) config/udev: Adding input device 2.4GHZ Mouse (/dev/input/event5)
[    48.685] (**) 2.4GHZ Mouse: Applying InputClass "evdev pointer catchall"
[    48.685] (**) 2.4GHZ Mouse: Applying InputClass "evdev keyboard catchall"
[    48.685] (II) Using input driver 'evdev' for '2.4GHZ Mouse'
[    48.685] (**) 2.4GHZ Mouse: always reports core events
[    48.685] (**) evdev: 2.4GHZ Mouse: Device: "/dev/input/event5"
[    48.685] (--) evdev: 2.4GHZ Mouse: Vendor 0x1ea7 Product 0x2
[    48.685] (--) evdev: 2.4GHZ Mouse: Found 12 mouse buttons
[    48.685] (--) evdev: 2.4GHZ Mouse: Found scroll wheel(s)
[    48.685] (--) evdev: 2.4GHZ Mouse: Found relative axes
[    48.685] (--) evdev: 2.4GHZ Mouse: Found x and y relative axes
[    48.685] (--) evdev: 2.4GHZ Mouse: Found absolute axes
[    48.685] (II) evdev: 2.4GHZ Mouse: Forcing absolute x/y axes to exist.
[    48.685] (--) evdev: 2.4GHZ Mouse: Found keys
[    48.685] (II) evdev: 2.4GHZ Mouse: Configuring as mouse
[    48.685] (II) evdev: 2.4GHZ Mouse: Configuring as keyboard
[    48.685] (II) evdev: 2.4GHZ Mouse: Adding scrollwheel support
[    48.685] (**) evdev: 2.4GHZ Mouse: YAxisMapping: buttons 4 and 5
[    48.685] (**) evdev: 2.4GHZ Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    48.685] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.1/input/input5/event5"
[    48.685] (II) XINPUT: Adding extended input device "2.4GHZ Mouse" (type: KEYBOARD, id 11)
[    48.685] (**) Option "xkb_rules" "evdev"
[    48.685] (**) Option "xkb_model" "pc105"
[    48.685] (**) Option "xkb_layout" "fr"
[    48.685] (II) evdev: 2.4GHZ Mouse: initialized for relative axes.
[    48.685] (WW) evdev: 2.4GHZ Mouse: ignoring absolute axes.
[    48.685] (**) 2.4GHZ Mouse: (accel) keeping acceleration scheme 1
[    48.685] (**) 2.4GHZ Mouse: (accel) acceleration profile 0
[    48.685] (**) 2.4GHZ Mouse: (accel) acceleration factor: 2.000
[    48.685] (**) 2.4GHZ Mouse: (accel) acceleration threshold: 4
[    48.686] (II) config/udev: Adding input device 2.4GHZ Mouse (/dev/input/mouse1)
[    48.686] (II) No input driver specified, ignoring this device.
[    48.686] (II) This device may have been added with another device file.
[    48.686] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event10)
[    48.686] (II) No input driver specified, ignoring this device.
[    48.686] (II) This device may have been added with another device file.
[    48.686] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event11)
[    48.686] (II) No input driver specified, ignoring this device.
[    48.686] (II) This device may have been added with another device file.
[    48.686] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event12)
[    48.686] (II) No input driver specified, ignoring this device.
[    48.686] (II) This device may have been added with another device file.
[    48.686] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event13)
[    48.686] (II) No input driver specified, ignoring this device.
[    48.686] (II) This device may have been added with another device file.
[    48.686] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event6)
[    48.686] (II) No input driver specified, ignoring this device.
[    48.686] (II) This device may have been added with another device file.
[    48.687] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event7)
[    48.687] (II) No input driver specified, ignoring this device.
[    48.687] (II) This device may have been added with another device file.
[    48.687] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event8)
[    48.687] (II) No input driver specified, ignoring this device.
[    48.687] (II) This device may have been added with another device file.
[    48.687] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event9)
[    48.687] (II) No input driver specified, ignoring this device.
[    48.687] (II) This device may have been added with another device file.
[    50.306] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
[    50.306] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    50.306] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies has been enabled on
[    50.306] (**) NVIDIA(0):     all display devices.)
[    50.623] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
[    50.623] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    50.623] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies has been enabled on
[    50.623] (**) NVIDIA(0):     all display devices.)
[    51.607] (WW) NVIDIA(GPU-0): Unable[CO to read EDID for display device CRT-1
[    51.607] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.607] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies has been enabled on
[    51.607] (**) NVIDIA(0):     all display devices.)
[    51.624] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
[    51.624] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.624] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies has been enabled on
[    51.624] (**) NVIDIA(0):     all display devices.)
[    54.828] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
[    54.828] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    54.828] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies has been enabled on
[    54.828] (**) NVIDIA(0):     all display devices.)
[    55.695] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
[    55.695] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    55.695] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies has been enabled on
[    55.695] (**) NVIDIA(0):     all display devices.)

```


The connected device is VGA-0 as

xrandr gives 

```

Screen 0: minimum 8 x 8, current 640 x 480, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected 640x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   640x480        59.9*+
   320x240       120.1  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
  1680x1050 (0x272)  147.1MHz
        h: width  1680 start 1784 end 1968 total 2256 skew    0 clock   65.2KHz
        v: height 1050 start 1051 end 1054 total 1087           clock   60.0Hz
  1680 (0x299)  147.1MHz
        h: width  1680 start 1784 end 1968 total 2256 skew    0 clock   65.2KHz
        v: height 1050 start 1051 end 1054 total 1087           clock   60.0Hz

```

---

### Post by BicyclerBoy on 2012-11-03
The easiest thing to try is a DVI cable..
And I mean DVI-D link to monitor..

VGA EDID reporting problems seem to plague nVidia drivers..

The work-around for EDID reporting problems is not difficult but is to be avoided.

---

### Post by LucidOcelot on 2012-11-04
> **BicyclerBoy said:**
> The easiest thing to try is a DVI cable..
And I mean DVI-D link to monitor..

VGA EDID reporting problems seem to plague nVidia drivers..

The work-around for EDID reporting problems is not difficult but is to be avoided.


My screen have only a VGA input!

Please, please

Tell me how,

I reinstalled Ubuntu and now in have only 800x600 even without nvidia drivers...

```
xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 400, current 800 x 600, maximum 1680 x 1050
default connected 800x600+0+0 0mm x 0mm
   800x600         0.0* 
   640x480        60.0  
   640x400         0.0  
   320x400         0.0  
   1680x1050      60.0  

xrandr -s "1680x1050"
Failed to change the screen configuration!



```xorg.0.log content is


```

[    20.483] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    20.483] X Protocol Version 11, Revision 0
[    20.483] Build Operating System: Linux 3.2.0-30-generic x86_64 Ubuntu
[    20.483] Current Operating System: Linux kafiland 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 x86_64
[    20.483] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-generic root=UUID=facb3325-8271-46db-b7db-29aa3e7e0fbd ro quiet splash vt.handoff=7
[    20.483] Build Date: 08 October 2012  03:34:01PM
[    20.483] xorg-server 2:1.13.0-0ubuntu6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    20.483] Current version of pixman: 0.26.0
[    20.483]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    20.483] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.484] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov  4 21:46:42 2012
[    20.484] (==) Using config file: "/etc/X11/xorg.conf"
[    20.484] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.495] (==) ServerLayout "Layout0"
[    20.495] (**) |-->Screen "Screen0" (0)
[    20.495] (**) |   |-->Monitor "Monitor0"
[    20.495] (**) |   |-->Device "Device0"
[    20.495] (**) |-->Input Device "Keyboard0"
[    20.495] (**) |-->Input Device "Mouse0"
[    20.495] (==) Automatically adding devices
[    20.495] (==) Automatically enabling devices
[    20.495] (==) Automatically adding GPU devices
[    20.495] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.495]     Entry deleted from font path.
[    20.495] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.495]     Entry deleted from font path.
[    20.495] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.495]     Entry deleted from font path.
[    20.495] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.495]     Entry deleted from font path.
[    20.495] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.495]     Entry deleted from font path.
[    20.495] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    20.495]     Entry deleted from font path.
[    20.495] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    20.495] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.495] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    20.495] (WW) Disabling Keyboard0
[    20.495] (WW) Disabling Mouse0
[    20.495] (II) Loader magic: 0x7f036c78dc40
[    20.495] (II) Module ABI versions:
[    20.495]     X.Org ANSI C Emulation: 0.4
[    20.495]     X.Org Video Driver: 13.0
[    20.495]     X.Org XInput driver : 18.0
[    20.495]     X.Org Server Extension : 7.0
[    20.496] (--) PCI:*(0:1:0:0) 10de:0a65:1462:8094 rev 162, Mem @ 0xfb000000/16777216, 0xc0000000/268435456, 0xde000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
[    20.496] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.497] Initializing built-in extension Generic Event Extension
[    20.497] Initializing built-in extension SHAPE
[    20.497] Initializing built-in extension MIT-SHM
[    20.497] Initializing built-in extension XInputExtension
[    20.497] Initializing built-in extension XTEST
[    20.497] Initializing built-in extension BIG-REQUESTS
[    20.497] Initializing built-in extension SYNC
[    20.497] Initializing built-in extension XKEYBOARD
[    20.497] Initializing built-in extension XC-MISC
[    20.497] Initializing built-in extension SECURITY
[    20.497] Initializing built-in extension XINERAMA
[    20.497] Initializing built-in extension XFIXES
[    20.497] Initializing built-in extension RENDER
[    20.497] Initializing built-in extension RANDR
[    20.497] Initializing built-in extension COMPOSITE
[    20.497] Initializing built-in extension DAMAGE
[    20.497] Initializing built-in extension MIT-SCREEN-SAVER
[    20.497] Initializing built-in extension DOUBLE-BUFFER
[    20.497] Initializing built-in extension RECORD
[    20.497] Initializing built-in extension DPMS
[    20.497] Initializing built-in extension X-Resource
[    20.497] Initializing built-in extension XVideo
[    20.497] Initializing built-in extension XVideo-MotionCompensation
[    20.497] Initializing built-in extension XFree86-VidModeExtension
[    20.497] Initializing built-in extension XFree86-DGA
[    20.497] Initializing built-in extension XFree86-DRI
[    20.497] Initializing built-in extension DRI2
[    20.497] (II) LoadModule: "glx"
[    20.538] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.538] (II) Module glx: vendor="X.Org Foundation"
[    20.538]     compiled for 1.13.0, module version = 1.0.0
[    20.538]     ABI class: X.Org Server Extension, version 7.0
[    20.538] (==) AIGLX enabled
[    20.538] Loading extension GLX
[    20.538] (II) LoadModule: "nv"
[    20.539] (WW) Warning, couldn't open module nv
[    20.539] (II) UnloadModule: "nv"
[    20.539] (II) Unloading nv
[    20.539] (EE) Failed to load module "nv" (module does not exist, 0)
[    20.539] (==) Matched nvidia as autoconfigured driver 0
[    20.539] (==) Matched nouveau as autoconfigured driver 1
[    20.539] (==) Matched nv as autoconfigured driver 2
[    20.539] (==) Matched vesa as autoconfigured driver 3
[    20.539] (==) Matched modesetting as autoconfigured driver 4
[    20.539] (==) Matched fbdev as autoconfigured driver 5
[    20.539] (==) Assigned the driver to the xf86ConfigLayout
[    20.539] (II) LoadModule: "nvidia"
[    20.539] (WW) Warning, couldn't open module nvidia
[    20.539] (II) UnloadModule: "nvidia"
[    20.539] (II) Unloading nvidia
[    20.539] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    20.539] (II) LoadModule: "nouveau"
[    20.539] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    20.539] (II) Module nouveau: vendor="X.Org Foundation"
[    20.539]     compiled for 1.13.0, module version = 1.0.2
[    20.539]     Module class: X.Org Video Driver
[    20.539]     ABI class: X.Org Video Driver, version 13.0
[    20.539] (II) LoadModule: "nv"
[    20.540] (WW) Warning, couldn't open module nv
[    20.540] (II) UnloadModule: "nv"
[    20.540] (II) Unloading nv
[    20.540] (EE) Failed to load module "nv" (module does not exist, 0)
[    20.540] (II) LoadModule: "vesa"
[    20.540] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.540] (II) Module vesa: vendor="X.Org Foundation"
[    20.540]     compiled for 1.12.99.902, module version = 2.3.2
[    20.540]     Module class: X.Org Video Driver
[    20.540]     ABI class: X.Org Video Driver, version 13.0
[    20.540] (II) LoadModule: "modesetting"
[    20.540] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    20.540] (II) Module modesetting: vendor="X.Org Foundation"
[    20.540]     compiled for 1.13.0, module version = 0.5.0
[    20.540]     Module class: X.Org Video Driver
[    20.540]     ABI class: X.Org Video Driver, version 13.0
[    20.540] (II) LoadModule: "fbdev"
[    20.540] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.540] (II) Module fbdev: vendor="X.Org Foundation"
[    20.540]     compiled for 1.12.99.902, module version = 0.4.3
[    20.540]     Module class: X.Org Video Driver
[    20.540]     ABI class: X.Org Video Driver, version 13.0
[    20.540] (II) NOUVEAU driver Date:   Wed Sep 12 13:42:43 2012 +0200
[    20.540] (II) NOUVEAU driver for NVIDIA chipset families :
[    20.540]     RIVA TNT        (NV04)
[    20.540]     RIVA TNT2       (NV05)
[    20.540]     GeForce 256     (NV10)
[    20.540]     GeForce 2       (NV11, NV15)
[    20.540]     GeForce 4MX     (NV17, NV18)
[    20.540]     GeForce 3       (NV20)
[    20.540]     GeForce 4Ti     (NV25, NV28)
[    20.540]     GeForce FX      (NV3x)
[    20.540]     GeForce 6       (NV4x)
[    20.540]     GeForce 7       (G7x)
[    20.540]     GeForce 8       (G8x)
[    20.541]     GeForce GTX 200 (NVA0)
[    20.541]     GeForce GTX 400 (NVC0)
[    20.541] (II) VESA: driver for VESA chipsets: vesa
[    20.541] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    20.541] (II) FBDEV: driver for framebuffer: fbdev
[    20.541] (++) using VT number 7

[    20.651] (EE) [drm] failed to open device
[    20.651] (WW) Falling back to old probe method for modesetting
[    20.651] (EE) open /dev/dri/card0: No such file or directory
[    20.651] (WW) Falling back to old probe method for fbdev
[    20.651] (II) Loading sub module "fbdevhw"
[    20.651] (II) LoadModule: "fbdevhw"
[    20.651] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.651] (II) Module fbdevhw: vendor="X.Org Foundation"
[    20.651]     compiled for 1.13.0, module version = 0.0.2
[    20.651]     ABI class: X.Org Video Driver, version 13.0
[    20.651] (EE) open /dev/fb0: No such file or directory
[    20.651] (II) Loading sub module "vbe"
[    20.651] (II) LoadModule: "vbe"
[    20.651] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    20.651] (II) Module vbe: vendor="X.Org Foundation"
[    20.651]     compiled for 1.13.0, module version = 1.1.0
[    20.651]     ABI class: X.Org Video Driver, version 13.0
[    20.652] (II) Loading sub module "int10"
[    20.652] (II) LoadModule: "int10"
[    20.652] (II) Loading /usr/lib/xorg/modules/libint10.so
[    20.652] (II) Module int10: vendor="X.Org Foundation"
[    20.652]     compiled for 1.13.0, module version = 1.0.0
[    20.652]     ABI class: X.Org Video Driver, version 13.0
[    20.652] (II) VESA(0): initializing int10
[    20.654] (II) VESA(0): Bad V_BIOS checksum
[    20.654] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    20.676] (II) VESA(0): VESA BIOS detected
[    20.676] (II) VESA(0): VESA VBE Version 3.0
[    20.676] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    20.676] (II) VESA(0): VESA VBE OEM: NVIDIA
[    20.676] (II) VESA(0): VESA VBE OEM Software Rev: 112.24
[    20.676] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    20.676] (II) VESA(0): VESA VBE OEM Product: GT218 Board - 08730000
[    20.676] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    20.724] (**) VESA(0): Depth 24, (--) framebuffer bpp 32
[    20.724] (==) VESA(0): RGB weight 888
[    20.724] (==) VESA(0): Default visual is TrueColor
[    20.724] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    20.724] (II) Loading sub module "ddc"
[    20.724] (II) LoadModule: "ddc"
[    20.724] (II) Module "ddc" already built-in
[    20.728] (II) VESA(0): VESA VBE DDC supported
[    20.728] (II) VESA(0): VESA VBE DDC Level none
[    20.728] (II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
[    20.915] (II) VESA(0): VESA VBE DDC read failed
[    20.915] (II) VESA(0): Searching for matching VESA mode(s):
[    20.916] Mode: 100 (640x400)
[    20.916]     ModeAttributes: 0x3bf
[    20.916]     WinAAttributes: 0x7
[    20.916]     WinBAttributes: 0x0
[    20.916]     WinGranularity: 64
[    20.916]     WinSize: 64
[    20.916]     WinASegment: 0xa000
[    20.916]     WinBSegment: 0x0
[    20.916]     WinFuncPtr: 0xc00067ac
[    20.916]     BytesPerScanline: 640
[    20.916]     XResolution: 640
[    20.916]     YResolution: 400
[    20.916]     XCharSize: 8
[    20.916]     YCharSize: 16
[    20.916]     NumberOfPlanes: 1
[    20.916]     BitsPerPixel: 8
[    20.916]     NumberOfBanks: 1
[    20.916]     MemoryModel: 4
[    20.916]     BankSize: 0
[    20.916]     NumberOfImages: 14
[    20.916]     RedMaskSize: 0
[    20.916]     RedFieldPosition: 0
[    20.916]     GreenMaskSize: 0
[    20.916]     GreenFieldPosition: 0
[    20.916]     BlueMaskSize: 0
[    20.916]     BlueFieldPosition: 0
[    20.916]     RsvdMaskSize: 0
[    20.916]     RsvdFieldPosition: 0
[    20.916]     DirectColorModeInfo: 0
[    20.916]     PhysBasePtr: 0xdf000000
[    20.916]     LinBytesPerScanLine: 640
[    20.916]     BnkNumberOfImagePages: 14
[    20.916]     LinNumberOfImagePages: 14
[    20.916]     LinRedMaskSize: 0
[    20.916]     LinRedFieldPosition: 0
[    20.916]     LinGreenMaskSize: 0
[    20.916]     LinGreenFieldPosition: 0
[    20.916]     LinBlueMaskSize: 0
[    20.916]     LinBlueFieldPosition: 0
[    20.916]     LinRsvdMaskSize: 0
[    20.916]     LinRsvdFieldPosition: 0
[    20.916]     MaxPixelClock: 229500000
[    20.917] Mode: 101 (640x480)
[    20.917]     ModeAttributes: 0x3bf
[    20.917]     WinAAttributes: 0x7
[    20.917]     WinBAttributes: 0x0
[    20.917]     WinGranularity: 64
[    20.917]     WinSize: 64
[    20.917]     WinASegment: 0xa000
[    20.917]     WinBSegment: 0x0
[    20.917]     WinFuncPtr: 0xc00067ac
[    20.917]     BytesPerScanline: 640
[    20.917]     XResolution: 640
[    20.917]     YResolution: 480
[    20.917]     XCharSize: 8
[    20.917]     YCharSize: 16
[    20.917]     NumberOfPlanes: 1
[    20.917]     BitsPerPixel: 8
[    20.917]     NumberOfBanks: 1
[    20.917]     MemoryModel: 4
[    20.917]     BankSize: 0
[    20.917]     NumberOfImages: 10
[    20.917]     RedMaskSize: 0
[    20.917]     RedFieldPosition: 0
[    20.917]     GreenMaskSize: 0
[    20.917]     GreenFieldPosition: 0
[    20.917]     BlueMaskSize: 0
[    20.917]     BlueFieldPosition: 0
[    20.917]     RsvdMaskSize: 0
[    20.917]     RsvdFieldPosition: 0
[    20.917]     DirectColorModeInfo: 0
[    20.917]     PhysBasePtr: 0xdf000000
[    20.917]     LinBytesPerScanLine: 640
[    20.917]     BnkNumberOfImagePages: 10
[    20.917]     LinNumberOfImagePages: 10
[    20.917]     LinRedMaskSize: 0
[    20.917]     LinRedFieldPosition: 0
[    20.917]     LinGreenMaskSize: 0
[    20.917]     LinGreenFieldPosition: 0
[    20.917]     LinBlueMaskSize: 0
[    20.917]     LinBlueFieldPosition: 0
[    20.917]     LinRsvdMaskSize: 0
[    20.917]     LinRsvdFieldPosition: 0
[    20.917]     MaxPixelClock: 229500000
[    20.918] Mode: 102 (800x600)
[    20.918]     ModeAttributes: 0x33f
[    20.918]     WinAAttributes: 0x7
[    20.918]     WinBAttributes: 0x0
[    20.918]     WinGranularity: 64
[    20.918]     WinSize: 64
[    20.918]     WinASegment: 0xa000
[    20.918]     WinBSegment: 0x0
[    20.918]     WinFuncPtr: 0xc00067ac
[    20.918]     BytesPerScanline: 100
[    20.918]     XResolution: 800
[    20.918]     YResolution: 600
[    20.918]     XCharSize: 8
[    20.918]     YCharSize: 16
[    20.918]     NumberOfPlanes: 4
[    20.918]     BitsPerPixel: 4
[    20.918]     NumberOfBanks: 1
[    20.918]     MemoryModel: 3
[    20.918]     BankSize: 0
[    20.918]     NumberOfImages: 2
[    20.918]     RedMaskSize: 0
[    20.918]     RedFieldPosition: 0
[    20.918]     GreenMaskSize: 0
[    20.918]     GreenFieldPosition: 0
[    20.918]     BlueMaskSize: 0
[    20.918]     BlueFieldPosition: 0
[    20.918]     RsvdMaskSize: 0
[    20.918]     RsvdFieldPosition: 0
[    20.918]     DirectColorModeInfo: 0
[    20.918]     PhysBasePtr: 0x0
[    20.918]     LinBytesPerScanLine: 100
[    20.918]     BnkNumberOfImagePages: 2
[    20.918]     LinNumberOfImagePages: 2
[    20.918]     LinRedMaskSize: 0
[    20.918]     LinRedFieldPosition: 0
[    20.918]     LinGreenMaskSize: 0
[    20.918]     LinGreenFieldPosition: 0
[    20.918]     LinBlueMaskSize: 0
[    20.918]     LinBlueFieldPosition: 0
[    20.918]     LinRsvdMaskSize: 0
[    20.918]     LinRsvdFieldPosition: 0
[    20.918]     MaxPixelClock: 108500000
[    20.919] Mode: 103 (800x600)
[    20.919]     ModeAttributes: 0x3bf
[    20.919]     WinAAttributes: 0x7
[    20.919]     WinBAttributes: 0x0
[    20.919]     WinGranularity: 64
[    20.919]     WinSize: 64
[    20.919]     WinASegment: 0xa000
[    20.919]     WinBSegment: 0x0
[    20.919]     WinFuncPtr: 0xc00067ac
[    20.919]     BytesPerScanline: 800
[    20.919]     XResolution: 800
[    20.919]     YResolution: 600
[    20.919]     XCharSize: 8
[    20.919]     YCharSize: 16
[    20.919]     NumberOfPlanes: 1
[    20.919]     BitsPerPixel: 8
[    20.919]     NumberOfBanks: 1
[    20.919]     MemoryModel: 4
[    20.919]     BankSize: 0
[    20.919]     NumberOfImages: 6
[    20.919]     RedMaskSize: 0
[    20.919]     RedFieldPosition: 0
[    20.919]     GreenMaskSize: 0
[    20.919]     GreenFieldPosition: 0
[    20.919]     BlueMaskSize: 0
[    20.919]     BlueFieldPosition: 0
[    20.919]     RsvdMaskSize: 0
[    20.919]     RsvdFieldPosition: 0
[    20.919]     DirectColorModeInfo: 0
[    20.919]     PhysBasePtr: 0xdf000000
[    20.919]     LinBytesPerScanLine: 800
[    20.919]     BnkNumberOfImagePages: 6
[    20.919]     LinNumberOfImagePages: 6
[    20.919]     LinRedMaskSize: 0
[    20.919]     LinRedFieldPosition: 0
[    20.919]     LinGreenMaskSize: 0
[    20.919]     LinGreenFieldPosition: 0
[    20.919]     LinBlueMaskSize: 0
[    20.919]     LinBlueFieldPosition: 0
[    20.919]     LinRsvdMaskSize: 0
[    20.919]     LinRsvdFieldPosition: 0
[    20.919]     MaxPixelClock: 229500000
[    20.920] Mode: 104 (1024x768)
[    20.920]     ModeAttributes: 0x33f
[    20.920]     WinAAttributes: 0x7
[    20.920]     WinBAttributes: 0x0
[    20.920]     WinGranularity: 64
[    20.920]     WinSize: 64
[    20.920]     WinASegment: 0xa000
[    20.920]     WinBSegment: 0x0
[    20.920]     WinFuncPtr: 0xc00067ac
[    20.920]     BytesPerScanline: 128
[    20.920]     XResolution: 1024
[    20.920]     YResolution: 768
[    20.920]     XCharSize: 8
[    20.920]     YCharSize: 16
[    20.920]     NumberOfPlanes: 4
[    20.920]     BitsPerPixel: 4
[    20.920]     NumberOfBanks: 1
[    20.920]     MemoryModel: 3
[    20.920]     BankSize: 0
[    20.920]     NumberOfImages: 1
[    20.920]     RedMaskSize: 0
[    20.920]     RedFieldPosition: 0
[    20.920]     GreenMaskSize: 0
[    20.920]     GreenFieldPosition: 0
[    20.920]     BlueMaskSize: 0
[    20.920]     BlueFieldPosition: 0
[    20.920]     RsvdMaskSize: 0
[    20.920]     RsvdFieldPosition: 0
[    20.920]     DirectColorModeInfo: 0
[    20.920]     PhysBasePtr: 0x0
[    20.920]     LinBytesPerScanLine: 128
[    20.920]     BnkNumberOfImagePages: 1
[    20.920]     LinNumberOfImagePages: 1
[    20.920]     LinRedMaskSize: 0
[    20.920]     LinRedFieldPosition: 0
[    20.920]     LinGreenMaskSize: 0
[    20.920]     LinGreenFieldPosition: 0
[    20.920]     LinBlueMaskSize: 0
[    20.920]     LinBlueFieldPosition: 0
[    20.920]     LinRsvdMaskSize: 0
[    20.920]     LinRsvdFieldPosition: 0
[    20.920]     MaxPixelClock: 108500000
[    20.921] Mode: 105 (1024x768)
[    20.921]     ModeAttributes: 0x3bf
[    20.921]     WinAAttributes: 0x7
[    20.921]     WinBAttributes: 0x0
[    20.921]     WinGranularity: 64
[    20.921]     WinSize: 64
[    20.921]     WinASegment: 0xa000
[    20.921]     WinBSegment: 0x0
[    20.921]     WinFuncPtr: 0xc00067ac
[    20.921]     BytesPerScanline: 1024
[    20.921]     XResolution: 1024
[    20.921]     YResolution: 768
[    20.921]     XCharSize: 8
[    20.921]     YCharSize: 16
[    20.921]     NumberOfPlanes: 1
[    20.921]     BitsPerPixel: 8
[    20.921]     NumberOfBanks: 1
[    20.921]     MemoryModel: 4
[    20.921]     BankSize: 0
[    20.921]     NumberOfImages: 3
[    20.921]     RedMaskSize: 0
[    20.921]     RedFieldPosition: 0
[    20.921]     GreenMaskSize: 0
[    20.921]     GreenFieldPosition: 0
[    20.921]     BlueMaskSize: 0
[    20.921]     BlueFieldPosition: 0
[    20.921]     RsvdMaskSize: 0
[    20.921]     RsvdFieldPosition: 0
[    20.921]     DirectColorModeInfo: 0
[    20.921]     PhysBasePtr: 0xdf000000
[    20.921]     LinBytesPerScanLine: 1024
[    20.921]     BnkNumberOfImagePages: 3
[    20.921]     LinNumberOfImagePages: 3
[    20.921]     LinRedMaskSize: 0
[    20.921]     LinRedFieldPosition: 0
[    20.921]     LinGreenMaskSize: 0
[    20.921]     LinGreenFieldPosition: 0
[    20.921]     LinBlueMaskSize: 0
[    20.921]     LinBlueFieldPosition: 0
[    20.921]     LinRsvdMaskSize: 0
[    20.921]     LinRsvdFieldPosition: 0
[    20.921]     MaxPixelClock: 229500000
[    20.922] Mode: 106 (1280x1024)
[    20.922]     ModeAttributes: 0x33f
[    20.922]     WinAAttributes: 0x7
[    20.922]     WinBAttributes: 0x0
[    20.922]     WinGranularity: 64
[    20.922]     WinSize: 64
[    20.922]     WinASegment: 0xa000
[    20.922]     WinBSegment: 0x0
[    20.922]     WinFuncPtr: 0xc00067ac
[    20.922]     BytesPerScanline: 160
[    20.922]     XResolution: 1280
[    20.922]     YResolution: 1024
[    20.922]     XCharSize: 8
[    20.922]     YCharSize: 16
[    20.922]     NumberOfPlanes: 4
[    20.922]     BitsPerPixel: 4
[    20.922]     NumberOfBanks: 1
[    20.922]     MemoryModel: 3
[    20.922]     BankSize: 0
[    20.922]     NumberOfImages: 1
[    20.922]     RedMaskSize: 0
[    20.922]     RedFieldPosition: 0
[    20.922]     GreenMaskSize: 0
[    20.922]     GreenFieldPosition: 0
[    20.922]     BlueMaskSize: 0
[    20.922]     BlueFieldPosition: 0
[    20.922]     RsvdMaskSize: 0
[    20.922]     RsvdFieldPosition: 0
[    20.922]     DirectColorModeInfo: 0
[    20.922]     PhysBasePtr: 0x0
[    20.922]     LinBytesPerScanLine: 160
[    20.922]     BnkNumberOfImagePages: 1
[    20.922]     LinNumberOfImagePages: 1
[    20.922]     LinRedMaskSize: 0
[    20.922]     LinRedFieldPosition: 0
[    20.922]     LinGreenMaskSize: 0
[    20.922]     LinGreenFieldPosition: 0
[    20.922]     LinBlueMaskSize: 0
[    20.922]     LinBlueFieldPosition: 0
[    20.922]     LinRsvdMaskSize: 0
[    20.922]     LinRsvdFieldPosition: 0
[    20.922]     MaxPixelClock: 108500000
[    20.923] Mode: 107 (1280x1024)
[    20.923]     ModeAttributes: 0x3bf
[    20.923]     WinAAttributes: 0x7
[    20.923]     WinBAttributes: 0x0
[    20.923]     WinGranularity: 64
[    20.923]     WinSize: 64
[    20.923]     WinASegment: 0xa000
[    20.923]     WinBSegment: 0x0
[    20.923]     WinFuncPtr: 0xc00067ac
[    20.923]     BytesPerScanline: 1280
[    20.923]     XResolution: 1280
[    20.923]     YResolution: 1024
[    20.923]     XCharSize: 8
[    20.923]     YCharSize: 16
[    20.923]     NumberOfPlanes: 1
[    20.923]     BitsPerPixel: 8
[    20.923]     NumberOfBanks: 1
[    20.923]     MemoryModel: 4
[    20.923]     BankSize: 0
[    20.923]     NumberOfImages: 1
[    20.923]     RedMaskSize: 0
[    20.923]     RedFieldPosition: 0
[    20.923]     GreenMaskSize: 0
[    20.923]     GreenFieldPosition: 0
[    20.923]     BlueMaskSize: 0
[    20.923]     BlueFieldPosition: 0
[    20.923]     RsvdMaskSize: 0
[    20.923]     RsvdFieldPosition: 0
[    20.923]     DirectColorModeInfo: 0
[    20.923]     PhysBasePtr: 0xdf000000
[    20.923]     LinBytesPerScanLine: 1280
[    20.923]     BnkNumberOfImagePages: 1
[    20.923]     LinNumberOfImagePages: 1
[    20.923]     LinRedMaskSize: 0
[    20.923]     LinRedFieldPosition: 0
[    20.923]     LinGreenMaskSize: 0
[    20.923]     LinGreenFieldPosition: 0
[    20.923]     LinBlueMaskSize: 0
[    20.923]     LinBlueFieldPosition: 0
[    20.923]     LinRsvdMaskSize: 0
[    20.923]     LinRsvdFieldPosition: 0
[    20.923]     MaxPixelClock: 229500000
[    20.924] Mode: 10e (320x200)
[    20.924]     ModeAttributes: 0x3bf
[    20.924]     WinAAttributes: 0x7
[    20.924]     WinBAttributes: 0x0
[    20.924]     WinGranularity: 64
[    20.924]     WinSize: 64
[    20.924]     WinASegment: 0xa000
[    20.924]     WinBSegment: 0x0
[    20.924]     WinFuncPtr: 0xc00067ac
[    20.924]     BytesPerScanline: 640
[    20.924]     XResolution: 320
[    20.924]     YResolution: 200
[    20.924]     XCharSize: 8
[    20.924]     YCharSize: 8
[    20.924]     NumberOfPlanes: 1
[    20.924]     BitsPerPixel: 16
[    20.924]     NumberOfBanks: 1
[    20.924]     MemoryModel: 6
[    20.924]     BankSize: 0
[    20.924]     NumberOfImages: 30
[    20.924]     RedMaskSize: 5
[    20.924]     RedFieldPosition: 11
[    20.924]     GreenMaskSize: 6
[    20.924]     GreenFieldPosition: 5
[    20.924]     BlueMaskSize: 5
[    20.924]     BlueFieldPosition: 0
[    20.924]     RsvdMaskSize: 0
[    20.924]     RsvdFieldPosition: 0
[    20.924]     DirectColorModeInfo: 0
[    20.924]     PhysBasePtr: 0xdf000000
[    20.924]     LinBytesPerScanLine: 640
[    20.924]     BnkNumberOfImagePages: 30
[    20.924]     LinNumberOfImagePages: 30
[    20.924]     LinRedMaskSize: 5
[    20.924]     LinRedFieldPosition: 11
[    20.924]     LinGreenMaskSize: 6
[    20.924]     LinGreenFieldPosition: 5
[    20.924]     LinBlueMaskSize: 5
[    20.924]     LinBlueFieldPosition: 0
[    20.924]     LinRsvdMaskSize: 0
[    20.924]     LinRsvdFieldPosition: 0
[    20.924]     MaxPixelClock: 229500000
[    20.925] *Mode: 10f (320x200)
[    20.925]     ModeAttributes: 0x3bf
[    20.925]     WinAAttributes: 0x7
[    20.925]     WinBAttributes: 0x0
[    20.925]     WinGranularity: 64
[    20.925]     WinSize: 64
[    20.925]     WinASegment: 0xa000
[    20.925]     WinBSegment: 0x0
[    20.925]     WinFuncPtr: 0xc00067ac
[    20.925]     BytesPerScanline: 1280
[    20.925]     XResolution: 320
[    20.925]     YResolution: 200
[    20.925]     XCharSize: 8
[    20.925]     YCharSize: 8
[    20.925]     NumberOfPlanes: 1
[    20.925]     BitsPerPixel: 32
[    20.925]     NumberOfBanks: 1
[    20.925]     MemoryModel: 6
[    20.925]     BankSize: 0
[    20.925]     NumberOfImages: 14
[    20.925]     RedMaskSize: 8
[    20.925]     RedFieldPosition: 16
[    20.925]     GreenMaskSize: 8
[    20.925]     GreenFieldPosition: 8
[    20.925]     BlueMaskSize: 8
[    20.925]     BlueFieldPosition: 0
[    20.925]     RsvdMaskSize: 8
[    20.925]     RsvdFieldPosition: 24
[    20.925]     DirectColorModeInfo: 0
[    20.925]     PhysBasePtr: 0xdf000000
[    20.925]     LinBytesPerScanLine: 1280
[    20.925]     BnkNumberOfImagePages: 14
[    20.925]     LinNumberOfImagePages: 14
[    20.925]     LinRedMaskSize: 8
[    20.925]     LinRedFieldPosition: 16
[    20.925]     LinGreenMaskSize: 8
[    20.925]     LinGreenFieldPosition: 8
[    20.925]     LinBlueMaskSize: 8
[    20.925]     LinBlueFieldPosition: 0
[    20.925]     LinRsvdMaskSize: 8
[    20.925]     LinRsvdFieldPosition: 24
[    20.925]     MaxPixelClock: 229500000
[    20.926] Mode: 111 (640x480)
[    20.926]     ModeAttributes: 0x3bf
[    20.926]     WinAAttributes: 0x7
[    20.926]     WinBAttributes: 0x0
[    20.926]     WinGranularity: 64
[    20.926]     WinSize: 64
[    20.926]     WinASegment: 0xa000
[    20.926]     WinBSegment: 0x0
[    20.926]     WinFuncPtr: 0xc00067ac
[    20.926]     BytesPerScanline: 1280
[    20.926]     XResolution: 640
[    20.926]     YResolution: 480
[    20.926]     XCharSize: 8
[    20.926]     YCharSize: 16
[    20.926]     NumberOfPlanes: 1
[    20.926]     BitsPerPixel: 16
[    20.926]     NumberOfBanks: 1
[    20.926]     MemoryModel: 6
[    20.926]     BankSize: 0
[    20.926]     NumberOfImages: 4
[    20.926]     RedMaskSize: 5
[    20.926]     RedFieldPosition: 11
[    20.926]     GreenMaskSize: 6
[    20.926]     GreenFieldPosition: 5
[    20.926]     BlueMaskSize: 5
[    20.926]     BlueFieldPosition: 0
[    20.926]     RsvdMaskSize: 0
[    20.926]     RsvdFieldPosition: 0
[    20.926]     DirectColorModeInfo: 0
[    20.926]     PhysBasePtr: 0xdf000000
[    20.926]     LinBytesPerScanLine: 1280
[    20.926]     BnkNumberOfImagePages: 4
[    20.926]     LinNumberOfImagePages: 4
[    20.926]     LinRedMaskSize: 5
[    20.926]     LinRedFieldPosition: 11
[    20.926]     LinGreenMaskSize: 6
[    20.926]     LinGreenFieldPosition: 5
[    20.926]     LinBlueMaskSize: 5
[    20.926]     LinBlueFieldPosition: 0
[    20.926]     LinRsvdMaskSize: 0
[    20.926]     LinRsvdFieldPosition: 0
[    20.926]     MaxPixelClock: 229500000
[    20.927] *Mode: 112 (640x480)
[    20.927]     ModeAttributes: 0x3bf
[    20.927]     WinAAttributes: 0x7
[    20.927]     WinBAttributes: 0x0
[    20.927]     WinGranularity: 64
[    20.927]     WinSize: 64
[    20.927]     WinASegment: 0xa000
[    20.927]     WinBSegment: 0x0
[    20.927]     WinFuncPtr: 0xc00067ac
[    20.927]     BytesPerScanline: 2560
[    20.927]     XResolution: 640
[    20.927]     YResolution: 480
[    20.927]     XCharSize: 8
[    20.927]     YCharSize: 16
[    20.927]     NumberOfPlanes: 1
[    20.927]     BitsPerPixel: 32
[    20.927]     NumberOfBanks: 1
[    20.927]     MemoryModel: 6
[    20.927]     BankSize: 0
[    20.927]     NumberOfImages: 1
[    20.927]     RedMaskSize: 8
[    20.927]     RedFieldPosition: 16
[    20.927]     GreenMaskSize: 8
[    20.927]     GreenFieldPosition: 8
[    20.927]     BlueMaskSize: 8
[    20.927]     BlueFieldPosition: 0
[    20.927]     RsvdMaskSize: 8
[    20.927]     RsvdFieldPosition: 24
[    20.927]     DirectColorModeInfo: 0
[    20.927]     PhysBasePtr: 0xdf000000
[    20.927]     LinBytesPerScanLine: 2560
[    20.927]     BnkNumberOfImagePages: 1
[    20.927]     LinNumberOfImagePages: 1
[    20.927]     LinRedMaskSize: 8
[    20.927]     LinRedFieldPosition: 16
[    20.927]     LinGreenMaskSize: 8
[    20.927]     LinGreenFieldPosition: 8
[    20.927]     LinBlueMaskSize: 8
[    20.927]     LinBlueFieldPosition: 0
[    20.927]     LinRsvdMaskSize: 8
[    20.927]     LinRsvdFieldPosition: 24
[    20.927]     MaxPixelClock: 229500000
[    20.928] Mode: 114 (800x600)
[    20.928]     ModeAttributes: 0x3bf
[    20.928]     WinAAttributes: 0x7
[    20.928]     WinBAttributes: 0x0
[    20.928]     WinGranularity: 64
[    20.928]     WinSize: 64
[    20.928]     WinASegment: 0xa000
[    20.928]     WinBSegment: 0x0
[    20.928]     WinFuncPtr: 0xc00067ac
[    20.928]     BytesPerScanline: 1600
[    20.928]     XResolution: 800
[    20.928]     YResolution: 600
[    20.928]     XCharSize: 8
[    20.928]     YCharSize: 16
[    20.928]     NumberOfPlanes: 1
[    20.928]     BitsPerPixel: 16
[    20.928]     NumberOfBanks: 1
[    20.928]     MemoryModel: 6
[    20.928]     BankSize: 0
[    20.928]     NumberOfImages: 2
[    20.928]     RedMaskSize: 5
[    20.928]     RedFieldPosition: 11
[    20.928]     GreenMaskSize: 6
[    20.928]     GreenFieldPosition: 5
[    20.928]     BlueMaskSize: 5
[    20.928]     BlueFieldPosition: 0
[    20.928]     RsvdMaskSize: 0
[    20.928]     RsvdFieldPosition: 0
[    20.928]     DirectColorModeInfo: 0
[    20.928]     PhysBasePtr: 0xdf000000
[    20.928]     LinBytesPerScanLine: 1600
[    20.928]     BnkNumberOfImagePages: 2
[    20.928]     LinNumberOfImagePages: 2
[    20.928]     LinRedMaskSize: 5
[    20.928]     LinRedFieldPosition: 11
[    20.928]     LinGreenMaskSize: 6
[    20.928]     LinGreenFieldPosition: 5
[    20.928]     LinBlueMaskSize: 5
[    20.928]     LinBlueFieldPosition: 0
[    20.928]     LinRsvdMaskSize: 0
[    20.928]     LinRsvdFieldPosition: 0
[    20.928]     MaxPixelClock: 229500000
[    20.929] *Mode: 115 (800x600)
[    20.929]     ModeAttributes: 0x3bf
[    20.929]     WinAAttributes: 0x7
[    20.929]     WinBAttributes: 0x0
[    20.929]     WinGranularity: 64
[    20.929]     WinSize: 64
[    20.929]     WinASegment: 0xa000
[    20.929]     WinBSegment: 0x0
[    20.929]     WinFuncPtr: 0xc00067ac
[    20.929]     BytesPerScanline: 3200
[    20.929]     XResolution: 800
[    20.929]     YResolution: 600
[    20.929]     XCharSize: 8
[    20.929]     YCharSize: 16
[    20.929]     NumberOfPlanes: 1
[    20.929]     BitsPerPixel: 32
[    20.929]     NumberOfBanks: 1
[    20.929]     MemoryModel: 6
[    20.929]     BankSize: 0
[    20.929]     NumberOfImages: 1
[    20.929]     RedMaskSize: 8
[    20.929]     RedFieldPosition: 16
[    20.929]     GreenMaskSize: 8
[    20.929]     GreenFieldPosition: 8
[    20.929]     BlueMaskSize: 8
[    20.929]     BlueFieldPosition: 0
[    20.929]     RsvdMaskSize: 8
[    20.929]     RsvdFieldPosition: 24
[    20.929]     DirectColorModeInfo: 0
[    20.929]     PhysBasePtr: 0xdf000000
[    20.929]     LinBytesPerScanLine: 3200
[    20.929]     BnkNumberOfImagePages: 1
[    20.929]     LinNumberOfImagePages: 1
[    20.929]     LinRedMaskSize: 8
[    20.929]     LinRedFieldPosition: 16
[    20.929]     LinGreenMaskSize: 8
[    20.929]     LinGreenFieldPosition: 8
[    20.929]     LinBlueMaskSize: 8
[    20.929]     LinBlueFieldPosition: 0
[    20.929]     LinRsvdMaskSize: 8
[    20.929]     LinRsvdFieldPosition: 24
[    20.929]     MaxPixelClock: 229500000
[    20.930] Mode: 117 (1024x768)
[    20.930]     ModeAttributes: 0x3bf
[    20.930]     WinAAttributes: 0x7
[    20.930]     WinBAttributes: 0x0
[    20.930]     WinGranularity: 64
[    20.930]     WinSize: 64
[    20.930]     WinASegment: 0xa000
[    20.930]     WinBSegment: 0x0
[    20.930]     WinFuncPtr: 0xc00067ac
[    20.930]     BytesPerScanline: 2048
[    20.930]     XResolution: 1024
[    20.930]     YResolution: 768
[    20.930]     XCharSize: 8
[    20.930]     YCharSize: 16
[    20.930]     NumberOfPlanes: 1
[    20.930]     BitsPerPixel: 16
[    20.930]     NumberOfBanks: 1
[    20.930]     MemoryModel: 6
[    20.930]     BankSize: 0
[    20.930]     NumberOfImages: 1
[    20.930]     RedMaskSize: 5
[    20.930]     RedFieldPosition: 11
[    20.930]     GreenMaskSize: 6
[    20.930]     GreenFieldPosition: 5
[    20.930]     BlueMaskSize: 5
[    20.930]     BlueFieldPosition: 0
[    20.930]     RsvdMaskSize: 0
[    20.930]     RsvdFieldPosition: 0
[    20.930]     DirectColorModeInfo: 0
[    20.930]     PhysBasePtr: 0xdf000000
[    20.930]     LinBytesPerScanLine: 2048
[    20.930]     BnkNumberOfImagePages: 1
[    20.930]     LinNumberOfImagePages: 1
[    20.930]     LinRedMaskSize: 5
[    20.930]     LinRedFieldPosition: 11
[    20.930]     LinGreenMaskSize: 6
[    20.930]     LinGreenFieldPosition: 5
[    20.930]     LinBlueMaskSize: 5
[    20.930]     LinBlueFieldPosition: 0
[    20.930]     LinRsvdMaskSize: 0
[    20.930]     LinRsvdFieldPosition: 0
[    20.930]     MaxPixelClock: 229500000
[    20.931] *Mode: 118 (1024x768)
[    20.931]     ModeAttributes: 0x3bf
[    20.931]     WinAAttributes: 0x7
[    20.931]     WinBAttributes: 0x0
[    20.931]     WinGranularity: 64
[    20.931]     WinSize: 64
[    20.931]     WinASegment: 0xa000
[    20.931]     WinBSegment: 0x0
[    20.931]     WinFuncPtr: 0xc00067ac
[    20.931]     BytesPerScanline: 4096
[    20.931]     XResolution: 1024
[    20.931]     YResolution: 768
[    20.931]     XCharSize: 8
[    20.931]     YCharSize: 16
[    20.931]     NumberOfPlanes: 1
[    20.931]     BitsPerPixel: 32
[    20.931]     NumberOfBanks: 1
[    20.931]     MemoryModel: 6
[    20.931]     BankSize: 0
[    20.931]     NumberOfImages: 1
[    20.931]     RedMaskSize: 8
[    20.931]     RedFieldPosition: 16
[    20.931]     GreenMaskSize: 8
[    20.931]     GreenFieldPosition: 8
[    20.931]     BlueMaskSize: 8
[    20.931]     BlueFieldPosition: 0
[    20.931]     RsvdMaskSize: 8
[    20.931]     RsvdFieldPosition: 24
[    20.931]     DirectColorModeInfo: 0
[    20.931]     PhysBasePtr: 0xdf000000
[    20.931]     LinBytesPerScanLine: 4096
[    20.931]     BnkNumberOfImagePages: 1
[    20.931]     LinNumberOfImagePages: 1
[    20.931]     LinRedMaskSize: 8
[    20.931]     LinRedFieldPosition: 16
[    20.931]     LinGreenMaskSize: 8
[    20.931]     LinGreenFieldPosition: 8
[    20.931]     LinBlueMaskSize: 8
[    20.931]     LinBlueFieldPosition: 0
[    20.931]     LinRsvdMaskSize: 8
[    20.931]     LinRsvdFieldPosition: 24
[    20.931]     MaxPixelClock: 229500000
[    20.932] Mode: 11a (1280x1024)
[    20.932]     ModeAttributes: 0x3bf
[    20.932]     WinAAttributes: 0x7
[    20.932]     WinBAttributes: 0x0
[    20.932]     WinGranularity: 64
[    20.932]     WinSize: 64
[    20.932]     WinASegment: 0xa000
[    20.932]     WinBSegment: 0x0
[    20.932]     WinFuncPtr: 0xc00067ac
[    20.932]     BytesPerScanline: 2560
[    20.932]     XResolution: 1280
[    20.932]     YResolution: 1024
[    20.932]     XCharSize: 8
[    20.932]     YCharSize: 16
[    20.932]     NumberOfPlanes: 1
[    20.932]     BitsPerPixel: 16
[    20.932]     NumberOfBanks: 1
[    20.932]     MemoryModel: 6
[    20.932]     BankSize: 0
[    20.932]     NumberOfImages: 1
[    20.932]     RedMaskSize: 5
[    20.932]     RedFieldPosition: 11
[    20.932]     GreenMaskSize: 6
[    20.932]     GreenFieldPosition: 5
[    20.932]     BlueMaskSize: 5
[    20.932]     BlueFieldPosition: 0
[    20.932]     RsvdMaskSize: 0
[    20.932]     RsvdFieldPosition: 0
[    20.932]     DirectColorModeInfo: 0
[    20.932]     PhysBasePtr: 0xdf000000
[    20.932]     LinBytesPerScanLine: 2560
[    20.932]     BnkNumberOfImagePages: 1
[    20.932]     LinNumberOfImagePages: 1
[    20.932]     LinRedMaskSize: 5
[    20.932]     LinRedFieldPosition: 11
[    20.932]     LinGreenMaskSize: 6
[    20.932]     LinGreenFieldPosition: 5
[    20.932]     LinBlueMaskSize: 5
[    20.932]     LinBlueFieldPosition: 0
[    20.932]     LinRsvdMaskSize: 0
[    20.932]     LinRsvdFieldPosition: 0
[    20.932]     MaxPixelClock: 229500000
[    20.933] *Mode: 11b (1280x1024)
[    20.933]     ModeAttributes: 0x3bf
[    20.933]     WinAAttributes: 0x7
[    20.933]     WinBAttributes: 0x0
[    20.933]     WinGranularity: 64
[    20.933]     WinSize: 64
[    20.933]     WinASegment: 0xa000
[    20.933]     WinBSegment: 0x0
[    20.933]     WinFuncPtr: 0xc00067ac
[    20.933]     BytesPerScanline: 5120
[    20.933]     XResolution: 1280
[    20.933]     YResolution: 1024
[    20.933]     XCharSize: 8
[    20.933]     YCharSize: 16
[    20.933]     NumberOfPlanes: 1
[    20.933]     BitsPerPixel: 32
[    20.933]     NumberOfBanks: 1
[    20.933]     MemoryModel: 6
[    20.933]     BankSize: 0
[    20.933]     NumberOfImages: 1
[    20.933]     RedMaskSize: 8
[    20.933]     RedFieldPosition: 16
[    20.933]     GreenMaskSize: 8
[    20.933]     GreenFieldPosition: 8
[    20.933]     BlueMaskSize: 8
[    20.933]     BlueFieldPosition: 0
[    20.933]     RsvdMaskSize: 8
[    20.933]     RsvdFieldPosition: 24
[    20.933]     DirectColorModeInfo: 0
[    20.933]     PhysBasePtr: 0xdf000000
[    20.933]     LinBytesPerScanLine: 5120
[    20.933]     BnkNumberOfImagePages: 1
[    20.933]     LinNumberOfImagePages: 1
[    20.933]     LinRedMaskSize: 8
[    20.933]     LinRedFieldPosition: 16
[    20.933]     LinGreenMaskSize: 8
[    20.933]     LinGreenFieldPosition: 8
[    20.933]     LinBlueMaskSize: 8
[    20.933]     LinBlueFieldPosition: 0
[    20.933]     LinRsvdMaskSize: 8
[    20.933]     LinRsvdFieldPosition: 24
[    20.933]     MaxPixelClock: 229500000
[    20.933] Mode: 130 (320x200)
[    20.933]     ModeAttributes: 0x3bf
[    20.933]     WinAAttributes: 0x7
[    20.933]     WinBAttributes: 0x0
[    20.933]     WinGranularity: 64
[    20.933]     WinSize: 64
[    20.933]     WinASegment: 0xa000
[    20.934]     WinBSegment: 0x0
[    20.934]     WinFuncPtr: 0xc00067ac
[    20.934]     BytesPerScanline: 320
[    20.934]     XResolution: 320
[    20.934]     YResolution: 200
[    20.934]     XCharSize: 8
[    20.934]     YCharSize: 8
[    20.934]     NumberOfPlanes: 1
[    20.934]     BitsPerPixel: 8
[    20.934]     NumberOfBanks: 1
[    20.934]     MemoryModel: 4
[    20.934]     BankSize: 0
[    20.934]     NumberOfImages: 62
[    20.934]     RedMaskSize: 0
[    20.934]     RedFieldPosition: 0
[    20.934]     GreenMaskSize: 0
[    20.934]     GreenFieldPosition: 0
[    20.934]     BlueMaskSize: 0
[    20.934]     BlueFieldPosition: 0
[    20.934]     RsvdMaskSize: 0
[    20.934]     RsvdFieldPosition: 0
[    20.934]     DirectColorModeInfo: 0
[    20.934]     PhysBasePtr: 0xdf000000
[    20.934]     LinBytesPerScanLine: 320
[    20.934]     BnkNumberOfImagePages: 62
[    20.934]     LinNumberOfImagePages: 62
[    20.934]     LinRedMaskSize: 0
[    20.934]     LinRedFieldPosition: 0
[    20.934]     LinGreenMaskSize: 0
[    20.934]     LinGreenFieldPosition: 0
[    20.934]     LinBlueMaskSize: 0
[    20.934]     LinBlueFieldPosition: 0
[    20.934]     LinRsvdMaskSize: 0
[    20.934]     LinRsvdFieldPosition: 0
[    20.934]     MaxPixelClock: 229500000
[    20.934] Mode: 131 (320x400)
[    20.934]     ModeAttributes: 0x3bf
[    20.934]     WinAAttributes: 0x7
[    20.934]     WinBAttributes: 0x0
[    20.934]     WinGranularity: 64
[    20.934]     WinSize: 64
[    20.934]     WinASegment: 0xa000
[    20.934]     WinBSegment: 0x0
[    20.934]     WinFuncPtr: 0xc00067ac
[    20.934]     BytesPerScanline: 320
[    20.934]     XResolution: 320
[    20.934]     YResolution: 400
[    20.934]     XCharSize: 8
[    20.934]     YCharSize: 16
[    20.934]     NumberOfPlanes: 1
[    20.934]     BitsPerPixel: 8
[    20.934]     NumberOfBanks: 1
[    20.934]     MemoryModel: 4
[    20.934]     BankSize: 0
[    20.934]     NumberOfImages: 30
[    20.934]     RedMaskSize: 0
[    20.934]     RedFieldPosition: 0
[    20.934]     GreenMaskSize: 0
[    20.934]     GreenFieldPosition: 0
[    20.935]     BlueMaskSize: 0
[    20.935]     BlueFieldPosition: 0
[    20.935]     RsvdMaskSize: 0
[    20.935]     RsvdFieldPosition: 0
[    20.935]     DirectColorModeInfo: 0
[    20.935]     PhysBasePtr: 0xdf000000
[    20.935]     LinBytesPerScanLine: 320
[    20.935]     BnkNumberOfImagePages: 30
[    20.935]     LinNumberOfImagePages: 30
[    20.935]     LinRedMaskSize: 0
[    20.935]     LinRedFieldPosition: 0
[    20.935]     LinGreenMaskSize: 0
[    20.935]     LinGreenFieldPosition: 0
[    20.935]     LinBlueMaskSize: 0
[    20.935]     LinBlueFieldPosition: 0
[    20.935]     LinRsvdMaskSize: 0
[    20.935]     LinRsvdFieldPosition: 0
[    20.935]     MaxPixelClock: 229500000
[    20.935] Mode: 132 (320x400)
[    20.935]     ModeAttributes: 0x3bf
[    20.935]     WinAAttributes: 0x7
[    20.935]     WinBAttributes: 0x0
[    20.935]     WinGranularity: 64
[    20.935]     WinSize: 64
[    20.935]     WinASegment: 0xa000
[    20.935]     WinBSegment: 0x0
[    20.935]     WinFuncPtr: 0xc00067ac
[    20.935]     BytesPerScanline: 640
[    20.935]     XResolution: 320
[    20.935]     YResolution: 400
[    20.935]     XCharSize: 8
[    20.935]     YCharSize: 16
[    20.935]     NumberOfPlanes: 1
[    20.935]     BitsPerPixel: 16
[    20.935]     NumberOfBanks: 1
[    20.935]     MemoryModel: 6
[    20.935]     BankSize: 0
[    20.935]     NumberOfImages: 14
[    20.935]     RedMaskSize: 5
[    20.935]     RedFieldPosition: 11
[    20.935]     GreenMaskSize: 6
[    20.935]     GreenFieldPosition: 5
[    20.935]     BlueMaskSize: 5
[    20.935]     BlueFieldPosition: 0
[    20.935]     RsvdMaskSize: 0
[    20.935]     RsvdFieldPosition: 0
[    20.935]     DirectColorModeInfo: 0
[    20.935]     PhysBasePtr: 0xdf000000
[    20.935]     LinBytesPerScanLine: 640
[    20.935]     BnkNumberOfImagePages: 14
[    20.935]     LinNumberOfImagePages: 14
[    20.935]     LinRedMaskSize: 5
[    20.935]     LinRedFieldPosition: 11
[    20.935]     LinGreenMaskSize: 6
[    20.935]     LinGreenFieldPosition: 5
[    20.935]     LinBlueMaskSize: 5
[    20.935]     LinBlueFieldPosition: 0
[    20.935]     LinRsvdMaskSize: 0
[    20.935]     LinRsvdFieldPosition: 0
[    20.935]     MaxPixelClock: 229500000
[    20.936] *Mode: 133 (320x400)
[    20.936]     ModeAttributes: 0x3bf
[    20.936]     WinAAttributes: 0x7
[    20.936]     WinBAttributes: 0x0
[    20.936]     WinGranularity: 64
[    20.936]     WinSize: 64
[    20.936]     WinASegment: 0xa000
[    20.936]     WinBSegment: 0x0
[    20.936]     WinFuncPtr: 0xc00067ac
[    20.936]     BytesPerScanline: 1280
[    20.936]     XResolution: 320
[    20.936]     YResolution: 400
[    20.936]     XCharSize: 8
[    20.936]     YCharSize: 16
[    20.936]     NumberOfPlanes: 1
[    20.936]     BitsPerPixel: 32
[    20.936]     NumberOfBanks: 1
[    20.936]     MemoryModel: 6
[    20.936]     BankSize: 0
[    20.936]     NumberOfImages: 6
[    20.936]     RedMaskSize: 8
[    20.936]     RedFieldPosition: 16
[    20.936]     GreenMaskSize: 8
[    20.936]     GreenFieldPosition: 8
[    20.936]     BlueMaskSize: 8
[    20.936]     BlueFieldPosition: 0
[    20.936]     RsvdMaskSize: 8
[    20.936]     RsvdFieldPosition: 24
[    20.936]     DirectColorModeInfo: 0
[    20.936]     PhysBasePtr: 0xdf000000
[    20.936]     LinBytesPerScanLine: 1280
[    20.936]     BnkNumberOfImagePages: 6
[    20.936]     LinNumberOfImagePages: 6
[    20.936]     LinRedMaskSize: 8
[    20.936]     LinRedFieldPosition: 16
[    20.936]     LinGreenMaskSize: 8
[    20.936]     LinGreenFieldPosition: 8
[    20.936]     LinBlueMaskSize: 8
[    20.936]     LinBlueFieldPosition: 0
[    20.936]     LinRsvdMaskSize: 8
[    20.936]     LinRsvdFieldPosition: 24
[    20.936]     MaxPixelClock: 229500000
[    20.937] Mode: 134 (320x240)
[    20.937]     ModeAttributes: 0x3bf
[    20.937]     WinAAttributes: 0x7
[    20.937]     WinBAttributes: 0x0
[    20.937]     WinGranularity: 64
[    20.937]     WinSize: 64
[    20.937]     WinASegment: 0xa000
[    20.937]     WinBSegment: 0x0
[    20.937]     WinFuncPtr: 0xc00067ac
[    20.937]     BytesPerScanline: 320
[    20.937]     XResolution: 320
[    20.937]     YResolution: 240
[    20.937]     XCharSize: 8
[    20.937]     YCharSize: 8
[    20.937]     NumberOfPlanes: 1
[    20.937]     BitsPerPixel: 8
[    20.937]     NumberOfBanks: 1
[    20.937]     MemoryModel: 4
[    20.937]     BankSize: 0
[    20.937]     NumberOfImages: 30
[    20.937]     RedMaskSize: 0
[    20.937]     RedFieldPosition: 0
[    20.937]     GreenMaskSize: 0
[    20.937]     GreenFieldPosition: 0
[    20.937]     BlueMaskSize: 0
[    20.937]     BlueFieldPosition: 0
[    20.937]     RsvdMaskSize: 0
[    20.937]     RsvdFieldPosition: 0
[    20.937]     DirectColorModeInfo: 0
[    20.937]     PhysBasePtr: 0xdf000000
[    20.937]     LinBytesPerScanLine: 320
[    20.937]     BnkNumberOfImagePages: 30
[    20.937]     LinNumberOfImagePages: 30
[    20.937]     LinRedMaskSize: 0
[    20.937]     LinRedFieldPosition: 0
[    20.937]     LinGreenMaskSize: 0
[    20.937]     LinGreenFieldPosition: 0
[    20.937]     LinBlueMaskSize: 0
[    20.937]     LinBlueFieldPosition: 0
[    20.937]     LinRsvdMaskSize: 0
[    20.937]     LinRsvdFieldPosition: 0
[    20.937]     MaxPixelClock: 229500000
[    20.938] Mode: 135 (320x240)
[    20.938]     ModeAttributes: 0x3bf
[    20.938]     WinAAttributes: 0x7
[    20.938]     WinBAttributes: 0x0
[    20.938]     WinGranularity: 64
[    20.938]     WinSize: 64
[    20.938]     WinASegment: 0xa000
[    20.938]     WinBSegment: 0x0
[    20.938]     WinFuncPtr: 0xc00067ac
[    20.938]     BytesPerScanline: 640
[    20.938]     XResolution: 320
[    20.938]     YResolution: 240
[    20.938]     XCharSize: 8
[    20.938]     YCharSize: 8
[    20.938]     NumberOfPlanes: 1
[    20.938]     BitsPerPixel: 16
[    20.938]     NumberOfBanks: 1
[    20.938]     MemoryModel: 6
[    20.938]     BankSize: 0
[    20.938]     NumberOfImages: 19
[    20.938]     RedMaskSize: 5
[    20.938]     RedFieldPosition: 11
[    20.938]     GreenMaskSize: 6
[    20.938]     GreenFieldPosition: 5
[    20.938]     BlueMaskSize: 5
[    20.938]     BlueFieldPosition: 0
[    20.938]     RsvdMaskSize: 0
[    20.938]     RsvdFieldPosition: 0
[    20.938]     DirectColorModeInfo: 0
[    20.938]     PhysBasePtr: 0xdf000000
[    20.938]     LinBytesPerScanLine: 640
[    20.938]     BnkNumberOfImagePages: 19
[    20.938]     LinNumberOfImagePages: 19
[    20.938]     LinRedMaskSize: 5
[    20.938]     LinRedFieldPosition: 11
[    20.938]     LinGreenMaskSize: 6
[    20.938]     LinGreenFieldPosition: 5
[    20.938]     LinBlueMaskSize: 5
[    20.938]     LinBlueFieldPosition: 0
[    20.938]     LinRsvdMaskSize: 0
[    20.938]     LinRsvdFieldPosition: 0
[    20.938]     MaxPixelClock: 229500000
[    20.939] *Mode: 136 (320x240)
[    20.939]     ModeAttributes: 0x3bf
[    20.939]     WinAAttributes: 0x7
[    20.939]     WinBAttributes: 0x0
[    20.939]     WinGranularity: 64
[    20.939]     WinSize: 64
[    20.939]     WinASegment: 0xa000
[    20.939]     WinBSegment: 0x0
[    20.939]     WinFuncPtr: 0xc00067ac
[    20.939]     BytesPerScanline: 1280
[    20.939]     XResolution: 320
[    20.939]     YResolution: 240
[    20.939]     XCharSize: 8
[    20.939]     YCharSize: 8
[    20.939]     NumberOfPlanes: 1
[    20.939]     BitsPerPixel: 32
[    20.939]     NumberOfBanks: 1
[    20.939]     MemoryModel: 6
[    20.939]     BankSize: 0
[    20.939]     NumberOfImages: 10
[    20.939]     RedMaskSize: 8
[    20.939]     RedFieldPosition: 16
[    20.939]     GreenMaskSize: 8
[    20.939]     GreenFieldPosition: 8
[    20.939]     BlueMaskSize: 8
[    20.939]     BlueFieldPosition: 0
[    20.939]     RsvdMaskSize: 8
[    20.939]     RsvdFieldPosition: 24
[    20.939]     DirectColorModeInfo: 0
[    20.939]     PhysBasePtr: 0xdf000000
[    20.939]     LinBytesPerScanLine: 1280
[    20.939]     BnkNumberOfImagePages: 10
[    20.939]     LinNumberOfImagePages: 10
[    20.939]     LinRedMaskSize: 8
[    20.939]     LinRedFieldPosition: 16
[    20.939]     LinGreenMaskSize: 8
[    20.939]     LinGreenFieldPosition: 8
[    20.939]     LinBlueMaskSize: 8
[    20.939]     LinBlueFieldPosition: 0
[    20.939]     LinRsvdMaskSize: 8
[    20.939]     LinRsvdFieldPosition: 24
[    20.939]     MaxPixelClock: 229500000
[    20.940] Mode: 13d (640x400)
[    20.940]     ModeAttributes: 0x3bf
[    20.940]     WinAAttributes: 0x7
[    20.940]     WinBAttributes: 0x0
[    20.940]     WinGranularity: 64
[    20.940]     WinSize: 64
[    20.940]     WinASegment: 0xa000
[    20.940]     WinBSegment: 0x0
[    20.940]     WinFuncPtr: 0xc00067ac
[    20.940]     BytesPerScanline: 1280
[    20.940]     XResolution: 640
[    20.940]     YResolution: 400
[    20.940]     XCharSize: 8
[    20.940]     YCharSize: 16
[    20.940]     NumberOfPlanes: 1
[    20.940]     BitsPerPixel: 16
[    20.940]     NumberOfBanks: 1
[    20.940]     MemoryModel: 6
[    20.940]     BankSize: 0
[    20.940]     NumberOfImages: 6
[    20.940]     RedMaskSize: 5
[    20.940]     RedFieldPosition: 11
[    20.940]     GreenMaskSize: 6
[    20.940]     GreenFieldPosition: 5
[    20.940]     BlueMaskSize: 5
[    20.940]     BlueFieldPosition: 0
[    20.940]     RsvdMaskSize: 0
[    20.940]     RsvdFieldPosition: 0
[    20.940]     DirectColorModeInfo: 0
[    20.940]     PhysBasePtr: 0xdf000000
[    20.940]     LinBytesPerScanLine: 1280
[    20.940]     BnkNumberOfImagePages: 6
[    20.940]     LinNumberOfImagePages: 6
[    20.940]     LinRedMaskSize: 5
[    20.940]     LinRedFieldPosition: 11
[    20.940]     LinGreenMaskSize: 6
[    20.940]     LinGreenFieldPosition: 5
[    20.940]     LinBlueMaskSize: 5
[    20.940]     LinBlueFieldPosition: 0
[    20.940]     LinRsvdMaskSize: 0
[    20.940]     LinRsvdFieldPosition: 0
[    20.940]     MaxPixelClock: 229500000
[    20.941] *Mode: 13e (640x400)
[    20.941]     ModeAttributes: 0x3bf
[    20.941]     WinAAttributes: 0x7
[    20.941]     WinBAttributes: 0x0
[    20.941]     WinGranularity: 64
[    20.941]     WinSize: 64
[    20.941]     WinASegment: 0xa000
[    20.941]     WinBSegment: 0x0
[    20.941]     WinFuncPtr: 0xc00067ac
[    20.941]     BytesPerScanline: 2560
[    20.941]     XResolution: 640
[    20.941]     YResolution: 400
[    20.941]     XCharSize: 8
[    20.941]     YCharSize: 16
[    20.941]     NumberOfPlanes: 1
[    20.941]     BitsPerPixel: 32
[    20.941]     NumberOfBanks: 1
[    20.941]     MemoryModel: 6
[    20.941]     BankSize: 0
[    20.941]     NumberOfImages: 2
[    20.941]     RedMaskSize: 8
[    20.941]     RedFieldPosition: 16
[    20.941]     GreenMaskSize: 8
[    20.941]     GreenFieldPosition: 8
[    20.941]     BlueMaskSize: 8
[    20.941]     BlueFieldPosition: 0
[    20.941]     RsvdMaskSize: 8
[    20.941]     RsvdFieldPosition: 24
[    20.941]     DirectColorModeInfo: 0
[    20.941]     PhysBasePtr: 0xdf000000
[    20.941]     LinBytesPerScanLine: 2560
[    20.941]     BnkNumberOfImagePages: 2
[    20.941]     LinNumberOfImagePages: 2
[    20.941]     LinRedMaskSize: 8
[    20.941]     LinRedFieldPosition: 16
[    20.941]     LinGreenMaskSize: 8
[    20.941]     LinGreenFieldPosition: 8
[    20.941]     LinBlueMaskSize: 8
[    20.941]     LinBlueFieldPosition: 0
[    20.941]     LinRsvdMaskSize: 8
[    20.941]     LinRsvdFieldPosition: 24
[    20.941]     MaxPixelClock: 229500000
[    20.942] Mode: 145 (1600x1200)
[    20.942]     ModeAttributes: 0x3bf
[    20.942]     WinAAttributes: 0x7
[    20.942]     WinBAttributes: 0x0
[    20.942]     WinGranularity: 64
[    20.942]     WinSize: 64
[    20.942]     WinASegment: 0xa000
[    20.942]     WinBSegment: 0x0
[    20.942]     WinFuncPtr: 0xc00067ac
[    20.942]     BytesPerScanline: 1600
[    20.942]     XResolution: 1600
[    20.942]     YResolution: 1200
[    20.942]     XCharSize: 8
[    20.942]     YCharSize: 16
[    20.942]     NumberOfPlanes: 1
[    20.942]     BitsPerPixel: 8
[    20.942]     NumberOfBanks: 1
[    20.942]     MemoryModel: 4
[    20.942]     BankSize: 0
[    20.942]     NumberOfImages: 1
[    20.942]     RedMaskSize: 0
[    20.942]     RedFieldPosition: 0
[    20.942]     GreenMaskSize: 0
[    20.942]     GreenFieldPosition: 0
[    20.942]     BlueMaskSize: 0
[    20.942]     BlueFieldPosition: 0
[    20.942]     RsvdMaskSize: 0
[    20.942]     RsvdFieldPosition: 0
[    20.942]     DirectColorModeInfo: 0
[    20.942]     PhysBasePtr: 0xdf000000
[    20.942]     LinBytesPerScanLine: 1600
[    20.942]     BnkNumberOfImagePages: 1
[    20.942]     LinNumberOfImagePages: 1
[    20.942]     LinRedMaskSize: 0
[    20.942]     LinRedFieldPosition: 0
[    20.942]     LinGreenMaskSize: 0
[    20.942]     LinGreenFieldPosition: 0
[    20.942]     LinBlueMaskSize: 0
[    20.942]     LinBlueFieldPosition: 0
[    20.942]     LinRsvdMaskSize: 0
[    20.942]     LinRsvdFieldPosition: 0
[    20.942]     MaxPixelClock: 229500000
[    20.943] Mode: 146 (1600x1200)
[    20.943]     ModeAttributes: 0x3bf
[    20.943]     WinAAttributes: 0x7
[    20.943]     WinBAttributes: 0x0
[    20.943]     WinGranularity: 64
[    20.943]     WinSize: 64
[    20.943]     WinASegment: 0xa000
[    20.943]     WinBSegment: 0x0
[    20.943]     WinFuncPtr: 0xc00067ac
[    20.943]     BytesPerScanline: 3200
[    20.943]     XResolution: 1600
[    20.943]     YResolution: 1200
[    20.943]     XCharSize: 8
[    20.943]     YCharSize: 16
[    20.943]     NumberOfPlanes: 1
[    20.943]     BitsPerPixel: 16
[    20.943]     NumberOfBanks: 1
[    20.943]     MemoryModel: 6
[    20.943]     BankSize: 0
[    20.943]     NumberOfImages: 1
[    20.943]     RedMaskSize: 5
[    20.943]     RedFieldPosition: 11
[    20.943]     GreenMaskSize: 6
[    20.943]     GreenFieldPosition: 5
[    20.943]     BlueMaskSize: 5
[    20.943]     BlueFieldPosition: 0
[    20.943]     RsvdMaskSize: 0
[    20.943]     RsvdFieldPosition: 0
[    20.943]     DirectColorModeInfo: 0
[    20.943]     PhysBasePtr: 0xdf000000
[    20.943]     LinBytesPerScanLine: 3200
[    20.943]     BnkNumberOfImagePages: 1
[    20.943]     LinNumberOfImagePages: 1
[    20.943]     LinRedMaskSize: 5
[    20.943]     LinRedFieldPosition: 11
[    20.943]     LinGreenMaskSize: 6
[    20.943]     LinGreenFieldPosition: 5
[    20.943]     LinBlueMaskSize: 5
[    20.943]     LinBlueFieldPosition: 0
[    20.943]     LinRsvdMaskSize: 0
[    20.943]     LinRsvdFieldPosition: 0
[    20.943]     MaxPixelClock: 229500000
[    20.944] *Mode: 14a (1600x1200)
[    20.944]     ModeAttributes: 0x3bf
[    20.944]     WinAAttributes: 0x7
[    20.944]     WinBAttributes: 0x0
[    20.944]     WinGranularity: 64
[    20.944]     WinSize: 64
[    20.944]     WinASegment: 0xa000
[    20.944]     WinBSegment: 0x0
[    20.944]     WinFuncPtr: 0xc00067ac
[    20.944]     BytesPerScanline: 6400
[    20.944]     XResolution: 1600
[    20.944]     YResolution: 1200
[    20.944]     XCharSize: 8
[    20.944]     YCharSize: 16
[    20.944]     NumberOfPlanes: 1
[    20.944]     BitsPerPixel: 32
[    20.944]     NumberOfBanks: 1
[    20.944]     MemoryModel: 6
[    20.944]     BankSize: 0
[    20.944]     NumberOfImages: 1
[    20.944]     RedMaskSize: 8
[    20.944]     RedFieldPosition: 16
[    20.944]     GreenMaskSize: 8
[    20.944]     GreenFieldPosition: 8
[    20.944]     BlueMaskSize: 8
[    20.944]     BlueFieldPosition: 0
[    20.944]     RsvdMaskSize: 8
[    20.944]     RsvdFieldPosition: 24
[    20.944]     DirectColorModeInfo: 0
[    20.944]     PhysBasePtr: 0xdf000000
[    20.944]     LinBytesPerScanLine: 6400
[    20.944]     BnkNumberOfImagePages: 1
[    20.944]     LinNumberOfImagePages: 1
[    20.944]     LinRedMaskSize: 8
[    20.944]     LinRedFieldPosition: 16
[    20.944]     LinGreenMaskSize: 8
[    20.944]     LinGreenFieldPosition: 8
[    20.944]     LinBlueMaskSize: 8
[    20.944]     LinBlueFieldPosition: 0
[    20.944]     LinRsvdMaskSize: 8
[    20.944]     LinRsvdFieldPosition: 24
[    20.944]     MaxPixelClock: 229500000
[    20.944] 
[    20.944] (II) VESA(0): Total Memory: 224 64KB banks (14336kB)
[    20.944] (II) VESA(0): Monitor0: Using hsync range of 28.00-33.00 kHz
[    20.944] (II) VESA(0): Monitor0: Using vrefresh range of 43.00-72.00 Hz
[    20.944] (WW) VESA(0): Unable to estimate virtual size
[    20.944] (II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
[    20.944] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[    20.944] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    20.944] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    20.944] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    20.944] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[    20.944] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[    20.944] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    20.944] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    20.944] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    20.944] (II) VESA(0): Monitor0: Using hsync range of 28.00-33.00 kHz
[    20.944] (II) VESA(0): Monitor0: Using vrefresh range of 43.00-72.00 Hz
[    20.944] (WW) VESA(0): Unable to estimate virtual size
[    20.944] (II) VESA(0): Not using built-in mode "1600x1200" (hsync out of range)
[    20.944] (II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
[    20.944] (II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
[    20.944] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[    20.944] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[    20.944] (--) VESA(0): Virtual size is 800x600 (pitch 800)
[    20.944] (**) VESA(0): *Built-in mode "800x600"
[    20.944] (**) VESA(0): *Built-in mode "640x480"
[    20.944] (**) VESA(0): *Built-in mode "640x400"
[    20.944] (**) VESA(0): *Built-in mode "320x400"
[    20.944] (==) VESA(0): DPI set to (96, 96)
[    20.944] (II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
[    20.945] (**) VESA(0): Using "Shadow Framebuffer"
[    20.945] (II) Loading sub module "shadow"
[    20.945] (II) LoadModule: "shadow"
[    20.945] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    20.945] (II) Module shadow: vendor="X.Org Foundation"
[    20.945]     compiled for 1.13.0, module version = 1.1.0
[    20.945]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.945] (II) Loading sub module "fb"
[    20.945] (II) LoadModule: "fb"
[    20.945] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.945] (II) Module fb: vendor="X.Org Foundation"
[    20.945]     compiled for 1.13.0, module version = 1.0.0
[    20.945]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.945] (II) UnloadModule: "modesetting"
[    20.945] (II) Unloading modesetting
[    20.945] (II) UnloadModule: "fbdev"
[    20.945] (II) Unloading fbdev
[    20.945] (II) UnloadSubModule: "fbdevhw"
[    20.945] (II) Unloading fbdevhw
[    20.945] (==) Depth 24 pixmap format is 32 bpp
[    20.946] (II) Loading sub module "int10"
[    20.946] (II) LoadModule: "int10"
[    20.946] (II) Loading /usr/lib/xorg/modules/libint10.so
[    20.946] (II) Module int10: vendor="X.Org Foundation"
[    20.946]     compiled for 1.13.0, module version = 1.0.0
[    20.946]     ABI class: X.Org Video Driver, version 13.0
[    20.946] (II) VESA(0): initializing int10
[    20.948] (II) VESA(0): Bad V_BIOS checksum
[    20.948] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    20.971] (II) VESA(0): VESA BIOS detected
[    20.971] (II) VESA(0): VESA VBE Version 3.0
[    20.971] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    20.971] (II) VESA(0): VESA VBE OEM: NVIDIA
[    20.971] (II) VESA(0): VESA VBE OEM Software Rev: 112.24
[    20.971] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    20.971] (II) VESA(0): VESA VBE OEM Product: GT218 Board - 08730000
[    20.971] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    20.971] (II) VESA(0): virtual address = 0x7f03670fc000,
    physical address = 0xdf000000, size = 14680064
[    20.975] (II) VESA(0): Setting up VESA Mode 0x115 (800x600)
[    21.148] (==) VESA(0): Default visual is TrueColor
[    21.148] (==) VESA(0): Backing store disabled
[    21.148] (**) VESA(0): DPMS enabled
[    21.148] (==) RandR enabled
[    21.152] (II) AIGLX: Screen 0 is not DRI2 capable
[    21.152] (II) AIGLX: Screen 0 is not DRI capable
[    21.159] (II) AIGLX: Loaded and initialized swrast
[    21.160] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    21.167] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.169] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    21.169] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.169] (II) LoadModule: "evdev"
[    21.170] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.170] (II) Module evdev: vendor="X.Org Foundation"
[    21.170]     compiled for 1.13.0, module version = 2.7.3
[    21.170]     Module class: X.Org XInput Driver
[    21.170]     ABI class: X.Org XInput driver, version 18.0
[    21.170] (II) Using input driver 'evdev' for 'Power Button'
[    21.170] (**) Power Button: always reports core events
[    21.170] (**) evdev: Power Button: Device: "/dev/input/event1"
[    21.170] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.170] (--) evdev: Power Button: Found keys
[    21.170] (II) evdev: Power Button: Configuring as keyboard
[    21.170] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    21.170] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    21.170] (**) Option "xkb_rules" "evdev"
[    21.170] (**) Option "xkb_model" "pc105"
[    21.170] (**) Option "xkb_layout" "fr"
[    21.170] (**) Option "xkb_variant" "latin9"
[    21.172] (II) XKB: reuse xkmfile /var/lib/xkb/server-816A055A5FF7D63897839A4BDEDC3908551E49DA.xkm
[    21.172] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    21.172] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.172] (II) Using input driver 'evdev' for 'Power Button'
[    21.172] (**) Power Button: always reports core events
[    21.172] (**) evdev: Power Button: Device: "/dev/input/event0"
[    21.172] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.172] (--) evdev: Power Button: Found keys
[    21.172] (II) evdev: Power Button: Configuring as keyboard
[    21.172] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    21.172] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    21.172] (**) Option "xkb_rules" "evdev"
[    21.172] (**) Option "xkb_model" "pc105"
[    21.172] (**) Option "xkb_layout" "fr"
[    21.172] (**) Option "xkb_variant" "latin9"
[    21.173] (II) config/udev: Adding input device NOVATEK USB Keyboard (/dev/input/event2)
[    21.173] (**) NOVATEK USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    21.173] (II) Using input driver 'evdev' for 'NOVATEK USB Keyboard'
[    21.173] (**) NOVATEK USB Keyboard: always reports core events
[    21.173] (**) evdev: NOVATEK USB Keyboard: Device: "/dev/input/event2"
[    21.173] (--) evdev: NOVATEK USB Keyboard: Vendor 0x603 Product 0xf1
[    21.173] (--) evdev: NOVATEK USB Keyboard: Found keys
[    21.173] (II) evdev: NOVATEK USB Keyboard: Configuring as keyboard
[    21.173] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input2/event2"
[    21.173] (II) XINPUT: Adding extended input device "NOVATEK USB Keyboard" (type: KEYBOARD, id 8)
[    21.173] (**) Option "xkb_rules" "evdev"
[    21.173] (**) Option "xkb_model" "pc105"
[    21.173] (**) Option "xkb_layout" "fr"
[    21.173] (**) Option "xkb_variant" "latin9"
[    21.173] (II) config/udev: Adding input device NOVATEK USB Keyboard (/dev/input/event3)
[    21.173] (**) NOVATEK USB Keyboard: Applying InputClass "evdev pointer catchall"
[    21.173] (**) NOVATEK USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    21.173] (II) Using input driver 'evdev' for 'NOVATEK USB Keyboard'
[    21.173] (**) NOVATEK USB Keyboard: always reports core events
[    21.173] (**) evdev: NOVATEK USB Keyboard: Device: "/dev/input/event3"
[    21.174] (--) evdev: NOVATEK USB Keyboard: Vendor 0x603 Product 0xf1
[    21.174] (--) evdev: NOVATEK USB Keyboard: Found 20 mouse buttons
[    21.174] (--) evdev: NOVATEK USB Keyboard: Found scroll wheel(s)
[    21.174] (--) evdev: NOVATEK USB Keyboard: Found relative axes
[    21.174] (--) evdev: NOVATEK USB Keyboard: Found x and y relative axes
[    21.174] (--) evdev: NOVATEK USB Keyboard: Found keys
[    21.174] (II) evdev: NOVATEK USB Keyboard: Configuring as mouse
[    21.174] (II) evdev: NOVATEK USB Keyboard: Configuring as keyboard
[    21.174] (II) evdev: NOVATEK USB Keyboard: Adding scrollwheel support
[    21.174] (**) evdev: NOVATEK USB Keyboard: YAxisMapping: buttons 4 and 5
[    21.174] (**) evdev: NOVATEK USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.174] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.1/input/input3/event3"
[    21.174] (II) XINPUT: Adding extended input device "NOVATEK USB Keyboard" (type: KEYBOARD, id 9)
[    21.174] (**) Option "xkb_rules" "evdev"
[    21.174] (**) Option "xkb_model" "pc105"
[    21.174] (**) Option "xkb_layout" "fr"
[    21.174] (**) Option "xkb_variant" "latin9"
[    21.174] (II) evdev: NOVATEK USB Keyboard: initialized for relative axes.
[    21.174] (**) NOVATEK USB Keyboard: (accel) keeping acceleration scheme 1
[    21.174] (**) NOVATEK USB Keyboard: (accel) acceleration profile 0
[    21.174] (**) NOVATEK USB Keyboard: (accel) acceleration factor: 2.000
[    21.174] (**) NOVATEK USB Keyboard: (accel) acceleration threshold: 4
[    21.174] (II) config/udev: Adding input device NOVATEK USB Keyboard (/dev/input/mouse0)
[    21.174] (II) No input driver specified, ignoring this device.
[    21.174] (II) This device may have been added with another device file.
[    21.174] (II) config/udev: Adding input device 2.4GHZ Mouse (/dev/input/event4)
[    21.174] (**) 2.4GHZ Mouse: Applying InputClass "evdev keyboard catchall"
[    21.174] (II) Using input driver 'evdev' for '2.4GHZ Mouse'
[    21.175] (**) 2.4GHZ Mouse: always reports core events
[    21.175] (**) evdev: 2.4GHZ Mouse: Device: "/dev/input/event4"
[    21.175] (--) evdev: 2.4GHZ Mouse: Vendor 0x1ea7 Product 0x2
[    21.175] (--) evdev: 2.4GHZ Mouse: Found keys
[    21.175] (II) evdev: 2.4GHZ Mouse: Configuring as keyboard
[    21.175] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.0/input/input4/event4"
[    21.175] (II) XINPUT: Adding extended input device "2.4GHZ Mouse" (type: KEYBOARD, id 10)
[    21.175] (**) Option "xkb_rules" "evdev"
[    21.175] (**) Option "xkb_model" "pc105"
[    21.175] (**) Option "xkb_layout" "fr"
[    21.175] (**) Option "xkb_variant" "latin9"
[    21.175] (II) config/udev: Adding input device 2.4GHZ Mouse (/dev/input/event5)
[    21.175] (**) 2.4GHZ Mouse: Applying InputClass "evdev pointer catchall"
[    21.175] (**) 2.4GHZ Mouse: Applying InputClass "evdev keyboard catchall"
[    21.175] (II) Using input driver 'evdev' for '2.4GHZ Mouse'
[    21.175] (**) 2.4GHZ Mouse: always reports core events
[    21.175] (**) evdev: 2.4GHZ Mouse: Device: "/dev/input/event5"
[    21.175] (--) evdev: 2.4GHZ Mouse: Vendor 0x1ea7 Product 0x2
[    21.175] (--) evdev: 2.4GHZ Mouse: Found 12 mouse buttons
[    21.175] (--) evdev: 2.4GHZ Mouse: Found scroll wheel(s)
[    21.175] (--) evdev: 2.4GHZ Mouse: Found relative axes
[    21.175] (--) evdev: 2.4GHZ Mouse: Found x and y relative axes
[    21.175] (--) evdev: 2.4GHZ Mouse: Found absolute axes
[    21.175] (II) evdev: 2.4GHZ Mouse: Forcing absolute x/y axes to exist.
[    21.175] (--) evdev: 2.4GHZ Mouse: Found keys
[    21.175] (II) evdev: 2.4GHZ Mouse: Configuring as mouse
[    21.175] (II) evdev: 2.4GHZ Mouse: Configuring as keyboard
[    21.175] (II) evdev: 2.4GHZ Mouse: Adding scrollwheel support
[    21.175] (**) evdev: 2.4GHZ Mouse: YAxisMapping: buttons 4 and 5
[    21.175] (**) evdev: 2.4GHZ Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.175] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.1/input/input5/event5"
[    21.175] (II) XINPUT: Adding extended input device "2.4GHZ Mouse" (type: KEYBOARD, id 11)
[    21.175] (**) Option "xkb_rules" "evdev"
[    21.175] (**) Option "xkb_model" "pc105"
[    21.175] (**) Option "xkb_layout" "fr"
[    21.175] (**) Option "xkb_variant" "latin9"
[    21.175] (II) evdev: 2.4GHZ Mouse: initialized for relative axes.
[    21.175] (WW) evdev: 2.4GHZ Mouse: ignoring absolute axes.
[    21.176] (**) 2.4GHZ Mouse: (accel) keeping acceleration scheme 1
[    21.176] (**) 2.4GHZ Mouse: (accel) acceleration profile 0
[    21.176] (**) 2.4GHZ Mouse: (accel) acceleration factor: 2.000
[    21.176] (**) 2.4GHZ Mouse: (accel) acceleration threshold: 4
[    21.176] (II) config/udev: Adding input device 2.4GHZ Mouse (/dev/input/mouse1)
[    21.176] (II) No input driver specified, ignoring this device.
[    21.176] (II) This device may have been added with another device file.
[    23.330] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[    44.501] (II) XKB: reuse xkmfile /var/lib/xkb/server-C814AC61323ADD9F3C69F18721C056518480B483.xkm

```

---

### Post by LucidOcelot on 2012-11-05
Nobody?

---

### Post by BicyclerBoy on 2012-11-05
Now you have the nv, nouveau & VESA fighting over the video card.

Out of that bunch only nouveau is worth using..

I would re-install nvidia-current & then logout/login & run:
sudo nvidia-xconfig
logout/login.

If the /var/log/Xorg.0.log still shows VGA EDID problems then tell us what your monitor model is..

Some people seem to have nvidia troubles lately with missing headers dependency..
You could try:
sudo apt-get install linux-headers-generic
- this package always points to the match headers for your kernel..

If you only want actual current headers package then:
sudo apt-get install linux-headers-`uname -r`

---

### Post by LucidOcelot on 2012-11-06
Thanks for yours answers !!!


I had to reinstall Ubuntu to fall back in a normal state (family PC). I am a bit scared about reinstalling nvidia-current as it seems that it was the cause of my problems.

Before installing, the workaround with xrand is working, but not after installing nvidia-current.

Other point is that I try to plug that screen a (Yuraku M2BABW 22" Widescreen Monitor) on my working windows PC.
This screen in not recognized. But in screen configuration menu, a panel of resolution is proposed and include the native one.

On ubuntu, the panel of proposed resolution with  nvidia-current is reduce to 320*240 and 800*600.

I also tried with ubuntu with get-edid and on windows with phoenix edid to retreive EDID from my screen with no success. This could means that there is a problem with my screen and EDID.


....

I may try your solution on an other partition in a few days. Again thanks... Ubuntu rules !

---

### Post by BicyclerBoy on 2012-11-06
When you back to it try this:
after running
sudo nvidia-xconfig

sudo gedit /etc/X11/xorg.conf & merge this into that file..
```

Section "Monitor"
        Identifier   "Monitor5"
        VendorName   "Yuraku"
        ModelName    "M2BABW"
        Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
EndSection
Section "Device"
        Identifier  "Card0"
        Driver      "nvidia"
        VendorName  "nVidia Corporation"
        BoardName   "Unknown Board"
#        BusID       "PCI:1:0:0"
EndSection
Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor5"
        DefaultDepth 24
        Option      "UseEDID" "false"
        SubSection "Display"
                Viewport 0 0
                Depth   24
                Modes "1680x1050_60.00"
        EndSubSection
EndSection

```
(modeline from cvt 1680 1050 60)
logout/login
Does it work ?

---

### Post by LucidOcelot on 2012-11-07
Thank you,

I will try !


> **BicyclerBoy said:**
> When you back to it try this:
after running
sudo nvidia-xconfig

sudo gedit /etc/X11/xorg.conf & merge this into that file..
```

Section "Monitor"
        Identifier   "Monitor5"
        VendorName   "Yuraku"
        ModelName    "M2BABW"
        Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
EndSection
Section "Device"
        Identifier  "Card0"
        Driver      "nvidia"
        VendorName  "nVidia Corporation"
        BoardName   "Unknown Board"
#        BusID       "PCI:1:0:0"
EndSection
Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor5"
        DefaultDepth 24
        Option      "UseEDID" "false"
        SubSection "Display"
                Viewport 0 0
                Depth   24
                Modes "1680x1050_60.00"
        EndSubSection
EndSection

```(modeline from cvt 1680 1050 60)
logout/login
Does it work ?

---

### Post by BicyclerBoy on 2012-11-08
You might have to add this the same file as well..
```

Option   "UseDisplayDevice"  "CRT-1"

```

---

### Post by LucidOcelot on 2012-11-09
Hello,

I tried that, thanks,

Now i get a resolution [FONT=Arial][SIZE=2]of [/SIZE][/FONT][FONT=Arial][SIZE=2]1360x768 on _**VGA-1 **_instead of 1680*1050[/SIZE][/FONT][SIZE=3].[/SIZE] This is better than 800*600, but still not what expected ;-)

My new xorg.conf is

```
  # nvidia-xconfig: X configuration file generated by nvidia-xconfig # nvidia-xconfig:  version 304.43
  (buildmeister@swio-display-x86-rhel47-13)  Sun Aug 19 21:19:28 PDT 2012
   
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
          Identifier   "Monitor5"
          VendorName   "Yuraku"
          ModelName    "M2BABW"
          Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050
  1053 1059 1089 -hsync +vsync
  EndSection
   
  Section "Device"
          Identifier  "Card0"
          Driver      "nvidia"
          Option   "UseDisplayDevice"  "CRT-1"
          VendorName  "nVidia Corporation"
          BoardName   "Unknown Board"
  #        BusID       "PCI:1:0:0"
  EndSection
   
  Section "Screen"
          Identifier "Screen0"
          Device     "Card0"
          Monitor    "Monitor5"
          DefaultDepth 24
          Option      "UseEDID" "false"
          SubSection "Display"
                  Viewport 0 0
                  Depth   24
                  Modes "1680x1050"
          EndSubSection
  EndSection
   
  
```
And of the log file

 ```

  [    18.387]
  X.Org X Server 1.13.0
  Release Date: 2012-09-05
  [    18.387] X Protocol Version 11, Revision 0
  [    18.387] Build Operating System: Linux 3.2.0-30-generic x86_64 Ubuntu
  [    18.387] Current Operating System: Linux Kafiland 3.5.0-18-generic
  #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 x86_64
  [    18.387] Kernel command line:
  BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-generic
  root=UUID=88dc9bd7-077d-48e3-897c-efd5ef08556a ro quiet splash
  [    18.387] Build Date: 08 October 2012  03:34:01PM
  [    18.387] xorg-server 2:1.13.0-0ubuntu6 (For technical support please
  see http://www.ubuntu.com/support)
  [    18.387] Current version of pixman: 0.26.0
  [    18.387]     Before reporting problems, check http://wiki.x.org
      to make sure that you have the latest version.
  [    18.387] Markers: (--) probed, (**) from config file, (==) default
  setting,
      (++) from command line, (!!) notice, (II) informational,
      (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
  [    18.387] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov  8
  22:13:04 2012
  [    18.387] (==) Using config file: "/etc/X11/xorg.conf"
  [    18.387] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
  [    18.387] (==) ServerLayout "Layout0"
  [    18.387] (**) |-->Screen "Screen0" (0)
  [    18.387] (**) |   |-->Monitor "Monitor5"
  [    18.388] (**) |   |-->Device "Card0"
  [    18.388] (**) |-->Input Device "Keyboard0"
  [    18.388] (**) |-->Input Device "Mouse0"
  [    18.388] (==) Automatically adding devices
  [    18.388] (==) Automatically enabling devices
  [    18.388] (==) Automatically adding GPU devices
  [    18.388] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not
  exist.
  [    18.388]     Entry deleted from font path.
  [    18.388] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not
  exist.
  [    18.388]     Entry deleted from font path.
  [    18.388] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not
  exist.
  [    18.388]     Entry deleted from font path.
  [    18.388] (WW) The directory "/usr/share/fonts/X11/100dpi" does not
  exist.
  [    18.388]     Entry deleted from font path.
  [    18.388] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
  [    18.388]     Entry deleted from font path.
  [    18.388] (WW) The directory
  "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
  [    18.388]     Entry deleted from font path.
  [    18.388] (==) FontPath set to:
      /usr/share/fonts/X11/misc,
      /usr/share/fonts/X11/Type1,
      built-ins
  [    18.388] (==) ModulePath set to
  "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
  [    18.388] (WW) Hotplugging is on, devices using drivers 'kbd',
  'mouse' or 'vmmouse' will be disabled.
  [    18.388] (WW) Disabling Keyboard0
  [    18.388] (WW) Disabling Mouse0
  [    18.388] (II) Loader magic: 0x7ffcb6e8dc40
  [    18.388] (II) Module ABI versions:
  [    18.388]     X.Org ANSI C Emulation: 0.4
  [    18.388]     X.Org Video Driver: 13.0
  [    18.388]     X.Org XInput driver : 18.0
  [    18.388]     X.Org Server Extension : 7.0
  [    18.389] (--) PCI:*(0:1:0:0) 10de:0a65:1462:8094 rev 162, Mem @
  0xfb000000/16777216, 0xc0000000/268435456, 0xde000000/33554432, I/O @
  0x0000ef00/128, BIOS @ 0x????????/524288
  [    18.389] (II) Open ACPI successful (/var/run/acpid.socket)
  [    18.389] Initializing built-in extension Generic Event Extension
  [    18.389] Initializing built-in extension SHAPE
  [    18.389] Initializing built-in extension MIT-SHM
  [    18.389] Initializing built-in extension XInputExtension
  [    18.389] Initializing built-in extension XTEST
  [    18.389] Initializing built-in extension BIG-REQUESTS
  [    18.389] Initializing built-in extension SYNC
  [    18.389] Initializing built-in extension XKEYBOARD
  [    18.389] Initializing built-in extension XC-MISC
  [    18.389] Initializing built-in extension SECURITY
  [    18.389] Initializing built-in extension XINERAMA
  [    18.389] Initializing built-in extension XFIXES
  [    18.389] Initializing built-in extension RENDER
  [    18.389] Initializing built-in extension RANDR
  [    18.389] Initializing built-in extension COMPOSITE
  [    18.389] Initializing built-in extension DAMAGE
  [    18.389] Initializing built-in extension MIT-SCREEN-SAVER
  [    18.389] Initializing built-in extension DOUBLE-BUFFER
  [    18.389] Initializing built-in extension RECORD
  [    18.389] Initializing built-in extension DPMS
  [    18.389] Initializing built-in extension X-Resource
  [    18.389] Initializing built-in extension XVideo
  [    18.389] Initializing built-in extension XVideo-MotionCompensation
  [    18.389] Initializing built-in extension XFree86-VidModeExtension
  [    18.389] Initializing built-in extension XFree86-DGA
  [    18.389] Initializing built-in extension XFree86-DRI
  [    18.389] Initializing built-in extension DRI2
  [    18.389] (II) LoadModule: "glx"
  [    18.389] (II) Loading
  /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
  [    18.402] (II) Module glx: vendor="NVIDIA Corporation"
  [    18.402]     compiled for 4.0.2, module version = 1.0.0
  [    18.402]     Module class: X.Org Server Extension
  [    18.402] (II) NVIDIA GLX Module  304.43  Sun Aug 19 20:34:01 PDT 2012
  [    18.402] Loading extension GLX
  [    18.402] (II) LoadModule: "nvidia"
  [    18.402] (II) Loading
  /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
  [    18.402] (II) Module nvidia: vendor="NVIDIA Corporation"
  [    18.402]     compiled for 4.0.2, module version = 1.0.0
  [    18.402]     Module class: X.Org Video Driver
  [    18.402] (II) NVIDIA dlloader X Driver  304.43  Sun Aug 19 20:15:32
  PDT 2012
  [    18.402] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
  [    18.402] (++) using VT number 7
   
  [    18.404] (II) Loading sub module "fb"
  [    18.404] (II) LoadModule: "fb"
  [    18.451] (II) Loading /usr/lib/xorg/modules/libfb.so
  [    18.451] (II) Module fb: vendor="X.Org Foundation"
  [    18.451]     compiled for 1.13.0, module version = 1.0.0
  [    18.451]     ABI class: X.Org ANSI C Emulation, version 0.4
  [    18.451] (II) Loading sub module "wfb"
  [    18.451] (II) LoadModule: "wfb"
  [    18.451] (II) Loading /usr/lib/xorg/modules/libwfb.so
  [    18.451] (II) Module wfb: vendor="X.Org Foundation"
  [    18.451]     compiled for 1.13.0, module version = 1.0.0
  [    18.451]     ABI class: X.Org ANSI C Emulation, version 0.4
  [    18.451] (II) Loading sub module "ramdac"
  [    18.451] (II) LoadModule: "ramdac"
  [    18.451] (II) Module "ramdac" already built-in
  [    18.451] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
  [    18.451] (==) NVIDIA(0): RGB weight 888
  [    18.451] (==) NVIDIA(0): Default visual is TrueColor
  [    18.451] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
  [    18.451] (**) NVIDIA(0): Option "UseEDID" "false"
  [    18.451] (**) NVIDIA(0): Option "UseDisplayDevice" "CRT-1"
  [    18.451] (**) NVIDIA(0): Enabling 2D acceleration
  [    18.451] (**) NVIDIA(0): Ignoring EDIDs
  [    19.342] (II) NVIDIA(GPU-0): Not probing EDID on CRT-1.
  [    19.343] (II) NVIDIA(0): NVIDIA GPU GeForce 210 (GT218) at PCI:1:0:0
  (GPU-0)
  [    19.343] (--) NVIDIA(0): Memory: 1048576 kBytes
  [    19.343] (--) NVIDIA(0): VideoBIOS: 70.18.49.00.03
  [    19.343] (II) NVIDIA(0): Detected PCI Express Link width: 16X
  [    19.343] (--) NVIDIA(0): Interlaced video modes are supported on
  this GPU
  [    19.344] (--) NVIDIA(0): Valid display device(s) on GeForce 210 at
  PCI:1:0:0
  [    19.344] (--) NVIDIA(0):     CRT-0
  [    19.344] (--) NVIDIA(0):     CRT-1 (connected)
  [    19.344] (--) NVIDIA(0):     DFP-0
  [    19.344] (--) NVIDIA(0):     DFP-1
  [    19.344] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
  [    19.344] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
  [    19.344] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
  [    19.344] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
  [    19.344] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
  [    19.344] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
  [    19.344] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the
  EDID for display
  [    19.344] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies
  has been enabled on
  [    19.344] (**) NVIDIA(0):     all display devices.)
  [    19.347] (WW) NVIDIA(0): No valid modes for "CRT-1:1680x1050"; removing.
  [    19.347] (WW) NVIDIA(0):
  [    19.347] (WW) NVIDIA(0): Unable to validate any modes; falling back
  to the default mode
  [    19.347] (WW) NVIDIA(0):     "nvidia-auto-select".
  [    19.347] (WW) NVIDIA(0):
  [    19.347] (II) NVIDIA(0): Validated MetaModes:
  [    19.347] (II) NVIDIA(0):     "CRT-1:nvidia-auto-select"
  [    19.347] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
  [    19.371] (WW) NVIDIA(0): Unable to get display device CRT-1's EDID;
  cannot compute DPI
  [    19.371] (WW) NVIDIA(0):     from CRT-1's EDID.
  [    19.371] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in
  default
  [    19.371] (--) Depth 24 pixmap format is 32 bpp
  [    19.371] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect
  memory access.
  [    19.374] (II) NVIDIA(0): Setting mode "CRT-1:nvidia-auto-select"
  [    19.408] Loading extension NV-GLX
  [    19.435] (==) NVIDIA(0): Disabling shared memory pixmaps
  [    19.435] (==) NVIDIA(0): Backing store disabled
  [    19.435] (==) NVIDIA(0): Silken mouse enabled
  [    19.436] (==) NVIDIA(0): DPMS enabled
  [    19.436] Loading extension NV-CONTROL
  [    19.436] Loading extension XINERAMA
  [    19.436] (II) Loading sub module "dri2"
  [    19.436] (II) LoadModule: "dri2"
  [    19.436] (II) Module "dri2" already built-in
  [    19.436] (II) NVIDIA(0): [DRI2] Setup complete
  [    19.436] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
  [    19.436] (--) RandR disabled
  [    19.441] (II) Initializing extension GLX
  [    19.451] (II) XKB: reuse xkmfile
  /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
  [    19.453] (II) config/udev: Adding input device Power Button
  (/dev/input/event1)
  [    19.453] (**) Power Button: Applying InputClass "evdev keyboard
  catchall"
  [    19.453] (II) LoadModule: "evdev"
  [    19.453] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
  [    19.453] (II) Module evdev: vendor="X.Org Foundation"
  [    19.453]     compiled for 1.13.0, module version = 2.7.3
  [    19.453]     Module class: X.Org XInput Driver
  [    19.453]     ABI class: X.Org XInput driver, version 18.0
  [    19.453] (II) Using input driver 'evdev' for 'Power Button'
  [    19.454] (**) Power Button: always reports core events
  [    19.454] (**) evdev: Power Button: Device: "/dev/input/event1"
  [    19.454] (--) evdev: Power Button: Vendor 0 Product 0x1
  [    19.454] (--) evdev: Power Button: Found keys
  [    19.454] (II) evdev: Power Button: Configuring as keyboard
  [    19.454] (**) Option "config_info"
  "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
  [    19.454] (II) XINPUT: Adding extended input device "Power Button"
  (type: KEYBOARD, id 6)
  [    19.454] (**) Option "xkb_rules" "evdev"
  [    19.454] (**) Option "xkb_model" "pc105"
  [    19.454] (**) Option "xkb_layout" "fr"
  [    19.454] (**) Option "xkb_variant" "latin9"
  [    19.455] (II) XKB: reuse xkmfile
  /var/lib/xkb/server-816A055A5FF7D63897839A4BDEDC3908551E49DA.xkm
  [    19.456] (II) config/udev: Adding input device Power Button
  (/dev/input/event0)
  [    19.456] (**) Power Button: Applying InputClass "evdev keyboard
  catchall"
  [    19.456] (II) Using input driver 'evdev' for 'Power Button'
  [    19.456] (**) Power Button: always reports core events
  [    19.456] (**) evdev: Power Button: Device: "/dev/input/event0"
  [    19.456] (--) evdev: Power Button: Vendor 0 Product 0x1
  [    19.456] (--) evdev: Power Button: Found keys
  [    19.456] (II) evdev: Power Button: Configuring as keyboard
  [    19.456] (**) Option "config_info"
  "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
  [    19.456] (II) XINPUT: Adding extended input device "Power Button"
  (type: KEYBOARD, id 7)
  [    19.456] (**) Option "xkb_rules" "evdev"
  [    19.456] (**) Option "xkb_model" "pc105"
  [    19.456] (**) Option "xkb_layout" "fr"
  [    19.456] (**) Option "xkb_variant" "latin9"
  [    19.456] (II) config/udev: Adding input device HDA NVidia
  HDMI/DP,pcm=9 (/dev/input/event14)
  [    19.456] (II) No input driver specified, ignoring this device.
  [    19.456] (II) This device may have been added with another device file.
  [    19.456] (II) config/udev: Adding input device HDA NVidia
  HDMI/DP,pcm=8 (/dev/input/event15)
  [    19.456] (II) No input driver specified, ignoring this device.
  [    19.456] (II) This device may have been added with another device file.
  [    19.456] (II) config/udev: Adding input device HDA NVidia
  HDMI/DP,pcm=7 (/dev/input/event16)
  [    19.457] (II) No input driver specified, ignoring this device.
  [    19.457] (II) This device may have been added with another device file.
  [    19.457] (II) config/udev: Adding input device HDA NVidia
  HDMI/DP,pcm=3 (/dev/input/event17)
  [    19.457] (II) No input driver specified, ignoring this device.
  [    19.457] (II) This device may have been added with another device file.
  [    19.457] (II) config/udev: Adding input device NOVATEK USB Keyboard
  (/dev/input/event2)
  [    19.457] (**) NOVATEK USB Keyboard: Applying InputClass "evdev
  keyboard catchall"
  [    19.457] (II) Using input driver 'evdev' for 'NOVATEK USB Keyboard'
  [    19.457] (**) NOVATEK USB Keyboard: always reports core events
  [    19.457] (**) evdev: NOVATEK USB Keyboard: Device: "/dev/input/event2"
  [    19.457] (--) evdev: NOVATEK USB Keyboard: Vendor 0x603 Product 0xf1
  [    19.457] (--) evdev: NOVATEK USB Keyboard: Found keys
  [    19.457] (II) evdev: NOVATEK USB Keyboard: Configuring as keyboard
  [    19.457] (**) Option "config_info"
  "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input2/event2"
  [    19.457] (II) XINPUT: Adding extended input device "NOVATEK USB
  Keyboard" (type: KEYBOARD, id 8)
  [    19.457] (**) Option "xkb_rules" "evdev"
  [    19.457] (**) Option "xkb_model" "pc105"
  [    19.457] (**) Option "xkb_layout" "fr"
  [    19.457] (**) Option "xkb_variant" "latin9"
  [    19.457] (II) config/udev: Adding input device NOVATEK USB Keyboard
  (/dev/input/event3)
  [    19.457] (**) NOVATEK USB Keyboard: Applying InputClass "evdev
  pointer catchall"
  [    19.457] (**) NOVATEK USB Keyboard: Applying InputClass "evdev
  keyboard catchall"
  [    19.457] (II) Using input driver 'evdev' for 'NOVATEK USB Keyboard'
  [    19.457] (**) NOVATEK USB Keyboard: always reports core events
  [    19.457] (**) evdev: NOVATEK USB Keyboard: Device: "/dev/input/event3"
  [    19.457] (--) evdev: NOVATEK USB Keyboard: Vendor 0x603 Product 0xf1
  [    19.457] (--) evdev: NOVATEK USB Keyboard: Found 20 mouse buttons
  [    19.457] (--) evdev: NOVATEK USB Keyboard: Found scroll wheel(s)
  [    19.457] (--) evdev: NOVATEK USB Keyboard: Found relative axes
  [    19.457] (--) evdev: NOVATEK USB Keyboard: Found x and y relative axes
  [    19.457] (--) evdev: NOVATEK USB Keyboard: Found keys
  [    19.458] (II) evdev: NOVATEK USB Keyboard: Configuring as mouse
  [    19.458] (II) evdev: NOVATEK USB Keyboard: Configuring as keyboard
  [    19.458] (II) evdev: NOVATEK USB Keyboard: Adding scrollwheel support
  [    19.458] (**) evdev: NOVATEK USB Keyboard: YAxisMapping: buttons 4 and 5
  [    19.458] (**) evdev: NOVATEK USB Keyboard: EmulateWheelButton: 4,
  EmulateWheelInertia: 10, EmulateWheelTimeout: 200
  [    19.458] (**) Option "config_info"
  "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.1/input/input3/event3"
  [    19.458] (II) XINPUT: Adding extended input device "NOVATEK USB
  Keyboard" (type: KEYBOARD, id 9)
  [    19.458] (**) Option "xkb_rules" "evdev"
  [    19.458] (**) Option "xkb_model" "pc105"
  [    19.458] (**) Option "xkb_layout" "fr"
  [    19.458] (**) Option "xkb_variant" "latin9"
  [    19.458] (II) evdev: NOVATEK USB Keyboard: initialized for relative
  axes.
  [    19.458] (**) NOVATEK USB Keyboard: (accel) keeping acceleration
  scheme 1
  [    19.458] (**) NOVATEK USB Keyboard: (accel) acceleration profile 0
  [    19.458] (**) NOVATEK USB Keyboard: (accel) acceleration factor: 2.000
  [    19.458] (**) NOVATEK USB Keyboard: (accel) acceleration threshold: 4
  [    19.458] (II) config/udev: Adding input device NOVATEK USB Keyboard
  (/dev/input/mouse0)
  [    19.458] (II) No input driver specified, ignoring this device.
  [    19.458] (II) This device may have been added with another device file.
  [    19.458] (II) config/udev: Adding input device 2.4GHZ Mouse
  (/dev/input/event4)
  [    19.458] (**) 2.4GHZ Mouse: Applying InputClass "evdev keyboard
  catchall"
  [    19.458] (II) Using input driver 'evdev' for '2.4GHZ Mouse'
  [    19.458] (**) 2.4GHZ Mouse: always reports core events
  [    19.458] (**) evdev: 2.4GHZ Mouse: Device: "/dev/input/event4"
  [    19.458] (--) evdev: 2.4GHZ Mouse: Vendor 0x1ea7 Product 0x2
  [    19.458] (--) evdev: 2.4GHZ Mouse: Found keys
  [    19.458] (II) evdev: 2.4GHZ Mouse: Configuring as keyboard
  [    19.459] (**) Option "config_info"
  "udev:/sys/devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.0/input/input4/event4"
  [    19.459] (II) XINPUT: Adding extended input device "2.4GHZ Mouse"
  (type: KEYBOARD, id 10)
  [    19.459] (**) Option "xkb_rules" "evdev"
  [    19.459] (**) Option "xkb_model" "pc105"
  [    19.459] (**) Option "xkb_layout" "fr"
  [    19.459] (**) Option "xkb_variant" "latin9"
  [    19.459] (II) config/udev: Adding input device 2.4GHZ Mouse
  (/dev/input/event5)
  [    19.459] (**) 2.4GHZ Mouse: Applying InputClass "evdev pointer catchall"
  [    19.459] (**) 2.4GHZ Mouse: Applying InputClass "evdev keyboard
  catchall"
  [    19.459] (II) Using input driver 'evdev' for '2.4GHZ Mouse'
  [    19.459] (**) 2.4GHZ Mouse: always reports core events
  [    19.459] (**) evdev: 2.4GHZ Mouse: Device: "/dev/input/event5"
  [    19.459] (--) evdev: 2.4GHZ Mouse: Vendor 0x1ea7 Product 0x2
  [    19.459] (--) evdev: 2.4GHZ Mouse: Found 12 mouse buttons
  [    19.459] (--) evdev: 2.4GHZ Mouse: Found scroll wheel(s)
  [    19.459] (--) evdev: 2.4GHZ Mouse: Found relative axes
  [    19.459] (--) evdev: 2.4GHZ Mouse: Found x and y relative axes
  [    19.459] (--) evdev: 2.4GHZ Mouse: Found absolute axes
  [    19.459] (II) evdev: 2.4GHZ Mouse: Forcing absolute x/y axes to exist.
  [    19.459] (--) evdev: 2.4GHZ Mouse: Found keys
  [    19.459] (II) evdev: 2.4GHZ Mouse: Configuring as mouse
  [    19.459] (II) evdev: 2.4GHZ Mouse: Configuring as keyboard
  [    19.459] (II) evdev: 2.4GHZ Mouse: Adding scrollwheel support
  [    19.459] (**) evdev: 2.4GHZ Mouse: YAxisMapping: buttons 4 and 5
  [    19.459] (**) evdev: 2.4GHZ Mouse: EmulateWheelButton: 4,
  EmulateWheelInertia: 10, EmulateWheelTimeout: 200
  [    19.459] (**) Option "config_info"
  "udev:/sys/devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.1/input/input5/event5"
  [    19.459] (II) XINPUT: Adding extended input device "2.4GHZ Mouse"
  (type: KEYBOARD, id 11)
  [    19.459] (**) Option "xkb_rules" "evdev"
  [    19.459] (**) Option "xkb_model" "pc105"
  [    19.459] (**) Option "xkb_layout" "fr"
  [    19.459] (**) Option "xkb_variant" "latin9"
  [    19.459] (II) evdev: 2.4GHZ Mouse: initialized for relative axes.
  [    19.459] (WW) evdev: 2.4GHZ Mouse: ignoring absolute axes.
  [    19.460] (**) 2.4GHZ Mouse: (accel) keeping acceleration scheme 1
  [    19.460] (**) 2.4GHZ Mouse: (accel) acceleration profile 0
  [    19.460] (**) 2.4GHZ Mouse: (accel) acceleration factor: 2.000
  [    19.460] (**) 2.4GHZ Mouse: (accel) acceleration threshold: 4
  [    19.460] (II) config/udev: Adding input device 2.4GHZ Mouse
  (/dev/input/mouse1)
  [    19.460] (II) No input driver specified, ignoring this device.
  [    19.460] (II) This device may have been added with another device file.
  [    19.460] (II) config/udev: Adding input device HDA ATI SB Line Out
  Side (/dev/input/event10)
  [    19.460] (II) No input driver specified, ignoring this device.
  [    19.460] (II) This device may have been added with another device file.
  [    19.460] (II) config/udev: Adding input device HDA ATI SB Line Out
  CLFE (/dev/input/event11)
  [    19.460] (II) No input driver specified, ignoring this device.
  [    19.460] (II) This device may have been added with another device file.
  [    19.460] (II) config/udev: Adding input device HDA ATI SB Line Out
  Surround (/dev/input/event12)
  [    19.460] (II) No input driver specified, ignoring this device.
  [    19.460] (II) This device may have been added with another device file.
  [    19.460] (II) config/udev: Adding input device HDA ATI SB Line Out
  Front (/dev/input/event13)
  [    19.460] (II) No input driver specified, ignoring this device.
  [    19.460] (II) This device may have been added with another device file.
  [    19.461] (II) config/udev: Adding input device HDA ATI SB Line
  (/dev/input/event6)
  [    19.461] (II) No input driver specified, ignoring this device.
  [    19.461] (II) This device may have been added with another device file.
  [    19.461] (II) config/udev: Adding input device HDA ATI SB Front Mic
  (/dev/input/event7)
  [    19.461] (II) No input driver specified, ignoring this device.
  [    19.461] (II) This device may have been added with another device file.
  [    19.461] (II) config/udev: Adding input device HDA ATI SB Rear Mic
  (/dev/input/event8)
  [    19.461] (II) No input driver specified, ignoring this device.
  [    19.461] (II) This device may have been added with another device file.
  [    19.461] (II) config/udev: Adding input device HDA ATI SB Front
  Headphone (/dev/input/event9)
  [    19.461] (II) No input driver specified, ignoring this device.
  [    19.461] (II) This device may have been added with another device file.
  [    20.859] (II) NVIDIA(GPU-0): Not probing EDID on CRT-1.
  [    20.859] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the
  EDID for display
  [    20.859] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies
  has been enabled on
  [    20.859] (**) NVIDIA(0):     all display devices.)
  [    21.227] (II) NVIDIA(0): Setting mode "VGA-0: 1360x768 @1360x768 +0+0"
  [    21.363] (II) NVIDIA(GPU-0): Not probing EDID on CRT-1.
  [    21.363] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the
  EDID for display
  [    21.363] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies
  has been enabled on
  [    21.363] (**) NVIDIA(0):     all display devices.)
  [    21.495] (II) NVIDIA(GPU-0): Not probing EDID on CRT-1.
  [    21.495] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the
  EDID for display
  [    21.495] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies
  has been enabled on
  [    21.495] (**) NVIDIA(0):     all display devices.)
  [    22.872] (II) XKB: reuse xkmfile
  /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
  [    24.932] (II) NVIDIA(GPU-0): Not probing EDID on CRT-1.
  [    24.932] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the
  EDID for display
  [    24.932] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies
  has been enabled on
  [    24.932] (**) NVIDIA(0):     all display devices.)
  [    36.808] (II) NVIDIA(GPU-0): Not probing EDID on CRT-1.
  [    36.808] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the
  EDID for display
  [    36.808] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies
  has been enabled on
  [    36.808] (**) NVIDIA(0):     all display devices.)
  
```

The strange fact is that a

**[    18.451] (**) NVIDIA(0): Option "UseEDID" "false"**
[    18.451] (**) NVIDIA(0): Option "UseDisplayDevice" "CRT-1"
[    18.451] (**) NVIDIA(0): Enabling 2D acceleration
[    18.451] (**) NVIDIA(0): Ignoring EDIDs
[    19.342] (II) NVIDIA(GPU-0): Not probing EDID on CRT-1.


is followed by a 

[    22.872] (II) XKB: reuse xkmfile
   /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
 
and a 

[    21.363] (**) NVIDIA(0):     device CRT-1 (**Using EDID frequencies**
**has been enabled on**



Thanks for your high quality help,

Théophile

---

### Post by LucidOcelot on 2012-11-09
I may add that 

xrandr gives 


```
Screen 0: minimum 8 x 8, current 1360 x 768, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +
   1360x768       60.0*    59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384       119.9    119.6  
   640x480        59.9  
   512x384       120.0  
   400x300       144.4  
   320x240       120.1  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
  1680x1050 (0x2a7)  147.1MHz
        h: width  1680 start 1784 end 1968 total 2256 skew    0 clock   65.2KHz
        v: height 1050 start 1051 end 1054 total 1087           clock   60.0Hz

```

And is about VGA-0 not CRT-1 as in previous post log

---

### Post by BicyclerBoy on 2012-11-09
xrandr uses VGA labels & has enumerated the avail screens.

The nvidia driver CRT-0,1 refer to actual physical ports.

To use modelines:
I should have added horz & vert freq ranges to monitor section because your EDID is ignored.
You need a unique name for the modes..why did you remove part of the name?
The modeline must be **one line** in xorg.conf
We should make the modeline very unique or just use the built-in modes.
```

  Section "Monitor"
          Identifier   "Monitor5"
          VendorName   "Yuraku"
          ModelName    "M2BABW"
          Modeline "my_1680x1050p60"  146.25  1680 1784 1960 2240  1050  1053 1059 1089 -hsync +vsync
          VertRefresh    48.0  -  65.0
          HorizSync      54.0  - 70.0
  EndSection

Section "Screen"
          Identifier "Screen0"
          Device     "Card0"
          Monitor    "Monitor5"
          DefaultDepth 24
          Option      "UseEDID" "false"
          SubSection "Display"
                  Viewport 0 0
                  Depth   24
                  Modes "my_1680x1050p60"
          EndSubSection
EndSection

```

Alternative:
The mode 1680x1050 @ 60Hz is a built-in mode so can you try:
- fix monitor section to add horz & vert freqs
- edit monitor modeline as above
- leave the Screen section Modes "1680x1050"  (built-in mode)
- add Option "ModeDebug"  "True"
save logout/login look in /var/log/Xorg.0.log

Use nvidia-settings to query the screen setup..don't expect "Displays" tool to work.

---

### Post by LucidOcelot on 2012-11-10
Hello,

The first option **IS WORKING !!**

Thanks, thanks, thanks... 

I only have an error message at login :

```

No choosen mode is compatible with existing ones : Tests des modes pour le CRTC 585

 CRTC 585 : test du mode 960x540@120Hz avec une sortie à 1360x768@60Hz (passe 0) 
CRTC 585 : test du mode 1920x1080@60Hz avec une sortie à 1360x768@60Hz (passe 0)
 CRTC 585 : test du mode 1680x1050@60Hz avec une sortie à 1360x768@60Hz (passe 0)
 CRTC 585 : test du mode 1680x1050@60Hz avec une sortie à 1360x768@60Hz (passe 0) 
CRTC 585 : test du mode 1440x900@60Hz avec une sortie à 1360x768@60Hz (passe 0) 
CRTC 585 : test du mode 1400x1050@60Hz avec une sortie à 1360x768@60Hz (passe 0) 
CRTC 585 : test du mode 1280x1024@60Hz avec une sortie à 1360x768@60Hz (passe 0) 
CRTC 585 : test du mode 1280x960@60Hz avec une sortie à 1360x768@60Hz (passe 0) 
CRTC 585 : test du mode 1152x864@60Hz avec une sortie à 1360x768@60Hz (passe 0) 
CRTC 585 : test du mode 840x525@120Hz avec une sortie à 1360x768@60Hz (passe 0) 
CRTC 585 : test du mode 840x525@120Hz avec une sortie à 1360x768@60Hz (passe 0) 
CRTC 585 : test du mode 720x450@120Hz avec une sortie à 1360x768@60Hz (passe 0) 
CRTC 585 : test du mode 700x525@120Hz avec une sortie à 1360x768@60Hz (passe 0) 
CRTC 585 : test du mode 960x540@120Hz avec une sortie à 1360x768@60Hz (passe 1) 
CRTC 585 : test du mode 1920x1080@60Hz avec une sortie à 1360x768@60Hz (passe 1) 
CRTC 585 : test du mode 1680x1050@60Hz avec une sortie à 1360x768@60Hz (passe 1) 
CRTC 585 : test du mode 1680x1050@60Hz avec une sortie à 1360x768@60Hz (passe 1) 
CRTC 585 : test du mode 1440x900@60Hz avec une sortie à 1360x768@60Hz (passe 1) 
CRTC 585 : test du mode 1400x1050@60Hz avec une sortie à 1360x768@60Hz (passe 1) 
CRTC 585 : test du mode 1280x1024@60Hz avec une sortie à 1360x768@60Hz (passe 1) 
CRTC 585 : test du mode 1280x960@60Hz avec une sortie à 1360x768@60Hz (passe 1) 
CRTC 585 : test du mode 1152x864@60Hz avec une sortie à 1360x768@60Hz (passe 1) 
CRTC 585 : test du mode 840x525@120Hz avec une sortie à 1360x768@60Hz (passe 1) 
CRTC 585 : test du mode 840x525@120Hz avec une sortie à 1360x768@60Hz (passe 1) 
CRTC 585 : test du mode 720x450@120Hz avec une sortie à 1360x768@60Hz (passe 1) 
CRTC 585 : test du mode 700x525@120Hz avec une sortie à 1360x768@60Hz (passe 1) 
Tests des modes pour le CRTC 586 CRTC 586 : 
test du mode 960x540@120Hz avec une sortie à 1360x768@60Hz (passe 0) CRTC 586 : 
test du mode 1920x1080@60Hz avec une sortie à 1360x768@60Hz (passe 0) CRTC 586 : 
test du mode 1680x1050@60Hz avec une sortie à 1360x768@60Hz (passe 0) CRTC 586 : 
test du mode 1680x1050@60Hz avec une sortie à 1360x768@60Hz (passe 0) CRTC 586 : 
test du mode 1440x900@60Hz avec une sortie à 1360x768@60Hz (passe 0) CRTC 586 : test du mode 1400x1050@60Hz avec une sortie à 1360x768@60Hz (passe 0) CRTC 586 : 
test du mode 1280x1024@60Hz avec une sortie à 1360x768@60Hz (passe 0) CRTC 586 : 
test du mode 1280x960@60Hz avec une sortie à 1360x768@60Hz (passe 0) CRTC 586 : 
test du mode 1152x864@60Hz avec une sortie à 1360x768@60Hz (passe 0) CRTC 586 : 
test du mode 840x525@120Hz avec une sortie à 1360x768@60Hz (passe 0) CRTC 586 : 
test du mode 840x525@120Hz avec une sortie à 1360x768@60Hz (passe 0) CRTC 586 : 
test du mode 720x450@120Hz avec une sortie à 1360x768@60Hz (passe 0) CRTC 586 : 
test du mode 700x525@120Hz avec une sortie à 1360x768@60Hz (passe 0) CRTC 586 : 
test du mode 960x540@120Hz avec une sortie à 1360x768@60Hz (passe 1) CRTC 586 : 
test du mode 1920x1080@60Hz avec une sortie à 1360x768@60Hz (passe 1) CRTC 586 : 
test du mode 1680x1050@60Hz avec une sortie à 1360x768@60Hz (passe 1) CRTC 586 : 
test du mode 1680x1050@60Hz avec une sortie à 1360x768@60Hz (passe 1) CRTC 586 : 
test du mode 1440x900@60Hz avec une sortie à 1360x768@60Hz (passe 1) CRTC 586 : 
test du mode 1400x1050@60Hz avec une sortie à 1360x768@60Hz (passe 1) CRTC 586 : 
test du mode 1280x1024@60Hz avec une sortie à 1360x768@60Hz (passe 1) CRTC 586 : 
test du mode 1280x960@60Hz avec une sortie à 1360x768@60Hz (passe 1) CRTC 586 : 
test du mode 1152x864@60Hz avec une sortie à 1360x768@60Hz (passe 1) CRTC 586 : 
test du mode 840x525@120Hz avec une sortie à 1360x768@60Hz (passe 1) CRTC 586 : 
test du mode 840x525@120Hz avec une sortie à 1360x768@60Hz (passe 1) CRTC 586 : 
test du mode 720x450@120Hz avec une sortie à 1360x768@60Hz (passe 1) CRTC 586 : 
test du mode 700x525@120Hz avec une sortie à 1360x768@60Hz (passe 1) 
```My log is 

```
[    18.227] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    18.227] X Protocol Version 11, Revision 0
[    18.227] Build Operating System: Linux 3.2.0-30-generic x86_64 Ubuntu
[    18.227] Current Operating System: Linux Kafiland 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 x86_64
[    18.227] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-generic root=UUID=88dc9bd7-077d-48e3-897c-efd5ef08556a ro quiet splash
[    18.227] Build Date: 08 October 2012  03:34:01PM
[    18.227] xorg-server 2:1.13.0-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    18.227] Current version of pixman: 0.26.0
[    18.227]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    18.227] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.227] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 10 14:54:32 2012
[    18.260] (==) Using config file: "/etc/X11/xorg.conf"
[    18.260] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.415] (==) ServerLayout "Layout0"
[    18.415] (**) |-->Screen "Screen0" (0)
[    18.415] (**) |   |-->Monitor "Monitor5"
[    18.415] (**) |   |-->Device "Card0"
[    18.415] (**) |-->Input Device "Keyboard0"
[    18.415] (**) |-->Input Device "Mouse0"
[    18.415] (==) Automatically adding devices
[    18.415] (==) Automatically enabling devices
[    18.415] (==) Automatically adding GPU devices
[    18.552] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.552]     Entry deleted from font path.
[    18.552] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.552]     Entry deleted from font path.
[    18.552] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.552]     Entry deleted from font path.
[    18.574] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.574]     Entry deleted from font path.
[    18.574] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.574]     Entry deleted from font path.
[    18.574] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    18.574]     Entry deleted from font path.
[    18.574] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    18.574] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.574] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    18.574] (WW) Disabling Keyboard0
[    18.574] (WW) Disabling Mouse0
[    18.574] (II) Loader magic: 0x7fa59241dc40
[    18.574] (II) Module ABI versions:
[    18.574]     X.Org ANSI C Emulation: 0.4
[    18.574]     X.Org Video Driver: 13.0
[    18.574]     X.Org XInput driver : 18.0
[    18.574]     X.Org Server Extension : 7.0
[    18.576] (--) PCI:*(0:1:0:0) 10de:0a65:1462:8094 rev 162, Mem @ 0xfb000000/16777216, 0xc0000000/268435456, 0xde000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
[    18.576] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.576] Initializing built-in extension Generic Event Extension
[    18.576] Initializing built-in extension SHAPE
[    18.576] Initializing built-in extension MIT-SHM
[    18.576] Initializing built-in extension XInputExtension
[    18.576] Initializing built-in extension XTEST
[    18.576] Initializing built-in extension BIG-REQUESTS
[    18.576] Initializing built-in extension SYNC
[    18.576] Initializing built-in extension XKEYBOARD
[    18.576] Initializing built-in extension XC-MISC
[    18.576] Initializing built-in extension SECURITY
[    18.576] Initializing built-in extension XINERAMA
[    18.576] Initializing built-in extension XFIXES
[    18.576] Initializing built-in extension RENDER
[    18.576] Initializing built-in extension RANDR
[    18.576] Initializing built-in extension COMPOSITE
[    18.576] Initializing built-in extension DAMAGE
[    18.576] Initializing built-in extension MIT-SCREEN-SAVER
[    18.576] Initializing built-in extension DOUBLE-BUFFER
[    18.576] Initializing built-in extension RECORD
[    18.576] Initializing built-in extension DPMS
[    18.576] Initializing built-in extension X-Resource
[    18.576] Initializing built-in extension XVideo
[    18.576] Initializing built-in extension XVideo-MotionCompensation
[    18.576] Initializing built-in extension XFree86-VidModeExtension
[    18.576] Initializing built-in extension XFree86-DGA
[    18.576] Initializing built-in extension XFree86-DRI
[    18.576] Initializing built-in extension DRI2
[    18.576] (II) LoadModule: "glx"
[    18.618] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    19.963] (II) Module glx: vendor="NVIDIA Corporation"
[    19.963]     compiled for 4.0.2, module version = 1.0.0
[    19.963]     Module class: X.Org Server Extension
[    19.963] (II) NVIDIA GLX Module  304.43  Sun Aug 19 20:34:01 PDT 2012
[    19.963] Loading extension GLX
[    19.963] (II) LoadModule: "nvidia"
[    19.963] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    20.198] (II) Module nvidia: vendor="NVIDIA Corporation"
[    20.198]     compiled for 4.0.2, module version = 1.0.0
[    20.198]     Module class: X.Org Video Driver
[    20.229] (II) NVIDIA dlloader X Driver  304.43  Sun Aug 19 20:15:32 PDT 2012
[    20.229] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    20.247] (++) using VT number 7

[    20.249] (II) Loading sub module "fb"
[    20.249] (II) LoadModule: "fb"
[    20.276] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.319] (II) Module fb: vendor="X.Org Foundation"
[    20.319]     compiled for 1.13.0, module version = 1.0.0
[    20.319]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.319] (II) Loading sub module "wfb"
[    20.319] (II) LoadModule: "wfb"
[    20.319] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    20.335] (II) Module wfb: vendor="X.Org Foundation"
[    20.335]     compiled for 1.13.0, module version = 1.0.0
[    20.335]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.335] (II) Loading sub module "ramdac"
[    20.335] (II) LoadModule: "ramdac"
[    20.335] (II) Module "ramdac" already built-in
[    20.351] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    20.351] (==) NVIDIA(0): RGB weight 888
[    20.351] (==) NVIDIA(0): Default visual is TrueColor
[    20.351] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    20.351] (**) NVIDIA(0): Option "UseEDID" "false"
[    20.351] (**) NVIDIA(0): Option "UseDisplayDevice" "CRT-1"
[    20.351] (**) NVIDIA(0): Enabling 2D acceleration
[    20.351] (**) NVIDIA(0): Ignoring EDIDs
[    21.272] (II) NVIDIA(GPU-0): Not probing EDID on CRT-1.
[    21.281] (II) NVIDIA(0): NVIDIA GPU GeForce 210 (GT218) at PCI:1:0:0 (GPU-0)
[    21.281] (--) NVIDIA(0): Memory: 1048576 kBytes
[    21.281] (--) NVIDIA(0): VideoBIOS: 70.18.49.00.03
[    21.281] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    21.281] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    21.283] (--) NVIDIA(0): Valid display device(s) on GeForce 210 at PCI:1:0:0
[    21.283] (--) NVIDIA(0):     CRT-0
[    21.283] (--) NVIDIA(0):     CRT-1 (connected)
[    21.283] (--) NVIDIA(0):     DFP-0
[    21.283] (--) NVIDIA(0):     DFP-1
[    21.283] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    21.283] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    21.283] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    21.283] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    21.283] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    21.283] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    21.283] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    21.283] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies has been enabled on
[    21.283] (**) NVIDIA(0):     all display devices.)
[    21.286] (II) NVIDIA(0): Validated MetaModes:
[    21.286] (II) NVIDIA(0):     "CRT-1:my_1680x1050p60"
[    21.286] (II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
[    21.315] (WW) NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
[    21.315] (WW) NVIDIA(0):     from CRT-1's EDID.
[    21.315] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    21.315] (--) Depth 24 pixmap format is 32 bpp
[    21.315] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    21.318] (II) NVIDIA(0): Setting mode "CRT-1:my_1680x1050p60"
[    21.507] Loading extension NV-GLX
[    21.555] (==) NVIDIA(0): Disabling shared memory pixmaps
[    21.555] (==) NVIDIA(0): Backing store disabled
[    21.555] (==) NVIDIA(0): Silken mouse enabled
[    21.556] (==) NVIDIA(0): DPMS enabled
[    21.556] Loading extension NV-CONTROL
[    21.556] Loading extension XINERAMA
[    21.556] (II) Loading sub module "dri2"
[    21.556] (II) LoadModule: "dri2"
[    21.556] (II) Module "dri2" already built-in
[    21.556] (II) NVIDIA(0): [DRI2] Setup complete
[    21.556] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    21.556] (--) RandR disabled
[    21.569] (II) Initializing extension GLX
[    21.839] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.855] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    21.855] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.855] (II) LoadModule: "evdev"
[    21.855] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.881] (II) Module evdev: vendor="X.Org Foundation"
[    21.881]     compiled for 1.13.0, module version = 2.7.3
[    21.881]     Module class: X.Org XInput Driver
[    21.881]     ABI class: X.Org XInput driver, version 18.0
[    21.881] (II) Using input driver 'evdev' for 'Power Button'
[    21.881] (**) Power Button: always reports core events
[    21.881] (**) evdev: Power Button: Device: "/dev/input/event1"
[    21.881] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.881] (--) evdev: Power Button: Found keys
[    21.881] (II) evdev: Power Button: Configuring as keyboard
[    21.881] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    21.881] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    21.881] (**) Option "xkb_rules" "evdev"
[    21.881] (**) Option "xkb_model" "pc105"
[    21.881] (**) Option "xkb_layout" "fr"
[    21.881] (**) Option "xkb_variant" "latin9"
[    21.882] (II) XKB: reuse xkmfile /var/lib/xkb/server-816A055A5FF7D63897839A4BDEDC3908551E49DA.xkm
[    21.889] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    21.889] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.889] (II) Using input driver 'evdev' for 'Power Button'
[    21.889] (**) Power Button: always reports core events
[    21.889] (**) evdev: Power Button: Device: "/dev/input/event0"
[    21.889] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.889] (--) evdev: Power Button: Found keys
[    21.889] (II) evdev: Power Button: Configuring as keyboard
[    21.889] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    21.889] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    21.889] (**) Option "xkb_rules" "evdev"
[    21.889] (**) Option "xkb_model" "pc105"
[    21.889] (**) Option "xkb_layout" "fr"
[    21.889] (**) Option "xkb_variant" "latin9"
[    21.890] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event14)
[    21.890] (II) No input driver specified, ignoring this device.
[    21.890] (II) This device may have been added with another device file.
[    21.890] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event15)
[    21.890] (II) No input driver specified, ignoring this device.
[    21.890] (II) This device may have been added with another device file.
[    21.890] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event16)
[    21.890] (II) No input driver specified, ignoring this device.
[    21.890] (II) This device may have been added with another device file.
[    21.890] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event17)
[    21.890] (II) No input driver specified, ignoring this device.
[    21.890] (II) This device may have been added with another device file.
[    21.890] (II) config/udev: Adding input device NOVATEK USB Keyboard (/dev/input/event2)
[    21.890] (**) NOVATEK USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    21.890] (II) Using input driver 'evdev' for 'NOVATEK USB Keyboard'
[    21.890] (**) NOVATEK USB Keyboard: always reports core events
[    21.890] (**) evdev: NOVATEK USB Keyboard: Device: "/dev/input/event2"
[    21.890] (--) evdev: NOVATEK USB Keyboard: Vendor 0x603 Product 0xf1
[    21.890] (--) evdev: NOVATEK USB Keyboard: Found keys
[    21.890] (II) evdev: NOVATEK USB Keyboard: Configuring as keyboard
[    21.891] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input2/event2"
[    21.891] (II) XINPUT: Adding extended input device "NOVATEK USB Keyboard" (type: KEYBOARD, id 8)
[    21.891] (**) Option "xkb_rules" "evdev"
[    21.891] (**) Option "xkb_model" "pc105"
[    21.891] (**) Option "xkb_layout" "fr"
[    21.891] (**) Option "xkb_variant" "latin9"
[    21.891] (II) config/udev: Adding input device NOVATEK USB Keyboard (/dev/input/event3)
[    21.891] (**) NOVATEK USB Keyboard: Applying InputClass "evdev pointer catchall"
[    21.891] (**) NOVATEK USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    21.891] (II) Using input driver 'evdev' for 'NOVATEK USB Keyboard'
[    21.891] (**) NOVATEK USB Keyboard: always reports core events
[    21.891] (**) evdev: NOVATEK USB Keyboard: Device: "/dev/input/event3"
[    21.891] (--) evdev: NOVATEK USB Keyboard: Vendor 0x603 Product 0xf1
[    21.891] (--) evdev: NOVATEK USB Keyboard: Found 20 mouse buttons
[    21.891] (--) evdev: NOVATEK USB Keyboard: Found scroll wheel(s)
[    21.891] (--) evdev: NOVATEK USB Keyboard: Found relative axes
[    21.891] (--) evdev: NOVATEK USB Keyboard: Found x and y relative axes
[    21.891] (--) evdev: NOVATEK USB Keyboard: Found keys
[    21.891] (II) evdev: NOVATEK USB Keyboard: Configuring as mouse
[    21.891] (II) evdev: NOVATEK USB Keyboard: Configuring as keyboard
[    21.891] (II) evdev: NOVATEK USB Keyboard: Adding scrollwheel support
[    21.891] (**) evdev: NOVATEK USB Keyboard: YAxisMapping: buttons 4 and 5
[    21.891] (**) evdev: NOVATEK USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.891] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.1/input/input3/event3"
[    21.891] (II) XINPUT: Adding extended input device "NOVATEK USB Keyboard" (type: KEYBOARD, id 9)
[    21.891] (**) Option "xkb_rules" "evdev"
[    21.891] (**) Option "xkb_model" "pc105"
[    21.891] (**) Option "xkb_layout" "fr"
[    21.891] (**) Option "xkb_variant" "latin9"
[    21.891] (II) evdev: NOVATEK USB Keyboard: initialized for relative axes.
[    21.892] (**) NOVATEK USB Keyboard: (accel) keeping acceleration scheme 1
[    21.892] (**) NOVATEK USB Keyboard: (accel) acceleration profile 0
[    21.892] (**) NOVATEK USB Keyboard: (accel) acceleration factor: 2.000
[    21.892] (**) NOVATEK USB Keyboard: (accel) acceleration threshold: 4
[    21.892] (II) config/udev: Adding input device NOVATEK USB Keyboard (/dev/input/mouse0)
[    21.892] (II) No input driver specified, ignoring this device.
[    21.892] (II) This device may have been added with another device file.
[    21.892] (II) config/udev: Adding input device 2.4GHZ Mouse (/dev/input/event4)
[    21.892] (**) 2.4GHZ Mouse: Applying InputClass "evdev keyboard catchall"
[    21.892] (II) Using input driver 'evdev' for '2.4GHZ Mouse'
[    21.892] (**) 2.4GHZ Mouse: always reports core events
[    21.892] (**) evdev: 2.4GHZ Mouse: Device: "/dev/input/event4"
[    21.892] (--) evdev: 2.4GHZ Mouse: Vendor 0x1ea7 Product 0x2
[    21.892] (--) evdev: 2.4GHZ Mouse: Found keys
[    21.892] (II) evdev: 2.4GHZ Mouse: Configuring as keyboard
[    21.892] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.0/input/input4/event4"
[    21.892] (II) XINPUT: Adding extended input device "2.4GHZ Mouse" (type: KEYBOARD, id 10)
[    21.892] (**) Option "xkb_rules" "evdev"
[    21.892] (**) Option "xkb_model" "pc105"
[    21.892] (**) Option "xkb_layout" "fr"
[    21.892] (**) Option "xkb_variant" "latin9"
[    21.893] (II) config/udev: Adding input device 2.4GHZ Mouse (/dev/input/event5)
[    21.893] (**) 2.4GHZ Mouse: Applying InputClass "evdev pointer catchall"
[    21.893] (**) 2.4GHZ Mouse: Applying InputClass "evdev keyboard catchall"
[    21.893] (II) Using input driver 'evdev' for '2.4GHZ Mouse'
[    21.893] (**) 2.4GHZ Mouse: always reports core events
[    21.893] (**) evdev: 2.4GHZ Mouse: Device: "/dev/input/event5"
[    21.893] (--) evdev: 2.4GHZ Mouse: Vendor 0x1ea7 Product 0x2
[    21.893] (--) evdev: 2.4GHZ Mouse: Found 12 mouse buttons
[    21.893] (--) evdev: 2.4GHZ Mouse: Found scroll wheel(s)
[    21.893] (--) evdev: 2.4GHZ Mouse: Found relative axes
[    21.893] (--) evdev: 2.4GHZ Mouse: Found x and y relative axes
[    21.893] (--) evdev: 2.4GHZ Mouse: Found absolute axes
[    21.893] (II) evdev: 2.4GHZ Mouse: Forcing absolute x/y axes to exist.
[    21.893] (--) evdev: 2.4GHZ Mouse: Found keys
[    21.893] (II) evdev: 2.4GHZ Mouse: Configuring as mouse
[    21.893] (II) evdev: 2.4GHZ Mouse: Configuring as keyboard
[    21.893] (II) evdev: 2.4GHZ Mouse: Adding scrollwheel support
[    21.893] (**) evdev: 2.4GHZ Mouse: YAxisMapping: buttons 4 and 5
[    21.893] (**) evdev: 2.4GHZ Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.893] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.1/input/input5/event5"
[    21.893] (II) XINPUT: Adding extended input device "2.4GHZ Mouse" (type: KEYBOARD, id 11)
[    21.893] (**) Option "xkb_rules" "evdev"
[    21.893] (**) Option "xkb_model" "pc105"
[    21.893] (**) Option "xkb_layout" "fr"
[    21.893] (**) Option "xkb_variant" "latin9"
[    21.893] (II) evdev: 2.4GHZ Mouse: initialized for relative axes.
[    21.893] (WW) evdev: 2.4GHZ Mouse: ignoring absolute axes.
[    21.894] (**) 2.4GHZ Mouse: (accel) keeping acceleration scheme 1
[    21.894] (**) 2.4GHZ Mouse: (accel) acceleration profile 0
[    21.894] (**) 2.4GHZ Mouse: (accel) acceleration factor: 2.000
[    21.894] (**) 2.4GHZ Mouse: (accel) acceleration threshold: 4
[    21.894] (II) config/udev: Adding input device 2.4GHZ Mouse (/dev/input/mouse1)
[    21.894] (II) No input driver specified, ignoring this device.
[    21.894] (II) This device may have been added with another device file.
[    21.894] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event10)
[    21.894] (II) No input driver specified, ignoring this device.
[    21.894] (II) This device may have been added with another device file.
[    21.894] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event11)
[    21.894] (II) No input driver specified, ignoring this device.
[    21.894] (II) This device may have been added with another device file.
[    21.894] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event12)
[    21.894] (II) No input driver specified, ignoring this device.
[    21.894] (II) This device may have been added with another device file.
[    21.894] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event13)
[    21.894] (II) No input driver specified, ignoring this device.
[    21.894] (II) This device may have been added with another device file.
[    21.895] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event6)
[    21.895] (II) No input driver specified, ignoring this device.
[    21.895] (II) This device may have been added with another device file.
[    21.895] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event7)
[    21.895] (II) No input driver specified, ignoring this device.
[    21.895] (II) This device may have been added with another device file.
[    21.895] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event8)
[    21.895] (II) No input driver specified, ignoring this device.
[    21.895] (II) This device may have been added with another device file.
[    21.895] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event9)
[    21.895] (II) No input driver specified, ignoring this device.
[    21.895] (II) This device may have been added with another device file.
[    27.842] (II) NVIDIA(GPU-0): Not probing EDID on CRT-1.
[    27.842] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    27.842] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies has been enabled on
[    27.842] (**) NVIDIA(0):     all display devices.)
[    30.327] (II) NVIDIA(GPU-0): Not probing EDID on CRT-1.
[    30.327] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    30.327] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies has been enabled on
[    30.327] (**) NVIDIA(0):     all display devices.)
[    33.697] (II) NVIDIA(GPU-0): Not probing EDID on CRT-1.
[    33.697] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    33.697] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies has been enabled on
[    33.697] (**) NVIDIA(0):     all display devices.)
[    46.767] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
```BicyclerBoy you are a king !

---


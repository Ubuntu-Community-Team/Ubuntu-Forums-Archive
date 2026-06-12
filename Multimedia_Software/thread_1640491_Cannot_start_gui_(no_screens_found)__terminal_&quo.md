---
title: "Cannot start gui (no screens found) / terminal &quot;dual screen&quot;"
date: 2010-12-07
forum: Multimedia Software
---

### Post by cconner94 on 2010-12-07
I've experienced 3 1/2 years of Ubuntu bliss. I have run into the first issue that I cannot solve using these forums, and I'm at my wit's end. 

Problem: I cannot start gdm (gnome?). I get the "Fatal server error: no screens found" error. Also, my terminal screen is duplicated on the top and bottom of the laptop monitor, indicating something gone terribly wrong.

When the problem started: immediately after running standard update to 2.6.32-26 (this time).  Last time, it happened after running a standard update, but that was weeks ago.  I did a complete reinstall (three times, including once to 10.1)

My system:
Ubuntu 10.04.1 LTS (clean install + recent updates)
Kernel version 2.6.32-26
Also have 2.6.32-25.  Neither one works in recovery mode, either.
Machine: Dell Inspiron 1420
Intel Core2 Duo
Nvidia GeForce 8400M GS

---

### Post by cconner94 on 2010-12-07
A little more history:
I did manually update the Nvidia drivers by downloading and running them from the terminal.  The version I'm running currently is 185.18.26.  I also tried 260.19.21 and 173.14.28. Same result on each. 

I've also run nvidia-xconfig.
I've also added "nomodeset" to grub.

Note: as much as I've used these forums to solve issues, I'm embarrassingly "noob"...but not afraid to try anything and do my research.

---

### Post by cconner94 on 2010-12-08
I'm really hoping someone can help me with this...any ideas? I have searched this forum for hours and been unable to find a solution. :confused: 

Thanks in advance for any help!

---

### Post by matt_symes on 2010-12-08
Hi

Can you post the output of your files

/var/log/Xorg.0.log

and 

/etc/Xorg.conf

They might hold some clues. Post them in between code tags.

Could you also post a screen shot of your terminal. I am intrigued. You can use a camera phone

Kind regards

---

### Post by cconner94 on 2010-12-08
Matt -
I will post all you requested when I get back to my computer @ about 4pm CST today. Thanks!

---

### Post by cconner94 on 2010-12-08
First: what's the easiest way to get you those log files? I do have an internet connection on the machine, but I don't know how to extract / e-mail / post the files without re-typing (which I'm perfectly willing to do if that's the only way).

Screen shot (it looks like this from the Dell BIOS screen all the way through login and as I do everything):
[IMG]http://gigemconners.com/photos/albums/tech/ubuntuscreenshot.jpg[/IMG]

---

### Post by matt_symes on 2010-12-08
Hi

Blimy. I have never seen anything like that picture. Something has gone wrong. 

Are you sure there is no hardware issue there? Have you tried on another monitor? Does it only look like that when booted into the console?

Anyway, the best idea to get the files might be to mount a pen drive, copy the two files onto a pen drive, unmount the pen drive, move them to another computer and post the results here.

A whole host of eyes can look over them then.

Kind regards

---

### Post by cconner94 on 2010-12-08
Holy cow...the one thing I didn't try was hooking up to an external monitor, as I (almost) never use this laptop with a monitor. Whatta genius :redface:

It made me go into "failsafe graphics mode". The X-windows type interface came up that says "Ubuntu is running in low-graphics mode. You may need to update your configuration to solve this. 
(EE) Failed to load /usr/lib/xorg/modules/drivers/nvidia_drv.so
(EE) failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available"
This may be from all the horsing around I've done following advice in the forums.

When I try to run nvidia-settings, I get "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." I'm afraid to try it since I'm "in", but I'll do it and post results here. This may have happened because I manually installed the Nvidia driver?

xorg.conf and requested log file coming after I try manually run xconfig.

---

### Post by cconner94 on 2010-12-08
Okay...after selecting "run in failsafe graphics mode" then "Use default (generic) configuration", then rebooting, I got a new set of errors:
[INDENT](EE) Failed to load module "nouveau" (module does not exist, 0)
(EE) NV(0) Couldn't find the DDC routing table. Mode setting will probably fail!
(EE) Screen(s) found, but non have a usable configuration. [/INDENT]

After clicking OK, I selected "Reconfigure graphics" and then "Create new configuration for this hardware" instead. When I click OK, it goes right back to the selection.  Apparently I can't create a new configuration.

If I try to "Restart X" it just goes to a console. If I "Run in failsafe graphics mode for this session", I can get in, but I can't reconfigure the display, which is not optimized for the monitor I'm using.

I guess the question may be: how do I reinstall all the nvidia/graphics-related stuff to get this working?? (May not be the right question).

Thanks for bearing with me on this.

---

### Post by cconner94 on 2010-12-08
Xorg.conf:


# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Fri Aug 14 17:54:58 PDT 2009

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
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
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
    EndSubSection
EndSection

---

### Post by cconner94 on 2010-12-08
Output of Xorg.0.log:


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
Current Operating System: Linux cconner-laptop 2.6.32-26-generic-pae #48-Ubuntu SMP Wed Nov 24 10:31:20 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-26-generic-pae root=UUID=b72cc409-6118-4bec-b9e5-08ea8d89edfa ro nomodeset quiet splash
Build Date: 10 November 2010  11:25:26AM
xorg-server 2:1.7.6-2ubuntu7.4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec  8 16:30:58 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
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
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f1b20
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0427:1028:01f3 nVidia Corporation G86 [GeForce 8400M GS] rev 161, Mem @ 0xfd000000/16777216, 0xe0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/131072
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
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
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
(==) Matched nouveau as autoconfigured driver 0
(==) Matched nv as autoconfigured driver 1
(==) Matched vesa as autoconfigured driver 2
(==) Matched fbdev as autoconfigured driver 3
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nouveau"
(WW) Warning, couldn't open module nouveau
(II) UnloadModule: "nouveau"
(EE) Failed to load module "nouveau" (module does not exist, 0)
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.7.3.901, module version = 2.1.15
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) NV: driver for NVIDIA chipsets:  RIVA 128,  RIVA TNT,  RIVA TNT2,
	 RIVA TNT2 Ultra,  Unknown TNT2,  Vanta,  RIVA TNT2 Model 64,
	 GeForce 6800 Ultra,  GeForce 6800,  GeForce 6800 LE,
	 GeForce 6800 XE,  GeForce 6800 XT,  GeForce 6800 GT,
	 GeForce 6800 GT,  GeForce 6800 GS,  GeForce 6800 XT,
	 Quadro FX 4000,  GeForce 7800 GTX,  GeForce 7800 GTX,
	 GeForce 7800 GT,  GeForce 7800 GS,  GeForce 7800 SLI,
	 GeForce Go 7800,  GeForce Go 7800 GTX,  Quadro FX 4500,
	 Aladdin TNT2,  GeForce 6800 GS,  GeForce 6800,  GeForce 6800 LE,
	 GeForce 6800 XT,  GeForce Go 6800,  GeForce Go 6800 Ultra,
	 Quadro FX Go1400,  Quadro FX 3450/4000 SDI,  Quadro FX 1400,
	 GeForce 256,  GeForce DDR,  Quadro,  GeForce2 MX/MX 400,
	 GeForce2 MX 100/200,  GeForce2 Go,  Quadro2 MXR/EX/Go,
	 GeForce 6600 GT,  GeForce 6600,  GeForce 6600 LE,  GeForce 6600 VE,
	 GeForce Go 6600,  GeForce 6610 XL,  GeForce Go 6600 TE/6200 TE,
	 GeForce 6700 XL,  GeForce Go 6600,  GeForce Go 6600 GT,
	 Quadro NVS 440,  Quadro FX 550,  Quadro FX 550,  Quadro FX 540,
	 GeForce 6200,  GeForce2 GTS,  GeForce2 Ti,  GeForce2 Ultra,
	 Quadro2 Pro,  GeForce 6500,  GeForce 6200 TurboCache(TM),
	 GeForce 6200SE TurboCache(TM),  GeForce 6200 LE,  GeForce Go 6200,
	 Quadro NVS 285,  GeForce Go 6400,  GeForce Go 6200,
	 GeForce Go 6400,  GeForce 6250,  GeForce 7100 GS,  GeForce4 MX 460,
	 GeForce4 MX 440,  GeForce4 MX 420,  GeForce4 MX 440-SE,
	 GeForce4 440 Go,  GeForce4 420 Go,  GeForce4 420 Go 32M,
	 GeForce4 460 Go,  Quadro4 550 XGL,  GeForce4 440 Go 64M,
	 Quadro NVS,  Quadro4 500 GoGL,  GeForce4 410 Go 16M,
	 GeForce4 MX 440 with AGP8X,  GeForce4 MX 440SE with AGP8X,
	 GeForce4 MX 420 with AGP8X,  GeForce4 MX 4000,  GeForce4 448 Go,
	 GeForce4 488 Go,  Quadro4 580 XGL,  Quadro4 NVS 280 SD,
	 Quadro4 380 XGL,  Quadro NVS 50 PCI,  GeForce4 448 Go,
	 GeForce 8800 GTX,  GeForce 8800 GTS,  GeForce 8800 Ultra,
	 Quadro FX 5600,  Quadro FX 4600,  GeForce2 Integrated GPU,
	 GeForce 7350 LE,  GeForce 7300 LE,  GeForce 7300 SE,
	 GeForce Go 7200,  GeForce Go 7300,  GeForce Go 7400,
	 GeForce Go 7400 GS,  Quadro NVS 110M,  Quadro NVS 120M,
	 Quadro FX 350M,  GeForce 7500 LE,  Quadro FX 350,  GeForce 7300 GS,
	 GeForce4 MX Integrated GPU,  GeForce3,  GeForce3 Ti 200,
	 GeForce3 Ti 500,  Quadro DCC,  GeForce 6800,  GeForce 6800 LE,
	 GeForce 6800 GT,  GeForce 6800 XT,  GeForce 6200,
	 GeForce 6200 A-LE,  GeForce 6150,  GeForce 6150 LE,  GeForce 6100,
	 GeForce Go 6150,  Quadro NVS 210S / NVIDIA GeForce 6150LE,
	 GeForce Go 6100,  GeForce4 Ti 4600,  GeForce4 Ti 4400,
	 GeForce4 Ti 4200,  Quadro4 900 XGL,  Quadro4 750 XGL,
	 Quadro4 700 XGL,  GeForce4 Ti 4800,  GeForce4 Ti 4200 with AGP8X,
	 GeForce4 Ti 4800 SE,  GeForce4 4200 Go,  Quadro4 980 XGL,
	 Quadro4 780 XGL,  Quadro4 700 GoGL,  GeForce 7900 GTX,
	 GeForce 7900 GT,  GeForce 7900 GS,  GeForce 7950 GX2,
	 GeForce 7950 GX2,  GeForce 7950 GT},  GeForce Go 7950 GTX,
	 GeForce Go 7900 GS,  GeForce Go 7900 GTX,  Quadro FX 2500M,
	 Quadro FX 1500M,  Quadro FX 5500,  Quadro FX 3500,  Quadro FX 1500,
	 Quadro FX 4500 X2,  GeForce FX 5800 Ultra,  GeForce FX 5800,
	 Quadro FX 2000,  Quadro FX 1000,  GeForce FX 5600 Ultra,
	 GeForce FX 5600,  GeForce FX 560T,  GeForce FX Go5600,
	 GeForce FX Go5650,  Quadro FX Go700,  GeForce FX 5200,
	 GeForce FX 5200 Ultra,  GeForce FX 5200,  GeForce FX 5200LE,
	 GeForce FX Go5200,  GeForce FX Go5250,  GeForce FX 5500,
	 GeForce FX 5100,  GeForce FX Go5200 32M/64M,  Quadro NVS 55/280 PCI,
	 Quadro FX 500/600 PCI,  GeForce FX Go53xx Series,
	 GeForce FX Go5100,  GeForce FX 5900 Ultra,  GeForce FX 5900,
	 GeForce FX 590T,  GeForce FX 5950 Ultra,  GeForce FX 5900ZT,
	 Quadro FX 3000,  Quadro FX 700,  GeForce FX 5700 Ultra,
	 GeForce FX 5700,  GeForce FX 5700LE,  GeForce FX 5700VE,
	 GeForce FX Go5700,  GeForce FX Go5700,  Quadro FX Go1000,
	 Quadro FX 1100,  GeForce 7650 GS,  GeForce 7600 GT,
	 GeForce 7600 GS,  GeForce 7300 GT,  GeForce 7600 LE,
	 GeForce 7300 GT,  GeForce Go 7700,  GeForce Go 7600,
	 GeForce Go 7600 GT},  Quadro NVS 300M,  GeForce Go 7900 SE,
	 Quadro FX 550M,  Quadro FX 560,  GeForce 6150SE,
	 GeForce 6100 nForce 405,  GeForce 6100 nForce 400,
	 GeForce 6100 nForce 420,  GeForce 8600 GTS,  GeForce 8600 GT,
	 GeForce 8600 GT,  GeForce 8600 GS,  GeForce 8400 GS,
	 GeForce 9500M GS,  GeForce 8600M GT,  GeForce 9650M GS,
	 GeForce 8700M GT,  Quadro FX 370,  Quadro NVS 320M,  Quadro FX 570M,
	 Quadro FX 1600M,  Quadro FX 570,  Quadro FX 1700,  GeForce 8400 SE,
	 GeForce 8500 GT,  GeForce 8400 GS,  GeForce 8300 GS,
	 GeForce 8400 GS,  GeForce 8600M GS,  GeForce 8400M GT,
	 GeForce 8400M GS,  GeForce 8400M G,  Quadro NVS 140M,
	 Quadro NVS 130M,  Quadro NVS 135M,  GeForce 9400 GT,
	 Quadro FX 360M,  GeForce 9300M G,  Quadro NVS 290,  GeForce GTX 295,
	 GeForce GTX 280,  GeForce GTX 260,  GeForce GTX 285,  GeForce 7050,
	 GeForce 7025,  Quadro CX,  Quadro FX 5800,  Quadro FX 4800,
	 Quadro FX 3800,  GeForce 8800 GTS 512,  GeForce 9800 GT,
	 GeForce 8800 GT,  GeForce 9800 GX2,  GeForce 9800 GT,
	 GeForce 8800 GS,  GeForce 9800M GTX,  GeForce 8800M GTS,
	 GeForce 9800M GT,  GeForce 8800M GTX,  GeForce 8800 GS,
	 GeForce 9600 GSO,  GeForce 8800 GT,  GeForce 9800 GTX,
	 GeForce 9800 GTX+,  GeForce 9800 GT,  GeForce GTS 250,
	 GeForce 9800M GTX,  Quadro FX 3700,  Quadro FX 3600M,
	 Quadro FX 3700M,  GeForce 9600 GT,  GeForce 9600 GS,
	 GeForce 9600 GSO 512,  GeForce GT 130,  GeForce GT 140,
	 GeForce 9800M GTS,  GeForce 9700M GTS,  GeForce 9800M GS,
	 GeForce 9800M GTS,  Quadro FX 1800,  Quadro FX 2700M,
	 GeForce 9500 GT,  GeForce 9400 GT,  GeForce 9500 GT,
	 GeForce GT 120,  GeForce 9600M GT,  GeForce 9600M GS,
	 GeForce 9600M GT,  GeForce 9700M GT,  GeForce 9500M G,
	 GeForce 9650M GT,  GeForce 9500 GT,  Quadro FX 380,  Quadro FX 580,
	 Quadro FX 770M,  GeForce 9300 GE,  GeForce 9300 GS,
	 GeForce 8400 GS,  GeForce 9300M GS,  GeForce G100,
	 GeForce 9200M GS,  GeForce 9300M GS,  Quadro NVS 150M,
	 Quadro NVS 160M,  Quadro NVS 420,  Quadro FX 370 LP,
	 Quadro NVS 450,  Quadro NVS 295
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(--) NV: Found NVIDIA  GeForce 8400M GS at 01@00:00:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Console is VGA mode 0x3
(II) NV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(==) NV(0): Using hardware cursor
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): MMIO registers mapped at 0xb52a2000
(--) NV(0): Total video RAM: 128.0 MB
(--) NV(0):       BAR1 size: 256.0 MB
(--) NV(0):   Mapped memory: 127.0 MB
(II) NV(0): Linear framebuffer mapped at 0xad3a2000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(EE) NV(0): Couldn't find the DDC routing table.  Mode setting will probably fail!
(II) UnloadModule: "nv"
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules/libint10.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

### Post by matt_symes on 2010-12-08
Hi

There are a couple of error there, but the first is
> 
(II) LoadModule: "nouveau"
(WW) Warning, couldn't open module nouveau
(II) UnloadModule: "nouveau"
(EE) Failed to load module "nouveau" (module does not exist, 0)It wants to load the nouveau drivers for your nvidia card. These need to be installed first. I Dont use nvidia cards myself, i use ATI Radeon cards. So i might not be the best person to answer, but i will do some research.

Someone with that card may be able to help sooner

EDIT: For a quick fix and maybe better resolution you could change the driver name from **nvidia** to **vesa** and reboot 
in Xorg.conf. This may give better resultion (but i am unsure) and be a temporary fix until the nouveau driver is installed.

Section "Device"
    Identifier     "Device0"
    **Driver         "vesa"**
    VendorName     "NVIDIA Corporation"
EndSection

Kind regards

---

### Post by cconner94 on 2010-12-08
I'm hoping to go back to the nvidia drivers, which worked well for me for a long time.  I think I tried to install the nouveau stuff by following the forums. My bad that I got lost in some of it in my desperation.

---

### Post by matt_symes on 2010-12-08
Hi

If you don't want the open source drivers then here is a guide for nvidia drivers.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Hope this helps.

Kind regards

---

### Post by cconner94 on 2010-12-08
Now that I am back in gnome, I am unable to follow the steps recommended.  When I run System > Administration > Nvidia X Server Settings, I get a pop up that says "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server."

I've tried that multiple times and nothing changes.

When I go to System > Administration > Hardware Drivers, I see something interesting:
I have both nvidia_96 and nvidia_current installed. I've tried activating each one by itself.  They will turn the indicator green, but after restarting, the message at the bottom of the drivers screen says "This driver is activated but not currently in use."  Why won't it use the driver?

---

### Post by cconner94 on 2010-12-08
After selecting "failsafe graphics mode" when booting, I get the following message "(EE) Dec 08 21:11:01 NVIDIA(0): Failed to initialize the NVIDIA kernel module."

Here's the entire new /var/log/Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
Current Operating System: Linux cconner-laptop 2.6.32-26-generic-pae #48-Ubuntu SMP Wed Nov 24 10:31:20 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-26-generic-pae root=UUID=b72cc409-6118-4bec-b9e5-08ea8d89edfa ro nomodeset quiet splash
Build Date: 10 November 2010  11:25:26AM
xorg-server 2:1.7.6-2ubuntu7.4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec  8 21:11:00 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
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
(II) Loader magic: 0x81f1b20
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0427:1028:01f3 nVidia Corporation G86 [GeForce 8400M GS] rev 161, Mem @ 0xfd000000/16777216, 0xe0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/131072
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
(**) Dec 08 21:11:01 NVIDIA(0): Enabling RENDER acceleration
(II) Dec 08 21:11:01 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Dec 08 21:11:01 NVIDIA(0):     enabled.
(EE) Dec 08 21:11:01 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Dec 08 21:11:01 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Dec 08 21:11:01 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

### Post by matt_symes on 2010-12-08
Hi

What the output from

lsmod

That will tell you what kernel modules are loaded at the moment. I have read posts in the past where, after installing from the command line, it says the driver is not activated but actually is.

Also if your /etc/X11/xorg.conf file has changed could you repost that and also look in the xorg.0.log and post any errors. I'm off to sleep soon though so, unless someone else helps, it will have to be tomorrow. I think you're getting there though.

Kind regards

---

### Post by cconner94 on 2010-12-08
lsmod output:

```
Module                  Size  Used by
hidp                   11083  1 
snd_hda_codec_idt      51978  1 
snd_hda_intel          22101  4 
rfcomm                 33421  4 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
sco                     7885  2 
binfmt_misc             6587  1 
snd_seq_midi            4557  0 
bridge                 45614  0 
stp                     1655  1 bridge
fbcon                  35102  73 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
tileblit                2031  1 fbcon
ppdev                   5259  0 
bnep                    9436  2 
font                    7557  1 fbcon
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
l2cap                  30624  21 hidp,rfcomm,bnep
lib80211_crypt_tkip     7596  0 
sdhci_pci               5502  0 
bitblit                 4707  1 fbcon
snd_timer              19098  2 snd_pcm,snd_seq
joydev                  8708  0 
wl                   1959630  0 
sdhci                  15654  1 sdhci_pci
softcursor              1189  1 bitblit
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
[COLOR="Red"]nvidia               9582875  0 [/COLOR]
btusb                  10957  4 
dell_wmi                1793  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
bluetooth              49892  10 hidp,rfcomm,sco,bnep,l2cap,btusb
led_class               2864  1 sdhci
vga16fb                11385  1 
dell_laptop             6856  0 
snd                    54180  19 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
intel_agp              24671  0 
[COLOR="red"]agpgart                31788  2 nvidia,intel_agp[/COLOR]
psmouse                63245  0 
vgastate                8961  1 vga16fb
usbhid                 36206  0 
video                  17375  0 
uvcvideo               57118  0 
dcdbas                  5490  1 dell_laptop
hid                    67032  2 hidp,usbhid
output                  1871  1 video
serio_raw               3978  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               27238  0 
ahci                   32232  2 
ieee1394               81213  1 ohci1394
tg3                   109580  0 

```

xorg.conf:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 22 11:44:23 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
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
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
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
    EndSubSection
EndSection

```

---

### Post by cconner94 on 2010-12-08
New information:
- I downloaded and installed from command line the NVIDIA-Linux-x86-195.36.31-pkg1 driver.
- I used Synaptic to remove the .96 driver I had installed
- When restarting, I still go the X-windows error.  I chose the following options:
1) Reconfigure graphics
2) Configure new graphics for this hardware
3) Restart X
My monitor now displays properly (all the way across, whereas before it was about 2/3 of the way)

However, upon reboot I get the same error and have to do it all again.

I think if we can figure out why the Nvidia kernel module isn't loading, we'll be in good shape.

Thanks a ton for your help so far. This relative 'noob' is doing his best.

---

### Post by cconner94 on 2010-12-08
Not sure if it changed, but just in case, xorg.conf:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 22 11:44:23 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
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
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
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
    EndSubSection
EndSection

```

---

### Post by matt_symes on 2010-12-09
Hi

You are right. The reason it is saying 'no screens found' is because the screens section is dependent on the devices section in the xorg.conf file and the devices section loads the nvidia driver and that is failing.

> 
EE) Dec 08 21:11:01 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Dec 08 21:11:01 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Dec 08 21:11:01 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***

That does not tell us much apart from the fact it failed. However it does say to look at the kernel log. So, could you post the output of /var/log/kern.log or /var/log/syslog or  /var/log/messages. First have a look in the logs and see if you can see anything that looks like nvidia errors (vga, NVRM etc) just post the relevant parts as the files can get very large.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
```

As you can see above the xorg.conf file was generated by nvidia-xconfig and this tool configures the xorg.conf file so that file should be fine.

However reading the man page for the tool, it also does other things when it is run.

[http://linux.die.net/man/1/nvidia-xconfig](http://linux.die.net/man/1/nvidia-xconfig)

It also unloads some modules and loads others and i am wondering if this is what is happening when you reconfigure the graphics as the driver is obviously working then. I am wondering if it is a module conflict. Hopefully the logs can tell us more.

In the meantime read this

[http://ohioloco.ubuntuforums.org/showthread.php?t=1565491](http://ohioloco.ubuntuforums.org/showthread.php?t=1565491)

I think this may be a divide and conquer approach. Hopefully it is fixable.

Kind regards

---

### Post by cconner94 on 2010-12-10
Thank you for those suggestions.  

I'll post those logs and read as you suggest. I'm away from that computer for the next few hours, but I will get to it ASAP. 

I hope it's not obvious stuff I'm missing, but I've tried everything that I do understand (I always see the signatures that say "Don't run posted scripts that you don't understand!").

---

### Post by cconner94 on 2010-12-14
From /var/log/kern.log....this looks like it may be the problem!  However, I've no clue how to fix it. I'll look in the forums, but any advice is welcome.


```
Dec 14 06:34:05 cconner-laptop kernel: [   17.334208] NVRM: API mismatch: the client has the version 195.36.24, but
Dec 14 06:34:05 cconner-laptop kernel: [   17.334210] NVRM: this kernel module has the version 195.36.31.  Please
Dec 14 06:34:05 cconner-laptop kernel: [   17.334211] NVRM: make sure that this kernel module and all NVIDIA driver
Dec 14 06:34:05 cconner-laptop kernel: [   17.334212] NVRM: components have the same version.
```

Update: same message in var/log/syslog
Update: same message in /var/log/messages

---

### Post by cconner94 on 2010-12-14
What I gather from the ohioloco thread above is that I should remove the nvidia drivers and reinstall.  When I go to System > Admin > Hardware drivers, I can select nvidia-current and deactivate (the message says "This driver is activated but not currently in use"), but I cannot remove.

---

### Post by cconner94 on 2010-12-14
From [https://help.ubuntu.com/community/NvidiaTroubleshooting](https://help.ubuntu.com/community/NvidiaTroubleshooting) I found this:

**Revert from driver from nvidia to the ubuntu provided**
If you have installed the nvidia driver as a manual way and you want to revert to the ubuntu nvidia driver:

 1. Go to the directory where is NVIDIA*.run, and run sudo NVIDIA*.run --uninstall.
 2. You have to reinstall all the packages that refers to nvidia via synaptic.
 3. Execute restricted-manager and enable the nvidia-glx*.

Next time you reboot you will get a nvidia driver working on all kernels, no API mismatch, No could not load nvidia driver...

Does this sound like the right solution?  If so, how do I find  NVIDIA*.run?  The thread was last edited 2009-04-30, so I'd like to hear from someone if this is still recommended.

---

### Post by moodysega on 2011-02-03
i have the same problem.
it seems frustating that no solving yet.

i've just donlod the latest 10.10 ubuntu,
burn it to cd, and try it in my laptop, and seems working well with wireless,
but when i install it to computer...
after finish install... remove cd.... restart
it's bad, no gui....
but i can use it in "failsafe graphics mode", it cannot load in normal start.
maybe it because of graphic driver.
(my notebook is; compaq... intel display)

i have install it to my desktop(nvidia geforce 9600GT)...
work as charm... thanks...

so... anybody??? help...

---

### Post by cconner94 on 2011-02-04
Turns out, my ultimate problem was a bad NVIDIA chip.  There's a class action settlement defined here: [http://nvidiasettlement.com](http://nvidiasettlement.com).

Best of luck to anyone with this issue...mine turned out to be hardware after all.

Cheers,
Casey

---


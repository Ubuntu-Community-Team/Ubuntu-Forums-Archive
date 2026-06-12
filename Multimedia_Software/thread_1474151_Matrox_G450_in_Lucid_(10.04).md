---
title: "Matrox G450 in Lucid (10.04)"
date: 2010-05-05
forum: Multimedia Software
---

### Post by psyper on 2010-05-05
I've been using the older version of ubuntu for a couple of months now but always had a problem with my dual video card - matrox g450.  I have since upgraded to 10.04 and still getting the same problem.

When booting up I'm getting the same display showing on both monitors.  I have been through a few things with my old ubuntu by googling the issue and downloading patches and xorg.conf files etc but it never resolved the issue or made it worst.  I've now got a fresh install of lucid and want to resolve my monitor issue from scratch with someone step by step.  If there are any settings or files you need please let me know and I'll be happy to supply the details on this thread.

Help is greatly appriciated :D

---

### Post by psyper on 2010-05-13
bump!!

btw if this helps I have no xorg.conf file as its a default install.

my xorg.0.log:

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux desktop 2.6.32-22-generic-pae #33-Ubuntu SMP Wed Apr 28 14:57:29 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=93c53d60-5e4c-4b66-ae3a-880591c9324d ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri May  7 17:33:34 2010
(==) Using config file: "/etc/X11/xorg.conf"
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
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 102b:0525:102b:0641 Matrox Graphics, Inc. MGA G400/G450 rev 130, Mem @ 0xf4000000/33554432, 0xfe8fc000/16384, 0xfe000000/8388608, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
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
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
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
(==) Matched mga as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "mga"
(II) Loading /usr/lib/xorg/modules/drivers/mga_drv.so
(II) Module mga: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.4.11
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
(II) MGA: driver for Matrox chipsets: mga2064w, mga1064sg, mga2164w,
	mga2164w AGP, mgag100, mgag100 PCI, mgag200, mgag200 PCI,
	mgag200 SE A PCI, mgag200 SE B PCI, mgag200 EV Maxim,
	mgag200 eW Nuvoton, mgag200eH, mgag400, mgag550
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
(--) MGA(0): Chipset: "mgag400" (G450)
(--) MGA(0): Linear framebuffer at 0xF4000000
(--) MGA(0): MMIO registers at 0xFE8FC000
(--) MGA(0): Pseudo-DMA transfer window at 0xFE000000
(II) MGA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) MGA(0): Depth 24, (--) framebuffer bpp 32
(==) MGA(0): RGB weight 888
(==) MGA(0): Using AGP 1x mode
(==) MGA(0): Using HW cursor
(==) MGA(0): Using XAA acceleration
(--) MGA(0): Video BIOS info block at offset 0x079C0
(==) MGA(0): VideoRAM: 32768 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) MGA(0): I2C bus "DDC P1" initialized.
(II) MGA(0): I2C device "DDC P1:ddc2" registered at address 0xA0.
(II) MGA(0): I2C device "DDC P1:DDC control interface" registered at address 0x6E.
(II) MGA(0): I2C monitor info
(II) MGA(0): Manufacturer: NTS  Model: 1  Serial#: 1
(II) MGA(0): Year: 2007  Week: 5
(II) MGA(0): EDID Version: 1.3
(II) MGA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) MGA(0): Sync:  Separate
(II) MGA(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) MGA(0): Gamma: 2.20
(II) MGA(0): No DPMS capabilities specified; RGB/Color Display
(II) MGA(0): First detailed timing is preferred mode
(II) MGA(0): redX: 0.599 redY: 0.348   greenX: 0.310 greenY: 0.550
(II) MGA(0): blueX: 0.150 blueY: 0.115   whiteX: 0.312 whiteY: 0.328
(II) MGA(0): Supported established timings:
(II) MGA(0): 720x400@70Hz
(II) MGA(0): 640x480@60Hz
(II) MGA(0): 640x480@72Hz
(II) MGA(0): 800x600@56Hz
(II) MGA(0): 800x600@60Hz
(II) MGA(0): 800x600@72Hz
(II) MGA(0): 800x600@75Hz
(II) MGA(0): 1024x768@60Hz
(II) MGA(0): 1024x768@70Hz
(II) MGA(0): 1024x768@75Hz
(II) MGA(0): Manufacturer's mask: 0
(II) MGA(0): Supported detailed timing:
(II) MGA(0): clock: 106.5 MHz   Image Size:  410 x 256 mm
(II) MGA(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) MGA(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) MGA(0):  
(II) MGA(0): Monitor name: M-SERIAL
(II) MGA(0): Serial No: 
(II) MGA(0): EDID (in hex):
(II) MGA(0): 	00ffffffffffff003a93010001000000
(II) MGA(0): 	0511010308291a780a47a099594f8c26
(II) MGA(0): 	1d5054abce0001010101010101010101
(II) MGA(0): 	0101010101019a29a0d0518422305098
(II) MGA(0): 	36009a0011000018000000fe000a2020
(II) MGA(0): 	20202020202020202020000000fc004d
(II) MGA(0): 	2d53455249414c0a20202020000000ff
(II) MGA(0): 	000a2020202020202020202020200020
(II) MGA(0): end of monitor info
(II) MGA(0): EDID vendor "NTS", prod id 1
(II) MGA(0): Printing DDC gathered Modelines:
(II) MGA(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync -vsync (55.9 kHz)
(II) MGA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) MGA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) MGA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) MGA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) MGA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) MGA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) MGA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(==) MGA(0): Using gamma correction (1.0, 1.0, 1.0)
(==) MGA(0): Min pixel clock is 17 MHz
(--) MGA(0): Max pixel clock is 600 MHz
(II) MGA(0): <default monitor>: Using hsync range of 31.47-60.02 kHz
(II) MGA(0): <default monitor>: Using vrefresh range of 56.25-75.03 Hz
(II) MGA(0): Estimated virtual size for aspect ratio 1.5769 is 1440x900
(II) MGA(0): Clock range:  17.75 to 600.00 MHz
(II) MGA(0): Not using default mode "640x350" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "640x400" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "720x400" (vrefresh out of range)
(II) MGA(0): Not using default mode "360x200" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "640x480" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x240" (vrefresh out of range)
(II) MGA(0): Not using default mode "800x600" (vrefresh out of range)
(II) MGA(0): Not using default mode "400x300" (vrefresh out of range)
(II) MGA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) MGA(0): Not using default mode "512x384" (vrefresh out of range)
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(II) MGA(0): Not using default mode "512x384" (hsync out of range)
(II) MGA(0): Not using default mode "1152x864" (hsync out of range)
(II) MGA(0): Not using default mode "576x432" (hsync out of range)
(II) MGA(0): Not using default mode "1280x960" (height too large for virtual size)
(II) MGA(0): Not using default mode "1280x960" (height too large for virtual size)
(II) MGA(0): Not using default mode "640x480" (hsync out of range)
(II) MGA(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) MGA(0): Not using default mode "640x512" (hsync out of range)
(II) MGA(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) MGA(0): Not using default mode "640x512" (hsync out of range)
(II) MGA(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) MGA(0): Not using default mode "640x512" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) MGA(0): Not using default mode "896x672" (hsync out of range)
(II) MGA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) MGA(0): Not using default mode "896x672" (hsync out of range)
(II) MGA(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) MGA(0): Not using default mode "928x696" (hsync out of range)
(II) MGA(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) MGA(0): Not using default mode "928x696" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) MGA(0): Not using default mode "960x720" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) MGA(0): Not using default mode "960x720" (hsync out of range)
(II) MGA(0): Not using default mode "1152x864" (hsync out of range)
(II) MGA(0): Not using default mode "576x432" (hsync out of range)
(II) MGA(0): Not using default mode "1152x864" (hsync out of range)
(II) MGA(0): Not using default mode "576x432" (hsync out of range)
(II) MGA(0): Not using default mode "1152x864" (hsync out of range)
(II) MGA(0): Not using default mode "576x432" (hsync out of range)
(II) MGA(0): Not using default mode "1152x864" (hsync out of range)
(II) MGA(0): Not using default mode "576x432" (hsync out of range)
(II) MGA(0): Not using default mode "1152x864" (hsync out of range)
(II) MGA(0): Not using default mode "576x432" (hsync out of range)
(II) MGA(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) MGA(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) MGA(0): Not using default mode "700x525" (hsync out of range)
(II) MGA(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) MGA(0): Not using default mode "700x525" (hsync out of range)
(II) MGA(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) MGA(0): Not using default mode "700x525" (hsync out of range)
(II) MGA(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) MGA(0): Not using default mode "700x525" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) MGA(0): Not using default mode "800x512" (hsync out of range)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "840x525" (hsync out of range)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "840x525" (hsync out of range)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "840x525" (hsync out of range)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "840x525" (hsync out of range)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "840x525" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) MGA(0): Not using default mode "960x540" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "960x600" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) MGA(0): Not using default mode "960x720" (hsync out of range)
(II) MGA(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(II) MGA(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(II) MGA(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(--) MGA(0): Has SDRAM
(--) MGA(0): Virtual size is 1440x900 (pitch 1440)
(**) MGA(0): *Driver mode "1440x900": 106.5 MHz, 55.9 kHz, 59.9 Hz
(II) MGA(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync -vsync (55.9 kHz)
(**) MGA(0): *Default mode "1440x900": 106.5 MHz, 55.9 kHz, 59.9 Hz
(II) MGA(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(**) MGA(0): *Default mode "1360x768": 84.8 MHz, 47.7 kHz, 59.8 Hz
(II) MGA(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(**) MGA(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
(II) MGA(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) MGA(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) MGA(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) MGA(0): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) MGA(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) MGA(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) MGA(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) MGA(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) MGA(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) MGA(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) MGA(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) MGA(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) MGA(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) MGA(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) MGA(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) MGA(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) MGA(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) MGA(0): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) MGA(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) MGA(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MGA(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) MGA(0): *Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) MGA(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) MGA(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) MGA(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) MGA(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) MGA(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) MGA(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MGA(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) MGA(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) MGA(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) MGA(0): *Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
(II) MGA(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
(**) MGA(0): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) MGA(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) MGA(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MGA(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MGA(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) MGA(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) MGA(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) MGA(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) MGA(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) MGA(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MGA(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MGA(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) MGA(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) MGA(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
(**) MGA(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
(II) MGA(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
(**) MGA(0): *Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
(II) MGA(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
(**) MGA(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) MGA(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) MGA(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) MGA(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) MGA(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) MGA(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) MGA(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) MGA(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) MGA(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
(**) MGA(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) MGA(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(**) MGA(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) MGA(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) MGA(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) MGA(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) MGA(0): Display dimensions: (410, 260) mm
(**) MGA(0): DPI set to (89, 87)
(II) MGA(0): YDstOrg is set to 0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.1
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(--) MGA(0): 16 DWORD fifo
(==) MGA(0): Default visual is TrueColor
(II) MGA(0): [drm] bpp: 32 depth: 24
(II) MGA(0): [drm] Sarea 2200+664: 2864
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] loaded kernel module for "mga" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) MGA(0): [drm] Using the DRM lock SAREA also for drawables.
(II) MGA(0): [drm] framebuffer handle = 0xf4000000
(II) MGA(0): [drm] added 1 reserved context for kernel
(II) MGA(0): X context handle = 0x1
(II) MGA(0): [drm] installed DRM signal handler
(II) MGA(0): [dri] visual configs initialized
(II) MGA(0): Memory manager initialized to (0,0) (1440,1799)
(II) MGA(0): Largest offscreen area available: 1440 x 899
(II) MGA(0): Reserved back buffer at offset 0x9e4000
(II) MGA(0): Reserved depth buffer at offset 0xed6000
(II) MGA(0): Reserved 12512 kb for textures at offset 0x13c8000
(II) MGA(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid filled trapezoids
	8x8 mono pattern filled rectangles
	8x8 mono pattern filled trapezoids
	Indirect CPU to Screen color expansion
	Screen to Screen color expansion
	Solid Lines
	Dashed Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		11 256x256 slots
(==) MGA(0): Backing store disabled
(==) MGA(0): Silken mouse enabled
(==) MGA(0): DPMS enabled
(II) MGA(0): Using overlay video
(II) MGA(0): [DRI] installation complete
(II) MGA(0): [drm] Mapped 128 DMA buffers
(II) MGA(0): [drm] dma control initialized, using IRQ 16
(II) MGA(0): Direct rendering enabled
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
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: Loaded and initialized /usr/lib/dri/mga_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event4)
(**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event4"
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
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
```

and my lspi output:
```
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 82)
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
03:04.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
03:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

Please help!:)

---

### Post by eldiabolosk on 2010-12-12
Installed my system with Xubuntu Lucid 10.04 and have two monitors with high res and high freq, but have no option to run a dual monitor system wuth Matrox G450 PCI.

If you solved the problem or have a working system please let me know how.

Ed.

---


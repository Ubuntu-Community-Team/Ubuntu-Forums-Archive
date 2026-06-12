---
title: "High CPU usage with prosavage (KN266 chipset)"
date: 2009-04-05
forum: Multimedia Software
---

### Post by hotpurple on 2009-04-05
Hi,

I've got a packard bell easynote laptop with an Athlon XP-M 2400+ cpu, 1.25gb ram and a VIA KN266 chipset. Overall it's ok for most things, but I've always had a problem under ubuntu in that any movement on the screen causes a high cpu utilisation. For example while writing this post the moving smilies on the right are causing approx 25% cpu usage. Moving the mouse or using the trackpad results in approx 50-75% cpu usage etc. What could be causing this? I've attached the contents of the xorg.log file below. This is on a clean install of Ubuntu Jaunty Beta.

Thanks in advance.

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux laptop 2.6.28-11-generic #40-Ubuntu SMP Fri Apr 3 17:39:51 UTC 2009 i686
Build Date: 03 April 2009  07:14:39AM
xorg-server 2:1.6.0-0ubuntu9 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr  5 21:25:27 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) S3 Inc. VT8375 [ProSavage8 KM266/KL266] rev 0, Mem @ 0xe0000000/524288, 0x90000000/134217728, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched savage from file name savage.ids
(==) Matched savage for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "savage"
(II) Loading /usr/lib/xorg/modules/drivers//savage_drv.so
(II) Module savage: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) SAVAGE: driver (version 2.2.1) for S3 Savage chipsets: Savage4,
	Savage3D, Savage3D-MV, Savage2000, Savage/MX-MV, Savage/MX,
	Savage/IX-MV, Savage/IX, ProSavage PM133, ProSavage KM133,
	Twister PN133, Twister KN133, SuperSavage/MX 128, SuperSavage/MX 64,
	SuperSavage/MX 64C, SuperSavage/IX 128, SuperSavage/IX 128,
	SuperSavage/IX 64, SuperSavage/IX 64, SuperSavage/IXC 64,
	SuperSavage/IXC 64, ProSavage DDR, ProSavage DDR-K
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) SAVAGE(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 16/16
(==) SAVAGE(0): Depth 16, (--) framebuffer bpp 16
(==) SAVAGE(0): RGB weight 565
(==) SAVAGE(0): Default visual is TrueColor
(II) SAVAGE(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) SAVAGE(0): Using XAA acceleration architecture
(==) SAVAGE(0): Using HW cursor
(==) SAVAGE(0): Using video BIOS to set modes
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 3.0
(II) SAVAGE(0): VESA VBE Total Mem: 31680 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Graphics ProSavage DDR Family BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 2.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Garphics Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 3.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 0.0
(--) SAVAGE(0): Chip: id 8d04, "ProSavage DDR-K"
(--) SAVAGE(0): Engine: "ProSavageDDR"
(--) SAVAGE(0): AGP card detected
(==) SAVAGE(0): Using BusType PCI by default
(==) SAVAGE(0): Using PCI DMA
(==) SAVAGE(0): Will try command and vertex DMA mode
(==) SAVAGE(0): Using gamma correction (1.0, 1.0, 1.0)
(--) SAVAGE(0): probed videoram:  32768k
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) SAVAGE(0): No DDC signal
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) SAVAGE(0): I2C bus "I2C bus" initialized.
(II) SAVAGE(0): I2C device "I2C bus:E-EDID segment register" registered at address 0x60.
(II) SAVAGE(0): I2C device "I2C bus:ddc2" registered at address 0xA0.
(--) SAVAGE(0): Detected current MCLK value of 14.318 MHz
(--) SAVAGE(0): 1024x768 TFT LCD panel detected and active
(--) SAVAGE(0): - Limiting video mode to 1024x768
(--) SAVAGE(0): Found 13 modes at this depth:
    [10e] 320 x 200, 70Hz
    [133] 320 x 240, 72Hz
    [143] 400 x 300, 72Hz
    [153] 512 x 384, 70Hz
    [11d] 640 x 400, 70Hz
    [111] 640 x 480, 60Hz, 75Hz, 85Hz, 100Hz, 160Hz
    [114] 800 x 600, 60Hz, 75Hz, 85Hz
    [117] 1024 x 768, 60Hz, 70Hz, 75Hz, 85Hz, 100Hz, 130Hz
    [17a] 1280 x 768, 60Hz
    [14f] 1280 x 960, 60Hz, 85Hz
    [11a] 1280 x 1024, 60Hz, 75Hz, 85Hz, 100Hz
    [13c] 1400 x 1050, 60Hz, 75Hz
    [122] 1600 x 1200, 60Hz
(II) SAVAGE(0): Configured Monitor: Using hsync range of 31.50-47.82 kHz
(II) SAVAGE(0): Configured Monitor: Using vrefresh range of 56.00-59.92 Hz
(II) SAVAGE(0): Configured Monitor: Using maximum pixel clock of 63.50 MHz
(II) SAVAGE(0): Estimated virtual size for aspect ratio 1.3333 is 1024x768
(II) SAVAGE(0): Clock range:  10.00 to 250.00 MHz
(--) SAVAGE(0): No suitable BIOS mode found for 640x350 85Hz.
(II) SAVAGE(0): Not using default mode "640x350" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 320x175 85Hz.
(II) SAVAGE(0): Not using default mode "320x175" (no mode of this name)
(--) SAVAGE(0): Chose mode 11d at 70Hz.
(II) SAVAGE(0): Not using default mode "640x400" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 10e at 70Hz.
(II) SAVAGE(0): Not using default mode "320x200" (vrefresh out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 720x400 85Hz.
(II) SAVAGE(0): Not using default mode "720x400" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 360x200 85Hz.
(II) SAVAGE(0): Not using default mode "360x200" (no mode of this name)
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(II) SAVAGE(0): Not using default mode "640x480" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(II) SAVAGE(0): Not using default mode "320x240" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(II) SAVAGE(0): Not using default mode "640x480" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(II) SAVAGE(0): Not using default mode "320x240" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(II) SAVAGE(0): Not using default mode "640x480" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(II) SAVAGE(0): Not using default mode "320x240" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 70Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 75Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x960" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1280x960" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1280x1024" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 60Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x1024" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 75Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x1024" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 85Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1792x1344" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 60Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1792x1344" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 75Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1856x1392" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 60Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1856x1392" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 75Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 60Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 75Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 832x624 74Hz.
(II) SAVAGE(0): Not using default mode "832x624" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 416x312 74Hz.
(II) SAVAGE(0): Not using default mode "416x312" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 60Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 70Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 74Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 85Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 85Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 100Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1360x768" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 680x384 59Hz.
(II) SAVAGE(0): Not using default mode "680x384" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1360x768" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 680x384 59Hz.
(II) SAVAGE(0): Not using default mode "680x384" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 59Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 70Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 74Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 85Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1440x900" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 720x450 59Hz.
(II) SAVAGE(0): Not using default mode "720x450" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1600x1024" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 800x512 60Hz.
(II) SAVAGE(0): Not using default mode "800x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1680x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 59Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1680x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 60Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1680x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 69Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1680x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 74Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1680x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 85Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1080" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x540 59Hz.
(II) SAVAGE(0): Not using default mode "960x540" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1200" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x600 59Hz.
(II) SAVAGE(0): Not using default mode "960x600" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 85Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "2048x1536" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Virtual size is 1024x768 (pitch 1024)
(**) SAVAGE(0): *Driver mode "1024x768": 56.0 MHz, 47.3 kHz, 59.9 Hz
(II) SAVAGE(0): Modeline "1024x768"x59.9   56.00  1024 1072 1104 1184  768 771 775 790 +hsync -vsync (47.3 kHz)
(**) SAVAGE(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SAVAGE(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) SAVAGE(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) SAVAGE(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) SAVAGE(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) SAVAGE(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) SAVAGE(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) SAVAGE(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) SAVAGE(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) SAVAGE(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) SAVAGE(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 3.0
(II) SAVAGE(0): VESA VBE Total Mem: 31680 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Graphics ProSavage DDR Family BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 2.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Garphics Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 3.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 0.0
(II) SAVAGE(0): 4740 kB of Videoram needed for 3D; 32768 kB of Videoram available
(II) SAVAGE(0): Sufficient Videoram available for 3D
(II) SAVAGE(0): [drm] bpp: 16 depth: 16
(II) SAVAGE(0): [drm] Sarea 2200+284: 2484
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card2
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card3
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card4
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card5
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card6
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card7
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card8
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card9
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card10
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card11
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card12
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card13
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card14
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmGetBusid returned ''
(II) [drm] loaded kernel module for "savage" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) SAVAGE(0): [drm] Using the DRM lock SAREA also for drawables.
(II) SAVAGE(0): [drm] framebuffer handle = 0x90000000
(II) SAVAGE(0): [drm] added 1 reserved context for kernel
(II) SAVAGE(0): X context handle = 0x1
(II) SAVAGE(0): [drm] installed DRM signal handler
(II) SAVAGE(0): [drm] aperture handle = 0x92000000
(II) SAVAGE(0): [drm] PCI command DMA handle = 0x35f00000
(II) SAVAGE(0): [drm] Enabling ShadowStatus for DRI.
(II) SAVAGE(0): [drm] Status handle = 0x35e86000
(II) SAVAGE(0): [drm] Status page mapped at 0xb7fc0000
(II) SAVAGE(0): [dri] visual configs initialized
(**) SAVAGE(0): DRI is enabled
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(II) SAVAGE(0): virtualX:1024,virtualY:768
(II) SAVAGE(0): bpp:16,tiledwidthBytes:2048,tiledBufferSize:1572864 
(II) SAVAGE(0): bpp:16,widthBytes:2048,BufferSize:1572864 
(II) SAVAGE(0): videoRambytes:0x02000000 
(II) SAVAGE(0): textureSize:0x0195f000 
(II) SAVAGE(0): textureSize:0x0195f000 
(II) SAVAGE(0): textureOffset:0x00680000 
(II) SAVAGE(0): depthOffset:0x00500000,depthPitch:2048
(II) SAVAGE(0): backOffset:0x00380000,backPitch:2048
(II) SAVAGE(0): Reserved back buffer at offset 0x380000
(II) SAVAGE(0): Reserved depth buffer at offset 0x500000
(II) SAVAGE(0): Reserved 25980 kb for textures at offset 0x680000
(II) SAVAGE(0): Using 1023 lines for offscreen memory.
(II) SAVAGE(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Image Writes
	Setting up tile and stipple cache:
		28 128x128 slots
		7 256x256 slots
(==) SAVAGE(0): Backing store disabled
(II) SAVAGE(0): DPMS enabled
(II) SAVAGE(0): [DRI] installation complete
(II) SAVAGE(0): [junkers]pSAVAGEDRIServer:
(II) SAVAGE(0): [junkers]	reserved_map_agpstart:0x00000000
(II) SAVAGE(0): [junkers]	reserved_map_idx:0x00000000
(II) SAVAGE(0): [junkers]	sarea_priv_offset:0x00000000
(II) SAVAGE(0): [junkers]	chipset:0x00000000
(II) SAVAGE(0): [junkers]	sgram:0x00000000
(II) SAVAGE(0): [junkers]	frontbufferSize:0x00180000
(II) SAVAGE(0): [junkers]	frontOffset:0x00000000
(II) SAVAGE(0): [junkers]	frontPitch:0x00000800
(II) SAVAGE(0): [junkers]	backbufferSize:0x00180000
(II) SAVAGE(0): [junkers]	backOffset:0x00380000
(II) SAVAGE(0): [junkers]	backPitch:0x00000800
(II) SAVAGE(0): [junkers]	depthbufferSize:0x00180000
(II) SAVAGE(0): [junkers]	depthOffset:0x00500000
(II) SAVAGE(0): [junkers]	depthPitch:0x00000800
(II) SAVAGE(0): [junkers]	textureOffset:0x00680000
(II) SAVAGE(0): [junkers]	textureSize:0x0195f000
(II) SAVAGE(0): [junkers]	textureSize:0x0195f000
(II) SAVAGE(0): [junkers]	logTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers]	agp:handle:0x00000000
(II) SAVAGE(0): [junkers]	agp:offset:0x00000000
(II) SAVAGE(0): [junkers]	agp:size:0x00000000
(II) SAVAGE(0): [junkers]	agp:map:0x00000000
(II) SAVAGE(0): [junkers]	registers:handle:0xe0000000
(II) SAVAGE(0): [junkers]	registers:offset:0x00000000
(II) SAVAGE(0): [junkers]	registers:size:0x00080000
(II) SAVAGE(0): [junkers]	registers:map:0x00000000
(II) SAVAGE(0): [junkers]	status:handle:0x35e86000
(II) SAVAGE(0): [junkers]	status:offset:0x00000000
(II) SAVAGE(0): [junkers]	status:size:0x00001000
(II) SAVAGE(0): [junkers]	status:map:0xb7fc0000
(II) SAVAGE(0): [junkers]	agpTextures:handle:0x00000000
(II) SAVAGE(0): [junkers]	agpTextures:offset:0x00000000
(II) SAVAGE(0): [junkers]	agpTextures:size:0x00000000
(II) SAVAGE(0): [junkers]	apgTextures:map:0x00000000
(II) SAVAGE(0): [junkers]	logAgpTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers]	cmdDma:handle:0x35f00000
(II) SAVAGE(0): [junkers]	cmdDma:offset:0x00000000
(II) SAVAGE(0): [junkers]	cmdDma:size:0x00100000
(II) SAVAGE(0): [junkers]	cmdDma:map:0x00000000
(II) SAVAGE(0): [junkers]pSAVAGEDRI:
(II) SAVAGE(0): [junkers]	chipset:0x00000006
(II) SAVAGE(0): [junkers]	width:0x00000400
(II) SAVAGE(0): [junkers]	height:0x00000300
(II) SAVAGE(0): [junkers]	mem:0x02000000
(II) SAVAGE(0): [junkers]	cpp:2
(II) SAVAGE(0): [junkers]	zpp:2
(II) SAVAGE(0): [junkers]	agpMode:0
(II) SAVAGE(0): [junkers]	bufferSize:65536
(II) SAVAGE(0): [junkers]	frontbufferSize:0x00180000
(II) SAVAGE(0): [junkers]	frontOffset:0x00000000
(II) SAVAGE(0): [junkers]	backbufferSize:0x00180000
(II) SAVAGE(0): [junkers]	backOffset:0x00380000
(II) SAVAGE(0): [junkers]	depthbufferSize:0x00180000
(II) SAVAGE(0): [junkers]	depthOffset:0x00500000
(II) SAVAGE(0): [junkers]	textureOffset:0x00680000
(II) SAVAGE(0): [junkers]	textureSize:0x01800000
(II) SAVAGE(0): [junkers]	logTextureGranularity:0x00000015
(II) SAVAGE(0): [junkers]	agpTextureHandle:0x00000000
(II) SAVAGE(0): [junkers]	agpTextureSize:0x00000000
(II) SAVAGE(0): [junkers]	logAgpTextureGranularity:0x00000020
(II) SAVAGE(0): [junkers]	apertureHandle:0x92000000
(II) SAVAGE(0): [junkers]	apertureSize:0x05000000
(II) SAVAGE(0): [junkers]	aperturePitch:0x00001000
(II) SAVAGE(0): [junkers]	statusHandle:0x35e86000
(II) SAVAGE(0): [junkers]	statusSize:0x00001000
(II) SAVAGE(0): [junkers]	sarea_priv_offset:0x00000898
(II) SAVAGE(0): Direct rendering enabled
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/savage_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "gb"
(**) AT Translated Set 2 keyboard: xkb_layout: "gb"
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event6"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found

```

---


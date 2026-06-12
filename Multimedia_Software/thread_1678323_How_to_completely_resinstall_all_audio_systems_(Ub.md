---
title: "How to completely resinstall all audio systems (Ubuntu HDMI epic failure..) ?"
date: 2011-01-30
forum: Multimedia Software
---

### Post by Raptor Ramjet on 2011-01-30
Hello,

After two years worth of trying to get HDMI audio working on, what should be, a MythTV box I am now fed up to the teeth with it.  Utterly, completely sick and dissilusioned with Ubuntu & HDMI.

Firstly there is no problem with the hardware as I managed to get HDMI audio working using the original install of 9.04.  However the sata DVD drive didn't work.  So I waited until 10.04 and upgraded after which the DVD drive worked but HDMI audio didn't.  So after a couple of months worth of trying everything I could find in forums etc. I gave up and waited for 10.10.

Months later and after installing 10.10 not only does HDMI audio not work but the soundcard details shown in "gnome-volume-control" now only lists a single analogue device whereas running from a 10.10 live CD I get a comprehensive list of available devices including entries SPDIF and HDMI.

It's therefore obvious that something I've done in the huge list of things that I've changed has screwed up the audio configuration.  And despite having reams of notes I'm in no position to find out exactly what as a) I'm not an expert in Linux audio (nor do I want to be) and b) there have simply been too many changes for me to keep track of.

My question now is therefore how can I completely remove *ALL* traces of the current audio system and reinstall *EVERYTHING* related to audio using the latest versions ?

n.b. I want to completely obliterate the current audio installation (including all configuration files, kernel headers, drivers, alsa, the wretched pulse audio etc. etc.) and start from scratch.  I have already been through every sinlge HDMI related forum post and have tried everything so please don't suggest "make sure HDMI audio is unmuted in alsa-mixer" etc. as I've been there, tried that and am bored with it all.  I want to completely nuke the audio system from orbit and start again.

At this point I should say that I've already tried the following which didn't make any difference:

sudo rm /etc/asound.conf

rm ~/.*

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

sudo apt-get install linux-sound-base alsa-base alsa-utils

And to prove that the device is there here's the output from "aplay":

aplay -l

**** List of PLAYBACK Hardware Devices ****
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Or should I just give up and install Windows media centre ?  Having preformed a trial installation of Windows on a seperate disc everything "just works" with perfect HDMI audio, perfect picture, DVB card working perfectly, DVDs Playing etc. etc.

HDMI audio support on Ubuntu is a farce.

---

### Post by lidex on 2011-01-30
Can you post a little info to help figure out what needs to go?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
Also these outputs please:
```
sudo lshw -C display
grep "X Driver" /var/log/Xorg.0.log

```

---

### Post by Raptor Ramjet on 2011-01-31
Thanks for the reply.  Having run the script the output should now be at:

[http://www.alsa-project.org/db/?f=d70929bb7a20a9a26dd2b199e4306f500c725a50]("http://www.alsa-project.org/db/?f=d70929bb7a20a9a26dd2b199e4306f500c725a50")

Additionally the output of "sudo lshw -C display" was:

```

  *-display
       description: VGA compatible controller
       product: C77 [GeForce 8200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:21 memory:fd000000-fdffffff memory:f0000000-f7ffffff memory:fa000000-fbffffff ioport:ec00(size=128) memory:febe0000-febfffff

```

However when running 'grep "X Driver" /var/log/Xorg.0.log' I got no output so I've taken the liberty of attaching my entire "/var/log/Xorg.0.log" file.  The first thing I noticed was that line 1641 shows "[    22.560] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)" which doesn't look good ? 

So apologies for the length of the file but here it is:

```

[    16.317] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    17.512] X Protocol Version 11, Revision 0
[    17.512] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    17.512] Current Operating System: Linux mythic 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686
[    17.512] Kernel command line: root=UUID=557b23c1-6181-48b3-a03f-c5b7f47fcb8e ro quiet splash 
[    17.512] Build Date: 09 January 2011  12:14:58PM
[    17.512] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    17.783] Current version of pixman: 0.18.4
[    17.783] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    17.783] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.783] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 31 18:27:15 2011
[    18.080] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.113] (==) No Layout section.  Using the first Screen section.
[    18.113] (==) No screen section available. Using defaults.
[    18.113] (**) |-->Screen "Default Screen Section" (0)
[    18.113] (**) |   |-->Monitor "<default monitor>"
[    18.113] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    18.113] (==) Automatically adding devices
[    18.113] (==) Automatically enabling devices
[    18.414] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.414] 	Entry deleted from font path.
[    18.968] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    18.968] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.968] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.968] (II) Loader magic: 0x81f9b00
[    18.968] (II) Module ABI versions:
[    18.968] 	X.Org ANSI C Emulation: 0.4
[    18.968] 	X.Org Video Driver: 8.0
[    18.968] 	X.Org XInput driver : 11.0
[    18.968] 	X.Org Server Extension : 4.0
[    18.969] (--) PCI:*(0:2:0:0) 10de:0849:1043:82f2 rev 162, Mem @ 0xfd000000/16777216, 0xf0000000/134217728, 0xfa000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
[    18.969] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.969] (II) LoadModule: "extmod"
[    19.015] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.023] (II) Module extmod: vendor="X.Org Foundation"
[    19.023] 	compiled for 1.9.0, module version = 1.0.0
[    19.023] 	Module class: X.Org Server Extension
[    19.023] 	ABI class: X.Org Server Extension, version 4.0
[    19.023] (II) Loading extension MIT-SCREEN-SAVER
[    19.023] (II) Loading extension XFree86-VidModeExtension
[    19.023] (II) Loading extension XFree86-DGA
[    19.023] (II) Loading extension DPMS
[    19.023] (II) Loading extension XVideo
[    19.023] (II) Loading extension XVideo-MotionCompensation
[    19.023] (II) Loading extension X-Resource
[    19.023] (II) LoadModule: "dbe"
[    19.023] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.031] (II) Module dbe: vendor="X.Org Foundation"
[    19.031] 	compiled for 1.9.0, module version = 1.0.0
[    19.031] 	Module class: X.Org Server Extension
[    19.031] 	ABI class: X.Org Server Extension, version 4.0
[    19.031] (II) Loading extension DOUBLE-BUFFER
[    19.031] (II) LoadModule: "glx"
[    19.031] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    19.672] (II) Module glx: vendor="NVIDIA Corporation"
[    19.672] 	compiled for 4.0.2, module version = 1.0.0
[    19.672] 	Module class: X.Org Server Extension
[    19.672] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 07:01:31 PDT 2010
[    19.672] (II) Loading extension GLX
[    19.672] (II) LoadModule: "record"
[    19.673] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.678] (II) Module record: vendor="X.Org Foundation"
[    19.678] 	compiled for 1.9.0, module version = 1.13.0
[    19.678] 	Module class: X.Org Server Extension
[    19.678] 	ABI class: X.Org Server Extension, version 4.0
[    19.678] (II) Loading extension RECORD
[    19.678] (II) LoadModule: "dri"
[    19.678] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.693] (II) Module dri: vendor="X.Org Foundation"
[    19.693] 	compiled for 1.9.0, module version = 1.0.0
[    19.693] 	ABI class: X.Org Server Extension, version 4.0
[    19.693] (II) Loading extension XFree86-DRI
[    19.693] (II) LoadModule: "dri2"
[    19.693] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.694] (II) Module dri2: vendor="X.Org Foundation"
[    19.694] 	compiled for 1.9.0, module version = 1.2.0
[    19.694] 	ABI class: X.Org Server Extension, version 4.0
[    19.694] (II) Loading extension DRI2
[    19.694] (==) Matched nouveau as autoconfigured driver 0
[    19.694] (==) Matched nv as autoconfigured driver 1
[    19.694] (==) Matched vesa as autoconfigured driver 2
[    19.694] (==) Matched fbdev as autoconfigured driver 3
[    19.694] (==) Assigned the driver to the xf86ConfigLayout
[    19.694] (II) LoadModule: "nouveau"
[    20.007] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    20.021] (II) Module nouveau: vendor="X.Org Foundation"
[    20.021] 	compiled for 1.8.99.905, module version = 0.0.16
[    20.021] 	Module class: X.Org Video Driver
[    20.021] 	ABI class: X.Org Video Driver, version 8.0
[    20.028] (II) LoadModule: "nv"
[    20.028] (II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
[    20.069] (II) Module nv: vendor="X.Org Foundation"
[    20.069] 	compiled for 1.8.99.905, module version = 2.1.17
[    20.069] 	Module class: X.Org Video Driver
[    20.069] 	ABI class: X.Org Video Driver, version 8.0
[    20.069] (II) LoadModule: "vesa"
[    20.069] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.074] (II) Module vesa: vendor="X.Org Foundation"
[    20.074] 	compiled for 1.8.99.905, module version = 2.3.0
[    20.074] 	Module class: X.Org Video Driver
[    20.074] 	ABI class: X.Org Video Driver, version 8.0
[    20.074] (II) LoadModule: "fbdev"
[    20.074] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.075] (II) Module fbdev: vendor="X.Org Foundation"
[    20.075] 	compiled for 1.8.99.905, module version = 0.4.2
[    20.075] 	ABI class: X.Org Video Driver, version 8.0
[    20.075] (II) NOUVEAU driver Date:   Thu Aug 5 00:40:40 2010 +0200
[    20.075] (II) NOUVEAU driver for NVIDIA chipset families :
[    20.075] 	RIVA TNT    (NV04)
[    20.075] 	RIVA TNT2   (NV05)
[    20.075] 	GeForce 256 (NV10)
[    20.075] 	GeForce 2   (NV11, NV15)
[    20.075] 	GeForce 4MX (NV17, NV18)
[    20.075] 	GeForce 3   (NV20)
[    20.075] 	GeForce 4Ti (NV25, NV28)
[    20.075] 	GeForce FX  (NV3x)
[    20.075] 	GeForce 6   (NV4x)
[    20.075] 	GeForce 7   (G7x)
[    20.075] 	GeForce 8   (G8x)
[    20.075] (II) NOUVEAU driver Date:   Thu Aug 5 00:40:40 2010 +0200
[    20.075] (II) NOUVEAU driver for NVIDIA chipset families :
[    20.075] 	RIVA TNT    (NV04)
[    20.075] 	RIVA TNT2   (NV05)
[    20.075] 	GeForce 256 (NV10)
[    20.075] 	GeForce 2   (NV11, NV15)
[    20.075] 	GeForce 4MX (NV17, NV18)
[    20.075] 	GeForce 3   (NV20)
[    20.075] 	GeForce 4Ti (NV25, NV28)
[    20.075] 	GeForce FX  (NV3x)
[    20.075] 	GeForce 6   (NV4x)
[    20.075] 	GeForce 7   (G7x)
[    20.075] 	GeForce 8   (G8x)
[    20.075] (II) VESA: driver for VESA chipsets: vesa
[    20.075] (II) FBDEV: driver for framebuffer: fbdev
[    20.075] (++) using VT number 7

[    20.077] drmOpenDevice: node name is /dev/dri/card0
[    20.438] drmOpenByBusid: Searching for BusID pci:0000:02:00.0
[    20.438] drmOpenDevice: node name is /dev/dri/card0
[    20.442] drmOpenByBusid: drmOpenMinor returns -1
[    20.442] drmOpenDevice: node name is /dev/dri/card1
[    20.446] drmOpenByBusid: drmOpenMinor returns -1
[    20.446] drmOpenDevice: node name is /dev/dri/card2
[    20.450] drmOpenByBusid: drmOpenMinor returns -1
[    20.450] drmOpenDevice: node name is /dev/dri/card3
[    20.454] drmOpenByBusid: drmOpenMinor returns -1
[    20.454] drmOpenDevice: node name is /dev/dri/card4
[    20.458] drmOpenByBusid: drmOpenMinor returns -1
[    20.458] drmOpenDevice: node name is /dev/dri/card5
[    20.462] drmOpenByBusid: drmOpenMinor returns -1
[    20.462] drmOpenDevice: node name is /dev/dri/card6
[    20.466] drmOpenByBusid: drmOpenMinor returns -1
[    20.466] drmOpenDevice: node name is /dev/dri/card7
[    20.470] drmOpenByBusid: drmOpenMinor returns -1
[    20.470] drmOpenDevice: node name is /dev/dri/card8
[    20.474] drmOpenByBusid: drmOpenMinor returns -1
[    20.474] drmOpenDevice: node name is /dev/dri/card9
[    20.478] drmOpenByBusid: drmOpenMinor returns -1
[    20.478] drmOpenDevice: node name is /dev/dri/card10
[    20.482] drmOpenByBusid: drmOpenMinor returns -1
[    20.482] drmOpenDevice: node name is /dev/dri/card11
[    20.486] drmOpenByBusid: drmOpenMinor returns -1
[    20.486] drmOpenDevice: node name is /dev/dri/card12
[    20.490] drmOpenByBusid: drmOpenMinor returns -1
[    20.490] drmOpenDevice: node name is /dev/dri/card13
[    20.494] drmOpenByBusid: drmOpenMinor returns -1
[    20.494] drmOpenDevice: node name is /dev/dri/card14
[    20.498] drmOpenByBusid: drmOpenMinor returns -1
[    20.498] drmOpenDevice: node name is /dev/dri/card15
[    20.502] drmOpenByBusid: drmOpenMinor returns -1
[    20.502] drmOpenDevice: node name is /dev/dri/card0
[    20.508] drmOpenDevice: node name is /dev/dri/card0
[    20.513] drmOpenDevice: node name is /dev/dri/card1
[    20.517] drmOpenDevice: node name is /dev/dri/card2
[    20.521] drmOpenDevice: node name is /dev/dri/card3
[    20.525] drmOpenDevice: node name is /dev/dri/card4
[    20.529] drmOpenDevice: node name is /dev/dri/card5
[    20.533] drmOpenDevice: node name is /dev/dri/card6
[    20.537] drmOpenDevice: node name is /dev/dri/card7
[    20.541] drmOpenDevice: node name is /dev/dri/card8
[    20.544] drmOpenDevice: node name is /dev/dri/card9
[    20.548] drmOpenDevice: node name is /dev/dri/card10
[    20.552] drmOpenDevice: node name is /dev/dri/card11
[    20.556] drmOpenDevice: node name is /dev/dri/card12
[    20.560] drmOpenDevice: node name is /dev/dri/card13
[    20.564] drmOpenDevice: node name is /dev/dri/card14
[    20.568] drmOpenDevice: node name is /dev/dri/card15
[    20.572] (EE) [drm] failed to open device
[    20.572] (WW) Falling back to old probe method for fbdev
[    20.572] (II) Loading sub module "fbdevhw"
[    20.572] (II) LoadModule: "fbdevhw"
[    20.573] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.612] (II) Module fbdevhw: vendor="X.Org Foundation"
[    20.612] 	compiled for 1.9.0, module version = 0.0.2
[    20.612] 	ABI class: X.Org Video Driver, version 8.0
[    20.612] (EE) open /dev/fb0: No such file or directory
[    20.612] (II) Loading sub module "vbe"
[    20.612] (II) LoadModule: "vbe"
[    20.612] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    20.632] (II) Module vbe: vendor="X.Org Foundation"
[    20.632] 	compiled for 1.9.0, module version = 1.1.0
[    20.632] 	ABI class: X.Org Video Driver, version 8.0
[    20.632] (II) Loading sub module "int10"
[    20.632] (II) LoadModule: "int10"
[    20.632] (II) Loading /usr/lib/xorg/modules/libint10.so
[    20.671] (II) Module int10: vendor="X.Org Foundation"
[    20.671] 	compiled for 1.9.0, module version = 1.0.0
[    20.671] 	ABI class: X.Org Video Driver, version 8.0
[    20.675] (II) VESA(0): initializing int10
[    20.679] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    20.820] (II) VESA(0): VESA BIOS detected
[    20.820] (II) VESA(0): VESA VBE Version 3.0
[    20.820] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    20.820] (II) VESA(0): VESA VBE OEM: NVIDIA
[    20.820] (II) VESA(0): VESA VBE OEM Software Rev: 98.119
[    20.820] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    20.820] (II) VESA(0): VESA VBE OEM Product: MCP77 Board - mcp78so 
[    20.820] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    21.060] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    21.060] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    21.274] (==) VESA(0): RGB weight 888
[    21.274] (==) VESA(0): Default visual is TrueColor
[    21.274] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.274] (II) Loading sub module "ddc"
[    21.274] (II) LoadModule: "ddc"
[    21.274] (II) Module "ddc" already built-in
[    21.344] (II) VESA(0): VESA VBE DDC supported
[    21.344] (II) VESA(0): VESA VBE DDC Level none
[    21.344] (II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
[    21.661] (II) VESA(0): VESA VBE DDC read failed
[    21.661] (II) VESA(0): VESA VBE PanelID read failed
[    21.661] (II) VESA(0): Searching for matching VESA mode(s):
[    21.665] Mode: 100 (640x400)
[    21.665] 	ModeAttributes: 0x3bf
[    21.665] 	WinAAttributes: 0x7
[    21.665] 	WinBAttributes: 0x0
[    21.665] 	WinGranularity: 64
[    21.665] 	WinSize: 64
[    21.665] 	WinASegment: 0xa000
[    21.665] 	WinBSegment: 0x0
[    21.665] 	WinFuncPtr: 0xc0008608
[    21.665] 	BytesPerScanline: 640
[    21.665] 	XResolution: 640
[    21.665] 	YResolution: 400
[    21.665] 	XCharSize: 8
[    21.665] 	YCharSize: 16
[    21.665] 	NumberOfPlanes: 1
[    21.665] 	BitsPerPixel: 8
[    21.665] 	NumberOfBanks: 1
[    21.665] 	MemoryModel: 4
[    21.665] 	BankSize: 0
[    21.665] 	NumberOfImages: 14
[    21.665] 	RedMaskSize: 0
[    21.665] 	RedFieldPosition: 0
[    21.665] 	GreenMaskSize: 0
[    21.665] 	GreenFieldPosition: 0
[    21.665] 	BlueMaskSize: 0
[    21.665] 	BlueFieldPosition: 0
[    21.665] 	RsvdMaskSize: 0
[    21.665] 	RsvdFieldPosition: 0
[    21.665] 	DirectColorModeInfo: 0
[    21.665] 	PhysBasePtr: 0xfb000000
[    21.665] 	LinBytesPerScanLine: 640
[    21.665] 	BnkNumberOfImagePages: 14
[    21.665] 	LinNumberOfImagePages: 14
[    21.665] 	LinRedMaskSize: 0
[    21.665] 	LinRedFieldPosition: 0
[    21.665] 	LinGreenMaskSize: 0
[    21.665] 	LinGreenFieldPosition: 0
[    21.665] 	LinBlueMaskSize: 0
[    21.665] 	LinBlueFieldPosition: 0
[    21.665] 	LinRsvdMaskSize: 0
[    21.665] 	LinRsvdFieldPosition: 0
[    21.665] 	MaxPixelClock: 229500000
[    21.668] Mode: 101 (640x480)
[    21.668] 	ModeAttributes: 0x3bf
[    21.668] 	WinAAttributes: 0x7
[    21.668] 	WinBAttributes: 0x0
[    21.668] 	WinGranularity: 64
[    21.668] 	WinSize: 64
[    21.668] 	WinASegment: 0xa000
[    21.668] 	WinBSegment: 0x0
[    21.668] 	WinFuncPtr: 0xc0008608
[    21.669] 	BytesPerScanline: 640
[    21.669] 	XResolution: 640
[    21.669] 	YResolution: 480
[    21.669] 	XCharSize: 8
[    21.669] 	YCharSize: 16
[    21.669] 	NumberOfPlanes: 1
[    21.669] 	BitsPerPixel: 8
[    21.669] 	NumberOfBanks: 1
[    21.669] 	MemoryModel: 4
[    21.669] 	BankSize: 0
[    21.669] 	NumberOfImages: 10
[    21.669] 	RedMaskSize: 0
[    21.669] 	RedFieldPosition: 0
[    21.669] 	GreenMaskSize: 0
[    21.669] 	GreenFieldPosition: 0
[    21.669] 	BlueMaskSize: 0
[    21.669] 	BlueFieldPosition: 0
[    21.669] 	RsvdMaskSize: 0
[    21.669] 	RsvdFieldPosition: 0
[    21.669] 	DirectColorModeInfo: 0
[    21.669] 	PhysBasePtr: 0xfb000000
[    21.669] 	LinBytesPerScanLine: 640
[    21.669] 	BnkNumberOfImagePages: 10
[    21.669] 	LinNumberOfImagePages: 10
[    21.669] 	LinRedMaskSize: 0
[    21.669] 	LinRedFieldPosition: 0
[    21.669] 	LinGreenMaskSize: 0
[    21.669] 	LinGreenFieldPosition: 0
[    21.669] 	LinBlueMaskSize: 0
[    21.669] 	LinBlueFieldPosition: 0
[    21.669] 	LinRsvdMaskSize: 0
[    21.669] 	LinRsvdFieldPosition: 0
[    21.669] 	MaxPixelClock: 229500000
[    21.672] Mode: 102 (800x600)
[    21.672] 	ModeAttributes: 0x33f
[    21.672] 	WinAAttributes: 0x7
[    21.672] 	WinBAttributes: 0x0
[    21.672] 	WinGranularity: 64
[    21.672] 	WinSize: 64
[    21.672] 	WinASegment: 0xa000
[    21.672] 	WinBSegment: 0x0
[    21.672] 	WinFuncPtr: 0xc0008608
[    21.672] 	BytesPerScanline: 100
[    21.695] 	XResolution: 800
[    21.695] 	YResolution: 600
[    21.695] 	XCharSize: 8
[    21.695] 	YCharSize: 16
[    21.695] 	NumberOfPlanes: 4
[    21.695] 	BitsPerPixel: 4
[    21.695] 	NumberOfBanks: 1
[    21.695] 	MemoryModel: 3
[    21.695] 	BankSize: 0
[    21.695] 	NumberOfImages: 2
[    21.695] 	RedMaskSize: 0
[    21.695] 	RedFieldPosition: 0
[    21.695] 	GreenMaskSize: 0
[    21.695] 	GreenFieldPosition: 0
[    21.695] 	BlueMaskSize: 0
[    21.695] 	BlueFieldPosition: 0
[    21.695] 	RsvdMaskSize: 0
[    21.696] 	RsvdFieldPosition: 0
[    21.696] 	DirectColorModeInfo: 0
[    21.696] 	PhysBasePtr: 0x0
[    21.696] 	LinBytesPerScanLine: 100
[    21.696] 	BnkNumberOfImagePages: 2
[    21.696] 	LinNumberOfImagePages: 2
[    21.696] 	LinRedMaskSize: 0
[    21.696] 	LinRedFieldPosition: 0
[    21.696] 	LinGreenMaskSize: 0
[    21.696] 	LinGreenFieldPosition: 0
[    21.696] 	LinBlueMaskSize: 0
[    21.696] 	LinBlueFieldPosition: 0
[    21.696] 	LinRsvdMaskSize: 0
[    21.696] 	LinRsvdFieldPosition: 0
[    21.696] 	MaxPixelClock: 108500000
[    21.699] Mode: 103 (800x600)
[    21.699] 	ModeAttributes: 0x3bf
[    21.699] 	WinAAttributes: 0x7
[    21.699] 	WinBAttributes: 0x0
[    21.699] 	WinGranularity: 64
[    21.699] 	WinSize: 64
[    21.699] 	WinASegment: 0xa000
[    21.699] 	WinBSegment: 0x0
[    21.699] 	WinFuncPtr: 0xc0008608
[    21.699] 	BytesPerScanline: 800
[    21.699] 	XResolution: 800
[    21.699] 	YResolution: 600
[    21.699] 	XCharSize: 8
[    21.699] 	YCharSize: 16
[    21.699] 	NumberOfPlanes: 1
[    21.699] 	BitsPerPixel: 8
[    21.699] 	NumberOfBanks: 1
[    21.699] 	MemoryModel: 4
[    21.699] 	BankSize: 0
[    21.699] 	NumberOfImages: 6
[    21.699] 	RedMaskSize: 0
[    21.699] 	RedFieldPosition: 0
[    21.699] 	GreenMaskSize: 0
[    21.699] 	GreenFieldPosition: 0
[    21.699] 	BlueMaskSize: 0
[    21.699] 	BlueFieldPosition: 0
[    21.699] 	RsvdMaskSize: 0
[    21.699] 	RsvdFieldPosition: 0
[    21.699] 	DirectColorModeInfo: 0
[    21.699] 	PhysBasePtr: 0xfb000000
[    21.699] 	LinBytesPerScanLine: 800
[    21.699] 	BnkNumberOfImagePages: 6
[    21.699] 	LinNumberOfImagePages: 6
[    21.699] 	LinRedMaskSize: 0
[    21.699] 	LinRedFieldPosition: 0
[    21.699] 	LinGreenMaskSize: 0
[    21.699] 	LinGreenFieldPosition: 0
[    21.699] 	LinBlueMaskSize: 0
[    21.699] 	LinBlueFieldPosition: 0
[    21.699] 	LinRsvdMaskSize: 0
[    21.699] 	LinRsvdFieldPosition: 0
[    21.699] 	MaxPixelClock: 229500000
[    21.703] Mode: 104 (1024x768)
[    21.703] 	ModeAttributes: 0x33f
[    21.703] 	WinAAttributes: 0x7
[    21.703] 	WinBAttributes: 0x0
[    21.703] 	WinGranularity: 64
[    21.703] 	WinSize: 64
[    21.703] 	WinASegment: 0xa000
[    21.703] 	WinBSegment: 0x0
[    21.703] 	WinFuncPtr: 0xc0008608
[    21.703] 	BytesPerScanline: 128
[    21.703] 	XResolution: 1024
[    21.703] 	YResolution: 768
[    21.703] 	XCharSize: 8
[    21.703] 	YCharSize: 16
[    21.703] 	NumberOfPlanes: 4
[    21.703] 	BitsPerPixel: 4
[    21.703] 	NumberOfBanks: 1
[    21.703] 	MemoryModel: 3
[    21.703] 	BankSize: 0
[    21.703] 	NumberOfImages: 1
[    21.703] 	RedMaskSize: 0
[    21.703] 	RedFieldPosition: 0
[    21.703] 	GreenMaskSize: 0
[    21.703] 	GreenFieldPosition: 0
[    21.703] 	BlueMaskSize: 0
[    21.703] 	BlueFieldPosition: 0
[    21.703] 	RsvdMaskSize: 0
[    21.703] 	RsvdFieldPosition: 0
[    21.703] 	DirectColorModeInfo: 0
[    21.703] 	PhysBasePtr: 0x0
[    21.703] 	LinBytesPerScanLine: 128
[    21.703] 	BnkNumberOfImagePages: 1
[    21.703] 	LinNumberOfImagePages: 1
[    21.703] 	LinRedMaskSize: 0
[    21.703] 	LinRedFieldPosition: 0
[    21.703] 	LinGreenMaskSize: 0
[    21.703] 	LinGreenFieldPosition: 0
[    21.703] 	LinBlueMaskSize: 0
[    21.703] 	LinBlueFieldPosition: 0
[    21.703] 	LinRsvdMaskSize: 0
[    21.703] 	LinRsvdFieldPosition: 0
[    21.703] 	MaxPixelClock: 108500000
[    21.706] Mode: 105 (1024x768)
[    21.706] 	ModeAttributes: 0x3bf
[    21.706] 	WinAAttributes: 0x7
[    21.706] 	WinBAttributes: 0x0
[    21.706] 	WinGranularity: 64
[    21.706] 	WinSize: 64
[    21.706] 	WinASegment: 0xa000
[    21.706] 	WinBSegment: 0x0
[    21.706] 	WinFuncPtr: 0xc0008608
[    21.706] 	BytesPerScanline: 1024
[    21.706] 	XResolution: 1024
[    21.706] 	YResolution: 768
[    21.706] 	XCharSize: 8
[    21.706] 	YCharSize: 16
[    21.706] 	NumberOfPlanes: 1
[    21.706] 	BitsPerPixel: 8
[    21.706] 	NumberOfBanks: 1
[    21.706] 	MemoryModel: 4
[    21.706] 	BankSize: 0
[    21.706] 	NumberOfImages: 3
[    21.706] 	RedMaskSize: 0
[    21.706] 	RedFieldPosition: 0
[    21.706] 	GreenMaskSize: 0
[    21.706] 	GreenFieldPosition: 0
[    21.706] 	BlueMaskSize: 0
[    21.706] 	BlueFieldPosition: 0
[    21.706] 	RsvdMaskSize: 0
[    21.706] 	RsvdFieldPosition: 0
[    21.707] 	DirectColorModeInfo: 0
[    21.707] 	PhysBasePtr: 0xfb000000
[    21.707] 	LinBytesPerScanLine: 1024
[    21.707] 	BnkNumberOfImagePages: 3
[    21.707] 	LinNumberOfImagePages: 3
[    21.707] 	LinRedMaskSize: 0
[    21.707] 	LinRedFieldPosition: 0
[    21.707] 	LinGreenMaskSize: 0
[    21.707] 	LinGreenFieldPosition: 0
[    21.707] 	LinBlueMaskSize: 0
[    21.707] 	LinBlueFieldPosition: 0
[    21.707] 	LinRsvdMaskSize: 0
[    21.707] 	LinRsvdFieldPosition: 0
[    21.707] 	MaxPixelClock: 229500000
[    21.710] Mode: 106 (1280x1024)
[    21.710] 	ModeAttributes: 0x33f
[    21.710] 	WinAAttributes: 0x7
[    21.710] 	WinBAttributes: 0x0
[    21.710] 	WinGranularity: 64
[    21.710] 	WinSize: 64
[    21.710] 	WinASegment: 0xa000
[    21.710] 	WinBSegment: 0x0
[    21.710] 	WinFuncPtr: 0xc0008608
[    21.710] 	BytesPerScanline: 160
[    21.710] 	XResolution: 1280
[    21.710] 	YResolution: 1024
[    21.710] 	XCharSize: 8
[    21.710] 	YCharSize: 16
[    21.710] 	NumberOfPlanes: 4
[    21.710] 	BitsPerPixel: 4
[    21.710] 	NumberOfBanks: 1
[    21.710] 	MemoryModel: 3
[    21.710] 	BankSize: 0
[    21.710] 	NumberOfImages: 1
[    21.710] 	RedMaskSize: 0
[    21.710] 	RedFieldPosition: 0
[    21.710] 	GreenMaskSize: 0
[    21.710] 	GreenFieldPosition: 0
[    21.710] 	BlueMaskSize: 0
[    21.710] 	BlueFieldPosition: 0
[    21.710] 	RsvdMaskSize: 0
[    21.710] 	RsvdFieldPosition: 0
[    21.710] 	DirectColorModeInfo: 0
[    21.710] 	PhysBasePtr: 0x0
[    21.710] 	LinBytesPerScanLine: 160
[    21.710] 	BnkNumberOfImagePages: 1
[    21.710] 	LinNumberOfImagePages: 1
[    21.710] 	LinRedMaskSize: 0
[    21.710] 	LinRedFieldPosition: 0
[    21.710] 	LinGreenMaskSize: 0
[    21.710] 	LinGreenFieldPosition: 0
[    21.710] 	LinBlueMaskSize: 0
[    21.710] 	LinBlueFieldPosition: 0
[    21.710] 	LinRsvdMaskSize: 0
[    21.710] 	LinRsvdFieldPosition: 0
[    21.710] 	MaxPixelClock: 108500000
[    21.714] Mode: 107 (1280x1024)
[    21.714] 	ModeAttributes: 0x3bf
[    21.714] 	WinAAttributes: 0x7
[    21.714] 	WinBAttributes: 0x0
[    21.714] 	WinGranularity: 64
[    21.714] 	WinSize: 64
[    21.714] 	WinASegment: 0xa000
[    21.714] 	WinBSegment: 0x0
[    21.714] 	WinFuncPtr: 0xc0008608
[    21.714] 	BytesPerScanline: 1280
[    21.714] 	XResolution: 1280
[    21.714] 	YResolution: 1024
[    21.714] 	XCharSize: 8
[    21.714] 	YCharSize: 16
[    21.714] 	NumberOfPlanes: 1
[    21.714] 	BitsPerPixel: 8
[    21.714] 	NumberOfBanks: 1
[    21.714] 	MemoryModel: 4
[    21.714] 	BankSize: 0
[    21.714] 	NumberOfImages: 1
[    21.714] 	RedMaskSize: 0
[    21.714] 	RedFieldPosition: 0
[    21.714] 	GreenMaskSize: 0
[    21.714] 	GreenFieldPosition: 0
[    21.714] 	BlueMaskSize: 0
[    21.714] 	BlueFieldPosition: 0
[    21.714] 	RsvdMaskSize: 0
[    21.714] 	RsvdFieldPosition: 0
[    21.714] 	DirectColorModeInfo: 0
[    21.714] 	PhysBasePtr: 0xfb000000
[    21.714] 	LinBytesPerScanLine: 1280
[    21.714] 	BnkNumberOfImagePages: 1
[    21.714] 	LinNumberOfImagePages: 1
[    21.714] 	LinRedMaskSize: 0
[    21.714] 	LinRedFieldPosition: 0
[    21.714] 	LinGreenMaskSize: 0
[    21.714] 	LinGreenFieldPosition: 0
[    21.714] 	LinBlueMaskSize: 0
[    21.714] 	LinBlueFieldPosition: 0
[    21.714] 	LinRsvdMaskSize: 0
[    21.714] 	LinRsvdFieldPosition: 0
[    21.714] 	MaxPixelClock: 229500000
[    21.717] Mode: 10e (320x200)
[    21.717] 	ModeAttributes: 0x3bf
[    21.717] 	WinAAttributes: 0x7
[    21.717] 	WinBAttributes: 0x0
[    21.717] 	WinGranularity: 64
[    21.717] 	WinSize: 64
[    21.717] 	WinASegment: 0xa000
[    21.717] 	WinBSegment: 0x0
[    21.717] 	WinFuncPtr: 0xc0008608
[    21.718] 	BytesPerScanline: 640
[    21.718] 	XResolution: 320
[    21.718] 	YResolution: 200
[    21.718] 	XCharSize: 8
[    21.718] 	YCharSize: 8
[    21.718] 	NumberOfPlanes: 1
[    21.718] 	BitsPerPixel: 16
[    21.718] 	NumberOfBanks: 1
[    21.718] 	MemoryModel: 6
[    21.718] 	BankSize: 0
[    21.718] 	NumberOfImages: 30
[    21.718] 	RedMaskSize: 5
[    21.718] 	RedFieldPosition: 11
[    21.718] 	GreenMaskSize: 6
[    21.718] 	GreenFieldPosition: 5
[    21.718] 	BlueMaskSize: 5
[    21.718] 	BlueFieldPosition: 0
[    21.718] 	RsvdMaskSize: 0
[    21.718] 	RsvdFieldPosition: 0
[    21.718] 	DirectColorModeInfo: 0
[    21.718] 	PhysBasePtr: 0xfb000000
[    21.718] 	LinBytesPerScanLine: 640
[    21.718] 	BnkNumberOfImagePages: 30
[    21.718] 	LinNumberOfImagePages: 30
[    21.718] 	LinRedMaskSize: 5
[    21.718] 	LinRedFieldPosition: 11
[    21.718] 	LinGreenMaskSize: 6
[    21.718] 	LinGreenFieldPosition: 5
[    21.718] 	LinBlueMaskSize: 5
[    21.718] 	LinBlueFieldPosition: 0
[    21.718] 	LinRsvdMaskSize: 0
[    21.718] 	LinRsvdFieldPosition: 0
[    21.718] 	MaxPixelClock: 229500000
[    21.721] *Mode: 10f (320x200)
[    21.721] 	ModeAttributes: 0x3bf
[    21.721] 	WinAAttributes: 0x7
[    21.721] 	WinBAttributes: 0x0
[    21.721] 	WinGranularity: 64
[    21.721] 	WinSize: 64
[    21.721] 	WinASegment: 0xa000
[    21.721] 	WinBSegment: 0x0
[    21.721] 	WinFuncPtr: 0xc0008608
[    21.721] 	BytesPerScanline: 1280
[    21.721] 	XResolution: 320
[    21.721] 	YResolution: 200
[    21.721] 	XCharSize: 8
[    21.721] 	YCharSize: 8
[    21.721] 	NumberOfPlanes: 1
[    21.721] 	BitsPerPixel: 32
[    21.721] 	NumberOfBanks: 1
[    21.721] 	MemoryModel: 6
[    21.721] 	BankSize: 0
[    21.721] 	NumberOfImages: 14
[    21.721] 	RedMaskSize: 8
[    21.721] 	RedFieldPosition: 16
[    21.721] 	GreenMaskSize: 8
[    21.721] 	GreenFieldPosition: 8
[    21.721] 	BlueMaskSize: 8
[    21.721] 	BlueFieldPosition: 0
[    21.721] 	RsvdMaskSize: 8
[    21.721] 	RsvdFieldPosition: 24
[    21.721] 	DirectColorModeInfo: 0
[    21.721] 	PhysBasePtr: 0xfb000000
[    21.721] 	LinBytesPerScanLine: 1280
[    21.721] 	BnkNumberOfImagePages: 14
[    21.721] 	LinNumberOfImagePages: 14
[    21.721] 	LinRedMaskSize: 8
[    21.721] 	LinRedFieldPosition: 16
[    21.721] 	LinGreenMaskSize: 8
[    21.721] 	LinGreenFieldPosition: 8
[    21.721] 	LinBlueMaskSize: 8
[    21.721] 	LinBlueFieldPosition: 0
[    21.721] 	LinRsvdMaskSize: 8
[    21.721] 	LinRsvdFieldPosition: 24
[    21.721] 	MaxPixelClock: 229500000
[    21.725] Mode: 111 (640x480)
[    21.725] 	ModeAttributes: 0x3bf
[    21.725] 	WinAAttributes: 0x7
[    21.725] 	WinBAttributes: 0x0
[    21.725] 	WinGranularity: 64
[    21.725] 	WinSize: 64
[    21.725] 	WinASegment: 0xa000
[    21.725] 	WinBSegment: 0x0
[    21.725] 	WinFuncPtr: 0xc0008608
[    21.725] 	BytesPerScanline: 1280
[    21.725] 	XResolution: 640
[    21.725] 	YResolution: 480
[    21.725] 	XCharSize: 8
[    21.725] 	YCharSize: 16
[    21.725] 	NumberOfPlanes: 1
[    21.725] 	BitsPerPixel: 16
[    21.725] 	NumberOfBanks: 1
[    21.725] 	MemoryModel: 6
[    21.725] 	BankSize: 0
[    21.725] 	NumberOfImages: 4
[    21.725] 	RedMaskSize: 5
[    21.725] 	RedFieldPosition: 11
[    21.725] 	GreenMaskSize: 6
[    21.725] 	GreenFieldPosition: 5
[    21.725] 	BlueMaskSize: 5
[    21.725] 	BlueFieldPosition: 0
[    21.725] 	RsvdMaskSize: 0
[    21.725] 	RsvdFieldPosition: 0
[    21.725] 	DirectColorModeInfo: 0
[    21.725] 	PhysBasePtr: 0xfb000000
[    21.725] 	LinBytesPerScanLine: 1280
[    21.725] 	BnkNumberOfImagePages: 4
[    21.725] 	LinNumberOfImagePages: 4
[    21.725] 	LinRedMaskSize: 5
[    21.725] 	LinRedFieldPosition: 11
[    21.725] 	LinGreenMaskSize: 6
[    21.725] 	LinGreenFieldPosition: 5
[    21.725] 	LinBlueMaskSize: 5
[    21.725] 	LinBlueFieldPosition: 0
[    21.725] 	LinRsvdMaskSize: 0
[    21.725] 	LinRsvdFieldPosition: 0
[    21.725] 	MaxPixelClock: 229500000
[    21.728] *Mode: 112 (640x480)
[    21.728] 	ModeAttributes: 0x3bf
[    21.728] 	WinAAttributes: 0x7
[    21.728] 	WinBAttributes: 0x0
[    21.728] 	WinGranularity: 64
[    21.728] 	WinSize: 64
[    21.728] 	WinASegment: 0xa000
[    21.728] 	WinBSegment: 0x0
[    21.728] 	WinFuncPtr: 0xc0008608
[    21.728] 	BytesPerScanline: 2560
[    21.728] 	XResolution: 640
[    21.728] 	YResolution: 480
[    21.728] 	XCharSize: 8
[    21.728] 	YCharSize: 16
[    21.728] 	NumberOfPlanes: 1
[    21.728] 	BitsPerPixel: 32
[    21.728] 	NumberOfBanks: 1
[    21.728] 	MemoryModel: 6
[    21.728] 	BankSize: 0
[    21.728] 	NumberOfImages: 1
[    21.728] 	RedMaskSize: 8
[    21.728] 	RedFieldPosition: 16
[    21.728] 	GreenMaskSize: 8
[    21.728] 	GreenFieldPosition: 8
[    21.728] 	BlueMaskSize: 8
[    21.728] 	BlueFieldPosition: 0
[    21.728] 	RsvdMaskSize: 8
[    21.728] 	RsvdFieldPosition: 24
[    21.728] 	DirectColorModeInfo: 0
[    21.728] 	PhysBasePtr: 0xfb000000
[    21.728] 	LinBytesPerScanLine: 2560
[    21.728] 	BnkNumberOfImagePages: 1
[    21.728] 	LinNumberOfImagePages: 1
[    21.728] 	LinRedMaskSize: 8
[    21.728] 	LinRedFieldPosition: 16
[    21.728] 	LinGreenMaskSize: 8
[    21.728] 	LinGreenFieldPosition: 8
[    21.728] 	LinBlueMaskSize: 8
[    21.728] 	LinBlueFieldPosition: 0
[    21.728] 	LinRsvdMaskSize: 8
[    21.728] 	LinRsvdFieldPosition: 24
[    21.728] 	MaxPixelClock: 229500000
[    21.732] Mode: 114 (800x600)
[    21.732] 	ModeAttributes: 0x3bf
[    21.732] 	WinAAttributes: 0x7
[    21.732] 	WinBAttributes: 0x0
[    21.732] 	WinGranularity: 64
[    21.732] 	WinSize: 64
[    21.732] 	WinASegment: 0xa000
[    21.732] 	WinBSegment: 0x0
[    21.732] 	WinFuncPtr: 0xc0008608
[    21.732] 	BytesPerScanline: 1600
[    21.732] 	XResolution: 800
[    21.732] 	YResolution: 600
[    21.732] 	XCharSize: 8
[    21.732] 	YCharSize: 16
[    21.732] 	NumberOfPlanes: 1
[    21.732] 	BitsPerPixel: 16
[    21.732] 	NumberOfBanks: 1
[    21.732] 	MemoryModel: 6
[    21.732] 	BankSize: 0
[    21.732] 	NumberOfImages: 2
[    21.732] 	RedMaskSize: 5
[    21.732] 	RedFieldPosition: 11
[    21.732] 	GreenMaskSize: 6
[    21.732] 	GreenFieldPosition: 5
[    21.732] 	BlueMaskSize: 5
[    21.732] 	BlueFieldPosition: 0
[    21.732] 	RsvdMaskSize: 0
[    21.732] 	RsvdFieldPosition: 0
[    21.732] 	DirectColorModeInfo: 0
[    21.732] 	PhysBasePtr: 0xfb000000
[    21.732] 	LinBytesPerScanLine: 1600
[    21.732] 	BnkNumberOfImagePages: 2
[    21.732] 	LinNumberOfImagePages: 2
[    21.732] 	LinRedMaskSize: 5
[    21.732] 	LinRedFieldPosition: 11
[    21.732] 	LinGreenMaskSize: 6
[    21.732] 	LinGreenFieldPosition: 5
[    21.732] 	LinBlueMaskSize: 5
[    21.732] 	LinBlueFieldPosition: 0
[    21.732] 	LinRsvdMaskSize: 0
[    21.732] 	LinRsvdFieldPosition: 0
[    21.732] 	MaxPixelClock: 229500000
[    21.735] *Mode: 115 (800x600)
[    21.735] 	ModeAttributes: 0x3bf
[    21.735] 	WinAAttributes: 0x7
[    21.735] 	WinBAttributes: 0x0
[    21.735] 	WinGranularity: 64
[    21.735] 	WinSize: 64
[    21.735] 	WinASegment: 0xa000
[    21.735] 	WinBSegment: 0x0
[    21.735] 	WinFuncPtr: 0xc0008608
[    21.735] 	BytesPerScanline: 3200
[    21.735] 	XResolution: 800
[    21.735] 	YResolution: 600
[    21.735] 	XCharSize: 8
[    21.735] 	YCharSize: 16
[    21.735] 	NumberOfPlanes: 1
[    21.735] 	BitsPerPixel: 32
[    21.735] 	NumberOfBanks: 1
[    21.735] 	MemoryModel: 6
[    21.735] 	BankSize: 0
[    21.735] 	NumberOfImages: 1
[    21.735] 	RedMaskSize: 8
[    21.735] 	RedFieldPosition: 16
[    21.735] 	GreenMaskSize: 8
[    21.735] 	GreenFieldPosition: 8
[    21.735] 	BlueMaskSize: 8
[    21.735] 	BlueFieldPosition: 0
[    21.735] 	RsvdMaskSize: 8
[    21.735] 	RsvdFieldPosition: 24
[    21.735] 	DirectColorModeInfo: 0
[    21.735] 	PhysBasePtr: 0xfb000000
[    21.735] 	LinBytesPerScanLine: 3200
[    21.735] 	BnkNumberOfImagePages: 1
[    21.735] 	LinNumberOfImagePages: 1
[    21.735] 	LinRedMaskSize: 8
[    21.735] 	LinRedFieldPosition: 16
[    21.735] 	LinGreenMaskSize: 8
[    21.735] 	LinGreenFieldPosition: 8
[    21.735] 	LinBlueMaskSize: 8
[    21.735] 	LinBlueFieldPosition: 0
[    21.735] 	LinRsvdMaskSize: 8
[    21.735] 	LinRsvdFieldPosition: 24
[    21.735] 	MaxPixelClock: 229500000
[    21.739] Mode: 117 (1024x768)
[    21.739] 	ModeAttributes: 0x3bf
[    21.739] 	WinAAttributes: 0x7
[    21.739] 	WinBAttributes: 0x0
[    21.739] 	WinGranularity: 64
[    21.739] 	WinSize: 64
[    21.739] 	WinASegment: 0xa000
[    21.739] 	WinBSegment: 0x0
[    21.739] 	WinFuncPtr: 0xc0008608
[    21.739] 	BytesPerScanline: 2048
[    21.739] 	XResolution: 1024
[    21.739] 	YResolution: 768
[    21.739] 	XCharSize: 8
[    21.739] 	YCharSize: 16
[    21.739] 	NumberOfPlanes: 1
[    21.739] 	BitsPerPixel: 16
[    21.739] 	NumberOfBanks: 1
[    21.739] 	MemoryModel: 6
[    21.739] 	BankSize: 0
[    21.739] 	NumberOfImages: 1
[    21.739] 	RedMaskSize: 5
[    21.739] 	RedFieldPosition: 11
[    21.739] 	GreenMaskSize: 6
[    21.739] 	GreenFieldPosition: 5
[    21.739] 	BlueMaskSize: 5
[    21.739] 	BlueFieldPosition: 0
[    21.739] 	RsvdMaskSize: 0
[    21.739] 	RsvdFieldPosition: 0
[    21.739] 	DirectColorModeInfo: 0
[    21.739] 	PhysBasePtr: 0xfb000000
[    21.739] 	LinBytesPerScanLine: 2048
[    21.739] 	BnkNumberOfImagePages: 1
[    21.739] 	LinNumberOfImagePages: 1
[    21.739] 	LinRedMaskSize: 5
[    21.739] 	LinRedFieldPosition: 11
[    21.739] 	LinGreenMaskSize: 6
[    21.739] 	LinGreenFieldPosition: 5
[    21.739] 	LinBlueMaskSize: 5
[    21.739] 	LinBlueFieldPosition: 0
[    21.739] 	LinRsvdMaskSize: 0
[    21.739] 	LinRsvdFieldPosition: 0
[    21.739] 	MaxPixelClock: 229500000
[    21.742] *Mode: 118 (1024x768)
[    21.742] 	ModeAttributes: 0x3bf
[    21.742] 	WinAAttributes: 0x7
[    21.742] 	WinBAttributes: 0x0
[    21.742] 	WinGranularity: 64
[    21.742] 	WinSize: 64
[    21.742] 	WinASegment: 0xa000
[    21.742] 	WinBSegment: 0x0
[    21.742] 	WinFuncPtr: 0xc0008608
[    21.742] 	BytesPerScanline: 4096
[    21.742] 	XResolution: 1024
[    21.742] 	YResolution: 768
[    21.742] 	XCharSize: 8
[    21.742] 	YCharSize: 16
[    21.742] 	NumberOfPlanes: 1
[    21.742] 	BitsPerPixel: 32
[    21.742] 	NumberOfBanks: 1
[    21.742] 	MemoryModel: 6
[    21.742] 	BankSize: 0
[    21.742] 	NumberOfImages: 1
[    21.742] 	RedMaskSize: 8
[    21.742] 	RedFieldPosition: 16
[    21.742] 	GreenMaskSize: 8
[    21.742] 	GreenFieldPosition: 8
[    21.742] 	BlueMaskSize: 8
[    21.742] 	BlueFieldPosition: 0
[    21.742] 	RsvdMaskSize: 8
[    21.742] 	RsvdFieldPosition: 24
[    21.743] 	DirectColorModeInfo: 0
[    21.743] 	PhysBasePtr: 0xfb000000
[    21.743] 	LinBytesPerScanLine: 4096
[    21.743] 	BnkNumberOfImagePages: 1
[    21.743] 	LinNumberOfImagePages: 1
[    21.743] 	LinRedMaskSize: 8
[    21.743] 	LinRedFieldPosition: 16
[    21.743] 	LinGreenMaskSize: 8
[    21.743] 	LinGreenFieldPosition: 8
[    21.743] 	LinBlueMaskSize: 8
[    21.743] 	LinBlueFieldPosition: 0
[    21.743] 	LinRsvdMaskSize: 8
[    21.743] 	LinRsvdFieldPosition: 24
[    21.743] 	MaxPixelClock: 229500000
[    21.746] Mode: 11a (1280x1024)
[    21.746] 	ModeAttributes: 0x3bf
[    21.746] 	WinAAttributes: 0x7
[    21.746] 	WinBAttributes: 0x0
[    21.746] 	WinGranularity: 64
[    21.746] 	WinSize: 64
[    21.746] 	WinASegment: 0xa000
[    21.746] 	WinBSegment: 0x0
[    21.746] 	WinFuncPtr: 0xc0008608
[    21.746] 	BytesPerScanline: 2560
[    21.746] 	XResolution: 1280
[    21.746] 	YResolution: 1024
[    21.746] 	XCharSize: 8
[    21.746] 	YCharSize: 16
[    21.746] 	NumberOfPlanes: 1
[    21.746] 	BitsPerPixel: 16
[    21.746] 	NumberOfBanks: 1
[    21.746] 	MemoryModel: 6
[    21.746] 	BankSize: 0
[    21.746] 	NumberOfImages: 1
[    21.746] 	RedMaskSize: 5
[    21.746] 	RedFieldPosition: 11
[    21.746] 	GreenMaskSize: 6
[    21.746] 	GreenFieldPosition: 5
[    21.746] 	BlueMaskSize: 5
[    21.746] 	BlueFieldPosition: 0
[    21.746] 	RsvdMaskSize: 0
[    21.746] 	RsvdFieldPosition: 0
[    21.746] 	DirectColorModeInfo: 0
[    21.746] 	PhysBasePtr: 0xfb000000
[    21.746] 	LinBytesPerScanLine: 2560
[    21.746] 	BnkNumberOfImagePages: 1
[    21.746] 	LinNumberOfImagePages: 1
[    21.746] 	LinRedMaskSize: 5
[    21.746] 	LinRedFieldPosition: 11
[    21.746] 	LinGreenMaskSize: 6
[    21.746] 	LinGreenFieldPosition: 5
[    21.746] 	LinBlueMaskSize: 5
[    21.746] 	LinBlueFieldPosition: 0
[    21.746] 	LinRsvdMaskSize: 0
[    21.746] 	LinRsvdFieldPosition: 0
[    21.746] 	MaxPixelClock: 229500000
[    21.750] *Mode: 11b (1280x1024)
[    21.750] 	ModeAttributes: 0x3bf
[    21.750] 	WinAAttributes: 0x7
[    21.750] 	WinBAttributes: 0x0
[    21.750] 	WinGranularity: 64
[    21.750] 	WinSize: 64
[    21.750] 	WinASegment: 0xa000
[    21.750] 	WinBSegment: 0x0
[    21.750] 	WinFuncPtr: 0xc0008608
[    21.750] 	BytesPerScanline: 5120
[    21.750] 	XResolution: 1280
[    21.750] 	YResolution: 1024
[    21.750] 	XCharSize: 8
[    21.750] 	YCharSize: 16
[    21.750] 	NumberOfPlanes: 1
[    21.750] 	BitsPerPixel: 32
[    21.750] 	NumberOfBanks: 1
[    21.750] 	MemoryModel: 6
[    21.750] 	BankSize: 0
[    21.750] 	NumberOfImages: 1
[    21.750] 	RedMaskSize: 8
[    21.750] 	RedFieldPosition: 16
[    21.750] 	GreenMaskSize: 8
[    21.750] 	GreenFieldPosition: 8
[    21.750] 	BlueMaskSize: 8
[    21.750] 	BlueFieldPosition: 0
[    21.750] 	RsvdMaskSize: 8
[    21.750] 	RsvdFieldPosition: 24
[    21.750] 	DirectColorModeInfo: 0
[    21.750] 	PhysBasePtr: 0xfb000000
[    21.750] 	LinBytesPerScanLine: 5120
[    21.750] 	BnkNumberOfImagePages: 1
[    21.750] 	LinNumberOfImagePages: 1
[    21.750] 	LinRedMaskSize: 8
[    21.750] 	LinRedFieldPosition: 16
[    21.750] 	LinGreenMaskSize: 8
[    21.750] 	LinGreenFieldPosition: 8
[    21.750] 	LinBlueMaskSize: 8
[    21.750] 	LinBlueFieldPosition: 0
[    21.750] 	LinRsvdMaskSize: 8
[    21.750] 	LinRsvdFieldPosition: 24
[    21.750] 	MaxPixelClock: 229500000
[    21.753] Mode: 130 (320x200)
[    21.753] 	ModeAttributes: 0x3bf
[    21.753] 	WinAAttributes: 0x7
[    21.753] 	WinBAttributes: 0x0
[    21.753] 	WinGranularity: 64
[    21.753] 	WinSize: 64
[    21.753] 	WinASegment: 0xa000
[    21.753] 	WinBSegment: 0x0
[    21.753] 	WinFuncPtr: 0xc0008608
[    21.753] 	BytesPerScanline: 320
[    21.753] 	XResolution: 320
[    21.753] 	YResolution: 200
[    21.753] 	XCharSize: 8
[    21.753] 	YCharSize: 8
[    21.753] 	NumberOfPlanes: 1
[    21.753] 	BitsPerPixel: 8
[    21.753] 	NumberOfBanks: 1
[    21.753] 	MemoryModel: 4
[    21.753] 	BankSize: 0
[    21.753] 	NumberOfImages: 62
[    21.753] 	RedMaskSize: 0
[    21.753] 	RedFieldPosition: 0
[    21.753] 	GreenMaskSize: 0
[    21.753] 	GreenFieldPosition: 0
[    21.753] 	BlueMaskSize: 0
[    21.753] 	BlueFieldPosition: 0
[    21.753] 	RsvdMaskSize: 0
[    21.753] 	RsvdFieldPosition: 0
[    21.753] 	DirectColorModeInfo: 0
[    21.753] 	PhysBasePtr: 0xfb000000
[    21.753] 	LinBytesPerScanLine: 320
[    21.753] 	BnkNumberOfImagePages: 62
[    21.753] 	LinNumberOfImagePages: 62
[    21.753] 	LinRedMaskSize: 0
[    21.753] 	LinRedFieldPosition: 0
[    21.753] 	LinGreenMaskSize: 0
[    21.753] 	LinGreenFieldPosition: 0
[    21.753] 	LinBlueMaskSize: 0
[    21.753] 	LinBlueFieldPosition: 0
[    21.753] 	LinRsvdMaskSize: 0
[    21.753] 	LinRsvdFieldPosition: 0
[    21.753] 	MaxPixelClock: 229500000
[    21.756] Mode: 131 (320x400)
[    21.756] 	ModeAttributes: 0x3bf
[    21.756] 	WinAAttributes: 0x7
[    21.756] 	WinBAttributes: 0x0
[    21.756] 	WinGranularity: 64
[    21.756] 	WinSize: 64
[    21.756] 	WinASegment: 0xa000
[    21.756] 	WinBSegment: 0x0
[    21.756] 	WinFuncPtr: 0xc0008608
[    21.756] 	BytesPerScanline: 320
[    21.756] 	XResolution: 320
[    21.756] 	YResolution: 400
[    21.756] 	XCharSize: 8
[    21.756] 	YCharSize: 16
[    21.756] 	NumberOfPlanes: 1
[    21.756] 	BitsPerPixel: 8
[    21.757] 	NumberOfBanks: 1
[    21.757] 	MemoryModel: 4
[    21.757] 	BankSize: 0
[    21.757] 	NumberOfImages: 30
[    21.757] 	RedMaskSize: 0
[    21.757] 	RedFieldPosition: 0
[    21.757] 	GreenMaskSize: 0
[    21.757] 	GreenFieldPosition: 0
[    21.757] 	BlueMaskSize: 0
[    21.757] 	BlueFieldPosition: 0
[    21.757] 	RsvdMaskSize: 0
[    21.757] 	RsvdFieldPosition: 0
[    21.757] 	DirectColorModeInfo: 0
[    21.757] 	PhysBasePtr: 0xfb000000
[    21.757] 	LinBytesPerScanLine: 320
[    21.757] 	BnkNumberOfImagePages: 30
[    21.757] 	LinNumberOfImagePages: 30
[    21.757] 	LinRedMaskSize: 0
[    21.757] 	LinRedFieldPosition: 0
[    21.757] 	LinGreenMaskSize: 0
[    21.757] 	LinGreenFieldPosition: 0
[    21.757] 	LinBlueMaskSize: 0
[    21.757] 	LinBlueFieldPosition: 0
[    21.757] 	LinRsvdMaskSize: 0
[    21.757] 	LinRsvdFieldPosition: 0
[    21.757] 	MaxPixelClock: 229500000
[    21.760] Mode: 132 (320x400)
[    21.760] 	ModeAttributes: 0x3bf
[    21.760] 	WinAAttributes: 0x7
[    21.760] 	WinBAttributes: 0x0
[    21.760] 	WinGranularity: 64
[    21.760] 	WinSize: 64
[    21.760] 	WinASegment: 0xa000
[    21.760] 	WinBSegment: 0x0
[    21.760] 	WinFuncPtr: 0xc0008608
[    21.760] 	BytesPerScanline: 640
[    21.760] 	XResolution: 320
[    21.760] 	YResolution: 400
[    21.760] 	XCharSize: 8
[    21.760] 	YCharSize: 16
[    21.760] 	NumberOfPlanes: 1
[    21.760] 	BitsPerPixel: 16
[    21.760] 	NumberOfBanks: 1
[    21.760] 	MemoryModel: 6
[    21.760] 	BankSize: 0
[    21.760] 	NumberOfImages: 14
[    21.760] 	RedMaskSize: 5
[    21.760] 	RedFieldPosition: 11
[    21.760] 	GreenMaskSize: 6
[    21.760] 	GreenFieldPosition: 5
[    21.760] 	BlueMaskSize: 5
[    21.760] 	BlueFieldPosition: 0
[    21.760] 	RsvdMaskSize: 0
[    21.760] 	RsvdFieldPosition: 0
[    21.760] 	DirectColorModeInfo: 0
[    21.760] 	PhysBasePtr: 0xfb000000
[    21.760] 	LinBytesPerScanLine: 640
[    21.760] 	BnkNumberOfImagePages: 14
[    21.760] 	LinNumberOfImagePages: 14
[    21.760] 	LinRedMaskSize: 5
[    21.760] 	LinRedFieldPosition: 11
[    21.760] 	LinGreenMaskSize: 6
[    21.760] 	LinGreenFieldPosition: 5
[    21.760] 	LinBlueMaskSize: 5
[    21.760] 	LinBlueFieldPosition: 0
[    21.760] 	LinRsvdMaskSize: 0
[    21.760] 	LinRsvdFieldPosition: 0
[    21.760] 	MaxPixelClock: 229500000
[    21.763] *Mode: 133 (320x400)
[    21.763] 	ModeAttributes: 0x3bf
[    21.763] 	WinAAttributes: 0x7
[    21.763] 	WinBAttributes: 0x0
[    21.763] 	WinGranularity: 64
[    21.763] 	WinSize: 64
[    21.763] 	WinASegment: 0xa000
[    21.763] 	WinBSegment: 0x0
[    21.763] 	WinFuncPtr: 0xc0008608
[    21.763] 	BytesPerScanline: 1280
[    21.763] 	XResolution: 320
[    21.763] 	YResolution: 400
[    21.763] 	XCharSize: 8
[    21.763] 	YCharSize: 16
[    21.763] 	NumberOfPlanes: 1
[    21.763] 	BitsPerPixel: 32
[    21.763] 	NumberOfBanks: 1
[    21.763] 	MemoryModel: 6
[    21.763] 	BankSize: 0
[    21.763] 	NumberOfImages: 6
[    21.763] 	RedMaskSize: 8
[    21.763] 	RedFieldPosition: 16
[    21.763] 	GreenMaskSize: 8
[    21.763] 	GreenFieldPosition: 8
[    21.763] 	BlueMaskSize: 8
[    21.763] 	BlueFieldPosition: 0
[    21.763] 	RsvdMaskSize: 8
[    21.763] 	RsvdFieldPosition: 24
[    21.763] 	DirectColorModeInfo: 0
[    21.763] 	PhysBasePtr: 0xfb000000
[    21.763] 	LinBytesPerScanLine: 1280
[    21.763] 	BnkNumberOfImagePages: 6
[    21.763] 	LinNumberOfImagePages: 6
[    21.763] 	LinRedMaskSize: 8
[    21.764] 	LinRedFieldPosition: 16
[    21.764] 	LinGreenMaskSize: 8
[    21.764] 	LinGreenFieldPosition: 8
[    21.764] 	LinBlueMaskSize: 8
[    21.764] 	LinBlueFieldPosition: 0
[    21.764] 	LinRsvdMaskSize: 8
[    21.764] 	LinRsvdFieldPosition: 24
[    21.764] 	MaxPixelClock: 229500000
[    21.767] Mode: 134 (320x240)
[    21.767] 	ModeAttributes: 0x3bf
[    21.767] 	WinAAttributes: 0x7
[    21.767] 	WinBAttributes: 0x0
[    21.767] 	WinGranularity: 64
[    21.767] 	WinSize: 64
[    21.767] 	WinASegment: 0xa000
[    21.767] 	WinBSegment: 0x0
[    21.767] 	WinFuncPtr: 0xc0008608
[    21.767] 	BytesPerScanline: 320
[    21.767] 	XResolution: 320
[    21.767] 	YResolution: 240
[    21.767] 	XCharSize: 8
[    21.767] 	YCharSize: 8
[    21.767] 	NumberOfPlanes: 1
[    21.767] 	BitsPerPixel: 8
[    21.767] 	NumberOfBanks: 1
[    21.767] 	MemoryModel: 4
[    21.767] 	BankSize: 0
[    21.767] 	NumberOfImages: 30
[    21.767] 	RedMaskSize: 0
[    21.767] 	RedFieldPosition: 0
[    21.767] 	GreenMaskSize: 0
[    21.767] 	GreenFieldPosition: 0
[    21.767] 	BlueMaskSize: 0
[    21.767] 	BlueFieldPosition: 0
[    21.767] 	RsvdMaskSize: 0
[    21.767] 	RsvdFieldPosition: 0
[    21.767] 	DirectColorModeInfo: 0
[    21.767] 	PhysBasePtr: 0xfb000000
[    21.767] 	LinBytesPerScanLine: 320
[    21.767] 	BnkNumberOfImagePages: 30
[    21.767] 	LinNumberOfImagePages: 30
[    21.767] 	LinRedMaskSize: 0
[    21.767] 	LinRedFieldPosition: 0
[    21.767] 	LinGreenMaskSize: 0
[    21.767] 	LinGreenFieldPosition: 0
[    21.767] 	LinBlueMaskSize: 0
[    21.767] 	LinBlueFieldPosition: 0
[    21.767] 	LinRsvdMaskSize: 0
[    21.767] 	LinRsvdFieldPosition: 0
[    21.767] 	MaxPixelClock: 229500000
[    21.770] Mode: 135 (320x240)
[    21.770] 	ModeAttributes: 0x3bf
[    21.770] 	WinAAttributes: 0x7
[    21.770] 	WinBAttributes: 0x0
[    21.770] 	WinGranularity: 64
[    21.770] 	WinSize: 64
[    21.770] 	WinASegment: 0xa000
[    21.770] 	WinBSegment: 0x0
[    21.770] 	WinFuncPtr: 0xc0008608
[    21.770] 	BytesPerScanline: 640
[    21.770] 	XResolution: 320
[    21.770] 	YResolution: 240
[    21.770] 	XCharSize: 8
[    21.770] 	YCharSize: 8
[    21.770] 	NumberOfPlanes: 1
[    21.770] 	BitsPerPixel: 16
[    21.770] 	NumberOfBanks: 1
[    21.770] 	MemoryModel: 6
[    21.770] 	BankSize: 0
[    21.770] 	NumberOfImages: 19
[    21.770] 	RedMaskSize: 5
[    21.770] 	RedFieldPosition: 11
[    21.770] 	GreenMaskSize: 6
[    21.771] 	GreenFieldPosition: 5
[    21.771] 	BlueMaskSize: 5
[    21.771] 	BlueFieldPosition: 0
[    21.771] 	RsvdMaskSize: 0
[    21.771] 	RsvdFieldPosition: 0
[    21.771] 	DirectColorModeInfo: 0
[    21.771] 	PhysBasePtr: 0xfb000000
[    21.771] 	LinBytesPerScanLine: 640
[    21.771] 	BnkNumberOfImagePages: 19
[    21.771] 	LinNumberOfImagePages: 19
[    21.771] 	LinRedMaskSize: 5
[    21.771] 	LinRedFieldPosition: 11
[    21.771] 	LinGreenMaskSize: 6
[    21.771] 	LinGreenFieldPosition: 5
[    21.771] 	LinBlueMaskSize: 5
[    21.771] 	LinBlueFieldPosition: 0
[    21.771] 	LinRsvdMaskSize: 0
[    21.771] 	LinRsvdFieldPosition: 0
[    21.771] 	MaxPixelClock: 229500000
[    21.774] *Mode: 136 (320x240)
[    21.774] 	ModeAttributes: 0x3bf
[    21.774] 	WinAAttributes: 0x7
[    21.774] 	WinBAttributes: 0x0
[    21.774] 	WinGranularity: 64
[    21.774] 	WinSize: 64
[    21.774] 	WinASegment: 0xa000
[    21.774] 	WinBSegment: 0x0
[    21.774] 	WinFuncPtr: 0xc0008608
[    21.774] 	BytesPerScanline: 1280
[    21.774] 	XResolution: 320
[    21.774] 	YResolution: 240
[    21.774] 	XCharSize: 8
[    21.774] 	YCharSize: 8
[    21.774] 	NumberOfPlanes: 1
[    21.774] 	BitsPerPixel: 32
[    21.774] 	NumberOfBanks: 1
[    21.774] 	MemoryModel: 6
[    21.774] 	BankSize: 0
[    21.774] 	NumberOfImages: 10
[    21.774] 	RedMaskSize: 8
[    21.774] 	RedFieldPosition: 16
[    21.774] 	GreenMaskSize: 8
[    21.774] 	GreenFieldPosition: 8
[    21.774] 	BlueMaskSize: 8
[    21.774] 	BlueFieldPosition: 0
[    21.774] 	RsvdMaskSize: 8
[    21.774] 	RsvdFieldPosition: 24
[    21.774] 	DirectColorModeInfo: 0
[    21.774] 	PhysBasePtr: 0xfb000000
[    21.774] 	LinBytesPerScanLine: 1280
[    21.774] 	BnkNumberOfImagePages: 10
[    21.774] 	LinNumberOfImagePages: 10
[    21.774] 	LinRedMaskSize: 8
[    21.774] 	LinRedFieldPosition: 16
[    21.774] 	LinGreenMaskSize: 8
[    21.774] 	LinGreenFieldPosition: 8
[    21.774] 	LinBlueMaskSize: 8
[    21.774] 	LinBlueFieldPosition: 0
[    21.774] 	LinRsvdMaskSize: 8
[    21.774] 	LinRsvdFieldPosition: 24
[    21.774] 	MaxPixelClock: 229500000
[    21.777] Mode: 13d (640x400)
[    21.777] 	ModeAttributes: 0x3bf
[    21.777] 	WinAAttributes: 0x7
[    21.777] 	WinBAttributes: 0x0
[    21.777] 	WinGranularity: 64
[    21.777] 	WinSize: 64
[    21.777] 	WinASegment: 0xa000
[    21.777] 	WinBSegment: 0x0
[    21.777] 	WinFuncPtr: 0xc0008608
[    21.777] 	BytesPerScanline: 1280
[    21.777] 	XResolution: 640
[    21.777] 	YResolution: 400
[    21.777] 	XCharSize: 8
[    21.777] 	YCharSize: 16
[    21.777] 	NumberOfPlanes: 1
[    21.777] 	BitsPerPixel: 16
[    21.777] 	NumberOfBanks: 1
[    21.777] 	MemoryModel: 6
[    21.777] 	BankSize: 0
[    21.777] 	NumberOfImages: 6
[    21.777] 	RedMaskSize: 5
[    21.777] 	RedFieldPosition: 11
[    21.777] 	GreenMaskSize: 6
[    21.778] 	GreenFieldPosition: 5
[    21.778] 	BlueMaskSize: 5
[    21.778] 	BlueFieldPosition: 0
[    21.778] 	RsvdMaskSize: 0
[    21.778] 	RsvdFieldPosition: 0
[    21.778] 	DirectColorModeInfo: 0
[    21.778] 	PhysBasePtr: 0xfb000000
[    21.778] 	LinBytesPerScanLine: 1280
[    21.778] 	BnkNumberOfImagePages: 6
[    21.778] 	LinNumberOfImagePages: 6
[    21.778] 	LinRedMaskSize: 5
[    21.778] 	LinRedFieldPosition: 11
[    21.778] 	LinGreenMaskSize: 6
[    21.778] 	LinGreenFieldPosition: 5
[    21.778] 	LinBlueMaskSize: 5
[    21.778] 	LinBlueFieldPosition: 0
[    21.778] 	LinRsvdMaskSize: 0
[    21.778] 	LinRsvdFieldPosition: 0
[    21.778] 	MaxPixelClock: 229500000
[    21.781] *Mode: 13e (640x400)
[    21.781] 	ModeAttributes: 0x3bf
[    21.781] 	WinAAttributes: 0x7
[    21.781] 	WinBAttributes: 0x0
[    21.781] 	WinGranularity: 64
[    21.781] 	WinSize: 64
[    21.781] 	WinASegment: 0xa000
[    21.781] 	WinBSegment: 0x0
[    21.781] 	WinFuncPtr: 0xc0008608
[    21.781] 	BytesPerScanline: 2560
[    21.781] 	XResolution: 640
[    21.781] 	YResolution: 400
[    21.781] 	XCharSize: 8
[    21.781] 	YCharSize: 16
[    21.781] 	NumberOfPlanes: 1
[    21.781] 	BitsPerPixel: 32
[    21.781] 	NumberOfBanks: 1
[    21.781] 	MemoryModel: 6
[    21.781] 	BankSize: 0
[    21.781] 	NumberOfImages: 2
[    21.781] 	RedMaskSize: 8
[    21.781] 	RedFieldPosition: 16
[    21.781] 	GreenMaskSize: 8
[    21.781] 	GreenFieldPosition: 8
[    21.781] 	BlueMaskSize: 8
[    21.781] 	BlueFieldPosition: 0
[    21.781] 	RsvdMaskSize: 8
[    21.781] 	RsvdFieldPosition: 24
[    21.781] 	DirectColorModeInfo: 0
[    21.781] 	PhysBasePtr: 0xfb000000
[    21.781] 	LinBytesPerScanLine: 2560
[    21.781] 	BnkNumberOfImagePages: 2
[    21.781] 	LinNumberOfImagePages: 2
[    21.781] 	LinRedMaskSize: 8
[    21.781] 	LinRedFieldPosition: 16
[    21.781] 	LinGreenMaskSize: 8
[    21.781] 	LinGreenFieldPosition: 8
[    21.781] 	LinBlueMaskSize: 8
[    21.781] 	LinBlueFieldPosition: 0
[    21.781] 	LinRsvdMaskSize: 8
[    21.781] 	LinRsvdFieldPosition: 24
[    21.781] 	MaxPixelClock: 229500000
[    21.785] Mode: 160 (1280x800)
[    21.785] 	ModeAttributes: 0x3bf
[    21.785] 	WinAAttributes: 0x7
[    21.785] 	WinBAttributes: 0x0
[    21.785] 	WinGranularity: 64
[    21.785] 	WinSize: 64
[    21.785] 	WinASegment: 0xa000
[    21.785] 	WinBSegment: 0x0
[    21.785] 	WinFuncPtr: 0xc0008608
[    21.785] 	BytesPerScanline: 1280
[    21.785] 	XResolution: 1280
[    21.785] 	YResolution: 800
[    21.785] 	XCharSize: 8
[    21.785] 	YCharSize: 16
[    21.785] 	NumberOfPlanes: 1
[    21.785] 	BitsPerPixel: 8
[    21.785] 	NumberOfBanks: 1
[    21.785] 	MemoryModel: 4
[    21.785] 	BankSize: 0
[    21.785] 	NumberOfImages: 2
[    21.785] 	RedMaskSize: 0
[    21.785] 	RedFieldPosition: 0
[    21.785] 	GreenMaskSize: 0
[    21.785] 	GreenFieldPosition: 0
[    21.785] 	BlueMaskSize: 0
[    21.785] 	BlueFieldPosition: 0
[    21.785] 	RsvdMaskSize: 0
[    21.785] 	RsvdFieldPosition: 0
[    21.785] 	DirectColorModeInfo: 0
[    21.785] 	PhysBasePtr: 0xfb000000
[    21.785] 	LinBytesPerScanLine: 1280
[    21.785] 	BnkNumberOfImagePages: 2
[    21.785] 	LinNumberOfImagePages: 2
[    21.785] 	LinRedMaskSize: 0
[    21.785] 	LinRedFieldPosition: 0
[    21.785] 	LinGreenMaskSize: 0
[    21.785] 	LinGreenFieldPosition: 0
[    21.785] 	LinBlueMaskSize: 0
[    21.785] 	LinBlueFieldPosition: 0
[    21.785] 	LinRsvdMaskSize: 0
[    21.785] 	LinRsvdFieldPosition: 0
[    21.785] 	MaxPixelClock: 229500000
[    21.788] *Mode: 161 (1280x800)
[    21.788] 	ModeAttributes: 0x3bf
[    21.788] 	WinAAttributes: 0x7
[    21.788] 	WinBAttributes: 0x0
[    21.789] 	WinGranularity: 64
[    21.789] 	WinSize: 64
[    21.789] 	WinASegment: 0xa000
[    21.789] 	WinBSegment: 0x0
[    21.789] 	WinFuncPtr: 0xc0008608
[    21.789] 	BytesPerScanline: 5120
[    21.789] 	XResolution: 1280
[    21.789] 	YResolution: 800
[    21.789] 	XCharSize: 8
[    21.789] 	YCharSize: 16
[    21.789] 	NumberOfPlanes: 1
[    21.789] 	BitsPerPixel: 32
[    21.789] 	NumberOfBanks: 1
[    21.789] 	MemoryModel: 6
[    21.789] 	BankSize: 0
[    21.789] 	NumberOfImages: 1
[    21.789] 	RedMaskSize: 8
[    21.789] 	RedFieldPosition: 16
[    21.789] 	GreenMaskSize: 8
[    21.789] 	GreenFieldPosition: 8
[    21.789] 	BlueMaskSize: 8
[    21.789] 	BlueFieldPosition: 0
[    21.789] 	RsvdMaskSize: 8
[    21.789] 	RsvdFieldPosition: 24
[    21.789] 	DirectColorModeInfo: 0
[    21.789] 	PhysBasePtr: 0xfb000000
[    21.789] 	LinBytesPerScanLine: 5120
[    21.789] 	BnkNumberOfImagePages: 1
[    21.789] 	LinNumberOfImagePages: 1
[    21.789] 	LinRedMaskSize: 8
[    21.789] 	LinRedFieldPosition: 16
[    21.789] 	LinGreenMaskSize: 8
[    21.789] 	LinGreenFieldPosition: 8
[    21.789] 	LinBlueMaskSize: 8
[    21.789] 	LinBlueFieldPosition: 0
[    21.789] 	LinRsvdMaskSize: 8
[    21.789] 	LinRsvdFieldPosition: 24
[    21.789] 	MaxPixelClock: 229500000
[    21.792] Mode: 162 (768x480)
[    21.792] 	ModeAttributes: 0x3bf
[    21.792] 	WinAAttributes: 0x7
[    21.792] 	WinBAttributes: 0x0
[    21.792] 	WinGranularity: 64
[    21.792] 	WinSize: 64
[    21.792] 	WinASegment: 0xa000
[    21.792] 	WinBSegment: 0x0
[    21.792] 	WinFuncPtr: 0xc0008608
[    21.792] 	BytesPerScanline: 768
[    21.792] 	XResolution: 768
[    21.792] 	YResolution: 480
[    21.792] 	XCharSize: 8
[    21.792] 	YCharSize: 16
[    21.792] 	NumberOfPlanes: 1
[    21.792] 	BitsPerPixel: 8
[    21.792] 	NumberOfBanks: 1
[    21.792] 	MemoryModel: 4
[    21.792] 	BankSize: 0
[    21.792] 	NumberOfImages: 8
[    21.792] 	RedMaskSize: 0
[    21.792] 	RedFieldPosition: 0
[    21.792] 	GreenMaskSize: 0
[    21.792] 	GreenFieldPosition: 0
[    21.793] 	BlueMaskSize: 0
[    21.793] 	BlueFieldPosition: 0
[    21.793] 	RsvdMaskSize: 0
[    21.793] 	RsvdFieldPosition: 0
[    21.793] 	DirectColorModeInfo: 0
[    21.793] 	PhysBasePtr: 0xfb000000
[    21.793] 	LinBytesPerScanLine: 768
[    21.793] 	BnkNumberOfImagePages: 8
[    21.793] 	LinNumberOfImagePages: 8
[    21.793] 	LinRedMaskSize: 0
[    21.793] 	LinRedFieldPosition: 0
[    21.793] 	LinGreenMaskSize: 0
[    21.793] 	LinGreenFieldPosition: 0
[    21.793] 	LinBlueMaskSize: 0
[    21.793] 	LinBlueFieldPosition: 0
[    21.793] 	LinRsvdMaskSize: 0
[    21.793] 	LinRsvdFieldPosition: 0
[    21.793] 	MaxPixelClock: 229500000
[    21.796] *Mode: 17b (1280x720)
[    21.796] 	ModeAttributes: 0x3bf
[    21.796] 	WinAAttributes: 0x7
[    21.796] 	WinBAttributes: 0x0
[    21.796] 	WinGranularity: 64
[    21.796] 	WinSize: 64
[    21.796] 	WinASegment: 0xa000
[    21.796] 	WinBSegment: 0x0
[    21.796] 	WinFuncPtr: 0xc0008608
[    21.796] 	BytesPerScanline: 5120
[    21.796] 	XResolution: 1280
[    21.796] 	YResolution: 720
[    21.796] 	XCharSize: 8
[    21.796] 	YCharSize: 16
[    21.796] 	NumberOfPlanes: 1
[    21.796] 	BitsPerPixel: 32
[    21.796] 	NumberOfBanks: 1
[    21.796] 	MemoryModel: 6
[    21.796] 	BankSize: 0
[    21.796] 	NumberOfImages: 1
[    21.796] 	RedMaskSize: 8
[    21.796] 	RedFieldPosition: 16
[    21.796] 	GreenMaskSize: 8
[    21.796] 	GreenFieldPosition: 8
[    21.796] 	BlueMaskSize: 8
[    21.796] 	BlueFieldPosition: 0
[    21.796] 	RsvdMaskSize: 8
[    21.796] 	RsvdFieldPosition: 24
[    21.796] 	DirectColorModeInfo: 0
[    21.796] 	PhysBasePtr: 0xfb000000
[    21.796] 	LinBytesPerScanLine: 5120
[    21.796] 	BnkNumberOfImagePages: 1
[    21.796] 	LinNumberOfImagePages: 1
[    21.796] 	LinRedMaskSize: 8
[    21.796] 	LinRedFieldPosition: 16
[    21.796] 	LinGreenMaskSize: 8
[    21.796] 	LinGreenFieldPosition: 8
[    21.796] 	LinBlueMaskSize: 8
[    21.796] 	LinBlueFieldPosition: 0
[    21.796] 	LinRsvdMaskSize: 8
[    21.796] 	LinRsvdFieldPosition: 24
[    21.796] 	MaxPixelClock: 229500000
[    21.796] 
[    21.796] (II) VESA(0): Total Memory: 224 64KB banks (14336kB)
[    21.797] (II) VESA(0): <default monitor>: Using default hsync range of 31.50-37.90 kHz
[    21.797] (II) VESA(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[    21.797] (WW) VESA(0): Unable to estimate virtual size
[    21.797] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[    21.797] (II) VESA(0): Not using built-in mode "1280x800" (no mode of this name)
[    21.797] (II) VESA(0): Not using built-in mode "1280x720" (no mode of this name)
[    21.797] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    21.797] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    21.797] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    21.797] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[    21.797] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[    21.797] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    21.797] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    21.797] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    21.797] (II) VESA(0): <default monitor>: Using hsync range of 31.50-37.90 kHz
[    21.797] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-70.00 Hz
[    21.797] (WW) VESA(0): Unable to estimate virtual size
[    21.797] (II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
[    21.797] (II) VESA(0): Not using built-in mode "1280x800" (hsync out of range)
[    21.797] (II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
[    21.797] (II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
[    21.797] (II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
[    21.797] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[    21.797] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[    21.797] (--) VESA(0): Virtual size is 1280x720 (pitch 1280)
[    21.797] (**) VESA(0): *Built-in mode "1280x720"
[    21.797] (**) VESA(0): *Built-in mode "800x600"
[    21.797] (**) VESA(0): *Built-in mode "640x480"
[    21.797] (==) VESA(0): DPI set to (96, 96)
[    21.797] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
[    21.799] (II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
[    21.801] (**) VESA(0): Using "Shadow Framebuffer"
[    21.801] (II) Loading sub module "shadow"
[    21.801] (II) LoadModule: "shadow"
[    21.801] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    21.928] (II) Module shadow: vendor="X.Org Foundation"
[    21.928] 	compiled for 1.9.0, module version = 1.1.0
[    21.928] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.928] (II) Loading sub module "fb"
[    21.928] (II) LoadModule: "fb"
[    21.928] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.043] (II) Module fb: vendor="X.Org Foundation"
[    22.043] 	compiled for 1.9.0, module version = 1.0.0
[    22.043] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    22.043] (II) UnloadModule: "nv"
[    22.043] (II) Unloading /usr/lib/xorg/modules/drivers/nv_drv.so
[    22.043] (II) UnloadModule: "fbdev"
[    22.043] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.043] (II) UnloadModule: "fbdevhw"
[    22.043] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    22.043] (==) Depth 24 pixmap format is 32 bpp
[    22.043] (II) Loading sub module "int10"
[    22.043] (II) LoadModule: "int10"
[    22.043] (II) Reloading /usr/lib/xorg/modules/libint10.so
[    22.043] (II) VESA(0): initializing int10
[    22.047] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    22.187] (II) VESA(0): VESA BIOS detected
[    22.187] (II) VESA(0): VESA VBE Version 3.0
[    22.187] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    22.187] (II) VESA(0): VESA VBE OEM: NVIDIA
[    22.187] (II) VESA(0): VESA VBE OEM Software Rev: 98.119
[    22.187] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    22.187] (II) VESA(0): VESA VBE OEM Product: MCP77 Board - mcp78so 
[    22.187] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    22.188] (II) VESA(0): virtual address = 0xb6932000,
	physical address = 0xfb000000, size = 14680064
[    22.208] (II) VESA(0): Setting up VESA Mode 0x17B (1280x720)
[    22.481] (==) VESA(0): Default visual is TrueColor
[    22.512] (==) VESA(0): Backing store disabled
[    22.526] (==) VESA(0): DPMS enabled
[    22.526] (==) RandR enabled
[    22.526] (II) Initializing built-in extension Generic Event Extension
[    22.526] (II) Initializing built-in extension SHAPE
[    22.526] (II) Initializing built-in extension MIT-SHM
[    22.526] (II) Initializing built-in extension XInputExtension
[    22.526] (II) Initializing built-in extension XTEST
[    22.526] (II) Initializing built-in extension BIG-REQUESTS
[    22.526] (II) Initializing built-in extension SYNC
[    22.526] (II) Initializing built-in extension XKEYBOARD
[    22.526] (II) Initializing built-in extension XC-MISC
[    22.526] (II) Initializing built-in extension SECURITY
[    22.526] (II) Initializing built-in extension XINERAMA
[    22.526] (II) Initializing built-in extension XFIXES
[    22.526] (II) Initializing built-in extension RENDER
[    22.526] (II) Initializing built-in extension RANDR
[    22.526] (II) Initializing built-in extension COMPOSITE
[    22.526] (II) Initializing built-in extension DAMAGE
[    22.526] (II) Initializing built-in extension GESTURE
[    22.560] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    24.328] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    24.346] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    24.346] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.346] (II) LoadModule: "evdev"
[    24.347] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.384] (II) Module evdev: vendor="X.Org Foundation"
[    24.384] 	compiled for 1.9.0, module version = 2.3.2
[    24.384] 	Module class: X.Org XInput Driver
[    24.384] 	ABI class: X.Org XInput driver, version 11.0
[    24.384] (**) Power Button: always reports core events
[    24.384] (**) Power Button: Device: "/dev/input/event1"
[    24.385] (II) Power Button: Found keys
[    24.385] (II) Power Button: Configuring as keyboard
[    24.385] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    24.385] (**) Option "xkb_rules" "evdev"
[    24.385] (**) Option "xkb_model" "pc105"
[    24.385] (**) Option "xkb_layout" "gb"
[    24.404] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    24.405] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    24.406] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    24.406] (**) Video Bus: always reports core events
[    24.406] (**) Video Bus: Device: "/dev/input/event6"
[    24.420] (II) Video Bus: Found keys
[    24.420] (II) Video Bus: Configuring as keyboard
[    24.420] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    24.420] (**) Option "xkb_rules" "evdev"
[    24.420] (**) Option "xkb_model" "pc105"
[    24.420] (**) Option "xkb_layout" "gb"
[    24.421] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    24.421] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.421] (**) Power Button: always reports core events
[    24.421] (**) Power Button: Device: "/dev/input/event0"
[    24.436] (II) Power Button: Found keys
[    24.436] (II) Power Button: Configuring as keyboard
[    24.436] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    24.436] (**) Option "xkb_rules" "evdev"
[    24.436] (**) Option "xkb_model" "pc105"
[    24.436] (**) Option "xkb_layout" "gb"
[    24.438] (II) config/udev: Adding input device HID 1267:0103 (/dev/input/event2)
[    24.439] (**) HID 1267:0103: Applying InputClass "evdev keyboard catchall"
[    24.439] (**) HID 1267:0103: always reports core events
[    24.439] (**) HID 1267:0103: Device: "/dev/input/event2"
[    24.448] (II) HID 1267:0103: Found keys
[    24.448] (II) HID 1267:0103: Configuring as keyboard
[    24.448] (II) XINPUT: Adding extended input device "HID 1267:0103" (type: KEYBOARD)
[    24.448] (**) Option "xkb_rules" "evdev"
[    24.448] (**) Option "xkb_model" "pc105"
[    24.448] (**) Option "xkb_layout" "gb"
[    24.449] (II) config/udev: Adding input device HID 1267:0103 (/dev/input/event3)
[    24.449] (**) HID 1267:0103: Applying InputClass "evdev keyboard catchall"
[    24.449] (**) HID 1267:0103: always reports core events
[    24.449] (**) HID 1267:0103: Device: "/dev/input/event3"
[    24.460] (II) HID 1267:0103: Found 1 mouse buttons
[    24.460] (II) HID 1267:0103: Found scroll wheel(s)
[    24.460] (II) HID 1267:0103: Found relative axes
[    24.460] (II) HID 1267:0103: Found absolute axes
[    24.460] (II) evdev-grail: failed to open grail, no gesture support
[    24.460] (II) HID 1267:0103: Found keys
[    24.460] (II) HID 1267:0103: Configuring as mouse
[    24.460] (II) HID 1267:0103: Configuring as keyboard
[    24.460] (**) HID 1267:0103: YAxisMapping: buttons 4 and 5
[    24.460] (**) HID 1267:0103: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.460] (II) XINPUT: Adding extended input device "HID 1267:0103" (type: KEYBOARD)
[    24.460] (**) Option "xkb_rules" "evdev"
[    24.460] (**) Option "xkb_model" "pc105"
[    24.460] (**) Option "xkb_layout" "gb"
[    24.461] (EE) HID 1267:0103: failed to initialize for relative axes.
[    24.461] (II) HID 1267:0103: initialized for absolute axes.
[    24.461] (II) config/udev: Adding input device BTC USB Multimedia Cordless Keyboard (/dev/input/event4)
[    24.461] (**) BTC USB Multimedia Cordless Keyboard: Applying InputClass "evdev keyboard catchall"
[    24.461] (**) BTC USB Multimedia Cordless Keyboard: always reports core events
[    24.461] (**) BTC USB Multimedia Cordless Keyboard: Device: "/dev/input/event4"
[    24.476] (II) BTC USB Multimedia Cordless Keyboard: Found keys
[    24.476] (II) BTC USB Multimedia Cordless Keyboard: Configuring as keyboard
[    24.476] (II) XINPUT: Adding extended input device "BTC USB Multimedia Cordless Keyboard" (type: KEYBOARD)
[    24.476] (**) Option "xkb_rules" "evdev"
[    24.476] (**) Option "xkb_model" "pc105"
[    24.476] (**) Option "xkb_layout" "gb"
[    24.477] (II) config/udev: Adding input device BTC USB Multimedia Cordless Keyboard (/dev/input/event5)
[    24.477] (**) BTC USB Multimedia Cordless Keyboard: Applying InputClass "evdev pointer catchall"
[    24.477] (**) BTC USB Multimedia Cordless Keyboard: Applying InputClass "evdev keyboard catchall"
[    24.477] (**) BTC USB Multimedia Cordless Keyboard: always reports core events
[    24.477] (**) BTC USB Multimedia Cordless Keyboard: Device: "/dev/input/event5"
[    24.492] (II) BTC USB Multimedia Cordless Keyboard: Found 8 mouse buttons
[    24.492] (II) BTC USB Multimedia Cordless Keyboard: Found scroll wheel(s)
[    24.492] (II) BTC USB Multimedia Cordless Keyboard: Found relative axes
[    24.492] (II) BTC USB Multimedia Cordless Keyboard: Found x and y relative axes
[    24.492] (II) BTC USB Multimedia Cordless Keyboard: Found absolute axes
[    24.492] (II) evdev-grail: failed to open grail, no gesture support
[    24.492] (II) BTC USB Multimedia Cordless Keyboard: Found keys
[    24.492] (II) BTC USB Multimedia Cordless Keyboard: Configuring as mouse
[    24.492] (II) BTC USB Multimedia Cordless Keyboard: Configuring as keyboard
[    24.492] (**) BTC USB Multimedia Cordless Keyboard: YAxisMapping: buttons 4 and 5
[    24.492] (**) BTC USB Multimedia Cordless Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.492] (II) XINPUT: Adding extended input device "BTC USB Multimedia Cordless Keyboard" (type: KEYBOARD)
[    24.492] (**) Option "xkb_rules" "evdev"
[    24.492] (**) Option "xkb_model" "pc105"
[    24.492] (**) Option "xkb_layout" "gb"
[    24.493] (II) BTC USB Multimedia Cordless Keyboard: initialized for relative axes.
[    24.493] (WW) BTC USB Multimedia Cordless Keyboard: ignoring absolute axes.
[    24.493] (II) config/udev: Adding input device BTC USB Multimedia Cordless Keyboard (/dev/input/mouse0)
[    24.493] (II) No input driver/identifier specified (ignoring)
[    24.495] (II) config/udev: Adding input device IR-receiver inside an USB DVB receiver (/dev/input/event7)
[    24.495] (**) IR-receiver inside an USB DVB receiver: Applying InputClass "evdev keyboard catchall"
[    24.495] (**) IR-receiver inside an USB DVB receiver: always reports core events
[    24.495] (**) IR-receiver inside an USB DVB receiver: Device: "/dev/input/event7"
[    24.504] (II) IR-receiver inside an USB DVB receiver: Found keys
[    24.504] (II) IR-receiver inside an USB DVB receiver: Configuring as keyboard
[    24.504] (II) XINPUT: Adding extended input device "IR-receiver inside an USB DVB receiver" (type: KEYBOARD)
[    24.504] (**) Option "xkb_rules" "evdev"
[    24.504] (**) Option "xkb_model" "pc105"
[    24.504] (**) Option "xkb_layout" "gb"


```

Hope this isn't too much !

Finally the output of "aplay -l" is:

```

aplay -l

**** List of PLAYBACK Hardware Devices ****
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And I can confirm that running the following command seems to succeed (i.e. I don't get an error message as I do when I input an invalid card address) but it doesn't output sound over HDMI (which it used to do way back under 9.04...)

```

sudo aplay -D plughw:0,3 03-Object.wav" 

```

Cheers again for the reply.

---


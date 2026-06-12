---
title: "ATI Radeon HD3450 Video card dangerous?"
date: 2012-04-21
forum: Multimedia Software
---

### Post by Senior_Buckethead on 2012-04-21
Hi All

I want to download and install the Fglrx driver for my ATI RADEON HD3450 graphics card. I am running 11.10.

I downloaded the ATI Driver, filename: amd-driver-installer-12-3-x86.x86_64.run, all 108 Mb of it, and would like to install it. I went to the wiki page:

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

and was reading down, when I came upon this warning:

> 
NOTE: If you enter your card information on AMD/ATI's driver page, it  will offer you the Catalyst 9-3 driver to download. However, the  Catalyst 9-3 driver doesn't support X servers past 1.5, and it will not  work with Oneiric (or anything later than Lucid/10,04)! !!!SO BE  CAREFUL!!! If you tried to install Catalyst on a system with one of  these cards, see the 'Removing the Driver' section to restore the  default/pre-installed drivers.
How do I know which X-Server I am running? Should I install the driver?

Please let me know.
Glenn.

---

### Post by Yellow Pasque on 2012-04-21
The warning refers to the cards listed in that section and is irrelevant to your 3450.

---

### Post by Senior_Buckethead on 2012-04-21
Ok, I installed the fglrx driver from the AMD website:
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

Bear In mind I was running off the motherboard graphics chip whilst installing the driver.

The install seemed to be successful, i now have AMD Catalyst control center application in menu.
I shutdown the machine, put the ATI Radeon HD3450 card in, booted the machine and it locked up before it loaded the login screen.

How do I diagnose what aspect of the video card is making the system sieze?

I Ran XOrg Diagnose and the following error messages were generated:

fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.
fglrx(0): XMM failed to open CMMQS connection. (EE) fglrx(0):
fglrx(0): XMM failed to initialize

Glenn.

---

### Post by Senior_Buckethead on 2012-04-22
From the ATI Oneiric webpage:
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

> 
Test your installation:
NOTE: if you don't reboot first, fglrxinfo gives an error message. Reboot the computer and type: fglrxinfo 

```

glenn@acer:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  139 (ATIFGLEXTENSION)
Minor opcode of failed request:  66 ()
Serial number of failed request:  13
Current serial number in output stream:  13
glenn@acer:~$ 

```Can anyone help?

---

### Post by Yellow Pasque on 2012-04-22
Pastebin your /var/log/Xorg.0.log

---

### Post by Senior_Buckethead on 2012-04-22
Here you go

```

[    13.243] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    13.243] X Protocol Version 11, Revision 0
[    13.243] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    13.243] Current Operating System: Linux acer 3.0.0-19-generic #33-Ubuntu SMP Thu Apr 19 19:05:57 UTC 2012 i686
[    13.243] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-19-generic root=UUID=2f247f57-afa1-43e1-8660-e9f6eea50fbf ro quiet splash vt.handoff=7
[    13.243] Build Date: 19 October 2011  05:09:41AM
[    13.243] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    13.243] Current version of pixman: 0.22.2
[    13.243]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    13.243] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.244] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 22 14:06:02 2012
[    13.244] (==) Using config file: "/etc/X11/xorg.conf"
[    13.244] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    13.244] (==) ServerLayout "aticonfig Layout"
[    13.244] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    13.244] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    13.244] (**) |   |-->Device "aticonfig-Device[0]-0"
[    13.244] (==) Automatically adding devices
[    13.244] (==) Automatically enabling devices
[    13.245] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.245]     Entry deleted from font path.
[    13.245] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    13.245]     Entry deleted from font path.
[    13.245] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    13.245]     Entry deleted from font path.
[    13.245] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    13.245]     Entry deleted from font path.
[    13.245] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    13.245]     Entry deleted from font path.
[    13.245] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    13.245] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    13.245] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    13.245] (II) Loader magic: 0x823ada0
[    13.245] (II) Module ABI versions:
[    13.245]     X.Org ANSI C Emulation: 0.4
[    13.245]     X.Org Video Driver: 10.0
[    13.245]     X.Org XInput driver : 12.3
[    13.245]     X.Org Server Extension : 5.0
[    13.246] (--) PCI:*(0:1:5:0) 1002:9610:1025:014e rev 0, Mem @ 0xd0000000/268435456, 0xfe8f0000/65536, 0xfe700000/1048576, I/O @ 0x0000c000/256
[    13.246] (II) Open ACPI successful (/var/run/acpid.socket)
[    13.246] (II) "extmod" will be loaded by default.
[    13.246] (II) "dbe" will be loaded by default.
[    13.246] (II) "glx" will be loaded by default.
[    13.246] (II) "record" will be loaded by default.
[    13.246] (II) "dri" will be loaded by default.
[    13.246] (II) "dri2" will be loaded by default.
[    13.246] (II) LoadModule: "extmod"
[    13.260] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    13.260] (II) Module extmod: vendor="X.Org Foundation"
[    13.260]     compiled for 1.10.4, module version = 1.0.0
[    13.260]     Module class: X.Org Server Extension
[    13.261]     ABI class: X.Org Server Extension, version 5.0
[    13.261] (II) Loading extension MIT-SCREEN-SAVER
[    13.261] (II) Loading extension XFree86-VidModeExtension
[    13.261] (II) Loading extension XFree86-DGA
[    13.261] (II) Loading extension DPMS
[    13.261] (II) Loading extension XVideo
[    13.261] (II) Loading extension XVideo-MotionCompensation
[    13.261] (II) Loading extension X-Resource
[    13.261] (II) LoadModule: "dbe"
[    13.261] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    13.261] (II) Module dbe: vendor="X.Org Foundation"
[    13.261]     compiled for 1.10.4, module version = 1.0.0
[    13.261]     Module class: X.Org Server Extension
[    13.261]     ABI class: X.Org Server Extension, version 5.0
[    13.261] (II) Loading extension DOUBLE-BUFFER
[    13.261] (II) LoadModule: "glx"
[    13.261] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    13.261] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    13.261]     compiled for 6.9.0, module version = 1.0.0
[    13.262] (II) Loading extension GLX
[    13.262] (II) LoadModule: "record"
[    13.262] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    13.262] (II) Module record: vendor="X.Org Foundation"
[    13.262]     compiled for 1.10.4, module version = 1.13.0
[    13.262]     Module class: X.Org Server Extension
[    13.262]     ABI class: X.Org Server Extension, version 5.0
[    13.262] (II) Loading extension RECORD
[    13.262] (II) LoadModule: "dri"
[    13.263] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    13.263] (II) Module dri: vendor="X.Org Foundation"
[    13.263]     compiled for 1.10.4, module version = 1.0.0
[    13.263]     ABI class: X.Org Server Extension, version 5.0
[    13.263] (II) Loading extension XFree86-DRI
[    13.263] (II) LoadModule: "dri2"
[    13.263] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.263] (II) Module dri2: vendor="X.Org Foundation"
[    13.263]     compiled for 1.10.4, module version = 1.2.0
[    13.263]     ABI class: X.Org Server Extension, version 5.0
[    13.263] (II) Loading extension DRI2
[    13.263] (II) LoadModule: "fglrx"
[    13.263] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    13.285] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    13.285]     compiled for 1.4.99.906, module version = 8.95.3
[    13.285]     Module class: X.Org Video Driver
[    13.286] (II) Loading sub module "fglrxdrm"
[    13.286] (II) LoadModule: "fglrxdrm"
[    13.286] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    13.286] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    13.286]     compiled for 1.4.99.906, module version = 8.95.3
[    13.286] (II) ATI Proprietary Linux Driver Version Identifier:8.95.3
[    13.286] (II) ATI Proprietary Linux Driver Release Identifier: 8.951                                
[    13.286] (II) ATI Proprietary Linux Driver Build Date: Mar  8 2012 23:06:36
[    13.286] (++) using VT number 7

[    13.286] (WW) Falling back to old probe method for fglrx
[    13.300] (II) Loading PCS database from /etc/ati/amdpcsdb
[    13.302] (--) Chipset Supported AMD Graphics Processor (0x9610) found
[    13.302] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[    13.302] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    13.302] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
[    13.302] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[    13.302] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    13.302] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
[    13.302] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    13.302] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    13.302] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[    13.302] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    13.302] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    13.302] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    13.302] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[    13.302] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:1) found
[    13.302] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    13.302] (II) AMD Video driver is signed
[    13.302] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    13.302] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    13.302] (II) fglrx(0): pEnt->device->identifier=0xa00af10
[    13.302] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[    13.303] (II) Loading sub module "vgahw"
[    13.303] (II) LoadModule: "vgahw"
[    13.303] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    13.303] (II) Module vgahw: vendor="X.Org Foundation"
[    13.303]     compiled for 1.10.4, module version = 0.1.0
[    13.303]     ABI class: X.Org Video Driver, version 10.0
[    13.303] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    13.303] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    13.303] (==) fglrx(0): Default visual is TrueColor
[    13.303] (**) fglrx(0): Option "DPMS" "true"
[    13.303] (==) fglrx(0): RGB weight 888
[    13.304] (II) fglrx(0): Using 8 bits per RGB 
[    13.304] (==) fglrx(0): Buffer Tiling is ON
[    13.304] (II) Loading sub module "fglrxdrm"
[    13.304] (II) LoadModule: "fglrxdrm"
[    13.304] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    13.304] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    13.304]     compiled for 1.4.99.906, module version = 8.95.3
[    13.306] ukiDynamicMajor: failed to open /proc/ati/major
[    13.306] ukiDynamicMajor: failed to open /proc/ati/major
[    13.306] (**) fglrx(0): NoAccel = NO
[    13.306] (**) fglrx(0): ATI 2D Acceleration Architecture enabled
[    13.306] (--) fglrx(0): Chipset: "ATI Radeon HD 3200 Graphics" (Chipset = 0x9610)
[    13.306] (--) fglrx(0): (PciSubVendor = 0x1025, PciSubDevice = 0x014e)
[    13.306] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    13.306] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    13.306] (--) fglrx(0): MMIO registers at 0xfe8f0000
[    13.306] (--) fglrx(0): I/O port at 0x0000c000
[    13.306] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    13.315] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    13.316] (II) Loading sub module "vbe"
[    13.316] (II) LoadModule: "vbe"
[    13.317] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    13.317] (II) Module vbe: vendor="X.Org Foundation"
[    13.317]     compiled for 1.10.4, module version = 1.1.0
[    13.317]     ABI class: X.Org Video Driver, version 10.0
[    13.317] (II) fglrx(0): VESA BIOS detected
[    13.317] (II) fglrx(0): VESA VBE Version 3.0
[    13.317] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    13.317] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    13.317] (II) fglrx(0): VESA VBE OEM Software Rev: 10.73
[    13.317] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    13.317] (II) fglrx(0): VESA VBE OEM Product: RS780
[    13.317] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    13.326] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    13.327] (--) fglrx(0): Video RAM: 262144 kByte, Type: DDR2
[    13.327] (II) fglrx(0): PCIE card detected
[    13.327] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    13.327] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    13.327] (WW) fglrx(0): Hasn't establisted DRM connection
[    13.327] (II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
[    13.327] (WW) fglrx(0): No DRM connection for driver fglrx.
[    13.327] (II) fglrx(0): RandR 1.2 support is enabled!
[    13.327] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    13.327] (==) fglrx(0): Center Mode is disabled 
[    13.327] (II) Loading sub module "fb"
[    13.327] (II) LoadModule: "fb"
[    13.327] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.327] (II) Module fb: vendor="X.Org Foundation"
[    13.327]     compiled for 1.10.4, module version = 1.0.0
[    13.327]     ABI class: X.Org ANSI C Emulation, version 0.4
[    13.327] (II) Loading sub module "ddc"
[    13.327] (II) LoadModule: "ddc"
[    13.327] (II) Module "ddc" already built-in
[    13.787] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    13.787] (II) fglrx(0): Output CRT1 has no monitor section
[    13.787] (II) Loading sub module "ddc"
[    13.787] (II) LoadModule: "ddc"
[    13.787] (II) Module "ddc" already built-in
[    13.787] (II) fglrx(0): Connected Display0: CRT1
[    13.787] (II) fglrx(0): Display0 EDID data ---------------------------
[    13.787] (II) fglrx(0): Manufacturer: SAN  Model: 52d  Serial#: 21389
[    13.787] (II) fglrx(0): Year: 2007  Week: 1
[    13.787] (II) fglrx(0): EDID Version: 1.3
[    13.787] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    13.787] (II) fglrx(0): Sync:  Separate
[    13.787] (II) fglrx(0): Max Image Size [cm]: horiz.: 30  vert.: 23
[    13.787] (II) fglrx(0): Gamma: 2.37
[    13.787] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    13.787] (II) fglrx(0): First detailed timing not preferred mode in violation of standard!
[    13.787] (II) fglrx(0): redX: 0.634 redY: 0.339   greenX: 0.285 greenY: 0.587
[    13.787] (II) fglrx(0): blueX: 0.144 blueY: 0.075   whiteX: 0.310 whiteY: 0.330
[    13.787] (II) fglrx(0): Supported established timings:
[    13.787] (II) fglrx(0): 640x480@60Hz
[    13.787] (II) fglrx(0): 640x480@72Hz
[    13.787] (II) fglrx(0): 640x480@75Hz
[    13.787] (II) fglrx(0): 800x600@56Hz
[    13.787] (II) fglrx(0): 1024x768@60Hz
[    13.787] (II) fglrx(0): Manufacturer's mask: 0
[    13.787] (II) fglrx(0): Supported standard timings:
[    13.787] (II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 61  vid: 16809
[    13.787] (II) fglrx(0): Supported detailed timing:
[    13.787] (II) fglrx(0): clock: 78.8 MHz   Image Size:  304 x 228 mm
[    13.788] (II) fglrx(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
[    13.788] (II) fglrx(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
[    13.788] (II) fglrx(0): Serial No: 0132544821389
[    13.788] (II) fglrx(0): Monitor name: SANCY
[    13.788] (II) fglrx(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 60 kHz, PixClock max 85 MHz
[    13.788] (II) fglrx(0): EDID (in hex):
[    13.788] (II) fglrx(0):     00ffffffffffff004c2e2d058d530000
[    13.788] (II) fglrx(0):     01110103081e1789e871d6a256499624
[    13.788] (II) fglrx(0):     134f542e0800a9410101010101010101
[    13.788] (II) fglrx(0):     010101010101c31e0020410020301060
[    13.788] (II) fglrx(0):     130030e410000018000000ff00303133
[    13.788] (II) fglrx(0):     32353434383231333839000000fc0053
[    13.788] (II) fglrx(0):     414e43590a20202020202020000000fd
[    13.788] (II) fglrx(0):     00324b1e3c08000a2020202020200094
[    13.788] (II) fglrx(0): End of Display0 EDID data --------------------
[    13.823] (II) fglrx(0): EDID for output DFP1
[    13.823] (II) fglrx(0): EDID for output CRT1
[    13.823] (II) fglrx(0): Manufacturer: SAN  Model: 52d  Serial#: 21389
[    13.823] (II) fglrx(0): Year: 2007  Week: 1
[    13.823] (II) fglrx(0): EDID Version: 1.3
[    13.823] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    13.823] (II) fglrx(0): Sync:  Separate
[    13.823] (II) fglrx(0): Max Image Size [cm]: horiz.: 30  vert.: 23
[    13.823] (II) fglrx(0): Gamma: 2.37
[    13.823] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    13.823] (II) fglrx(0): First detailed timing not preferred mode in violation of standard!
[    13.823] (II) fglrx(0): redX: 0.634 redY: 0.339   greenX: 0.285 greenY: 0.587
[    13.823] (II) fglrx(0): blueX: 0.144 blueY: 0.075   whiteX: 0.310 whiteY: 0.330
[    13.823] (II) fglrx(0): Supported established timings:
[    13.823] (II) fglrx(0): 640x480@60Hz
[    13.823] (II) fglrx(0): 640x480@72Hz
[    13.823] (II) fglrx(0): 640x480@75Hz
[    13.823] (II) fglrx(0): 800x600@56Hz
[    13.823] (II) fglrx(0): 1024x768@60Hz
[    13.823] (II) fglrx(0): Manufacturer's mask: 0
[    13.823] (II) fglrx(0): Supported standard timings:
[    13.823] (II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 61  vid: 16809
[    13.823] (II) fglrx(0): Supported detailed timing:
[    13.823] (II) fglrx(0): clock: 78.8 MHz   Image Size:  304 x 228 mm
[    13.823] (II) fglrx(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
[    13.823] (II) fglrx(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
[    13.823] (II) fglrx(0): Serial No: 0132544821389
[    13.823] (II) fglrx(0): Monitor name: SANCY
[    13.823] (II) fglrx(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 60 kHz, PixClock max 85 MHz
[    13.823] (II) fglrx(0): EDID (in hex):
[    13.823] (II) fglrx(0):     00ffffffffffff004c2e2d058d530000
[    13.823] (II) fglrx(0):     01110103081e1789e871d6a256499624
[    13.823] (II) fglrx(0):     134f542e0800a9410101010101010101
[    13.823] (II) fglrx(0):     010101010101c31e0020410020301060
[    13.823] (II) fglrx(0):     130030e410000018000000ff00303133
[    13.823] (II) fglrx(0):     32353434383231333839000000fc0053
[    13.823] (II) fglrx(0):     414e43590a20202020202020000000fd
[    13.823] (II) fglrx(0):     00324b1e3c08000a2020202020200094
[    13.823] (II) fglrx(0): Printing probed modes for output CRT1
[    13.823] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    13.823] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 -hsync -vsync (46.9 kHz)
[    13.823] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    13.823] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    13.823] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 -hsync -vsync (35.2 kHz)
[    13.823] (II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[    13.823] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
[    13.823] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 +hsync +vsync (37.9 kHz)
[    13.823] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[    13.823] (II) fglrx(0): Output DFP1 disconnected
[    13.823] (II) fglrx(0): Output CRT1 connected
[    13.823] (II) fglrx(0): Using exact sizes for initial modes
[    13.823] (II) fglrx(0): Output CRT1 using initial mode 1024x768
[    13.823] (II) fglrx(0): DPI set to (96, 96)
[    13.824] (II) fglrx(0): Adapter ATI Radeon HD 3200 Graphics has 2 configurable heads and 1 displays connected.
[    13.824] (==) fglrx(0):  PseudoColor visuals disabled
[    13.824] (II) Loading sub module "ramdac"
[    13.824] (II) LoadModule: "ramdac"
[    13.824] (II) Module "ramdac" already built-in
[    13.824] (==) fglrx(0): NoDRI = NO
[    13.824] (==) fglrx(0): Capabilities: 0x00000000
[    13.824] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    13.824] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    13.824] (==) fglrx(0): UseFastTLS=0
[    13.824] (==) fglrx(0): BlockSignalsOnLock=1
[    13.824] (--) Depth 24 pixmap format is 32 bpp
[    13.825] (EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
[    13.825] (WW) fglrx(0): ***********************************************************
[    13.825] (WW) fglrx(0): * DRI initialization failed                               *
[    13.825] (WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible *
[    13.825] (WW) fglrx(0): * 2D and 3D acceleration disabled                         *
[    13.825] (WW) fglrx(0): ***********************************************************
[    13.825] (II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x10000000
[    13.850] (II) fglrx(0): FBMM initialized for area (0,0)-(1024,8191)
[    13.850] (II) fglrx(0): FBMM auto alloc for area (0,0)-(1024,1024) (front color buffer - assumption)
[    13.850] (II) fglrx(0): Largest offscreen area available: 1024 x 7167
[    13.850] (==) fglrx(0): Backing store disabled
[    13.850] (II) Loading extension FGLRXEXTENSION
[    13.850] (**) fglrx(0): DPMS enabled
[    13.851] (II) fglrx(0): Initialized in-driver Xinerama extension
[    13.851] (WW) fglrx(0): Textured Video not supported without DRI enabled.
[    13.851] (II) LoadModule: "glesx"
[    13.851] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/glesx.so
[    13.853] (II) Module glesx: vendor="X.Org Foundation"
[    13.853]     compiled for 1.4.99.906, module version = 1.0.0
[    13.853] (II) Loading extension GLESX
[    13.853] (II) fglrx(0): GLESX enableFlags = 512
[    13.853] (II) LoadModule: "amdxmm"
[    13.853] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[    13.853] (II) Module amdxmm: vendor="X.Org Foundation"
[    13.853]     compiled for 1.4.99.906, module version = 2.0.0
[    13.853] (EE) fglrx(0): XMM failed to open CMMQS connection.(EE) fglrx(0): 
[    13.853] (EE) fglrx(0): XMM failed to initialize
[    13.853] (WW) fglrx(0): No XV video playback available
[    13.853] (II) fglrx(0): Enable composite support successfully
[    13.853] (WW) fglrx(0): Option "VendorName" is not used
[    13.853] (WW) fglrx(0): Option "ModelName" is not used
[    13.853] (==) fglrx(0): Silken mouse enabled
[    13.854] (==) fglrx(0): Using HW cursor of display infrastructure!
[    13.854] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    13.928] (--) RandR disabled
[    13.928] (II) Initializing built-in extension Generic Event Extension
[    13.928] (II) Initializing built-in extension SHAPE
[    13.928] (II) Initializing built-in extension MIT-SHM
[    13.928] (II) Initializing built-in extension XInputExtension
[    13.928] (II) Initializing built-in extension XTEST
[    13.928] (II) Initializing built-in extension BIG-REQUESTS
[    13.928] (II) Initializing built-in extension SYNC
[    13.928] (II) Initializing built-in extension XKEYBOARD
[    13.928] (II) Initializing built-in extension XC-MISC
[    13.928] (II) Initializing built-in extension SECURITY
[    13.928] (II) Initializing built-in extension XINERAMA
[    13.928] (II) Initializing built-in extension XFIXES
[    13.928] (II) Initializing built-in extension RENDER
[    13.928] (II) Initializing built-in extension RANDR
[    13.928] (II) Initializing built-in extension COMPOSITE
[    13.928] (II) Initializing built-in extension DAMAGE
[    13.928] (II) Initializing built-in extension GESTURE
[    13.931] (II) AIGLX: Screen 0 is not DRI capable
[    13.932] [glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!
[    13.938] (II) fglrx(0): Setting screen physical size to 270 x 203
[    13.961] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.971] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    13.971] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.971] (II) LoadModule: "evdev"
[    13.971] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.972] (II) Module evdev: vendor="X.Org Foundation"
[    13.972]     compiled for 1.10.2, module version = 2.6.0
[    13.972]     Module class: X.Org XInput Driver
[    13.972]     ABI class: X.Org XInput driver, version 12.3
[    13.973] (II) Using input driver 'evdev' for 'Power Button'
[    13.973] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.973] (**) Power Button: always reports core events
[    13.973] (**) Power Button: Device: "/dev/input/event1"
[    13.973] (--) Power Button: Found keys
[    13.973] (II) Power Button: Configuring as keyboard
[    13.973] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    13.973] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.973] (**) Option "xkb_rules" "evdev"
[    13.973] (**) Option "xkb_model" "pc105"
[    13.973] (**) Option "xkb_layout" "us"
[    13.975] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    13.975] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.975] (II) Using input driver 'evdev' for 'Power Button'
[    13.975] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.976] (**) Power Button: always reports core events
[    13.976] (**) Power Button: Device: "/dev/input/event0"
[    13.976] (--) Power Button: Found keys
[    13.976] (II) Power Button: Configuring as keyboard
[    13.976] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    13.976] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.976] (**) Option "xkb_rules" "evdev"
[    13.976] (**) Option "xkb_model" "pc105"
[    13.976] (**) Option "xkb_layout" "us"
[    13.986] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event3)
[    13.986] (II) No input driver/identifier specified (ignoring)
[    13.988] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    13.988] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    13.988] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    13.988] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.988] (**) AT Translated Set 2 keyboard: always reports core events
[    13.988] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    13.988] (--) AT Translated Set 2 keyboard: Found keys
[    13.988] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    13.988] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    13.988] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    13.988] (**) Option "xkb_rules" "evdev"
[    13.988] (**) Option "xkb_model" "pc105"
[    13.988] (**) Option "xkb_layout" "us"
[    13.989] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/event4)
[    13.989] (**) ImExPS/2 Generic Explorer Mouse: Applying InputClass "evdev pointer catchall"
[    13.989] (II) Using input driver 'evdev' for 'ImExPS/2 Generic Explorer Mouse'
[    13.989] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.989] (**) ImExPS/2 Generic Explorer Mouse: always reports core events
[    13.989] (**) ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event4"
[    13.989] (--) ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
[    13.989] (--) ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
[    13.989] (--) ImExPS/2 Generic Explorer Mouse: Found relative axes
[    13.989] (--) ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
[    13.989] (II) ImExPS/2 Generic Explorer Mouse: Configuring as mouse
[    13.989] (II) ImExPS/2 Generic Explorer Mouse: Adding scrollwheel support
[    13.989] (**) ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
[    13.989] (**) ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.989] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event4"
[    13.989] (II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE)
[    13.990] (II) ImExPS/2 Generic Explorer Mouse: initialized for relative axes.
[    13.990] (**) ImExPS/2 Generic Explorer Mouse: (accel) keeping acceleration scheme 1
[    13.990] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration profile 0
[    13.990] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration factor: 2.000
[    13.990] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration threshold: 4
[    13.990] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/mouse0)
[    13.990] (II) No input driver/identifier specified (ignoring)
[    14.019] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    14.329] (II) fglrx(0): EDID vendor "SAN", prod id 1325
[    14.329] (II) fglrx(0): Using EDID range info for horizontal sync
[    14.329] (II) fglrx(0): Using EDID range info for vertical refresh
[    14.329] (II) fglrx(0): Printing DDC gathered Modelines:
[    14.329] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    14.329] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    14.329] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    14.329] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    14.329] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.329] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.329] (II) fglrx(0): Modeline "1600x1200"x61.0  163.78  1600 1704 1880 2160  1200 1201 1204 1243 -hsync +vsync (75.8 kHz)
[    15.047] (II) fglrx(0): EDID vendor "SAN", prod id 1325
[    15.047] (II) fglrx(0): Using hsync ranges from config file
[    15.047] (II) fglrx(0): Using vrefresh ranges from config file
[    15.047] (II) fglrx(0): Printing DDC gathered Modelines:
[    15.047] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    15.047] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    15.047] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    15.047] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    15.047] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.047] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    15.047] (II) fglrx(0): Modeline "1600x1200"x61.0  163.78  1600 1704 1880 2160  1200 1201 1204 1243 -hsync +vsync (75.8 kHz)
[    15.777] (II) fglrx(0): EDID vendor "SAN", prod id 1325
[    15.777] (II) fglrx(0): Using hsync ranges from config file
[    15.778] (II) fglrx(0): Using vrefresh ranges from config file
[    15.778] (II) fglrx(0): Printing DDC gathered Modelines:
[    15.778] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    15.778] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    15.778] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    15.778] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    15.778] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.778] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    15.778] (II) fglrx(0): Modeline "1600x1200"x61.0  163.78  1600 1704 1880 2160  1200 1201 1204 1243 -hsync +vsync (75.8 kHz)
[    18.677] (II) fglrx(0): EDID vendor "SAN", prod id 1325
[    18.677] (II) fglrx(0): Using hsync ranges from config file
[    18.677] (II) fglrx(0): Using vrefresh ranges from config file
[    18.677] (II) fglrx(0): Printing DDC gathered Modelines:
[    18.677] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    18.677] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.677] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.677] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    18.677] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.677] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.677] (II) fglrx(0): Modeline "1600x1200"x61.0  163.78  1600 1704 1880 2160  1200 1201 1204 1243 -hsync +vsync (75.8 kHz)
[    26.977] (II) fglrx(0): EDID vendor "SAN", prod id 1325
[    26.977] (II) fglrx(0): Using hsync ranges from config file
[    26.977] (II) fglrx(0): Using vrefresh ranges from config file
[    26.977] (II) fglrx(0): Printing DDC gathered Modelines:
[    26.977] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    26.977] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    26.977] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    26.977] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    26.977] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    26.977] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    26.977] (II) fglrx(0): Modeline "1600x1200"x61.0  163.78  1600 1704 1880 2160  1200 1201 1204 1243 -hsync +vsync (75.8 kHz)
[    27.478] (II) fglrx(0): EDID vendor "SAN", prod id 1325
[    27.479] (II) fglrx(0): Using hsync ranges from config file
[    27.479] (II) fglrx(0): Using vrefresh ranges from config file
[    27.479] (II) fglrx(0): Printing DDC gathered Modelines:
[    27.479] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    27.479] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    27.479] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    27.479] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    27.479] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.479] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.479] (II) fglrx(0): Modeline "1600x1200"x61.0  163.78  1600 1704 1880 2160  1200 1201 1204 1243 -hsync +vsync (75.8 kHz)
[    27.886] (II) fglrx(0): EDID vendor "SAN", prod id 1325
[    27.886] (II) fglrx(0): Using hsync ranges from config file
[    27.886] (II) fglrx(0): Using vrefresh ranges from config file
[    27.886] (II) fglrx(0): Printing DDC gathered Modelines:
[    27.886] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    27.886] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    27.886] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    27.886] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    27.886] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.886] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.886] (II) fglrx(0): Modeline "1600x1200"x61.0  163.78  1600 1704 1880 2160  1200 1201 1204 1243 -hsync +vsync (75.8 kHz)
[    27.923] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[    33.486] (II) fglrx(0): EDID vendor "SAN", prod id 1325
[    33.486] (II) fglrx(0): Using hsync ranges from config file
[    33.486] (II) fglrx(0): Using vrefresh ranges from config file
[    33.486] (II) fglrx(0): Printing DDC gathered Modelines:
[    33.486] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    33.486] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    33.486] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    33.486] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    33.486] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    33.486] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    33.486] (II) fglrx(0): Modeline "1600x1200"x61.0  163.78  1600 1704 1880 2160  1200 1201 1204 1243 -hsync +vsync (75.8 kHz)
[   975.075] (II) fglrx(0): EDID vendor "SAN", prod id 1325
[   975.075] (II) fglrx(0): Using hsync ranges from config file
[   975.075] (II) fglrx(0): Using vrefresh ranges from config file
[   975.075] (II) fglrx(0): Printing DDC gathered Modelines:
[   975.075] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[   975.075] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   975.075] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   975.075] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   975.075] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   975.075] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   975.075] (II) fglrx(0): Modeline "1600x1200"x61.0  163.78  1600 1704 1880 2160  1200 1201 1204 1243 -hsync +vsync (75.8 kHz)
[  8734.914] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[ 23566.420] (II) fglrx(0): EDID vendor "SAN", prod id 1325
[ 23566.420] (II) fglrx(0): Using hsync ranges from config file
[ 23566.420] (II) fglrx(0): Using vrefresh ranges from config file
[ 23566.420] (II) fglrx(0): Printing DDC gathered Modelines:
[ 23566.420] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[ 23566.420] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[ 23566.420] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[ 23566.420] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[ 23566.421] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[ 23566.421] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[ 23566.421] (II) fglrx(0): Modeline "1600x1200"x61.0  163.78  1600 1704 1880 2160  1200 1201 1204 1243 -hsync +vsync (75.8 kHz)
[ 24826.708] (II) fglrx(0): EDID vendor "SAN", prod id 1325
[ 24826.708] (II) fglrx(0): Using hsync ranges from config file
[ 24826.708] (II) fglrx(0): Using vrefresh ranges from config file
[ 24826.708] (II) fglrx(0): Printing DDC gathered Modelines:
[ 24826.708] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[ 24826.708] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[ 24826.708] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[ 24826.708] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[ 24826.708] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[ 24826.708] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[ 24826.708] (II) fglrx(0): Modeline "1600x1200"x61.0  163.78  1600 1704 1880 2160  1200 1201 1204 1243 -hsync +vsync (75.8 kHz)
[ 24858.086] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[ 26120.748] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[ 26178.085] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[ 26671.446] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[ 26688.085] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[ 26689.945] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[ 26718.096] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[ 26753.641] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[ 26778.083] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[ 26878.143] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[ 26904.085] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[ 27031.480] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[ 27057.086] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[ 27194.703] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm


```

Thank you for Replying
Glenn.

---

### Post by Yellow Pasque on 2012-04-22
> 13.825] (WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible

What happens when you try to manually load the module with this command?
```
sudo modprobe -v fglrx
```

---

### Post by Senior_Buckethead on 2012-04-22
Ok, here it is:

```

glenn@acer:~$ sudo modprobe -v fglrx
[sudo] password for glenn: 
FATAL: Module fglrx not found.
glenn@acer:~$ 

```

Well now thats a surprise, I followed the install instructions. Very odd.

---

### Post by Yellow Pasque on 2012-04-23
There has to be some reason why it's not installing the kernel module. Maybe look in /var/lib/dkms/fglrx

---

### Post by Senior_Buckethead on 2012-04-23
```

glenn@acer:~$  cd /var/lib/dkms/fglrx
glenn@acer:/var/lib/dkms/fglrx$ ls
8.951
glenn@acer:/var/lib/dkms/fglrx$ cd 8.951
glenn@acer:/var/lib/dkms/fglrx/8.951$ ls
build  source
glenn@acer:/var/lib/dkms/fglrx/8.951$ cd build
glenn@acer:/var/lib/dkms/fglrx/8.951/build$ ls
2.6.x              firegl_public.c  kcl_debug.c  kcl_iommu.h     kcl_wait.h
dkms.conf          firegl_public.h  kcl_debug.h  kcl_osconfig.h  libfglrx_ip.a
drm_compat.h       kcl_acpi.c       kcl.h        kcl_pci.c       make.log
drm.h              kcl_acpi.h       kcl_io.c     kcl_pci.h       make.sh
drm_os_linux.h     kcl_agp.c        kcl_ioctl.c  kcl_str.c       make.sh.log
drmP.h             kcl_agp.h        kcl_ioctl.h  kcl_str.h       patches
drm_proc.h         kcl.c            kcl_io.h     kcl_type.h
fglrxko_pci_ids.h  kcl_config.h     kcl_iommu.c  kcl_wait.c
glenn@acer:/var/lib/dkms/fglrx/8.951/build$ 

```Ok, where to from here?

Glenn.

---

### Post by Yellow Pasque on 2012-04-23
> **Senior_Buckethead said:**
> ```

glenn@acer:~$  cd /var/lib/dkms/fglrx
glenn@acer:/var/lib/dkms/fglrx$ ls
8.951
glenn@acer:/var/lib/dkms/fglrx$ cd 8.951
glenn@acer:/var/lib/dkms/fglrx/8.951$ ls
build  source
glenn@acer:/var/lib/dkms/fglrx/8.951$ cd build
glenn@acer:/var/lib/dkms/fglrx/8.951/build$ ls
2.6.x              firegl_public.c  kcl_debug.c  kcl_iommu.h     kcl_wait.h
dkms.conf          firegl_public.h  kcl_debug.h  kcl_osconfig.h  libfglrx_ip.a
drm_compat.h       kcl_acpi.c       kcl.h        kcl_pci.c       make.log
drm.h              kcl_acpi.h       kcl_io.c     kcl_pci.h       make.sh
drm_os_linux.h     kcl_agp.c        kcl_ioctl.c  kcl_str.c       make.sh.log
drmP.h             kcl_agp.h        kcl_ioctl.h  kcl_str.h       patches
drm_proc.h         kcl.c            kcl_io.h     kcl_type.h
fglrxko_pci_ids.h  kcl_config.h     kcl_iommu.c  kcl_wait.c
glenn@acer:/var/lib/dkms/fglrx/8.951/build$ 

```Ok, where to from here?

Glenn.
Look at make.log?

---

### Post by Senior_Buckethead on 2012-04-24
Here is the make.log from /var/lib/dkms/fglrx/8.951/build/

```

DKMS make.log for fglrx-8.951 for kernel 3.0.0-19-generic (i686)
Sun Apr 22 13:41:24 NZST 2012
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers
make -C /lib/modules/3.0.0-19-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.951/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-19-generic'
  CC [M]  /var/lib/dkms/fglrx/8.951/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.951/build/2.6.x/firegl_public.c: In function ‘KCL_fpu_begin’:
/var/lib/dkms/fglrx/8.951/build/2.6.x/firegl_public.c:5804:28: error: ‘TS_USEDFPU’ undeclared (first use in this function)
/var/lib/dkms/fglrx/8.951/build/2.6.x/firegl_public.c:5804:28: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/var/lib/dkms/fglrx/8.951/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.951/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-19-generic'
make: *** [kmod_build] Error 2
build failed with return value 2

```It seems to go wrong here:

```

/var/lib/dkms/fglrx/8.951/build/2.6.x/firegl_public.c:5804:28: error: ‘TS_USEDFPU’ undeclared (first use in this function)
/var/lib/dkms/fglrx/8.951/build/2.6.x/firegl_public.c:5804:28: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/var/lib/dkms/fglrx/8.951/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.951/build/2.6.x] Error 2

```Can someone shed some light on what went wrong?

---

### Post by Yellow Pasque on 2012-04-24
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/947871](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/947871)

---

### Post by Senior_Buckethead on 2012-04-24
Ok, its now a known bug. I just hope the boys and girls out there can figure a fix, because I'm relying on my motherboard on-board video, and its not the same.

---


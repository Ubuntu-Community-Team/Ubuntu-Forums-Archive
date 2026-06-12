---
title: "Screen resolution is random every boot"
date: 2012-04-24
forum: Multimedia Software
---

### Post by fskreuz on 2012-04-24
I recently returned to using Ubuntu (Lubuntu 11.10 specifically) and currently I am having problems with my screen resolution. My monitor has a resolution of 1280x1024 but at times, it boots to 1024x768. I tried using xrandr to set my screen. When it boots to 1280x1024, running xrand lists a lot of modes supported by the monitor. But when it boots to 1024x768, xrandr lists only generic screen sizes, maximum is 1024x768. I also don't have an xorg.conf since they say it doesn't exist anymore in newer Ubuntu and the system relies on auto hardware detection.

when I also run xrandr or when I add a new mode, I get this error:
```
xrandr: Failed to get size of gamma for output default
```when I try to build xorg.conf using Xorg -configure (in root mode):
```
Number of created screens does not match number of detected devices. Configuration failed
```my xorg log, currently taken after a boot with 1280x1024:

```

[    26.957] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    26.957] X Protocol Version 11, Revision 0
[    26.957] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    26.957] Current Operating System: Linux ubuntu 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686
[    26.957] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=0e665365-03f9-41e6-b61e-340a067c68b1 ro splash quiet vt.handoff=7
[    26.957] Build Date: 19 October 2011  05:09:41AM
[    26.957] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    26.957] Current version of pixman: 0.22.2
[    26.957]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    26.957] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.958] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 24 18:49:00 2012
[    26.958] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.959] (==) No Layout section.  Using the first Screen section.
[    26.959] (==) No screen section available. Using defaults.
[    26.959] (**) |-->Screen "Default Screen Section" (0)
[    26.959] (**) |   |-->Monitor "<default monitor>"
[    26.959] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    26.972] (==) Automatically adding devices
[    26.972] (==) Automatically enabling devices
[    26.972] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.972]     Entry deleted from font path.
[    26.972] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    26.972]     Entry deleted from font path.
[    26.972] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    26.972]     Entry deleted from font path.
[    26.972] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    26.972] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.972] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.973] (II) Loader magic: 0x823ada0
[    26.973] (II) Module ABI versions:
[    26.973]     X.Org ANSI C Emulation: 0.4
[    26.973]     X.Org Video Driver: 10.0
[    26.973]     X.Org XInput driver : 12.3
[    26.973]     X.Org Server Extension : 5.0
[    26.974] (--) PCI:*(0:1:0:0) 1002:5446:1002:0408 rev 0, Mem @ 0xf8000000/67108864, 0xff8fc000/16384, I/O @ 0x0000ec00/256, BIOS @ 0x????????/131072
[    26.974] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    26.974] (II) LoadModule: "extmod"
[    26.988] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    26.989] (II) Module extmod: vendor="X.Org Foundation"
[    26.989]     compiled for 1.10.4, module version = 1.0.0
[    26.989]     Module class: X.Org Server Extension
[    26.989]     ABI class: X.Org Server Extension, version 5.0
[    26.989] (II) Loading extension MIT-SCREEN-SAVER
[    26.989] (II) Loading extension XFree86-VidModeExtension
[    26.989] (II) Loading extension XFree86-DGA
[    26.989] (II) Loading extension DPMS
[    26.989] (II) Loading extension XVideo
[    26.989] (II) Loading extension XVideo-MotionCompensation
[    26.989] (II) Loading extension X-Resource
[    26.989] (II) LoadModule: "dbe"
[    26.990] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    26.990] (II) Module dbe: vendor="X.Org Foundation"
[    26.990]     compiled for 1.10.4, module version = 1.0.0
[    26.990]     Module class: X.Org Server Extension
[    26.990]     ABI class: X.Org Server Extension, version 5.0
[    26.990] (II) Loading extension DOUBLE-BUFFER
[    26.990] (II) LoadModule: "glx"
[    26.991] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    26.991] (II) Module glx: vendor="X.Org Foundation"
[    26.991]     compiled for 1.10.4, module version = 1.0.0
[    26.991]     ABI class: X.Org Server Extension, version 5.0
[    26.991] (==) AIGLX enabled
[    26.991] (II) Loading extension GLX
[    26.991] (II) LoadModule: "record"
[    26.998] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    26.998] (II) Module record: vendor="X.Org Foundation"
[    26.998]     compiled for 1.10.4, module version = 1.13.0
[    26.998]     Module class: X.Org Server Extension
[    26.998]     ABI class: X.Org Server Extension, version 5.0
[    26.998] (II) Loading extension RECORD
[    26.998] (II) LoadModule: "dri"
[    26.999] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    27.002] (II) Module dri: vendor="X.Org Foundation"
[    27.002]     compiled for 1.10.4, module version = 1.0.0
[    27.002]     ABI class: X.Org Server Extension, version 5.0
[    27.002] (II) Loading extension XFree86-DRI
[    27.002] (II) LoadModule: "dri2"
[    27.003] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    27.003] (II) Module dri2: vendor="X.Org Foundation"
[    27.003]     compiled for 1.10.4, module version = 1.2.0
[    27.004]     ABI class: X.Org Server Extension, version 5.0
[    27.004] (II) Loading extension DRI2
[    27.004] (==) Matched fglrx as autoconfigured driver 0
[    27.004] (==) Matched ati as autoconfigured driver 1
[    27.004] (==) Matched vesa as autoconfigured driver 2
[    27.004] (==) Matched fbdev as autoconfigured driver 3
[    27.004] (==) Assigned the driver to the xf86ConfigLayout
[    27.004] (II) LoadModule: "fglrx"
[    27.005] (WW) Warning, couldn't open module fglrx
[    27.005] (II) UnloadModule: "fglrx"
[    27.005] (II) Unloading fglrx
[    27.005] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    27.005] (II) LoadModule: "ati"
[    27.006] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    27.006] (II) Module ati: vendor="X.Org Foundation"
[    27.006]     compiled for 1.10.2.902, module version = 6.14.99
[    27.006]     Module class: X.Org Video Driver
[    27.006]     ABI class: X.Org Video Driver, version 10.0
[    27.006] (II) LoadModule: "r128"
[    27.020] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[    27.020] (II) Module r128: vendor="X.Org Foundation"
[    27.020]     compiled for 1.10.1, module version = 6.8.1
[    27.020]     Module class: X.Org Video Driver
[    27.020]     ABI class: X.Org Video Driver, version 10.0
[    27.020] (II) LoadModule: "vesa"
[    27.021] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    27.021] (II) Module vesa: vendor="X.Org Foundation"
[    27.021]     compiled for 1.10.2, module version = 2.3.0
[    27.021]     Module class: X.Org Video Driver
[    27.021]     ABI class: X.Org Video Driver, version 10.0
[    27.021] (II) LoadModule: "fbdev"
[    27.022] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    27.022] (II) Module fbdev: vendor="X.Org Foundation"
[    27.022]     compiled for 1.10.0, module version = 0.4.2
[    27.022]     ABI class: X.Org Video Driver, version 10.0
[    27.022] (II) R128: Driver for ATI Rage 128 chipsets:
    ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
    ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
    ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
    ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
    ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
    ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
    ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
    ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
    ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
    ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
    ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
    ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
    ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
    ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
    ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
    ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
    ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
    ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
    ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
    ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
    ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
    ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
    ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
    ATI Rage 128 Pro ULTRA TU (AGP?)
[    27.023] (II) VESA: driver for VESA chipsets: vesa
[    27.023] (II) FBDEV: driver for framebuffer: fbdev
[    27.023] (++) using VT number 7

[    27.024] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[    27.024] (WW) Falling back to old probe method for vesa
[    27.024] (WW) Falling back to old probe method for fbdev
[    27.024] (II) Loading sub module "fbdevhw"
[    27.024] (II) LoadModule: "fbdevhw"
[    27.024] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    27.025] (II) Module fbdevhw: vendor="X.Org Foundation"
[    27.025]     compiled for 1.10.4, module version = 0.0.2
[    27.025]     ABI class: X.Org Video Driver, version 10.0
[    27.025] (II) R128(0): PCI bus 1 card 0 func 0
[    27.025] (II) R128(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    27.025] (==) R128(0): Depth 24, (--) framebuffer bpp 32
[    27.025] (II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    27.025] (==) R128(0): Default visual is TrueColor
[    27.025] (II) Loading sub module "vgahw"
[    27.025] (II) LoadModule: "vgahw"
[    27.026] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    27.026] (II) Module vgahw: vendor="X.Org Foundation"
[    27.026]     compiled for 1.10.4, module version = 0.1.0
[    27.026]     ABI class: X.Org Video Driver, version 10.0
[    27.026] (II) R128(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    27.026] (==) R128(0): RGB weight 888
[    27.026] (II) R128(0): Using 8 bits per RGB (8 bit DAC)
[    27.027] (II) Loading sub module "int10"
[    27.027] (II) LoadModule: "int10"
[    27.027] (II) Loading /usr/lib/xorg/modules/libint10.so
[    27.027] (II) Module int10: vendor="X.Org Foundation"
[    27.032]     compiled for 1.10.4, module version = 1.0.0
[    27.032]     ABI class: X.Org Video Driver, version 10.0
[    27.032] (II) R128(0): initializing int10
[    27.033] (II) R128(0): Primary V_BIOS segment is: 0xc000
[    27.033] (--) R128(0): Chipset: "ATI Rage 128 Pro ULTRA TF (AGP)" (ChipID = 0x5446)
[    27.033] (--) R128(0): Linear framebuffer at 0xf8000000
[    27.033] (--) R128(0): MMIO registers at 0xff8fc000
[    27.034] (--) R128(0): VideoRAM: 16384 kByte (128-bit SDR SGRAM 1:1)
[    27.034] (**) R128(0): Using external CRT for display
[    27.099] (II) R128(0): Primary Display == Type 3
[    27.099] (WW) R128(0): Can't determine panel dimensions, and none specified.
    Disabling programming of FP registers.
[    27.099] (II) R128(0): PLL parameters: rf=2950 rd=65 min=12500 max=35000; xclk=13000
[    27.099] (II) Loading sub module "ddc"
[    27.099] (II) LoadModule: "ddc"
[    27.099] (II) Module "ddc" already built-in
[    27.099] (II) Loading sub module "vbe"
[    27.099] (II) LoadModule: "vbe"
[    27.104] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    27.105] (II) Module vbe: vendor="X.Org Foundation"
[    27.105]     compiled for 1.10.4, module version = 1.1.0
[    27.105]     ABI class: X.Org Video Driver, version 10.0
[    27.105] (II) R128(0): VESA BIOS detected
[    27.105] (II) R128(0): VESA VBE Version 2.0
[    27.105] (II) R128(0): VESA VBE Total Mem: 16384 kB
[    27.105] (II) R128(0): VESA VBE OEM: ATI RAGE128
[    27.105] (II) R128(0): VESA VBE OEM Software Rev: 1.0
[    27.105] (II) R128(0): VESA VBE OEM Vendor: ATI Technologies Inc.
[    27.105] (II) R128(0): VESA VBE OEM Product: R128
[    27.105] (II) R128(0): VESA VBE OEM Product Rev: 01.00
[    27.105] (II) Loading sub module "ddc"
[    27.105] (II) LoadModule: "ddc"
[    27.105] (II) Module "ddc" already built-in
[    27.286] (II) R128(0): VESA VBE DDC supported
[    27.286] (II) R128(0): VESA VBE DDC Level 2
[    27.286] (II) R128(0): VESA VBE DDC transfer in appr. 2 sec.
[    28.829] (II) R128(0): VESA VBE DDC read successfully
[    28.829] (II) R128(0): Manufacturer: RDS  Model: 1763  Serial#: 25007444
[    28.829] (II) R128(0): Year: 2002  Week: 25
[    28.829] (II) R128(0): EDID Version: 1.3
[    28.829] (II) R128(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    28.829] (II) R128(0): Sync:  Separate  Composite  SyncOnGreenSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
[    28.829] (II) R128(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    28.829] (II) R128(0): Gamma: 2.50
[    28.829] (II) R128(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    28.829] (II) R128(0): First detailed timing not preferred mode in violation of standard!
[    28.829] (II) R128(0): redX: 0.634 redY: 0.354   greenX: 0.304 greenY: 0.580
[    28.829] (II) R128(0): blueX: 0.143 blueY: 0.102   whiteX: 0.318 whiteY: 0.339
[    28.829] (II) R128(0): Supported established timings:
[    28.829] (II) R128(0): 720x400@88Hz
[    28.829] (II) R128(0): 640x480@60Hz
[    28.829] (II) R128(0): 640x480@67Hz
[    28.829] (II) R128(0): 640x480@72Hz
[    28.829] (II) R128(0): 640x480@75Hz
[    28.829] (II) R128(0): 800x600@56Hz
[    28.829] (II) R128(0): 800x600@60Hz
[    28.829] (II) R128(0): 800x600@72Hz
[    28.829] (II) R128(0): 800x600@75Hz
[    28.829] (II) R128(0): 832x624@75Hz
[    28.829] (II) R128(0): 1024x768@87Hz (interlaced)
[    28.829] (II) R128(0): 1024x768@60Hz
[    28.829] (II) R128(0): 1024x768@70Hz
[    28.829] (II) R128(0): 1024x768@75Hz
[    28.829] (II) R128(0): 1280x1024@75Hz
[    28.829] (II) R128(0): 1152x864@75Hz
[    28.829] (II) R128(0): Manufacturer's mask: 7F
[    28.829] (II) R128(0): Supported standard timings:
[    28.829] (II) R128(0): #0: hsize: 2288  vsize 1287  refresh: 123  vid: 65535
[    28.829] (II) R128(0): #1: hsize: 2288  vsize 1287  refresh: 123  vid: 65535
[    28.830] (II) R128(0): #2: hsize: 2288  vsize 1287  refresh: 123  vid: 65535
[    28.830] (II) R128(0): #3: hsize: 2288  vsize 1287  refresh: 123  vid: 65535
[    28.830] (II) R128(0): #4: hsize: 2288  vsize 1287  refresh: 123  vid: 65535
[    28.830] (II) R128(0): #5: hsize: 2288  vsize 1287  refresh: 123  vid: 65535
[    28.830] (II) R128(0): #6: hsize: 2288  vsize 1287  refresh: 123  vid: 65535
[    28.830] (II) R128(0): #7: hsize: 2288  vsize 1287  refresh: 123  vid: 65535
[    28.830] (II) R128(0): Supported detailed timing:
[    28.830] (II) R128(0): clock: 655.4 MHz   Image Size:  4095 x 4095 mm
[    28.830] (II) R128(0): h_active: 4095  h_sync: 5118  h_sync_end 6141 h_blank_end 8190 h_border: 255
[    28.830] (II) R128(0): v_active: 4095  v_sync: 4158  v_sync_end 4221 v_blanking: 8190 v_border: 255
[    28.830] (II) R128(0): Stereo: left channel on sync
[    28.830] side-by-side interleaved(II) R128(0): Supported detailed timing:
[    28.830] (II) R128(0): clock: 655.4 MHz   Image Size:  4095 x 4095 mm
[    28.830] (II) R128(0): h_active: 4095  h_sync: 5118  h_sync_end 6141 h_blank_end 8190 h_border: 255
[    28.830] (II) R128(0): v_active: 4095  v_sync: 4158  v_sync_end 4221 v_blanking: 8190 v_border: 255
[    28.830] (II) R128(0): Stereo: left channel on sync
[    28.830] side-by-side interleaved(II) R128(0): Supported detailed timing:
[    28.830] (II) R128(0): clock: 655.4 MHz   Image Size:  4095 x 4095 mm
[    28.830] (II) R128(0): h_active: 4095  h_sync: 5118  h_sync_end 6141 h_blank_end 8190 h_border: 255
[    28.830] (II) R128(0): v_active: 4095  v_sync: 4158  v_sync_end 4221 v_blanking: 8190 v_border: 255
[    28.830] (II) R128(0): Stereo: left channel on sync
[    28.830] side-by-side interleaved(II) R128(0): Supported detailed timing:
[    28.830] (II) R128(0): clock: 655.4 MHz   Image Size:  4095 x 4095 mm
[    28.830] (II) R128(0): h_active: 4095  h_sync: 5118  h_sync_end 6141 h_blank_end 8190 h_border: 255
[    28.830] (II) R128(0): v_active: 4095  v_sync: 4158  v_sync_end 4221 v_blanking: 8190 v_border: 255
[    28.830] (II) R128(0): Stereo: left channel on sync
[    28.830] side-by-side interleaved(II) R128(0): Number of EDID sections to follow: -1
[    28.830] (II) R128(0): EDID (in hex):
[    28.830] (II) R128(0):     00ffffffffffff004893631754957d01
[    28.830] (II) R128(0):     190c01030f221b96e86e8ba25a4d9424
[    28.830] (II) R128(0):     1a51567fffffffffffffffffffffffff
[    28.831] (II) R128(0):     ffffffffffffffffffffffffffffffff
[    28.831] (II) R128(0):     ffffffffffffffffffffffffffffffff
[    28.831] (II) R128(0):     ffffffffffffffffffffffffffffffff
[    28.831] (II) R128(0):     ffffffffffffffffffffffffffffffff
[    28.831] (II) R128(0):     ffffffffffffffffffffffffffffffff
[    28.831] (II) R128(0): EDID vendor "RDS", prod id 5987
[    28.831] (II) R128(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[    28.831] (II) R128(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[    28.831] (II) R128(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[    28.831] (II) R128(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[    28.831] (II) R128(0): Printing DDC gathered Modelines:
[    28.831] (II) R128(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    28.831] (II) R128(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    28.831] (II) R128(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    28.831] (II) R128(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    28.831] (II) R128(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    28.831] (II) R128(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    28.831] (II) R128(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
[    28.831] (II) R128(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    28.831] (II) R128(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    28.831] (II) R128(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    28.831] (II) R128(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    28.831] (II) R128(0): Modeline "1024x768i"x0.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
[    28.831] (II) R128(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    28.831] (II) R128(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    28.831] (II) R128(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    28.831] (II) R128(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    28.831] (II) R128(0): Modeline "2288x1287"x123.0  540.84  2288 2480 2736 3184  1287 1288 1291 1381 -hsync +vsync (169.9 kHz)
[    28.832] (==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
[    28.835] (II) Loading sub module "i2c"
[    28.835] (II) LoadModule: "i2c"
[    28.835] (II) Module "i2c" already built-in
[    28.836] (II) R128(0): I2C bus "DDC" initialized.
[    28.836] (II) R128(0): I2C device "DDC:ddc2" registered at address 0xA0.
[    28.839] (EE) R128(0): No DFP detected
[    28.843] (II) R128(0): <default monitor>: Using hsync range of 31.47-169.86 kHz
[    28.843] (II) R128(0): <default monitor>: Using vrefresh range of 43.48-123.00 Hz
[    28.843] (II) R128(0): Estimated virtual size for aspect ratio 1.2593 is 1280x1024
[    28.843] (II) R128(0): Clock range:  12.50 to 350.00 MHz
[    28.844] (II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1792x1344" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1792x1344" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1856x1392" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1856x1392" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1920x1440" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1920x1440" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1360x768" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1360x768" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1440x900" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1600x1024" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
[    28.844] (II) R128(0): Not using default mode "1920x1080" (width too large for virtual size)
[    28.845] (II) R128(0): Not using default mode "1920x1200" (width too large for virtual size)
[    28.845] (II) R128(0): Not using default mode "1920x1440" (width too large for virtual size)
[    28.845] (II) R128(0): Not using default mode "2048x1536" (width too large for virtual size)
[    28.845] (II) R128(0): Not using default mode "2048x1536" (width too large for virtual size)
[    28.847] (II) R128(0): Not using default mode "2048x1536" (width too large for virtual size)
[    28.847] (II) R128(0): Not using driver mode "2288x1287" (width too large for virtual size)
[    28.849] (--) R128(0): Virtual size is 1280x1024 (pitch 1280)
[    28.849] (**) R128(0): *Driver mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
[    28.849] (II) R128(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    28.849] (**) R128(0): *Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
[    28.849] (II) R128(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
[    28.849] (**) R128(0): *Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
[    28.849] (II) R128(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    28.849] (**) R128(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
[    28.849] (II) R128(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    28.849] (**) R128(0): *Default mode "1280x960": 148.5 MHz, 85.9 kHz, 85.0 Hz
[    28.849] (II) R128(0): Modeline "1280x960"x85.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
[    28.849] (**) R128(0): *Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
[    28.850] (II) R128(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    28.850] (**) R128(0): *Driver mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
[    28.850] (II) R128(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    28.850] (**) R128(0): *Default mode "1152x864": 143.5 MHz, 91.5 kHz, 100.0 Hz
[    28.850] (II) R128(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 -hsync +vsync (91.5 kHz)
[    28.850] (**) R128(0): *Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
[    28.850] (II) R128(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
[    28.850] (**) R128(0): *Default mode "1152x864": 119.7 MHz, 77.1 kHz, 85.0 Hz
[    28.850] (II) R128(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
[    28.850] (**) R128(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
[    28.850] (II) R128(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    28.850] (**) R128(0): *Default mode "1152x864": 105.0 MHz, 67.6 kHz, 75.0 Hz
[    28.850] (II) R128(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
[    28.850] (**) R128(0): *Default mode "1152x864": 96.8 MHz, 63.0 kHz, 70.0 Hz
[    28.850] (II) R128(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
[    28.850] (**) R128(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
[    28.850] (II) R128(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    28.850] (**) R128(0): *Driver mode "1024x768i": 44.9 MHz, 35.5 kHz, 43.5 Hz (I)
[    28.850] (II) R128(0): Modeline "1024x768i"x43.5   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
[    28.850] (**) R128(0): *Default mode "1024x768i": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
[    28.850] (II) R128(0): Modeline "1024x768i"x86.9   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
[    28.850] (**) R128(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[    28.850] (II) R128(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    28.850] (**) R128(0): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[    28.850] (II) R128(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    28.850] (**) R128(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    28.850] (II) R128(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    28.850] (**) R128(0): *Default mode "1024x768": 194.0 MHz, 137.0 kHz, 85.0 Hz (D)
[    28.850] (II) R128(0): Modeline "1024x768"x85.0  194.02  1024 1108 1220 1416  768 768 770 806 doublescan -hsync +vsync (137.0 kHz)
[    28.850] (**) R128(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
[    28.851] (II) R128(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[    28.851] (**) R128(0): *Default mode "1024x768": 170.2 MHz, 120.2 kHz, 75.0 Hz (D)
[    28.851] (II) R128(0): Modeline "1024x768"x75.0  170.24  1024 1108 1220 1416  768 768 770 801 doublescan -hsync +vsync (120.2 kHz)
[    28.851] (**) R128(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[    28.851] (II) R128(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    28.851] (**) R128(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[    28.851] (II) R128(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    28.851] (**) R128(0): *Default mode "1024x768": 133.5 MHz, 95.3 kHz, 60.0 Hz (D)
[    28.851] (II) R128(0): Modeline "1024x768"x60.0  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz)
[    28.851] (**) R128(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    28.851] (II) R128(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    28.851] (**) R128(0): *Default mode "960x720": 170.7 MHz, 128.5 kHz, 85.0 Hz (D)
[    28.851] (II) R128(0): Modeline "960x720"x85.0  170.68  960 1036 1144 1328  720 720 722 756 doublescan -hsync +vsync (128.5 kHz)
[    28.851] (**) R128(0): *Default mode "960x720": 148.5 MHz, 112.5 kHz, 75.0 Hz (D)
[    28.851] (II) R128(0): Modeline "960x720"x75.0  148.50  960 1032 1144 1320  720 720 722 750 doublescan -hsync +vsync (112.5 kHz)
[    28.851] (**) R128(0): *Default mode "960x720": 117.0 MHz, 90.0 kHz, 60.0 Hz (D)
[    28.851] (II) R128(0): Modeline "960x720"x60.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz)
[    28.851] (**) R128(0): *Default mode "928x696": 144.0 MHz, 112.5 kHz, 75.0 Hz (D)
[    28.851] (II) R128(0): Modeline "928x696"x75.0  144.00  928 992 1104 1280  696 696 698 750 doublescan -hsync +vsync (112.5 kHz)
[    28.851] (**) R128(0): *Default mode "928x696": 109.2 MHz, 86.4 kHz, 60.1 Hz (D)
[    28.851] (II) R128(0): Modeline "928x696"x60.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz)
[    28.851] (**) R128(0): *Default mode "896x672": 130.5 MHz, 106.3 kHz, 75.0 Hz (D)
[    28.851] (II) R128(0): Modeline "896x672"x75.0  130.50  896 944 1052 1228  672 672 674 708 doublescan -hsync +vsync (106.3 kHz)
[    28.851] (**) R128(0): *Default mode "896x672": 102.4 MHz, 83.7 kHz, 60.0 Hz (D)
[    28.851] (II) R128(0): Modeline "896x672"x60.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz)
[    28.851] (**) R128(0): *Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
[    28.851] (II) R128(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    28.851] (**) R128(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
[    28.851] (II) R128(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    28.851] (**) R128(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[    28.851] (II) R128(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    28.852] (**) R128(0): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
[    28.852] (II) R128(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    28.852] (**) R128(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    28.852] (II) R128(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    28.852] (**) R128(0): *Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[    28.852] (II) R128(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    28.852] (**) R128(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
[    28.852] (II) R128(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[    28.852] (**) R128(0): *Default mode "800x600": 114.8 MHz, 106.2 kHz, 85.0 Hz (D)
[    28.852] (II) R128(0): Modeline "800x600"x85.0  114.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (106.2 kHz)
[    28.852] (**) R128(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[    28.852] (II) R128(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    28.852] (**) R128(0): *Default mode "800x600": 101.2 MHz, 93.8 kHz, 75.0 Hz (D)
[    28.852] (II) R128(0): Modeline "800x600"x75.0  101.25  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (93.8 kHz)
[    28.852] (**) R128(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
[    28.852] (II) R128(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    28.852] (**) R128(0): *Default mode "800x600": 94.5 MHz, 87.5 kHz, 70.0 Hz (D)
[    28.852] (II) R128(0): Modeline "800x600"x70.0   94.50  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (87.5 kHz)
[    28.852] (**) R128(0): *Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
[    28.852] (II) R128(0): Modeline "800x600"x65.0   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (81.2 kHz)
[    28.852] (**) R128(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    28.852] (II) R128(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    28.852] (**) R128(0): *Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
[    28.852] (II) R128(0): Modeline "800x600"x60.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz)
[    28.852] (**) R128(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[    28.852] (II) R128(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    28.852] (**) R128(0): *Default mode "840x525": 107.4 MHz, 93.9 kHz, 85.0 Hz (D)
[    28.852] (II) R128(0): Modeline "840x525"x85.0  107.38  840 904 992 1144  525 526 529 552 doublescan -hsync +vsync (93.9 kHz)
[    28.852] (**) R128(0): *Default mode "840x525": 93.5 MHz, 82.3 kHz, 75.0 Hz (D)
[    28.852] (II) R128(0): Modeline "840x525"x75.0   93.50  840 900 988 1136  525 526 529 549 doublescan -hsync +vsync (82.3 kHz)
[    28.852] (**) R128(0): *Default mode "840x525": 87.0 MHz, 76.6 kHz, 69.9 Hz (D)
[    28.853] (II) R128(0): Modeline "840x525"x69.9   87.00  840 900 988 1136  525 526 529 548 doublescan -hsync +vsync (76.6 kHz)
[    28.853] (**) R128(0): *Default mode "840x525": 73.1 MHz, 65.3 kHz, 60.0 Hz (D)
[    28.853] (II) R128(0): Modeline "840x525"x60.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz)
[    28.853] (**) R128(0): *Default mode "700x525": 89.6 MHz, 93.8 kHz, 85.1 Hz (D)
[    28.853] (II) R128(0): Modeline "700x525"x85.1   89.63  700 752 828 956  525 525 527 551 doublescan -hsync +vsync (93.8 kHz)
[    28.853] (**) R128(0): *Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
[    28.853] (II) R128(0): Modeline "700x525"x74.8   77.90  700 732 892 956  525 526 532 545 doublescan +hsync +vsync (81.5 kHz)
[    28.853] (**) R128(0): *Default mode "700x525": 72.5 MHz, 76.5 kHz, 70.1 Hz (D)
[    28.853] (II) R128(0): Modeline "700x525"x70.1   72.53  700 748 824 948  525 525 527 546 doublescan -hsync +vsync (76.5 kHz)
[    28.853] (**) R128(0): *Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
[    28.853] (II) R128(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
[    28.853] (**) R128(0): *Default mode "640x512": 78.8 MHz, 91.1 kHz, 85.0 Hz (D)
[    28.853] (II) R128(0): Modeline "640x512"x85.0   78.75  640 672 752 864  512 512 514 536 doublescan +hsync +vsync (91.1 kHz)
[    28.853] (**) R128(0): *Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
[    28.853] (II) R128(0): Modeline "640x512"x75.0   67.50  640 648 720 844  512 512 514 533 doublescan +hsync +vsync (80.0 kHz)
[    28.853] (**) R128(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
[    28.853] (II) R128(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
[    28.854] (**) R128(0): *Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
[    28.854] (II) R128(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
[    28.854] (**) R128(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[    28.854] (II) R128(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    28.854] (**) R128(0): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[    28.854] (II) R128(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    28.854] (**) R128(0): *Driver mode "640x480": 30.2 MHz, 35.0 kHz, 66.7 Hz
[    28.854] (II) R128(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    28.854] (**) R128(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    28.854] (II) R128(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    28.854] (**) R128(0): *Default mode "640x480": 74.2 MHz, 85.9 kHz, 85.1 Hz (D)
[    28.854] (II) R128(0): Modeline "640x480"x85.1   74.25  640 672 752 864  480 480 482 505 doublescan +hsync +vsync (85.9 kHz)
[    28.854] (**) R128(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
[    28.854] (II) R128(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[    28.854] (**) R128(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[    28.854] (II) R128(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    28.854] (**) R128(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[    28.854] (II) R128(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    28.854] (**) R128(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
[    28.854] (II) R128(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
[    28.854] (**) R128(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    28.854] (II) R128(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    28.854] (**) R128(0): *Driver mode "720x400": 35.5 MHz, 39.4 kHz, 87.8 Hz
[    28.854] (II) R128(0): Modeline "720x400"x87.8   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
[    28.854] (**) R128(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
[    28.854] (II) R128(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[    28.854] (**) R128(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
[    28.854] (II) R128(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
[    28.854] (**) R128(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
[    28.854] (II) R128(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
[    28.854] (**) R128(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
[    28.855] (II) R128(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[    28.855] (**) R128(0): *Default mode "576x432": 71.7 MHz, 91.5 kHz, 100.1 Hz (D)
[    28.855] (II) R128(0): Modeline "576x432"x100.1   71.73  576 616 680 784  432 432 434 457 doublescan -hsync +vsync (91.5 kHz)
[    28.855] (**) R128(0): *Default mode "576x432": 60.8 MHz, 77.5 kHz, 85.2 Hz (D)
[    28.855] (II) R128(0): Modeline "576x432"x85.2   60.75  576 608 672 784  432 432 434 455 doublescan +hsync -vsync (77.5 kHz)
[    28.855] (**) R128(0): *Default mode "576x432": 59.8 MHz, 77.1 kHz, 85.1 Hz (D)
[    28.855] (II) R128(0): Modeline "576x432"x85.1   59.83  576 612 676 776  432 432 434 453 doublescan -hsync +vsync (77.1 kHz)
[    28.855] (**) R128(0): *Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
[    28.855] (II) R128(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
[    28.855] (**) R128(0): *Default mode "576x432": 52.5 MHz, 67.6 kHz, 75.0 Hz (D)
[    28.855] (II) R128(0): Modeline "576x432"x75.0   52.49  576 612 676 776  432 432 434 451 doublescan -hsync +vsync (67.6 kHz)
[    28.855] (**) R128(0): *Default mode "576x432": 48.4 MHz, 63.0 kHz, 70.0 Hz (D)
[    28.855] (II) R128(0): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450 doublescan -hsync +vsync (63.0 kHz)
[    28.855] (**) R128(0): *Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
[    28.855] (II) R128(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
[    28.855] (**) R128(0): *Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
[    28.855] (II) R128(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[    28.855] (**) R128(0): *Default mode "512x384i": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
[    28.855] (II) R128(0): Modeline "512x384i"x86.6   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync (35.5 kHz)
[    28.855] (**) R128(0): *Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
[    28.855] (II) R128(0): Modeline "512x384"x85.0   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync (68.7 kHz)
[    28.855] (**) R128(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
[    28.855] (II) R128(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
[    28.855] (**) R128(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
[    28.855] (II) R128(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
[    28.855] (**) R128(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
[    28.855] (II) R128(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
[    28.855] (**) R128(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
[    28.855] (II) R128(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
[    28.855] (**) R128(0): *Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
[    28.855] (II) R128(0): Modeline "400x300"x85.3   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync (53.7 kHz)
[    28.856] (**) R128(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
[    28.856] (II) R128(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
[    28.856] (**) R128(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
[    28.856] (II) R128(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
[    28.856] (**) R128(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
[    28.856] (II) R128(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
[    28.856] (**) R128(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
[    28.856] (II) R128(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
[    28.856] (**) R128(0): *Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
[    28.856] (II) R128(0): Modeline "320x240"x85.2   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync (43.3 kHz)
[    28.856] (**) R128(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
[    28.856] (II) R128(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
[    28.856] (**) R128(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
[    28.856] (II) R128(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
[    28.856] (**) R128(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
[    28.856] (II) R128(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
[    28.856] (**) R128(0): *Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
[    28.856] (II) R128(0): Modeline "360x200"x85.0   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync (37.9 kHz)
[    28.856] (**) R128(0): *Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
[    28.856] (II) R128(0): Modeline "320x200"x85.3   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync (37.9 kHz)
[    28.856] (**) R128(0): *Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
[    28.856] (II) R128(0): Modeline "320x175"x85.3   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync (37.9 kHz)
[    28.856] (**) R128(0): Display dimensions: (340, 270) mm
[    28.856] (**) R128(0): DPI set to (95, 96)
[    28.856] (II) Loading sub module "fb"
[    28.856] (II) LoadModule: "fb"
[    28.857] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.858] (II) Module fb: vendor="X.Org Foundation"
[    28.858]     compiled for 1.10.4, module version = 1.0.0
[    28.858]     ABI class: X.Org ANSI C Emulation, version 0.4
[    28.858] (II) Loading sub module "ramdac"
[    28.858] (II) LoadModule: "ramdac"
[    28.858] (II) Module "ramdac" already built-in
[    28.858] (II) Loading sub module "xaa"
[    28.858] (II) LoadModule: "xaa"
[    28.859] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    28.859] (II) Module xaa: vendor="X.Org Foundation"
[    28.859]     compiled for 1.10.4, module version = 1.2.1
[    28.859]     ABI class: X.Org Video Driver, version 10.0
[    28.859] (II) Loading sub module "shadowfb"
[    28.859] (II) LoadModule: "shadowfb"
[    28.859] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    28.860] (II) Module shadowfb: vendor="X.Org Foundation"
[    28.860]     compiled for 1.10.4, module version = 1.0.0
[    28.860]     ABI class: X.Org ANSI C Emulation, version 0.4
[    28.860] (II) R128(0): Page flipping disabled
[    28.860] (!!) R128(0): For information on using the multimedia capabilities
    of this adapter, please see http://gatos.sf.net.
[    28.860] (II) UnloadModule: "vesa"
[    28.860] (II) Unloading vesa
[    28.860] (II) UnloadModule: "fbdev"
[    28.860] (II) Unloading fbdev
[    28.860] (II) UnloadModule: "fbdevhw"
[    28.860] (II) Unloading fbdevhw
[    28.860] (--) Depth 24 pixmap format is 32 bpp
[    28.870] drmOpenDevice: node name is /dev/dri/card0
[    28.874] drmOpenDevice: node name is /dev/dri/card0
[    28.916] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    28.916] drmOpenDevice: node name is /dev/dri/card0
[    28.916] drmOpenDevice: open result is 13, (OK)
[    28.917] drmOpenByBusid: drmOpenMinor returns 13
[    28.917] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    28.917] (II) [drm] loaded kernel module for "r128" driver.
[    28.917] (II) [drm] DRM interface version 1.4
[    28.917] (II) [drm] DRM open master succeeded.
[    28.917] (II) R128(0): [drm] Using the DRM lock SAREA also for drawables.
[    28.917] (II) R128(0): [drm] framebuffer handle = 0xf8000000
[    28.917] (II) R128(0): [drm] added 1 reserved context for kernel
[    28.917] (II) R128(0): X context handle = 0x1
[    28.917] (II) R128(0): [drm] installed DRM signal handler
[    28.918] (II) R128(0): [agp] Mode 0x1f000211 [AGP 0x8086/0x1a30; Card 0x1002/0x5446]
[    28.943] (II) R128(0): [agp] 8192 kB allocated with handle 0x00000001
[    28.944] (II) R128(0): [agp] ring handle = 0xfc000000
[    28.944] (II) R128(0): [agp] Ring mapped at 0xb649d000
[    28.945] (II) R128(0): [agp] ring read ptr handle = 0xfc101000
[    28.945] (II) R128(0): [agp] Ring read ptr mapped at 0xb76fe000
[    28.945] (II) R128(0): [agp] vertex/indirect buffers handle = 0xfc102000
[    28.945] (II) R128(0): [agp] Vertex/indirect buffers mapped at 0xb629d000
[    28.945] (II) R128(0): [agp] AGP texture map handle = 0xfc302000
[    28.946] (II) R128(0): [agp] AGP Texture map mapped at 0xb5dbd000
[    28.946] (II) R128(0): [drm] register handle = 0xff8fc000
[    28.946] (II) R128(0): [dri] Visual configs initialized
[    28.947] (II) R128(0): CCE in BM mode
[    28.947] (II) R128(0): Using 8 MB AGP aperture
[    28.947] (II) R128(0): Using 1 MB for the ring buffer
[    28.947] (II) R128(0): Using 2 MB for vertex/indirect buffers
[    28.947] (II) R128(0): Using 5 MB for AGP textures
[    28.947] (II) R128(0): Memory manager initialized to (0,0) (1280,3276)
[    28.947] (II) R128(0): Reserved area from (0,1024) to (1280,1026)
[    28.947] (II) R128(0): Largest offscreen area available: 1280 x 2250
[    28.947] (II) R128(0): Reserved back buffer from (0,1026) to (1280,2050)
[    28.947] (II) R128(0): Reserved depth buffer from (0,2050) to (1280,3075)
[    28.947] (II) R128(0): Reserved depth span from (0,3074) offset 0xf02800
[    28.947] (II) R128(0): Reserved 0 kb for textures at offset 0xfff000
[    28.947] (II) R128(0): Using XFree86 Acceleration Architecture (XAA)
[    28.947]     Screen to screen bit blits
[    28.947]     Solid filled rectangles
[    28.947]     8x8 mono pattern filled rectangles
[    28.947]     Indirect CPU to Screen color expansion
[    28.947]     Solid Lines
[    28.947]     Dashed Lines
[    28.947]     Setting up tile and stipple cache:
[    28.947]         10 128x128 slots
[    28.947] (II) R128(0): Acceleration enabled
[    28.948] (==) R128(0): Backing store disabled
[    28.948] (==) R128(0): Silken mouse enabled
[    28.948] (II) R128(0): Using hardware cursor (scanline 12300)
[    28.948] (II) R128(0): Largest offscreen area available: 1280 x 199
[    28.949] (==) R128(0): DPMS enabled
[    28.949] (II) R128(0): [DRI] installation complete
[    28.961] (II) R128(0): [drm] Added 128 16384 byte vertex/indirect buffers
[    28.962] (II) R128(0): [drm] Mapped 128 vertex/indirect buffers
[    28.962] (II) R128(0): [drm] dma control initialized, using IRQ 16
[    28.962] (II) R128(0): Direct rendering enabled
[    28.962] (==) RandR enabled
[    28.962] (II) Initializing built-in extension Generic Event Extension
[    28.962] (II) Initializing built-in extension SHAPE
[    28.962] (II) Initializing built-in extension MIT-SHM
[    28.962] (II) Initializing built-in extension XInputExtension
[    28.962] (II) Initializing built-in extension XTEST
[    28.962] (II) Initializing built-in extension BIG-REQUESTS
[    28.962] (II) Initializing built-in extension SYNC
[    28.962] (II) Initializing built-in extension XKEYBOARD
[    28.962] (II) Initializing built-in extension XC-MISC
[    28.962] (II) Initializing built-in extension SECURITY
[    28.963] (II) Initializing built-in extension XINERAMA
[    28.963] (II) Initializing built-in extension XFIXES
[    28.963] (II) Initializing built-in extension RENDER
[    28.963] (II) Initializing built-in extension RANDR
[    28.963] (II) Initializing built-in extension COMPOSITE
[    28.963] (II) Initializing built-in extension DAMAGE
[    28.963] (II) Initializing built-in extension GESTURE
[    28.990] (II) AIGLX: Screen 0 is not DRI2 capable
[    28.990] drmOpenDevice: node name is /dev/dri/card0
[    28.990] drmOpenDevice: open result is 14, (OK)
[    28.990] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    28.990] drmOpenDevice: node name is /dev/dri/card0
[    28.991] drmOpenDevice: open result is 14, (OK)
[    28.991] drmOpenByBusid: drmOpenMinor returns 14
[    28.991] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    28.991] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    28.991] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/r128_dri.so
[    29.008] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    29.008] (II) AIGLX: Loaded and initialized r128
[    29.008] (II) GLX: Initialized DRI GL provider for screen 0
[    29.044] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    29.065] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    29.065] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.065] (II) LoadModule: "evdev"
[    29.065] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.068] (II) Module evdev: vendor="X.Org Foundation"
[    29.068]     compiled for 1.10.2, module version = 2.6.0
[    29.068]     Module class: X.Org XInput Driver
[    29.068]     ABI class: X.Org XInput driver, version 12.3
[    29.068] (II) Using input driver 'evdev' for 'Power Button'
[    29.068] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.068] (**) Power Button: always reports core events
[    29.068] (**) Power Button: Device: "/dev/input/event1"
[    29.068] (--) Power Button: Found keys
[    29.068] (II) Power Button: Configuring as keyboard
[    29.069] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    29.069] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    29.069] (**) Option "xkb_rules" "evdev"
[    29.069] (**) Option "xkb_model" "pc105"
[    29.069] (**) Option "xkb_layout" "us"
[    29.072] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    29.072] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.072] (II) Using input driver 'evdev' for 'Power Button'
[    29.072] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.072] (**) Power Button: always reports core events
[    29.072] (**) Power Button: Device: "/dev/input/event0"
[    29.073] (--) Power Button: Found keys
[    29.073] (II) Power Button: Configuring as keyboard
[    29.073] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    29.073] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    29.073] (**) Option "xkb_rules" "evdev"
[    29.073] (**) Option "xkb_model" "pc105"
[    29.073] (**) Option "xkb_layout" "us"
[    29.085] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    29.085] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    29.085] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    29.085] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.085] (**) AT Translated Set 2 keyboard: always reports core events
[    29.085] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    29.085] (--) AT Translated Set 2 keyboard: Found keys
[    29.085] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    29.085] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    29.085] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    29.085] (**) Option "xkb_rules" "evdev"
[    29.085] (**) Option "xkb_model" "pc105"
[    29.085] (**) Option "xkb_layout" "us"
[    29.087] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event3)
[    29.087] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    29.087] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    29.087] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.087] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    29.087] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event3"
[    29.087] (--) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    29.087] (--) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    29.087] (--) ImPS/2 Generic Wheel Mouse: Found relative axes
[    29.087] (--) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    29.087] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    29.087] (II) ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    29.087] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    29.088] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.088] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[    29.088] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    29.088] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    29.088] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    29.088] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    29.088] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    29.088] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    29.089] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    29.089] (II) No input driver/identifier specified (ignoring)

```

xorg log taken after it booted 1024x768
```

[    20.275] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    20.276] X Protocol Version 11, Revision 0
[    20.276] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    20.276] Current Operating System: Linux ubuntu 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686
[    20.276] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=0e665365-03f9-41e6-b61e-340a067c68b1 ro splash quiet vt.handoff=7
[    20.276] Build Date: 19 October 2011  05:09:41AM
[    20.276] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    20.276] Current version of pixman: 0.22.2
[    20.276]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    20.276] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.276] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 24 20:03:05 2012
[    20.289] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.289] (==) No Layout section.  Using the first Screen section.
[    20.289] (==) No screen section available. Using defaults.
[    20.289] (**) |-->Screen "Default Screen Section" (0)
[    20.289] (**) |   |-->Monitor "<default monitor>"
[    20.290] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    20.290] (==) Automatically adding devices
[    20.290] (==) Automatically enabling devices
[    20.290] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.290]     Entry deleted from font path.
[    20.290] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.290]     Entry deleted from font path.
[    20.290] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.290]     Entry deleted from font path.
[    20.291] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    20.291] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.291] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.291] (II) Loader magic: 0x823ada0
[    20.291] (II) Module ABI versions:
[    20.291]     X.Org ANSI C Emulation: 0.4
[    20.291]     X.Org Video Driver: 10.0
[    20.291]     X.Org XInput driver : 12.3
[    20.291]     X.Org Server Extension : 5.0
[    20.292] (--) PCI:*(0:1:0:0) 1002:5446:1002:0408 rev 0, Mem @ 0xf8000000/67108864, 0xff8fc000/16384, I/O @ 0x0000ec00/256, BIOS @ 0x????????/131072
[    20.292] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    20.292] (II) LoadModule: "extmod"
[    20.294] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.295] (II) Module extmod: vendor="X.Org Foundation"
[    20.295]     compiled for 1.10.4, module version = 1.0.0
[    20.295]     Module class: X.Org Server Extension
[    20.295]     ABI class: X.Org Server Extension, version 5.0
[    20.295] (II) Loading extension MIT-SCREEN-SAVER
[    20.295] (II) Loading extension XFree86-VidModeExtension
[    20.295] (II) Loading extension XFree86-DGA
[    20.295] (II) Loading extension DPMS
[    20.295] (II) Loading extension XVideo
[    20.295] (II) Loading extension XVideo-MotionCompensation
[    20.295] (II) Loading extension X-Resource
[    20.295] (II) LoadModule: "dbe"
[    20.296] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.296] (II) Module dbe: vendor="X.Org Foundation"
[    20.296]     compiled for 1.10.4, module version = 1.0.0
[    20.296]     Module class: X.Org Server Extension
[    20.296]     ABI class: X.Org Server Extension, version 5.0
[    20.296] (II) Loading extension DOUBLE-BUFFER
[    20.296] (II) LoadModule: "glx"
[    20.297] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.297] (II) Module glx: vendor="X.Org Foundation"
[    20.297]     compiled for 1.10.4, module version = 1.0.0
[    20.297]     ABI class: X.Org Server Extension, version 5.0
[    20.297] (==) AIGLX enabled
[    20.297] (II) Loading extension GLX
[    20.298] (II) LoadModule: "record"
[    20.298] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    20.299] (II) Module record: vendor="X.Org Foundation"
[    20.299]     compiled for 1.10.4, module version = 1.13.0
[    20.299]     Module class: X.Org Server Extension
[    20.299]     ABI class: X.Org Server Extension, version 5.0
[    20.299] (II) Loading extension RECORD
[    20.299] (II) LoadModule: "dri"
[    20.299] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    20.300] (II) Module dri: vendor="X.Org Foundation"
[    20.300]     compiled for 1.10.4, module version = 1.0.0
[    20.300]     ABI class: X.Org Server Extension, version 5.0
[    20.300] (II) Loading extension XFree86-DRI
[    20.300] (II) LoadModule: "dri2"
[    20.301] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.301] (II) Module dri2: vendor="X.Org Foundation"
[    20.301]     compiled for 1.10.4, module version = 1.2.0
[    20.301]     ABI class: X.Org Server Extension, version 5.0
[    20.301] (II) Loading extension DRI2
[    20.301] (==) Matched fglrx as autoconfigured driver 0
[    20.301] (==) Matched ati as autoconfigured driver 1
[    20.301] (==) Matched vesa as autoconfigured driver 2
[    20.301] (==) Matched fbdev as autoconfigured driver 3
[    20.301] (==) Assigned the driver to the xf86ConfigLayout
[    20.301] (II) LoadModule: "fglrx"
[    20.303] (WW) Warning, couldn't open module fglrx
[    20.303] (II) UnloadModule: "fglrx"
[    20.303] (II) Unloading fglrx
[    20.303] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    20.303] (II) LoadModule: "ati"
[    20.304] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    20.304] (II) Module ati: vendor="X.Org Foundation"
[    20.304]     compiled for 1.10.2.902, module version = 6.14.99
[    20.304]     Module class: X.Org Video Driver
[    20.304]     ABI class: X.Org Video Driver, version 10.0
[    20.304] (II) LoadModule: "r128"
[    20.305] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[    20.305] (II) Module r128: vendor="X.Org Foundation"
[    20.305]     compiled for 1.10.1, module version = 6.8.1
[    20.305]     Module class: X.Org Video Driver
[    20.305]     ABI class: X.Org Video Driver, version 10.0
[    20.305] (II) LoadModule: "vesa"
[    20.306] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.306] (II) Module vesa: vendor="X.Org Foundation"
[    20.306]     compiled for 1.10.2, module version = 2.3.0
[    20.306]     Module class: X.Org Video Driver
[    20.306]     ABI class: X.Org Video Driver, version 10.0
[    20.306] (II) LoadModule: "fbdev"
[    20.307] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.307] (II) Module fbdev: vendor="X.Org Foundation"
[    20.307]     compiled for 1.10.0, module version = 0.4.2
[    20.307]     ABI class: X.Org Video Driver, version 10.0
[    20.307] (II) R128: Driver for ATI Rage 128 chipsets:
    ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
    ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
    ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
    ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
    ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
    ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
    ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
    ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
    ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
    ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
    ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
    ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
    ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
    ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
    ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
    ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
    ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
    ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
    ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
    ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
    ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
    ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
    ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
    ATI Rage 128 Pro ULTRA TU (AGP?)
[    20.309] (II) VESA: driver for VESA chipsets: vesa
[    20.309] (II) FBDEV: driver for framebuffer: fbdev
[    20.309] (++) using VT number 7

[    20.309] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[    20.309] (WW) Falling back to old probe method for vesa
[    20.309] (WW) Falling back to old probe method for fbdev
[    20.309] (II) Loading sub module "fbdevhw"
[    20.309] (II) LoadModule: "fbdevhw"
[    20.310] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.310] (II) Module fbdevhw: vendor="X.Org Foundation"
[    20.310]     compiled for 1.10.4, module version = 0.0.2
[    20.310]     ABI class: X.Org Video Driver, version 10.0
[    20.310] (II) R128(0): PCI bus 1 card 0 func 0
[    20.310] (II) R128(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    20.310] (==) R128(0): Depth 24, (--) framebuffer bpp 32
[    20.310] (II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    20.310] (==) R128(0): Default visual is TrueColor
[    20.310] (II) Loading sub module "vgahw"
[    20.310] (II) LoadModule: "vgahw"
[    20.311] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    20.311] (II) Module vgahw: vendor="X.Org Foundation"
[    20.312]     compiled for 1.10.4, module version = 0.1.0
[    20.312]     ABI class: X.Org Video Driver, version 10.0
[    20.312] (II) R128(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    20.312] (==) R128(0): RGB weight 888
[    20.312] (II) R128(0): Using 8 bits per RGB (8 bit DAC)
[    20.312] (II) Loading sub module "int10"
[    20.312] (II) LoadModule: "int10"
[    20.313] (II) Loading /usr/lib/xorg/modules/libint10.so
[    20.313] (II) Module int10: vendor="X.Org Foundation"
[    20.313]     compiled for 1.10.4, module version = 1.0.0
[    20.313]     ABI class: X.Org Video Driver, version 10.0
[    20.313] (II) R128(0): initializing int10
[    20.314] (II) R128(0): Primary V_BIOS segment is: 0xc000
[    20.314] (--) R128(0): Chipset: "ATI Rage 128 Pro ULTRA TF (AGP)" (ChipID = 0x5446)
[    20.314] (--) R128(0): Linear framebuffer at 0xf8000000
[    20.314] (--) R128(0): MMIO registers at 0xff8fc000
[    20.315] (--) R128(0): VideoRAM: 16384 kByte (128-bit SDR SGRAM 1:1)
[    20.315] (**) R128(0): Using external CRT for display
[    20.345] (II) R128(0): Primary Display == Type 3
[    20.345] (WW) R128(0): Can't determine panel dimensions, and none specified.
    Disabling programming of FP registers.
[    20.345] (II) R128(0): PLL parameters: rf=2950 rd=65 min=12500 max=35000; xclk=13000
[    20.345] (II) Loading sub module "ddc"
[    20.345] (II) LoadModule: "ddc"
[    20.345] (II) Module "ddc" already built-in
[    20.345] (II) Loading sub module "vbe"
[    20.345] (II) LoadModule: "vbe"
[    20.345] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    20.346] (II) Module vbe: vendor="X.Org Foundation"
[    20.346]     compiled for 1.10.4, module version = 1.1.0
[    20.346]     ABI class: X.Org Video Driver, version 10.0
[    20.346] (II) R128(0): VESA BIOS detected
[    20.346] (II) R128(0): VESA VBE Version 2.0
[    20.346] (II) R128(0): VESA VBE Total Mem: 16384 kB
[    20.346] (II) R128(0): VESA VBE OEM: ATI RAGE128
[    20.346] (II) R128(0): VESA VBE OEM Software Rev: 1.0
[    20.346] (II) R128(0): VESA VBE OEM Vendor: ATI Technologies Inc.
[    20.346] (II) R128(0): VESA VBE OEM Product: R128
[    20.346] (II) R128(0): VESA VBE OEM Product Rev: 01.00
[    20.347] (II) Loading sub module "ddc"
[    20.347] (II) LoadModule: "ddc"
[    20.347] (II) Module "ddc" already built-in
[    20.436] (II) R128(0): VESA VBE DDC supported
[    20.437] (II) R128(0): VESA VBE DDC Level 2
[    20.437] (II) R128(0): VESA VBE DDC transfer in appr. 2 sec.
[    21.435] (II) R128(0): VESA VBE DDC read successfully
[    21.435] (EE) R128(0): Unknown EDID version 255
[    21.436] (==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.439] (II) Loading sub module "i2c"
[    21.439] (II) LoadModule: "i2c"
[    21.439] (II) Module "i2c" already built-in
[    21.439] (II) R128(0): I2C bus "DDC" initialized.
[    21.439] (II) R128(0): I2C device "DDC:ddc2" registered at address 0xA0.
[    21.443] (EE) R128(0): No DFP detected
[    21.447] (II) R128(0): <default monitor>: Using default hsync range of 31.50-48.00 kHz
[    21.447] (II) R128(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[    21.447] (II) R128(0): <default monitor>: Using default maximum pixel clock of 65.00 MHz
[    21.447] (WW) R128(0): Unable to estimate virtual size
[    21.447] (II) R128(0): Clock range:  12.50 to 350.00 MHz
[    21.447] (II) R128(0): Not using default mode "640x350" (vrefresh out of range)
[    21.447] (II) R128(0): Not using default mode "320x175" (vrefresh out of range)
[    21.447] (II) R128(0): Not using default mode "640x400" (vrefresh out of range)
[    21.447] (II) R128(0): Not using default mode "320x200" (vrefresh out of range)
[    21.447] (II) R128(0): Not using default mode "720x400" (vrefresh out of range)
[    21.447] (II) R128(0): Not using default mode "360x200" (vrefresh out of range)
[    21.448] (II) R128(0): Not using default mode "640x480" (vrefresh out of range)
[    21.448] (II) R128(0): Not using default mode "320x240" (vrefresh out of range)
[    21.448] (II) R128(0): Not using default mode "640x480" (vrefresh out of range)
[    21.448] (II) R128(0): Not using default mode "320x240" (vrefresh out of range)
[    21.448] (II) R128(0): Not using default mode "640x480" (vrefresh out of range)
[    21.448] (II) R128(0): Not using default mode "320x240" (vrefresh out of range)
[    21.448] (II) R128(0): Not using default mode "800x600" (vrefresh out of range)
[    21.448] (II) R128(0): Not using default mode "400x300" (vrefresh out of range)
[    21.448] (II) R128(0): Not using default mode "800x600" (vrefresh out of range)
[    21.448] (II) R128(0): Not using default mode "400x300" (vrefresh out of range)
[    21.448] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    21.448] (II) R128(0): Not using default mode "400x300" (hsync out of range)
[    21.448] (II) R128(0): Not using default mode "1024x768i" (vrefresh out of range)
[    21.448] (II) R128(0): Not using default mode "512x384i" (vrefresh out of range)
[    21.448] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    21.448] (II) R128(0): Not using default mode "512x384" (hsync out of range)
[    21.448] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    21.448] (II) R128(0): Not using default mode "512x384" (hsync out of range)
[    21.448] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    21.448] (II) R128(0): Not using default mode "512x384" (hsync out of range)
[    21.448] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    21.448] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    21.448] (II) R128(0): Not using default mode "1280x960" (hsync out of range)
[    21.448] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    21.448] (II) R128(0): Not using default mode "1280x960" (hsync out of range)
[    21.448] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    21.448] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[    21.448] (II) R128(0): Not using default mode "640x512" (hsync out of range)
[    21.448] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "640x512" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "640x512" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1792x1344" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "896x672" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1792x1344" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "896x672" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1856x1392" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "928x696" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1856x1392" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "928x696" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1920x1440" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "960x720" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1920x1440" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "960x720" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "832x624" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "416x312" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    21.449] (II) R128(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    21.449] (II) R128(0): Not using default mode "1360x768" (mode clock too high)
[    21.450] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "700x525" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "700x525" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "700x525" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "700x525" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "1440x900" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "720x450" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "1600x1024" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "800x512" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "1920x1080" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "960x540" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "1920x1200" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "960x600" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "1920x1440" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "960x720" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "2048x1536" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "2048x1536" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    21.450] (II) R128(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[    21.450] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    21.450] (--) R128(0): Virtual size is 1024x768 (pitch 1024)
[    21.450] (**) R128(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    21.450] (II) R128(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    21.450] (**) R128(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    21.450] (II) R128(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    21.451] (**) R128(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[    21.451] (II) R128(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    21.451] (**) R128(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    21.451] (II) R128(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    21.451] (**) R128(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
[    21.451] (II) R128(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
[    21.451] (**) R128(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
[    21.451] (II) R128(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
[    21.451] (**) R128(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
[    21.451] (II) R128(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
[    21.451] (**) R128(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
[    21.451] (II) R128(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
[    21.451] (**) R128(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
[    21.451] (II) R128(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
[    21.451] (**) R128(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
[    21.451] (II) R128(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
[    21.451] (==) R128(0): DPI set to (96, 96)
[    21.451] (II) Loading sub module "fb"
[    21.451] (II) LoadModule: "fb"
[    21.452] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.452] (II) Module fb: vendor="X.Org Foundation"
[    21.452]     compiled for 1.10.4, module version = 1.0.0
[    21.452]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.452] (II) Loading sub module "ramdac"
[    21.453] (II) LoadModule: "ramdac"
[    21.453] (II) Module "ramdac" already built-in
[    21.453] (II) Loading sub module "xaa"
[    21.453] (II) LoadModule: "xaa"
[    21.453] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    21.454] (II) Module xaa: vendor="X.Org Foundation"
[    21.454]     compiled for 1.10.4, module version = 1.2.1
[    21.454]     ABI class: X.Org Video Driver, version 10.0
[    21.454] (II) Loading sub module "shadowfb"
[    21.454] (II) LoadModule: "shadowfb"
[    21.454] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    21.454] (II) Module shadowfb: vendor="X.Org Foundation"
[    21.454]     compiled for 1.10.4, module version = 1.0.0
[    21.454]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.454] (II) R128(0): Page flipping disabled
[    21.455] (!!) R128(0): For information on using the multimedia capabilities
    of this adapter, please see http://gatos.sf.net.
[    21.455] (II) UnloadModule: "vesa"
[    21.455] (II) Unloading vesa
[    21.455] (II) UnloadModule: "fbdev"
[    21.455] (II) Unloading fbdev
[    21.455] (II) UnloadModule: "fbdevhw"
[    21.455] (II) Unloading fbdevhw
[    21.455] (--) Depth 24 pixmap format is 32 bpp
[    21.465] drmOpenDevice: node name is /dev/dri/card0
[    21.469] drmOpenDevice: node name is /dev/dri/card0
[    21.511] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    21.511] drmOpenDevice: node name is /dev/dri/card0
[    21.511] drmOpenDevice: open result is 13, (OK)
[    21.511] drmOpenByBusid: drmOpenMinor returns 13
[    21.511] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    21.511] (II) [drm] loaded kernel module for "r128" driver.
[    21.511] (II) [drm] DRM interface version 1.4
[    21.511] (II) [drm] DRM open master succeeded.
[    21.512] (II) R128(0): [drm] Using the DRM lock SAREA also for drawables.
[    21.512] (II) R128(0): [drm] framebuffer handle = 0xf8000000
[    21.512] (II) R128(0): [drm] added 1 reserved context for kernel
[    21.513] (II) R128(0): X context handle = 0x1
[    21.513] (II) R128(0): [drm] installed DRM signal handler
[    21.513] (II) R128(0): [agp] Mode 0x1f000211 [AGP 0x8086/0x1a30; Card 0x1002/0x5446]
[    21.538] (II) R128(0): [agp] 8192 kB allocated with handle 0x00000001
[    21.539] (II) R128(0): [agp] ring handle = 0xfc000000
[    21.540] (II) R128(0): [agp] Ring mapped at 0xb64ce000
[    21.540] (II) R128(0): [agp] ring read ptr handle = 0xfc101000
[    21.540] (II) R128(0): [agp] Ring read ptr mapped at 0xb772f000
[    21.540] (II) R128(0): [agp] vertex/indirect buffers handle = 0xfc102000
[    21.540] (II) R128(0): [agp] Vertex/indirect buffers mapped at 0xb62ce000
[    21.540] (II) R128(0): [agp] AGP texture map handle = 0xfc302000
[    21.542] (II) R128(0): [agp] AGP Texture map mapped at 0xb5dee000
[    21.542] (II) R128(0): [drm] register handle = 0xff8fc000
[    21.542] (II) R128(0): [dri] Visual configs initialized
[    21.542] (II) R128(0): CCE in BM mode
[    21.542] (II) R128(0): Using 8 MB AGP aperture
[    21.542] (II) R128(0): Using 1 MB for the ring buffer
[    21.542] (II) R128(0): Using 2 MB for vertex/indirect buffers
[    21.542] (II) R128(0): Using 5 MB for AGP textures
[    21.542] (II) R128(0): Memory manager initialized to (0,0) (1024,3072)
[    21.542] (II) R128(0): Reserved area from (0,768) to (1024,770)
[    21.542] (II) R128(0): Largest offscreen area available: 1024 x 2302
[    21.542] (II) R128(0): Reserved back buffer from (0,770) to (1024,1538)
[    21.542] (II) R128(0): Reserved depth buffer from (0,1538) to (1024,2307)
[    21.542] (II) R128(0): Reserved depth span from (0,2306) offset 0x902000
[    21.542] (II) R128(0): Reserved 4096 kb for textures at offset 0xc00000
[    21.542] (II) R128(0): Using XFree86 Acceleration Architecture (XAA)
[    21.543]     Screen to screen bit blits
[    21.543]     Solid filled rectangles
[    21.543]     8x8 mono pattern filled rectangles
[    21.543]     Indirect CPU to Screen color expansion
[    21.543]     Solid Lines
[    21.543]     Dashed Lines
[    21.543]     Setting up tile and stipple cache:
[    21.543]         20 128x128 slots
[    21.543]         5 256x256 slots
[    21.543] (II) R128(0): Acceleration enabled
[    21.543] (==) R128(0): Backing store disabled
[    21.543] (==) R128(0): Silken mouse enabled
[    21.543] (II) R128(0): Using hardware cursor (scanline 9228)
[    21.543] (II) R128(0): Largest offscreen area available: 1024 x 763
[    21.543] (==) R128(0): DPMS enabled
[    21.544] (II) R128(0): [DRI] installation complete
[    21.573] (II) R128(0): [drm] Added 128 16384 byte vertex/indirect buffers
[    21.574] (II) R128(0): [drm] Mapped 128 vertex/indirect buffers
[    21.574] (II) R128(0): [drm] dma control initialized, using IRQ 16
[    21.574] (II) R128(0): Direct rendering enabled
[    21.574] (==) RandR enabled
[    21.574] (II) Initializing built-in extension Generic Event Extension
[    21.574] (II) Initializing built-in extension SHAPE
[    21.574] (II) Initializing built-in extension MIT-SHM
[    21.574] (II) Initializing built-in extension XInputExtension
[    21.574] (II) Initializing built-in extension XTEST
[    21.574] (II) Initializing built-in extension BIG-REQUESTS
[    21.574] (II) Initializing built-in extension SYNC
[    21.574] (II) Initializing built-in extension XKEYBOARD
[    21.574] (II) Initializing built-in extension XC-MISC
[    21.574] (II) Initializing built-in extension SECURITY
[    21.574] (II) Initializing built-in extension XINERAMA
[    21.574] (II) Initializing built-in extension XFIXES
[    21.574] (II) Initializing built-in extension RENDER
[    21.574] (II) Initializing built-in extension RANDR
[    21.574] (II) Initializing built-in extension COMPOSITE
[    21.574] (II) Initializing built-in extension DAMAGE
[    21.574] (II) Initializing built-in extension GESTURE
[    21.601] (II) AIGLX: Screen 0 is not DRI2 capable
[    21.602] drmOpenDevice: node name is /dev/dri/card0
[    21.602] drmOpenDevice: open result is 14, (OK)
[    21.602] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    21.602] drmOpenDevice: node name is /dev/dri/card0
[    21.602] drmOpenDevice: open result is 14, (OK)
[    21.602] drmOpenByBusid: drmOpenMinor returns 14
[    21.602] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    21.602] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    21.602] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/r128_dri.so
[    21.619] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    21.619] (II) AIGLX: Loaded and initialized r128
[    21.619] (II) GLX: Initialized DRI GL provider for screen 0
[    21.654] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.674] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    21.674] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.674] (II) LoadModule: "evdev"
[    21.675] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.677] (II) Module evdev: vendor="X.Org Foundation"
[    21.677]     compiled for 1.10.2, module version = 2.6.0
[    21.677]     Module class: X.Org XInput Driver
[    21.677]     ABI class: X.Org XInput driver, version 12.3
[    21.677] (II) Using input driver 'evdev' for 'Power Button'
[    21.677] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.677] (**) Power Button: always reports core events
[    21.678] (**) Power Button: Device: "/dev/input/event1"
[    21.678] (--) Power Button: Found keys
[    21.678] (II) Power Button: Configuring as keyboard
[    21.678] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    21.678] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    21.678] (**) Option "xkb_rules" "evdev"
[    21.678] (**) Option "xkb_model" "pc105"
[    21.678] (**) Option "xkb_layout" "us"
[    21.681] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    21.682] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.682] (II) Using input driver 'evdev' for 'Power Button'
[    21.682] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.682] (**) Power Button: always reports core events
[    21.682] (**) Power Button: Device: "/dev/input/event0"
[    21.682] (--) Power Button: Found keys
[    21.682] (II) Power Button: Configuring as keyboard
[    21.682] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    21.682] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    21.682] (**) Option "xkb_rules" "evdev"
[    21.682] (**) Option "xkb_model" "pc105"
[    21.682] (**) Option "xkb_layout" "us"
[    21.694] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    21.694] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    21.694] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    21.694] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.694] (**) AT Translated Set 2 keyboard: always reports core events
[    21.694] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    21.695] (--) AT Translated Set 2 keyboard: Found keys
[    21.695] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    21.695] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    21.695] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    21.695] (**) Option "xkb_rules" "evdev"
[    21.695] (**) Option "xkb_model" "pc105"
[    21.695] (**) Option "xkb_layout" "us"
[    21.696] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event3)
[    21.696] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    21.696] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    21.697] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.697] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    21.697] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event3"
[    21.697] (--) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    21.697] (--) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    21.697] (--) ImPS/2 Generic Wheel Mouse: Found relative axes
[    21.697] (--) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    21.697] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    21.697] (II) ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    21.697] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    21.697] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.697] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[    21.697] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    21.697] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    21.697] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    21.697] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    21.698] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    21.698] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    21.698] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    21.698] (II) No input driver/identifier specified (ignoring)

```

---


---
title: "Available screen resolutions fluctuate randomly each boot"
date: 2011-07-28
forum: Multimedia Software
---

### Post by Gus Polly on 2011-07-28
I installed Natty on a 5-year-old Compaq with an integrated Intel 8xx chipset, using a Polaroid TLA-01511C monitor, and the list of available resolutions varies quite a bit each time I boot. Sometimes it will only give me 1024x768, 800x600, and 640x480; sometimes it gives me a dozen resolutions ranging up to 1600x1200. Only once has it ever offered me the monitor's native resolution, 1280x800. I'm guessing the EDID is being missent or misread each time. How can I set it to (ignore the EDID and) allow me to select 1280x800 each time?

I did notice that when it was a Windows machine, it would give me the short list of resolutions when booted with the monitor off, but gave more options when booted with the monitor on. Here though, it seems to give the long list when booted with monitor off.

Here's my most current /var/log/Xorg.0.log; this time it booted with about a dozen modes available, but not 1280x800.

```

[    35.690] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    35.691] X Protocol Version 11, Revision 0
[    35.691] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    35.691] Current Operating System: Linux home 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686
[    35.691] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=0a8255a4-4395-4e62-875d-b0400dae7fa1 ro splash vga=795 quiet splash vt.handoff=7
[    35.691] Build Date: 21 May 2011  11:38:35AM
[    35.691] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    35.691] Current version of pixman: 0.20.2
[    35.691]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    35.691] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    35.699] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 28 21:02:52 2011
[    35.719] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    35.720] (==) No Layout section.  Using the first Screen section.
[    35.720] (==) No screen section available. Using defaults.
[    35.720] (**) |-->Screen "Default Screen Section" (0)
[    35.720] (**) |   |-->Monitor "<default monitor>"
[    35.721] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    35.721] (==) Automatically adding devices
[    35.721] (==) Automatically enabling devices
[    35.722] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    35.722]     Entry deleted from font path.
[    35.722] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    35.722]     Entry deleted from font path.
[    35.722] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    35.722]     Entry deleted from font path.
[    35.722] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    35.722]     Entry deleted from font path.
[    35.722] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    35.722]     Entry deleted from font path.
[    35.722] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    35.722] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    35.722] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    35.722] (II) Loader magic: 0x81ffde0
[    35.722] (II) Module ABI versions:
[    35.722]     X.Org ANSI C Emulation: 0.4
[    35.722]     X.Org Video Driver: 10.0
[    35.722]     X.Org XInput driver : 12.3
[    35.723]     X.Org Server Extension : 5.0
[    35.728] (--) PCI:*(0:0:1:0) 8086:7125:0e11:b165 rev 3, Mem @ 0x44000000/67108864, 0x40100000/524288
[    35.732] (II) Open ACPI successful (/var/run/acpid.socket)
[    35.732] (II) LoadModule: "extmod"
[    35.751] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    35.752] (II) Module extmod: vendor="X.Org Foundation"
[    35.752]     compiled for 1.10.1, module version = 1.0.0
[    35.752]     Module class: X.Org Server Extension
[    35.752]     ABI class: X.Org Server Extension, version 5.0
[    35.752] (II) Loading extension MIT-SCREEN-SAVER
[    35.752] (II) Loading extension XFree86-VidModeExtension
[    35.752] (II) Loading extension XFree86-DGA
[    35.752] (II) Loading extension DPMS
[    35.752] (II) Loading extension XVideo
[    35.753] (II) Loading extension XVideo-MotionCompensation
[    35.753] (II) Loading extension X-Resource
[    35.753] (II) LoadModule: "dbe"
[    35.753] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    35.753] (II) Module dbe: vendor="X.Org Foundation"
[    35.754]     compiled for 1.10.1, module version = 1.0.0
[    35.754]     Module class: X.Org Server Extension
[    35.754]     ABI class: X.Org Server Extension, version 5.0
[    35.754] (II) Loading extension DOUBLE-BUFFER
[    35.754] (II) LoadModule: "glx"
[    35.754] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    35.755] (II) Module glx: vendor="X.Org Foundation"
[    35.755]     compiled for 1.10.1, module version = 1.0.0
[    35.755]     ABI class: X.Org Server Extension, version 5.0
[    35.755] (==) AIGLX enabled
[    35.755] (II) Loading extension GLX
[    35.755] (II) LoadModule: "record"
[    35.760] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    35.761] (II) Module record: vendor="X.Org Foundation"
[    35.761]     compiled for 1.10.1, module version = 1.13.0
[    35.761]     Module class: X.Org Server Extension
[    35.761]     ABI class: X.Org Server Extension, version 5.0
[    35.761] (II) Loading extension RECORD
[    35.761] (II) LoadModule: "dri"
[    35.761] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    35.762] (II) Module dri: vendor="X.Org Foundation"
[    35.762]     compiled for 1.10.1, module version = 1.0.0
[    35.762]     ABI class: X.Org Server Extension, version 5.0
[    35.762] (II) Loading extension XFree86-DRI
[    35.762] (II) LoadModule: "dri2"
[    35.763] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    35.763] (II) Module dri2: vendor="X.Org Foundation"
[    35.763]     compiled for 1.10.1, module version = 1.2.0
[    35.763]     ABI class: X.Org Server Extension, version 5.0
[    35.763] (II) Loading extension DRI2
[    35.763] (==) Matched intel as autoconfigured driver 0
[    35.763] (==) Matched vesa as autoconfigured driver 1
[    35.763] (==) Matched fbdev as autoconfigured driver 2
[    35.773] (==) Assigned the driver to the xf86ConfigLayout
[    35.773] (II) LoadModule: "intel"
[    35.849] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    35.850] (II) Module intel: vendor="X.Org Foundation"
[    35.850]     compiled for 1.10.1, module version = 2.14.0
[    35.850]     Module class: X.Org Video Driver
[    35.850]     ABI class: X.Org Video Driver, version 10.0
[    35.850] (II) LoadModule: "vesa"
[    35.851] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    35.851] (II) Module vesa: vendor="X.Org Foundation"
[    35.852]     compiled for 1.10.0, module version = 2.3.0
[    35.854]     Module class: X.Org Video Driver
[    35.855]     ABI class: X.Org Video Driver, version 10.0
[    35.855] (II) LoadModule: "fbdev"
[    35.856] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    35.856] (II) Module fbdev: vendor="X.Org Foundation"
[    35.856]     compiled for 1.10.0, module version = 0.4.2
[    35.857]     ABI class: X.Org Video Driver, version 10.0
[    35.857] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    35.859] (II) VESA: driver for VESA chipsets: vesa
[    35.859] (II) FBDEV: driver for framebuffer: fbdev
[    35.859] (++) using VT number 7

[    36.481] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    36.482] (WW) Falling back to old probe method for vesa
[    36.482] (WW) Falling back to old probe method for fbdev
[    36.482] (II) Loading sub module "fbdevhw"
[    36.482] (II) LoadModule: "fbdevhw"
[    36.483] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    36.483] (II) Module fbdevhw: vendor="X.Org Foundation"
[    36.483]     compiled for 1.10.1, module version = 0.0.2
[    36.483]     ABI class: X.Org Video Driver, version 10.0
[    36.483] (EE) open /dev/fb0: No such file or directory
[    36.483] (II) Loading sub module "vgahw"
[    36.484] (II) LoadModule: "vgahw"
[    36.484] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    36.485] (II) Module vgahw: vendor="X.Org Foundation"
[    36.485]     compiled for 1.10.1, module version = 0.1.0
[    36.485]     ABI class: X.Org Video Driver, version 10.0
[    36.485] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 16/16
[    36.485] (==) intel(0): Depth 16, (==) framebuffer bpp 16
[    36.485] (==) intel(0): RGB weight 565
[    36.485] (==) intel(0): Default visual is TrueColor
[    36.485] (II) Loading sub module "xaa"
[    36.485] (II) LoadModule: "xaa"
[    36.486] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    36.487] (II) Module xaa: vendor="X.Org Foundation"
[    36.487]     compiled for 1.10.1, module version = 1.2.1
[    36.487]     ABI class: X.Org Video Driver, version 10.0
[    36.487] (II) Loading sub module "vbe"
[    36.487] (II) LoadModule: "vbe"
[    36.487] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    36.488] (II) Module vbe: vendor="X.Org Foundation"
[    36.488]     compiled for 1.10.1, module version = 1.1.0
[    36.488]     ABI class: X.Org Video Driver, version 10.0
[    36.488] (II) Loading sub module "int10"
[    36.488] (II) LoadModule: "int10"
[    36.488] (II) Loading /usr/lib/xorg/modules/libint10.so
[    36.489] (II) Module int10: vendor="X.Org Foundation"
[    36.489]     compiled for 1.10.1, module version = 1.0.0
[    36.489]     ABI class: X.Org Video Driver, version 10.0
[    36.489] (II) intel(0): initializing int10
[    36.491] (II) intel(0): Primary V_BIOS segment is: 0xc000
[    36.492] (II) intel(0): VESA BIOS detected
[    36.492] (II) intel(0): VESA VBE Version 3.0
[    36.492] (II) intel(0): VESA VBE Total Mem: 1024 kB
[    36.492] (II) intel(0): VESA VBE OEM: Intel(R) 8xx Chipset Video BIOS
[    36.492] (II) intel(0): VESA VBE OEM Software Rev: 33.118
[    36.492] (II) intel(0): VESA VBE OEM Vendor: Intel Corporation
[    36.492] (II) intel(0): VESA VBE OEM Product: Intel(R) 8xx Chipset
[    36.492] (II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    36.492] (II) Loading sub module "ddc"
[    36.492] (II) LoadModule: "ddc"
[    36.492] (II) Module "ddc" already built-in
[    36.516] (II) intel(0): VESA VBE DDC supported
[    36.516] (II) intel(0): VESA VBE DDC Level 2
[    36.516] (II) intel(0): VESA VBE DDC transfer in appr. 1 sec.
[    37.261] (II) intel(0): VESA VBE DDC read successfully
[    37.261] (II) intel(0): Manufacturer: PTS  Model: 651  Serial#: 870001951
[    37.261] (II) intel(0): Year: 2007  Week: 52
[    37.261] (II) intel(0): EDID Version: 1.3
[    37.261] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    37.261] (II) intel(0): Sync:  Separate
[    37.262] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 20
[    37.262] (II) intel(0): Gamma: 2.37
[    37.262] (II) intel(0): DPMS capabilities: Off; RGB/Color Display
[    37.262] (II) intel(0): First detailed timing is preferred mode
[    37.262] (II) intel(0): redX: 0.600 redY: 0.346   greenX: 0.312 greenY: 0.538
[    37.262] (II) intel(0): blueX: 0.137 blueY: 0.137   whiteX: 0.998 whiteY: 0.997
[    37.262] (II) intel(0): Supported established timings:
[    37.262] (II) intel(0): 720x400@70Hz
[    37.262] (II) intel(0): 720x400@88Hz
[    37.262] (II) intel(0): 640x480@60Hz
[    37.262] (II) intel(0): 640x480@67Hz
[    37.262] (II) intel(0): 640x480@72Hz
[    37.262] (II) intel(0): 640x480@75Hz
[    37.262] (II) intel(0): 800x600@56Hz
[    37.262] (II) intel(0): 800x600@60Hz
[    37.262] (II) intel(0): 800x600@72Hz
[    37.262] (II) intel(0): 800x600@75Hz
[    37.262] (II) intel(0): 832x624@75Hz
[    37.262] (II) intel(0): 1024x768@87Hz (interlaced)
[    37.262] (II) intel(0): 1024x768@60Hz
[    37.262] (II) intel(0): 1024x768@70Hz
[    37.262] (II) intel(0): 1024x768@75Hz
[    37.263] (II) intel(0): 1280x1024@75Hz
[    37.263] (II) intel(0): 1152x864@75Hz
[    37.263] (II) intel(0): Manufacturer's mask: 7F
[    37.263] (II) intel(0): Supported standard timings:
[    37.263] (II) intel(0): #0: hsize: 2288  vsize 1287  refresh: 123  vid: 65535
[    37.263] (II) intel(0): #1: hsize: 2288  vsize 1287  refresh: 123  vid: 65535
[    37.263] (II) intel(0): #2: hsize: 2288  vsize 1287  refresh: 123  vid: 65535
[    37.263] (II) intel(0): #3: hsize: 2288  vsize 1287  refresh: 123  vid: 65535
[    37.263] (II) intel(0): #4: hsize: 2288  vsize 1287  refresh: 123  vid: 65535
[    37.263] (II) intel(0): #5: hsize: 2288  vsize 1287  refresh: 123  vid: 65535
[    37.263] (II) intel(0): #6: hsize: 2288  vsize 1287  refresh: 123  vid: 65535
[    37.263] (II) intel(0): #7: hsize: 2288  vsize 1287  refresh: 123  vid: 65535
[    37.263] (II) intel(0): Supported detailed timing:
[    37.263] (II) intel(0): clock: 655.4 MHz   Image Size:  4095 x 4095 mm
[    37.263] (II) intel(0): h_active: 4095  h_sync: 5118  h_sync_end 6141 h_blank_end 8190 h_border: 255
[    37.263] (II) intel(0): v_active: 4095  v_sync: 4158  v_sync_end 4221 v_blanking: 8190 v_border: 255
[    37.263] (II) intel(0): Stereo: left channel on sync
[    37.263] side-by-side interleaved(II) intel(0): Supported detailed timing:
[    37.263] (II) intel(0): clock: 655.4 MHz   Image Size:  4095 x 4095 mm
[    37.263] (II) intel(0): h_active: 4095  h_sync: 5118  h_sync_end 6141 h_blank_end 8190 h_border: 255
[    37.264] (II) intel(0): v_active: 4095  v_sync: 4158  v_sync_end 4221 v_blanking: 8190 v_border: 255
[    37.264] (II) intel(0): Stereo: left channel on sync
[    37.264] side-by-side interleaved(II) intel(0): Supported detailed timing:
[    37.264] (II) intel(0): clock: 655.4 MHz   Image Size:  4095 x 4095 mm
[    37.264] (II) intel(0): h_active: 4095  h_sync: 5118  h_sync_end 6141 h_blank_end 8190 h_border: 255
[    37.264] (II) intel(0): v_active: 4095  v_sync: 4158  v_sync_end 4221 v_blanking: 8190 v_border: 255
[    37.264] (II) intel(0): Stereo: left channel on sync
[    37.264] side-by-side interleaved(II) intel(0): Supported detailed timing:
[    37.264] (II) intel(0): clock: 655.4 MHz   Image Size:  4095 x 4095 mm
[    37.264] (II) intel(0): h_active: 4095  h_sync: 5118  h_sync_end 6141 h_blank_end 8190 h_border: 255
[    37.264] (II) intel(0): v_active: 4095  v_sync: 4158  v_sync_end 4221 v_blanking: 8190 v_border: 255
[    37.264] (II) intel(0): Stereo: left channel on sync
[    37.264] side-by-side interleaved(II) intel(0): Number of EDID sections to follow: -1
[    37.264] (II) intel(0): EDID (in hex):
[    37.264] (II) intel(0):     00ffffffffffff00429351061f2ddb33
[    37.265] (II) intel(0):     34110103082114892aaf0999584f8923
[    37.265] (II) intel(0):     23ffffffffffffffffffffffffffffff
[    37.265] (II) intel(0):     ffffffffffffffffffffffffffffffff
[    37.265] (II) intel(0):     ffffffffffffffffffffffffffffffff
[    37.265] (II) intel(0):     ffffffffffffffffffffffffffffffff
[    37.265] (II) intel(0):     ffffffffffffffffffffffffffffffff
[    37.265] (II) intel(0):     ffffffffffffffffffffffffffffffff
[    37.265] (II) intel(0): EDID vendor "PTS", prod id 1617
[    37.265] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[    37.265] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[    37.265] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[    37.265] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[    37.265] (II) intel(0): Printing DDC gathered Modelines:
[    37.265] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    37.265] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    37.265] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    37.266] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    37.266] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    37.266] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    37.266] (II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
[    37.266] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    37.266] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    37.266] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    37.266] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    37.266] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    37.266] (II) intel(0): Modeline "1024x768i"x0.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
[    37.266] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    37.266] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    37.266] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    37.266] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    37.266] (II) intel(0): Modeline "2288x1287"x123.0  540.84  2288 2480 2736 3184  1287 1288 1291 1381 -hsync +vsync (169.9 kHz)
[    37.267] (II) intel(0): Integrated Graphics Chipset: Intel(R) i810e
[    37.267] (--) intel(0): Chipset: "i810e"
[    37.267] (--) intel(0): Linear framebuffer at 0x44000000
[    37.267] (--) intel(0): IO registers at addr 0x40100000
[    37.267] (II) intel(0): Kernel reported 75520 total, 0 used
[    37.267] (II) intel(0): I810CheckAvailableMemory: 302080k available
[    37.267] (==) intel(0): Will alloc AGP framebuffer: 24576 kByte
[    37.267] (==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
[    37.267] (II) intel(0): <default monitor>: Using hsync range of 31.47-169.86 kHz
[    37.267] (II) intel(0): <default monitor>: Using vrefresh range of 43.48-123.00 Hz
[    37.268] (WW) intel(0): Unable to estimate virtual size
[    37.268] (II) intel(0): Clock range:   9.50 to 163.00 MHz
[    37.268] (II) intel(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
[    37.268] (II) intel(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
[    37.268] (II) intel(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
[    37.268] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    37.268] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    37.268] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    37.268] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    37.268] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    37.268] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    37.268] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    37.268] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    37.268] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    37.268] (II) intel(0): Not using default mode "1024x768i" (unknown reason)
[    37.268] (II) intel(0): Not using default mode "512x384i" (bad mode clock/interlace/doublescan)
[    37.268] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    37.268] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[    37.269] (II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    37.270] (II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
[    37.270] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
[    37.271] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
[    37.271] (II) intel(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
[    37.271] (II) intel(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[    37.271] (II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    37.272] (II) intel(0): Not using driver mode "1024x768i" (unknown reason)
[    37.272] (II) intel(0): Not using driver mode "2288x1287" (bad mode clock/interlace/doublescan)
[    37.272] (--) intel(0): Virtual size is 1680x1200 (pitch 2048)
[    37.272] (**) intel(0): *Default mode "1600x1200": 162.0 MHz, 75.0 kHz, 60.0 Hz
[    37.272] (II) intel(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    37.272] (**) intel(0): *Default mode "1680x1050": 146.2 MHz, 65.3 kHz, 60.0 Hz
[    37.272] (II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    37.273] (**) intel(0): *Default mode "1400x1050": 155.8 MHz, 81.5 kHz, 74.8 Hz
[    37.273] (II) intel(0): Modeline "1400x1050"x74.8  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync (81.5 kHz)
[    37.273] (**) intel(0): *Default mode "1400x1050": 145.1 MHz, 76.5 kHz, 70.0 Hz
[    37.273] (II) intel(0): Modeline "1400x1050"x70.0  145.06  1400 1496 1648 1896  1050 1051 1054 1093 -hsync +vsync (76.5 kHz)
[    37.273] (**) intel(0): *Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
[    37.273] (II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
[    37.273] (**) intel(0): *Driver mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
[    37.273] (II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    37.273] (**) intel(0): *Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
[    37.273] (II) intel(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
[    37.273] (**) intel(0): *Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
[    37.273] (II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    37.273] (**) intel(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
[    37.273] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    37.273] (**) intel(0): *Default mode "1440x900": 106.5 MHz, 55.9 kHz, 59.9 Hz
[    37.273] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    37.273] (**) intel(0): *Default mode "1280x960": 148.5 MHz, 85.9 kHz, 85.0 Hz
[    37.274] (II) intel(0): Modeline "1280x960"x85.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
[    37.274] (**) intel(0): *Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
[    37.274] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    37.278] (**) intel(0): *Default mode "1360x768": 84.8 MHz, 47.7 kHz, 59.8 Hz
[    37.278] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    37.278] (**) intel(0): *Driver mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
[    37.278] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    37.278] (**) intel(0): *Default mode "1152x864": 143.5 MHz, 91.5 kHz, 100.0 Hz
[    37.278] (II) intel(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 -hsync +vsync (91.5 kHz)
[    37.278] (**) intel(0): *Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
[    37.278] (II) intel(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
[    37.278] (**) intel(0): *Default mode "1152x864": 119.7 MHz, 77.1 kHz, 85.0 Hz
[    37.278] (II) intel(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
[    37.278] (**) intel(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
[    37.278] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    37.278] (**) intel(0): *Default mode "1152x864": 105.0 MHz, 67.6 kHz, 75.0 Hz
[    37.279] (II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
[    37.279] (**) intel(0): *Default mode "1152x864": 96.8 MHz, 63.0 kHz, 70.0 Hz
[    37.279] (II) intel(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
[    37.279] (**) intel(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
[    37.279] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    37.279] (**) intel(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[    37.279] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    37.279] (**) intel(0): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[    37.279] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    37.279] (**) intel(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    37.279] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    37.279] (**) intel(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
[    37.279] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[    37.279] (**) intel(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[    37.279] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    37.279] (**) intel(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[    37.279] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    37.279] (**) intel(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    37.280] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    37.280] (**) intel(0): *Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
[    37.280] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    37.280] (**) intel(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
[    37.280] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    37.280] (**) intel(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[    37.280] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    37.280] (**) intel(0): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
[    37.280] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    37.280] (**) intel(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    37.280] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    37.280] (**) intel(0): *Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[    37.280] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    37.280] (**) intel(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
[    37.280] (II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[    37.280] (**) intel(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[    37.281] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    37.281] (**) intel(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
[    37.281] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    37.281] (**) intel(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    37.281] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    37.281] (**) intel(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[    37.281] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    37.281] (**) intel(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[    37.281] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    37.281] (**) intel(0): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[    37.281] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    37.281] (**) intel(0): *Driver mode "640x480": 30.2 MHz, 35.0 kHz, 66.7 Hz
[    37.281] (II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    37.281] (**) intel(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    37.281] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    37.281] (**) intel(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
[    37.281] (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[    37.281] (**) intel(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[    37.282] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    37.282] (**) intel(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[    37.282] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    37.282] (**) intel(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    37.282] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    37.282] (**) intel(0): *Driver mode "720x400": 35.5 MHz, 39.4 kHz, 87.8 Hz
[    37.282] (II) intel(0): Modeline "720x400"x87.8   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
[    37.282] (**) intel(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
[    37.282] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    37.282] (**) intel(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
[    37.282] (II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[    37.282] (**) intel(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
[    37.282] (II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[    37.282] (**) intel(0): *Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
[    37.282] (II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[    37.282] (**) intel(0): Display dimensions: (330, 200) mm
[    37.286] (**) intel(0): DPI set to (129, 152)
[    37.286] (II) Loading sub module "fb"
[    37.286] (II) LoadModule: "fb"
[    37.287] (II) Loading /usr/lib/xorg/modules/libfb.so
[    37.287] (II) Module fb: vendor="X.Org Foundation"
[    37.287]     compiled for 1.10.1, module version = 1.0.0
[    37.288]     ABI class: X.Org ANSI C Emulation, version 0.4
[    37.288] (II) Loading sub module "ramdac"
[    37.288] (II) LoadModule: "ramdac"
[    37.288] (II) Module "ramdac" already built-in
[    37.288] (**) intel(0): page flipping disabled
[    37.288] (II) intel(0): XvMC is Disabled: use XvMCSurfaces config option to enable.
[    37.288] (II) UnloadModule: "vesa"
[    37.288] (II) Unloading vesa
[    37.288] (II) UnloadModule: "fbdev"
[    37.288] (II) Unloading fbdev
[    37.288] (II) UnloadModule: "fbdevhw"
[    37.288] (II) Unloading fbdevhw
[    37.288] drmOpenDevice: node name is /dev/dri/card0
[    37.294] drmOpenDevice: node name is /dev/dri/card0
[    37.599] drmOpenByBusid: Searching for BusID pci:0000:00:01.0
[    37.599] drmOpenDevice: node name is /dev/dri/card0
[    37.599] drmOpenDevice: open result is 12, (OK)
[    37.599] drmOpenByBusid: drmOpenMinor returns 12
[    37.599] drmOpenByBusid: drmGetBusid reports pci:0000:00:01.0
[    37.599] (II) [drm] loaded kernel module for "i810" driver.
[    37.599] (II) [drm] DRM interface version 1.4
[    37.600] (II) [drm] DRM open master succeeded.
[    37.600] (II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
[    37.600] (II) intel(0): [drm] framebuffer handle = 0x44000000
[    37.600] (II) intel(0): [drm] added 1 reserved context for kernel
[    37.601] (II) intel(0): X context handle = 0x1
[    37.601] (II) intel(0): [drm] installed DRM signal handler
[    37.601] (II) intel(0): [drm] Registers = 0x40100000
[    37.601] (II) intel(0): [agp] dcacheHandle : 0x0
[    37.601] (II) intel(0): [agp] GART: no dcache memory found
[    37.659] (II) intel(0): [agp] Bound backbuffer memory
[    37.696] (II) intel(0): [agp] Bound depthbuffer memory
[    37.847] (II) intel(0): [agp] Bound System Texture Memory
[    37.847] (II) intel(0): [agp] GART: Allocated 4K for mouse cursor image
[    37.852] (II) intel(0): [agp] GART: Allocated 16K for ARGB mouse cursor image
[    37.852] (II) intel(0): Adding 384 scanlines for pixmap caching
[    37.852] (II) intel(0): Allocated Scratch Memory
[    37.852] (II) intel(0): [dri] Buffer map : d9b000
[    37.852] (II) intel(0): [drm] added 256 4096 byte DMA buffers
[    37.852] (II) intel(0): [drm] Init v1.4 interface.
[    37.858] (II) intel(0): [drm] dma control initialized, using IRQ -22
[    37.858] (II) intel(0): [dri] visual configs initialized.
[    37.875] (II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    37.970] (II) intel(0): Setting dot clock to 162.0 MHz [ 0x19 0x6 0x10 ] [ 27 8 1 ]
[    37.970] (II) intel(0): chose watermark 0x22416000: (tab.freq 162.0)
[    38.023] (II) intel(0): Using XFree86 Acceleration Architecture (XAA)
[    38.023]     Screen to screen bit blits
[    38.023]     Solid filled rectangles
[    38.023]     8x8 mono pattern filled rectangles
[    38.023]     Indirect CPU to Screen color expansion
[    38.023]     Solid Horizontal and Vertical Lines
[    38.023]     Setting up tile and stipple cache:
[    38.023]         32 128x128 slots
[    38.024]         8 256x256 slots
[    38.024] (==) intel(0): Backing store disabled
[    38.024] (==) intel(0): Silken mouse enabled
[    38.024] (==) intel(0): DPMS enabled
[    38.024] (II) intel(0): [DRI] installation complete
[    38.025] (II) intel(0): Direct rendering enabled
[    38.025] (==) RandR enabled
[    38.025] (II) Initializing built-in extension Generic Event Extension
[    38.025] (II) Initializing built-in extension SHAPE
[    38.025] (II) Initializing built-in extension MIT-SHM
[    38.025] (II) Initializing built-in extension XInputExtension
[    38.025] (II) Initializing built-in extension XTEST
[    38.025] (II) Initializing built-in extension BIG-REQUESTS
[    38.025] (II) Initializing built-in extension SYNC
[    38.025] (II) Initializing built-in extension XKEYBOARD
[    38.025] (II) Initializing built-in extension XC-MISC
[    38.025] (II) Initializing built-in extension SECURITY
[    38.025] (II) Initializing built-in extension XINERAMA
[    38.025] (II) Initializing built-in extension XFIXES
[    38.025] (II) Initializing built-in extension RENDER
[    38.025] (II) Initializing built-in extension RANDR
[    38.025] (II) Initializing built-in extension COMPOSITE
[    38.025] (II) Initializing built-in extension DAMAGE
[    38.025] (II) Initializing built-in extension GESTURE
[    38.097] (II) AIGLX: Screen 0 is not DRI2 capable
[    38.097] drmOpenDevice: node name is /dev/dri/card0
[    38.097] drmOpenDevice: open result is 13, (OK)
[    41.096] drmOpenByBusid: Searching for BusID pci:0000:00:01.0
[    41.179] drmOpenDevice: node name is /dev/dri/card0
[    41.179] drmOpenDevice: open result is 13, (OK)
[    41.179] drmOpenByBusid: drmOpenMinor returns 13
[    41.179] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    41.179] drmOpenByBusid: drmGetBusid reports pci:0000:00:01.0
[    41.179] (II) AIGLX: Trying DRI driver /usr/lib/dri/i810_dri.so
[    41.231] (II) AIGLX: Loaded and initialized i810
[    41.231] (II) GLX: Initialized DRI GL provider for screen 0
[    41.282] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    41.311] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    41.311] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    41.311] (II) LoadModule: "evdev"
[    41.311] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    41.313] (II) Module evdev: vendor="X.Org Foundation"
[    41.313]     compiled for 1.10.0.902, module version = 2.6.0
[    41.313]     Module class: X.Org XInput Driver
[    41.313]     ABI class: X.Org XInput driver, version 12.3
[    41.313] (II) Using input driver 'evdev' for 'Power Button'
[    41.313] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    41.313] (**) Power Button: always reports core events
[    41.313] (**) Power Button: Device: "/dev/input/event1"
[    41.314] (--) Power Button: Found keys
[    41.314] (II) Power Button: Configuring as keyboard
[    41.314] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    41.314] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    41.314] (**) Option "xkb_rules" "evdev"
[    41.314] (**) Option "xkb_model" "pc105"
[    41.314] (**) Option "xkb_layout" "us"
[    41.319] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    41.319] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    41.319] (II) Using input driver 'evdev' for 'Power Button'
[    41.319] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    41.319] (**) Power Button: always reports core events
[    41.319] (**) Power Button: Device: "/dev/input/event0"
[    41.320] (--) Power Button: Found keys
[    41.320] (II) Power Button: Configuring as keyboard
[    41.320] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    41.320] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    41.320] (**) Option "xkb_rules" "evdev"
[    41.320] (**) Option "xkb_model" "pc105"
[    41.320] (**) Option "xkb_layout" "us"
[    41.336] (II) config/udev: Adding input device Microsoft Microsoft Optical Mouse with Tilt Wheel (/dev/input/event3)
[    41.336] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: Applying InputClass "evdev pointer catchall"
[    41.336] (II) Using input driver 'evdev' for 'Microsoft Microsoft Optical Mouse with Tilt Wheel'
[    41.336] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    41.336] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: always reports core events
[    41.337] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: Device: "/dev/input/event3"
[    41.337] (--) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found 9 mouse buttons
[    41.337] (--) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found scroll wheel(s)
[    41.337] (--) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found relative axes
[    41.337] (--) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found x and y relative axes
[    41.337] (II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Configuring as mouse
[    41.337] (II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Adding scrollwheel support
[    41.337] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: YAxisMapping: buttons 4 and 5
[    41.337] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    41.337] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1f.2/usb1/1-1/1-1.3/1-1.3:1.0/input/input3/event3"
[    41.337] (II) XINPUT: Adding extended input device "Microsoft Microsoft Optical Mouse with Tilt Wheel" (type: MOUSE)
[    41.337] (II) Microsoft Microsoft Optical Mouse with Tilt Wheel: initialized for relative axes.
[    41.338] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) keeping acceleration scheme 1
[    41.338] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) acceleration profile 0
[    41.338] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) acceleration factor: 2.000
[    41.338] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) acceleration threshold: 4
[    41.339] (II) config/udev: Adding input device Microsoft Microsoft Optical Mouse with Tilt Wheel (/dev/input/mouse0)
[    41.339] (II) No input driver/identifier specified (ignoring)
[    41.343] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    41.343] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    41.343] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    41.343] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    41.343] (**) AT Translated Set 2 keyboard: always reports core events
[    41.343] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    41.344] (--) AT Translated Set 2 keyboard: Found keys
[    41.344] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    41.344] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    41.344] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    41.344] (**) Option "xkb_rules" "evdev"
[    41.344] (**) Option "xkb_model" "pc105"
[    41.344] (**) Option "xkb_layout" "us"
[    45.604] (II) intel(0): Setting dot clock to 108.0 MHz [ 0x10 0x2 0x20 ] [ 18 4 2 ]
[    45.604] (II) intel(0): chose watermark 0x22210000: (tab.freq 108.0)

```

---

### Post by Gus Polly on 2011-07-29
Now after rebooting with the monitor off, and waiting until it was fully booted to turn it back on, now it loads 1280x800 again. How can I keep this configuration from disappearing whenever I reboot?

```

[    35.847] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    36.015] X Protocol Version 11, Revision 0
[    36.015] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    36.015] Current Operating System: Linux home 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686
[    36.015] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=0a8255a4-4395-4e62-875d-b0400dae7fa1 ro splash vga=795 quiet splash vt.handoff=7
[    36.015] Build Date: 21 May 2011  11:38:35AM
[    36.015] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    36.126] Current version of pixman: 0.20.2
[    36.128]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    36.128] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    36.129] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 28 23:30:33 2011
[    36.244] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    36.410] (==) No Layout section.  Using the first Screen section.
[    36.410] (==) No screen section available. Using defaults.
[    36.410] (**) |-->Screen "Default Screen Section" (0)
[    36.410] (**) |   |-->Monitor "<default monitor>"
[    36.433] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    36.433] (==) Automatically adding devices
[    36.433] (==) Automatically enabling devices
[    36.529] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    36.529]     Entry deleted from font path.
[    36.529] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    36.529]     Entry deleted from font path.
[    36.529] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    36.529]     Entry deleted from font path.
[    36.545] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    36.545]     Entry deleted from font path.
[    36.545] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    36.545]     Entry deleted from font path.
[    36.803] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    36.803] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    36.803] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    36.803] (II) Loader magic: 0x81ffde0
[    36.803] (II) Module ABI versions:
[    36.803]     X.Org ANSI C Emulation: 0.4
[    36.803]     X.Org Video Driver: 10.0
[    36.803]     X.Org XInput driver : 12.3
[    36.803]     X.Org Server Extension : 5.0
[    36.805] (--) PCI:*(0:0:1:0) 8086:7125:0e11:b165 rev 3, Mem @ 0x44000000/67108864, 0x40100000/524288
[    36.806] (II) Open ACPI successful (/var/run/acpid.socket)
[    36.806] (II) LoadModule: "extmod"
[    37.007] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    37.187] (II) Module extmod: vendor="X.Org Foundation"
[    37.187]     compiled for 1.10.1, module version = 1.0.0
[    37.187]     Module class: X.Org Server Extension
[    37.187]     ABI class: X.Org Server Extension, version 5.0
[    37.187] (II) Loading extension MIT-SCREEN-SAVER
[    37.188] (II) Loading extension XFree86-VidModeExtension
[    37.188] (II) Loading extension XFree86-DGA
[    37.234] (II) Loading extension DPMS
[    37.234] (II) Loading extension XVideo
[    37.234] (II) Loading extension XVideo-MotionCompensation
[    37.234] (II) Loading extension X-Resource
[    37.234] (II) LoadModule: "dbe"
[    37.235] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    37.258] (II) Module dbe: vendor="X.Org Foundation"
[    37.258]     compiled for 1.10.1, module version = 1.0.0
[    37.258]     Module class: X.Org Server Extension
[    37.258]     ABI class: X.Org Server Extension, version 5.0
[    37.258] (II) Loading extension DOUBLE-BUFFER
[    37.258] (II) LoadModule: "glx"
[    37.259] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    37.310] (II) Module glx: vendor="X.Org Foundation"
[    37.310]     compiled for 1.10.1, module version = 1.0.0
[    37.310]     ABI class: X.Org Server Extension, version 5.0
[    37.318] (==) AIGLX enabled
[    37.318] (II) Loading extension GLX
[    37.318] (II) LoadModule: "record"
[    37.319] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    37.645] (II) Module record: vendor="X.Org Foundation"
[    37.645]     compiled for 1.10.1, module version = 1.13.0
[    37.645]     Module class: X.Org Server Extension
[    37.646]     ABI class: X.Org Server Extension, version 5.0
[    37.646] (II) Loading extension RECORD
[    37.646] (II) LoadModule: "dri"
[    37.646] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    37.755] (II) Module dri: vendor="X.Org Foundation"
[    37.755]     compiled for 1.10.1, module version = 1.0.0
[    37.755]     ABI class: X.Org Server Extension, version 5.0
[    37.755] (II) Loading extension XFree86-DRI
[    37.755] (II) LoadModule: "dri2"
[    37.756] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    37.863] (II) Module dri2: vendor="X.Org Foundation"
[    37.863]     compiled for 1.10.1, module version = 1.2.0
[    37.863]     ABI class: X.Org Server Extension, version 5.0
[    37.863] (II) Loading extension DRI2
[    37.863] (==) Matched intel as autoconfigured driver 0
[    37.863] (==) Matched vesa as autoconfigured driver 1
[    37.863] (==) Matched fbdev as autoconfigured driver 2
[    37.864] (==) Assigned the driver to the xf86ConfigLayout
[    37.864] (II) LoadModule: "intel"
[    38.009] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    38.227] (II) Module intel: vendor="X.Org Foundation"
[    38.227]     compiled for 1.10.1, module version = 2.14.0
[    38.227]     Module class: X.Org Video Driver
[    38.227]     ABI class: X.Org Video Driver, version 10.0
[    38.227] (II) LoadModule: "vesa"
[    38.229] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    38.311] (II) Module vesa: vendor="X.Org Foundation"
[    38.311]     compiled for 1.10.0, module version = 2.3.0
[    38.311]     Module class: X.Org Video Driver
[    38.311]     ABI class: X.Org Video Driver, version 10.0
[    38.311] (II) LoadModule: "fbdev"
[    38.313] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    38.368] (II) Module fbdev: vendor="X.Org Foundation"
[    38.368]     compiled for 1.10.0, module version = 0.4.2
[    38.368]     ABI class: X.Org Video Driver, version 10.0
[    38.368] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    38.371] (II) VESA: driver for VESA chipsets: vesa
[    38.371] (II) FBDEV: driver for framebuffer: fbdev
[    38.371] (++) using VT number 7

[    39.316] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    39.316] (WW) Falling back to old probe method for vesa
[    39.316] (WW) Falling back to old probe method for fbdev
[    39.316] (II) Loading sub module "fbdevhw"
[    39.316] (II) LoadModule: "fbdevhw"
[    39.317] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    39.397] (II) Module fbdevhw: vendor="X.Org Foundation"
[    39.398]     compiled for 1.10.1, module version = 0.0.2
[    39.398]     ABI class: X.Org Video Driver, version 10.0
[    39.398] (EE) open /dev/fb0: No such file or directory
[    39.398] (II) Loading sub module "vgahw"
[    39.398] (II) LoadModule: "vgahw"
[    39.399] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    39.414] (II) Module vgahw: vendor="X.Org Foundation"
[    39.414]     compiled for 1.10.1, module version = 0.1.0
[    39.414]     ABI class: X.Org Video Driver, version 10.0
[    39.414] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 16/16
[    39.414] (==) intel(0): Depth 16, (==) framebuffer bpp 16
[    39.414] (==) intel(0): RGB weight 565
[    39.414] (==) intel(0): Default visual is TrueColor
[    39.414] (II) Loading sub module "xaa"
[    39.414] (II) LoadModule: "xaa"
[    39.415] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    39.463] (II) Module xaa: vendor="X.Org Foundation"
[    39.463]     compiled for 1.10.1, module version = 1.2.1
[    39.463]     ABI class: X.Org Video Driver, version 10.0
[    39.463] (II) Loading sub module "vbe"
[    39.463] (II) LoadModule: "vbe"
[    39.464] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    39.517] (II) Module vbe: vendor="X.Org Foundation"
[    39.517]     compiled for 1.10.1, module version = 1.1.0
[    39.517]     ABI class: X.Org Video Driver, version 10.0
[    39.517] (II) Loading sub module "int10"
[    39.517] (II) LoadModule: "int10"
[    39.518] (II) Loading /usr/lib/xorg/modules/libint10.so
[    39.544] (II) Module int10: vendor="X.Org Foundation"
[    39.544]     compiled for 1.10.1, module version = 1.0.0
[    39.544]     ABI class: X.Org Video Driver, version 10.0
[    39.545] (II) intel(0): initializing int10
[    39.555] (II) intel(0): Primary V_BIOS segment is: 0xc000
[    39.557] (II) intel(0): VESA BIOS detected
[    39.557] (II) intel(0): VESA VBE Version 3.0
[    39.557] (II) intel(0): VESA VBE Total Mem: 1024 kB
[    39.557] (II) intel(0): VESA VBE OEM: Intel(R) 8xx Chipset Video BIOS
[    39.557] (II) intel(0): VESA VBE OEM Software Rev: 33.118
[    39.557] (II) intel(0): VESA VBE OEM Vendor: Intel Corporation
[    39.557] (II) intel(0): VESA VBE OEM Product: Intel(R) 8xx Chipset
[    39.557] (II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    39.557] (II) Loading sub module "ddc"
[    39.557] (II) LoadModule: "ddc"
[    39.557] (II) Module "ddc" already built-in
[    39.607] (II) intel(0): VESA VBE DDC supported
[    39.608] (II) intel(0): VESA VBE DDC Level 2
[    39.608] (II) intel(0): VESA VBE DDC transfer in appr. 1 sec.
[    40.207] (II) intel(0): VESA VBE DDC read successfully
[    40.207] (II) intel(0): Manufacturer: PTS  Model: 651  Serial#: 870001951
[    40.207] (II) intel(0): Year: 2007  Week: 52
[    40.207] (II) intel(0): EDID Version: 1.3
[    40.207] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    40.208] (II) intel(0): Sync:  Separate
[    40.208] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 20
[    40.208] (II) intel(0): Gamma: 2.37
[    40.208] (II) intel(0): DPMS capabilities: Off; RGB/Color Display
[    40.208] (II) intel(0): First detailed timing is preferred mode
[    40.208] (II) intel(0): redX: 0.600 redY: 0.346   greenX: 0.312 greenY: 0.538
[    40.208] (II) intel(0): blueX: 0.137 blueY: 0.191   whiteX: 0.307 whiteY: 0.345
[    40.208] (II) intel(0): Supported established timings:
[    40.208] (II) intel(0): 720x400@70Hz
[    40.208] (II) intel(0): 640x480@60Hz
[    40.208] (II) intel(0): 640x480@67Hz
[    40.208] (II) intel(0): 640x480@72Hz
[    40.208] (II) intel(0): 640x480@75Hz
[    40.208] (II) intel(0): 800x600@56Hz
[    40.208] (II) intel(0): 800x600@60Hz
[    40.208] (II) intel(0): 800x600@72Hz
[    40.208] (II) intel(0): 800x600@75Hz
[    40.209] (II) intel(0): 832x624@75Hz
[    40.209] (II) intel(0): 1024x768@60Hz
[    40.209] (II) intel(0): 1024x768@70Hz
[    40.209] (II) intel(0): 1024x768@75Hz
[    40.209] (II) intel(0): Manufacturer's mask: 10
[    40.209] (II) intel(0): Supported detailed timing:
[    40.209] (II) intel(0): clock: 70.0 MHz   Image Size:  332 x 207 mm
[    40.209] (II) intel(0): h_active: 1280  h_sync: 1290  h_sync_end 1300 h_blank_end 1400 h_border: 0
[    40.209] (II) intel(0): v_active: 800  v_sync: 802  v_sync_end 812 v_blanking: 833 v_border: 0
[    40.209] (II) intel(0): Monitor name: TLA-01511C
[    40.209] (II) intel(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 85 MHz
[    40.209] (II) intel(0): Serial No: 6434870000307
[    40.209] (II) intel(0): EDID (in hex):
[    40.209] (II) intel(0):     00ffffffffffff00429351061f2ddb33
[    40.209] (II) intel(0):     34110103082114892aaf0999584f8923
[    40.209] (II) intel(0):     314e58bfee1001010101010101010101
[    40.209] (II) intel(0):     010101010101581b0078502021300a0a
[    40.209] (II) intel(0):     2a004ccf1000001e000000fc00544c41
[    40.210] (II) intel(0):     2d3031353131430a2020000000fd0038
[    40.210] (II) intel(0):     4b1e5008000a202020202020000000ff
[    40.210] (II) intel(0):     003634333438373030303033303700e4
[    40.210] (II) intel(0): EDID vendor "PTS", prod id 1617
[    40.210] (II) intel(0): Using EDID range info for horizontal sync
[    40.210] (II) intel(0): Using EDID range info for vertical refresh
[    40.210] (II) intel(0): Printing DDC gathered Modelines:
[    40.210] (II) intel(0): Modeline "1280x800"x0.0   70.00  1280 1290 1300 1400  800 802 812 833 +hsync +vsync (50.0 kHz)
[    40.210] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    40.210] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    40.210] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    40.210] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    40.210] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    40.210] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    40.210] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    40.210] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    40.211] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    40.211] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    40.211] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    40.211] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    40.211] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    40.211] (II) intel(0): Integrated Graphics Chipset: Intel(R) i810e
[    40.211] (--) intel(0): Chipset: "i810e"
[    40.211] (--) intel(0): Linear framebuffer at 0x44000000
[    40.211] (--) intel(0): IO registers at addr 0x40100000
[    40.212] (II) intel(0): Kernel reported 75520 total, 0 used
[    40.212] (II) intel(0): I810CheckAvailableMemory: 302080k available
[    40.212] (==) intel(0): Will alloc AGP framebuffer: 24576 kByte
[    40.212] (==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
[    40.212] (II) intel(0): <default monitor>: Using hsync range of 30.00-80.00 kHz
[    40.212] (II) intel(0): <default monitor>: Using vrefresh range of 56.00-75.00 Hz
[    40.212] (II) intel(0): <default monitor>: Using maximum pixel clock of 85.00 MHz
[    40.212] (II) intel(0): Estimated virtual size for aspect ratio 1.6500 is 1280x800
[    40.212] (II) intel(0): Clock range:   9.50 to 163.00 MHz
[    40.212] (II) intel(0): Not using default mode "640x350" (vrefresh out of range)
[    40.212] (II) intel(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
[    40.212] (II) intel(0): Not using default mode "640x400" (vrefresh out of range)
[    40.212] (II) intel(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
[    40.212] (II) intel(0): Not using default mode "720x400" (vrefresh out of range)
[    40.212] (II) intel(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
[    40.212] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    40.212] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    40.213] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    40.213] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    40.213] (II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    40.213] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    40.213] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    40.213] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    40.213] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    40.213] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    40.213] (II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    40.213] (II) intel(0): Not using default mode "1024x768i" (unknown reason)
[    40.213] (II) intel(0): Not using default mode "512x384i" (bad mode clock/interlace/doublescan)
[    40.213] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    40.213] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    40.213] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    40.213] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    40.213] (II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    40.213] (II) intel(0): Not using default mode "1152x864" (height too large for virtual size)
[    40.213] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    40.213] (II) intel(0): Not using default mode "1280x960" (height too large for virtual size)
[    40.213] (II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[    40.213] (II) intel(0): Not using default mode "1280x960" (height too large for virtual size)
[    40.214] (II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[    40.214] (II) intel(0): Not using default mode "1280x1024" (height too large for virtual size)
[    40.214] (II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[    40.214] (II) intel(0): Not using default mode "1280x1024" (height too large for virtual size)
[    40.214] (II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[    40.214] (II) intel(0): Not using default mode "1280x1024" (height too large for virtual size)
[    40.214] (II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[    40.214] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[    40.214] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    40.214] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[    40.214] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    40.214] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[    40.214] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    40.214] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[    40.214] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    40.214] (II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
[    40.214] (II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    40.214] (II) intel(0): Not using default mode "1792x1344" (width too large for virtual size)
[    40.214] (II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[    40.214] (II) intel(0): Not using default mode "1792x1344" (width too large for virtual size)
[    40.214] (II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[    40.214] (II) intel(0): Not using default mode "1856x1392" (width too large for virtual size)
[    40.214] (II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[    40.215] (II) intel(0): Not using default mode "1856x1392" (width too large for virtual size)
[    40.215] (II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[    40.215] (II) intel(0): Not using default mode "1920x1440" (width too large for virtual size)
[    40.215] (II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    40.215] (II) intel(0): Not using default mode "1920x1440" (width too large for virtual size)
[    40.215] (II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    40.215] (II) intel(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
[    40.215] (II) intel(0): Not using default mode "1152x864" (height too large for virtual size)
[    40.215] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    40.215] (II) intel(0): Not using default mode "1152x864" (height too large for virtual size)
[    40.215] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    40.215] (II) intel(0): Not using default mode "1152x864" (height too large for virtual size)
[    40.215] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    40.215] (II) intel(0): Not using default mode "1152x864" (height too large for virtual size)
[    40.215] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    40.215] (II) intel(0): Not using default mode "1152x864" (height too large for virtual size)
[    40.215] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    40.215] (II) intel(0): Not using default mode "1152x864" (height too large for virtual size)
[    40.215] (II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    40.215] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[    40.215] (II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[    40.215] (II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
[    40.215] (II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[    40.216] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[    40.216] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    40.216] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[    40.216] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    40.216] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[    40.216] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    40.216] (II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
[    40.216] (II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    40.216] (II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
[    40.216] (II) intel(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
[    40.216] (II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
[    40.216] (II) intel(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
[    40.216] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[    40.216] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    40.216] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[    40.216] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    40.216] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[    40.217] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    40.217] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[    40.217] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    40.217] (II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
[    40.217] (II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    40.217] (II) intel(0): Not using default mode "1920x1080" (width too large for virtual size)
[    40.217] (II) intel(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
[    40.217] (II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
[    40.217] (II) intel(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
[    40.217] (II) intel(0): Not using default mode "1920x1440" (width too large for virtual size)
[    40.217] (II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    40.217] (II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
[    40.217] (II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    40.217] (II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
[    40.217] (II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    40.217] (II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
[    40.217] (II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    40.218] (--) intel(0): Virtual size is 1280x800 (pitch 1280)
[    40.218] (**) intel(0): *Driver mode "1280x800": 70.0 MHz, 50.0 kHz, 60.0 Hz
[    40.218] (II) intel(0): Modeline "1280x800"x60.0   70.00  1280 1290 1300 1400  800 802 812 833 +hsync +vsync (50.0 kHz)
[    40.218] (**) intel(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[    40.218] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    40.218] (**) intel(0): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[    40.218] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    40.218] (**) intel(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    40.218] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    40.218] (**) intel(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[    40.218] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    40.218] (**) intel(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[    40.218] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    40.218] (**) intel(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    40.218] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    40.218] (**) intel(0): *Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
[    40.218] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    40.218] (**) intel(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
[    40.219] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    40.219] (**) intel(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[    40.219] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    40.219] (**) intel(0): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
[    40.219] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    40.219] (**) intel(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    40.219] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    40.219] (**) intel(0): *Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[    40.219] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    40.219] (**) intel(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[    40.219] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    40.219] (**) intel(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
[    40.219] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    40.219] (**) intel(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    40.219] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    40.219] (**) intel(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[    40.219] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    40.219] (**) intel(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[    40.220] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    40.220] (**) intel(0): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[    40.220] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    40.220] (**) intel(0): *Driver mode "640x480": 30.2 MHz, 35.0 kHz, 66.7 Hz
[    40.220] (II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    40.220] (**) intel(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    40.220] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    40.220] (**) intel(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[    40.220] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    40.220] (**) intel(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[    40.220] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    40.220] (**) intel(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    40.220] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    40.220] (**) intel(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
[    40.220] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    40.220] (**) intel(0): Display dimensions: (330, 200) mm
[    40.220] (**) intel(0): DPI set to (98, 101)
[    40.221] (II) Loading sub module "fb"
[    40.221] (II) LoadModule: "fb"
[    40.221] (II) Loading /usr/lib/xorg/modules/libfb.so
[    40.442] (II) Module fb: vendor="X.Org Foundation"
[    40.442]     compiled for 1.10.1, module version = 1.0.0
[    40.442]     ABI class: X.Org ANSI C Emulation, version 0.4
[    40.442] (II) Loading sub module "ramdac"
[    40.442] (II) LoadModule: "ramdac"
[    40.442] (II) Module "ramdac" already built-in
[    40.442] (**) intel(0): page flipping disabled
[    40.442] (II) intel(0): XvMC is Disabled: use XvMCSurfaces config option to enable.
[    40.442] (II) UnloadModule: "vesa"
[    40.442] (II) Unloading vesa
[    40.442] (II) UnloadModule: "fbdev"
[    40.442] (II) Unloading fbdev
[    40.442] (II) UnloadModule: "fbdevhw"
[    40.442] (II) Unloading fbdevhw
[    40.443] drmOpenDevice: node name is /dev/dri/card0
[    40.448] drmOpenDevice: node name is /dev/dri/card0
[    40.578] drmOpenByBusid: Searching for BusID pci:0000:00:01.0
[    40.579] drmOpenDevice: node name is /dev/dri/card0
[    40.579] drmOpenDevice: open result is 12, (OK)
[    40.579] drmOpenByBusid: drmOpenMinor returns 12
[    40.579] drmOpenByBusid: drmGetBusid reports pci:0000:00:01.0
[    40.579] (II) [drm] loaded kernel module for "i810" driver.
[    40.579] (II) [drm] DRM interface version 1.4
[    40.579] (II) [drm] DRM open master succeeded.
[    40.579] (II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
[    40.579] (II) intel(0): [drm] framebuffer handle = 0x44000000
[    40.580] (II) intel(0): [drm] added 1 reserved context for kernel
[    40.580] (II) intel(0): X context handle = 0x1
[    40.580] (II) intel(0): [drm] installed DRM signal handler
[    40.581] (II) intel(0): [drm] Registers = 0x40100000
[    40.581] (II) intel(0): [agp] dcacheHandle : 0x0
[    40.581] (II) intel(0): [agp] GART: no dcache memory found
[    40.603] (II) intel(0): [agp] Bound backbuffer memory
[    40.625] (II) intel(0): [agp] Bound depthbuffer memory
[    40.741] (II) intel(0): [agp] Bound System Texture Memory
[    40.742] (II) intel(0): [agp] GART: Allocated 4K for mouse cursor image
[    40.742] (II) intel(0): [agp] GART: Allocated 16K for ARGB mouse cursor image
[    40.742] (II) intel(0): Adding 384 scanlines for pixmap caching
[    40.742] (II) intel(0): Allocated Scratch Memory
[    40.742] (II) intel(0): [dri] Buffer map : 10bb000
[    40.743] (II) intel(0): [drm] added 256 4096 byte DMA buffers
[    40.743] (II) intel(0): [drm] Init v1.4 interface.
[    40.747] (II) intel(0): [drm] dma control initialized, using IRQ -22
[    40.747] (II) intel(0): [dri] visual configs initialized.
[    40.765] (II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    40.841] (II) intel(0): Setting dot clock to 70.0 MHz [ 0x21 0x4 0x30 ] [ 35 6 3 ]
[    40.841] (II) intel(0): chose watermark 0x2210e000: (tab.freq 75.0)
[    40.939] (II) intel(0): Using XFree86 Acceleration Architecture (XAA)
[    40.939]     Screen to screen bit blits
[    40.939]     Solid filled rectangles
[    40.939]     8x8 mono pattern filled rectangles
[    40.939]     Indirect CPU to Screen color expansion
[    40.939]     Solid Horizontal and Vertical Lines
[    40.939]     Setting up tile and stipple cache:
[    40.939]         32 128x128 slots
[    40.940]         13 256x256 slots
[    40.940] (==) intel(0): Backing store disabled
[    40.940] (==) intel(0): Silken mouse enabled
[    40.942] (==) intel(0): DPMS enabled
[    40.942] (II) intel(0): [DRI] installation complete
[    40.942] (II) intel(0): Direct rendering enabled
[    40.942] (==) RandR enabled
[    40.942] (II) Initializing built-in extension Generic Event Extension
[    40.942] (II) Initializing built-in extension SHAPE
[    40.942] (II) Initializing built-in extension MIT-SHM
[    40.942] (II) Initializing built-in extension XInputExtension
[    40.942] (II) Initializing built-in extension XTEST
[    40.942] (II) Initializing built-in extension BIG-REQUESTS
[    40.942] (II) Initializing built-in extension SYNC
[    40.942] (II) Initializing built-in extension XKEYBOARD
[    40.942] (II) Initializing built-in extension XC-MISC
[    40.942] (II) Initializing built-in extension SECURITY
[    40.942] (II) Initializing built-in extension XINERAMA
[    40.942] (II) Initializing built-in extension XFIXES
[    40.942] (II) Initializing built-in extension RENDER
[    40.942] (II) Initializing built-in extension RANDR
[    40.943] (II) Initializing built-in extension COMPOSITE
[    40.943] (II) Initializing built-in extension DAMAGE
[    40.943] (II) Initializing built-in extension GESTURE
[    41.019] (II) AIGLX: Screen 0 is not DRI2 capable
[    41.024] drmOpenDevice: node name is /dev/dri/card0
[    41.025] drmOpenDevice: open result is 13, (OK)
[    44.024] drmOpenByBusid: Searching for BusID pci:0000:00:01.0
[    44.024] drmOpenDevice: node name is /dev/dri/card0
[    44.024] drmOpenDevice: open result is 13, (OK)
[    44.024] drmOpenByBusid: drmOpenMinor returns 13
[    44.024] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    44.024] drmOpenByBusid: drmGetBusid reports pci:0000:00:01.0
[    44.024] (II) AIGLX: Trying DRI driver /usr/lib/dri/i810_dri.so
[    44.266] (II) AIGLX: Loaded and initialized i810
[    44.266] (II) GLX: Initialized DRI GL provider for screen 0
[    44.548] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    44.591] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    44.591] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    44.591] (II) LoadModule: "evdev"
[    44.592] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    44.662] (II) Module evdev: vendor="X.Org Foundation"
[    44.662]     compiled for 1.10.0.902, module version = 2.6.0
[    44.662]     Module class: X.Org XInput Driver
[    44.662]     ABI class: X.Org XInput driver, version 12.3
[    44.662] (II) Using input driver 'evdev' for 'Power Button'
[    44.662] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    44.662] (**) Power Button: always reports core events
[    44.663] (**) Power Button: Device: "/dev/input/event1"
[    44.663] (--) Power Button: Found keys
[    44.663] (II) Power Button: Configuring as keyboard
[    44.663] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    44.663] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    44.663] (**) Option "xkb_rules" "evdev"
[    44.663] (**) Option "xkb_model" "pc105"
[    44.663] (**) Option "xkb_layout" "us"
[    44.668] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    44.668] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    44.668] (II) Using input driver 'evdev' for 'Power Button'
[    44.669] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    44.669] (**) Power Button: always reports core events
[    44.669] (**) Power Button: Device: "/dev/input/event0"
[    44.669] (--) Power Button: Found keys
[    44.669] (II) Power Button: Configuring as keyboard
[    44.669] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    44.669] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    44.669] (**) Option "xkb_rules" "evdev"
[    44.669] (**) Option "xkb_model" "pc105"
[    44.669] (**) Option "xkb_layout" "us"
[    44.686] (II) config/udev: Adding input device Microsoft Microsoft Optical Mouse with Tilt Wheel (/dev/input/event3)
[    44.686] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: Applying InputClass "evdev pointer catchall"
[    44.686] (II) Using input driver 'evdev' for 'Microsoft Microsoft Optical Mouse with Tilt Wheel'
[    44.686] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    44.686] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: always reports core events
[    44.686] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: Device: "/dev/input/event3"
[    44.686] (--) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found 9 mouse buttons
[    44.686] (--) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found scroll wheel(s)
[    44.686] (--) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found relative axes
[    44.686] (--) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found x and y relative axes
[    44.686] (II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Configuring as mouse
[    44.687] (II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Adding scrollwheel support
[    44.687] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: YAxisMapping: buttons 4 and 5
[    44.687] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    44.687] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1f.2/usb1/1-1/1-1.3/1-1.3:1.0/input/input3/event3"
[    44.687] (II) XINPUT: Adding extended input device "Microsoft Microsoft Optical Mouse with Tilt Wheel" (type: MOUSE)
[    44.687] (II) Microsoft Microsoft Optical Mouse with Tilt Wheel: initialized for relative axes.
[    44.687] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) keeping acceleration scheme 1
[    44.687] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) acceleration profile 0
[    44.687] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) acceleration factor: 2.000
[    44.687] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) acceleration threshold: 4
[    44.689] (II) config/udev: Adding input device Microsoft Microsoft Optical Mouse with Tilt Wheel (/dev/input/mouse0)
[    44.689] (II) No input driver/identifier specified (ignoring)
[    44.693] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    44.693] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    44.693] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    44.693] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    44.694] (**) AT Translated Set 2 keyboard: always reports core events
[    44.694] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    44.694] (--) AT Translated Set 2 keyboard: Found keys
[    44.694] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    44.694] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    44.694] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    44.694] (**) Option "xkb_rules" "evdev"
[    44.694] (**) Option "xkb_model" "pc105"
[    44.694] (**) Option "xkb_layout" "us"

```

---

### Post by dronkot on 2012-02-11
Have you tried to fix resolution in  /etc/xorg.conf file where is Monitor section?

---


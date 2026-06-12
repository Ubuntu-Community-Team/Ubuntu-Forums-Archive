---
title: "Intel HD 2000 confused by receiver (video problems)"
date: 2012-01-11
forum: Multimedia Software
---

### Post by kenneyjs on 2012-01-11
Good evening all,

I am having problems with ubuntu 11.10 and the integrated HD 2000 video (i3-2100t) being confused by my audio receiver (Marantz NR1501).  I originally set up the machine with a simple acer monitor (1080p resolution) but when I plug it into the receiver which is connected to a projector (PT-AE4000U) the screen is blank.

I added nomodeset to the boot options, and I can see the boot sequence now, and the graphics are visible but cut off (i see a portion of the screen), I assume that this has something to do with the marantz reporting a resolution of 1920x540 (crazy eh)  via the edid. 

Is there a way to trick the intel driver into not checking for an EDID and ignoring it completely?  I have been searching the forums and the web for days, but most options have not made a difference or have been specific to the other graphics card manufacturers.

The goal is making this machine a no-noise htpc running xbmc (which I thought I was at before I plugged it into my real home theater set up).

Any advice would be greatly appreciated!

---

### Post by BicyclerBoy on 2012-01-11
nomodeset will just kill the intel driver & you get the VESA which is limited to 1024x768.

Your half screen/double display seems very similar to another recent forum post (also SNA graphics & HDMI recent kernels..).

Is the projector connected by HDMI ?
Can you connect projector direct to HTPC ?

Your EDID info should be listed in
/var/log/Xorg.0.log..

---

### Post by kenneyjs on 2012-01-12
> **BicyclerBoy said:**
> nomodeset will just kill the intel driver & you get the VESA which is limited to 1024x768.

Your half screen/double display seems very similar to another recent forum post (also SNA graphics & HDMI recent kernels..).

Is the projector connected by HDMI ?
Can you connect projector direct to HTPC ?

Your EDID info should be listed in
/var/log/Xorg.0.log..

Thanks, I didn't realize that nomodeset would kill the intel driver, which means all my attempts with xorg.conf were doomed to fail.  I'll try connecting the projector directly this evening to see what happens as well.  Everything is currently connected via hdmi (hdmi from htpc to receiver and then hdmi to projector).  

Thanks for the info, I'll report back the results later today.

---

### Post by kenneyjs on 2012-01-15
I tried connecting the pc directly to the projector with identical problems.  The screen goes black with no source input.  It happens only moments into booting.  I can get data because I installed x11vnc prior to plugging it into the projector.

This is the results of xrandr -q

```

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 708mm x 398mm
   1920x1080      24.0* 
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)

```Using "sudo get-edid | parse-edid" I get

```

parse-edid: parse-edid version 2.0.0
parse-edid: EDID checksum passed.

    # EDID version 1 revision 3
Section "Monitor"
    # Block type: 2:0 3:fc
    Identifier "NR1501"
    VendorName "MJI"
    ModelName "NR1501"
    # Block type: 2:0 3:fc
    # Block type: 2:0 3:fd
    HorizSync 28-68
    VertRefresh 24-61
    # Max dot clock (video bandwidth) 150 MHz
    # DPMS capabilities: Active off:no  Suspend:no  Standby:no

    Mode     "1920x540"    # vfreq 60.053Hz, hfreq 33.750kHz
        DotClock    74.250000
        HTimings    1920 2008 2052 2200
        VTimings    540 542 547 562
        Flags    "Interlace" "+HSync" "+VSync"
    EndMode
    Mode     "1920x540"    # vfreq 50.044Hz, hfreq 28.125kHz
        DotClock    74.250000
        HTimings    1920 1968 2012 2640
        VTimings    540 542 547 562
        Flags    "Interlace" "+HSync" "+VSync"
    EndMode
    # Block type: 2:0 3:fc
    # Block type: 2:0 3:fd
EndSection

```Here is my Xorg.0.log

```

[    15.358] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    15.358] X Protocol Version 11, Revision 0
[    15.358] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    15.358] Current Operating System: Linux ubuntu 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64
[    15.358] Kernel command line: BOOT_IMAGE=(loop)/casper/vmlinuz boot=casper file=/preseed/ubuntu.seed iso-scan/filename=/boot/iso/s2.iso toram --
[    15.358] Build Date: 19 October 2011  05:21:26AM
[    15.358] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    15.358] Current version of pixman: 0.22.2
[    15.358]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    15.358] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.358] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 15 16:19:45 2012
[    15.360] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.362] (==) No Layout section.  Using the first Screen section.
[    15.362] (==) No screen section available. Using defaults.
[    15.362] (**) |-->Screen "Default Screen Section" (0)
[    15.362] (**) |   |-->Monitor "<default monitor>"
[    15.363] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    15.363] (==) Automatically adding devices
[    15.363] (==) Automatically enabling devices
[    15.370] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.370]     Entry deleted from font path.
[    15.370] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    15.370]     Entry deleted from font path.
[    15.370] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    15.370]     Entry deleted from font path.
[    15.370] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    15.370]     Entry deleted from font path.
[    15.370] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    15.370]     Entry deleted from font path.
[    15.371] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    15.371] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.371] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.371] (II) Loader magic: 0x7e0220
[    15.371] (II) Module ABI versions:
[    15.371]     X.Org ANSI C Emulation: 0.4
[    15.371]     X.Org Video Driver: 10.0
[    15.371]     X.Org XInput driver : 12.3
[    15.371]     X.Org Server Extension : 5.0
[    15.371] (--) PCI:*(0:0:2:0) 8086:0102:8086:2001 rev 9, Mem @ 0xfe000000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[    15.372] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.372] (II) LoadModule: "extmod"
[    15.379] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.381] (II) Module extmod: vendor="X.Org Foundation"
[    15.381]     compiled for 1.10.4, module version = 1.0.0
[    15.381]     Module class: X.Org Server Extension
[    15.381]     ABI class: X.Org Server Extension, version 5.0
[    15.381] (II) Loading extension MIT-SCREEN-SAVER
[    15.381] (II) Loading extension XFree86-VidModeExtension
[    15.381] (II) Loading extension XFree86-DGA
[    15.381] (II) Loading extension DPMS
[    15.381] (II) Loading extension XVideo
[    15.381] (II) Loading extension XVideo-MotionCompensation
[    15.381] (II) Loading extension X-Resource
[    15.381] (II) LoadModule: "dbe"
[    15.382] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.383] (II) Module dbe: vendor="X.Org Foundation"
[    15.383]     compiled for 1.10.4, module version = 1.0.0
[    15.383]     Module class: X.Org Server Extension
[    15.383]     ABI class: X.Org Server Extension, version 5.0
[    15.383] (II) Loading extension DOUBLE-BUFFER
[    15.383] (II) LoadModule: "glx"
[    15.384] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    15.390] (II) Module glx: vendor="X.Org Foundation"
[    15.390]     compiled for 1.10.4, module version = 1.0.0
[    15.390]     ABI class: X.Org Server Extension, version 5.0
[    15.391] (==) AIGLX enabled
[    15.391] (II) Loading extension GLX
[    15.391] (II) LoadModule: "record"
[    15.394] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.395] (II) Module record: vendor="X.Org Foundation"
[    15.395]     compiled for 1.10.4, module version = 1.13.0
[    15.395]     Module class: X.Org Server Extension
[    15.395]     ABI class: X.Org Server Extension, version 5.0
[    15.395] (II) Loading extension RECORD
[    15.395] (II) LoadModule: "dri"
[    15.396] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.412] (II) Module dri: vendor="X.Org Foundation"
[    15.412]     compiled for 1.10.4, module version = 1.0.0
[    15.412]     ABI class: X.Org Server Extension, version 5.0
[    15.412] (II) Loading extension XFree86-DRI
[    15.412] (II) LoadModule: "dri2"
[    15.412] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.413] (II) Module dri2: vendor="X.Org Foundation"
[    15.413]     compiled for 1.10.4, module version = 1.2.0
[    15.413]     ABI class: X.Org Server Extension, version 5.0
[    15.413] (II) Loading extension DRI2
[    15.413] (==) Matched intel as autoconfigured driver 0
[    15.413] (==) Matched vesa as autoconfigured driver 1
[    15.413] (==) Matched fbdev as autoconfigured driver 2
[    15.413] (==) Assigned the driver to the xf86ConfigLayout
[    15.413] (II) LoadModule: "intel"
[    15.414] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    15.432] (II) Module intel: vendor="X.Org Foundation"
[    15.432]     compiled for 1.10.4, module version = 2.15.901
[    15.432]     Module class: X.Org Video Driver
[    15.432]     ABI class: X.Org Video Driver, version 10.0
[    15.432] (II) LoadModule: "vesa"
[    15.432] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.443] (II) Module vesa: vendor="X.Org Foundation"
[    15.443]     compiled for 1.10.2, module version = 2.3.0
[    15.443]     Module class: X.Org Video Driver
[    15.443]     ABI class: X.Org Video Driver, version 10.0
[    15.443] (II) LoadModule: "fbdev"
[    15.446] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.447] (II) Module fbdev: vendor="X.Org Foundation"
[    15.447]     compiled for 1.10.0, module version = 0.4.2
[    15.447]     ABI class: X.Org Video Driver, version 10.0
[    15.447] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    15.449] (II) VESA: driver for VESA chipsets: vesa
[    15.449] (II) FBDEV: driver for framebuffer: fbdev
[    15.449] (++) using VT number 7

[    15.451] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    15.451] (WW) Falling back to old probe method for vesa
[    15.451] (WW) Falling back to old probe method for fbdev
[    15.451] (II) Loading sub module "fbdevhw"
[    15.451] (II) LoadModule: "fbdevhw"
[    15.452] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.463] (II) Module fbdevhw: vendor="X.Org Foundation"
[    15.463]     compiled for 1.10.4, module version = 0.0.2
[    15.463]     ABI class: X.Org Video Driver, version 10.0
[    15.463] drmOpenDevice: node name is /dev/dri/card0
[    15.463] drmOpenDevice: open result is 12, (OK)
[    15.463] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    15.463] drmOpenDevice: node name is /dev/dri/card0
[    15.463] drmOpenDevice: open result is 12, (OK)
[    15.463] drmOpenByBusid: drmOpenMinor returns 12
[    15.463] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    15.463] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    15.463] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    15.463] (==) intel(0): RGB weight 888
[    15.463] (==) intel(0): Default visual is TrueColor
[    15.463] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Desktop (GT1)
[    15.463] (--) intel(0): Chipset: "Sandybridge Desktop (GT1)"
[    15.463] (**) intel(0): Relaxed fencing enabled
[    15.463] (**) intel(0): Wait on SwapBuffers? enabled
[    15.463] (**) intel(0): Triple buffering? enabled
[    15.463] (**) intel(0): Framebuffer tiled
[    15.463] (**) intel(0): Pixmaps tiled
[    15.463] (**) intel(0): 3D buffers tiled
[    15.463] (**) intel(0): SwapBuffers wait enabled
[    15.463] (==) intel(0): video overlay key set to 0x101fe
[    15.463] (II) intel(0): Output VGA1 has no monitor section
[    15.499] (II) intel(0): Output HDMI1 has no monitor section
[    15.548] (II) intel(0): Output DP1 has no monitor section
[    15.573] (II) intel(0): Output HDMI2 has no monitor section
[    15.819] (II) intel(0): Output HDMI3 has no monitor section
[    15.864] (II) intel(0): Output DP2 has no monitor section
[    15.912] (II) intel(0): Output DP3 has no monitor section
[    15.912] (II) intel(0): EDID for output VGA1
[    15.944] (II) intel(0): EDID for output HDMI1
[    15.992] (II) intel(0): EDID for output DP1
[    16.023] (II) intel(0): EDID for output HDMI2
[    16.269] (II) intel(0): EDID for output HDMI3
[    16.269] (II) intel(0): Manufacturer: MJI  Model: 18  Serial#: 0
[    16.269] (II) intel(0): Year: 2009  Week: 0
[    16.269] (II) intel(0): EDID Version: 1.3
[    16.269] (II) intel(0): Digital Display Input
[    16.269] (II) intel(0): Indeterminate output size
[    16.269] (II) intel(0): Gamma: 2.20
[    16.269] (II) intel(0): No DPMS capabilities specified
[    16.269] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    16.269] (II) intel(0): First detailed timing is preferred mode
[    16.269] (II) intel(0): redX: 0.649 redY: 0.342   greenX: 0.326 greenY: 0.649
[    16.269] (II) intel(0): blueX: 0.139 blueY: 0.050   whiteX: 0.284 whiteY: 0.334
[    16.269] (II) intel(0): Manufacturer's mask: 0
[    16.269] (II) intel(0): Supported detailed timing:
[    16.269] (II) intel(0): clock: 74.2 MHz   Image Size:  708 x 398 mm
[    16.269] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    16.269] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    16.269] (II) intel(0): Supported detailed timing:
[    16.269] (II) intel(0): clock: 74.2 MHz   Image Size:  708 x 398 mm
[    16.269] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    16.269] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    16.269] (II) intel(0): Monitor name: NR1501
[    16.269] (II) intel(0): Ranges: V min: 24 V max: 61 Hz, H min: 28 H max: 68 kHz, PixClock max 155 MHz
[    16.269] (II) intel(0): Supported detailed timing:
[    16.269] (II) intel(0): clock: 74.2 MHz   Image Size:  708 x 398 mm
[    16.269] (II) intel(0): h_active: 1920  h_sync: 2558  h_sync_end 2602 h_blank_end 2750 h_border: 0
[    16.269] (II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    16.269] (II) intel(0): Supported detailed timing:
[    16.269] (II) intel(0): clock: 27.0 MHz   Image Size:  531 x 398 mm
[    16.269] (II) intel(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    16.269] (II) intel(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    16.269] (II) intel(0): Supported detailed timing:
[    16.269] (II) intel(0): clock: 27.0 MHz   Image Size:  531 x 398 mm
[    16.269] (II) intel(0): h_active: 720  h_sync: 732  h_sync_end 796 h_blank_end 864 h_border: 0
[    16.269] (II) intel(0): v_active: 576  v_sync: 581  v_sync_end 586 v_blanking: 625 v_border: 0
[    16.269] (II) intel(0): Supported detailed timing:
[    16.269] (II) intel(0): clock: 74.2 MHz   Image Size:  708 x 398 mm
[    16.269] (II) intel(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    16.269] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    16.269] (II) intel(0): Number of EDID sections to follow: 1
[    16.269] (II) intel(0): EDID (in hex):
[    16.269] (II) intel(0):     00ffffffffffff003549180000000000
[    16.269] (II) intel(0):     00130103800000780a69bea65753a623
[    16.269] (II) intel(0):     0c485500000001010101010101010101
[    16.269] (II) intel(0):     010101010101011d8018711c1620582c
[    16.269] (II) intel(0):     2500c48e2100009e011d80d0721c1620
[    16.269] (II) intel(0):     102c2580c48e2100009e000000fc004e
[    16.269] (II) intel(0):     52313530310a202020202020000000fd
[    16.269] (II) intel(0):     00183d1c440f000a202020202020014e
[    16.269] (II) intel(0):     020335714a0514041320021101101f35
[    16.269] (II) intel(0):     097f070f7f071507503e1ec05706005f
[    16.269] (II) intel(0):     7e01677e00e305030167030c002400b8
[    16.269] (II) intel(0):     26834f0000011d803e73382d407e2c45
[    16.269] (II) intel(0):     80c48e2100001e8c0ad08a20e02d1010
[    16.269] (II) intel(0):     3e9600138e210000188c0ad090204031
[    16.269] (II) intel(0):     200c405500138e21000018011d007251
[    16.269] (II) intel(0):     d01e206e285500c48e2100001e0000d5
[    16.269] (II) intel(0): Printing probed modes for output HDMI3
[    16.269] (II) intel(0): Modeline "1920x1080"x24.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    16.324] (II) intel(0): EDID for output DP2
[    16.372] (II) intel(0): EDID for output DP3
[    16.372] (II) intel(0): Output VGA1 disconnected
[    16.372] (II) intel(0): Output HDMI1 disconnected
[    16.372] (II) intel(0): Output DP1 disconnected
[    16.372] (II) intel(0): Output HDMI2 disconnected
[    16.372] (II) intel(0): Output HDMI3 connected
[    16.372] (II) intel(0): Output DP2 disconnected
[    16.372] (II) intel(0): Output DP3 disconnected
[    16.372] (II) intel(0): Using exact sizes for initial modes
[    16.372] (II) intel(0): Output HDMI3 using initial mode 1920x1080
[    16.372] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    16.372] (II) intel(0): Kernel page flipping support detected, enabling
[    16.372] (==) intel(0): DPI set to (96, 96)
[    16.372] (II) Loading sub module "fb"
[    16.372] (II) LoadModule: "fb"
[    16.372] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.374] (II) Module fb: vendor="X.Org Foundation"
[    16.374]     compiled for 1.10.4, module version = 1.0.0
[    16.374]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.374] (II) Loading sub module "dri2"
[    16.374] (II) LoadModule: "dri2"
[    16.374] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.374] (II) Module dri2: vendor="X.Org Foundation"
[    16.374]     compiled for 1.10.4, module version = 1.2.0
[    16.374]     ABI class: X.Org Server Extension, version 5.0
[    16.374] (II) UnloadModule: "vesa"
[    16.374] (II) Unloading vesa
[    16.374] (II) UnloadModule: "fbdev"
[    16.374] (II) Unloading fbdev
[    16.375] (II) UnloadModule: "fbdevhw"
[    16.375] (II) Unloading fbdevhw
[    16.375] (==) Depth 24 pixmap format is 32 bpp
[    16.375] (II) intel(0): [DRI2] Setup complete
[    16.375] (II) intel(0): [DRI2]   DRI driver: i965
[    16.375] (II) intel(0): Allocated new frame buffer 1920x1080 stride 7680, tiled
[    16.381] (II) UXA(0): Driver registered support for the following operations:
[    16.381] (II)         solid
[    16.381] (II)         copy
[    16.381] (II)         composite (RENDER acceleration)
[    16.381] (II)         put_image
[    16.381] (II)         get_image
[    16.381] (==) intel(0): Backing store disabled
[    16.381] (==) intel(0): Silken mouse enabled
[    16.381] (II) intel(0): Initializing HW Cursor
[    16.448] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    16.448] (==) intel(0): DPMS enabled
[    16.448] (==) intel(0): Intel XvMC decoder enabled
[    16.448] (II) intel(0): Set up textured video
[    16.448] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    16.448] (II) intel(0): direct rendering: DRI2 Enabled
[    16.448] (==) intel(0): hotplug detection: "enabled"
[    16.448] (--) RandR disabled
[    16.448] (II) Initializing built-in extension Generic Event Extension
[    16.448] (II) Initializing built-in extension SHAPE
[    16.448] (II) Initializing built-in extension MIT-SHM
[    16.448] (II) Initializing built-in extension XInputExtension
[    16.448] (II) Initializing built-in extension XTEST
[    16.448] (II) Initializing built-in extension BIG-REQUESTS
[    16.448] (II) Initializing built-in extension SYNC
[    16.448] (II) Initializing built-in extension XKEYBOARD
[    16.448] (II) Initializing built-in extension XC-MISC
[    16.448] (II) Initializing built-in extension SECURITY
[    16.448] (II) Initializing built-in extension XINERAMA
[    16.448] (II) Initializing built-in extension XFIXES
[    16.448] (II) Initializing built-in extension RENDER
[    16.448] (II) Initializing built-in extension RANDR
[    16.448] (II) Initializing built-in extension COMPOSITE
[    16.448] (II) Initializing built-in extension DAMAGE
[    16.448] (II) Initializing built-in extension GESTURE
[    16.456] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
[    16.497] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    16.497] (II) AIGLX: enabled GLX_INTEL_swap_event
[    16.497] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    16.497] (II) AIGLX: enabled GLX_SGI_make_current_read
[    16.497] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    16.497] (II) AIGLX: Loaded and initialized i965
[    16.497] (II) GLX: Initialized DRI2 GL provider for screen 0
[    16.497] (II) intel(0): Setting screen physical size to 508 x 285
[    16.517] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.599] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    16.599] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.599] (II) LoadModule: "evdev"
[    16.599] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.612] (II) Module evdev: vendor="X.Org Foundation"
[    16.612]     compiled for 1.10.2, module version = 2.6.0
[    16.612]     Module class: X.Org XInput Driver
[    16.612]     ABI class: X.Org XInput driver, version 12.3
[    16.612] (II) Using input driver 'evdev' for 'Power Button'
[    16.612] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.612] (**) Power Button: always reports core events
[    16.612] (**) Power Button: Device: "/dev/input/event1"
[    16.612] (--) Power Button: Found keys
[    16.612] (II) Power Button: Configuring as keyboard
[    16.612] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    16.612] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.612] (**) Option "xkb_rules" "evdev"
[    16.612] (**) Option "xkb_model" "pc105"
[    16.612] (**) Option "xkb_layout" "us"
[    16.616] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    16.616] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.616] (II) Using input driver 'evdev' for 'Power Button'
[    16.616] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.616] (**) Power Button: always reports core events
[    16.616] (**) Power Button: Device: "/dev/input/event0"
[    16.616] (--) Power Button: Found keys
[    16.616] (II) Power Button: Configuring as keyboard
[    16.616] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    16.616] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.616] (**) Option "xkb_rules" "evdev"
[    16.616] (**) Option "xkb_model" "pc105"
[    16.616] (**) Option "xkb_layout" "us"
[    16.619] (II) config/udev: Adding input device Logitech Trackball (/dev/input/event2)
[    16.619] (**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
[    16.619] (II) Using input driver 'evdev' for 'Logitech Trackball'
[    16.619] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.619] (**) Logitech Trackball: always reports core events
[    16.619] (**) Logitech Trackball: Device: "/dev/input/event2"
[    16.620] (--) Logitech Trackball: Found 3 mouse buttons
[    16.620] (--) Logitech Trackball: Found scroll wheel(s)
[    16.620] (--) Logitech Trackball: Found relative axes
[    16.620] (--) Logitech Trackball: Found x and y relative axes
[    16.620] (II) Logitech Trackball: Configuring as mouse
[    16.620] (II) Logitech Trackball: Adding scrollwheel support
[    16.620] (**) Logitech Trackball: YAxisMapping: buttons 4 and 5
[    16.620] (**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.620] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input2/event2"
[    16.620] (II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
[    16.620] (II) Logitech Trackball: initialized for relative axes.
[    16.620] (**) Logitech Trackball: (accel) keeping acceleration scheme 1
[    16.620] (**) Logitech Trackball: (accel) acceleration profile 0
[    16.620] (**) Logitech Trackball: (accel) acceleration factor: 2.000
[    16.620] (**) Logitech Trackball: (accel) acceleration threshold: 4
[    16.620] (II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse0)
[    16.620] (II) No input driver/identifier specified (ignoring)
[    16.623] (II) config/udev: Adding input device MOSART Semi. Wireless Keyboard & Mouse (/dev/input/event3)
[    16.623] (**) MOSART Semi. Wireless Keyboard & Mouse: Applying InputClass "evdev keyboard catchall"
[    16.623] (II) Using input driver 'evdev' for 'MOSART Semi. Wireless Keyboard & Mouse'
[    16.623] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.623] (**) MOSART Semi. Wireless Keyboard & Mouse: always reports core events
[    16.623] (**) MOSART Semi. Wireless Keyboard & Mouse: Device: "/dev/input/event3"
[    16.623] (--) MOSART Semi. Wireless Keyboard & Mouse: Found keys
[    16.623] (II) MOSART Semi. Wireless Keyboard & Mouse: Configuring as keyboard
[    16.623] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input3/event3"
[    16.623] (II) XINPUT: Adding extended input device "MOSART Semi. Wireless Keyboard & Mouse" (type: KEYBOARD)
[    16.623] (**) Option "xkb_rules" "evdev"
[    16.623] (**) Option "xkb_model" "pc105"
[    16.623] (**) Option "xkb_layout" "us"
[    16.625] (II) config/udev: Adding input device MOSART Semi. Wireless Keyboard & Mouse (/dev/input/event4)
[    16.625] (**) MOSART Semi. Wireless Keyboard & Mouse: Applying InputClass "evdev pointer catchall"
[    16.625] (**) MOSART Semi. Wireless Keyboard & Mouse: Applying InputClass "evdev keyboard catchall"
[    16.625] (II) Using input driver 'evdev' for 'MOSART Semi. Wireless Keyboard & Mouse'
[    16.625] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.625] (**) MOSART Semi. Wireless Keyboard & Mouse: always reports core events
[    16.625] (**) MOSART Semi. Wireless Keyboard & Mouse: Device: "/dev/input/event4"
[    16.625] (--) MOSART Semi. Wireless Keyboard & Mouse: Found 3 mouse buttons
[    16.625] (--) MOSART Semi. Wireless Keyboard & Mouse: Found scroll wheel(s)
[    16.625] (--) MOSART Semi. Wireless Keyboard & Mouse: Found relative axes
[    16.625] (--) MOSART Semi. Wireless Keyboard & Mouse: Found x and y relative axes
[    16.625] (--) MOSART Semi. Wireless Keyboard & Mouse: Found absolute axes
[    16.625] (II) evdev-grail: failed to open grail, no gesture support
[    16.625] (--) MOSART Semi. Wireless Keyboard & Mouse: Found keys
[    16.625] (II) MOSART Semi. Wireless Keyboard & Mouse: Configuring as mouse
[    16.625] (II) MOSART Semi. Wireless Keyboard & Mouse: Configuring as keyboard
[    16.625] (II) MOSART Semi. Wireless Keyboard & Mouse: Adding scrollwheel support
[    16.625] (**) MOSART Semi. Wireless Keyboard & Mouse: YAxisMapping: buttons 4 and 5
[    16.625] (**) MOSART Semi. Wireless Keyboard & Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.625] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.1/input/input4/event4"
[    16.625] (II) XINPUT: Adding extended input device "MOSART Semi. Wireless Keyboard & Mouse" (type: KEYBOARD)
[    16.625] (**) Option "xkb_rules" "evdev"
[    16.625] (**) Option "xkb_model" "pc105"
[    16.625] (**) Option "xkb_layout" "us"
[    16.625] (II) MOSART Semi. Wireless Keyboard & Mouse: initialized for relative axes.
[    16.625] (WW) MOSART Semi. Wireless Keyboard & Mouse: ignoring absolute axes.
[    16.626] (**) MOSART Semi. Wireless Keyboard & Mouse: (accel) keeping acceleration scheme 1
[    16.626] (**) MOSART Semi. Wireless Keyboard & Mouse: (accel) acceleration profile 0
[    16.626] (**) MOSART Semi. Wireless Keyboard & Mouse: (accel) acceleration factor: 2.000
[    16.626] (**) MOSART Semi. Wireless Keyboard & Mouse: (accel) acceleration threshold: 4
[    16.626] (II) config/udev: Adding input device MOSART Semi. Wireless Keyboard & Mouse (/dev/input/mouse1)
[    16.626] (II) No input driver/identifier specified (ignoring)
[    16.628] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event7)
[    16.628] (II) No input driver/identifier specified (ignoring)
[    16.628] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event8)
[    16.628] (II) No input driver/identifier specified (ignoring)
[    16.630] (II) config/udev: Adding input device HOLTEK (/dev/input/event5)
[    16.630] (**) HOLTEK: Applying InputClass "evdev keyboard catchall"
[    16.630] (II) Using input driver 'evdev' for 'HOLTEK'
[    16.630] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.630] (**) HOLTEK: always reports core events
[    16.630] (**) HOLTEK: Device: "/dev/input/event5"
[    16.630] (--) HOLTEK: Found keys
[    16.630] (II) HOLTEK: Configuring as keyboard
[    16.631] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input5/event5"
[    16.631] (II) XINPUT: Adding extended input device "HOLTEK" (type: KEYBOARD)
[    16.631] (**) Option "xkb_rules" "evdev"
[    16.631] (**) Option "xkb_model" "pc105"
[    16.631] (**) Option "xkb_layout" "us"
[    16.631] (II) config/udev: Adding input device HOLTEK (/dev/input/event6)
[    16.631] (**) HOLTEK: Applying InputClass "evdev pointer catchall"
[    16.631] (**) HOLTEK: Applying InputClass "evdev keyboard catchall"
[    16.631] (II) Using input driver 'evdev' for 'HOLTEK'
[    16.631] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.631] (**) HOLTEK: always reports core events
[    16.631] (**) HOLTEK: Device: "/dev/input/event6"
[    16.631] (--) HOLTEK: Found 9 mouse buttons
[    16.631] (--) HOLTEK: Found scroll wheel(s)
[    16.631] (--) HOLTEK: Found relative axes
[    16.631] (--) HOLTEK: Found x and y relative axes
[    16.631] (--) HOLTEK: Found absolute axes
[    16.632] (II) evdev-grail: failed to open grail, no gesture support
[    16.632] (--) HOLTEK: Found keys
[    16.632] (II) HOLTEK: Configuring as mouse
[    16.632] (II) HOLTEK: Configuring as keyboard
[    16.632] (II) HOLTEK: Adding scrollwheel support
[    16.632] (**) HOLTEK: YAxisMapping: buttons 4 and 5
[    16.632] (**) HOLTEK: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.632] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1/input/input6/event6"
[    16.632] (II) XINPUT: Adding extended input device "HOLTEK" (type: KEYBOARD)
[    16.632] (**) Option "xkb_rules" "evdev"
[    16.640] (**) Option "xkb_model" "pc105"
[    16.640] (**) Option "xkb_layout" "us"
[    16.640] (II) HOLTEK: initialized for relative axes.
[    16.640] (WW) HOLTEK: ignoring absolute axes.
[    16.640] (**) HOLTEK: (accel) keeping acceleration scheme 1
[    16.640] (**) HOLTEK: (accel) acceleration profile 0
[    16.640] (**) HOLTEK: (accel) acceleration factor: 2.000
[    16.640] (**) HOLTEK: (accel) acceleration threshold: 4
[    16.640] (II) config/udev: Adding input device HOLTEK (/dev/input/mouse2)
[    16.640] (II) No input driver/identifier specified (ignoring)
[    17.335] (II) intel(0): EDID vendor "MJI", prod id 24
[    17.335] (II) intel(0): Using EDID range info for horizontal sync
[    17.335] (II) intel(0): Using EDID range info for vertical refresh
[    17.335] (II) intel(0): Printing DDC gathered Modelines:
[    17.335] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    17.335] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    17.335] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    17.335] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    17.335] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    17.335] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    17.335] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    17.335] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    17.335] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    17.767] (II) intel(0): EDID vendor "MJI", prod id 24
[    17.767] (II) intel(0): Using hsync ranges from config file
[    17.767] (II) intel(0): Using vrefresh ranges from config file
[    17.767] (II) intel(0): Printing DDC gathered Modelines:
[    17.767] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    17.767] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    17.767] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    17.767] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    17.767] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    17.767] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    17.767] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    17.767] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    17.767] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    18.528] (II) intel(0): EDID vendor "MJI", prod id 24
[    18.528] (II) intel(0): Using hsync ranges from config file
[    18.528] (II) intel(0): Using vrefresh ranges from config file
[    18.528] (II) intel(0): Printing DDC gathered Modelines:
[    18.528] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    18.528] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    18.528] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    18.528] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    18.528] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    18.528] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    18.528] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    18.528] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    18.528] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    27.587] (II) intel(0): EDID vendor "MJI", prod id 24
[    27.587] (II) intel(0): Using hsync ranges from config file
[    27.587] (II) intel(0): Using vrefresh ranges from config file
[    27.587] (II) intel(0): Printing DDC gathered Modelines:
[    27.587] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    27.587] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    27.587] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    27.587] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    27.587] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    27.587] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    27.587] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    27.587] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    27.587] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    29.603] (II) intel(0): EDID vendor "MJI", prod id 24
[    29.603] (II) intel(0): Using hsync ranges from config file
[    29.603] (II) intel(0): Using vrefresh ranges from config file
[    29.603] (II) intel(0): Printing DDC gathered Modelines:
[    29.603] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    29.603] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    29.603] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    29.603] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    29.603] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    29.603] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    29.603] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    29.603] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    29.603] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)

```Anyone had a similiar experience?

---

### Post by kenneyjs on 2012-01-16
Still no luck, and I think I have tried various boot settings mentioned in other posts, and from the manuals, such as:

acpi=off 
GRUB_GFXPAYLOAD_LINUX=text 
i915.modeset=1 i915.semaphores=1 
video=HDMI3:1920x1080@60 
acpi_osi=linux pci=noacpi

I also tried various xorg.conf modifications, from the simple to much more complex, and still nothing comes out of the video after about 1st second of boot (when it finds the intel side)

I grabbed an ATI card that wouldn't fit in this htpc (I am planning to use a Streacom FC5 OD), and the ATI card worked fine with the projector.  Arg.

I think the screen disappears at the point where it loads the console (from dmesg):

```

[    1.369405] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.369450] i915 0000:00:02.0: setting latency timer to 64
[    1.376019] firewire_ohci: Added fw-ohci device 0000:04:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    1.426852] i915 0000:00:02.0: irq 49 for MSI/MSI-X
[    1.426858] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.426898] [drm] Driver supports precise vblank timestamp query.
[    1.426963] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
    1.862975] fbcon: inteldrmfb (fb0) is primary device
[    2.038053] Console: switching to colour frame buffer device 240x67
[    2.042403] fb0: inteldrmfb frame buffer device
[    2.042421] drm: registered panic notifier
[    2.042447] No ACPI video bus found
[    2.042503] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[[   16.253691] hda_codec: ALC892: BIOS auto-probing.
[   16.283018] HDMI hot plug event: Pin=7 Presence_Detect=1 ELD_Valid=1
[   16.283199] HDMI status: Pin=6 Presence_Detect=0 ELD_Valid=0
[   16.283275] HDMI status: Pin=7 Presence_Detect=1 ELD_Valid=1
[   16.286774] HDMI: detected monitor  at connection type HDMI
[   16.286776] HDMI: available speakers: FL/FR
[   16.286780] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16
[   16.286783] HDMI hot plug event: Pin=7 Presence_Detect=1 ELD_Valid=1
[   16.286835] HDMI status: Pin=7 Presence_Detect=1 ELD_Valid=1
[   16.290334] HDMI: detected monitor  at connection type HDMI
[   16.290337] HDMI: available speakers: FL/FR
[   16.290341] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16
[   16.290437] HDMI status: Pin=7 Presence_Detect=1 ELD_Valid=1
[   16.293935] HDMI: detected monitor  at connection type HDMI
[   16.293938] HDMI: available speakers: FL/FR
[   16.293941] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16
[   16.294253] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   16.294383] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8

```

Any help would be greatly appreciated.

---

### Post by BicyclerBoy on 2012-01-17
I'm not sure that 1920x540p is crazy..
It is just another way of denoting 1080i (interlaced)

Your projector's EDIDs don't look right to me..
The value 74.25MHz dot clock is repeated in lots of the modelines.
And it is listed for a 1080p mode which is not possible.

Your video card is trying to use 1080p24 & maybe this is not supported by projector.

Can you try this in X server GUI terminal:
```

$ xrandr --newmode "1920x1080i_60.0"   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync
$ xrandr --addmode HDMI3 "1920x1080i_60.0"
$ xrandr --output HDMI3 --mode "1920x1080i_60.0"

```

---

### Post by kenneyjs on 2012-01-17
BicylerBoy, thanks for the help, I just tried those lines without luck, same result.  

```
ubuntu@ubuntu:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 708mm x 398mm
   1920x1080      24.0* 
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
ubuntu@ubuntu:~$ xrandr --newmode "1920x1080i_60.0"   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync
ubuntu@ubuntu:~$ xrandr --addmode HDMI3 "1920x1080i_60.0"
ubuntu@ubuntu:~$ xrandr --output HDMI3 --mode "1920x1080i_60.0"
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 708mm x 398mm
   1920x1080      24.0  
   1920x1080i_60.0   25.0* 
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)

```

Thanks, any other ideas?

---

### Post by BicyclerBoy on 2012-01-18
Your previous reported EDID looks to be the AVR/HT-amp EDID & not the display/projector.
You have not posted your display EDID info.

The AVR should have EDID management options:
- cached
- modify/add
- pass-thru

The AVR has to change the EDID data to add ELD (audio) capabilities.
The AVR may have to add/change EDID to do OSD display for AVR setup.

Can you ?
- enable ACPI (required)
- direct connect HDMI
- add/set video mode 1920x1080i60.0
- post /var/log/Xorg.0.log
- determine the display capabilities from the internet (720p/480p ?)

---

### Post by kenneyjs on 2012-01-18
Good Afternoon, and thanks for the help,

The projector is a Panasonic PT-AE4000U, which is a native 1920x1080 projector capable of
480p, 576p, 1080/60i, 1080/50i, 1080/60p, 1080/50p, 1080/25p, 720/60p, 720/50p.

ACPI is enabled, HDMI is connected directly.

I am running from a modified lived that is fully updated and with x11vnc set to autostart.

Something really weird (and probably very bad) happened, as soon as I ran "xrandr --output HDMI3 --mode "1920x1080i_60.0"" my entire house network just stopped working (I have a wired house with gigabit switches, etc.) and nothing was reachable.  I was being optimistic and just reset the routers and switches with no luck, it wasn't until I unplugged the htpc that things went back to normal.  Since I had lost connectivity I just assumed the pc had crashed, but it was having some effect on the network.

oh well...

---

### Post by BicyclerBoy on 2012-01-18
I was under the impression that get-edid tools did not work with 64bit systems. It has never worked for me..

For a HTPC setup I would be using xorg-edgers ppa & sarvatt ppa.
A recent kernel seems to be needed for SNA graphics. Maybe even later than your 3.0.14..

If the projector supports 1080p then you can make your modelines with 
$ cvt -r 1920 1080 60
$ cvt 1920 1080 50

You probably only need the first one..
Intel 24p (real 23.97..) is still broken in h/w for intel HD2000.

The interlaced 1080i60 mode should have worked tho..

---

### Post by kenneyjs on 2012-01-18
Again thanks for the assist.  I know the xorg-edgers folks are updating their base this week.  I'll build a precise 12.04 livecd (for a newer kernel) with the updated xorg-edgers and sarvatt ppa (never tried the sarvatt one) as soon as they finish.  I tried an xorg-edgers with 11.10 last week with an xorg.conf using 1080p/60 mode lines with no luck (at least it didn't crash my network though...)

I give an update as soon as the xorg-edgers update is out.

Thanks!

---

### Post by BicyclerBoy on 2012-01-18
Seems to be a very trying time (trying to get it to work) for intel HD users just now.
Intel iCPU/SNA should make ultimately a very tidy solution..

Maybe x11vnc caused the network crash/lockup?

---

### Post by kenneyjs on 2012-01-18
I hadn't thought about a possible conflict with x11vnc.  Will make testing a bit painful, might have to try some ssh fun and see if that prevents the system from crashing when connected directly to the projector just to test...

This would make such a perfect HTPC, I really don't want to add an external video card.  (I have tried a fan less nvidia card and it works perfectly in this setup with the receiver-->projector, but I am trying to keep power/heat as low as possible as there won't be an fans.  The ATI card worked as well, but hdmi audio is a pain with ATI and it likes to overscan the video with projectors.

What I am doing is building a livecd with everything perfectly configured for the htpc with xbmc and acceleration, and booting from the livecd via an iso from the ssd.  makes for crazy quick application run times as everything is in memory the entire time.

If the new xorg-edgers has the same effect, I'll have to throw up my hands and use the nvidia card which will nearly double the power used by the system... The integrated video worked perfectly in windows 7, but I don't have the same control of the setup, and I am working to get the iso file quite small vice the 30GB size for windows.

Thanks!

---


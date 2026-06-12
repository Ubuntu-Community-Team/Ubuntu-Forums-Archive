---
title: "HDMI showing only the upper half of the screen (twice)"
date: 2012-01-05
forum: Multimedia Software
---

### Post by alfonso78 on 2012-01-05
Hi,

**UPDATE: this problem needed some patches. See my [last post]("http://ubuntuforums.org/showpost.php?p=11646385&postcount=30").**

I just finished to upgrade my motherboard.

The BIOS screen over HDMI looks fine, but when I run both the Ubuntu 11.10 that I already had installed in my HD and also the installation from USB, both show the upper half on both halves of the screen. :confused: :confused:

In other words I can't see the bottom half of the screen!

I have a Zotac H67 with an Intel i3 2130.

I have the i915 driver:
```

$ lsmod | grep i915
i915                  505143  2
drm_kms_helper         32889  1 i915
drm                   196322  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915

```

since I can browse the BIOS without problem, I imagine the problem is in the Ubuntu driver. Any idea?

The same TV was working without any problem with my previous motherboard.

UPDATE:

**when I'm the BIOS and I can see the full screen, the TV says "HD 1080" while in ubuntu the TV says "XGA"**

I have a Philips 32pf9731d

Thank you,
alfonso

---

### Post by BicyclerBoy on 2012-01-05
You could post the contents of file:
/var/log/Xorg.0.log

The sandybridge SNA driver in ubuntu is out-of-date & conservative.
If you want some risk try adding xorg-edgers ppa

You need to add
[https://launchpad.net/~sarvatt/+archive/intel-sna](https://launchpad.net/~sarvatt/+archive/intel-sna)
as well to get SNA acceleration..

---

### Post by alfonso78 on 2012-01-06
> **BicyclerBoy said:**
> You could post the contents of file:
/var/log/Xorg.0.log

The sandybridge SNA driver in ubuntu is out-of-date & conservative.
If you want some risk try adding xorg-edgers ppa

You need to add
[https://launchpad.net/~sarvatt/+archive/intel-sna](https://launchpad.net/~sarvatt/+archive/intel-sna)
as well to get SNA acceleration..

Thank you BicyclerBoy!

Here is my /var/log/Xorg.0.log

I would first try to simply fix the current situation before looking into xorg-edgers ppa.

Any idea?

```

$ cat Xorg.0.log
[     6.496]
X.Org X Server 1.10.4
Release Date: 2011-08-19
[     6.496] X Protocol Version 11, Revision 0
[     6.496] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[     6.496] Current Operating System: Linux NAS 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686
[     6.496] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic-pae root=UUID=2f050176-99ce-49de-9826-a01fe25ecec9 ro bootdegraded=true quiet splash vt.handoff=7
[     6.496] Build Date: 19 October 2011  05:09:41AM
[     6.496] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support)
[     6.496] Current version of pixman: 0.22.2
[     6.496]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[     6.496] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     6.496] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan  6 16:38:06 2012
[     6.501] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     6.503] (==) No Layout section.  Using the first Screen section.
[     6.503] (==) No screen section available. Using defaults.
[     6.503] (**) |-->Screen "Default Screen Section" (0)
[     6.503] (**) |   |-->Monitor "<default monitor>"
[     6.504] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[     6.504] (==) Automatically adding devices
[     6.504] (==) Automatically enabling devices
[     6.508] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     6.508]    Entry deleted from font path.
[     6.508] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     6.508]    Entry deleted from font path.
[     6.508] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     6.508]    Entry deleted from font path.
[     6.508] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     6.508]    Entry deleted from font path.
[     6.508] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     6.508]    Entry deleted from font path.
[     6.509] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[     6.509] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     6.509] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[     6.509] (II) Loader magic: 0x823ada0
[     6.509] (II) Module ABI versions:
[     6.509]    X.Org ANSI C Emulation: 0.4
[     6.509]    X.Org Video Driver: 10.0
[     6.509]    X.Org XInput driver : 12.3
[     6.509]    X.Org Server Extension : 5.0
[     6.509] (--) PCI:*(0:0:2:0) 8086:0102:19da:a166 rev 9, Mem @ 0xfe000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
[     6.510] (II) Open ACPI successful (/var/run/acpid.socket)
[     6.510] (II) LoadModule: "extmod"
[     6.516] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     6.517] (II) Module extmod: vendor="X.Org Foundation"
[     6.517]    compiled for 1.10.4, module version = 1.0.0
[     6.517]    Module class: X.Org Server Extension
[     6.517]    ABI class: X.Org Server Extension, version 5.0
[     6.517] (II) Loading extension MIT-SCREEN-SAVER
[     6.517] (II) Loading extension XFree86-VidModeExtension
[     6.517] (II) Loading extension XFree86-DGA
[     6.517] (II) Loading extension DPMS
[     6.517] (II) Loading extension XVideo
[     6.517] (II) Loading extension XVideo-MotionCompensation
[     6.517] (II) Loading extension X-Resource
[     6.517] (II) LoadModule: "dbe"
[     6.517] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     6.518] (II) Module dbe: vendor="X.Org Foundation"
[     6.518]    compiled for 1.10.4, module version = 1.0.0
[     6.518]    Module class: X.Org Server Extension
[     6.518]    ABI class: X.Org Server Extension, version 5.0
[     6.518] (II) Loading extension DOUBLE-BUFFER
[     6.518] (II) LoadModule: "glx"
[     6.518] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     6.521] (II) Module glx: vendor="X.Org Foundation"
[     6.521]    compiled for 1.10.4, module version = 1.0.0
[     6.521]    ABI class: X.Org Server Extension, version 5.0
[     6.522] (==) AIGLX enabled
[     6.522] (II) Loading extension GLX
[     6.522] (II) LoadModule: "record"
[     6.522] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     6.522] (II) Module record: vendor="X.Org Foundation"
[     6.522]    compiled for 1.10.4, module version = 1.13.0
[     6.522]    Module class: X.Org Server Extension
[     6.522]    ABI class: X.Org Server Extension, version 5.0
[     6.522] (II) Loading extension RECORD
[     6.522] (II) LoadModule: "dri"
[     6.522] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     6.524] (II) Module dri: vendor="X.Org Foundation"
[     6.524]    compiled for 1.10.4, module version = 1.0.0
[     6.524]    ABI class: X.Org Server Extension, version 5.0
[     6.524] (II) Loading extension XFree86-DRI
[     6.524] (II) LoadModule: "dri2"
[     6.524] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     6.525] (II) Module dri2: vendor="X.Org Foundation"
[     6.525]    compiled for 1.10.4, module version = 1.2.0
[     6.525]    ABI class: X.Org Server Extension, version 5.0
[     6.525] (II) Loading extension DRI2
[     6.525] (==) Matched intel as autoconfigured driver 0
[     6.525] (==) Matched vesa as autoconfigured driver 1
[     6.525] (==) Matched fbdev as autoconfigured driver 2
[     6.525] (==) Assigned the driver to the xf86ConfigLayout
[     6.525] (II) LoadModule: "intel"
[     6.527] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     6.531] (II) Module intel: vendor="X.Org Foundation"
[     6.531]    compiled for 1.10.2.902, module version = 2.15.901
[     6.531]    Module class: X.Org Video Driver
[     6.531]    ABI class: X.Org Video Driver, version 10.0
[     6.531] (II) LoadModule: "vesa"
[     6.531] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     6.532] (II) Module vesa: vendor="X.Org Foundation"
[     6.532]    compiled for 1.10.2, module version = 2.3.0
[     6.532]    Module class: X.Org Video Driver
[     6.532]    ABI class: X.Org Video Driver, version 10.0
[     6.532] (II) LoadModule: "fbdev"
[     6.532] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     6.532] (II) Module fbdev: vendor="X.Org Foundation"
[     6.532]    compiled for 1.10.0, module version = 0.4.2
[     6.532]    ABI class: X.Org Video Driver, version 10.0
[     6.532] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
        Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
        Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
        Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
        Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[     6.533] (II) VESA: driver for VESA chipsets: vesa
[     6.533] (II) FBDEV: driver for framebuffer: fbdev
[     6.533] (++) using VT number 7

[     6.534] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     6.534] (WW) Falling back to old probe method for vesa
[     6.534] (WW) Falling back to old probe method for fbdev
[     6.534] (II) Loading sub module "fbdevhw"
[     6.534] (II) LoadModule: "fbdevhw"
[     6.534] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     6.534] (II) Module fbdevhw: vendor="X.Org Foundation"
[     6.534]    compiled for 1.10.4, module version = 0.0.2
[     6.534]    ABI class: X.Org Video Driver, version 10.0
[     6.535] drmOpenDevice: node name is /dev/dri/card0
[     6.535] drmOpenDevice: open result is 12, (OK)
[     6.535] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[     6.535] drmOpenDevice: node name is /dev/dri/card0
[     6.535] drmOpenDevice: open result is 12, (OK)
[     6.535] drmOpenByBusid: drmOpenMinor returns 12
[     6.535] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[     6.535] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[     6.535] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     6.535] (==) intel(0): RGB weight 888
[     6.535] (==) intel(0): Default visual is TrueColor
[     6.535] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Desktop (GT1)
[     6.535] (--) intel(0): Chipset: "Sandybridge Desktop (GT1)"
[     6.535] (**) intel(0): Relaxed fencing enabled
[     6.535] (**) intel(0): Wait on SwapBuffers? enabled
[     6.535] (**) intel(0): Triple buffering? enabled
[     6.535] (**) intel(0): Framebuffer tiled
[     6.535] (**) intel(0): Pixmaps tiled
[     6.535] (**) intel(0): 3D buffers tiled
[     6.535] (**) intel(0): SwapBuffers wait enabled
[     6.535] (==) intel(0): video overlay key set to 0x101fe
[     6.535] (II) intel(0): Output VGA1 has no monitor section
[     6.559] (II) intel(0): Output HDMI1 has no monitor section
[     6.608] (II) intel(0): Output DP1 has no monitor section
[     6.861] (II) intel(0): Output HDMI2 has no monitor section
[     6.884] (II) intel(0): Output HDMI3 has no monitor section
[     6.936] (II) intel(0): Output DP2 has no monitor section
[     6.984] (II) intel(0): Output DP3 has no monitor section
[     6.984] (II) intel(0): EDID for output VGA1
[     7.006] (II) intel(0): EDID for output HDMI1
[     7.052] (II) intel(0): EDID for output DP1
[     7.293] (II) intel(0): EDID for output HDMI2
[     7.333] (II) intel(0): Manufacturer: PHL  Model: 1  Serial#: 16843009
[     7.333] (II) intel(0): Year: 2006  Week: 1
[     7.333] (II) intel(0): EDID Version: 1.3
[     7.333] (II) intel(0): Digital Display Input
[     7.333] (II) intel(0): Max Image Size [cm]: horiz.: 64  vert.: 36
[     7.333] (II) intel(0): Gamma: 2.20
[     7.333] (II) intel(0): No DPMS capabilities specified
[     7.333] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[     7.333] (II) intel(0): First detailed timing is preferred mode
[     7.333] (II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.290 greenY: 0.600
[     7.333] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.289 whiteY: 0.299
[     7.333] (II) intel(0): Supported established timings:
[     7.333] (II) intel(0): 640x480@60Hz
[     7.333] (II) intel(0): 800x600@60Hz
[     7.333] (II) intel(0): 1024x768@60Hz
[     7.333] (II) intel(0): Manufacturer's mask: 0
[     7.333] (II) intel(0): Supported detailed timing:
[     7.333] (II) intel(0): clock: 74.2 MHz   Image Size:  640 x 360 mm
[     7.333] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[     7.333] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[     7.333] (II) intel(0): Supported detailed timing:
[     7.333] (II) intel(0): clock: 65.0 MHz   Image Size:  400 x 300 mm
[     7.333] (II) intel(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[     7.333] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[     7.333] (II) intel(0): Monitor name: Philips FTV
[     7.333] (II) intel(0): Ranges: V min: 48 V max: 62 Hz, H min: 15 H max: 50 kHz, PixClock max 95 MHz
[     7.333] (II) intel(0): Supported detailed timing:
[     7.333] (II) intel(0): clock: 74.2 MHz   Image Size:  640 x 360 mm
[     7.333] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     7.333] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[     7.333] (II) intel(0): Supported detailed timing:
[     7.333] (II) intel(0): clock: 74.2 MHz   Image Size:  640 x 360 mm
[     7.333] (II) intel(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[     7.333] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[     7.333] (II) intel(0): Supported detailed timing:
[     7.333] (II) intel(0): clock: 74.2 MHz   Image Size:  640 x 360 mm
[     7.333] (II) intel(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[     7.333] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[     7.333] (II) intel(0): Supported detailed timing:
[     7.333] (II) intel(0): clock: 27.0 MHz   Image Size:  640 x 360 mm
[     7.333] (II) intel(0): h_active: 720  h_sync: 732  h_sync_end 796 h_blank_end 864 h_border: 0
[     7.333] (II) intel(0): v_active: 576  v_sync: 581  v_sync_end 586 v_blanking: 625 v_border: 0
[     7.333] (II) intel(0): Supported detailed timing:
[     7.333] (II) intel(0): clock: 27.0 MHz   Image Size:  640 x 360 mm
[     7.333] (II) intel(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[     7.333] (II) intel(0): v_active: 480  v_sync: 483  v_sync_end 489 v_blanking: 525 v_border: 0
[     7.333] (II) intel(0): Number of EDID sections to follow: 1
[     7.333] (II) intel(0): EDID (in hex):
[     7.333] (II) intel(0):     00ffffffffffff00410c010001010101
[     7.333] (II) intel(0):     01100103804024780ae692a3544a9926
[     7.333] (II) intel(0):     0f4a4c21080001010101010101010101
[     7.333] (II) intel(0):     010101010101011d80d0721c1620102c
[     7.333] (II) intel(0):     258080682100009e6419004041002630
[     7.333] (II) intel(0):     18883600902c11000018000000fc0050
[     7.333] (II) intel(0):     68696c697073204654560a20000000fd
[     7.333] (II) intel(0):     00303e0f3209000a202020202020018b
[     7.333] (II) intel(0):     020324f04b0103040506071213141516
[     7.333] (II) intel(0):     29091f07150750190786830100006503
[     7.333] (II) intel(0):     0c001000011d8018711c1620582c2500
[     7.333] (II) intel(0):     80682100009e011d00bc52d01e20b828
[     7.333] (II) intel(0):     554080682100001e011d007251d01e20
[     7.333] (II) intel(0):     6e28550080682100001e8c0ad0902040
[     7.333] (II) intel(0):     31200c4055008068210000188c0ad08a
[     7.333] (II) intel(0):     20e02d10103e360080682100001800d1
[     7.333] (II) intel(0): Printing probed modes for output HDMI2
[     7.333] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[     7.333] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[     7.333] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[     7.357] (II) intel(0): EDID for output HDMI3
[     7.412] (II) intel(0): EDID for output DP2
[     7.460] (II) intel(0): EDID for output DP3
[     7.460] (II) intel(0): Output VGA1 disconnected
[     7.460] (II) intel(0): Output HDMI1 disconnected
[     7.460] (II) intel(0): Output DP1 disconnected
[     7.460] (II) intel(0): Output HDMI2 connected
[     7.460] (II) intel(0): Output HDMI3 disconnected
[     7.460] (II) intel(0): Output DP2 disconnected
[     7.460] (II) intel(0): Output DP3 disconnected
[     7.460] (II) intel(0): Using fuzzy aspect match for initial modes
[     7.460] (II) intel(0): Output HDMI2 using initial mode 1024x768
[     7.460] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     7.460] (II) intel(0): Kernel page flipping support detected, enabling
[     7.460] (==) intel(0): DPI set to (96, 96)
[     7.460] (II) Loading sub module "fb"
[     7.460] (II) LoadModule: "fb"
[     7.460] (II) Loading /usr/lib/xorg/modules/libfb.so
[     7.460] (II) Module fb: vendor="X.Org Foundation"
[     7.460]    compiled for 1.10.4, module version = 1.0.0
[     7.460]    ABI class: X.Org ANSI C Emulation, version 0.4
[     7.460] (II) Loading sub module "dri2"
[     7.460] (II) LoadModule: "dri2"
[     7.460] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     7.460] (II) Module dri2: vendor="X.Org Foundation"
[     7.460]    compiled for 1.10.4, module version = 1.2.0
[     7.460]    ABI class: X.Org Server Extension, version 5.0
[     7.460] (II) UnloadModule: "vesa"
[     7.460] (II) Unloading vesa
[     7.460] (II) UnloadModule: "fbdev"
[     7.460] (II) Unloading fbdev
[     7.460] (II) UnloadModule: "fbdevhw"
[     7.460] (II) Unloading fbdevhw
[     7.460] (==) Depth 24 pixmap format is 32 bpp
[     7.460] (II) intel(0): [DRI2] Setup complete
[     7.460] (II) intel(0): [DRI2]   DRI driver: i965
[     7.460] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[     7.461] (II) UXA(0): Driver registered support for the following operations:
[     7.461] (II)         solid
[     7.461] (II)         copy
[     7.461] (II)         composite (RENDER acceleration)
[     7.461] (II)         put_image
[     7.461] (II)         get_image
[     7.461] (==) intel(0): Backing store disabled
[     7.461] (==) intel(0): Silken mouse enabled
[     7.461] (II) intel(0): Initializing HW Cursor
[     7.520] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     7.520] (==) intel(0): DPMS enabled
[     7.520] (==) intel(0): Intel XvMC decoder enabled
[     7.520] (II) intel(0): Set up textured video
[     7.520] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[     7.520] (II) intel(0): direct rendering: DRI2 Enabled
[     7.520] (==) intel(0): hotplug detection: "enabled"
[     7.520] (--) RandR disabled
[     7.520] (II) Initializing built-in extension Generic Event Extension
[     7.520] (II) Initializing built-in extension SHAPE
[     7.520] (II) Initializing built-in extension MIT-SHM
[     7.520] (II) Initializing built-in extension XInputExtension
[     7.520] (II) Initializing built-in extension XTEST
[     7.520] (II) Initializing built-in extension BIG-REQUESTS
[     7.520] (II) Initializing built-in extension SYNC
[     7.520] (II) Initializing built-in extension XKEYBOARD
[     7.520] (II) Initializing built-in extension XC-MISC
[     7.520] (II) Initializing built-in extension SECURITY
[     7.520] (II) Initializing built-in extension XINERAMA
[     7.520] (II) Initializing built-in extension XFIXES
[     7.520] (II) Initializing built-in extension RENDER
[     7.520] (II) Initializing built-in extension RANDR
[     7.520] (II) Initializing built-in extension COMPOSITE
[     7.520] (II) Initializing built-in extension DAMAGE
[     7.520] (II) Initializing built-in extension GESTURE
[     7.527] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/i965_dri.so
[     7.530] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     7.530] (II) AIGLX: enabled GLX_INTEL_swap_event
[     7.530] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     7.530] (II) AIGLX: enabled GLX_SGI_make_current_read
[     7.530] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     7.530] (II) AIGLX: Loaded and initialized i965
[     7.530] (II) GLX: Initialized DRI2 GL provider for screen 0
[     7.530] (II) intel(0): Setting screen physical size to 270 x 203
[     7.537] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     7.542] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     7.542] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.542] (II) LoadModule: "evdev"
[     7.542] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.543] (II) Module evdev: vendor="X.Org Foundation"
[     7.543]    compiled for 1.10.2, module version = 2.6.0
[     7.543]    Module class: X.Org XInput Driver
[     7.543]    ABI class: X.Org XInput driver, version 12.3
[     7.543] (II) Using input driver 'evdev' for 'Power Button'
[     7.543] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.543] (**) Power Button: always reports core events
[     7.543] (**) Power Button: Device: "/dev/input/event1"
[     7.543] (--) Power Button: Found keys
[     7.543] (II) Power Button: Configuring as keyboard
[     7.543] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     7.543] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[     7.543] (**) Option "xkb_rules" "evdev"
[     7.543] (**) Option "xkb_model" "pc105"
[     7.543] (**) Option "xkb_layout" "us"
[     7.545] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     7.545] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.545] (II) Using input driver 'evdev' for 'Power Button'
[     7.545] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.545] (**) Power Button: always reports core events
[     7.545] (**) Power Button: Device: "/dev/input/event0"
[     7.545] (--) Power Button: Found keys
[     7.545] (II) Power Button: Configuring as keyboard
[     7.545] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     7.545] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[     7.545] (**) Option "xkb_rules" "evdev"
[     7.545] (**) Option "xkb_model" "pc105"
[     7.545] (**) Option "xkb_layout" "us"
[     7.547] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event5)
[     7.547] (II) No input driver/identifier specified (ignoring)
[     7.547] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event6)
[     7.547] (II) No input driver/identifier specified (ignoring)
[     7.548] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event4)
[     7.548] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[     7.548] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[     7.548] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.548] (**) USB Optical Mouse: always reports core events
[     7.548] (**) USB Optical Mouse: Device: "/dev/input/event4"
[     7.548] (--) USB Optical Mouse: Found 3 mouse buttons
[     7.548] (--) USB Optical Mouse: Found scroll wheel(s)
[     7.548] (--) USB Optical Mouse: Found relative axes
[     7.548] (--) USB Optical Mouse: Found x and y relative axes
[     7.548] (II) USB Optical Mouse: Configuring as mouse
[     7.548] (II) USB Optical Mouse: Adding scrollwheel support
[     7.548] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[     7.548] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     7.548] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0/usb3/3-1/3-1.4/3-1.4:1.0/input/input4/event4"
[     7.548] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[     7.548] (II) USB Optical Mouse: initialized for relative axes.
[     7.549] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[     7.549] (**) USB Optical Mouse: (accel) acceleration profile 0
[     7.549] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[     7.549] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[     7.549] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[     7.549] (II) No input driver/identifier specified (ignoring)
[     7.549] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event2)
[     7.549] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[     7.550] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[     7.550] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.550] (**) HID 04f3:0103: always reports core events
[     7.550] (**) HID 04f3:0103: Device: "/dev/input/event2"
[     7.550] (--) HID 04f3:0103: Found keys
[     7.550] (II) HID 04f3:0103: Configuring as keyboard
[     7.550] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input2/event2"
[     7.550] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD)
[     7.550] (**) Option "xkb_rules" "evdev"
[     7.550] (**) Option "xkb_model" "pc105"
[     7.550] (**) Option "xkb_layout" "us"
[     7.550] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event3)
[     7.550] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[     7.550] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[     7.550] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.550] (**) HID 04f3:0103: always reports core events
[     7.550] (**) HID 04f3:0103: Device: "/dev/input/event3"
[     7.550] (--) HID 04f3:0103: Found 1 mouse buttons
[     7.550] (--) HID 04f3:0103: Found scroll wheel(s)
[     7.550] (--) HID 04f3:0103: Found relative axes
[     7.550] (--) HID 04f3:0103: Found absolute axes
[     7.550] (II) evdev-grail: failed to open grail, no gesture support
[     7.550] (--) HID 04f3:0103: Found keys
[     7.550] (II) HID 04f3:0103: Configuring as mouse
[     7.550] (II) HID 04f3:0103: Configuring as keyboard
[     7.550] (II) HID 04f3:0103: Adding scrollwheel support
[     7.550] (**) HID 04f3:0103: YAxisMapping: buttons 4 and 5
[     7.550] (**) HID 04f3:0103: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     7.550] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.1/input/input3/event3"
[     7.550] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD)
[     7.550] (**) Option "xkb_rules" "evdev"
[     7.550] (**) Option "xkb_model" "pc105"
[     7.550] (**) Option "xkb_layout" "us"
[     7.550] (EE) HID 04f3:0103: failed to initialize for relative axes.
[     7.550] (II) HID 04f3:0103: initialized for absolute axes.
[     7.550] (**) HID 04f3:0103: (accel) keeping acceleration scheme 1
[     7.550] (**) HID 04f3:0103: (accel) acceleration profile 0
[     7.550] (**) HID 04f3:0103: (accel) acceleration factor: 2.000
[     7.550] (**) HID 04f3:0103: (accel) acceleration threshold: 4
[     8.026] (II) intel(0): EDID vendor "PHL", prod id 1
[     8.026] (II) intel(0): Using EDID range info for horizontal sync
[     8.026] (II) intel(0): Using EDID range info for vertical refresh
[     8.026] (II) intel(0): Printing DDC gathered Modelines:
[     8.026] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[     8.026] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[     8.026] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[     8.026] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[     8.026] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[     8.026] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[     8.026] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[     8.026] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[     8.026] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[     8.026] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[     8.026] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[     8.026] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[     8.026] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[     8.026] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    10.898] (II) intel(0): EDID vendor "PHL", prod id 1
[    10.898] (II) intel(0): Using hsync ranges from config file
[    10.898] (II) intel(0): Using vrefresh ranges from config file
[    10.898] (II) intel(0): Printing DDC gathered Modelines:
[    10.898] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    10.898] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    10.898] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    10.898] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    10.898] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    10.898] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    10.898] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[    10.898] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    10.898] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    10.898] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    10.898] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    10.898] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    10.898] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    10.898] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    11.938] (II) intel(0): EDID vendor "PHL", prod id 1
[    11.938] (II) intel(0): Using hsync ranges from config file
[    11.938] (II) intel(0): Using vrefresh ranges from config file
[    11.938] (II) intel(0): Printing DDC gathered Modelines:
[    11.938] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    11.938] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    11.938] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    11.938] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    11.938] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    11.938] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    11.938] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[    11.938] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    11.938] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    11.938] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    11.938] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    11.938] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    11.938] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    11.938] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)

```

---

### Post by BicyclerBoy on 2012-01-06
Appears to be using 1024x768 (XGA) for HDMI2 but the EDID modelines seems okay..

There are lots of bugs in sandybridge with HDMI & displayport.

I would suggest trying the retrograde step of using a VGA cable (temporarily).

Post output from:
xrandr --prop

I wouldn't use 32bit linux/ubuntu on any CPU that supports 64..

---

### Post by alfonso78 on 2012-01-06
> **BicyclerBoy said:**
> Appears to be using 1024x768 (XGA) for HDMI2 but the EDID modelines seems okay..

There are lots of bugs in sandybridge with HDMI & displayport.

I would suggest trying the retrograde step of using a VGA cable (temporarily).

Post output from:
xrandr --prop

I wouldn't use 32bit linux/ubuntu on any CPU that supports 64..

Hi and thank you!

It seems I have a more pressing problem... The system hangs after about 20 minutes with no message in /var/log/syslog

I added a random command for every minute in crontab (echo "beep" | wall) to monitor the system and in the minute of the last entry in syslog there is no other entry in any log in /var/log.

So I will start a new thread and come back to this when the computer seems a bit more stable.

Regarding your suggestion for 64 bit: to be honest I put to much effort in configuring this installation. I'm not so thrilled thinking of throwing all this work. I'll go in that direction only if it's my last option.

Thank you for your help so far and hopefully you'll have time to give me more ideas when I make the system stable!

alfonso

---

### Post by alfonso78 on 2012-01-07
Hi!

so it seems the system is more stable now. It was running for about 8 hours and it also completed the RAID re-sync. So I can move on.

I thought that maybe the X problem could also be the reason for the instability, so I did the following:
```

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade

```

This PPA is for stable upstream releases of X.org components.

But unfortunately the screen still has the same problem.

About VGA: my MB does not have a VGA connector. I have only a DVI connector with an adapter. I tried to connect the box to the TV using the adapter, then switched the TV to VGA input and then switched the box off and on (without the HDMI cable plugged in). But I cannot see anything, not even the BIOS.
So I have to find an other way...

any idea from here?

thank you!

---

### Post by alfonso78 on 2012-01-07
So,

I removed ppa:ubuntu-x-swat/x-updates and installed ppa:xorg-edgers/ppa:

```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

```

but my screen is still spit in two... :(

here is /var/log/Xorg.0.log:

```

$ cat Xorg.0.log
[    13.071]
X.Org X Server 1.11.2.902 (1.11.3 RC 2)
Release Date: 2011-12-09
[    13.071] X Protocol Version 11, Revision 0
[    13.071] Build Operating System: Linux 2.6.24-29-xen i686 Ubuntu
[    13.071] Current Operating System: Linux NAS 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686
[    13.071] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic-pae root=UUID=2f050176-99ce-49de-9826-a01fe25ecec9 ro bootdegraded=true debug ignore_loglevel
[    13.071] Build Date: 10 December 2011  11:17:47PM
[    13.071] xorg-server 2:1.11.2.902+git20111209+server-1.11-branch.0ca8869e-0ubuntu0sarvatt~oneiric (For technical support please see http://www.ubuntu.com/support)
[    13.071] Current version of pixman: 0.24.0
[    13.071]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    13.071] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.071] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan  7 13:26:58 2012
[    13.072] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    13.073] (==) No Layout section.  Using the first Screen section.
[    13.073] (==) No screen section available. Using defaults.
[    13.073] (**) |-->Screen "Default Screen Section" (0)
[    13.073] (**) |   |-->Monitor "<default monitor>"
[    13.074] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    13.074] (==) Automatically adding devices
[    13.074] (==) Automatically enabling devices
[    13.074] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.074]    Entry deleted from font path.
[    13.074] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    13.074]    Entry deleted from font path.
[    13.074] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    13.074]    Entry deleted from font path.
[    13.074] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    13.074]    Entry deleted from font path.
[    13.074] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    13.074]    Entry deleted from font path.
[    13.074] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[    13.074] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    13.074] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    13.075] (II) Loader magic: 0x822a580
[    13.075] (II) Module ABI versions:
[    13.075]    X.Org ANSI C Emulation: 0.4
[    13.075]    X.Org Video Driver: 11.0
[    13.075]    X.Org XInput driver : 13.0
[    13.075]    X.Org Server Extension : 6.0
[    13.075] (--) PCI:*(0:0:2:0) 8086:0102:19da:a166 rev 9, Mem @ 0xfe000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
[    13.075] (II) Open ACPI successful (/var/run/acpid.socket)
[    13.075] (II) LoadModule: "extmod"
[    13.076] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    13.077] (II) Module extmod: vendor="X.Org Foundation"
[    13.077]    compiled for 1.11.2.902, module version = 1.0.0
[    13.077]    Module class: X.Org Server Extension
[    13.077]    ABI class: X.Org Server Extension, version 6.0
[    13.077] (II) Loading extension MIT-SCREEN-SAVER
[    13.077] (II) Loading extension XFree86-VidModeExtension
[    13.077] (II) Loading extension XFree86-DGA
[    13.077] (II) Loading extension DPMS
[    13.077] (II) Loading extension XVideo
[    13.077] (II) Loading extension XVideo-MotionCompensation
[    13.077] (II) Loading extension X-Resource
[    13.077] (II) LoadModule: "dbe"
[    13.077] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    13.078] (II) Module dbe: vendor="X.Org Foundation"
[    13.078]    compiled for 1.11.2.902, module version = 1.0.0
[    13.078]    Module class: X.Org Server Extension
[    13.078]    ABI class: X.Org Server Extension, version 6.0
[    13.078] (II) Loading extension DOUBLE-BUFFER
[    13.078] (II) LoadModule: "glx"
[    13.078] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    13.081] (II) Module glx: vendor="X.Org Foundation"
[    13.081]    compiled for 1.11.2.902, module version = 1.0.0
[    13.081]    ABI class: X.Org Server Extension, version 6.0
[    13.081] (==) AIGLX enabled
[    13.081] (II) Loading extension GLX
[    13.081] (II) LoadModule: "record"
[    13.081] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    13.082] (II) Module record: vendor="X.Org Foundation"
[    13.082]    compiled for 1.11.2.902, module version = 1.13.0
[    13.082]    Module class: X.Org Server Extension
[    13.082]    ABI class: X.Org Server Extension, version 6.0
[    13.082] (II) Loading extension RECORD
[    13.082] (II) LoadModule: "dri"
[    13.082] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    13.084] (II) Module dri: vendor="X.Org Foundation"
[    13.084]    compiled for 1.11.2.902, module version = 1.0.0
[    13.084]    ABI class: X.Org Server Extension, version 6.0
[    13.084] (II) Loading extension XFree86-DRI
[    13.084] (II) LoadModule: "dri2"
[    13.084] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.085] (II) Module dri2: vendor="X.Org Foundation"
[    13.085]    compiled for 1.11.2.902, module version = 1.2.0
[    13.085]    ABI class: X.Org Server Extension, version 6.0
[    13.085] (II) Loading extension DRI2
[    13.085] (==) Matched intel as autoconfigured driver 0
[    13.085] (==) Matched vesa as autoconfigured driver 1
[    13.085] (==) Matched fbdev as autoconfigured driver 2
[    13.085] (==) Assigned the driver to the xf86ConfigLayout
[    13.085] (II) LoadModule: "intel"
[    13.085] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    13.089] (II) Module intel: vendor="X.Org Foundation"
[    13.089]    compiled for 1.11.2.902, module version = 2.17.0
[    13.089]    Module class: X.Org Video Driver
[    13.089]    ABI class: X.Org Video Driver, version 11.0
[    13.089] (II) LoadModule: "vesa"
[    13.090] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    13.090] (II) Module vesa: vendor="X.Org Foundation"
[    13.090]    compiled for 1.11.2, module version = 2.3.0
[    13.090]    Module class: X.Org Video Driver
[    13.090]    ABI class: X.Org Video Driver, version 11.0
[    13.090] (II) LoadModule: "fbdev"
[    13.090] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    13.091] (II) Module fbdev: vendor="X.Org Foundation"
[    13.091]    compiled for 1.11.2, module version = 0.4.2
[    13.091]    Module class: X.Org Video Driver
[    13.091]    ABI class: X.Org Video Driver, version 11.0
[    13.091] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
        Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
        Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
        Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
        Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    13.092] (II) VESA: driver for VESA chipsets: vesa
[    13.092] (II) FBDEV: driver for framebuffer: fbdev
[    13.092] (++) using VT number 7

[    13.093] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    13.093] (WW) Falling back to old probe method for vesa
[    13.093] (WW) Falling back to old probe method for fbdev
[    13.093] (II) Loading sub module "fbdevhw"
[    13.093] (II) LoadModule: "fbdevhw"
[    13.093] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    13.093] (II) Module fbdevhw: vendor="X.Org Foundation"
[    13.093]    compiled for 1.11.2.902, module version = 0.0.2
[    13.093]    ABI class: X.Org Video Driver, version 11.0
[    13.094] drmOpenDevice: node name is /dev/dri/card0
[    13.094] drmOpenDevice: open result is 12, (OK)
[    13.094] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    13.094] drmOpenDevice: node name is /dev/dri/card0
[    13.094] drmOpenDevice: open result is 12, (OK)
[    13.094] drmOpenByBusid: drmOpenMinor returns 12
[    13.094] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    13.094] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    13.094] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    13.094] (==) intel(0): RGB weight 888
[    13.094] (==) intel(0): Default visual is TrueColor
[    13.094] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Desktop (GT1)
[    13.094] (--) intel(0): Chipset: "Sandybridge Desktop (GT1)"
[    13.094] (**) intel(0): Relaxed fencing enabled
[    13.094] (**) intel(0): Wait on SwapBuffers? enabled
[    13.094] (**) intel(0): Triple buffering? enabled
[    13.094] (**) intel(0): Framebuffer tiled
[    13.094] (**) intel(0): Pixmaps tiled
[    13.094] (**) intel(0): 3D buffers tiled
[    13.094] (**) intel(0): SwapBuffers wait enabled
[    13.094] (==) intel(0): video overlay key set to 0x101fe
[    13.094] (II) intel(0): Output VGA1 has no monitor section
[    13.117] (II) intel(0): Output HDMI1 has no monitor section
[    13.164] (II) intel(0): Output DP1 has no monitor section
[    13.410] (II) intel(0): Output HDMI2 has no monitor section
[    13.433] (II) intel(0): Output HDMI3 has no monitor section
[    13.480] (II) intel(0): Output DP2 has no monitor section
[    13.528] (II) intel(0): Output DP3 has no monitor section
[    13.528] (II) intel(0): EDID for output VGA1
[    13.551] (II) intel(0): EDID for output HDMI1
[    13.596] (II) intel(0): EDID for output DP1
[    14.054] (II) intel(0): EDID for output HDMI2
[    14.054] (II) intel(0): Manufacturer: PHL  Model: 1  Serial#: 16843009
[    14.054] (II) intel(0): Year: 2006  Week: 1
[    14.054] (II) intel(0): EDID Version: 1.3
[    14.054] (II) intel(0): Digital Display Input
[    14.054] (II) intel(0): Max Image Size [cm]: horiz.: 64  vert.: 36
[    14.054] (II) intel(0): Gamma: 2.20
[    14.054] (II) intel(0): No DPMS capabilities specified
[    14.054] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[    14.054] (II) intel(0): First detailed timing is preferred mode
[    14.054] (II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.290 greenY: 0.600
[    14.054] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.289 whiteY: 0.299
[    14.054] (II) intel(0): Supported established timings:
[    14.054] (II) intel(0): 640x480@60Hz
[    14.054] (II) intel(0): 800x600@60Hz
[    14.054] (II) intel(0): 1024x768@60Hz
[    14.054] (II) intel(0): Manufacturer's mask: 0
[    14.054] (II) intel(0): Supported detailed timing:
[    14.054] (II) intel(0): clock: 74.2 MHz   Image Size:  640 x 360 mm
[    14.054] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    14.054] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    14.054] (II) intel(0): Supported detailed timing:
[    14.054] (II) intel(0): clock: 65.0 MHz   Image Size:  400 x 300 mm
[    14.054] (II) intel(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[    14.054] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[    14.054] (II) intel(0): Monitor name: Philips FTV
[    14.054] (II) intel(0): Ranges: V min: 48 V max: 62 Hz, H min: 15 H max: 50 kHz, PixClock max 95 MHz
[    14.054] (II) intel(0): Supported detailed timing:
[    14.054] (II) intel(0): clock: 74.2 MHz   Image Size:  640 x 360 mm
[    14.054] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    14.054] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    14.054] (II) intel(0): Supported detailed timing:
[    14.054] (II) intel(0): clock: 74.2 MHz   Image Size:  640 x 360 mm
[    14.054] (II) intel(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[    14.054] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    14.054] (II) intel(0): Supported detailed timing:
[    14.054] (II) intel(0): clock: 74.2 MHz   Image Size:  640 x 360 mm
[    14.054] (II) intel(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    14.054] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    14.054] (II) intel(0): Supported detailed timing:
[    14.054] (II) intel(0): clock: 27.0 MHz   Image Size:  640 x 360 mm
[    14.054] (II) intel(0): h_active: 720  h_sync: 732  h_sync_end 796 h_blank_end 864 h_border: 0
[    14.054] (II) intel(0): v_active: 576  v_sync: 581  v_sync_end 586 v_blanking: 625 v_border: 0
[    14.054] (II) intel(0): Supported detailed timing:
[    14.054] (II) intel(0): clock: 27.0 MHz   Image Size:  640 x 360 mm
[    14.054] (II) intel(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    14.054] (II) intel(0): v_active: 480  v_sync: 483  v_sync_end 489 v_blanking: 525 v_border: 0
[    14.054] (II) intel(0): Number of EDID sections to follow: 1
[    14.054] (II) intel(0): EDID (in hex):
[    14.054] (II) intel(0):     00ffffffffffff00410c010001010101
[    14.054] (II) intel(0):     01100103804024780ae692a3544a9926
[    14.054] (II) intel(0):     0f4a4c21080001010101010101010101
[    14.054] (II) intel(0):     010101010101011d80d0721c1620102c
[    14.054] (II) intel(0):     258080682100009e6419004041002630
[    14.054] (II) intel(0):     18883600902c11000018000000fc0050
[    14.054] (II) intel(0):     68696c697073204654560a20000000fd
[    14.054] (II) intel(0):     00303e0f3209000a202020202020018b
[    14.054] (II) intel(0):     020324f04b0103040506071213141516
[    14.054] (II) intel(0):     29091f07150750190786830100006503
[    14.054] (II) intel(0):     0c001000011d8018711c1620582c2500
[    14.054] (II) intel(0):     80682100009e011d00bc52d01e20b828
[    14.054] (II) intel(0):     554080682100001e011d007251d01e20
[    14.054] (II) intel(0):     6e28550080682100001e8c0ad0902040
[    14.055] (II) intel(0):     31200c4055008068210000188c0ad08a
[    14.055] (II) intel(0):     20e02d10103e360080682100001800d1
[    14.055] (II) intel(0): Printing probed modes for output HDMI2
[    14.055] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.055] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.055] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.078] (II) intel(0): EDID for output HDMI3
[    14.124] (II) intel(0): EDID for output DP2
[    14.172] (II) intel(0): EDID for output DP3
[    14.172] (II) intel(0): Output VGA1 disconnected
[    14.172] (II) intel(0): Output HDMI1 disconnected
[    14.172] (II) intel(0): Output DP1 disconnected
[    14.172] (II) intel(0): Output HDMI2 connected
[    14.172] (II) intel(0): Output HDMI3 disconnected
[    14.172] (II) intel(0): Output DP2 disconnected
[    14.172] (II) intel(0): Output DP3 disconnected
[    14.172] (II) intel(0): Using fuzzy aspect match for initial modes
[    14.172] (II) intel(0): Output HDMI2 using initial mode 1024x768
[    14.172] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    14.172] (II) intel(0): Kernel page flipping support detected, enabling
[    14.172] (==) intel(0): DPI set to (96, 96)
[    14.172] (II) Loading sub module "fb"
[    14.172] (II) LoadModule: "fb"
[    14.172] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.173] (II) Module fb: vendor="X.Org Foundation"
[    14.173]    compiled for 1.11.2.902, module version = 1.0.0
[    14.173]    ABI class: X.Org ANSI C Emulation, version 0.4
[    14.173] (II) Loading sub module "dri2"
[    14.173] (II) LoadModule: "dri2"
[    14.173] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.173] (II) Module dri2: vendor="X.Org Foundation"
[    14.173]    compiled for 1.11.2.902, module version = 1.2.0
[    14.173]    ABI class: X.Org Server Extension, version 6.0
[    14.173] (II) UnloadModule: "vesa"
[    14.173] (II) Unloading vesa
[    14.173] (II) UnloadModule: "fbdev"
[    14.173] (II) Unloading fbdev
[    14.173] (II) UnloadModule: "fbdevhw"
[    14.173] (II) Unloading fbdevhw
[    14.173] (==) Depth 24 pixmap format is 32 bpp
[    14.173] (II) intel(0): [DRI2] Setup complete
[    14.173] (II) intel(0): [DRI2]   DRI driver: i965
[    14.173] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    14.177] (II) UXA(0): Driver registered support for the following operations:
[    14.177] (II)         solid
[    14.177] (II)         copy
[    14.177] (II)         composite (RENDER acceleration)
[    14.177] (II)         put_image
[    14.177] (II)         get_image
[    14.177] (==) intel(0): Backing store disabled
[    14.177] (==) intel(0): Silken mouse enabled
[    14.177] (II) intel(0): Initializing HW Cursor
[    14.237] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    14.238] (==) intel(0): DPMS enabled
[    14.238] (==) intel(0): Intel XvMC decoder enabled
[    14.238] (II) intel(0): Set up textured video
[    14.238] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    14.238] (II) intel(0): direct rendering: DRI2 Enabled
[    14.238] (==) intel(0): hotplug detection: "enabled"
[    14.238] (--) RandR disabled
[    14.238] (II) Initializing built-in extension Generic Event Extension
[    14.238] (II) Initializing built-in extension SHAPE
[    14.238] (II) Initializing built-in extension MIT-SHM
[    14.238] (II) Initializing built-in extension XInputExtension
[    14.238] (II) Initializing built-in extension XTEST
[    14.238] (II) Initializing built-in extension BIG-REQUESTS
[    14.238] (II) Initializing built-in extension SYNC
[    14.238] (II) Initializing built-in extension XKEYBOARD
[    14.238] (II) Initializing built-in extension XC-MISC
[    14.238] (II) Initializing built-in extension SECURITY
[    14.238] (II) Initializing built-in extension XINERAMA
[    14.238] (II) Initializing built-in extension XFIXES
[    14.238] (II) Initializing built-in extension RENDER
[    14.238] (II) Initializing built-in extension RANDR
[    14.238] (II) Initializing built-in extension COMPOSITE
[    14.238] (II) Initializing built-in extension DAMAGE
[    14.244] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/i965_dri.so
[    14.260] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    14.260] (II) AIGLX: enabled GLX_INTEL_swap_event
[    14.260] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    14.260] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    14.260] (II) AIGLX: Loaded and initialized i965
[    14.260] (II) GLX: Initialized DRI2 GL provider for screen 0
[    14.260] (II) intel(0): Setting screen physical size to 270 x 203
[    14.268] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    14.270] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    14.270] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.270] (II) LoadModule: "evdev"
[    14.271] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.271] (II) Module evdev: vendor="X.Org Foundation"
[    14.271]    compiled for 1.11.2.902, module version = 2.6.99
[    14.271]    Module class: X.Org XInput Driver
[    14.271]    ABI class: X.Org XInput driver, version 13.0
[    14.271] (II) Using input driver 'evdev' for 'Power Button'
[    14.271] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.271] (**) Power Button: always reports core events
[    14.271] (**) evdev: Power Button: Device: "/dev/input/event1"
[    14.271] (--) evdev: Power Button: Vendor 0 Product 0x1
[    14.271] (--) evdev: Power Button: Found keys
[    14.271] (II) evdev: Power Button: Configuring as keyboard
[    14.271] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    14.271] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    14.271] (**) Option "xkb_rules" "evdev"
[    14.271] (**) Option "xkb_model" "pc105"
[    14.271] (**) Option "xkb_layout" "us"
[    14.272] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    14.272] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.272] (II) Using input driver 'evdev' for 'Power Button'
[    14.272] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.272] (**) Power Button: always reports core events
[    14.272] (**) evdev: Power Button: Device: "/dev/input/event0"
[    14.272] (--) evdev: Power Button: Vendor 0 Product 0x1
[    14.272] (--) evdev: Power Button: Found keys
[    14.272] (II) evdev: Power Button: Configuring as keyboard
[    14.272] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    14.272] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    14.272] (**) Option "xkb_rules" "evdev"
[    14.272] (**) Option "xkb_model" "pc105"
[    14.272] (**) Option "xkb_layout" "us"
[    14.272] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event5)
[    14.272] (II) No input driver/identifier specified (ignoring)
[    14.272] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event6)
[    14.272] (II) No input driver/identifier specified (ignoring)
[    14.273] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event4)
[    14.273] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    14.273] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    14.273] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.273] (**) USB Optical Mouse: always reports core events
[    14.273] (**) evdev: USB Optical Mouse: Device: "/dev/input/event4"
[    14.273] (--) evdev: USB Optical Mouse: Vendor 0x15ca Product 0xc3
[    14.273] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    14.273] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    14.273] (--) evdev: USB Optical Mouse: Found relative axes
[    14.273] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    14.273] (II) evdev: USB Optical Mouse: Configuring as mouse
[    14.273] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    14.273] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    14.273] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.273] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0/usb3/3-1/3-1.4/3-1.4:1.0/input/input4/event4"
[    14.273] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 8)
[    14.273] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    14.273] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    14.273] (**) USB Optical Mouse: (accel) acceleration profile 0
[    14.273] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    14.273] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    14.273] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    14.273] (II) No input driver/identifier specified (ignoring)
[    14.273] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event2)
[    14.273] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[    14.273] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[    14.273] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.273] (**) HID 04f3:0103: always reports core events
[    14.273] (**) evdev: HID 04f3:0103: Device: "/dev/input/event2"
[    14.273] (--) evdev: HID 04f3:0103: Vendor 0x4f3 Product 0x103
[    14.273] (--) evdev: HID 04f3:0103: Found keys
[    14.273] (II) evdev: HID 04f3:0103: Configuring as keyboard
[    14.273] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input2/event2"
[    14.273] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD, id 9)
[    14.273] (**) Option "xkb_rules" "evdev"
[    14.273] (**) Option "xkb_model" "pc105"
[    14.273] (**) Option "xkb_layout" "us"
[    14.274] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event3)
[    14.274] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[    14.274] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[    14.274] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.274] (**) HID 04f3:0103: always reports core events
[    14.274] (**) evdev: HID 04f3:0103: Device: "/dev/input/event3"
[    14.274] (--) evdev: HID 04f3:0103: Vendor 0x4f3 Product 0x103
[    14.274] (--) evdev: HID 04f3:0103: Found 1 mouse buttons
[    14.274] (--) evdev: HID 04f3:0103: Found scroll wheel(s)
[    14.274] (--) evdev: HID 04f3:0103: Found relative axes
[    14.274] (--) evdev: HID 04f3:0103: Found absolute axes
[    14.274] (--) evdev: HID 04f3:0103: Found keys
[    14.274] (II) evdev: HID 04f3:0103: Configuring as mouse
[    14.274] (II) evdev: HID 04f3:0103: Configuring as keyboard
[    14.274] (II) evdev: HID 04f3:0103: Adding scrollwheel support
[    14.274] (**) evdev: HID 04f3:0103: YAxisMapping: buttons 4 and 5
[    14.274] (**) evdev: HID 04f3:0103: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.274] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.1/input/input3/event3"
[    14.274] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD, id 10)
[    14.274] (**) Option "xkb_rules" "evdev"
[    14.274] (**) Option "xkb_model" "pc105"
[    14.274] (**) Option "xkb_layout" "us"
[    14.274] (EE) evdev: HID 04f3:0103: failed to initialize for relative axes.
[    14.274] (II) evdev: HID 04f3:0103: initialized for absolute axes.
[    14.274] (**) HID 04f3:0103: (accel) keeping acceleration scheme 1
[    14.274] (**) HID 04f3:0103: (accel) acceleration profile 0
[    14.274] (**) HID 04f3:0103: (accel) acceleration factor: 2.000
[    14.274] (**) HID 04f3:0103: (accel) acceleration threshold: 4
[    14.998] (II) intel(0): EDID vendor "PHL", prod id 1
[    14.998] (II) intel(0): Using EDID range info for horizontal sync
[    14.998] (II) intel(0): Using EDID range info for vertical refresh
[    14.998] (II) intel(0): Printing DDC gathered Modelines:
[    14.998] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    14.998] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.998] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    14.998] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    14.998] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    14.998] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    14.998] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[    14.998] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.998] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.998] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    14.998] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    14.998] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    14.998] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    14.998] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    18.090] (II) intel(0): EDID vendor "PHL", prod id 1
[    18.090] (II) intel(0): Using hsync ranges from config file
[    18.090] (II) intel(0): Using vrefresh ranges from config file
[    18.090] (II) intel(0): Printing DDC gathered Modelines:
[    18.090] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    18.090] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.090] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    18.090] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    18.090] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    18.090] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    18.090] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[    18.090] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.090] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.090] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    18.090] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    18.090] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    18.090] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    18.090] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    18.706] (II) intel(0): EDID vendor "PHL", prod id 1
[    18.706] (II) intel(0): Using hsync ranges from config file
[    18.706] (II) intel(0): Using vrefresh ranges from config file
[    18.706] (II) intel(0): Printing DDC gathered Modelines:
[    18.706] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    18.706] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.706] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    18.706] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    18.706] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    18.706] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    18.706] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[    18.706] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.706] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.706] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    18.706] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    18.706] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    18.706] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    18.706] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)

```

---

### Post by alfonso78 on 2012-01-07
> **thomasedison13 said:**
> now how is it working? does it works properly after removing it? 


[Performance Chips](http://www.engineperformancechip.com)

I cannot see anything on my TV over VGA.
If I use HDMI, I tried standard Ubuntu 11.10, ppa:ubuntu-x-swat/x-updates and ppa: xorg-edgers/ppa but in all cases the screen is still with the top half showing both in the top and the bottom.

---

### Post by alfonso78 on 2012-01-07
> **BicyclerBoy said:**
> 
Post output from:
xrandr --prop


I forgot you asked me this:

```

$ xrandr --prop
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
	Broadcast RGB:	Full
		supported: Full         Limited 16:2
	audio:	auto
		supported: off          auto         on          
DP1 disconnected (normal left inverted right x axis y axis)
	Broadcast RGB:	Full
		supported: Full         Limited 16:2
	audio:	auto
		supported: off          auto         on          
HDMI2 connected 1024x768+0+0 (normal left inverted right x axis y axis) 640mm x 360mm
	EDID:
		00ffffffffffff00410c010001010101
		01100103804024780ae692a3544a9926
		0f4a4c21080001010101010101010101
		010101010101011d80d0721c1620102c
		258080682100009e6419004041002630
		18883600902c11000018000000fc0050
		68696c697073204654560a20000000fd
		00303e0f3209000a202020202020018b
		020324f04b0103040506071213141516
		29091f07150750190786830100006503
		0c001000011d8018711c1620582c2500
		80682100009e011d00bc52d01e20b828
		554080682100001e011d007251d01e20
		6e28550080682100001e8c0ad0902040
		31200c4055008068210000188c0ad08a
		20e02d10103e360080682100001800d1
	Broadcast RGB:	Full
		supported: Full         Limited 16:2
	audio:	auto
		supported: off          auto         on          
   1024x768       60.0* 
   800x600        60.3  
   640x480        60.0  
HDMI3 disconnected (normal left inverted right x axis y axis)
	Broadcast RGB:	Full
		supported: Full         Limited 16:2
	audio:	auto
		supported: off          auto         on          
DP2 disconnected (normal left inverted right x axis y axis)
	Broadcast RGB:	Full
		supported: Full         Limited 16:2
	audio:	auto
		supported: off          auto         on          
DP3 disconnected (normal left inverted right x axis y axis)
	Broadcast RGB:	Full
		supported: Full         Limited 16:2
	audio:	auto
		supported: off          auto         on          

```

---

### Post by alfonso78 on 2012-01-07
I tried to follow a suggestion I found here (at the bottom):
[https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution)

so I tried to disable KMS with:

```
echo options i915 modeset=0 > /etc/modprobe.d/i915-kms.conf
```

but it didn't work. So I re-enabled it and then tried using the framebuffer -fbdev driver following this page:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

again, no success.

Still split screen...

---

### Post by alfonso78 on 2012-01-07
I tested Live Debian 6.0.3 with Gnome and the screen was handled without problem.

This is Xorg.0.log. Is there anything I can learn from this that would help me make Ubuntu work?

Thank you.

```

# cat Xorg.0.log

X.Org X Server 1.7.7
Release Date: 2010-05-04
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.32.29-dsa-ia32 i686 Debian
Current Operating System: Linux debian 2.6.32-5-486 #1 Mon Oct 3 03:34:28 UTC 2011 i686
Kernel command line: initrd=/live/initrd.img boot=live config   quiet BOOT_IMAGE=/live/vmlinuz
Build Date: 19 February 2011  02:37:36PM
xorg-server 2:1.7.7-13 (Cyril Brulebois <kibi@debian.org>)
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan  7 18:55:44 2012
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81ecca0
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 6.0
        X.Org XInput driver : 7.0
        X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:0102:19da:a166 Intel Corporation Sandy Bridge Integrated Graphics Controller rev 9, Mem @ 0xfe000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.7.7, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension SELinux
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
        compiled for 1.7.7, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.7.7, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.7.7, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.7.7, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.7.7, module version = 1.1.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
        compiled for 1.7.7, module version = 2.13.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
        compiled for 1.7.7, module version = 2.3.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
        compiled for 1.7.6.901, module version = 0.4.2
        ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
        Sandybridge, Sandybridge
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
        compiled for 1.7.7, module version = 0.0.2
        ABI class: X.Org Video Driver, version 6.0
(EE) open /dev/fb0: No such file or directory
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 1.7.7, module version = 1.1.0
        ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.7.7, module version = 1.0.0
        ABI class: X.Org Video Driver, version 6.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65472 kB
(II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Desktop Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: PHL  Model: 1  Serial#: 16843009
(II) VESA(0): Year: 2006  Week: 1
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): Max Image Size [cm]: horiz.: 64  vert.: 36
(II) VESA(0): Gamma: 2.20
(II) VESA(0): No DPMS capabilities specified
(II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.640 redY: 0.330   greenX: 0.290 greenY: 0.600
(II) VESA(0): blueX: 0.150 blueY: 0.060   whiteX: 0.289 whiteY: 0.299
(II) VESA(0): Supported established timings:
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported detailed timing:
(II) VESA(0): clock: 74.2 MHz   Image Size:  640 x 360 mm
(II) VESA(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) VESA(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
(II) VESA(0): Supported detailed timing:
(II) VESA(0): clock: 65.0 MHz   Image Size:  400 x 300 mm
(II) VESA(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) VESA(0): Monitor name: Philips FTV
(II) VESA(0): Ranges: V min: 48 V max: 62 Hz, H min: 15 H max: 50 kHz, PixClock max 95 MHz
(II) VESA(0): Number of EDID sections to follow: 1
(II) VESA(0): EDID (in hex):
(II) VESA(0):   00ffffffffffff00410c010001010101
(II) VESA(0):   01100103804024780ae692a3544a9926
(II) VESA(0):   0f4a4c21080001010101010101010101
(II) VESA(0):   010101010101011d80d0721c1620102c
(II) VESA(0):   258080682100009e6419004041002630
(II) VESA(0):   18883600902c11000018000000fc0050
(II) VESA(0):   68696c697073204654560a20000000fd
(II) VESA(0):   00303e0f3209000a202020202020018b
(II) VESA(0): EDID vendor "PHL", prod id 1
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1920x540"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 161 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 162 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 163 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 164 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 165 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 166 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 167 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 168 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 13c (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 14d (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 15c (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 13a (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 14b (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 15a (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        XCharSize: 0
        YCharSize: 0
        NumberOfPlanes: 0
        BitsPerPixel: 0
        NumberOfBanks: 0
        MemoryModel: 0
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 0
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 0
Mode: 107 (1280x1024)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00078cc
        BytesPerScanline: 1280
        XResolution: 1280
        YResolution: 1024
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 8
        NumberOfBanks: 1
        MemoryModel: 4
        BankSize: 0
        NumberOfImages: 50
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 1280
        BnkNumberOfImagePages: 50
        LinNumberOfImagePages: 50
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 230000000
Mode: 11a (1280x1024)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00078cc
        BytesPerScanline: 2560
        XResolution: 1280
        YResolution: 1024
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 16
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 24
        RedMaskSize: 5
        RedFieldPosition: 11
        GreenMaskSize: 6
        GreenFieldPosition: 5
        BlueMaskSize: 5
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 2560
        BnkNumberOfImagePages: 24
        LinNumberOfImagePages: 24
        LinRedMaskSize: 5
        LinRedFieldPosition: 11
        LinGreenMaskSize: 6
        LinGreenFieldPosition: 5
        LinBlueMaskSize: 5
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 230000000
*Mode: 11b (1280x1024)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00078cc
        BytesPerScanline: 5120
        XResolution: 1280
        YResolution: 1024
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 11
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 8
        RsvdFieldPosition: 24
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 5120
        BnkNumberOfImagePages: 11
        LinNumberOfImagePages: 11
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 230000000
Mode: 105 (1024x768)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00078cc
        BytesPerScanline: 1024
        XResolution: 1024
        YResolution: 768
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 8
        NumberOfBanks: 1
        MemoryModel: 4
        BankSize: 0
        NumberOfImages: 84
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 1024
        BnkNumberOfImagePages: 84
        LinNumberOfImagePages: 84
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 230000000
Mode: 117 (1024x768)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00078cc
        BytesPerScanline: 2048
        XResolution: 1024
        YResolution: 768
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 16
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 41
        RedMaskSize: 5
        RedFieldPosition: 11
        GreenMaskSize: 6
        GreenFieldPosition: 5
        BlueMaskSize: 5
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 2048
        BnkNumberOfImagePages: 41
        LinNumberOfImagePages: 41
        LinRedMaskSize: 5
        LinRedFieldPosition: 11
        LinGreenMaskSize: 6
        LinGreenFieldPosition: 5
        LinBlueMaskSize: 5
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 230000000
*Mode: 118 (1024x768)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00078cc
        BytesPerScanline: 4096
        XResolution: 1024
        YResolution: 768
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 20
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 8
        RsvdFieldPosition: 24
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 4096
        BnkNumberOfImagePages: 20
        LinNumberOfImagePages: 20
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 230000000
*Mode: 112 (640x480)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00078cc
        BytesPerScanline: 2560
        XResolution: 640
        YResolution: 480
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 52
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 8
        RsvdFieldPosition: 24
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 2560
        BnkNumberOfImagePages: 52
        LinNumberOfImagePages: 52
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 230000000
Mode: 114 (800x600)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00078cc
        BytesPerScanline: 1600
        XResolution: 800
        YResolution: 600
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 16
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 67
        RedMaskSize: 5
        RedFieldPosition: 11
        GreenMaskSize: 6
        GreenFieldPosition: 5
        BlueMaskSize: 5
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 1600
        BnkNumberOfImagePages: 67
        LinNumberOfImagePages: 67
        LinRedMaskSize: 5
        LinRedFieldPosition: 11
        LinGreenMaskSize: 6
        LinGreenFieldPosition: 5
        LinBlueMaskSize: 5
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 230000000
*Mode: 115 (800x600)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00078cc
        BytesPerScanline: 3200
        XResolution: 800
        YResolution: 600
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 33
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 8
        RsvdFieldPosition: 24
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 3200
        BnkNumberOfImagePages: 33
        LinNumberOfImagePages: 33
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 230000000
Mode: 101 (640x480)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00078cc
        BytesPerScanline: 640
        XResolution: 640
        YResolution: 480
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 8
        NumberOfBanks: 1
        MemoryModel: 4
        BankSize: 0
        NumberOfImages: 203
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 640
        BnkNumberOfImagePages: 203
        LinNumberOfImagePages: 203
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 230000000
Mode: 103 (800x600)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00078cc
        BytesPerScanline: 832
        XResolution: 800
        YResolution: 600
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 8
        NumberOfBanks: 1
        MemoryModel: 4
        BankSize: 0
        NumberOfImages: 126
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 832
        BnkNumberOfImagePages: 126
        LinNumberOfImagePages: 126
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 230000000
Mode: 111 (640x480)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc00078cc
        BytesPerScanline: 1280
        XResolution: 640
        YResolution: 480
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 16
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 101
        RedMaskSize: 5
        RedFieldPosition: 11
        GreenMaskSize: 6
        GreenFieldPosition: 5
        BlueMaskSize: 5
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 1280
        BnkNumberOfImagePages: 101
        LinNumberOfImagePages: 101
        LinRedMaskSize: 5
        LinRedFieldPosition: 11
        LinGreenMaskSize: 6
        LinGreenFieldPosition: 5
        LinBlueMaskSize: 5
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 1023 64KB banks (65472kB)
(II) VESA(0): <default monitor>: Using hsync range of 15.00-50.00 kHz
(II) VESA(0): <default monitor>: Using vrefresh range of 48.00-62.00 Hz
(II) VESA(0): <default monitor>: Using maximum pixel clock of 95.00 MHz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0): Display dimensions: (640, 360) mm
(**) VESA(0): DPI set to (40, 54)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
        compiled for 1.7.7, module version = 1.1.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.7.7, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65472 kB
(II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Desktop Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): virtual address = 0xb30c7000,
        physical address = 0xc0000000, size = 67043328
(II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(==) VESA(0): DPMS enabled
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
SELinux: Disabled on system, not enabling in X server
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/udev: Adding input device Power Button (/dev/input/event5)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
        compiled for 1.7.6.901, module version = 2.3.2
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event5"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event4)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event4"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device USB Optical Mouse (/dev/input/event0)
(**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) USB Optical Mouse: always reports core events
(**) USB Optical Mouse: Device: "/dev/input/event0"
(II) USB Optical Mouse: Found 3 mouse buttons
(II) USB Optical Mouse: Found scroll wheel(s)
(II) USB Optical Mouse: Found relative axes
(II) USB Optical Mouse: Found x and y relative axes
(II) USB Optical Mouse: Configuring as mouse
(**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
(II) USB Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event1)
(**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
(**) HID 04f3:0103: always reports core events
(**) HID 04f3:0103: Device: "/dev/input/event1"
(II) HID 04f3:0103: Found keys
(II) HID 04f3:0103: Configuring as keyboard
(II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event2)
(**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
(**) HID 04f3:0103: always reports core events
(**) HID 04f3:0103: Device: "/dev/input/event2"
(II) HID 04f3:0103: Found 1 mouse buttons
(II) HID 04f3:0103: Found scroll wheel(s)
(II) HID 04f3:0103: Found relative axes
(II) HID 04f3:0103: Found absolute axes
(II) HID 04f3:0103: Found keys
(II) HID 04f3:0103: Configuring as mouse
(II) HID 04f3:0103: Configuring as keyboard
(**) HID 04f3:0103: YAxisMapping: buttons 4 and 5
(**) HID 04f3:0103: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(EE) HID 04f3:0103: failed to initialize for relative axes.
(II) HID 04f3:0103: initialized for absolute axes.
(II) config/udev: Adding input device PC Speaker (/dev/input/event3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ACPI Virtual Keyboard Device (/dev/input/event6)
(**) ACPI Virtual Keyboard Device: Applying InputClass "evdev keyboard catchall"
(**) ACPI Virtual Keyboard Device: always reports core events
(**) ACPI Virtual Keyboard Device: Device: "/dev/input/event6"
(II) ACPI Virtual Keyboard Device: Found keys
(II) ACPI Virtual Keyboard Device: Configuring as keyboard
(II) XINPUT: Adding extended input device "ACPI Virtual Keyboard Device" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"

```

---

### Post by alfonso78 on 2012-01-07
more research... more clues...

I realized if I can force a vesa driver, I can at least use the computer while I find a better solution.

I found this page [http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html) that describes how to force vesa for installation:

> 
At the very first screen, the one with just the rectangle (it’s meant to be a keyboard) and a human figure, press any key - spacebar will do.

Then choose your language.

Then make sure you have “Try Ubuntu without any changes” selected, and then press F6

Add this to the end of the command line:

```
i915.modeset=0 xforcevesa
```

Then press enter and it should boot successfully.


---

### Post by alfonso78 on 2012-01-07
Ok, I finally can see the whole screen. I *think* I forced the usage of the VESA driver.

I edited /etc/default/grub so that GRUB_CMDLINE_LINUX_DEFAULT ends now with nomodeset.

In my case:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

then

```
sudo update-grub
```

and now I can see the normal screen.

Xorg.0.log is now as follow:

```
$ cat /var/log/Xorg.0.log
[    11.559]
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    11.559] X Protocol Version 11, Revision 0
[    11.559] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    11.559] Current Operating System: Linux NAS 3.0.0-14-generic-pae #23-Ubuntu SMP Mon Nov 21 22:07:10 UTC 2011 i686
[    11.559] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic-pae root=UUID=2f050176-99ce-49de-9826-a01fe25ecec9 ro bootdegraded=true quiet splash nomodeset vt.handoff=7
[    11.559] Build Date: 19 October 2011  05:09:41AM
[    11.559] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support)
[    11.559] Current version of pixman: 0.22.2
[    11.559]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    11.559] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.559] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan  8 02:57:39 2012
[    11.559] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.560] (==) No Layout section.  Using the first Screen section.
[    11.560] (==) No screen section available. Using defaults.
[    11.560] (**) |-->Screen "Default Screen Section" (0)
[    11.560] (**) |   |-->Monitor "<default monitor>"
[    11.560] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    11.560] (==) Automatically adding devices
[    11.560] (==) Automatically enabling devices
[    11.564] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.564]    Entry deleted from font path.
[    11.564] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    11.564]    Entry deleted from font path.
[    11.564] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    11.564]    Entry deleted from font path.
[    11.564] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    11.564]    Entry deleted from font path.
[    11.564] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    11.564]    Entry deleted from font path.
[    11.565] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[    11.565] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    11.565] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    11.565] (II) Loader magic: 0x823ada0
[    11.565] (II) Module ABI versions:
[    11.565]    X.Org ANSI C Emulation: 0.4
[    11.565]    X.Org Video Driver: 10.0
[    11.565]    X.Org XInput driver : 12.3
[    11.565]    X.Org Server Extension : 5.0
[    11.566] (--) PCI:*(0:0:2:0) 8086:0102:19da:a166 rev 9, Mem @ 0xfe000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
[    11.566] (II) Open ACPI successful (/var/run/acpid.socket)
[    11.566] (II) LoadModule: "extmod"
[    11.571] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    11.571] (II) Module extmod: vendor="X.Org Foundation"
[    11.571]    compiled for 1.10.4, module version = 1.0.0
[    11.571]    Module class: X.Org Server Extension
[    11.571]    ABI class: X.Org Server Extension, version 5.0
[    11.571] (II) Loading extension MIT-SCREEN-SAVER
[    11.571] (II) Loading extension XFree86-VidModeExtension
[    11.571] (II) Loading extension XFree86-DGA
[    11.571] (II) Loading extension DPMS
[    11.571] (II) Loading extension XVideo
[    11.571] (II) Loading extension XVideo-MotionCompensation
[    11.571] (II) Loading extension X-Resource
[    11.571] (II) LoadModule: "dbe"
[    11.571] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    11.571] (II) Module dbe: vendor="X.Org Foundation"
[    11.571]    compiled for 1.10.4, module version = 1.0.0
[    11.571]    Module class: X.Org Server Extension
[    11.571]    ABI class: X.Org Server Extension, version 5.0
[    11.571] (II) Loading extension DOUBLE-BUFFER
[    11.571] (II) LoadModule: "glx"
[    11.571] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    11.571] (II) Module glx: vendor="X.Org Foundation"
[    11.571]    compiled for 1.10.4, module version = 1.0.0
[    11.571]    ABI class: X.Org Server Extension, version 5.0
[    11.571] (==) AIGLX enabled
[    11.571] (II) Loading extension GLX
[    11.571] (II) LoadModule: "record"
[    11.572] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    11.572] (II) Module record: vendor="X.Org Foundation"
[    11.572]    compiled for 1.10.4, module version = 1.13.0
[    11.572]    Module class: X.Org Server Extension
[    11.572]    ABI class: X.Org Server Extension, version 5.0
[    11.572] (II) Loading extension RECORD
[    11.572] (II) LoadModule: "dri"
[    11.572] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    11.572] (II) Module dri: vendor="X.Org Foundation"
[    11.572]    compiled for 1.10.4, module version = 1.0.0
[    11.572]    ABI class: X.Org Server Extension, version 5.0
[    11.572] (II) Loading extension XFree86-DRI
[    11.572] (II) LoadModule: "dri2"
[    11.572] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    11.572] (II) Module dri2: vendor="X.Org Foundation"
[    11.572]    compiled for 1.10.4, module version = 1.2.0
[    11.572]    ABI class: X.Org Server Extension, version 5.0
[    11.572] (II) Loading extension DRI2
[    11.572] (==) Matched intel as autoconfigured driver 0
[    11.572] (==) Matched vesa as autoconfigured driver 1
[    11.572] (==) Matched fbdev as autoconfigured driver 2
[    11.572] (==) Assigned the driver to the xf86ConfigLayout
[    11.572] (II) LoadModule: "intel"
[    11.574] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    11.575] (II) Module intel: vendor="X.Org Foundation"
[    11.575]    compiled for 1.10.4, module version = 2.15.901
[    11.575]    Module class: X.Org Video Driver
[    11.575]    ABI class: X.Org Video Driver, version 10.0
[    11.575] (II) LoadModule: "vesa"
[    11.575] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.575] (II) Module vesa: vendor="X.Org Foundation"
[    11.575]    compiled for 1.10.2, module version = 2.3.0
[    11.575]    Module class: X.Org Video Driver
[    11.575]    ABI class: X.Org Video Driver, version 10.0
[    11.575] (II) LoadModule: "fbdev"
[    11.575] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.575] (II) Module fbdev: vendor="X.Org Foundation"
[    11.575]    compiled for 1.10.0, module version = 0.4.2
[    11.575]    ABI class: X.Org Video Driver, version 10.0
[    11.575] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
        Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
        Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
        Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
        Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    11.575] (II) VESA: driver for VESA chipsets: vesa
[    11.575] (II) FBDEV: driver for framebuffer: fbdev
[    11.575] (++) using VT number 7

[    11.577] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.577] (WW) Falling back to old probe method for fbdev
[    11.577] (II) Loading sub module "fbdevhw"
[    11.577] (II) LoadModule: "fbdevhw"
[    11.577] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    11.577] (II) Module fbdevhw: vendor="X.Org Foundation"
[    11.577]    compiled for 1.10.4, module version = 0.0.2
[    11.577]    ABI class: X.Org Video Driver, version 10.0
[    11.577] (II) Loading sub module "vbe"
[    11.577] (II) LoadModule: "vbe"
[    11.577] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    11.578] (II) Module vbe: vendor="X.Org Foundation"
[    11.578]    compiled for 1.10.4, module version = 1.1.0
[    11.578]    ABI class: X.Org Video Driver, version 10.0
[    11.578] (II) Loading sub module "int10"
[    11.578] (II) LoadModule: "int10"
[    11.578] (II) Loading /usr/lib/xorg/modules/libint10.so
[    11.579] (II) Module int10: vendor="X.Org Foundation"
[    11.579]    compiled for 1.10.4, module version = 1.0.0
[    11.579]    ABI class: X.Org Video Driver, version 10.0
[    11.579] (II) VESA(0): initializing int10
[    11.580] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    11.580] (II) VESA(0): VESA BIOS detected
[    11.580] (II) VESA(0): VESA VBE Version 3.0
[    11.580] (II) VESA(0): VESA VBE Total Mem: 65472 kB
[    11.580] (II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS
[    11.580] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    11.580] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    11.580] (II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Desktop Graphics Controller
[    11.580] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    11.588] (II) VESA(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    11.588] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    11.588] (==) VESA(0): RGB weight 888
[    11.588] (==) VESA(0): Default visual is TrueColor
[    11.588] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    11.588] (II) Loading sub module "ddc"
[    11.588] (II) LoadModule: "ddc"
[    11.588] (II) Module "ddc" already built-in
[    11.589] (II) VESA(0): VESA VBE DDC supported
[    11.589] (II) VESA(0): VESA VBE DDC Level 2
[    11.589] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    11.601] (II) VESA(0): VESA VBE DDC read successfully
[    11.601] (II) VESA(0): Manufacturer: PHL  Model: 1  Serial#: 16843009
[    11.601] (II) VESA(0): Year: 2006  Week: 1
[    11.601] (II) VESA(0): EDID Version: 1.3
[    11.601] (II) VESA(0): Digital Display Input
[    11.601] (II) VESA(0): Max Image Size [cm]: horiz.: 64  vert.: 36
[    11.601] (II) VESA(0): Gamma: 2.20
[    11.601] (II) VESA(0): No DPMS capabilities specified
[    11.601] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[    11.601] (II) VESA(0): First detailed timing is preferred mode
[    11.601] (II) VESA(0): redX: 0.640 redY: 0.330   greenX: 0.290 greenY: 0.600
[    11.601] (II) VESA(0): blueX: 0.150 blueY: 0.060   whiteX: 0.289 whiteY: 0.299
[    11.601] (II) VESA(0): Supported established timings:
[    11.601] (II) VESA(0): 640x480@60Hz
[    11.601] (II) VESA(0): 800x600@60Hz
[    11.601] (II) VESA(0): 1024x768@60Hz
[    11.601] (II) VESA(0): Manufacturer's mask: 0
[    11.601] (II) VESA(0): Supported detailed timing:
[    11.601] (II) VESA(0): clock: 74.2 MHz   Image Size:  640 x 360 mm
[    11.601] (II) VESA(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    11.601] (II) VESA(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    11.601] (II) VESA(0): Supported detailed timing:
[    11.601] (II) VESA(0): clock: 65.0 MHz   Image Size:  400 x 300 mm
[    11.601] (II) VESA(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[    11.601] (II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[    11.601] (II) VESA(0): Monitor name: Philips FTV
[    11.601] (II) VESA(0): Ranges: V min: 48 V max: 62 Hz, H min: 15 H max: 50 kHz, PixClock max 95 MHz
[    11.601] (II) VESA(0): Number of EDID sections to follow: 1
[    11.601] (II) VESA(0): EDID (in hex):
[    11.601] (II) VESA(0):      00ffffffffffff00410c010001010101
[    11.601] (II) VESA(0):      01100103804024780ae692a3544a9926
[    11.601] (II) VESA(0):      0f4a4c21080001010101010101010101
[    11.601] (II) VESA(0):      010101010101011d80d0721c1620102c
[    11.601] (II) VESA(0):      258080682100009e6419004041002630
[    11.601] (II) VESA(0):      18883600902c11000018000000fc0050
[    11.601] (II) VESA(0):      68696c697073204654560a20000000fd
[    11.601] (II) VESA(0):      00303e0f3209000a202020202020018b
[    11.601] (II) VESA(0): EDID vendor "PHL", prod id 1
[    11.601] (II) VESA(0): Using EDID range info for horizontal sync
[    11.601] (II) VESA(0): Using EDID range info for vertical refresh
[    11.601] (II) VESA(0): Printing DDC gathered Modelines:
[    11.601] (II) VESA(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    11.601] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    11.601] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    11.601] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    11.601] (II) VESA(0): Searching for matching VESA mode(s):
[    11.602] Mode: 160 (0x0)
[    11.602]    ModeAttributes: 0x0
[    11.602]    WinAAttributes: 0x0
[    11.602]    WinBAttributes: 0x0
[    11.602]    WinGranularity: 0
[    11.602]    WinSize: 0
[    11.602]    WinASegment: 0x0
[    11.602]    WinBSegment: 0x0
[    11.602]    WinFuncPtr: 0x0
[    11.602]    BytesPerScanline: 0
[    11.602]    XResolution: 0
[    11.602]    YResolution: 0
[    11.602]    XCharSize: 0
[    11.602]    YCharSize: 0
[    11.602]    NumberOfPlanes: 0
[    11.602]    BitsPerPixel: 0
[    11.602]    NumberOfBanks: 0
[    11.602]    MemoryModel: 0
[    11.602]    BankSize: 0
[    11.602]    NumberOfImages: 0
[    11.602]    RedMaskSize: 0
[    11.602]    RedFieldPosition: 0
[    11.602]    GreenMaskSize: 0
[    11.602]    GreenFieldPosition: 0
[    11.602]    BlueMaskSize: 0
[    11.602]    BlueFieldPosition: 0
[    11.602]    RsvdMaskSize: 0
[    11.602]    RsvdFieldPosition: 0
[    11.602]    DirectColorModeInfo: 0
[    11.602]    PhysBasePtr: 0x0
[    11.602]    LinBytesPerScanLine: 0
[    11.602]    BnkNumberOfImagePages: 0
[    11.602]    LinNumberOfImagePages: 0
[    11.602]    LinRedMaskSize: 0
[    11.602]    LinRedFieldPosition: 0
[    11.602]    LinGreenMaskSize: 0
[    11.602]    LinGreenFieldPosition: 0
[    11.602]    LinBlueMaskSize: 0
[    11.602]    LinBlueFieldPosition: 0
[    11.602]    LinRsvdMaskSize: 0
[    11.602]    LinRsvdFieldPosition: 0
[    11.602]    MaxPixelClock: 0
[    11.602] Mode: 161 (0x0)
[    11.602]    ModeAttributes: 0x0
[    11.602]    WinAAttributes: 0x0
[    11.602]    WinBAttributes: 0x0
[    11.602]    WinGranularity: 0
[    11.602]    WinSize: 0
[    11.602]    WinASegment: 0x0
[    11.602]    WinBSegment: 0x0
[    11.602]    WinFuncPtr: 0x0
[    11.602]    BytesPerScanline: 0
[    11.602]    XResolution: 0
[    11.602]    YResolution: 0
[    11.602]    XCharSize: 0
[    11.602]    YCharSize: 0
[    11.602]    NumberOfPlanes: 0
[    11.602]    BitsPerPixel: 0
[    11.602]    NumberOfBanks: 0
[    11.602]    MemoryModel: 0
[    11.602]    BankSize: 0
[    11.602]    NumberOfImages: 0
[    11.602]    RedMaskSize: 0
[    11.602]    RedFieldPosition: 0
[    11.602]    GreenMaskSize: 0
[    11.602]    GreenFieldPosition: 0
[    11.602]    BlueMaskSize: 0
[    11.602]    BlueFieldPosition: 0
[    11.602]    RsvdMaskSize: 0
[    11.602]    RsvdFieldPosition: 0
[    11.602]    DirectColorModeInfo: 0
[    11.602]    PhysBasePtr: 0x0
[    11.602]    LinBytesPerScanLine: 0
[    11.602]    BnkNumberOfImagePages: 0
[    11.602]    LinNumberOfImagePages: 0
[    11.602]    LinRedMaskSize: 0
[    11.602]    LinRedFieldPosition: 0
[    11.602]    LinGreenMaskSize: 0
[    11.602]    LinGreenFieldPosition: 0
[    11.602]    LinBlueMaskSize: 0
[    11.602]    LinBlueFieldPosition: 0
[    11.602]    LinRsvdMaskSize: 0
[    11.602]    LinRsvdFieldPosition: 0
[    11.602]    MaxPixelClock: 0
[    11.602] Mode: 162 (0x0)
[    11.602]    ModeAttributes: 0x0
[    11.602]    WinAAttributes: 0x0
[    11.602]    WinBAttributes: 0x0
[    11.602]    WinGranularity: 0
[    11.602]    WinSize: 0
[    11.602]    WinASegment: 0x0
[    11.603]    WinBSegment: 0x0
[    11.603]    WinFuncPtr: 0x0
[    11.603]    BytesPerScanline: 0
[    11.603]    XResolution: 0
[    11.603]    YResolution: 0
[    11.603]    XCharSize: 0
[    11.603]    YCharSize: 0
[    11.603]    NumberOfPlanes: 0
[    11.603]    BitsPerPixel: 0
[    11.603]    NumberOfBanks: 0
[    11.603]    MemoryModel: 0
[    11.603]    BankSize: 0
[    11.603]    NumberOfImages: 0
[    11.603]    RedMaskSize: 0
[    11.603]    RedFieldPosition: 0
[    11.603]    GreenMaskSize: 0
[    11.603]    GreenFieldPosition: 0
[    11.603]    BlueMaskSize: 0
[    11.603]    BlueFieldPosition: 0
[    11.603]    RsvdMaskSize: 0
[    11.603]    RsvdFieldPosition: 0
[    11.603]    DirectColorModeInfo: 0
[    11.603]    PhysBasePtr: 0x0
[    11.603]    LinBytesPerScanLine: 0
[    11.603]    BnkNumberOfImagePages: 0
[    11.603]    LinNumberOfImagePages: 0
[    11.603]    LinRedMaskSize: 0
[    11.603]    LinRedFieldPosition: 0
[    11.603]    LinGreenMaskSize: 0
[    11.603]    LinGreenFieldPosition: 0
[    11.603]    LinBlueMaskSize: 0
[    11.603]    LinBlueFieldPosition: 0
[    11.603]    LinRsvdMaskSize: 0
[    11.603]    LinRsvdFieldPosition: 0
[    11.603]    MaxPixelClock: 0
[    11.603] Mode: 163 (0x0)
[    11.603]    ModeAttributes: 0x0
[    11.603]    WinAAttributes: 0x0
[    11.603]    WinBAttributes: 0x0
[    11.603]    WinGranularity: 0
[    11.603]    WinSize: 0
[    11.603]    WinASegment: 0x0
[    11.603]    WinBSegment: 0x0
[    11.603]    WinFuncPtr: 0x0
[    11.603]    BytesPerScanline: 0
[    11.603]    XResolution: 0
[    11.603]    YResolution: 0
[    11.603]    XCharSize: 0
[    11.603]    YCharSize: 0
[    11.603]    NumberOfPlanes: 0
[    11.603]    BitsPerPixel: 0
[    11.603]    NumberOfBanks: 0
[    11.603]    MemoryModel: 0
[    11.603]    BankSize: 0
[    11.603]    NumberOfImages: 0
[    11.603]    RedMaskSize: 0
[    11.603]    RedFieldPosition: 0
[    11.603]    GreenMaskSize: 0
[    11.603]    GreenFieldPosition: 0
[    11.603]    BlueMaskSize: 0
[    11.603]    BlueFieldPosition: 0
[    11.603]    RsvdMaskSize: 0
[    11.603]    RsvdFieldPosition: 0
[    11.603]    DirectColorModeInfo: 0
[    11.603]    PhysBasePtr: 0x0
[    11.603]    LinBytesPerScanLine: 0
[    11.603]    BnkNumberOfImagePages: 0
[    11.603]    LinNumberOfImagePages: 0
[    11.603]    LinRedMaskSize: 0
[    11.603]    LinRedFieldPosition: 0
[    11.603]    LinGreenMaskSize: 0
[    11.603]    LinGreenFieldPosition: 0
[    11.603]    LinBlueMaskSize: 0
[    11.603]    LinBlueFieldPosition: 0
[    11.603]    LinRsvdMaskSize: 0
[    11.603]    LinRsvdFieldPosition: 0
[    11.603]    MaxPixelClock: 0
[    11.603] Mode: 164 (0x0)
[    11.603]    ModeAttributes: 0x0
[    11.603]    WinAAttributes: 0x0
[    11.603]    WinBAttributes: 0x0
[    11.603]    WinGranularity: 0
[    11.603]    WinSize: 0
[    11.603]    WinASegment: 0x0
[    11.603]    WinBSegment: 0x0
[    11.603]    WinFuncPtr: 0x0
[    11.603]    BytesPerScanline: 0
[    11.603]    XResolution: 0
[    11.603]    YResolution: 0
[    11.603]    XCharSize: 0
[    11.603]    YCharSize: 0
[    11.603]    NumberOfPlanes: 0
[    11.603]    BitsPerPixel: 0
[    11.603]    NumberOfBanks: 0
[    11.603]    MemoryModel: 0
[    11.603]    BankSize: 0
[    11.603]    NumberOfImages: 0
[    11.603]    RedMaskSize: 0
[    11.603]    RedFieldPosition: 0
[    11.603]    GreenMaskSize: 0
[    11.603]    GreenFieldPosition: 0
[    11.603]    BlueMaskSize: 0
[    11.603]    BlueFieldPosition: 0
[    11.603]    RsvdMaskSize: 0
[    11.603]    RsvdFieldPosition: 0
[    11.603]    DirectColorModeInfo: 0
[    11.603]    PhysBasePtr: 0x0
[    11.603]    LinBytesPerScanLine: 0
[    11.603]    BnkNumberOfImagePages: 0
[    11.603]    LinNumberOfImagePages: 0
[    11.603]    LinRedMaskSize: 0
[    11.603]    LinRedFieldPosition: 0
[    11.603]    LinGreenMaskSize: 0
[    11.603]    LinGreenFieldPosition: 0
[    11.603]    LinBlueMaskSize: 0
[    11.603]    LinBlueFieldPosition: 0
[    11.603]    LinRsvdMaskSize: 0
[    11.604]    LinRsvdFieldPosition: 0
[    11.604]    MaxPixelClock: 0
[    11.604] Mode: 165 (0x0)
[    11.604]    ModeAttributes: 0x0
[    11.604]    WinAAttributes: 0x0
[    11.604]    WinBAttributes: 0x0
[    11.604]    WinGranularity: 0
[    11.604]    WinSize: 0
[    11.604]    WinASegment: 0x0
[    11.604]    WinBSegment: 0x0
[    11.604]    WinFuncPtr: 0x0
[    11.604]    BytesPerScanline: 0
[    11.604]    XResolution: 0
[    11.604]    YResolution: 0
[    11.604]    XCharSize: 0
[    11.604]    YCharSize: 0
[    11.604]    NumberOfPlanes: 0
[    11.604]    BitsPerPixel: 0
[    11.604]    NumberOfBanks: 0
[    11.604]    MemoryModel: 0
[    11.604]    BankSize: 0
[    11.604]    NumberOfImages: 0
[    11.604]    RedMaskSize: 0
[    11.604]    RedFieldPosition: 0
[    11.604]    GreenMaskSize: 0
[    11.604]    GreenFieldPosition: 0
[    11.604]    BlueMaskSize: 0
[    11.604]    BlueFieldPosition: 0
[    11.604]    RsvdMaskSize: 0
[    11.604]    RsvdFieldPosition: 0
[    11.604]    DirectColorModeInfo: 0
[    11.604]    PhysBasePtr: 0x0
[    11.604]    LinBytesPerScanLine: 0
[    11.604]    BnkNumberOfImagePages: 0
[    11.604]    LinNumberOfImagePages: 0
[    11.604]    LinRedMaskSize: 0
[    11.604]    LinRedFieldPosition: 0
[    11.604]    LinGreenMaskSize: 0
[    11.604]    LinGreenFieldPosition: 0
[    11.604]    LinBlueMaskSize: 0
[    11.604]    LinBlueFieldPosition: 0
[    11.604]    LinRsvdMaskSize: 0
[    11.604]    LinRsvdFieldPosition: 0
[    11.604]    MaxPixelClock: 0
[    11.604] Mode: 166 (0x0)
[    11.604]    ModeAttributes: 0x0
[    11.604]    WinAAttributes: 0x0
[    11.604]    WinBAttributes: 0x0
[    11.604]    WinGranularity: 0
[    11.604]    WinSize: 0
[    11.604]    WinASegment: 0x0
[    11.604]    WinBSegment: 0x0
[    11.604]    WinFuncPtr: 0x0
[    11.604]    BytesPerScanline: 0
[    11.604]    XResolution: 0
[    11.604]    YResolution: 0
[    11.604]    XCharSize: 0
[    11.604]    YCharSize: 0
[    11.604]    NumberOfPlanes: 0
[    11.604]    BitsPerPixel: 0
[    11.604]    NumberOfBanks: 0
[    11.604]    MemoryModel: 0
[    11.604]    BankSize: 0
[    11.604]    NumberOfImages: 0
[    11.604]    RedMaskSize: 0
[    11.604]    RedFieldPosition: 0
[    11.604]    GreenMaskSize: 0
[    11.604]    GreenFieldPosition: 0
[    11.604]    BlueMaskSize: 0
[    11.604]    BlueFieldPosition: 0
[    11.604]    RsvdMaskSize: 0
[    11.604]    RsvdFieldPosition: 0
[    11.604]    DirectColorModeInfo: 0
[    11.604]    PhysBasePtr: 0x0
[    11.604]    LinBytesPerScanLine: 0
[    11.604]    BnkNumberOfImagePages: 0
[    11.604]    LinNumberOfImagePages: 0
[    11.604]    LinRedMaskSize: 0
[    11.604]    LinRedFieldPosition: 0
[    11.604]    LinGreenMaskSize: 0
[    11.604]    LinGreenFieldPosition: 0
[    11.604]    LinBlueMaskSize: 0
[    11.604]    LinBlueFieldPosition: 0
[    11.604]    LinRsvdMaskSize: 0
[    11.604]    LinRsvdFieldPosition: 0
[    11.604]    MaxPixelClock: 0
[    11.605] Mode: 167 (0x0)
[    11.605]    ModeAttributes: 0x0
[    11.605]    WinAAttributes: 0x0
[    11.605]    WinBAttributes: 0x0
[    11.605]    WinGranularity: 0
[    11.605]    WinSize: 0
[    11.605]    WinASegment: 0x0
[    11.605]    WinBSegment: 0x0
[    11.605]    WinFuncPtr: 0x0
[    11.605]    BytesPerScanline: 0
[    11.605]    XResolution: 0
[    11.605]    YResolution: 0
[    11.605]    XCharSize: 0
[    11.605]    YCharSize: 0
[    11.605]    NumberOfPlanes: 0
[    11.605]    BitsPerPixel: 0
[    11.605]    NumberOfBanks: 0
[    11.605]    MemoryModel: 0
[    11.605]    BankSize: 0
[    11.605]    NumberOfImages: 0
[    11.605]    RedMaskSize: 0
[    11.605]    RedFieldPosition: 0
[    11.605]    GreenMaskSize: 0
[    11.605]    GreenFieldPosition: 0
[    11.605]    BlueMaskSize: 0
[    11.605]    BlueFieldPosition: 0
[    11.605]    RsvdMaskSize: 0
[    11.605]    RsvdFieldPosition: 0
[    11.605]    DirectColorModeInfo: 0
[    11.605]    PhysBasePtr: 0x0
[    11.605]    LinBytesPerScanLine: 0
[    11.605]    BnkNumberOfImagePages: 0
[    11.605]    LinNumberOfImagePages: 0
[    11.605]    LinRedMaskSize: 0
[    11.605]    LinRedFieldPosition: 0
[    11.605]    LinGreenMaskSize: 0
[    11.605]    LinGreenFieldPosition: 0
[    11.605]    LinBlueMaskSize: 0
[    11.605]    LinBlueFieldPosition: 0
[    11.605]    LinRsvdMaskSize: 0
[    11.605]    LinRsvdFieldPosition: 0
[    11.605]    MaxPixelClock: 0
[    11.605] Mode: 168 (0x0)
[    11.605]    ModeAttributes: 0x0
[    11.605]    WinAAttributes: 0x0
[    11.605]    WinBAttributes: 0x0
[    11.605]    WinGranularity: 0
[    11.605]    WinSize: 0
[    11.605]    WinASegment: 0x0
[    11.605]    WinBSegment: 0x0
[    11.605]    WinFuncPtr: 0x0
[    11.605]    BytesPerScanline: 0
[    11.605]    XResolution: 0
[    11.605]    YResolution: 0
[    11.605]    XCharSize: 0
[    11.605]    YCharSize: 0
[    11.605]    NumberOfPlanes: 0
[    11.605]    BitsPerPixel: 0
[    11.605]    NumberOfBanks: 0
[    11.605]    MemoryModel: 0
[    11.605]    BankSize: 0
[    11.605]    NumberOfImages: 0
[    11.606]    RedMaskSize: 0
[    11.606]    RedFieldPosition: 0
[    11.606]    GreenMaskSize: 0
[    11.606]    GreenFieldPosition: 0
[    11.606]    BlueMaskSize: 0
[    11.606]    BlueFieldPosition: 0
[    11.606]    RsvdMaskSize: 0
[    11.606]    RsvdFieldPosition: 0
[    11.606]    DirectColorModeInfo: 0
[    11.606]    PhysBasePtr: 0x0
[    11.606]    LinBytesPerScanLine: 0
[    11.606]    BnkNumberOfImagePages: 0
[    11.606]    LinNumberOfImagePages: 0
[    11.606]    LinRedMaskSize: 0
[    11.606]    LinRedFieldPosition: 0
[    11.606]    LinGreenMaskSize: 0
[    11.606]    LinGreenFieldPosition: 0
[    11.606]    LinBlueMaskSize: 0
[    11.606]    LinBlueFieldPosition: 0
[    11.606]    LinRsvdMaskSize: 0
[    11.606]    LinRsvdFieldPosition: 0
[    11.606]    MaxPixelClock: 0
[    11.606] Mode: 13c (0x0)
[    11.606]    ModeAttributes: 0x0
[    11.606]    WinAAttributes: 0x0
[    11.606]    WinBAttributes: 0x0
[    11.606]    WinGranularity: 0
[    11.606]    WinSize: 0
[    11.606]    WinASegment: 0x0
[    11.606]    WinBSegment: 0x0
[    11.606]    WinFuncPtr: 0x0
[    11.606]    BytesPerScanline: 0
[    11.606]    XResolution: 0
[    11.606]    YResolution: 0
[    11.606]    XCharSize: 0
[    11.606]    YCharSize: 0
[    11.606]    NumberOfPlanes: 0
[    11.606]    BitsPerPixel: 0
[    11.606]    NumberOfBanks: 0
[    11.606]    MemoryModel: 0
[    11.606]    BankSize: 0
[    11.606]    NumberOfImages: 0
[    11.606]    RedMaskSize: 0
[    11.606]    RedFieldPosition: 0
[    11.606]    GreenMaskSize: 0
[    11.606]    GreenFieldPosition: 0
[    11.606]    BlueMaskSize: 0
[    11.606]    BlueFieldPosition: 0
[    11.606]    RsvdMaskSize: 0
[    11.606]    RsvdFieldPosition: 0
[    11.606]    DirectColorModeInfo: 0
[    11.606]    PhysBasePtr: 0x0
[    11.606]    LinBytesPerScanLine: 0
[    11.606]    BnkNumberOfImagePages: 0
[    11.606]    LinNumberOfImagePages: 0
[    11.606]    LinRedMaskSize: 0
[    11.606]    LinRedFieldPosition: 0
[    11.606]    LinGreenMaskSize: 0
[    11.606]    LinGreenFieldPosition: 0
[    11.606]    LinBlueMaskSize: 0
[    11.606]    LinBlueFieldPosition: 0
[    11.606]    LinRsvdMaskSize: 0
[    11.606]    LinRsvdFieldPosition: 0
[    11.606]    MaxPixelClock: 0
[    11.607] Mode: 14d (0x0)
[    11.607]    ModeAttributes: 0x0
[    11.607]    WinAAttributes: 0x0
[    11.607]    WinBAttributes: 0x0
[    11.607]    WinGranularity: 0
[    11.607]    WinSize: 0
[    11.607]    WinASegment: 0x0
[    11.607]    WinBSegment: 0x0
[    11.607]    WinFuncPtr: 0x0
[    11.607]    BytesPerScanline: 0
[    11.607]    XResolution: 0
[    11.607]    YResolution: 0
[    11.607]    XCharSize: 0
[    11.607]    YCharSize: 0
[    11.607]    NumberOfPlanes: 0
[    11.607]    BitsPerPixel: 0
[    11.607]    NumberOfBanks: 0
[    11.607]    MemoryModel: 0
[    11.607]    BankSize: 0
[    11.607]    NumberOfImages: 0
[    11.607]    RedMaskSize: 0
[    11.607]    RedFieldPosition: 0
[    11.607]    GreenMaskSize: 0
[    11.607]    GreenFieldPosition: 0
[    11.607]    BlueMaskSize: 0
[    11.607]    BlueFieldPosition: 0
[    11.607]    RsvdMaskSize: 0
[    11.607]    RsvdFieldPosition: 0
[    11.607]    DirectColorModeInfo: 0
[    11.607]    PhysBasePtr: 0x0
[    11.607]    LinBytesPerScanLine: 0
[    11.607]    BnkNumberOfImagePages: 0
[    11.607]    LinNumberOfImagePages: 0
[    11.607]    LinRedMaskSize: 0
[    11.607]    LinRedFieldPosition: 0
[    11.607]    LinGreenMaskSize: 0
[    11.607]    LinGreenFieldPosition: 0
[    11.607]    LinBlueMaskSize: 0
[    11.607]    LinBlueFieldPosition: 0
[    11.607]    LinRsvdMaskSize: 0
[    11.607]    LinRsvdFieldPosition: 0
[    11.607]    MaxPixelClock: 0
[    11.607] Mode: 15c (0x0)
[    11.607]    ModeAttributes: 0x0
[    11.607]    WinAAttributes: 0x0
[    11.607]    WinBAttributes: 0x0
[    11.607]    WinGranularity: 0
[    11.607]    WinSize: 0
[    11.607]    WinASegment: 0x0
[    11.607]    WinBSegment: 0x0
[    11.607]    WinFuncPtr: 0x0
[    11.607]    BytesPerScanline: 0
[    11.607]    XResolution: 0
[    11.607]    YResolution: 0
[    11.607]    XCharSize: 0
[    11.607]    YCharSize: 0
[    11.607]    NumberOfPlanes: 0
[    11.607]    BitsPerPixel: 0
[    11.607]    NumberOfBanks: 0
[    11.607]    MemoryModel: 0
[    11.607]    BankSize: 0
[    11.607]    NumberOfImages: 0
[    11.608]    RedMaskSize: 0
[    11.608]    RedFieldPosition: 0
[    11.608]    GreenMaskSize: 0
[    11.608]    GreenFieldPosition: 0
[    11.608]    BlueMaskSize: 0
[    11.608]    BlueFieldPosition: 0
[    11.608]    RsvdMaskSize: 0
[    11.608]    RsvdFieldPosition: 0
[    11.608]    DirectColorModeInfo: 0
[    11.608]    PhysBasePtr: 0x0
[    11.608]    LinBytesPerScanLine: 0
[    11.608]    BnkNumberOfImagePages: 0
[    11.608]    LinNumberOfImagePages: 0
[    11.608]    LinRedMaskSize: 0
[    11.608]    LinRedFieldPosition: 0
[    11.608]    LinGreenMaskSize: 0
[    11.608]    LinGreenFieldPosition: 0
[    11.608]    LinBlueMaskSize: 0
[    11.608]    LinBlueFieldPosition: 0
[    11.608]    LinRsvdMaskSize: 0
[    11.608]    LinRsvdFieldPosition: 0
[    11.608]    MaxPixelClock: 0
[    11.608] Mode: 13a (0x0)
[    11.608]    ModeAttributes: 0x0
[    11.608]    WinAAttributes: 0x0
[    11.608]    WinBAttributes: 0x0
[    11.608]    WinGranularity: 0
[    11.608]    WinSize: 0
[    11.608]    WinASegment: 0x0
[    11.608]    WinBSegment: 0x0
[    11.608]    WinFuncPtr: 0x0
[    11.608]    BytesPerScanline: 0
[    11.608]    XResolution: 0
[    11.608]    YResolution: 0
[    11.608]    XCharSize: 0
[    11.608]    YCharSize: 0
[    11.608]    NumberOfPlanes: 0
[    11.608]    BitsPerPixel: 0
[    11.608]    NumberOfBanks: 0
[    11.608]    MemoryModel: 0
[    11.608]    BankSize: 0
[    11.608]    NumberOfImages: 0
[    11.608]    RedMaskSize: 0
[    11.608]    RedFieldPosition: 0
[    11.608]    GreenMaskSize: 0
[    11.608]    GreenFieldPosition: 0
[    11.608]    BlueMaskSize: 0
[    11.608]    BlueFieldPosition: 0
[    11.608]    RsvdMaskSize: 0
[    11.608]    RsvdFieldPosition: 0
[    11.608]    DirectColorModeInfo: 0
[    11.608]    PhysBasePtr: 0x0
[    11.608]    LinBytesPerScanLine: 0
[    11.608]    BnkNumberOfImagePages: 0
[    11.608]    LinNumberOfImagePages: 0
[    11.608]    LinRedMaskSize: 0
[    11.608]    LinRedFieldPosition: 0
[    11.608]    LinGreenMaskSize: 0
[    11.608]    LinGreenFieldPosition: 0
[    11.608]    LinBlueMaskSize: 0
[    11.608]    LinBlueFieldPosition: 0
[    11.608]    LinRsvdMaskSize: 0
[    11.608]    LinRsvdFieldPosition: 0
[    11.608]    MaxPixelClock: 0
[    11.608] Mode: 14b (0x0)
[    11.608]    ModeAttributes: 0x0
[    11.608]    WinAAttributes: 0x0
[    11.608]    WinBAttributes: 0x0
[    11.608]    WinGranularity: 0
[    11.608]    WinSize: 0
[    11.608]    WinASegment: 0x0
[    11.608]    WinBSegment: 0x0
[    11.608]    WinFuncPtr: 0x0
[    11.608]    BytesPerScanline: 0
[    11.608]    XResolution: 0
[    11.608]    YResolution: 0
[    11.608]    XCharSize: 0
[    11.608]    YCharSize: 0
[    11.608]    NumberOfPlanes: 0
[    11.608]    BitsPerPixel: 0
[    11.608]    NumberOfBanks: 0
[    11.608]    MemoryModel: 0
[    11.608]    BankSize: 0
[    11.608]    NumberOfImages: 0
[    11.608]    RedMaskSize: 0
[    11.608]    RedFieldPosition: 0
[    11.608]    GreenMaskSize: 0
[    11.608]    GreenFieldPosition: 0
[    11.608]    BlueMaskSize: 0
[    11.608]    BlueFieldPosition: 0
[    11.608]    RsvdMaskSize: 0
[    11.608]    RsvdFieldPosition: 0
[    11.608]    DirectColorModeInfo: 0
[    11.608]    PhysBasePtr: 0x0
[    11.608]    LinBytesPerScanLine: 0
[    11.608]    BnkNumberOfImagePages: 0
[    11.608]    LinNumberOfImagePages: 0
[    11.609]    LinRedMaskSize: 0
[    11.609]    LinRedFieldPosition: 0
[    11.609]    LinGreenMaskSize: 0
[    11.609]    LinGreenFieldPosition: 0
[    11.609]    LinBlueMaskSize: 0
[    11.609]    LinBlueFieldPosition: 0
[    11.609]    LinRsvdMaskSize: 0
[    11.609]    LinRsvdFieldPosition: 0
[    11.609]    MaxPixelClock: 0
[    11.609] Mode: 15a (0x0)
[    11.609]    ModeAttributes: 0x0
[    11.609]    WinAAttributes: 0x0
[    11.609]    WinBAttributes: 0x0
[    11.609]    WinGranularity: 0
[    11.609]    WinSize: 0
[    11.609]    WinASegment: 0x0
[    11.609]    WinBSegment: 0x0
[    11.609]    WinFuncPtr: 0x0
[    11.609]    BytesPerScanline: 0
[    11.609]    XResolution: 0
[    11.609]    YResolution: 0
[    11.609]    XCharSize: 0
[    11.609]    YCharSize: 0
[    11.609]    NumberOfPlanes: 0
[    11.609]    BitsPerPixel: 0
[    11.609]    NumberOfBanks: 0
[    11.609]    MemoryModel: 0
[    11.609]    BankSize: 0
[    11.609]    NumberOfImages: 0
[    11.609]    RedMaskSize: 0
[    11.609]    RedFieldPosition: 0
[    11.609]    GreenMaskSize: 0
[    11.609]    GreenFieldPosition: 0
[    11.609]    BlueMaskSize: 0
[    11.609]    BlueFieldPosition: 0
[    11.609]    RsvdMaskSize: 0
[    11.609]    RsvdFieldPosition: 0
[    11.609]    DirectColorModeInfo: 0
[    11.609]    PhysBasePtr: 0x0
[    11.609]    LinBytesPerScanLine: 0
[    11.609]    BnkNumberOfImagePages: 0
[    11.609]    LinNumberOfImagePages: 0
[    11.609]    LinRedMaskSize: 0
[    11.609]    LinRedFieldPosition: 0
[    11.609]    LinGreenMaskSize: 0
[    11.609]    LinGreenFieldPosition: 0
[    11.609]    LinBlueMaskSize: 0
[    11.609]    LinBlueFieldPosition: 0
[    11.609]    LinRsvdMaskSize: 0
[    11.609]    LinRsvdFieldPosition: 0
[    11.609]    MaxPixelClock: 0
[    11.609] Mode: 107 (1280x1024)
[    11.609]    ModeAttributes: 0x9b
[    11.609]    WinAAttributes: 0x7
[    11.609]    WinBAttributes: 0x0
[    11.609]    WinGranularity: 64
[    11.609]    WinSize: 64
[    11.609]    WinASegment: 0xa000
[    11.609]    WinBSegment: 0x0
[    11.610]    WinFuncPtr: 0xc00078cc
[    11.610]    BytesPerScanline: 1280
[    11.610]    XResolution: 1280
[    11.610]    YResolution: 1024
[    11.610]    XCharSize: 8
[    11.610]    YCharSize: 16
[    11.610]    NumberOfPlanes: 1
[    11.610]    BitsPerPixel: 8
[    11.610]    NumberOfBanks: 1
[    11.610]    MemoryModel: 4
[    11.610]    BankSize: 0
[    11.610]    NumberOfImages: 50
[    11.610]    RedMaskSize: 0
[    11.610]    RedFieldPosition: 0
[    11.610]    GreenMaskSize: 0
[    11.610]    GreenFieldPosition: 0
[    11.610]    BlueMaskSize: 0
[    11.610]    BlueFieldPosition: 0
[    11.610]    RsvdMaskSize: 0
[    11.610]    RsvdFieldPosition: 0
[    11.610]    DirectColorModeInfo: 0
[    11.610]    PhysBasePtr: 0xc0000000
[    11.610]    LinBytesPerScanLine: 1280
[    11.610]    BnkNumberOfImagePages: 50
[    11.610]    LinNumberOfImagePages: 50
[    11.610]    LinRedMaskSize: 0
[    11.610]    LinRedFieldPosition: 0
[    11.610]    LinGreenMaskSize: 0
[    11.610]    LinGreenFieldPosition: 0
[    11.610]    LinBlueMaskSize: 0
[    11.610]    LinBlueFieldPosition: 0
[    11.610]    LinRsvdMaskSize: 0
[    11.610]    LinRsvdFieldPosition: 0
[    11.610]    MaxPixelClock: 230000000
[    11.610] Mode: 11a (1280x1024)
[    11.610]    ModeAttributes: 0x9b
[    11.610]    WinAAttributes: 0x7
[    11.610]    WinBAttributes: 0x0
[    11.610]    WinGranularity: 64
[    11.610]    WinSize: 64
[    11.610]    WinASegment: 0xa000
[    11.610]    WinBSegment: 0x0
[    11.610]    WinFuncPtr: 0xc00078cc
[    11.610]    BytesPerScanline: 2560
[    11.610]    XResolution: 1280
[    11.610]    YResolution: 1024
[    11.610]    XCharSize: 8
[    11.610]    YCharSize: 16
[    11.610]    NumberOfPlanes: 1
[    11.610]    BitsPerPixel: 16
[    11.610]    NumberOfBanks: 1
[    11.610]    MemoryModel: 6
[    11.610]    BankSize: 0
[    11.610]    NumberOfImages: 24
[    11.610]    RedMaskSize: 5
[    11.610]    RedFieldPosition: 11
[    11.610]    GreenMaskSize: 6
[    11.610]    GreenFieldPosition: 5
[    11.610]    BlueMaskSize: 5
[    11.610]    BlueFieldPosition: 0
[    11.610]    RsvdMaskSize: 0
[    11.610]    RsvdFieldPosition: 0
[    11.610]    DirectColorModeInfo: 0
[    11.610]    PhysBasePtr: 0xc0000000
[    11.610]    LinBytesPerScanLine: 2560
[    11.610]    BnkNumberOfImagePages: 24
[    11.610]    LinNumberOfImagePages: 24
[    11.610]    LinRedMaskSize: 5
[    11.610]    LinRedFieldPosition: 11
[    11.610]    LinGreenMaskSize: 6
[    11.610]    LinGreenFieldPosition: 5
[    11.610]    LinBlueMaskSize: 5
[    11.610]    LinBlueFieldPosition: 0
[    11.610]    LinRsvdMaskSize: 0
[    11.610]    LinRsvdFieldPosition: 0
[    11.610]    MaxPixelClock: 230000000
[    11.611] *Mode: 11b (1280x1024)
[    11.611]    ModeAttributes: 0x9b
[    11.611]    WinAAttributes: 0x7
[    11.611]    WinBAttributes: 0x0
[    11.611]    WinGranularity: 64
[    11.611]    WinSize: 64
[    11.611]    WinASegment: 0xa000
[    11.611]    WinBSegment: 0x0
[    11.611]    WinFuncPtr: 0xc00078cc
[    11.611]    BytesPerScanline: 5120
[    11.611]    XResolution: 1280
[    11.611]    YResolution: 1024
[    11.611]    XCharSize: 8
[    11.611]    YCharSize: 16
[    11.611]    NumberOfPlanes: 1
[    11.611]    BitsPerPixel: 32
[    11.611]    NumberOfBanks: 1
[    11.611]    MemoryModel: 6
[    11.611]    BankSize: 0
[    11.611]    NumberOfImages: 11
[    11.611]    RedMaskSize: 8
[    11.611]    RedFieldPosition: 16
[    11.611]    GreenMaskSize: 8
[    11.611]    GreenFieldPosition: 8
[    11.611]    BlueMaskSize: 8
[    11.611]    BlueFieldPosition: 0
[    11.611]    RsvdMaskSize: 8
[    11.611]    RsvdFieldPosition: 24
[    11.611]    DirectColorModeInfo: 0
[    11.611]    PhysBasePtr: 0xc0000000
[    11.611]    LinBytesPerScanLine: 5120
[    11.611]    BnkNumberOfImagePages: 11
[    11.611]    LinNumberOfImagePages: 11
[    11.611]    LinRedMaskSize: 8
[    11.611]    LinRedFieldPosition: 16
[    11.611]    LinGreenMaskSize: 8
[    11.611]    LinGreenFieldPosition: 8
[    11.611]    LinBlueMaskSize: 8
[    11.611]    LinBlueFieldPosition: 0
[    11.611]    LinRsvdMaskSize: 8
[    11.611]    LinRsvdFieldPosition: 24
[    11.611]    MaxPixelClock: 230000000
[    11.611] Mode: 105 (1024x768)
[    11.612]    ModeAttributes: 0x9b
[    11.612]    WinAAttributes: 0x7
[    11.612]    WinBAttributes: 0x0
[    11.612]    WinGranularity: 64
[    11.612]    WinSize: 64
[    11.612]    WinASegment: 0xa000
[    11.612]    WinBSegment: 0x0
[    11.612]    WinFuncPtr: 0xc00078cc
[    11.612]    BytesPerScanline: 1024
[    11.612]    XResolution: 1024
[    11.612]    YResolution: 768
[    11.612]    XCharSize: 8
[    11.612]    YCharSize: 16
[    11.612]    NumberOfPlanes: 1
[    11.612]    BitsPerPixel: 8
[    11.612]    NumberOfBanks: 1
[    11.612]    MemoryModel: 4
[    11.612]    BankSize: 0
[    11.612]    NumberOfImages: 84
[    11.612]    RedMaskSize: 0
[    11.612]    RedFieldPosition: 0
[    11.612]    GreenMaskSize: 0
[    11.612]    GreenFieldPosition: 0
[    11.612]    BlueMaskSize: 0
[    11.612]    BlueFieldPosition: 0
[    11.612]    RsvdMaskSize: 0
[    11.612]    RsvdFieldPosition: 0
[    11.612]    DirectColorModeInfo: 0
[    11.612]    PhysBasePtr: 0xc0000000
[    11.612]    LinBytesPerScanLine: 1024
[    11.612]    BnkNumberOfImagePages: 84
[    11.612]    LinNumberOfImagePages: 84
[    11.612]    LinRedMaskSize: 0
[    11.612]    LinRedFieldPosition: 0
[    11.612]    LinGreenMaskSize: 0
[    11.612]    LinGreenFieldPosition: 0
[    11.612]    LinBlueMaskSize: 0
[    11.612]    LinBlueFieldPosition: 0
[    11.612]    LinRsvdMaskSize: 0
[    11.612]    LinRsvdFieldPosition: 0
[    11.612]    MaxPixelClock: 230000000
[    11.612] Mode: 117 (1024x768)
[    11.612]    ModeAttributes: 0x9b
[    11.612]    WinAAttributes: 0x7
[    11.612]    WinBAttributes: 0x0
[    11.612]    WinGranularity: 64
[    11.612]    WinSize: 64
[    11.612]    WinASegment: 0xa000
[    11.612]    WinBSegment: 0x0
[    11.612]    WinFuncPtr: 0xc00078cc
[    11.612]    BytesPerScanline: 2048
[    11.612]    XResolution: 1024
[    11.612]    YResolution: 768
[    11.612]    XCharSize: 8
[    11.612]    YCharSize: 16
[    11.612]    NumberOfPlanes: 1
[    11.612]    BitsPerPixel: 16
[    11.612]    NumberOfBanks: 1
[    11.612]    MemoryModel: 6
[    11.612]    BankSize: 0
[    11.612]    NumberOfImages: 41
[    11.612]    RedMaskSize: 5
[    11.612]    RedFieldPosition: 11
[    11.612]    GreenMaskSize: 6
[    11.612]    GreenFieldPosition: 5
[    11.612]    BlueMaskSize: 5
[    11.612]    BlueFieldPosition: 0
[    11.612]    RsvdMaskSize: 0
[    11.612]    RsvdFieldPosition: 0
[    11.612]    DirectColorModeInfo: 0
[    11.612]    PhysBasePtr: 0xc0000000
[    11.612]    LinBytesPerScanLine: 2048
[    11.612]    BnkNumberOfImagePages: 41
[    11.612]    LinNumberOfImagePages: 41
[    11.612]    LinRedMaskSize: 5
[    11.612]    LinRedFieldPosition: 11
[    11.612]    LinGreenMaskSize: 6
[    11.612]    LinGreenFieldPosition: 5
[    11.612]    LinBlueMaskSize: 5
[    11.612]    LinBlueFieldPosition: 0
[    11.612]    LinRsvdMaskSize: 0
[    11.612]    LinRsvdFieldPosition: 0
[    11.612]    MaxPixelClock: 230000000
[    11.613] *Mode: 118 (1024x768)
[    11.613]    ModeAttributes: 0x9b
[    11.613]    WinAAttributes: 0x7
[    11.613]    WinBAttributes: 0x0
[    11.613]    WinGranularity: 64
[    11.613]    WinSize: 64
[    11.613]    WinASegment: 0xa000
[    11.613]    WinBSegment: 0x0
[    11.613]    WinFuncPtr: 0xc00078cc
[    11.613]    BytesPerScanline: 4096
[    11.613]    XResolution: 1024
[    11.613]    YResolution: 768
[    11.613]    XCharSize: 8
[    11.613]    YCharSize: 16
[    11.613]    NumberOfPlanes: 1
[    11.613]    BitsPerPixel: 32
[    11.613]    NumberOfBanks: 1
[    11.613]    MemoryModel: 6
[    11.613]    BankSize: 0
[    11.613]    NumberOfImages: 20
[    11.613]    RedMaskSize: 8
[    11.613]    RedFieldPosition: 16
[    11.613]    GreenMaskSize: 8
[    11.613]    GreenFieldPosition: 8
[    11.613]    BlueMaskSize: 8
[    11.613]    BlueFieldPosition: 0
[    11.613]    RsvdMaskSize: 8
[    11.613]    RsvdFieldPosition: 24
[    11.613]    DirectColorModeInfo: 0
[    11.613]    PhysBasePtr: 0xc0000000
[    11.613]    LinBytesPerScanLine: 4096
[    11.613]    BnkNumberOfImagePages: 20
[    11.613]    LinNumberOfImagePages: 20
[    11.613]    LinRedMaskSize: 8
[    11.613]    LinRedFieldPosition: 16
[    11.613]    LinGreenMaskSize: 8
[    11.613]    LinGreenFieldPosition: 8
[    11.613]    LinBlueMaskSize: 8
[    11.613]    LinBlueFieldPosition: 0
[    11.613]    LinRsvdMaskSize: 8
[    11.613]    LinRsvdFieldPosition: 24
[    11.613]    MaxPixelClock: 230000000
[    11.614] *Mode: 112 (640x480)
[    11.614]    ModeAttributes: 0x9b
[    11.614]    WinAAttributes: 0x7
[    11.614]    WinBAttributes: 0x0
[    11.614]    WinGranularity: 64
[    11.614]    WinSize: 64
[    11.614]    WinASegment: 0xa000
[    11.614]    WinBSegment: 0x0
[    11.614]    WinFuncPtr: 0xc00078cc
[    11.614]    BytesPerScanline: 2560
[    11.614]    XResolution: 640
[    11.614]    YResolution: 480
[    11.614]    XCharSize: 8
[    11.614]    YCharSize: 16
[    11.614]    NumberOfPlanes: 1
[    11.614]    BitsPerPixel: 32
[    11.614]    NumberOfBanks: 1
[    11.614]    MemoryModel: 6
[    11.614]    BankSize: 0
[    11.614]    NumberOfImages: 52
[    11.614]    RedMaskSize: 8
[    11.614]    RedFieldPosition: 16
[    11.614]    GreenMaskSize: 8
[    11.614]    GreenFieldPosition: 8
[    11.614]    BlueMaskSize: 8
[    11.614]    BlueFieldPosition: 0
[    11.614]    RsvdMaskSize: 8
[    11.614]    RsvdFieldPosition: 24
[    11.614]    DirectColorModeInfo: 0
[    11.614]    PhysBasePtr: 0xc0000000
[    11.614]    LinBytesPerScanLine: 2560
[    11.614]    BnkNumberOfImagePages: 52
[    11.614]    LinNumberOfImagePages: 52
[    11.614]    LinRedMaskSize: 8
[    11.614]    LinRedFieldPosition: 16
[    11.614]    LinGreenMaskSize: 8
[    11.614]    LinGreenFieldPosition: 8
[    11.614]    LinBlueMaskSize: 8
[    11.614]    LinBlueFieldPosition: 0
[    11.614]    LinRsvdMaskSize: 8
[    11.614]    LinRsvdFieldPosition: 24
[    11.614]    MaxPixelClock: 230000000
[    11.614] Mode: 114 (800x600)
[    11.614]    ModeAttributes: 0x9b
[    11.614]    WinAAttributes: 0x7
[    11.614]    WinBAttributes: 0x0
[    11.614]    WinGranularity: 64
[    11.614]    WinSize: 64
[    11.614]    WinASegment: 0xa000
[    11.614]    WinBSegment: 0x0
[    11.614]    WinFuncPtr: 0xc00078cc
[    11.614]    BytesPerScanline: 1600
[    11.614]    XResolution: 800
[    11.614]    YResolution: 600
[    11.614]    XCharSize: 8
[    11.614]    YCharSize: 16
[    11.614]    NumberOfPlanes: 1
[    11.614]    BitsPerPixel: 16
[    11.614]    NumberOfBanks: 1
[    11.614]    MemoryModel: 6
[    11.614]    BankSize: 0
[    11.614]    NumberOfImages: 67
[    11.614]    RedMaskSize: 5
[    11.614]    RedFieldPosition: 11
[    11.614]    GreenMaskSize: 6
[    11.614]    GreenFieldPosition: 5
[    11.614]    BlueMaskSize: 5
[    11.614]    BlueFieldPosition: 0
[    11.614]    RsvdMaskSize: 0
[    11.614]    RsvdFieldPosition: 0
[    11.614]    DirectColorModeInfo: 0
[    11.614]    PhysBasePtr: 0xc0000000
[    11.614]    LinBytesPerScanLine: 1600
[    11.614]    BnkNumberOfImagePages: 67
[    11.614]    LinNumberOfImagePages: 67
[    11.614]    LinRedMaskSize: 5
[    11.614]    LinRedFieldPosition: 11
[    11.614]    LinGreenMaskSize: 6
[    11.614]    LinGreenFieldPosition: 5
[    11.614]    LinBlueMaskSize: 5
[    11.614]    LinBlueFieldPosition: 0
[    11.614]    LinRsvdMaskSize: 0
[    11.614]    LinRsvdFieldPosition: 0
[    11.614]    MaxPixelClock: 230000000
[    11.615] *Mode: 115 (800x600)
[    11.615]    ModeAttributes: 0x9b
[    11.615]    WinAAttributes: 0x7
[    11.615]    WinBAttributes: 0x0
[    11.615]    WinGranularity: 64
[    11.615]    WinSize: 64
[    11.615]    WinASegment: 0xa000
[    11.615]    WinBSegment: 0x0
[    11.615]    WinFuncPtr: 0xc00078cc
[    11.615]    BytesPerScanline: 3200
[    11.615]    XResolution: 800
[    11.615]    YResolution: 600
[    11.615]    XCharSize: 8
[    11.615]    YCharSize: 16
[    11.615]    NumberOfPlanes: 1
[    11.615]    BitsPerPixel: 32
[    11.615]    NumberOfBanks: 1
[    11.615]    MemoryModel: 6
[    11.615]    BankSize: 0
[    11.615]    NumberOfImages: 33
[    11.615]    RedMaskSize: 8
[    11.615]    RedFieldPosition: 16
[    11.615]    GreenMaskSize: 8
[    11.615]    GreenFieldPosition: 8
[    11.615]    BlueMaskSize: 8
[    11.615]    BlueFieldPosition: 0
[    11.615]    RsvdMaskSize: 8
[    11.615]    RsvdFieldPosition: 24
[    11.615]    DirectColorModeInfo: 0
[    11.615]    PhysBasePtr: 0xc0000000
[    11.615]    LinBytesPerScanLine: 3200
[    11.615]    BnkNumberOfImagePages: 33
[    11.615]    LinNumberOfImagePages: 33
[    11.615]    LinRedMaskSize: 8
[    11.615]    LinRedFieldPosition: 16
[    11.615]    LinGreenMaskSize: 8
[    11.615]    LinGreenFieldPosition: 8
[    11.615]    LinBlueMaskSize: 8
[    11.615]    LinBlueFieldPosition: 0
[    11.615]    LinRsvdMaskSize: 8
[    11.615]    LinRsvdFieldPosition: 24
[    11.615]    MaxPixelClock: 230000000
[    11.615] Mode: 101 (640x480)
[    11.615]    ModeAttributes: 0x9b
[    11.615]    WinAAttributes: 0x7
[    11.615]    WinBAttributes: 0x0
[    11.615]    WinGranularity: 64
[    11.615]    WinSize: 64
[    11.615]    WinASegment: 0xa000
[    11.615]    WinBSegment: 0x0
[    11.615]    WinFuncPtr: 0xc00078cc
[    11.615]    BytesPerScanline: 640
[    11.615]    XResolution: 640
[    11.615]    YResolution: 480
[    11.615]    XCharSize: 8
[    11.615]    YCharSize: 16
[    11.615]    NumberOfPlanes: 1
[    11.615]    BitsPerPixel: 8
[    11.615]    NumberOfBanks: 1
[    11.615]    MemoryModel: 4
[    11.615]    BankSize: 0
[    11.615]    NumberOfImages: 203
[    11.615]    RedMaskSize: 0
[    11.615]    RedFieldPosition: 0
[    11.615]    GreenMaskSize: 0
[    11.615]    GreenFieldPosition: 0
[    11.615]    BlueMaskSize: 0
[    11.615]    BlueFieldPosition: 0
[    11.615]    RsvdMaskSize: 0
[    11.615]    RsvdFieldPosition: 0
[    11.615]    DirectColorModeInfo: 0
[    11.615]    PhysBasePtr: 0xc0000000
[    11.615]    LinBytesPerScanLine: 640
[    11.615]    BnkNumberOfImagePages: 203
[    11.615]    LinNumberOfImagePages: 203
[    11.615]    LinRedMaskSize: 0
[    11.615]    LinRedFieldPosition: 0
[    11.615]    LinGreenMaskSize: 0
[    11.615]    LinGreenFieldPosition: 0
[    11.615]    LinBlueMaskSize: 0
[    11.615]    LinBlueFieldPosition: 0
[    11.615]    LinRsvdMaskSize: 0
[    11.615]    LinRsvdFieldPosition: 0
[    11.615]    MaxPixelClock: 230000000
[    11.616] Mode: 103 (800x600)
[    11.616]    ModeAttributes: 0x9b
[    11.616]    WinAAttributes: 0x7
[    11.616]    WinBAttributes: 0x0
[    11.616]    WinGranularity: 64
[    11.616]    WinSize: 64
[    11.616]    WinASegment: 0xa000
[    11.616]    WinBSegment: 0x0
[    11.616]    WinFuncPtr: 0xc00078cc
[    11.616]    BytesPerScanline: 832
[    11.616]    XResolution: 800
[    11.616]    YResolution: 600
[    11.616]    XCharSize: 8
[    11.616]    YCharSize: 16
[    11.616]    NumberOfPlanes: 1
[    11.616]    BitsPerPixel: 8
[    11.616]    NumberOfBanks: 1
[    11.616]    MemoryModel: 4
[    11.616]    BankSize: 0
[    11.616]    NumberOfImages: 126
[    11.616]    RedMaskSize: 0
[    11.616]    RedFieldPosition: 0
[    11.616]    GreenMaskSize: 0
[    11.616]    GreenFieldPosition: 0
[    11.616]    BlueMaskSize: 0
[    11.616]    BlueFieldPosition: 0
[    11.616]    RsvdMaskSize: 0
[    11.616]    RsvdFieldPosition: 0
[    11.616]    DirectColorModeInfo: 0
[    11.616]    PhysBasePtr: 0xc0000000
[    11.616]    LinBytesPerScanLine: 832
[    11.616]    BnkNumberOfImagePages: 126
[    11.616]    LinNumberOfImagePages: 126
[    11.616]    LinRedMaskSize: 0
[    11.616]    LinRedFieldPosition: 0
[    11.616]    LinGreenMaskSize: 0
[    11.616]    LinGreenFieldPosition: 0
[    11.616]    LinBlueMaskSize: 0
[    11.616]    LinBlueFieldPosition: 0
[    11.616]    LinRsvdMaskSize: 0
[    11.616]    LinRsvdFieldPosition: 0
[    11.616]    MaxPixelClock: 230000000
[    11.617] Mode: 111 (640x480)
[    11.617]    ModeAttributes: 0x9b
[    11.617]    WinAAttributes: 0x7
[    11.617]    WinBAttributes: 0x0
[    11.617]    WinGranularity: 64
[    11.617]    WinSize: 64
[    11.617]    WinASegment: 0xa000
[    11.617]    WinBSegment: 0x0
[    11.617]    WinFuncPtr: 0xc00078cc
[    11.617]    BytesPerScanline: 1280
[    11.617]    XResolution: 640
[    11.617]    YResolution: 480
[    11.617]    XCharSize: 8
[    11.617]    YCharSize: 16
[    11.617]    NumberOfPlanes: 1
[    11.617]    BitsPerPixel: 16
[    11.617]    NumberOfBanks: 1
[    11.617]    MemoryModel: 6
[    11.617]    BankSize: 0
[    11.617]    NumberOfImages: 101
[    11.617]    RedMaskSize: 5
[    11.617]    RedFieldPosition: 11
[    11.617]    GreenMaskSize: 6
[    11.617]    GreenFieldPosition: 5
[    11.617]    BlueMaskSize: 5
[    11.617]    BlueFieldPosition: 0
[    11.617]    RsvdMaskSize: 0
[    11.617]    RsvdFieldPosition: 0
[    11.617]    DirectColorModeInfo: 0
[    11.617]    PhysBasePtr: 0xc0000000
[    11.617]    LinBytesPerScanLine: 1280
[    11.617]    BnkNumberOfImagePages: 101
[    11.617]    LinNumberOfImagePages: 101
[    11.617]    LinRedMaskSize: 5
[    11.617]    LinRedFieldPosition: 11
[    11.617]    LinGreenMaskSize: 6
[    11.617]    LinGreenFieldPosition: 5
[    11.617]    LinBlueMaskSize: 5
[    11.617]    LinBlueFieldPosition: 0
[    11.617]    LinRsvdMaskSize: 0
[    11.617]    LinRsvdFieldPosition: 0
[    11.617]    MaxPixelClock: 230000000
[    11.617]
[    11.617] (II) VESA(0): Total Memory: 1023 64KB banks (65472kB)
[    11.617] (II) VESA(0): <default monitor>: Using hsync range of 15.00-50.00 kHz
[    11.617] (II) VESA(0): <default monitor>: Using vrefresh range of 48.00-62.00 Hz
[    11.617] (II) VESA(0): <default monitor>: Using maximum pixel clock of 95.00 MHz
[    11.617] (WW) VESA(0): Unable to estimate virtual size
[    11.617] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[    11.619] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    11.619] (**) VESA(0): *Built-in mode "1024x768"
[    11.619] (**) VESA(0): *Built-in mode "800x600"
[    11.619] (**) VESA(0): *Built-in mode "640x480"
[    11.619] (**) VESA(0): Display dimensions: (640, 360) mm
[    11.619] (**) VESA(0): DPI set to (40, 54)
[    11.619] (**) VESA(0): Using "Shadow Framebuffer"
[    11.619] (II) Loading sub module "shadow"
[    11.619] (II) LoadModule: "shadow"
[    11.619] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    11.624] (II) Module shadow: vendor="X.Org Foundation"
[    11.624]    compiled for 1.10.4, module version = 1.1.0
[    11.624]    ABI class: X.Org ANSI C Emulation, version 0.4
[    11.624] (II) Loading sub module "fb"
[    11.624] (II) LoadModule: "fb"
[    11.624] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.629] (II) Module fb: vendor="X.Org Foundation"
[    11.629]    compiled for 1.10.4, module version = 1.0.0
[    11.629]    ABI class: X.Org ANSI C Emulation, version 0.4
[    11.629] (II) UnloadModule: "fbdev"
[    11.629] (II) Unloading fbdev
[    11.629] (II) UnloadModule: "fbdevhw"
[    11.629] (II) Unloading fbdevhw
[    11.629] (==) Depth 24 pixmap format is 32 bpp
[    11.629] (II) Loading sub module "int10"
[    11.629] (II) LoadModule: "int10"
[    11.630] (II) Loading /usr/lib/xorg/modules/libint10.so
[    11.630] (II) Module int10: vendor="X.Org Foundation"
[    11.630]    compiled for 1.10.4, module version = 1.0.0
[    11.630]    ABI class: X.Org Video Driver, version 10.0
[    11.630] (II) VESA(0): initializing int10
[    11.630] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    11.630] (II) VESA(0): VESA BIOS detected
[    11.630] (II) VESA(0): VESA VBE Version 3.0
[    11.630] (II) VESA(0): VESA VBE Total Mem: 65472 kB
[    11.630] (II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS
[    11.630] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    11.630] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    11.630] (II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Desktop Graphics Controller
[    11.630] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    11.636] (II) VESA(0): virtual address = 0xb3122000,
        physical address = 0xc0000000, size = 67043328
[    11.642] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[    11.792] (==) VESA(0): Default visual is TrueColor
[    11.792] (==) VESA(0): Backing store disabled
[    11.792] (==) VESA(0): DPMS enabled
[    11.792] (==) RandR enabled
[    11.792] (II) Initializing built-in extension Generic Event Extension
[    11.792] (II) Initializing built-in extension SHAPE
[    11.792] (II) Initializing built-in extension MIT-SHM
[    11.792] (II) Initializing built-in extension XInputExtension
[    11.792] (II) Initializing built-in extension XTEST
[    11.792] (II) Initializing built-in extension BIG-REQUESTS
[    11.792] (II) Initializing built-in extension SYNC
[    11.792] (II) Initializing built-in extension XKEYBOARD
[    11.792] (II) Initializing built-in extension XC-MISC
[    11.792] (II) Initializing built-in extension SECURITY
[    11.792] (II) Initializing built-in extension XINERAMA
[    11.792] (II) Initializing built-in extension XFIXES
[    11.792] (II) Initializing built-in extension RENDER
[    11.792] (II) Initializing built-in extension RANDR
[    11.792] (II) Initializing built-in extension COMPOSITE
[    11.792] (II) Initializing built-in extension DAMAGE
[    11.792] (II) Initializing built-in extension GESTURE
[    11.798] (II) AIGLX: Screen 0 is not DRI2 capable
[    11.798] (II) AIGLX: Screen 0 is not DRI capable
[    11.798] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/swrast_dri.so
[    11.817] (II) AIGLX: Loaded and initialized swrast
[    11.817] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    11.827] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    11.836] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    11.836] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    11.836] (II) LoadModule: "evdev"
[    11.836] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.836] (II) Module evdev: vendor="X.Org Foundation"
[    11.836]    compiled for 1.10.2, module version = 2.6.0
[    11.836]    Module class: X.Org XInput Driver
[    11.836]    ABI class: X.Org XInput driver, version 12.3
[    11.836] (II) Using input driver 'evdev' for 'Power Button'
[    11.836] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.836] (**) Power Button: always reports core events
[    11.836] (**) Power Button: Device: "/dev/input/event1"
[    11.836] (--) Power Button: Found keys
[    11.836] (II) Power Button: Configuring as keyboard
[    11.836] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    11.836] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    11.836] (**) Option "xkb_rules" "evdev"
[    11.836] (**) Option "xkb_model" "pc105"
[    11.836] (**) Option "xkb_layout" "us"
[    11.838] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    11.838] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    11.838] (II) Using input driver 'evdev' for 'Power Button'
[    11.838] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.838] (**) Power Button: always reports core events
[    11.838] (**) Power Button: Device: "/dev/input/event0"
[    11.838] (--) Power Button: Found keys
[    11.838] (II) Power Button: Configuring as keyboard
[    11.838] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    11.838] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    11.838] (**) Option "xkb_rules" "evdev"
[    11.838] (**) Option "xkb_model" "pc105"
[    11.838] (**) Option "xkb_layout" "us"
[    11.841] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event4)
[    11.841] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    11.841] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    11.841] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.841] (**) USB Optical Mouse: always reports core events
[    11.841] (**) USB Optical Mouse: Device: "/dev/input/event4"
[    11.841] (--) USB Optical Mouse: Found 3 mouse buttons
[    11.841] (--) USB Optical Mouse: Found scroll wheel(s)
[    11.841] (--) USB Optical Mouse: Found relative axes
[    11.841] (--) USB Optical Mouse: Found x and y relative axes
[    11.841] (II) USB Optical Mouse: Configuring as mouse
[    11.841] (II) USB Optical Mouse: Adding scrollwheel support
[    11.841] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    11.841] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    11.841] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0/usb3/3-1/3-1.4/3-1.4:1.0/input/input4/event4"
[    11.841] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[    11.841] (II) USB Optical Mouse: initialized for relative axes.
[    11.841] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    11.841] (**) USB Optical Mouse: (accel) acceleration profile 0
[    11.841] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    11.841] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    11.841] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    11.841] (II) No input driver/identifier specified (ignoring)
[    11.842] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event2)
[    11.842] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[    11.842] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[    11.842] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.842] (**) HID 04f3:0103: always reports core events
[    11.842] (**) HID 04f3:0103: Device: "/dev/input/event2"
[    11.842] (--) HID 04f3:0103: Found keys
[    11.842] (II) HID 04f3:0103: Configuring as keyboard
[    11.842] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input2/event2"
[    11.842] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD)
[    11.842] (**) Option "xkb_rules" "evdev"
[    11.842] (**) Option "xkb_model" "pc105"
[    11.842] (**) Option "xkb_layout" "us"
[    11.842] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event3)
[    11.842] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[    11.842] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[    11.842] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.843] (**) HID 04f3:0103: always reports core events
[    11.843] (**) HID 04f3:0103: Device: "/dev/input/event3"
[    11.843] (--) HID 04f3:0103: Found 1 mouse buttons
[    11.843] (--) HID 04f3:0103: Found scroll wheel(s)
[    11.843] (--) HID 04f3:0103: Found relative axes
[    11.843] (--) HID 04f3:0103: Found absolute axes
[    11.843] (II) evdev-grail: failed to open grail, no gesture support
[    11.843] (--) HID 04f3:0103: Found keys
[    11.843] (II) HID 04f3:0103: Configuring as mouse
[    11.843] (II) HID 04f3:0103: Configuring as keyboard
[    11.843] (II) HID 04f3:0103: Adding scrollwheel support
[    11.843] (**) HID 04f3:0103: YAxisMapping: buttons 4 and 5
[    11.843] (**) HID 04f3:0103: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    11.843] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.1/input/input3/event3"
[    11.843] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD)
[    11.843] (**) Option "xkb_rules" "evdev"
[    11.843] (**) Option "xkb_model" "pc105"
[    11.843] (**) Option "xkb_layout" "us"
[    11.843] (EE) HID 04f3:0103: failed to initialize for relative axes.
[    11.843] (II) HID 04f3:0103: initialized for absolute axes.
[    11.843] (**) HID 04f3:0103: (accel) keeping acceleration scheme 1
[    11.843] (**) HID 04f3:0103: (accel) acceleration profile 0
[    11.843] (**) HID 04f3:0103: (accel) acceleration factor: 2.000
[    11.843] (**) HID 04f3:0103: (accel) acceleration threshold: 4
[    11.856] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event5)
[    11.856] (II) No input driver/identifier specified (ignoring)
[    11.856] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event6)
[    11.856] (II) No input driver/identifier specified (ignoring)

```

---

### Post by BicyclerBoy on 2012-01-07
Your DVI jack output may not have the analogue part (DVI-D).
You can study the pin pattern & c.f. wikipedia images..

The VESA driver can not go higher than 1024x768..

Using no-kernel-mode-setting (nomodeset) will stop the intel driver from loading..

You can force VESA or intel with the keywords in /etc/X11/xorg.conf
```

Section "Device"
   Option "Driver" "intel"
EndSection

```
Can you try an DVI-D to HDMI adapter cable ?

Was that xrandr --prop cmd run when using the intel driver ?

Maybe we can try to set a new video mode using intel driver & xrandr...

IHO is that you need the latest kernel & intel driver (xorg edgers + sarvatt)  for sandybridge to work (well)..

---

### Post by alfonso78 on 2012-01-08
> **BicyclerBoy said:**
> Your DVI jack output may not have the analogue part (DVI-D).
You can study the pin pattern & c.f. wikipedia images..

The VESA driver can not go higher than 1024x768..

Using no-kernel-mode-setting (nomodeset) will stop the intel driver from loading..

You can force VESA or intel with the keywords in /etc/X11/xorg.conf
```

Section "Device"
   Option "Driver" "intel"
EndSection

```
Can you try an DVI-D to HDMI adapter cable ?

Was that xrandr --prop cmd run when using the intel driver ?

Maybe we can try to set a new video mode using intel driver & xrandr...

IHO is that you need the latest kernel & intel driver (xorg edgers + sarvatt)  for sandybridge to work (well)..

Hi BicyclerBoy and thank you! :)

first of all, with nomodeset I can't really watch a video on my screen (the video is not fluid) so I must find a better solution.

To force VESA with Intel as you suggested, do I keep "nomodeset" or not? What about "xforcevesa"? what is the difference?

About the DVI port: based on the wiki page and the website of the producer it's a DVI-I (but the website mentions also HDCP, I don't know if that maybe cause VGA to work differently).

I read yesterday an article saying that for VGA to work, due to a bug, I should try to connect e disconnect the cable at every boot. I might try that also.

> The VESA driver can not go higher than 1024x768..
that is NOT a problem for me at all. My TV only goes up to 1024x768 so if with VESA driver I can see a video in a fluid way, I'll be happy.

> Using no-kernel-mode-setting (nomodeset) will stop the intel driver from loading..
is this a different thing than using the VESA driver or is it the same thing?

> Can you try an DVI-D to HDMI adapter cable ?
I don't have one. If I don't find a better solution I'll buy one this week to test.

> Was that xrandr --prop cmd run when using the intel driver ?
I'm not sure. I'll test later and tell you.

> Maybe we can try to set a new video mode using intel driver & xrandr...

do you mean a new resolution? I need 1024x768... that's the best I can do with this TV and it's enough for my needs.

> IHO is that you need the latest kernel & intel driver (xorg edgers + sarvatt)  for sandybridge to work (well)..
I tried xorg edgers and the system became very unstable. It crashes after a few minutes. Do you know if it's possible to troubleshoot the instability?

On xorg edgers there is this note: 
> *IMPORTANT NOTICE* - xserver 1.12 is being prepared for this PPA and should be in during the week of jan 9th. As usual, expect problems if you are using proprietary drivers until they are updated.
maybe I could try 1.12 when it's out in a few days...

sarvatt is a used ID... to which PPA do you refer to?

thanks a lot!

---

### Post by BicyclerBoy on 2012-01-09
The vesa driver will have terrible gl/glx & video performance.

All video drivers have kernel & user space components. The intel & VESA kernel space parts are built-in to linux kernel.

The nomodeset option is a hack & stops the loading of video drivers that require KMS to function. VESA does not use KMS.

You can override the video driver choice (HAL/udev rules?) by using xorg.conf.

You could try the different video output formats in VLC, possible something will work better.
I believe that mplayer & VLC can drive the console framebuffer directly (no X server running). This might not work on SNA.

Maybe it is a bad time to be using xorg-edgers ppa.
This ppa changes the user space driver.

Force VGA output on with grub boot option:
add a kernel boot option "video=VGA1:e"
(remove the "nomodeset" option)

Try fix VGA with xrandr:
 xrandr --output VGA1 --mode 1024x768
could do this X server running & with HDMI connected..should get 2 virtual screens connected to the same monitor..try switch TV to VGA input ..does it work ?

---

### Post by alfonso78 on 2012-01-10
Hi BicyclerBoy,

so here are my news. I finally manage to install a new kernel (3.2.0-7-generic-pae) and things changed for sure.
Now not only the screen is splitted, but it's also flickering (before it wasn't).

so this is the current output of xrandr --prop :

```

xrandr --prop
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
	Broadcast RGB:	Full
		supported: Full         Limited 16:2
	audio:	auto
		supported: off          auto         on          
DP1 disconnected (normal left inverted right x axis y axis)
	Broadcast RGB:	Full
		supported: Full         Limited 16:2
	audio:	auto
		supported: off          auto         on          
HDMI2 connected 1024x768+0+0 (normal left inverted right x axis y axis) 640mm x 360mm
	EDID:
		00ffffffffffff00410c010001010101
		01100103804024780ae692a3544a9926
		0f4a4c21080001010101010101010101
		010101010101011d80d0721c1620102c
		258080682100009e6419004041002630
		18883600902c11000018000000fc0050
		68696c697073204654560a20000000fd
		00303e0f3209000a202020202020018b
		020324f04b0103040506071213141516
		29091f07150750190786830100006503
		0c002000011d8018711c1620582c2500
		80682100009e011d00bc52d01e20b828
		554080682100001e011d007251d01e20
		6e28550080682100001e8c0ad0902040
		31200c4055008068210000188c0ad08a
		20e02d10103e360080682100001800c1
	Broadcast RGB:	Full
		supported: Full         Limited 16:2
	audio:	auto
		supported: off          auto         on          
   1024x768       60.0* 
   800x600        60.3  
   640x480        60.0  
HDMI3 disconnected (normal left inverted right x axis y axis)
	Broadcast RGB:	Full
		supported: Full         Limited 16:2
	audio:	auto
		supported: off          auto         on          
DP2 disconnected (normal left inverted right x axis y axis)
	Broadcast RGB:	Full
		supported: Full         Limited 16:2
	audio:	auto
		supported: off          auto         on          
DP3 disconnected (normal left inverted right x axis y axis)
	Broadcast RGB:	Full
		supported: Full         Limited 16:2
	audio:	auto
		supported: off          auto         on

```

and this is the current output of cat /var/log/Xorg.0.log :

```

$ cat /var/log/Xorg.0.log
[    11.372]
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    11.372] X Protocol Version 11, Revision 0
[    11.372] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    11.372] Current Operating System: Linux NAS 3.2.0-7-generic-pae #13-Ubuntu SMP Sun Dec 25 03:44:50 UTC 2011 i686
[    11.372] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-7-generic-pae root=UUID=2f050176-99ce-49de-9826-a01fe25ecec9 ro bootdegraded=true quiet splash vt.handoff=7
[    11.372] Build Date: 19 October 2011  05:09:41AM
[    11.372] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support)
[    11.372] Current version of pixman: 0.22.2
[    11.372]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    11.372] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.372] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 10 09:11:43 2012
[    11.372] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.373] (==) No Layout section.  Using the first Screen section.
[    11.373] (==) No screen section available. Using defaults.
[    11.373] (**) |-->Screen "Default Screen Section" (0)
[    11.373] (**) |   |-->Monitor "<default monitor>"
[    11.373] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    11.373] (==) Automatically adding devices
[    11.373] (==) Automatically enabling devices
[    11.376] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.376]    Entry deleted from font path.
[    11.376] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    11.376]    Entry deleted from font path.
[    11.376] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    11.376]    Entry deleted from font path.
[    11.376] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    11.376]    Entry deleted from font path.
[    11.376] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    11.376]    Entry deleted from font path.
[    11.379] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[    11.379] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    11.379] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    11.379] (II) Loader magic: 0x823ada0
[    11.379] (II) Module ABI versions:
[    11.379]    X.Org ANSI C Emulation: 0.4
[    11.379]    X.Org Video Driver: 10.0
[    11.379]    X.Org XInput driver : 12.3
[    11.379]    X.Org Server Extension : 5.0
[    11.379] (--) PCI:*(0:0:2:0) 8086:0102:19da:a166 rev 9, Mem @ 0xfe000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
[    11.379] (II) Open ACPI successful (/var/run/acpid.socket)
[    11.379] (II) LoadModule: "extmod"
[    11.382] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    11.382] (II) Module extmod: vendor="X.Org Foundation"
[    11.382]    compiled for 1.10.4, module version = 1.0.0
[    11.382]    Module class: X.Org Server Extension
[    11.382]    ABI class: X.Org Server Extension, version 5.0
[    11.382] (II) Loading extension MIT-SCREEN-SAVER
[    11.382] (II) Loading extension XFree86-VidModeExtension
[    11.382] (II) Loading extension XFree86-DGA
[    11.382] (II) Loading extension DPMS
[    11.382] (II) Loading extension XVideo
[    11.382] (II) Loading extension XVideo-MotionCompensation
[    11.382] (II) Loading extension X-Resource
[    11.382] (II) LoadModule: "dbe"
[    11.382] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    11.382] (II) Module dbe: vendor="X.Org Foundation"
[    11.382]    compiled for 1.10.4, module version = 1.0.0
[    11.382]    Module class: X.Org Server Extension
[    11.382]    ABI class: X.Org Server Extension, version 5.0
[    11.382] (II) Loading extension DOUBLE-BUFFER
[    11.382] (II) LoadModule: "glx"
[    11.383] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    11.383] (II) Module glx: vendor="X.Org Foundation"
[    11.383]    compiled for 1.10.4, module version = 1.0.0
[    11.383]    ABI class: X.Org Server Extension, version 5.0
[    11.383] (==) AIGLX enabled
[    11.383] (II) Loading extension GLX
[    11.383] (II) LoadModule: "record"
[    11.383] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    11.383] (II) Module record: vendor="X.Org Foundation"
[    11.383]    compiled for 1.10.4, module version = 1.13.0
[    11.383]    Module class: X.Org Server Extension
[    11.383]    ABI class: X.Org Server Extension, version 5.0
[    11.383] (II) Loading extension RECORD
[    11.383] (II) LoadModule: "dri"
[    11.383] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    11.383] (II) Module dri: vendor="X.Org Foundation"
[    11.383]    compiled for 1.10.4, module version = 1.0.0
[    11.383]    ABI class: X.Org Server Extension, version 5.0
[    11.383] (II) Loading extension XFree86-DRI
[    11.383] (II) LoadModule: "dri2"
[    11.383] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    11.383] (II) Module dri2: vendor="X.Org Foundation"
[    11.383]    compiled for 1.10.4, module version = 1.2.0
[    11.383]    ABI class: X.Org Server Extension, version 5.0
[    11.383] (II) Loading extension DRI2
[    11.383] (==) Matched intel as autoconfigured driver 0
[    11.383] (==) Matched vesa as autoconfigured driver 1
[    11.383] (==) Matched fbdev as autoconfigured driver 2
[    11.383] (==) Assigned the driver to the xf86ConfigLayout
[    11.383] (II) LoadModule: "intel"
[    11.390] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    11.390] (II) Module intel: vendor="X.Org Foundation"
[    11.390]    compiled for 1.10.4, module version = 2.15.901
[    11.390]    Module class: X.Org Video Driver
[    11.390]    ABI class: X.Org Video Driver, version 10.0
[    11.390] (II) LoadModule: "vesa"
[    11.390] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.390] (II) Module vesa: vendor="X.Org Foundation"
[    11.390]    compiled for 1.10.2, module version = 2.3.0
[    11.390]    Module class: X.Org Video Driver
[    11.390]    ABI class: X.Org Video Driver, version 10.0
[    11.390] (II) LoadModule: "fbdev"
[    11.390] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.390] (II) Module fbdev: vendor="X.Org Foundation"
[    11.390]    compiled for 1.10.0, module version = 0.4.2
[    11.390]    ABI class: X.Org Video Driver, version 10.0
[    11.390] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
        Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
        Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
        Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
        Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    11.391] (II) VESA: driver for VESA chipsets: vesa
[    11.391] (II) FBDEV: driver for framebuffer: fbdev
[    11.391] (++) using VT number 7

[    11.392] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    11.392] (WW) Falling back to old probe method for vesa
[    11.392] (WW) Falling back to old probe method for fbdev
[    11.392] (II) Loading sub module "fbdevhw"
[    11.392] (II) LoadModule: "fbdevhw"
[    11.392] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    11.392] (II) Module fbdevhw: vendor="X.Org Foundation"
[    11.392]    compiled for 1.10.4, module version = 0.0.2
[    11.392]    ABI class: X.Org Video Driver, version 10.0
[    11.392] drmOpenDevice: node name is /dev/dri/card0
[    11.392] drmOpenDevice: open result is 12, (OK)
[    11.392] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    11.392] drmOpenDevice: node name is /dev/dri/card0
[    11.392] drmOpenDevice: open result is 12, (OK)
[    11.392] drmOpenByBusid: drmOpenMinor returns 12
[    11.392] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    11.392] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    11.392] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    11.392] (==) intel(0): RGB weight 888
[    11.392] (==) intel(0): Default visual is TrueColor
[    11.392] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Desktop (GT1)
[    11.392] (--) intel(0): Chipset: "Sandybridge Desktop (GT1)"
[    11.392] (**) intel(0): Relaxed fencing enabled
[    11.392] (**) intel(0): Wait on SwapBuffers? enabled
[    11.392] (**) intel(0): Triple buffering? enabled
[    11.392] (**) intel(0): Framebuffer tiled
[    11.392] (**) intel(0): Pixmaps tiled
[    11.392] (**) intel(0): 3D buffers tiled
[    11.392] (**) intel(0): SwapBuffers wait enabled
[    11.392] (==) intel(0): video overlay key set to 0x101fe
[    11.392] (II) intel(0): Output VGA1 has no monitor section
[    11.427] (II) intel(0): Output HDMI1 has no monitor section
[    11.476] (II) intel(0): Output DP1 has no monitor section
[    11.732] (II) intel(0): Output HDMI2 has no monitor section
[    11.755] (II) intel(0): Output HDMI3 has no monitor section
[    11.804] (II) intel(0): Output DP2 has no monitor section
[    11.852] (II) intel(0): Output DP3 has no monitor section
[    11.852] (II) intel(0): EDID for output VGA1
[    11.874] (II) intel(0): EDID for output HDMI1
[    11.920] (II) intel(0): EDID for output DP1
[    12.164] (II) intel(0): EDID for output HDMI2
[    12.164] (II) intel(0): Manufacturer: PHL  Model: 1  Serial#: 16843009
[    12.164] (II) intel(0): Year: 2006  Week: 1
[    12.164] (II) intel(0): EDID Version: 1.3
[    12.164] (II) intel(0): Digital Display Input
[    12.164] (II) intel(0): Max Image Size [cm]: horiz.: 64  vert.: 36
[    12.164] (II) intel(0): Gamma: 2.20
[    12.164] (II) intel(0): No DPMS capabilities specified
[    12.164] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[    12.164] (II) intel(0): First detailed timing is preferred mode
[    12.164] (II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.290 greenY: 0.600
[    12.164] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.289 whiteY: 0.299
[    12.164] (II) intel(0): Supported established timings:
[    12.164] (II) intel(0): 640x480@60Hz
[    12.164] (II) intel(0): 800x600@60Hz
[    12.164] (II) intel(0): 1024x768@60Hz
[    12.164] (II) intel(0): Manufacturer's mask: 0
[    12.164] (II) intel(0): Supported detailed timing:
[    12.164] (II) intel(0): clock: 74.2 MHz   Image Size:  640 x 360 mm
[    12.164] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    12.164] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    12.164] (II) intel(0): Supported detailed timing:
[    12.164] (II) intel(0): clock: 65.0 MHz   Image Size:  400 x 300 mm
[    12.164] (II) intel(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[    12.164] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[    12.164] (II) intel(0): Monitor name: Philips FTV
[    12.164] (II) intel(0): Ranges: V min: 48 V max: 62 Hz, H min: 15 H max: 50 kHz, PixClock max 95 MHz
[    12.164] (II) intel(0): Supported detailed timing:
[    12.164] (II) intel(0): clock: 74.2 MHz   Image Size:  640 x 360 mm
[    12.164] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    12.164] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    12.164] (II) intel(0): Supported detailed timing:
[    12.164] (II) intel(0): clock: 74.2 MHz   Image Size:  640 x 360 mm
[    12.164] (II) intel(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[    12.164] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    12.164] (II) intel(0): Supported detailed timing:
[    12.164] (II) intel(0): clock: 74.2 MHz   Image Size:  640 x 360 mm
[    12.164] (II) intel(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    12.164] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    12.164] (II) intel(0): Supported detailed timing:
[    12.164] (II) intel(0): clock: 27.0 MHz   Image Size:  640 x 360 mm
[    12.164] (II) intel(0): h_active: 720  h_sync: 732  h_sync_end 796 h_blank_end 864 h_border: 0
[    12.164] (II) intel(0): v_active: 576  v_sync: 581  v_sync_end 586 v_blanking: 625 v_border: 0
[    12.164] (II) intel(0): Supported detailed timing:
[    12.164] (II) intel(0): clock: 27.0 MHz   Image Size:  640 x 360 mm
[    12.164] (II) intel(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    12.164] (II) intel(0): v_active: 480  v_sync: 483  v_sync_end 489 v_blanking: 525 v_border: 0
[    12.164] (II) intel(0): Number of EDID sections to follow: 1
[    12.164] (II) intel(0): EDID (in hex):
[    12.164] (II) intel(0):     00ffffffffffff00410c010001010101
[    12.164] (II) intel(0):     01100103804024780ae692a3544a9926
[    12.164] (II) intel(0):     0f4a4c21080001010101010101010101
[    12.164] (II) intel(0):     010101010101011d80d0721c1620102c
[    12.164] (II) intel(0):     258080682100009e6419004041002630
[    12.164] (II) intel(0):     18883600902c11000018000000fc0050
[    12.164] (II) intel(0):     68696c697073204654560a20000000fd
[    12.164] (II) intel(0):     00303e0f3209000a202020202020018b
[    12.164] (II) intel(0):     020324f04b0103040506071213141516
[    12.164] (II) intel(0):     29091f07150750190786830100006503
[    12.164] (II) intel(0):     0c002000011d8018711c1620582c2500
[    12.164] (II) intel(0):     80682100009e011d00bc52d01e20b828
[    12.164] (II) intel(0):     554080682100001e011d007251d01e20
[    12.164] (II) intel(0):     6e28550080682100001e8c0ad0902040
[    12.164] (II) intel(0):     31200c4055008068210000188c0ad08a
[    12.164] (II) intel(0):     20e02d10103e360080682100001800c1
[    12.164] (II) intel(0): Printing probed modes for output HDMI2
[    12.164] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    12.164] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    12.164] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    12.187] (II) intel(0): EDID for output HDMI3
[    12.236] (II) intel(0): EDID for output DP2
[    12.288] (II) intel(0): EDID for output DP3
[    12.288] (II) intel(0): Output VGA1 disconnected
[    12.288] (II) intel(0): Output HDMI1 disconnected
[    12.288] (II) intel(0): Output DP1 disconnected
[    12.288] (II) intel(0): Output HDMI2 connected
[    12.288] (II) intel(0): Output HDMI3 disconnected
[    12.288] (II) intel(0): Output DP2 disconnected
[    12.288] (II) intel(0): Output DP3 disconnected
[    12.288] (II) intel(0): Using fuzzy aspect match for initial modes
[    12.288] (II) intel(0): Output HDMI2 using initial mode 1024x768
[    12.288] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    12.288] (II) intel(0): Kernel page flipping support detected, enabling
[    12.288] (==) intel(0): DPI set to (96, 96)
[    12.288] (II) Loading sub module "fb"
[    12.288] (II) LoadModule: "fb"
[    12.289] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.289] (II) Module fb: vendor="X.Org Foundation"
[    12.289]    compiled for 1.10.4, module version = 1.0.0
[    12.289]    ABI class: X.Org ANSI C Emulation, version 0.4
[    12.289] (II) Loading sub module "dri2"
[    12.289] (II) LoadModule: "dri2"
[    12.289] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    12.289] (II) Module dri2: vendor="X.Org Foundation"
[    12.289]    compiled for 1.10.4, module version = 1.2.0
[    12.289]    ABI class: X.Org Server Extension, version 5.0
[    12.289] (II) UnloadModule: "vesa"
[    12.289] (II) Unloading vesa
[    12.289] (II) UnloadModule: "fbdev"
[    12.289] (II) Unloading fbdev
[    12.289] (II) UnloadModule: "fbdevhw"
[    12.289] (II) Unloading fbdevhw
[    12.289] (==) Depth 24 pixmap format is 32 bpp
[    12.289] (II) intel(0): [DRI2] Setup complete
[    12.289] (II) intel(0): [DRI2]   DRI driver: i965
[    12.289] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    12.290] (II) UXA(0): Driver registered support for the following operations:
[    12.290] (II)         solid
[    12.290] (II)         copy
[    12.290] (II)         composite (RENDER acceleration)
[    12.290] (II)         put_image
[    12.290] (II)         get_image
[    12.290] (==) intel(0): Backing store disabled
[    12.290] (==) intel(0): Silken mouse enabled
[    12.290] (II) intel(0): Initializing HW Cursor
[    12.348] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    12.348] (==) intel(0): DPMS enabled
[    12.348] (==) intel(0): Intel XvMC decoder enabled
[    12.348] (II) intel(0): Set up textured video
[    12.348] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    12.348] (II) intel(0): direct rendering: DRI2 Enabled
[    12.348] (==) intel(0): hotplug detection: "enabled"
[    12.348] (--) RandR disabled
[    12.348] (II) Initializing built-in extension Generic Event Extension
[    12.348] (II) Initializing built-in extension SHAPE
[    12.348] (II) Initializing built-in extension MIT-SHM
[    12.348] (II) Initializing built-in extension XInputExtension
[    12.348] (II) Initializing built-in extension XTEST
[    12.348] (II) Initializing built-in extension BIG-REQUESTS
[    12.348] (II) Initializing built-in extension SYNC
[    12.348] (II) Initializing built-in extension XKEYBOARD
[    12.348] (II) Initializing built-in extension XC-MISC
[    12.348] (II) Initializing built-in extension SECURITY
[    12.348] (II) Initializing built-in extension XINERAMA
[    12.348] (II) Initializing built-in extension XFIXES
[    12.348] (II) Initializing built-in extension RENDER
[    12.348] (II) Initializing built-in extension RANDR
[    12.348] (II) Initializing built-in extension COMPOSITE
[    12.348] (II) Initializing built-in extension DAMAGE
[    12.348] (II) Initializing built-in extension GESTURE
[    12.354] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/i965_dri.so
[    12.355] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    12.355] (II) AIGLX: enabled GLX_INTEL_swap_event
[    12.355] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    12.355] (II) AIGLX: enabled GLX_SGI_make_current_read
[    12.355] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    12.355] (II) AIGLX: Loaded and initialized i965
[    12.355] (II) GLX: Initialized DRI2 GL provider for screen 0
[    12.356] (II) intel(0): Setting screen physical size to 270 x 203
[    12.361] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    12.366] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    12.366] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    12.366] (II) LoadModule: "evdev"
[    12.366] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.367] (II) Module evdev: vendor="X.Org Foundation"
[    12.367]    compiled for 1.10.2, module version = 2.6.0
[    12.367]    Module class: X.Org XInput Driver
[    12.367]    ABI class: X.Org XInput driver, version 12.3
[    12.367] (II) Using input driver 'evdev' for 'Power Button'
[    12.367] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.367] (**) Power Button: always reports core events
[    12.367] (**) Power Button: Device: "/dev/input/event1"
[    12.367] (--) Power Button: Found keys
[    12.367] (II) Power Button: Configuring as keyboard
[    12.367] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    12.367] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    12.367] (**) Option "xkb_rules" "evdev"
[    12.367] (**) Option "xkb_model" "pc105"
[    12.367] (**) Option "xkb_layout" "us"
[    12.368] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    12.368] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    12.368] (II) Using input driver 'evdev' for 'Power Button'
[    12.368] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.368] (**) Power Button: always reports core events
[    12.368] (**) Power Button: Device: "/dev/input/event0"
[    12.368] (--) Power Button: Found keys
[    12.368] (II) Power Button: Configuring as keyboard
[    12.368] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    12.368] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    12.368] (**) Option "xkb_rules" "evdev"
[    12.368] (**) Option "xkb_model" "pc105"
[    12.368] (**) Option "xkb_layout" "us"
[    12.370] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event5)
[    12.370] (II) No input driver/identifier specified (ignoring)
[    12.370] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event6)
[    12.370] (II) No input driver/identifier specified (ignoring)
[    12.371] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event2)
[    12.372] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[    12.372] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[    12.372] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.372] (**) HID 04f3:0103: always reports core events
[    12.372] (**) HID 04f3:0103: Device: "/dev/input/event2"
[    12.372] (--) HID 04f3:0103: Found keys
[    12.372] (II) HID 04f3:0103: Configuring as keyboard
[    12.372] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input2/event2"
[    12.372] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD)
[    12.372] (**) Option "xkb_rules" "evdev"
[    12.372] (**) Option "xkb_model" "pc105"
[    12.372] (**) Option "xkb_layout" "us"
[    12.372] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event3)
[    12.372] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[    12.372] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[    12.372] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.372] (**) HID 04f3:0103: always reports core events
[    12.372] (**) HID 04f3:0103: Device: "/dev/input/event3"
[    12.372] (--) HID 04f3:0103: Found 1 mouse buttons
[    12.372] (--) HID 04f3:0103: Found scroll wheel(s)
[    12.372] (--) HID 04f3:0103: Found relative axes
[    12.372] (--) HID 04f3:0103: Found absolute axes
[    12.372] (II) evdev-grail: failed to open grail, no gesture support
[    12.372] (--) HID 04f3:0103: Found keys
[    12.372] (II) HID 04f3:0103: Configuring as mouse
[    12.372] (II) HID 04f3:0103: Configuring as keyboard
[    12.372] (II) HID 04f3:0103: Adding scrollwheel support
[    12.372] (**) HID 04f3:0103: YAxisMapping: buttons 4 and 5
[    12.372] (**) HID 04f3:0103: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    12.372] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.1/input/input3/event3"
[    12.372] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD)
[    12.372] (**) Option "xkb_rules" "evdev"
[    12.372] (**) Option "xkb_model" "pc105"
[    12.372] (**) Option "xkb_layout" "us"
[    12.372] (EE) HID 04f3:0103: failed to initialize for relative axes.
[    12.372] (II) HID 04f3:0103: initialized for absolute axes.
[    12.372] (**) HID 04f3:0103: (accel) keeping acceleration scheme 1
[    12.372] (**) HID 04f3:0103: (accel) acceleration profile 0
[    12.372] (**) HID 04f3:0103: (accel) acceleration factor: 2.000
[    12.372] (**) HID 04f3:0103: (accel) acceleration threshold: 4
[    12.373] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event4)
[    12.373] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    12.373] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    12.373] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.373] (**) USB Optical Mouse: always reports core events
[    12.373] (**) USB Optical Mouse: Device: "/dev/input/event4"
[    12.373] (--) USB Optical Mouse: Found 3 mouse buttons
[    12.373] (--) USB Optical Mouse: Found scroll wheel(s)
[    12.373] (--) USB Optical Mouse: Found relative axes
[    12.373] (--) USB Optical Mouse: Found x and y relative axes
[    12.373] (II) USB Optical Mouse: Configuring as mouse
[    12.373] (II) USB Optical Mouse: Adding scrollwheel support
[    12.373] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    12.373] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    12.373] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input4/event4"
[    12.373] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[    12.373] (II) USB Optical Mouse: initialized for relative axes.
[    12.373] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    12.373] (**) USB Optical Mouse: (accel) acceleration profile 0
[    12.373] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    12.373] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    12.373] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    12.373] (II) No input driver/identifier specified (ignoring)
[    12.838] (II) intel(0): EDID vendor "PHL", prod id 1
[    12.838] (II) intel(0): Using EDID range info for horizontal sync
[    12.838] (II) intel(0): Using EDID range info for vertical refresh
[    12.838] (II) intel(0): Printing DDC gathered Modelines:
[    12.838] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    12.838] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    12.838] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    12.838] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    12.838] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    12.838] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    12.838] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[    12.838] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    12.838] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    12.838] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    12.838] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    12.838] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    12.838] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    12.838] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    15.662] (II) intel(0): EDID vendor "PHL", prod id 1
[    15.662] (II) intel(0): Using hsync ranges from config file
[    15.662] (II) intel(0): Using vrefresh ranges from config file
[    15.662] (II) intel(0): Printing DDC gathered Modelines:
[    15.662] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    15.662] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    15.662] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    15.662] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    15.662] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    15.662] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    15.662] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[    15.662] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    15.662] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.662] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    15.662] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    15.662] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    15.662] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    15.662] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    16.770] (II) intel(0): EDID vendor "PHL", prod id 1
[    16.770] (II) intel(0): Using hsync ranges from config file
[    16.770] (II) intel(0): Using vrefresh ranges from config file
[    16.770] (II) intel(0): Printing DDC gathered Modelines:
[    16.770] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    16.770] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    16.770] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    16.770] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    16.770] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    16.770] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    16.770] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[    16.770] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    16.770] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    16.770] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    16.770] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    16.770] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    16.770] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    16.770] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[   100.267] (II) intel(0): EDID vendor "PHL", prod id 1
[   100.267] (II) intel(0): Using hsync ranges from config file
[   100.267] (II) intel(0): Using vrefresh ranges from config file
[   100.267] (II) intel(0): Printing DDC gathered Modelines:
[   100.267] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   100.267] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   100.267] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   100.267] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   100.267] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   100.267] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   100.267] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[   100.267] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   100.267] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   100.267] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   100.267] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   100.267] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[   100.267] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[   100.267] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[   100.931] (II) intel(0): EDID vendor "PHL", prod id 1
[   100.931] (II) intel(0): Using hsync ranges from config file
[   100.931] (II) intel(0): Using vrefresh ranges from config file
[   100.931] (II) intel(0): Printing DDC gathered Modelines:
[   100.931] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   100.931] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   100.931] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   100.931] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   100.931] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   100.931] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   100.931] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[   100.931] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   100.931] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   100.931] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   100.931] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   100.931] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[   100.931] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[   100.931] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[   101.379] (II) intel(0): EDID vendor "PHL", prod id 1
[   101.379] (II) intel(0): Using hsync ranges from config file
[   101.379] (II) intel(0): Using vrefresh ranges from config file
[   101.379] (II) intel(0): Printing DDC gathered Modelines:
[   101.379] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   101.379] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   101.379] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   101.379] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   101.379] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   101.379] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   101.379] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[   101.379] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   101.379] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   101.379] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   101.379] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   101.379] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[   101.379] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[   101.379] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[   102.064] (II) intel(0): EDID vendor "PHL", prod id 1
[   102.064] (II) intel(0): Using hsync ranges from config file
[   102.064] (II) intel(0): Using vrefresh ranges from config file
[   102.064] (II) intel(0): Printing DDC gathered Modelines:
[   102.064] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   102.064] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   102.064] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   102.064] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   102.064] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   102.064] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   102.064] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[   102.064] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   102.064] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   102.064] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   102.064] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   102.064] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[   102.064] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[   102.064] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[   103.252] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[   284.623] (II) intel(0): EDID vendor "PHL", prod id 1
[   284.623] (II) intel(0): Using hsync ranges from config file
[   284.623] (II) intel(0): Using vrefresh ranges from config file
[   284.623] (II) intel(0): Printing DDC gathered Modelines:
[   284.623] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   284.623] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   284.623] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   284.623] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   284.623] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   284.623] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   284.623] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[   284.623] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   284.623] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   284.623] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   284.623] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   284.623] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[   284.623] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[   284.624] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)

```

I also tried the command you suggested:

```

$ xrandr --output VGA1 --mode 1024x768
xrandr: cannot find mode 1024x768

```

Then I realized probably I need to run this with VGA cable plugged in, so I did the mod you suggest for grub and rebooted with VGA cable plugged in. I saw something (in split screen) on the screen but then no login screen was shown (over VGA cable).
I logged in using VNC and typed again xrandr --output VGA1 --mode 1024x768. This time no error, but also nothing shown on the TV.

I just realized even the BIOS doesn't appear over VGA, so let's forget about it.

I tried changing with "xforcevesa" without nomodeset in grub and I get the flickering.

I tried changing grub with "i915.modeset=0 xforcevesa" and it actually works but the video in xbmc is still choppy.

I'm also waiting for the DVI-I to HDMI adapter, hopefully by the end of the week.

> You can override the video driver choice (HAL/udev rules?) by using xorg.conf.
can you show me an example of how the xorg.conf should be in my case? which driver do I need?

---

### Post by alfonso78 on 2012-01-10
Ah!

Now I know what I did...

> i915.modeset=0 is the Intel equivalent to nomodeset for other video cards.

from: [https://wiki.archlinux.org/index.php/Intel](https://wiki.archlinux.org/index.php/Intel)

so back to square 1.

I also tried "i915.semaphores=1" without anything else I get the flickering back... :(

then I tried with no specific instructions in grub and this xorg.conf (following [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting) ) using framebuffer but I still get the flickering!

```
# /etc/X11/xorg.conf
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fbdev"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

I tried also with this conf file, but still no luck:

```
$ cat /etc/X11/xorg.conf
Section "Device"
    Identifier "old intel stuff"
    Driver "intel"
    Option "Shadow" "True"
    Option "DRI" "false"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

so it seems it only works for me with KMS off. :(

---

### Post by alfonso78 on 2012-01-10
> **BicyclerBoy said:**
> 
You could try the different video output formats in VLC, possible something will work better.
I believe that mplayer & VLC can drive the console framebuffer directly (no X server running). This might not work on SNA.


BicyclerBoy you're golden! That was indeed a great idea. So now I can watch videos too, so more or less I can leave the situation like this for a while longer, but surely I'd love to fix the problem.

Now I run with nomodeset and xbmc using vlc as default player, but my xbmc HTTP remote control on my phone now is "broken" cause I cannot pilot VLC from a web interface as I could do with the embedded player...

my plan will be to try xserver 1.12 when it's released by xorg-edgers, but a guy with same MB and also using HDMI output on a TV told me it works for him using Debian unstable.
I'll give it a try if I manage to run it from USB and report, maybe with your help I can fix things. I'd like to stay on Ubuntu if possible.

and the DVI-HDMI adapter will be here any day now.

thank you!

---

### Post by BicyclerBoy on 2012-01-10
Glad something worked..
which video output mode is usable (with VLC) ?

The VGA xrandr stuff:
forgot the newmode stuff..
```

$ cvt 1024 768 60
(returns video mode info for the below)
$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
$ xrandr --addmode VGA1 "1024x768_60.00"
$ xrandr --output VGA1 --mode "1024x768_60.00"

```
The default position of the new virtual VGA1 screen may be positioned 'below' the existing screen.
xrandr --output VGA1 --right-of HDMI2

---

### Post by alfonso78 on 2012-01-10
> which video output mode is usable (with VLC) ?
how to check?

> The VGA xrandr stuff:
forgot the newmode stuff..
```

$ cvt 1024 768 60
(returns video mode info for the below)
$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
$ xrandr --addmode VGA1 "1024x768_60.00"
$ xrandr --output VGA1 --mode "1024x768_60.00"

```
The default position of the new virtual VGA1 screen may be positioned 'below' the existing screen.
xrandr --output VGA1 --right-of HDMI2
sorry, but should I run all these commands in order? and what should happen? should I run the commands without nomodeset using the VGA cable?

thanks.

I spent hours trying to install debian wheezy on an USB pen to test (someone told me my MB works ok with wheezy) but I didn't manage...

---

### Post by BicyclerBoy on 2012-01-11
The terminal commands allow you to turn on the VGA output & set the resolution..I do not think VESA supports xrandr/randr.

Using intel driver (remove nomodeset) & X screen running over HDMI connection to TV...
If you want to try the VGA cable (connected to the same TV by VGA) then the last 3 of 4 commands will turn on the VGA1 output with 1024x768 60p.

The first of the 4 commands is just to show how the modeline was generated.

So all that was just an expt to see if the VGA output works without screen 'distortion'.

You should be able to install the latest kernel from ubuntu kernel devs ppa..you do not need to change distributions..
This may not be so easy..I can find only ppa packages for lucid..

There are the debian packages here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by alfonso78 on 2012-01-13
Hi,

so I received the DVI->HDMI adapter and I reboot without nomodeset and unfortunately the TV is still showing half screen twice plus flickering. So I switched off and connected over VGA (and HDMI at the same time) with nomodeset.

Now I'm running these commands from X over vnc (since VGA output is not showing anything).

```
$ cvt 1024 768 60
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
```

Then in the same session I executed:

```
$ xrandr --newmode "1024x768_60.00" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
$ xrandr --addmode VGA1 "1024x768_60.00"
$ xrandr --output VGA1 --mode "1024x768_60.00"
```

but nothing is shown on the TV (I double checked that the TV is taking input from VGA)

so apparently I have no solution in sight...

> You should be able to install the latest kernel from ubuntu kernel devs ppa

I did, I actually now run 3.2.0-7-generic-pae (from ppa:ptn107/ppa). The only difference I saw was that the old kernel showed twice the upper screen WITHOUT flickering while the new kernel added flickering...

> you do not need to change distributions..

the things is I found a guy on internet with my same MB who solved his video problems with debian. Maybe they compile X or the kernel in a different way that solves the problem. I'd like to check that. I'll try now to do it...

thanks, and feel free to share any new idea...

---

### Post by BicyclerBoy on 2012-01-14
I doubt xrandr will work with VESA driver (nomodeset).
VESA may not support multiple screens.

I'm not sure how X over VNC will affect this..have you used the gnome remote desktop interface?

You can connect & use/view the HDMI connected screen & type in those commands in a terminal (window in the X server GUI desktop).
After xrandr --prop
 shows both the HDMI & the VGA connected (activated), then switch the input on the TV to VGA.

Does this problem only occur with this low resolution (netbook like) screen?
Maybe this is a bug that has just never been noticed..

---

### Post by alfonso78 on 2012-01-14
> **BicyclerBoy said:**
> I doubt xrandr will work with VESA driver (nomodeset).
VESA may not support multiple screens.


Hi and my apologies!

I meant I run all the commands WITHOUT nomodeset... In fact the screen was flickering in HDMI, so there was no nomodeset.

> I'm not sure how X over VNC will affect this..have you used the gnome remote desktop interface?
I do not have an other linux machine. My laptop runs windows.
I can only launch commands over VNC or over SSH.

> Does this problem only occur with this low resolution (netbook like) screen?
Maybe this is a bug that has just never been noticed..

That's a good idea. In fact I was thinking about something similar.
I don't have an other monitor. I'll try to check on an other screen when I have the chance.

---

### Post by alfonso78 on 2012-01-15
Hi,

I've been trying for ages but I can't manage to install debian wheezy on a usb pendrive. So I can't test my MB and TV with a different build.
On the other side I received the Xorg.0.log from the guy that has my same motherboard and has managed to solve his problems (kernel 3.1.0-1-amd64 on wheezy).

I wonder if this can help you find any clue to help my case...

The only difference is that I have an i3-2130 (onboard HD 2000) and he has an i5-2500k (onboard HD 3000)

thank you!

this is his grub:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

and this is his Xorg.0.log:

```
[    34.257] 
X.Org X Server 1.11.2.902 (1.11.3 RC 2)
Release Date: 2011-12-09
[    34.257] X Protocol Version 11, Revision 0
[    34.257] Build Operating System: Linux 3.1.0-1-amd64 x86_64 Debian
[    34.257] Current Operating System: Linux kelvin 3.1.0-1-amd64 #1 SMP Tue Jan 10 05:01:58 UTC 2012 x86_64
[    34.257] Kernel command line: BOOT_IMAGE=/vmlinuz-3.1.0-1-amd64 root=/dev/mapper/kelvin-root ro quiet
[    34.257] Build Date: 10 December 2011  09:55:45PM
[    34.257] xorg-server 2:1.11.2.902-1 (Cyril Brulebois <kibi@debian.org>) 
[    34.257] Current version of pixman: 0.24.0
[    34.257] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    34.257] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    34.257] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 15 12:17:58 2012
[    34.279] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    34.280] (==) No Layout section.  Using the first Screen section.
[    34.280] (==) No screen section available. Using defaults.
[    34.280] (**) |-->Screen "Default Screen Section" (0)
[    34.280] (**) |   |-->Monitor "<default monitor>"
[    34.280] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    34.280] (==) Automatically adding devices
[    34.280] (==) Automatically enabling devices
[    34.280] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    34.280] 	Entry deleted from font path.
[    34.280] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    34.280] (==) ModulePath set to "/usr/lib/xorg/modules"
[    34.280] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    34.280] (II) Loader magic: 0x7f7c81ebfae0
[    34.280] (II) Module ABI versions:
[    34.280] 	X.Org ANSI C Emulation: 0.4
[    34.280] 	X.Org Video Driver: 11.0
[    34.280] 	X.Org XInput driver : 13.0
[    34.280] 	X.Org Server Extension : 6.0
[    34.281] (--) PCI:*(0:0:2:0) 8086:0112:19da:a166 rev 9, Mem @ 0xfe000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
[    34.281] (II) Open ACPI successful (/var/run/acpid.socket)
[    34.281] (II) LoadModule: "extmod"
[    34.369] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    34.370] (II) Module extmod: vendor="X.Org Foundation"
[    34.370] 	compiled for 1.11.2.902, module version = 1.0.0
[    34.370] 	Module class: X.Org Server Extension
[    34.370] 	ABI class: X.Org Server Extension, version 6.0
[    34.370] (II) Loading extension SELinux
[    34.370] (II) Loading extension MIT-SCREEN-SAVER
[    34.370] (II) Loading extension XFree86-VidModeExtension
[    34.370] (II) Loading extension XFree86-DGA
[    34.370] (II) Loading extension DPMS
[    34.370] (II) Loading extension XVideo
[    34.370] (II) Loading extension XVideo-MotionCompensation
[    34.370] (II) Loading extension X-Resource
[    34.370] (II) LoadModule: "dbe"
[    34.370] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    34.370] (II) Module dbe: vendor="X.Org Foundation"
[    34.370] 	compiled for 1.11.2.902, module version = 1.0.0
[    34.370] 	Module class: X.Org Server Extension
[    34.370] 	ABI class: X.Org Server Extension, version 6.0
[    34.370] (II) Loading extension DOUBLE-BUFFER
[    34.370] (II) LoadModule: "glx"
[    34.370] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    34.370] (II) Module glx: vendor="X.Org Foundation"
[    34.370] 	compiled for 1.11.2.902, module version = 1.0.0
[    34.370] 	ABI class: X.Org Server Extension, version 6.0
[    34.370] (==) AIGLX enabled
[    34.370] (II) Loading extension GLX
[    34.370] (II) LoadModule: "record"
[    34.371] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    34.371] (II) Module record: vendor="X.Org Foundation"
[    34.371] 	compiled for 1.11.2.902, module version = 1.13.0
[    34.371] 	Module class: X.Org Server Extension
[    34.371] 	ABI class: X.Org Server Extension, version 6.0
[    34.371] (II) Loading extension RECORD
[    34.371] (II) LoadModule: "dri"
[    34.371] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    34.371] (II) Module dri: vendor="X.Org Foundation"
[    34.371] 	compiled for 1.11.2.902, module version = 1.0.0
[    34.371] 	ABI class: X.Org Server Extension, version 6.0
[    34.371] (II) Loading extension XFree86-DRI
[    34.371] (II) LoadModule: "dri2"
[    34.371] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    34.371] (II) Module dri2: vendor="X.Org Foundation"
[    34.371] 	compiled for 1.11.2.902, module version = 1.2.0
[    34.371] 	ABI class: X.Org Server Extension, version 6.0
[    34.371] (II) Loading extension DRI2
[    34.371] (==) Matched intel as autoconfigured driver 0
[    34.371] (==) Matched vesa as autoconfigured driver 1
[    34.371] (==) Matched fbdev as autoconfigured driver 2
[    34.371] (==) Assigned the driver to the xf86ConfigLayout
[    34.371] (II) LoadModule: "intel"
[    34.371] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    34.371] (II) Module intel: vendor="X.Org Foundation"
[    34.371] 	compiled for 1.11.1.902, module version = 2.17.0
[    34.371] 	Module class: X.Org Video Driver
[    34.371] 	ABI class: X.Org Video Driver, version 11.0
[    34.372] (II) LoadModule: "vesa"
[    34.372] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    34.372] (II) Module vesa: vendor="X.Org Foundation"
[    34.372] 	compiled for 1.11.0, module version = 2.3.0
[    34.372] 	Module class: X.Org Video Driver
[    34.372] 	ABI class: X.Org Video Driver, version 11.0
[    34.372] (II) LoadModule: "fbdev"
[    34.372] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    34.372] (II) Module fbdev: vendor="X.Org Foundation"
[    34.372] 	compiled for 1.11.0, module version = 0.4.2
[    34.372] 	ABI class: X.Org Video Driver, version 11.0
[    34.372] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    34.372] (II) VESA: driver for VESA chipsets: vesa
[    34.372] (II) FBDEV: driver for framebuffer: fbdev
[    34.372] (++) using VT number 7

[    34.379] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    34.379] (WW) Falling back to old probe method for vesa
[    34.379] (WW) Falling back to old probe method for fbdev
[    34.379] (II) Loading sub module "fbdevhw"
[    34.379] (II) LoadModule: "fbdevhw"
[    34.379] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    34.379] (II) Module fbdevhw: vendor="X.Org Foundation"
[    34.379] 	compiled for 1.11.2.902, module version = 0.0.2
[    34.379] 	ABI class: X.Org Video Driver, version 11.0
[    34.379] drmOpenDevice: node name is /dev/dri/card0
[    34.379] drmOpenDevice: open result is 9, (OK)
[    34.379] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    34.379] drmOpenDevice: node name is /dev/dri/card0
[    34.379] drmOpenDevice: open result is 9, (OK)
[    34.379] drmOpenByBusid: drmOpenMinor returns 9
[    34.379] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    34.379] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    34.379] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    34.379] (==) intel(0): RGB weight 888
[    34.379] (==) intel(0): Default visual is TrueColor
[    34.379] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Desktop (GT2)
[    34.379] (--) intel(0): Chipset: "Sandybridge Desktop (GT2)"
[    34.379] (**) intel(0): Relaxed fencing enabled
[    34.379] (**) intel(0): Wait on SwapBuffers? enabled
[    34.379] (**) intel(0): Triple buffering? enabled
[    34.379] (**) intel(0): Framebuffer tiled
[    34.379] (**) intel(0): Pixmaps tiled
[    34.379] (**) intel(0): 3D buffers tiled
[    34.379] (**) intel(0): SwapBuffers wait enabled
[    34.379] (==) intel(0): video overlay key set to 0x101fe
[    34.379] (II) intel(0): Output VGA1 has no monitor section
[    34.403] (II) intel(0): Output HDMI1 has no monitor section
[    34.448] (II) intel(0): Output DP1 has no monitor section
[    34.692] (II) intel(0): Output HDMI2 has no monitor section
[    34.946] (II) intel(0): Output HDMI3 has no monitor section
[    34.992] (II) intel(0): Output DP2 has no monitor section
[    35.040] (II) intel(0): Output DP3 has no monitor section
[    35.040] (II) intel(0): EDID for output VGA1
[    35.063] (II) intel(0): EDID for output HDMI1
[    35.108] (II) intel(0): EDID for output DP1
[    35.351] (II) intel(0): EDID for output HDMI2
[    35.351] (II) intel(0): Manufacturer: SNY  Model: a401  Serial#: 16843009
[    35.351] (II) intel(0): Year: 2009  Week: 1
[    35.351] (II) intel(0): EDID Version: 1.3
[    35.351] (II) intel(0): Digital Display Input
[    35.351] (II) intel(0): Max Image Size [cm]: horiz.: 160  vert.: 90
[    35.351] (II) intel(0): Gamma: 2.20
[    35.351] (II) intel(0): No DPMS capabilities specified
[    35.351] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    35.351] (II) intel(0): First detailed timing is preferred mode
[    35.351] (II) intel(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
[    35.351] (II) intel(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
[    35.351] (II) intel(0): Supported established timings:
[    35.351] (II) intel(0): 640x480@60Hz
[    35.351] (II) intel(0): 800x600@60Hz
[    35.351] (II) intel(0): 1024x768@60Hz
[    35.351] (II) intel(0): Manufacturer's mask: 0
[    35.351] (II) intel(0): Supported standard timings:
[    35.351] (II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    35.351] (II) intel(0): Supported detailed timing:
[    35.351] (II) intel(0): clock: 148.5 MHz   Image Size:  1600 x 900 mm
[    35.351] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    35.351] (II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    35.351] (II) intel(0): Supported detailed timing:
[    35.351] (II) intel(0): clock: 74.2 MHz   Image Size:  1600 x 900 mm
[    35.351] (II) intel(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    35.351] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    35.351] (II) intel(0): Monitor name: SONY TV
[    35.351] (II) intel(0): Ranges: V min: 48 V max: 62 Hz, H min: 14 H max: 70 kHz, PixClock max 155 MHz
[    35.351] (II) intel(0): Supported detailed timing:
[    35.351] (II) intel(0): clock: 148.5 MHz   Image Size:  1600 x 900 mm
[    35.351] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    35.351] (II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    35.351] (II) intel(0): Supported detailed timing:
[    35.351] (II) intel(0): clock: 74.2 MHz   Image Size:  1600 x 900 mm
[    35.351] (II) intel(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[    35.351] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    35.351] (II) intel(0): Supported detailed timing:
[    35.351] (II) intel(0): clock: 74.2 MHz   Image Size:  1600 x 900 mm
[    35.351] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    35.351] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    35.351] (II) intel(0): Supported detailed timing:
[    35.351] (II) intel(0): clock: 74.2 MHz   Image Size:  1600 x 900 mm
[    35.351] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    35.351] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    35.351] (II) intel(0): Number of EDID sections to follow: 1
[    35.351] (II) intel(0): EDID (in hex):
[    35.351] (II) intel(0): 	00ffffffffffff004dd901a401010101
[    35.351] (II) intel(0): 	0113010380a05a780a0dc9a057479827
[    35.351] (II) intel(0): 	12484c21080081800101010101010101
[    35.351] (II) intel(0): 	010101010101023a801871382d40582c
[    35.351] (II) intel(0): 	450040846300001e011d007251d01e20
[    35.352] (II) intel(0): 	6e28550040846300001e000000fc0053
[    35.352] (II) intel(0): 	4f4e592054560a2020202020000000fd
[    35.352] (II) intel(0): 	00303e0e460f000a2020202020200109
[    35.352] (II) intel(0): 	02032cf0501f10140513041211161503
[    35.352] (II) intel(0): 	02070601202609070715075083010000
[    35.352] (II) intel(0): 	68030c00300080000fe2007b023a80d0
[    35.352] (II) intel(0): 	72382d40102c458040846300001e011d
[    35.352] (II) intel(0): 	00bc52d01e20b828554040846300001e
[    35.352] (II) intel(0): 	011d8018711c1620582c250040846300
[    35.352] (II) intel(0): 	009e011d80d0721c1620102c25804084
[    35.352] (II) intel(0): 	6300009e000000000000000000000053
[    35.352] (II) intel(0): Printing probed modes for output HDMI2
[    35.352] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    35.352] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    35.352] (II) intel(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    35.352] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    35.352] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    35.352] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    35.375] (II) intel(0): EDID for output HDMI3
[    35.420] (II) intel(0): EDID for output DP2
[    35.468] (II) intel(0): EDID for output DP3
[    35.468] (II) intel(0): Output VGA1 disconnected
[    35.468] (II) intel(0): Output HDMI1 disconnected
[    35.468] (II) intel(0): Output DP1 disconnected
[    35.468] (II) intel(0): Output HDMI2 connected
[    35.468] (II) intel(0): Output HDMI3 disconnected
[    35.468] (II) intel(0): Output DP2 disconnected
[    35.468] (II) intel(0): Output DP3 disconnected
[    35.468] (II) intel(0): Using exact sizes for initial modes
[    35.468] (II) intel(0): Output HDMI2 using initial mode 1920x1080
[    35.468] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    35.468] (II) intel(0): Kernel page flipping support detected, enabling
[    35.468] (==) intel(0): DPI set to (96, 96)
[    35.468] (II) Loading sub module "fb"
[    35.468] (II) LoadModule: "fb"
[    35.468] (II) Loading /usr/lib/xorg/modules/libfb.so
[    35.468] (II) Module fb: vendor="X.Org Foundation"
[    35.468] 	compiled for 1.11.2.902, module version = 1.0.0
[    35.468] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    35.468] (II) Loading sub module "dri2"
[    35.468] (II) LoadModule: "dri2"
[    35.468] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    35.468] (II) Module dri2: vendor="X.Org Foundation"
[    35.468] 	compiled for 1.11.2.902, module version = 1.2.0
[    35.468] 	ABI class: X.Org Server Extension, version 6.0
[    35.468] (II) UnloadModule: "vesa"
[    35.468] (II) Unloading vesa
[    35.468] (II) UnloadModule: "fbdev"
[    35.468] (II) Unloading fbdev
[    35.468] (II) UnloadModule: "fbdevhw"
[    35.468] (II) Unloading fbdevhw
[    35.468] (==) Depth 24 pixmap format is 32 bpp
[    35.468] (II) intel(0): [DRI2] Setup complete
[    35.468] (II) intel(0): [DRI2]   DRI driver: i965
[    35.468] (II) intel(0): Allocated new frame buffer 1920x1080 stride 7680, tiled
[    35.469] (II) UXA(0): Driver registered support for the following operations:
[    35.469] (II)         solid
[    35.469] (II)         copy
[    35.469] (II)         composite (RENDER acceleration)
[    35.469] (II)         put_image
[    35.469] (II)         get_image
[    35.469] (==) intel(0): Backing store disabled
[    35.469] (==) intel(0): Silken mouse enabled
[    35.469] (II) intel(0): Initializing HW Cursor
[    35.528] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    35.528] (==) intel(0): DPMS enabled
[    35.528] (==) intel(0): Intel XvMC decoder enabled
[    35.528] (II) intel(0): Set up textured video
[    35.528] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    35.528] (II) intel(0): direct rendering: DRI2 Enabled
[    35.528] (==) intel(0): hotplug detection: "enabled"
[    35.528] (--) RandR disabled
[    35.528] (II) Initializing built-in extension Generic Event Extension
[    35.528] (II) Initializing built-in extension SHAPE
[    35.528] (II) Initializing built-in extension MIT-SHM
[    35.528] (II) Initializing built-in extension XInputExtension
[    35.528] (II) Initializing built-in extension XTEST
[    35.528] (II) Initializing built-in extension BIG-REQUESTS
[    35.528] (II) Initializing built-in extension SYNC
[    35.528] (II) Initializing built-in extension XKEYBOARD
[    35.528] (II) Initializing built-in extension XC-MISC
[    35.528] (II) Initializing built-in extension SECURITY
[    35.528] (II) Initializing built-in extension XINERAMA
[    35.528] (II) Initializing built-in extension XFIXES
[    35.528] (II) Initializing built-in extension RENDER
[    35.528] (II) Initializing built-in extension RANDR
[    35.528] (II) Initializing built-in extension COMPOSITE
[    35.528] (II) Initializing built-in extension DAMAGE
[    35.528] (II) SELinux: Disabled on system
[    35.532] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    35.532] (II) AIGLX: enabled GLX_INTEL_swap_event
[    35.532] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    35.532] (II) AIGLX: enabled GLX_SGI_make_current_read
[    35.532] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    35.533] (II) AIGLX: Loaded and initialized i965
[    35.533] (II) GLX: Initialized DRI2 GL provider for screen 0
[    35.533] (II) intel(0): Setting screen physical size to 508 x 285
[    35.584] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    35.584] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    35.584] (II) LoadModule: "evdev"
[    35.584] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.584] (II) Module evdev: vendor="X.Org Foundation"
[    35.584] 	compiled for 1.11.0, module version = 2.6.0
[    35.584] 	Module class: X.Org XInput Driver
[    35.584] 	ABI class: X.Org XInput driver, version 13.0
[    35.584] (II) Using input driver 'evdev' for 'Power Button'
[    35.584] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.584] (**) Power Button: always reports core events
[    35.584] (**) Power Button: Device: "/dev/input/event3"
[    35.584] (--) Power Button: Found keys
[    35.584] (II) Power Button: Configuring as keyboard
[    35.584] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    35.584] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    35.584] (**) Option "xkb_rules" "evdev"
[    35.584] (**) Option "xkb_model" "pc105"
[    35.584] (**) Option "xkb_layout" "us"
[    35.584] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    35.584] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    35.584] (II) Using input driver 'evdev' for 'Power Button'
[    35.585] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.585] (**) Power Button: always reports core events
[    35.585] (**) Power Button: Device: "/dev/input/event2"
[    35.585] (--) Power Button: Found keys
[    35.585] (II) Power Button: Configuring as keyboard
[    35.585] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2"
[    35.585] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    35.585] (**) Option "xkb_rules" "evdev"
[    35.585] (**) Option "xkb_model" "pc105"
[    35.585] (**) Option "xkb_layout" "us"
[    35.585] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP (/dev/input/event5)
[    35.585] (II) No input driver/identifier specified (ignoring)
[    35.585] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP (/dev/input/event6)
[    35.585] (II) No input driver/identifier specified (ignoring)
[    35.585] (II) config/udev: Adding input device RF-Dongle (/dev/input/event0)
[    35.585] (**) RF-Dongle: Applying InputClass "evdev keyboard catchall"
[    35.585] (II) Using input driver 'evdev' for 'RF-Dongle'
[    35.585] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.585] (**) RF-Dongle: always reports core events
[    35.585] (**) RF-Dongle: Device: "/dev/input/event0"
[    35.585] (--) RF-Dongle: Found keys
[    35.585] (II) RF-Dongle: Configuring as keyboard
[    35.585] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.3/4-1.3:1.0/input/input0/event0"
[    35.585] (II) XINPUT: Adding extended input device "RF-Dongle" (type: KEYBOARD, id 8)
[    35.585] (**) Option "xkb_rules" "evdev"
[    35.585] (**) Option "xkb_model" "pc105"
[    35.585] (**) Option "xkb_layout" "us"
[    35.586] (II) config/udev: Adding input device RF-Dongle (/dev/input/event1)
[    35.586] (**) RF-Dongle: Applying InputClass "evdev pointer catchall"
[    35.586] (**) RF-Dongle: Applying InputClass "evdev keyboard catchall"
[    35.586] (II) Using input driver 'evdev' for 'RF-Dongle'
[    35.586] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.586] (**) RF-Dongle: always reports core events
[    35.586] (**) RF-Dongle: Device: "/dev/input/event1"
[    35.586] (--) RF-Dongle: Found 9 mouse buttons
[    35.586] (--) RF-Dongle: Found scroll wheel(s)
[    35.586] (--) RF-Dongle: Found relative axes
[    35.586] (--) RF-Dongle: Found x and y relative axes
[    35.586] (--) RF-Dongle: Found absolute axes
[    35.586] (--) RF-Dongle: Found keys
[    35.586] (II) RF-Dongle: Configuring as mouse
[    35.586] (II) RF-Dongle: Configuring as keyboard
[    35.586] (II) RF-Dongle: Adding scrollwheel support
[    35.586] (**) RF-Dongle: YAxisMapping: buttons 4 and 5
[    35.586] (**) RF-Dongle: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    35.586] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.3/4-1.3:1.1/input/input1/event1"
[    35.586] (II) XINPUT: Adding extended input device "RF-Dongle" (type: KEYBOARD, id 9)
[    35.586] (**) Option "xkb_rules" "evdev"
[    35.586] (**) Option "xkb_model" "pc105"
[    35.586] (**) Option "xkb_layout" "us"
[    35.586] (II) RF-Dongle: initialized for relative axes.
[    35.586] (WW) RF-Dongle: ignoring absolute axes.
[    35.586] (**) RF-Dongle: (accel) keeping acceleration scheme 1
[    35.586] (**) RF-Dongle: (accel) acceleration profile 0
[    35.586] (**) RF-Dongle: (accel) acceleration factor: 2.000
[    35.586] (**) RF-Dongle: (accel) acceleration threshold: 4
[    35.586] (II) config/udev: Adding input device RF-Dongle (/dev/input/mouse0)
[    35.586] (II) No input driver/identifier specified (ignoring)
[    35.587] (II) config/udev: Adding input device PC Speaker (/dev/input/event4)
[    35.587] (II) No input driver/identifier specified (ignoring)
[    35.902] (II) intel(0): EDID vendor "SNY", prod id 41985
[    35.902] (II) intel(0): Using EDID range info for horizontal sync
[    35.902] (II) intel(0): Using EDID range info for vertical refresh
[    35.902] (II) intel(0): Printing DDC gathered Modelines:
[    35.902] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    35.902] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    35.902] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    35.902] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    35.902] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    35.903] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    35.903] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    35.903] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    35.903] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    35.903] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    35.903] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    35.903] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    35.903] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    35.903] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    35.903] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    35.903] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    35.903] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    35.903] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    36.808] (II) intel(0): EDID vendor "SNY", prod id 41985
[    36.808] (II) intel(0): Using hsync ranges from config file
[    36.808] (II) intel(0): Using vrefresh ranges from config file
[    36.808] (II) intel(0): Printing DDC gathered Modelines:
[    36.808] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    36.808] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    36.808] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    36.808] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    36.808] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    36.808] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    36.808] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    36.808] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    36.808] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    36.808] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    36.808] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    36.808] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    36.808] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    36.808] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    36.808] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    36.808] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    36.808] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    36.808] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    37.668] (II) intel(0): EDID vendor "SNY", prod id 41985
[    37.668] (II) intel(0): Using hsync ranges from config file
[    37.668] (II) intel(0): Using vrefresh ranges from config file
[    37.668] (II) intel(0): Printing DDC gathered Modelines:
[    37.668] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    37.668] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    37.668] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    37.668] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    37.668] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    37.668] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    37.668] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    37.668] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    37.668] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    37.668] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    37.668] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    37.668] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    37.668] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    37.668] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    37.668] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    37.668] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    37.668] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    37.668] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    38.710] (II) intel(0): EDID vendor "SNY", prod id 41985
[    38.851] (II) intel(0): Using hsync ranges from config file
[    38.851] (II) intel(0): Using vrefresh ranges from config file
[    38.851] (II) intel(0): Printing DDC gathered Modelines:
[    38.851] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    38.851] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    38.851] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    38.851] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    38.851] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    38.851] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    38.851] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    38.851] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    38.851] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    38.851] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    38.851] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    38.851] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    38.851] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    38.851] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    38.851] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    38.851] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    38.851] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    38.851] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    39.283] (II) intel(0): EDID vendor "SNY", prod id 41985
[    39.385] (II) intel(0): Using hsync ranges from config file
[    39.385] (II) intel(0): Using vrefresh ranges from config file
[    39.385] (II) intel(0): Printing DDC gathered Modelines:
[    39.385] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    39.385] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    39.385] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    39.385] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    39.385] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    39.385] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    39.385] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    39.385] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    39.385] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    39.385] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    39.385] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    39.385] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    39.385] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    39.385] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    39.385] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    39.385] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    39.385] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    39.385] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    39.818] (II) intel(0): EDID vendor "SNY", prod id 41985
[    39.818] (II) intel(0): Using hsync ranges from config file
[    39.818] (II) intel(0): Using vrefresh ranges from config file
[    39.818] (II) intel(0): Printing DDC gathered Modelines:
[    39.818] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    39.818] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    39.818] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    39.818] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    39.818] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    39.818] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    39.818] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    39.818] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    39.818] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    39.818] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    39.818] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    39.818] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    39.818] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    39.818] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    39.818] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    39.818] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    39.818] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    39.818] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    40.251] (II) intel(0): EDID vendor "SNY", prod id 41985
[    40.251] (II) intel(0): Using hsync ranges from config file
[    40.251] (II) intel(0): Using vrefresh ranges from config file
[    40.251] (II) intel(0): Printing DDC gathered Modelines:
[    40.251] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    40.251] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    40.251] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    40.251] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    40.251] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    40.251] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    40.251] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    40.251] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    40.251] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    40.251] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    40.251] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    40.251] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    40.251] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    40.251] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    40.251] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    40.251] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    40.251] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    40.251] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    47.924] (II) intel(0): EDID vendor "SNY", prod id 41985
[    47.924] (II) intel(0): Using hsync ranges from config file
[    47.924] (II) intel(0): Using vrefresh ranges from config file
[    47.924] (II) intel(0): Printing DDC gathered Modelines:
[    47.924] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    47.924] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    47.924] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    47.924] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    47.924] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    47.924] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    47.924] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    47.924] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    47.924] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    47.924] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    47.924] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    47.924] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    47.924] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    47.924] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    47.924] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    47.924] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    47.924] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    47.924] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    78.615] (II) intel(0): EDID vendor "SNY", prod id 41985
[    78.615] (II) intel(0): Using hsync ranges from config file
[    78.615] (II) intel(0): Using vrefresh ranges from config file
[    78.615] (II) intel(0): Printing DDC gathered Modelines:
[    78.615] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    78.615] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    78.615] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    78.615] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    78.615] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    78.615] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    78.615] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    78.615] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    78.615] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    78.615] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    78.615] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    78.615] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    78.615] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    78.615] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    78.615] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    78.615] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    78.615] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    78.615] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    79.043] (II) intel(0): EDID vendor "SNY", prod id 41985
[    79.043] (II) intel(0): Using hsync ranges from config file
[    79.043] (II) intel(0): Using vrefresh ranges from config file
[    79.043] (II) intel(0): Printing DDC gathered Modelines:
[    79.043] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    79.043] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    79.043] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    79.043] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    79.043] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    79.043] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    79.043] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    79.043] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    79.043] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    79.043] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    79.043] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    79.043] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    79.043] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    79.043] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    79.043] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    79.043] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    79.043] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    79.043] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    80.563] (II) intel(0): EDID vendor "SNY", prod id 41985
[    80.563] (II) intel(0): Using hsync ranges from config file
[    80.563] (II) intel(0): Using vrefresh ranges from config file
[    80.563] (II) intel(0): Printing DDC gathered Modelines:
[    80.563] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    80.563] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    80.563] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    80.563] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    80.563] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    80.563] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    80.563] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    80.563] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    80.563] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    80.563] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    80.563] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    80.563] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    80.563] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    80.563] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    80.563] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    80.563] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    80.563] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    80.563] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    80.994] (II) intel(0): EDID vendor "SNY", prod id 41985
[    80.994] (II) intel(0): Using hsync ranges from config file
[    80.995] (II) intel(0): Using vrefresh ranges from config file
[    80.995] (II) intel(0): Printing DDC gathered Modelines:
[    80.995] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    80.995] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    80.995] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    80.995] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    80.995] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    80.995] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    80.995] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    80.995] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    80.995] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    80.995] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    80.995] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    80.995] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    80.995] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    80.995] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    80.995] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    80.995] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    80.995] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    80.995] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    81.427] (II) intel(0): EDID vendor "SNY", prod id 41985
[    81.427] (II) intel(0): Using hsync ranges from config file
[    81.427] (II) intel(0): Using vrefresh ranges from config file
[    81.427] (II) intel(0): Printing DDC gathered Modelines:
[    81.427] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    81.427] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    81.427] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    81.427] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    81.427] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    81.427] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    81.427] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    81.427] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    81.427] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    81.427] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    81.427] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    81.427] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    81.427] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    81.427] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    81.427] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    81.427] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    81.427] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    81.427] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    99.487] (II) intel(0): EDID vendor "SNY", prod id 41985
[    99.487] (II) intel(0): Using hsync ranges from config file
[    99.487] (II) intel(0): Using vrefresh ranges from config file
[    99.487] (II) intel(0): Printing DDC gathered Modelines:
[    99.487] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    99.487] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    99.487] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    99.487] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    99.487] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    99.487] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    99.487] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    99.487] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    99.487] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    99.487] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    99.487] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    99.487] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    99.487] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    99.487] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    99.487] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    99.487] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    99.487] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    99.487] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   101.330] (II) intel(0): EDID vendor "SNY", prod id 41985
[   101.331] (II) intel(0): Using hsync ranges from config file
[   101.331] (II) intel(0): Using vrefresh ranges from config file
[   101.331] (II) intel(0): Printing DDC gathered Modelines:
[   101.331] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   101.331] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   101.331] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   101.331] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   101.331] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   101.331] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   101.331] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   101.331] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   101.331] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   101.331] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   101.331] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   101.331] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   101.331] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[   101.331] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   101.331] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[   101.331] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   101.331] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[   101.331] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)

```

---

### Post by alfonso78 on 2012-01-15
Terrible terrible news... ;(

I finally managed to have a working USB pendrive for Debian wheezy (kernel 3.1.0-1-686-pae and X 1.11.2.902) and the screen is also split! :(

only difference is that it's not flickering (as it is now under ubuntu when I boot from Ubuntu without nomodeset with kernel 3.2.0-7-generic-pae and X 1.10.4).

so it's either my low resolution (hence I need to change TV) or a faulty MB (I doubt it).

I will wait for xorg-edgers to release xserver 1.12 this week and test that.

Bummer.

just for the record, the debian Xorg.0.log:

```
$ cat /var/log/Xorg.0.log
[    87.641]
X.Org X Server 1.11.2.902 (1.11.3 RC 2)
Release Date: 2011-12-09
[    87.641] X Protocol Version 11, Revision 0
[    87.641] Build Operating System: Linux 2.6.32-5-686-bigmem i686 Debian
[    87.641] Current Operating System: Linux debian 3.1.0-1-686-pae #1 SMP Tue Jan 10 05:42:54 UTC 2012 i686
[    87.641] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.1.0-1-686-pae root=UUID=f6cd3aa6-c683-4750-b750-5db71d2a1ab9 ro quiet
[    87.641] Build Date: 11 December 2011  11:26:25AM
[    87.641] xorg-server 2:1.11.2.902-1 (Cyril Brulebois <kibi@debian.org>)
[    87.641] Current version of pixman: 0.24.0
[    87.641]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    87.641] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    87.641] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 16 01:00:51 2012
[    87.641] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    87.642] (==) No Layout section.  Using the first Screen section.
[    87.642] (==) No screen section available. Using defaults.
[    87.642] (**) |-->Screen "Default Screen Section" (0)
[    87.642] (**) |   |-->Monitor "<default monitor>"
[    87.642] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    87.642] (==) Automatically adding devices
[    87.642] (==) Automatically enabling devices
[    87.642] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    87.642]    Entry deleted from font path.
[    87.642] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    87.642]    Entry deleted from font path.
[    87.642] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        built-ins
[    87.642] (==) ModulePath set to "/usr/lib/xorg/modules"
[    87.642] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    87.642] (II) Loader magic: 0xb78a7580
[    87.642] (II) Module ABI versions:
[    87.642]    X.Org ANSI C Emulation: 0.4
[    87.642]    X.Org Video Driver: 11.0
[    87.642]    X.Org XInput driver : 13.0
[    87.642]    X.Org Server Extension : 6.0
[    87.642] (--) PCI:*(0:0:2:0) 8086:0102:19da:a166 rev 9, Mem @ 0xfe000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
[    87.642] (II) Open ACPI successful (/var/run/acpid.socket)
[    87.642] (II) LoadModule: "extmod"
[    87.643] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    87.643] (II) Module extmod: vendor="X.Org Foundation"
[    87.643]    compiled for 1.11.2.902, module version = 1.0.0
[    87.643]    Module class: X.Org Server Extension
[    87.643]    ABI class: X.Org Server Extension, version 6.0
[    87.643] (II) Loading extension SELinux
[    87.643] (II) Loading extension MIT-SCREEN-SAVER
[    87.643] (II) Loading extension XFree86-VidModeExtension
[    87.643] (II) Loading extension XFree86-DGA
[    87.643] (II) Loading extension DPMS
[    87.643] (II) Loading extension XVideo
[    87.643] (II) Loading extension XVideo-MotionCompensation
[    87.643] (II) Loading extension X-Resource
[    87.643] (II) LoadModule: "dbe"
[    87.643] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    87.643] (II) Module dbe: vendor="X.Org Foundation"
[    87.643]    compiled for 1.11.2.902, module version = 1.0.0
[    87.643]    Module class: X.Org Server Extension
[    87.643]    ABI class: X.Org Server Extension, version 6.0
[    87.643] (II) Loading extension DOUBLE-BUFFER
[    87.643] (II) LoadModule: "glx"
[    87.643] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    87.643] (II) Module glx: vendor="X.Org Foundation"
[    87.643]    compiled for 1.11.2.902, module version = 1.0.0
[    87.643]    ABI class: X.Org Server Extension, version 6.0
[    87.643] (==) AIGLX enabled
[    87.643] (II) Loading extension GLX
[    87.643] (II) LoadModule: "record"
[    87.643] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    87.643] (II) Module record: vendor="X.Org Foundation"
[    87.643]    compiled for 1.11.2.902, module version = 1.13.0
[    87.643]    Module class: X.Org Server Extension
[    87.643]    ABI class: X.Org Server Extension, version 6.0
[    87.643] (II) Loading extension RECORD
[    87.643] (II) LoadModule: "dri"
[    87.643] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    87.643] (II) Module dri: vendor="X.Org Foundation"
[    87.643]    compiled for 1.11.2.902, module version = 1.0.0
[    87.643]    ABI class: X.Org Server Extension, version 6.0
[    87.643] (II) Loading extension XFree86-DRI
[    87.643] (II) LoadModule: "dri2"
[    87.643] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    87.643] (II) Module dri2: vendor="X.Org Foundation"
[    87.643]    compiled for 1.11.2.902, module version = 1.2.0
[    87.643]    ABI class: X.Org Server Extension, version 6.0
[    87.643] (II) Loading extension DRI2
[    87.643] (==) Matched intel as autoconfigured driver 0
[    87.643] (==) Matched vesa as autoconfigured driver 1
[    87.643] (==) Matched fbdev as autoconfigured driver 2
[    87.643] (==) Assigned the driver to the xf86ConfigLayout
[    87.643] (II) LoadModule: "intel"
[    87.643] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    87.644] (II) Module intel: vendor="X.Org Foundation"
[    87.644]    compiled for 1.11.1.902, module version = 2.17.0
[    87.644]    Module class: X.Org Video Driver
[    87.644]    ABI class: X.Org Video Driver, version 11.0
[    87.644] (II) LoadModule: "vesa"
[    87.644] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    87.644] (II) Module vesa: vendor="X.Org Foundation"
[    87.644]    compiled for 1.11.0, module version = 2.3.0
[    87.644]    Module class: X.Org Video Driver
[    87.644]    ABI class: X.Org Video Driver, version 11.0
[    87.644] (II) LoadModule: "fbdev"
[    87.644] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    87.644] (II) Module fbdev: vendor="X.Org Foundation"
[    87.644]    compiled for 1.11.0, module version = 0.4.2
[    87.644]    ABI class: X.Org Video Driver, version 11.0
[    87.644] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
        Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
        Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
        Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
        Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    87.644] (II) VESA: driver for VESA chipsets: vesa
[    87.644] (II) FBDEV: driver for framebuffer: fbdev
[    87.644] (++) using VT number 8

[    87.647] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    87.647] (WW) Falling back to old probe method for vesa
[    87.647] (WW) Falling back to old probe method for fbdev
[    87.647] (II) Loading sub module "fbdevhw"
[    87.647] (II) LoadModule: "fbdevhw"
[    87.647] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    87.647] (II) Module fbdevhw: vendor="X.Org Foundation"
[    87.647]    compiled for 1.11.2.902, module version = 0.0.2
[    87.647]    ABI class: X.Org Video Driver, version 11.0
[    87.647] drmOpenDevice: node name is /dev/dri/card0
[    87.647] drmOpenDevice: open result is 9, (OK)
[    87.647] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    87.647] drmOpenDevice: node name is /dev/dri/card0
[    87.647] drmOpenDevice: open result is 9, (OK)
[    87.647] drmOpenByBusid: drmOpenMinor returns 9
[    87.647] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    87.647] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    87.647] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    87.647] (==) intel(0): RGB weight 888
[    87.647] (==) intel(0): Default visual is TrueColor
[    87.647] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Desktop (GT1)
[    87.647] (--) intel(0): Chipset: "Sandybridge Desktop (GT1)"
[    87.647] (**) intel(0): Relaxed fencing enabled
[    87.647] (**) intel(0): Wait on SwapBuffers? enabled
[    87.647] (**) intel(0): Triple buffering? enabled
[    87.647] (**) intel(0): Framebuffer tiled
[    87.647] (**) intel(0): Pixmaps tiled
[    87.647] (**) intel(0): 3D buffers tiled
[    87.647] (**) intel(0): SwapBuffers wait enabled
[    87.647] (==) intel(0): video overlay key set to 0x101fe
[    87.647] (II) intel(0): Output VGA1 has no monitor section
[    87.670] (II) intel(0): Output HDMI1 has no monitor section
[    87.716] (II) intel(0): Output DP1 has no monitor section
[    87.954] (II) intel(0): Output HDMI2 has no monitor section
[    87.976] (II) intel(0): Output HDMI3 has no monitor section
[    88.024] (II) intel(0): Output DP2 has no monitor section
[    88.072] (II) intel(0): Output DP3 has no monitor section
[    88.072] (II) intel(0): EDID for output VGA1
[    88.094] (II) intel(0): EDID for output HDMI1
[    88.140] (II) intel(0): EDID for output DP1
[    88.377] (II) intel(0): EDID for output HDMI2
[    88.377] (II) intel(0): Manufacturer: PHL  Model: 1  Serial#: 16843009
[    88.377] (II) intel(0): Year: 2006  Week: 1
[    88.377] (II) intel(0): EDID Version: 1.3
[    88.377] (II) intel(0): Digital Display Input
[    88.377] (II) intel(0): Max Image Size [cm]: horiz.: 64  vert.: 36
[    88.377] (II) intel(0): Gamma: 2.20
[    88.377] (II) intel(0): No DPMS capabilities specified
[    88.377] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[    88.377] (II) intel(0): First detailed timing is preferred mode
[    88.377] (II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.290 greenY: 0.600
[    88.377] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.289 whiteY: 0.299
[    88.377] (II) intel(0): Supported established timings:
[    88.377] (II) intel(0): 640x480@60Hz
[    88.377] (II) intel(0): 800x600@60Hz
[    88.377] (II) intel(0): 1024x768@60Hz
[    88.377] (II) intel(0): Manufacturer's mask: 0
[    88.377] (II) intel(0): Supported detailed timing:
[    88.377] (II) intel(0): clock: 74.2 MHz   Image Size:  640 x 360 mm
[    88.377] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    88.377] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    88.377] (II) intel(0): Supported detailed timing:
[    88.377] (II) intel(0): clock: 65.0 MHz   Image Size:  400 x 300 mm
[    88.377] (II) intel(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[    88.377] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[    88.377] (II) intel(0): Monitor name: Philips FTV
[    88.377] (II) intel(0): Ranges: V min: 48 V max: 62 Hz, H min: 15 H max: 50 kHz, PixClock max 95 MHz
[    88.377] (II) intel(0): Supported detailed timing:
[    88.377] (II) intel(0): clock: 74.2 MHz   Image Size:  640 x 360 mm
[    88.377] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    88.377] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    88.377] (II) intel(0): Supported detailed timing:
[    88.377] (II) intel(0): clock: 74.2 MHz   Image Size:  640 x 360 mm
[    88.377] (II) intel(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[    88.377] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    88.377] (II) intel(0): Supported detailed timing:
[    88.377] (II) intel(0): clock: 74.2 MHz   Image Size:  640 x 360 mm
[    88.377] (II) intel(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    88.377] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    88.377] (II) intel(0): Supported detailed timing:
[    88.377] (II) intel(0): clock: 27.0 MHz   Image Size:  640 x 360 mm
[    88.377] (II) intel(0): h_active: 720  h_sync: 732  h_sync_end 796 h_blank_end 864 h_border: 0
[    88.377] (II) intel(0): v_active: 576  v_sync: 581  v_sync_end 586 v_blanking: 625 v_border: 0
[    88.377] (II) intel(0): Supported detailed timing:
[    88.377] (II) intel(0): clock: 27.0 MHz   Image Size:  640 x 360 mm
[    88.377] (II) intel(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    88.377] (II) intel(0): v_active: 480  v_sync: 483  v_sync_end 489 v_blanking: 525 v_border: 0
[    88.377] (II) intel(0): Number of EDID sections to follow: 1
[    88.377] (II) intel(0): EDID (in hex):
[    88.377] (II) intel(0):     00ffffffffffff00410c010001010101
[    88.377] (II) intel(0):     01100103804024780ae692a3544a9926
[    88.377] (II) intel(0):     0f4a4c21080001010101010101010101
[    88.377] (II) intel(0):     010101010101011d80d0721c1620102c
[    88.377] (II) intel(0):     258080682100009e6419004041002630
[    88.377] (II) intel(0):     18883600902c11000018000000fc0050
[    88.377] (II) intel(0):     68696c697073204654560a20000000fd
[    88.377] (II) intel(0):     00303e0f3209000a202020202020018b
[    88.377] (II) intel(0):     020324f04b0103040506071213141516
[    88.377] (II) intel(0):     29091f07150750190786830100006503
[    88.377] (II) intel(0):     0c002000011d8018711c1620582c2500
[    88.377] (II) intel(0):     80682100009e011d00bc52d01e20b828
[    88.377] (II) intel(0):     554080682100001e011d007251d01e20
[    88.377] (II) intel(0):     6e28550080682100001e8c0ad0902040
[    88.377] (II) intel(0):     31200c4055008068210000188c0ad08a
[    88.378] (II) intel(0):     20e02d10103e360080682100001800c1
[    88.378] (II) intel(0): Printing probed modes for output HDMI2
[    88.378] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    88.378] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    88.378] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    88.400] (II) intel(0): EDID for output HDMI3
[    88.448] (II) intel(0): EDID for output DP2
[    88.496] (II) intel(0): EDID for output DP3
[    88.496] (II) intel(0): Output VGA1 disconnected
[    88.496] (II) intel(0): Output HDMI1 disconnected
[    88.496] (II) intel(0): Output DP1 disconnected
[    88.496] (II) intel(0): Output HDMI2 connected
[    88.496] (II) intel(0): Output HDMI3 disconnected
[    88.496] (II) intel(0): Output DP2 disconnected
[    88.496] (II) intel(0): Output DP3 disconnected
[    88.496] (II) intel(0): Using fuzzy aspect match for initial modes
[    88.496] (II) intel(0): Output HDMI2 using initial mode 1024x768
[    88.496] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    88.496] (II) intel(0): Kernel page flipping support detected, enabling
[    88.496] (==) intel(0): DPI set to (96, 96)
[    88.496] (II) Loading sub module "fb"
[    88.496] (II) LoadModule: "fb"
[    88.496] (II) Loading /usr/lib/xorg/modules/libfb.so
[    88.496] (II) Module fb: vendor="X.Org Foundation"
[    88.496]    compiled for 1.11.2.902, module version = 1.0.0
[    88.496]    ABI class: X.Org ANSI C Emulation, version 0.4
[    88.496] (II) Loading sub module "dri2"
[    88.496] (II) LoadModule: "dri2"
[    88.496] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    88.496] (II) Module dri2: vendor="X.Org Foundation"
[    88.496]    compiled for 1.11.2.902, module version = 1.2.0
[    88.496]    ABI class: X.Org Server Extension, version 6.0
[    88.496] (II) UnloadModule: "vesa"
[    88.496] (II) Unloading vesa
[    88.496] (II) UnloadModule: "fbdev"
[    88.496] (II) Unloading fbdev
[    88.496] (II) UnloadModule: "fbdevhw"
[    88.496] (II) Unloading fbdevhw
[    88.496] (==) Depth 24 pixmap format is 32 bpp
[    88.496] (II) intel(0): [DRI2] Setup complete
[    88.496] (II) intel(0): [DRI2]   DRI driver: i965
[    88.496] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    88.497] (II) UXA(0): Driver registered support for the following operations:
[    88.497] (II)         solid
[    88.497] (II)         copy
[    88.497] (II)         composite (RENDER acceleration)
[    88.497] (II)         put_image
[    88.497] (II)         get_image
[    88.497] (==) intel(0): Backing store disabled
[    88.497] (==) intel(0): Silken mouse enabled
[    88.497] (II) intel(0): Initializing HW Cursor
[    88.552] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    88.552] (==) intel(0): DPMS enabled
[    88.552] (==) intel(0): Intel XvMC decoder enabled
[    88.552] (II) intel(0): Set up textured video
[    88.552] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    88.552] (II) intel(0): direct rendering: DRI2 Enabled
[    88.552] (==) intel(0): hotplug detection: "enabled"
[    88.552] (--) RandR disabled
[    88.552] (II) Initializing built-in extension Generic Event Extension
[    88.552] (II) Initializing built-in extension SHAPE
[    88.552] (II) Initializing built-in extension MIT-SHM
[    88.552] (II) Initializing built-in extension XInputExtension
[    88.552] (II) Initializing built-in extension XTEST
[    88.552] (II) Initializing built-in extension BIG-REQUESTS
[    88.552] (II) Initializing built-in extension SYNC
[    88.552] (II) Initializing built-in extension XKEYBOARD
[    88.552] (II) Initializing built-in extension XC-MISC
[    88.552] (II) Initializing built-in extension SECURITY
[    88.552] (II) Initializing built-in extension XINERAMA
[    88.552] (II) Initializing built-in extension XFIXES
[    88.552] (II) Initializing built-in extension RENDER
[    88.552] (II) Initializing built-in extension RANDR
[    88.552] (II) Initializing built-in extension COMPOSITE
[    88.552] (II) Initializing built-in extension DAMAGE
[    88.552] (II) SELinux: Disabled on system
[    88.559] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    88.559] (II) AIGLX: enabled GLX_INTEL_swap_event
[    88.559] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    88.559] (II) AIGLX: enabled GLX_SGI_make_current_read
[    88.559] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    88.559] (II) AIGLX: Loaded and initialized i965
[    88.559] (II) GLX: Initialized DRI2 GL provider for screen 0
[    88.560] (II) intel(0): Setting screen physical size to 270 x 203
[    88.581] (II) config/udev: Adding input device Power Button (/dev/input/event5)
[    88.581] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    88.581] (II) LoadModule: "evdev"
[    88.581] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    88.581] (II) Module evdev: vendor="X.Org Foundation"
[    88.581]    compiled for 1.11.0, module version = 2.6.0
[    88.581]    Module class: X.Org XInput Driver
[    88.581]    ABI class: X.Org XInput driver, version 13.0
[    88.581] (II) Using input driver 'evdev' for 'Power Button'
[    88.581] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    88.581] (**) Power Button: always reports core events
[    88.582] (**) Power Button: Device: "/dev/input/event5"
[    88.582] (--) Power Button: Found keys
[    88.582] (II) Power Button: Configuring as keyboard
[    88.582] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input5/event5"
[    88.582] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    88.582] (**) Option "xkb_rules" "evdev"
[    88.582] (**) Option "xkb_model" "pc105"
[    88.582] (**) Option "xkb_layout" "us"
[    88.582] (II) config/udev: Adding input device Power Button (/dev/input/event4)
[    88.582] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    88.582] (II) Using input driver 'evdev' for 'Power Button'
[    88.582] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    88.582] (**) Power Button: always reports core events
[    88.582] (**) Power Button: Device: "/dev/input/event4"
[    88.582] (--) Power Button: Found keys
[    88.582] (II) Power Button: Configuring as keyboard
[    88.582] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4/event4"
[    88.582] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    88.582] (**) Option "xkb_rules" "evdev"
[    88.582] (**) Option "xkb_model" "pc105"
[    88.582] (**) Option "xkb_layout" "us"
[    88.582] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP (/dev/input/event7)
[    88.582] (II) No input driver/identifier specified (ignoring)
[    88.582] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP (/dev/input/event8)
[    88.582] (II) No input driver/identifier specified (ignoring)
[    88.582] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event0)
[    88.582] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[    88.582] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[    88.582] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    88.583] (**) HID 04f3:0103: always reports core events
[    88.583] (**) HID 04f3:0103: Device: "/dev/input/event0"
[    88.583] (--) HID 04f3:0103: Found keys
[    88.583] (II) HID 04f3:0103: Configuring as keyboard
[    88.583] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input0/event0"
[    88.583] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD, id 8)
[    88.583] (**) Option "xkb_rules" "evdev"
[    88.583] (**) Option "xkb_model" "pc105"
[    88.583] (**) Option "xkb_layout" "us"
[    88.583] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event1)
[    88.583] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[    88.583] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[    88.583] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    88.583] (**) HID 04f3:0103: always reports core events
[    88.583] (**) HID 04f3:0103: Device: "/dev/input/event1"
[    88.583] (--) HID 04f3:0103: Found 1 mouse buttons
[    88.583] (--) HID 04f3:0103: Found scroll wheel(s)
[    88.583] (--) HID 04f3:0103: Found relative axes
[    88.583] (--) HID 04f3:0103: Found absolute axes
[    88.583] (--) HID 04f3:0103: Found keys
[    88.583] (II) HID 04f3:0103: Configuring as mouse
[    88.583] (II) HID 04f3:0103: Configuring as keyboard
[    88.583] (II) HID 04f3:0103: Adding scrollwheel support
[    88.583] (**) HID 04f3:0103: YAxisMapping: buttons 4 and 5
[    88.583] (**) HID 04f3:0103: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    88.583] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.1/input/input1/event1"
[    88.583] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD, id 9)
[    88.583] (**) Option "xkb_rules" "evdev"
[    88.583] (**) Option "xkb_model" "pc105"
[    88.583] (**) Option "xkb_layout" "us"
[    88.583] (EE) HID 04f3:0103: failed to initialize for relative axes.
[    88.583] (II) HID 04f3:0103: initialized for absolute axes.
[    88.583] (**) HID 04f3:0103: (accel) keeping acceleration scheme 1
[    88.583] (**) HID 04f3:0103: (accel) acceleration profile 0
[    88.583] (**) HID 04f3:0103: (accel) acceleration factor: 2.000
[    88.583] (**) HID 04f3:0103: (accel) acceleration threshold: 4
[    88.583] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event2)
[    88.583] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    88.583] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    88.583] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    88.583] (**) USB Optical Mouse: always reports core events
[    88.583] (**) USB Optical Mouse: Device: "/dev/input/event2"
[    88.583] (--) USB Optical Mouse: Found 3 mouse buttons
[    88.583] (--) USB Optical Mouse: Found scroll wheel(s)
[    88.583] (--) USB Optical Mouse: Found relative axes
[    88.583] (--) USB Optical Mouse: Found x and y relative axes
[    88.583] (II) USB Optical Mouse: Configuring as mouse
[    88.583] (II) USB Optical Mouse: Adding scrollwheel support
[    88.583] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    88.583] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    88.583] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input2/event2"
[    88.583] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 10)
[    88.583] (II) USB Optical Mouse: initialized for relative axes.
[    88.584] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    88.584] (**) USB Optical Mouse: (accel) acceleration profile 0
[    88.584] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    88.584] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    88.584] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    88.584] (II) No input driver/identifier specified (ignoring)
[    88.584] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    88.584] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    88.584] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    88.584] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    88.584] (**) Logitech USB Receiver: always reports core events
[    88.584] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    88.584] (--) Logitech USB Receiver: Found 12 mouse buttons
[    88.584] (--) Logitech USB Receiver: Found scroll wheel(s)
[    88.584] (--) Logitech USB Receiver: Found relative axes
[    88.584] (--) Logitech USB Receiver: Found x and y relative axes
[    88.584] (II) Logitech USB Receiver: Configuring as mouse
[    88.584] (II) Logitech USB Receiver: Adding scrollwheel support
[    88.584] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    88.584] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    88.584] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input3/event3"
[    88.584] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 11)
[    88.584] (II) Logitech USB Receiver: initialized for relative axes.
[    88.584] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    88.584] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    88.584] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    88.584] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    88.584] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[    88.584] (II) No input driver/identifier specified (ignoring)
[    88.584] (II) config/udev: Adding input device PC Speaker (/dev/input/event6)
[    88.584] (II) No input driver/identifier specified (ignoring)
[    88.893] (II) intel(0): EDID vendor "PHL", prod id 1
[    88.893] (II) intel(0): Using EDID range info for horizontal sync
[    88.893] (II) intel(0): Using EDID range info for vertical refresh
[    88.893] (II) intel(0): Printing DDC gathered Modelines:
[    88.893] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    88.893] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    88.893] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    88.893] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    88.893] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    88.893] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    88.893] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[    88.893] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    88.893] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    88.893] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    88.893] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    88.893] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    88.893] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    88.893] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    89.421] (II) intel(0): EDID vendor "PHL", prod id 1
[    89.421] (II) intel(0): Using hsync ranges from config file
[    89.421] (II) intel(0): Using vrefresh ranges from config file
[    89.421] (II) intel(0): Printing DDC gathered Modelines:
[    89.421] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    89.421] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    89.421] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    89.421] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    89.421] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    89.421] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    89.421] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[    89.421] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    89.421] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    89.421] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    89.421] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    89.421] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    89.421] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    89.421] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    89.849] (II) intel(0): EDID vendor "PHL", prod id 1
[    89.849] (II) intel(0): Using hsync ranges from config file
[    89.849] (II) intel(0): Using vrefresh ranges from config file
[    89.849] (II) intel(0): Printing DDC gathered Modelines:
[    89.849] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    89.849] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    89.849] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    89.849] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    89.849] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    89.849] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    89.849] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[    89.849] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    89.849] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    89.849] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    89.849] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    89.849] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    89.849] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    89.849] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    90.277] (II) intel(0): EDID vendor "PHL", prod id 1
[    90.277] (II) intel(0): Using hsync ranges from config file
[    90.277] (II) intel(0): Using vrefresh ranges from config file
[    90.277] (II) intel(0): Printing DDC gathered Modelines:
[    90.277] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    90.277] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    90.277] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    90.277] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    90.277] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    90.277] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    90.277] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[    90.277] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    90.277] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    90.278] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    90.278] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    90.278] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    90.278] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    90.278] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    90.701] (II) intel(0): EDID vendor "PHL", prod id 1
[    90.701] (II) intel(0): Using hsync ranges from config file
[    90.701] (II) intel(0): Using vrefresh ranges from config file
[    90.701] (II) intel(0): Printing DDC gathered Modelines:
[    90.701] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    90.701] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    90.701] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    90.701] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    90.701] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    90.701] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    90.701] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[    90.701] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    90.701] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    90.701] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    90.701] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    90.701] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    90.701] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    90.701] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    91.129] (II) intel(0): EDID vendor "PHL", prod id 1
[    91.129] (II) intel(0): Using hsync ranges from config file
[    91.129] (II) intel(0): Using vrefresh ranges from config file
[    91.129] (II) intel(0): Printing DDC gathered Modelines:
[    91.129] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    91.129] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    91.129] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    91.129] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    91.129] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    91.129] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    91.129] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[    91.129] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    91.129] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    91.129] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    91.129] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    91.129] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    91.129] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    91.129] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    91.553] (II) intel(0): EDID vendor "PHL", prod id 1
[    91.553] (II) intel(0): Using hsync ranges from config file
[    91.553] (II) intel(0): Using vrefresh ranges from config file
[    91.553] (II) intel(0): Printing DDC gathered Modelines:
[    91.553] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    91.553] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    91.553] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    91.553] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    91.553] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    91.553] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    91.553] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[    91.553] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    91.553] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    91.553] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    91.553] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    91.553] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    91.553] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    91.553] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    92.137] (II) intel(0): EDID vendor "PHL", prod id 1
[    92.137] (II) intel(0): Using hsync ranges from config file
[    92.137] (II) intel(0): Using vrefresh ranges from config file
[    92.137] (II) intel(0): Printing DDC gathered Modelines:
[    92.137] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    92.137] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    92.137] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    92.137] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    92.137] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    92.137] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    92.137] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[    92.137] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    92.137] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    92.137] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    92.137] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    92.137] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    92.137] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    92.137] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[   140.233] (II) intel(0): EDID vendor "PHL", prod id 1
[   140.233] (II) intel(0): Using hsync ranges from config file
[   140.233] (II) intel(0): Using vrefresh ranges from config file
[   140.233] (II) intel(0): Printing DDC gathered Modelines:
[   140.233] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   140.233] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   140.233] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   140.233] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   140.233] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   140.233] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   140.233] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[   140.233] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   140.233] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   140.233] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   140.233] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   140.233] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[   140.233] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[   140.233] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[   140.661] (II) intel(0): EDID vendor "PHL", prod id 1
[   140.661] (II) intel(0): Using hsync ranges from config file
[   140.661] (II) intel(0): Using vrefresh ranges from config file
[   140.661] (II) intel(0): Printing DDC gathered Modelines:
[   140.661] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   140.661] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   140.661] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   140.661] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   140.661] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   140.661] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   140.661] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[   140.661] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   140.661] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   140.661] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   140.661] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   140.661] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[   140.661] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[   140.661] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[   141.089] (II) intel(0): EDID vendor "PHL", prod id 1
[   141.089] (II) intel(0): Using hsync ranges from config file
[   141.089] (II) intel(0): Using vrefresh ranges from config file
[   141.089] (II) intel(0): Printing DDC gathered Modelines:
[   141.089] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   141.089] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   141.089] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   141.089] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   141.089] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   141.089] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   141.089] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[   141.089] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   141.089] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   141.089] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   141.089] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   141.089] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[   141.089] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[   141.089] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[   141.517] (II) intel(0): EDID vendor "PHL", prod id 1
[   141.517] (II) intel(0): Using hsync ranges from config file
[   141.517] (II) intel(0): Using vrefresh ranges from config file
[   141.517] (II) intel(0): Printing DDC gathered Modelines:
[   141.517] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   141.517] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   141.517] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   141.517] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   141.517] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   141.517] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   141.517] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[   141.517] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   141.517] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   141.517] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   141.517] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   141.517] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[   141.517] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[   141.517] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[   141.945] (II) intel(0): EDID vendor "PHL", prod id 1
[   141.945] (II) intel(0): Using hsync ranges from config file
[   141.945] (II) intel(0): Using vrefresh ranges from config file
[   141.945] (II) intel(0): Printing DDC gathered Modelines:
[   141.945] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   141.945] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   141.945] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   141.945] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   141.945] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   141.945] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   141.946] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[   141.946] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   141.946] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   141.946] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   141.946] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   141.946] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[   141.946] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[   141.946] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[   142.373] (II) intel(0): EDID vendor "PHL", prod id 1
[   142.373] (II) intel(0): Using hsync ranges from config file
[   142.373] (II) intel(0): Using vrefresh ranges from config file
[   142.373] (II) intel(0): Printing DDC gathered Modelines:
[   142.373] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   142.373] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   142.373] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   142.373] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   142.373] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   142.373] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   142.373] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[   142.373] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   142.373] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   142.373] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   142.373] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   142.373] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[   142.373] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[   142.373] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[   144.549] (II) intel(0): EDID vendor "PHL", prod id 1
[   144.549] (II) intel(0): Using hsync ranges from config file
[   144.549] (II) intel(0): Using vrefresh ranges from config file
[   144.549] (II) intel(0): Printing DDC gathered Modelines:
[   144.549] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   144.549] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   144.549] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   144.549] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   144.549] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   144.549] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   144.549] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[   144.549] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   144.549] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   144.549] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   144.549] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   144.549] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[   144.549] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[   144.549] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[   146.533] (II) intel(0): EDID vendor "PHL", prod id 1
[   146.533] (II) intel(0): Using hsync ranges from config file
[   146.533] (II) intel(0): Using vrefresh ranges from config file
[   146.533] (II) intel(0): Printing DDC gathered Modelines:
[   146.533] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   146.533] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   146.533] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   146.533] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   146.533] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   146.533] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   146.533] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 483 489 525 -hsync -vsync (31.5 kHz)
[   146.533] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   146.533] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   146.533] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   146.533] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   146.533] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[   146.533] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[   146.533] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)

```

---

### Post by BicyclerBoy on 2012-01-16
There is nothing special in that grub config file (that I can see).

You could ask for a copy of his/her: 
/etc/X11/xorg.conf file..

The Xorg.0.log just shows intel HDMI 1920x1080 video mode..

If you can get the VGA cable to work you should be able to use 720p60 or 1080i60/p60 because the TV will/should accept HD mode inputs.
You should be able to force 720 or 1080 over HDMI  if the TV is HD-ready..

Your previous Xorg.0.log file showed DDC video modes including the 1080i mode below..
So you could try to force this on your HDMI connection:
```

$ xrandr --newmode "1920x1080i_60.0"   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync
$ xrandr --addmode HDMI2 "1920x1080i_60.0"
$ xrandr --output HDMI2 --mode "1920x1080i_60.0"

```

---

### Post by alfonso78 on 2012-01-17
Hi BicyclerBoy and thank you,

I tried your mode and almost all others.

Only good news is that I can tell you doing commands over VNC is not a problem. Actually sometimes is the only way, since when the screen is disconnected I wouldn't be able to type anything otherwise!

```
$ xrandr --newmode "1920x1080i_60.0"   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync
$ xrandr --addmode HDMI2 "1920x1080i_60.0"
$ xrandr --output HDMI2 --mode "1920x1080i_60.0"
```

nothing - blue screen

```
xrandr --newmode "test2_60.0" 65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
xrandr --addmode HDMI2 "test2_60.0"
xrandr --output HDMI2 --mode "test2_60.0"
```

back to the original situation (two bands, flickering)

```
xrandr --newmode "test3_60.0" 74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync
xrandr --addmode HDMI2 "test3_60.0"
xrandr --output HDMI2 --mode "test3_60.0"
```

nothing - blue screen

```
xrandr --newmode "test4_60.0" 74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync
xrandr --addmode HDMI2 "test4_60.0"
xrandr --output HDMI2 --mode "test4_60.0"
```

three bands, flickering

```
xrandr --newmode "test5_60.0" 74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync
xrandr --addmode HDMI2 "test5_60.0"
xrandr --output HDMI2 --mode "test5_60.0"
```

two bands, flickering

```
xrandr --newmode "test6_60.0" 27.00  720 732 796 864  576 581 586 625 -hsync -vsync
xrandr --addmode HDMI2 "test6_60.0"
xrandr --output HDMI2 --mode "test6_60.0"
```

three bands, no flickering

```
xrandr --newmode "test7_60.0" 27.00  720 736 798 858  480 483 489 525 -hsync -vsync
xrandr --addmode HDMI2 "test7_60.0"
xrandr --output HDMI2 --mode "test7_60.0"
```

two bands, no flickering

```
xrandr --newmode "test8_60.0" 40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
xrandr --addmode HDMI2 "test8_60.0"
xrandr --output HDMI2 --mode "test8_60.0"
```

two bands, flickering

```
xrandr --newmode "test9_60.0" 27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync
xrandr --addmode HDMI2 "test9_60.0"
xrandr --output HDMI2 --mode "test9_60.0"
```

strange aspect ratio, the screen is zoomed, no flickering

the only thing left to test is a 64 bit kernel. I will try this prob tomorrow.

thank you,

---

### Post by alfonso78 on 2012-01-28
UPDATE:

I got in touch with the fine folks at Intel-gfx and they helped me solve the problem. They developed several patches for different issues.

About VGA:

instead of adding a newmode, I simply had to try the values offered by "xrandr -q".
The problem was that the driver by default used a refresh rate of 54.4 which is not good with my TV.

```
xrandr --output VGA1 --mode 1024x768 --rate 60.0
```

made VGA visible.

About the HDMI, it is now fixed in the interlaced branch of this git: git://people.freedesktop.org/~danvet/drm

I compiled the kernel and now I can use 1920x1080i, 1280x720p, 1280x720p and 800x600p

Thank you BicyclerBoy for teaching me what I needed to know to help the developers help me. :)

---


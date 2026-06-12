---
title: "Mach 3D Rage Pro / Mach64: No video, only when I drag window around will video show"
date: 2013-09-11
forum: Multimedia Software
---

### Post by EngineersGarage on 2013-09-11
Hi,

Im a noob to all linux and ubuntu.. still learning... I decided to load ubuntu once again on my pc, I now remember why I removed it the last time for mint...

Ok, on a fresh install of ubuntu 12.04Lts, with all updates done.... I just cant get my movies to play properly, even tried installing vlc, but have the exact same problem...
When I play a movie or video, I have no visual only sound..BUT.... when I drag the window around the desktop the video appears and I can see the video and when i let the window go and leave it stationary it immediately goes black again...

How do I fix this? I want to start using ubuntu and learn the OS... I had this problem last time to then i switched to mint, I actually forgot that ubuntu did this, only after i wiped and installed OS the problem re-emmerged again.

If anyone could aid me with this technical problem I would be really gratefull.

Thank you.

---

### Post by Yellow Pasque on 2013-09-11
Post your /var/log/Xorg.0.log (use [ code ][ /code ] tags).

---

### Post by EngineersGarage on 2013-09-12
Hi, I think this is what you asked for???


[    19.027] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    19.027] X Protocol Version 11, Revision 0
[    19.027] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    19.027] Current Operating System: Linux Home-Server 3.2.0-53-generic-pae #81-Ubuntu SMP Thu Aug 22 21:23:47 UTC 2013 i686
[    19.027] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-53-generic-pae root=UUID=7d926326-1f83-454c-80c6-2f3e5cf52feb ro quiet splash vt.handoff=7
[    19.027] Build Date: 11 April 2013  01:04:30PM
[    19.027] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    19.027] Current version of pixman: 0.24.4
[    19.027]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    19.027] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.028] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep  8 22:10:01 2013
[    19.058] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.059] (==) No Layout section.  Using the first Screen section.
[    19.059] (==) No screen section available. Using defaults.
[    19.059] (**) |-->Screen "Default Screen Section" (0)
[    19.059] (**) |   |-->Monitor "<default monitor>"
[    19.059] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    19.059] (==) Automatically adding devices
[    19.059] (==) Automatically enabling devices
[    19.059] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.059]     Entry deleted from font path.
[    19.059] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.059]     Entry deleted from font path.
[    19.059] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.059]     Entry deleted from font path.
[    19.060] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.060]     Entry deleted from font path.
[    19.060] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.060]     Entry deleted from font path.
[    19.060] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    19.060]     Entry deleted from font path.
[    19.060] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    19.060] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.060] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.060] (II) Loader magic: 0xb776b5a0
[    19.060] (II) Module ABI versions:
[    19.060]     X.Org ANSI C Emulation: 0.4
[    19.060]     X.Org Video Driver: 11.0
[    19.060]     X.Org XInput driver : 16.0
[    19.060]     X.Org Server Extension : 6.0
[    19.061] (--) PCI:*(0:5:2:0) 1002:4752:8086:3444 rev 39, Mem @ 0xdf000000/16777216, 0xdefff000/4096, I/O @ 0x0000e800/256, BIOS @ 0x????????/131072
[    19.061] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.061] (II) LoadModule: "extmod"
[    19.074] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.074] (II) Module extmod: vendor="X.Org Foundation"
[    19.074]     compiled for 1.11.3, module version = 1.0.0
[    19.074]     Module class: X.Org Server Extension
[    19.074]     ABI class: X.Org Server Extension, version 6.0
[    19.074] (II) Loading extension MIT-SCREEN-SAVER
[    19.074] (II) Loading extension XFree86-VidModeExtension
[    19.074] (II) Loading extension XFree86-DGA
[    19.074] (II) Loading extension DPMS
[    19.074] (II) Loading extension XVideo
[    19.074] (II) Loading extension XVideo-MotionCompensation
[    19.074] (II) Loading extension X-Resource
[    19.074] (II) LoadModule: "dbe"
[    19.074] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.075] (II) Module dbe: vendor="X.Org Foundation"
[    19.075]     compiled for 1.11.3, module version = 1.0.0
[    19.075]     Module class: X.Org Server Extension
[    19.075]     ABI class: X.Org Server Extension, version 6.0
[    19.075] (II) Loading extension DOUBLE-BUFFER
[    19.075] (II) LoadModule: "glx"
[    19.075] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    19.075] (II) Module glx: vendor="X.Org Foundation"
[    19.075]     compiled for 1.11.3, module version = 1.0.0
[    19.075]     ABI class: X.Org Server Extension, version 6.0
[    19.075] (==) AIGLX enabled
[    19.075] (II) Loading extension GLX
[    19.075] (II) LoadModule: "record"
[    19.076] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.076] (II) Module record: vendor="X.Org Foundation"
[    19.076]     compiled for 1.11.3, module version = 1.13.0
[    19.076]     Module class: X.Org Server Extension
[    19.076]     ABI class: X.Org Server Extension, version 6.0
[    19.076] (II) Loading extension RECORD
[    19.076] (II) LoadModule: "dri"
[    19.077] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.077] (II) Module dri: vendor="X.Org Foundation"
[    19.077]     compiled for 1.11.3, module version = 1.0.0
[    19.077]     ABI class: X.Org Server Extension, version 6.0
[    19.077] (II) Loading extension XFree86-DRI
[    19.077] (II) LoadModule: "dri2"
[    19.078] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.078] (II) Module dri2: vendor="X.Org Foundation"
[    19.078]     compiled for 1.11.3, module version = 1.2.0
[    19.078]     ABI class: X.Org Server Extension, version 6.0
[    19.078] (II) Loading extension DRI2
[    19.078] (==) Matched fglrx as autoconfigured driver 0
[    19.078] (==) Matched ati as autoconfigured driver 1
[    19.078] (==) Matched vesa as autoconfigured driver 2
[    19.078] (==) Matched fbdev as autoconfigured driver 3
[    19.078] (==) Assigned the driver to the xf86ConfigLayout
[    19.078] (II) LoadModule: "fglrx"
[    19.086] (WW) Warning, couldn't open module fglrx
[    19.086] (II) UnloadModule: "fglrx"
[    19.086] (II) Unloading fglrx
[    19.086] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    19.086] (II) LoadModule: "ati"
[    19.087] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    19.087] (II) Module ati: vendor="X.Org Foundation"
[    19.087]     compiled for 1.11.3, module version = 6.14.99
[    19.087]     Module class: X.Org Video Driver
[    19.087]     ABI class: X.Org Video Driver, version 11.0
[    19.087] (II) LoadModule: "mach64"
[    19.087] (II) Loading /usr/lib/xorg/modules/drivers/mach64_drv.so
[    19.087] (II) Module mach64: vendor="X.Org Foundation"
[    19.087]     compiled for 1.11.3, module version = 6.9.0
[    19.087]     Module class: X.Org Video Driver
[    19.087]     ABI class: X.Org Video Driver, version 11.0
[    19.088] (II) LoadModule: "vesa"
[    19.088] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.088] (II) Module vesa: vendor="X.Org Foundation"
[    19.088]     compiled for 1.11.3, module version = 2.3.0
[    19.088]     Module class: X.Org Video Driver
[    19.088]     ABI class: X.Org Video Driver, version 11.0
[    19.088] (II) LoadModule: "fbdev"
[    19.088] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.089] (II) Module fbdev: vendor="X.Org Foundation"
[    19.089]     compiled for 1.11.3, module version = 0.4.2
[    19.089]     ABI class: X.Org Video Driver, version 11.0
[    19.089] (==) Matched fglrx as autoconfigured driver 0
[    19.089] (==) Matched ati as autoconfigured driver 1
[    19.089] (==) Matched vesa as autoconfigured driver 2
[    19.089] (==) Matched fbdev as autoconfigured driver 3
[    19.089] (==) Assigned the driver to the xf86ConfigLayout
[    19.089] (II) LoadModule: "fglrx"
[    19.090] (WW) Warning, couldn't open module fglrx
[    19.090] (II) UnloadModule: "fglrx"
[    19.090] (II) Unloading fglrx
[    19.090] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    19.090] (II) LoadModule: "ati"
[    19.090] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    19.090] (II) Module ati: vendor="X.Org Foundation"
[    19.090]     compiled for 1.11.3, module version = 6.14.99
[    19.090]     Module class: X.Org Video Driver
[    19.090]     ABI class: X.Org Video Driver, version 11.0
[    19.090] (II) LoadModule: "vesa"
[    19.090] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.090] (II) Module vesa: vendor="X.Org Foundation"
[    19.090]     compiled for 1.11.3, module version = 2.3.0
[    19.090]     Module class: X.Org Video Driver
[    19.090]     ABI class: X.Org Video Driver, version 11.0
[    19.090] (II) UnloadModule: "vesa"
[    19.091] (II) Unloading vesa
[    19.091] (II) Failed to load module "vesa" (already loaded, 0)
[    19.091] (II) LoadModule: "fbdev"
[    19.091] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.091] (II) Module fbdev: vendor="X.Org Foundation"
[    19.091]     compiled for 1.11.3, module version = 0.4.2
[    19.091]     ABI class: X.Org Video Driver, version 11.0
[    19.091] (II) UnloadModule: "fbdev"
[    19.091] (II) Unloading fbdev
[    19.091] (II) Failed to load module "fbdev" (already loaded, 0)
[    19.091] (II) MACH64: Driver for ATI Mach64 chipsets
[    19.091] (II) VESA: driver for VESA chipsets: vesa
[    19.091] (II) FBDEV: driver for framebuffer: fbdev
[    19.091] (++) using VT number 7

[    19.091] (II) Loading /usr/lib/xorg/modules/drivers/mach64_drv.so
[    19.091] (WW) Falling back to old probe method for vesa
[    19.091] (WW) Falling back to old probe method for fbdev
[    19.091] (II) Loading sub module "fbdevhw"
[    19.091] (II) LoadModule: "fbdevhw"
[    19.092] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    19.092] (II) Module fbdevhw: vendor="X.Org Foundation"
[    19.092]     compiled for 1.11.3, module version = 0.0.2
[    19.092]     ABI class: X.Org Video Driver, version 11.0
[    19.092] (II) MACH64(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    19.092] (==) MACH64(0): Depth 24, (--) framebuffer bpp 32
[    19.092] (==) MACH64(0): Using XAA acceleration architecture
[    19.092] (II) MACH64: Mach64 in slot 5:2:0 detected.
[    19.092] (II) Loading sub module "int10"
[    19.092] (II) LoadModule: "int10"
[    19.093] (II) Loading /usr/lib/xorg/modules/libint10.so
[    19.093] (II) Module int10: vendor="X.Org Foundation"
[    19.093]     compiled for 1.11.3, module version = 1.0.0
[    19.093]     ABI class: X.Org Video Driver, version 11.0
[    19.100] (II) MACH64(0): Primary V_BIOS segment is: 0xc000
[    19.100] (II) Loading sub module "ddc"
[    19.100] (II) LoadModule: "ddc"
[    19.100] (II) Module "ddc" already built-in
[    19.100] (II) Loading sub module "vbe"
[    19.100] (II) LoadModule: "vbe"
[    19.101] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    19.101] (II) Module vbe: vendor="X.Org Foundation"
[    19.101]     compiled for 1.11.3, module version = 1.1.0
[    19.101]     ABI class: X.Org Video Driver, version 11.0
[    19.101] (II) MACH64(0): VESA BIOS detected
[    19.101] (II) MACH64(0): VESA VBE Version 2.0
[    19.101] (II) MACH64(0): VESA VBE Total Mem: 8128 kB
[    19.101] (II) MACH64(0): VESA VBE OEM: ATI MACH64
[    19.101] (II) MACH64(0): VESA VBE OEM Software Rev: 1.0
[    19.102] (II) MACH64(0): VESA VBE OEM Vendor: ATI Technologies Inc.
[    19.102] (II) MACH64(0): VESA VBE OEM Product: MACH64GM
[    19.102] (II) MACH64(0): VESA VBE OEM Product Rev: 01.00
[    19.106] (II) MACH64(0): VESA VBE DDC supported
[    19.106] (II) MACH64(0): VESA VBE DDC Level none
[    19.106] (II) MACH64(0): VESA VBE DDC transfer in appr. 2 sec.
[    19.109] (II) MACH64(0): VESA VBE DDC read failed
[    19.111] (II) MACH64(0): BIOS Data:  BIOSSize=0x8000, ROMTable=0x0128.
[    19.111] (II) MACH64(0): BIOS Data:  ClockTable=0x0994, FrequencyTable=0x0000.
[    19.111] (II) MACH64(0): BIOS Data:  LCDTable=0x0000.
[    19.111] (II) MACH64(0): BIOS Data:  VideoTable=0x0000, HardwareTable=0x0172.
[    19.111] (II) MACH64(0): BIOS Data:  I2CType=0x0F, Tuner=0x00, Decoder=0x00, Audio=0x0F.
[    19.111] (--) MACH64(0): ATI 3D Rage XL or XC graphics controller detected.
[    19.111] (--) MACH64(0): Chip type 4752 "GR", version 7, foundry TSMC, class 0, revision 0x00.
[    19.112] (--) MACH64(0): PCI bus interface detected;  block I/O base is 0xE800.
[    19.112] (--) MACH64(0): ATI Mach64 adapter detected.
[    19.112] (!!) MACH64(0): For information on using the multimedia capabilities
    of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
[    19.112] (--) MACH64(0): Internal RAMDAC (subtype 1) detected.
[    19.112] (==) MACH64(0): RGB weight 888
[    19.112] (==) MACH64(0): Default visual is TrueColor
[    19.112] (==) MACH64(0): Using gamma correction (1.0, 1.0, 1.0)
[    19.112] (II) MACH64(0): Using Mach64 accelerator CRTC.
[    19.112] (II) MACH64(0): Storing hardware cursor image at 0xDF7FFC00.
[    19.112] (II) MACH64(0): Using 8 MB linear aperture at 0xDF000000.
[    19.112] (!!) MACH64(0): Virtual resolutions will be limited to 8191 kB
 due to linear aperture size and/or placement of hardware cursor image area.
[    19.112] (II) MACH64(0): Using Block 0 MMIO aperture at 0xDEFFF400.
[    19.112] (II) MACH64(0): Using Block 1 MMIO aperture at 0xDEFFF000.
[    19.117] (II) MACH64(0): MMIO write caching enabled.
[    19.117] (--) MACH64(0): 8192 kB of SGRAM (2:1) 32-bit detected (using 8191 kB).
[    19.117] (WW) MACH64(0): Cannot shadow an accelerated frame buffer.
[    19.117] (II) MACH64(0): Engine XCLK 62.353 MHz;  Refresh rate code 1.
[    19.117] (--) MACH64(0): Internal programmable clock generator detected.
[    19.117] (--) MACH64(0): Reference clock 157.5/11 (14.318) MHz.
[    19.117] (II) MACH64(0): <default monitor>: Using default hsync range of 31.50-48.00 kHz
[    19.117] (II) MACH64(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[    19.117] (II) MACH64(0): <default monitor>: Using default maximum pixel clock of 65.00 MHz
[    19.117] (WW) MACH64(0): Unable to estimate virtual size
[    19.117] (II) MACH64(0): Maximum clock: 124.00 MHz
[    19.117] (II) MACH64(0): Not using default mode "640x350" (vrefresh out of range)
[    19.117] (II) MACH64(0): Not using default mode "320x175" (vrefresh out of range)
[    19.117] (II) MACH64(0): Not using default mode "640x400" (vrefresh out of range)
[    19.117] (II) MACH64(0): Not using default mode "320x200" (vrefresh out of range)
[    19.117] (II) MACH64(0): Not using default mode "720x400" (vrefresh out of range)
[    19.117] (II) MACH64(0): Not using default mode "360x200" (vrefresh out of range)
[    19.117] (II) MACH64(0): Not using default mode "640x480" (vrefresh out of range)
[    19.117] (II) MACH64(0): Not using default mode "320x240" (vrefresh out of range)
[    19.117] (II) MACH64(0): Not using default mode "640x480" (vrefresh out of range)
[    19.117] (II) MACH64(0): Not using default mode "320x240" (vrefresh out of range)
[    19.117] (II) MACH64(0): Not using default mode "640x480" (vrefresh out of range)
[    19.117] (II) MACH64(0): Not using default mode "320x240" (vrefresh out of range)
[    19.117] (II) MACH64(0): Not using default mode "800x600" (vrefresh out of range)
[    19.117] (II) MACH64(0): Not using default mode "400x300" (vrefresh out of range)
[    19.117] (II) MACH64(0): Not using default mode "800x600" (vrefresh out of range)
[    19.117] (II) MACH64(0): Not using default mode "400x300" (vrefresh out of range)
[    19.117] (II) MACH64(0): Not using default mode "800x600" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "400x300" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1024x768i" (vrefresh out of range)
[    19.118] (II) MACH64(0): Not using default mode "512x384i" (vrefresh out of range)
[    19.118] (II) MACH64(0): Not using default mode "1024x768" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "512x384" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1024x768" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "512x384" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1024x768" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "512x384" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "576x432" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1280x960" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "640x480" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
[    19.118] (II) MACH64(0): Not using default mode "640x480" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1280x1024" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "640x512" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
[    19.118] (II) MACH64(0): Not using default mode "640x512" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
[    19.118] (II) MACH64(0): Not using default mode "640x512" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[    19.118] (II) MACH64(0): Not using default mode "800x600" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[    19.118] (II) MACH64(0): Not using default mode "800x600" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[    19.118] (II) MACH64(0): Not using default mode "800x600" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[    19.118] (II) MACH64(0): Not using default mode "800x600" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[    19.118] (II) MACH64(0): Not using default mode "800x600" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    19.118] (II) MACH64(0): Not using default mode "896x672" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    19.118] (II) MACH64(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[    19.118] (II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    19.118] (II) MACH64(0): Not using default mode "928x696" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    19.118] (II) MACH64(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[    19.118] (II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    19.118] (II) MACH64(0): Not using default mode "960x720" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    19.118] (II) MACH64(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    19.118] (II) MACH64(0): Not using default mode "832x624" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "416x312" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "576x432" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "576x432" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "576x432" (hsync out of range)
[    19.118] (II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "576x432" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "576x432" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
[    19.119] (II) MACH64(0): Not using default mode "576x432" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    19.119] (II) MACH64(0): Not using default mode "1360x768" (mode clock too high)
[    19.119] (II) MACH64(0): Not using default mode "1400x1050" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "700x525" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
[    19.119] (II) MACH64(0): Not using default mode "700x525" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
[    19.119] (II) MACH64(0): Not using default mode "700x525" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
[    19.119] (II) MACH64(0): Not using default mode "700x525" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "1440x900" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "720x450" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "1600x1024" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "800x512" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "1680x1050" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "840x525" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[    19.119] (II) MACH64(0): Not using default mode "840x525" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[    19.119] (II) MACH64(0): Not using default mode "840x525" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[    19.119] (II) MACH64(0): Not using default mode "840x525" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[    19.119] (II) MACH64(0): Not using default mode "840x525" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "1920x1080" (bad mode clock/interlace/doublescan)
[    19.119] (II) MACH64(0): Not using default mode "960x540" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "1920x1200" (insufficient memory for mode)
[    19.119] (II) MACH64(0): Not using default mode "960x600" (hsync out of range)
[    19.119] (II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    19.119] (II) MACH64(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    19.119] (II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    19.119] (II) MACH64(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    19.119] (II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    19.119] (II) MACH64(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    19.119] (II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    19.119] (II) MACH64(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    19.119] (--) MACH64(0): Virtual size is 1024x768 (pitch 1024)
[    19.119] (**) MACH64(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    19.119] (II) MACH64(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    19.119] (**) MACH64(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    19.119] (II) MACH64(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    19.119] (**) MACH64(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[    19.119] (II) MACH64(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    19.120] (**) MACH64(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    19.120] (II) MACH64(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    19.120] (**) MACH64(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
[    19.120] (II) MACH64(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
[    19.120] (**) MACH64(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
[    19.120] (II) MACH64(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
[    19.120] (**) MACH64(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
[    19.120] (II) MACH64(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
[    19.120] (**) MACH64(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
[    19.120] (II) MACH64(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
[    19.120] (**) MACH64(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
[    19.120] (II) MACH64(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
[    19.120] (**) MACH64(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
[    19.120] (II) MACH64(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
[    19.120] (==) MACH64(0): DPI set to (96, 96)
[    19.120] (II) Loading sub module "fb"
[    19.120] (II) LoadModule: "fb"
[    19.120] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.120] (II) Module fb: vendor="X.Org Foundation"
[    19.120]     compiled for 1.11.3, module version = 1.0.0
[    19.120]     ABI class: X.Org ANSI C Emulation, version 0.4
[    19.120] (II) Loading sub module "ramdac"
[    19.120] (II) LoadModule: "ramdac"
[    19.121] (II) Module "ramdac" already built-in
[    19.121] (II) Loading sub module "xaa"
[    19.121] (II) LoadModule: "xaa"
[    19.121] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    19.121] (II) Module xaa: vendor="X.Org Foundation"
[    19.121]     compiled for 1.11.3, module version = 1.2.1
[    19.121]     ABI class: X.Org Video Driver, version 11.0
[    19.121] (II) Loading sub module "i2c"
[    19.121] (II) LoadModule: "i2c"
[    19.121] (II) Module "i2c" already built-in
[    19.121] (II) MACH64(0): I2C bus "Mach64" initialized.
[    19.123] (II) UnloadModule: "vesa"
[    19.123] (II) Unloading vesa
[    19.123] (II) UnloadModule: "fbdev"
[    19.123] (II) Unloading fbdev
[    19.123] (II) UnloadModule: "fbdevhw"
[    19.123] (II) Unloading fbdevhw
[    19.123] (--) Depth 24 pixmap format is 32 bpp
[    19.131] (II) MACH64(0): [drm] SAREA 2200+1208: 3408
[    19.131] drmOpenDevice: node name is /dev/dri/card0
[    19.135] drmOpenDevice: node name is /dev/dri/card0
[    19.148] [drm] failed to load kernel module "mach64"
[    19.148] (EE) [drm] drmOpen failed.
[    19.148] (EE) MACH64(0): [dri] DRIScreenInit Failed
[    19.148] (II) MACH64(0): Largest offscreen areas (with overlaps):
[    19.148] (II) MACH64(0):     1024 x 1279 rectangle at 0,768
[    19.148] (II) MACH64(0):     768 x 1280 rectangle at 0,768
[    19.148] (II) MACH64(0): Using XFree86 Acceleration Architecture (XAA)
[    19.149]     Screen to screen bit blits
[    19.149]     Solid filled rectangles
[    19.149]     8x8 mono pattern filled rectangles
[    19.149]     Indirect CPU to Screen color expansion
[    19.149]     Solid Lines
[    19.149]     Setting up tile and stipple cache:
[    19.149]         32 128x128 slots
[    19.149]         10 256x256 slots
[    19.149] (==) MACH64(0): Backing store disabled
[    19.149] (==) MACH64(0): Silken mouse enabled
[    19.152] (==) MACH64(0): DPMS enabled
[    19.152] (II) MACH64(0): Direct rendering disabled
[    19.152] (==) RandR enabled
[    19.152] (II) Initializing built-in extension Generic Event Extension
[    19.152] (II) Initializing built-in extension SHAPE
[    19.152] (II) Initializing built-in extension MIT-SHM
[    19.152] (II) Initializing built-in extension XInputExtension
[    19.152] (II) Initializing built-in extension XTEST
[    19.152] (II) Initializing built-in extension BIG-REQUESTS
[    19.152] (II) Initializing built-in extension SYNC
[    19.152] (II) Initializing built-in extension XKEYBOARD
[    19.152] (II) Initializing built-in extension XC-MISC
[    19.152] (II) Initializing built-in extension SECURITY
[    19.152] (II) Initializing built-in extension XINERAMA
[    19.152] (II) Initializing built-in extension XFIXES
[    19.152] (II) Initializing built-in extension RENDER
[    19.152] (II) Initializing built-in extension RANDR
[    19.152] (II) Initializing built-in extension COMPOSITE
[    19.152] (II) Initializing built-in extension DAMAGE
[    19.168] (II) AIGLX: Screen 0 is not DRI2 capable
[    19.168] (II) AIGLX: Screen 0 is not DRI capable
[    19.200] (II) AIGLX: Loaded and initialized swrast
[    19.200] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    19.220] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.227] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    19.227] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.227] (II) LoadModule: "evdev"
[    19.228] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.228] (II) Module evdev: vendor="X.Org Foundation"
[    19.228]     compiled for 1.11.3, module version = 2.7.0
[    19.228]     Module class: X.Org XInput Driver
[    19.228]     ABI class: X.Org XInput driver, version 16.0
[    19.229] (II) Using input driver 'evdev' for 'Power Button'
[    19.229] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.229] (**) Power Button: always reports core events
[    19.229] (**) evdev: Power Button: Device: "/dev/input/event1"
[    19.229] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.229] (--) evdev: Power Button: Found keys
[    19.229] (II) evdev: Power Button: Configuring as keyboard
[    19.229] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    19.229] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    19.229] (**) Option "xkb_rules" "evdev"
[    19.229] (**) Option "xkb_model" "pc105"
[    19.229] (**) Option "xkb_layout" "za"
[    19.237] (II) XKB: reuse xkmfile /var/lib/xkb/server-BCF7C4B78F6775858E983A1661EA7F5FD69F5903.xkm
[    19.238] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    19.238] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.239] (II) Using input driver 'evdev' for 'Power Button'
[    19.239] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.239] (**) Power Button: always reports core events
[    19.239] (**) evdev: Power Button: Device: "/dev/input/event0"
[    19.239] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.239] (--) evdev: Power Button: Found keys
[    19.239] (II) evdev: Power Button: Configuring as keyboard
[    19.239] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    19.239] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    19.239] (**) Option "xkb_rules" "evdev"
[    19.239] (**) Option "xkb_model" "pc105"
[    19.239] (**) Option "xkb_layout" "za"
[    19.240] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    19.240] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    19.240] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    19.240] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.240] (**) Logitech USB Receiver: always reports core events
[    19.240] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event2"
[    19.241] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc517
[    19.241] (--) evdev: Logitech USB Receiver: Found keys
[    19.241] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    19.241] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input2/event2"
[    19.241] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 8)
[    19.241] (**) Option "xkb_rules" "evdev"
[    19.241] (**) Option "xkb_model" "pc105"
[    19.241] (**) Option "xkb_layout" "za"
[    19.242] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    19.242] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    19.242] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    19.242] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    19.242] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.242] (**) Logitech USB Receiver: always reports core events
[    19.242] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event3"
[    19.242] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc517
[    19.242] (--) evdev: Logitech USB Receiver: Found 12 mouse buttons
[    19.242] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    19.242] (--) evdev: Logitech USB Receiver: Found relative axes
[    19.242] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[    19.242] (--) evdev: Logitech USB Receiver: Found absolute axes
[    19.242] (II) evdev: Logitech USB Receiver: Forcing absolute x/y axes to exist.
[    19.242] (--) evdev: Logitech USB Receiver: Found keys
[    19.243] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    19.243] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    19.243] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    19.243] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    19.243] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.243] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input3/event3"
[    19.243] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 9)
[    19.243] (**) Option "xkb_rules" "evdev"
[    19.243] (**) Option "xkb_model" "pc105"
[    19.243] (**) Option "xkb_layout" "za"
[    19.243] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    19.243] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.
[    19.244] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    19.244] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    19.244] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    19.244] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    19.245] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    19.245] (II) No input driver specified, ignoring this device.
[    19.245] (II) This device may have been added with another device file.
[    47.608] (II) XKB: reuse xkmfile /var/lib/xkb/server-46A88BF1E1D409377117604E95C2D723F90517D8.xkm


Thanks...

---

### Post by mörgæs on 2013-09-12
```
ATI 3D Rage XL or XC graphics controller detected
ATI Mach64 adapter detected
```

indicates really old hardware. With this graphics card you should be happy for just getting some kind of picture. Don't expect anything luxury! 

Your best option is a reinstall of Lubuntu 13.04.

---

### Post by Yellow Pasque on 2013-09-12
> Your best option is a reinstall of Lubuntu 13.04
The user should be aware of this bug (and the "noaccel" workaround) [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mach64/+bug/1077975](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mach64/+bug/1077975)

Before messing with another version, the first thing I would do is install another desktop (lxde or Unity2D) in the current install to rule out problems specific to Unity.

EDIT: just saw this updated xorg-mach64 package that may help mach64 users: [https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=raring](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=raring)

---

### Post by EngineersGarage on 2013-09-13
Hi guys,

Thanks for the help and your time...

I just want to menton that I was running Mint 12 before I decided to run ubuntu again... I had absolute no problems with Mint12... I'm starting to think I should switch back to Mint12.. I could watch any format with no problem... Its just that I wanted to start using wine to play windows games and  to network my windows pc's with my linux ones. A friend told me it would be easier to accomplish this with ubuntu... 

Thank again.

---

### Post by mörgæs on 2013-09-13
If you want to give Buntu a last chance you could try

```
sudo apt-get install lubuntu-desktop
```

which will give you a much lighter environment than Ubuntu.


Mint 12 is obsolete. If you go back to this family you should take one of the supported versions.

---


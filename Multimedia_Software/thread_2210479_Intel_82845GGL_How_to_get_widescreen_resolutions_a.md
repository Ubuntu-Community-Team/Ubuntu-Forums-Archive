---
title: "Intel 82845G/GL: How to get widescreen resolutions as an option?"
date: 2014-03-11
forum: Multimedia Software
---

### Post by snazzierella on 2014-03-11
I have an older computer with lubuntu on it. My monitor supports up to 1600x900, but the maximum resolution it's letting me use is 1280x1024. I've read about using xrandr and this is what I've done so far but I keep getting various errors and then I'm not sure what to do:

```
$ sudo xrandr --newmode "1280x720_60.00" 74.50 1280 1344 1472 1664 720 723 728 748 -hsync +vsync
```

which tells me 

```
xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19

```
but it creates the mode anyway, and then I did 

```
$ xrandr --addmode default "1280x720_60.00"

```
and I get this error again
```

xrandr: Failed to get size of gamma for output default

```
but it adds the mode to the list anyway as you can see from the xrandr output:

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  
   1280x720_60.00   59.9
``` 



then if I try
```
$ xrandr --output default --mode 1280x720_60.00
```

I get:

```
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed

```
and if I try
```
$ xrandr --fb 1280x720
```

I get this instead:


```
xrandr: Failed to get size of gamma for output default
xrandr: specified screen 1280x720 not large enough for output default (1280x1024+0+0)

```

I've also run ddcprobe, which gives me this information:
```
vbe: VESA 3.0 detected.
oem: Intel(r)845G/845GL/845GE/845GV Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)845G/845GL/845GE/845GV Graphics Controller Hardware Version 0.0
memory: 8000kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: 2904
eisa: HWP2904
serial: 01010101
manufacture: 25 2010
input: sync on green, analog signal.
screensize: 44 25
gamma: 2.200000
dpms: RGB, active off, no suspend, no standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 1024x768@87 Hz Interlaced (8514A)
ctiming: 1280x800@60
ctiming: 1280x1024@60
ctiming: 1440x1440@60
ctiming: 1600x1000@60
dtiming: 1600x900@60
monitorrange: 24-83, 50-76
monitorname: HP S2031
monitorserial: 3CQ0250DGC

```

If anyone can help me get on the right path to fixing this, I'd appreciate it.

---

### Post by Bucky Ball on 2014-03-11
*Thread moved to **Multimedia & Video**.*

Perhaps try arandr, the GUI. See what resolutions that offers off the bat. It is in the repositories (Software Centre or 'sudo apt-get install arandr' in a terminal). It should then be in your menu somewhere.

---

### Post by snazzierella on 2014-03-11
I opened arandr, went to outputs>default>resolution>1280x72060.00 (the resolution I added to the list earlier using xrandr in the terminal, it also shows the other resolutions xrandr lists) and then clicked the checkmark, and it told me 
"XRandR failed:XRandR returned error code 1: xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed"
so same error, different way of getting it.

---

### Post by Bucky Ball on 2014-03-11
Which Lubuntu release number are you using? (12.04, 13.10, etc.)

---

### Post by snazzierella on 2014-03-11
I'm on 13.10.

---

### Post by ajgreeny on 2014-03-11
What hardware do you have, particularly the graphics card?

One thing you could try is to write your own **/etc/X11/xorg.conf** file and see if that works; normally that file does not exist, but if it's there, it is read and used by the system. Simply add the following to the file, save it, as root of course, and then logout and in again.
```
Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1600x900" "1280x720" # Add other resolutions you might need here in same pattern
    EndSubSection
EndSection
```

---

### Post by snazzierella on 2014-03-11
Pretty sure this is my graphics card: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)

Added a xorg.conf file, pasted the code from above into it, saved, rebooted, and I'm still getting the same error from both arandr and xrandr in the terminal,
"[COLOR=#000000]XRandR failed:XRandR returned error code 1: xrandr: Failed to get size of gamma for output default[/COLOR]
[COLOR=#000000]xrandr: Configure crtc 0 failed"

[/COLOR]

---

### Post by Yellow Pasque on 2014-03-11
Post /var/log/Xorg.0.log
Use code tags.

---

### Post by snazzierella on 2014-03-11
Contents of /var/log/Xorg.0.log:
```
    29.153] X.Org X Server 1.14.5
Release Date: 2013-12-12
[    29.153] X Protocol Version 11, Revision 0
[    29.153] Build Operating System: Linux 3.2.0-54-generic i686 Ubuntu
[    29.153] Current Operating System: Linux gravytrain 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:53:31 UTC 2014 i686
[    29.153] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-17-generic root=UUID=ef7bfffe-2a36-4dd9-b2e5-48af6a4b75aa ro quiet splash vt.handoff=7
[    29.153] Build Date: 17 December 2013  10:03:52AM
[    29.153] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see http://www.ubuntu.com/support) 
[    29.153] Current version of pixman: 0.30.2
[    29.153]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.153] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.153] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 11 13:03:57 2014
[    29.154] (==) Using config file: "/etc/X11/xorg.conf"
[    29.154] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.192] (==) No Layout section.  Using the first Screen section.
[    29.193] (**) |-->Screen "Default Screen" (0)
[    29.193] (**) |   |-->Monitor "<default monitor>"
[    29.193] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    29.193] (==) Automatically adding devices
[    29.193] (==) Automatically enabling devices
[    29.193] (==) Automatically adding GPU devices
[    29.193] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.193]     Entry deleted from font path.
[    29.193] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.193]     Entry deleted from font path.
[    29.193] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.193]     Entry deleted from font path.
[    29.193] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.193]     Entry deleted from font path.
[    29.193] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.193]     Entry deleted from font path.
[    29.193] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.193] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.193] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.194] (II) Loader magic: 0xb77556a0
[    29.194] (II) Module ABI versions:
[    29.194]     X.Org ANSI C Emulation: 0.4
[    29.194]     X.Org Video Driver: 14.1
[    29.194]     X.Org XInput driver : 19.1
[    29.194]     X.Org Server Extension : 7.0
[    29.195] (--) PCI:*(0:0:2:0) 8086:2562:1462:5778 rev 3, Mem @ 0xe0000000/134217728, 0xee000000/524288
[    29.197] (II) Open ACPI successful (/var/run/acpid.socket)
[    29.197] Initializing built-in extension Generic Event Extension
[    29.197] Initializing built-in extension SHAPE
[    29.197] Initializing built-in extension MIT-SHM
[    29.197] Initializing built-in extension XInputExtension
[    29.197] Initializing built-in extension XTEST
[    29.197] Initializing built-in extension BIG-REQUESTS
[    29.197] Initializing built-in extension SYNC
[    29.197] Initializing built-in extension XKEYBOARD
[    29.198] Initializing built-in extension XC-MISC
[    29.198] Initializing built-in extension SECURITY
[    29.198] Initializing built-in extension XINERAMA
[    29.198] Initializing built-in extension XFIXES
[    29.198] Initializing built-in extension RENDER
[    29.198] Initializing built-in extension RANDR
[    29.198] Initializing built-in extension COMPOSITE
[    29.198] Initializing built-in extension DAMAGE
[    29.198] Initializing built-in extension MIT-SCREEN-SAVER
[    29.198] Initializing built-in extension DOUBLE-BUFFER
[    29.198] Initializing built-in extension RECORD
[    29.198] Initializing built-in extension DPMS
[    29.198] Initializing built-in extension X-Resource
[    29.198] Initializing built-in extension XVideo
[    29.198] Initializing built-in extension XVideo-MotionCompensation
[    29.198] Initializing built-in extension SELinux
[    29.198] Initializing built-in extension XFree86-VidModeExtension
[    29.198] Initializing built-in extension XFree86-DGA
[    29.198] Initializing built-in extension XFree86-DRI
[    29.198] Initializing built-in extension DRI2
[    29.198] (II) "glx" will be loaded by default.
[    29.198] (WW) "xmir" is not to be loaded by default. Skipping.
[    29.198] (II) LoadModule: "dri2"
[    29.198] (II) Module "dri2" already built-in
[    29.198] (II) LoadModule: "glamoregl"
[    29.311] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    29.786] (II) Module glamoregl: vendor="X.Org Foundation"
[    29.786]     compiled for 1.14.3, module version = 0.5.1
[    29.786]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.786] (II) LoadModule: "glx"
[    29.786] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    29.787] (II) Module glx: vendor="X.Org Foundation"
[    29.787]     compiled for 1.14.5, module version = 1.0.0
[    29.787]     ABI class: X.Org Server Extension, version 7.0
[    29.787] (==) AIGLX enabled
[    29.787] Loading extension GLX
[    29.787] (==) Matched intel as autoconfigured driver 0
[    29.787] (==) Matched vesa as autoconfigured driver 1
[    29.787] (==) Matched modesetting as autoconfigured driver 2
[    29.787] (==) Matched fbdev as autoconfigured driver 3
[    29.787] (==) Assigned the driver to the xf86ConfigLayout
[    29.787] (II) LoadModule: "intel"
[    29.787] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    29.851] (II) Module intel: vendor="X.Org Foundation"
[    29.851]     compiled for 1.14.5, module version = 2.99.904
[    29.851]     Module class: X.Org Video Driver
[    29.851]     ABI class: X.Org Video Driver, version 14.1
[    29.851] (II) LoadModule: "vesa"
[    29.852] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.852] (II) Module vesa: vendor="X.Org Foundation"
[    29.852]     compiled for 1.14.1, module version = 2.3.2
[    29.852]     Module class: X.Org Video Driver
[    29.852]     ABI class: X.Org Video Driver, version 14.1
[    29.853] (II) LoadModule: "modesetting"
[    29.853] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    29.853] (II) Module modesetting: vendor="X.Org Foundation"
[    29.853]     compiled for 1.14.1, module version = 0.8.0
[    29.853]     Module class: X.Org Video Driver
[    29.853]     ABI class: X.Org Video Driver, version 14.1
[    29.854] (II) LoadModule: "fbdev"
[    29.854] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.854] (II) Module fbdev: vendor="X.Org Foundation"
[    29.854]     compiled for 1.14.1, module version = 0.4.3
[    29.854]     Module class: X.Org Video Driver
[    29.854]     ABI class: X.Org Video Driver, version 14.1
[    29.854] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43, HD Graphics,
    HD Graphics 2000, HD Graphics 3000, HD Graphics 2500,
    HD Graphics 4000, HD Graphics P4000, HD Graphics 4600,
    HD Graphics 5000, HD Graphics P4600/P4700, Iris(TM) Graphics 5100,
    HD Graphics 4400, HD Graphics 4200, Iris(TM) Pro Graphics 5200
[    29.855] (II) VESA: driver for VESA chipsets: vesa
[    29.855] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    29.855] (II) FBDEV: driver for framebuffer: fbdev
[    29.855] (++) using VT number 7


[    29.911] (WW) Falling back to old probe method for modesetting
[    29.911] (EE) open /dev/dri/card0: No such file or directory
[    29.911] (WW) Falling back to old probe method for fbdev
[    29.912] (II) Loading sub module "fbdevhw"
[    29.912] (II) LoadModule: "fbdevhw"
[    29.912] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    29.912] (II) Module fbdevhw: vendor="X.Org Foundation"
[    29.912]     compiled for 1.14.5, module version = 0.0.2
[    29.912]     ABI class: X.Org Video Driver, version 14.1
[    29.920] (II) Loading sub module "vbe"
[    29.920] (II) LoadModule: "vbe"
[    29.920] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    29.921] (II) Module vbe: vendor="X.Org Foundation"
[    29.921]     compiled for 1.14.5, module version = 1.1.0
[    29.921]     ABI class: X.Org Video Driver, version 14.1
[    29.921] (II) Loading sub module "int10"
[    29.921] (II) LoadModule: "int10"
[    29.928] (II) Loading /usr/lib/xorg/modules/libint10.so
[    29.928] (II) Module int10: vendor="X.Org Foundation"
[    29.928]     compiled for 1.14.5, module version = 1.0.0
[    29.928]     ABI class: X.Org Video Driver, version 14.1
[    29.928] (II) VESA(0): initializing int10
[    29.979] (II) VESA(0): Bad V_BIOS checksum
[    29.979] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    29.980] (II) VESA(0): VESA BIOS detected
[    29.980] (II) VESA(0): VESA VBE Version 3.0
[    29.980] (II) VESA(0): VESA VBE Total Mem: 8000 kB
[    29.980] (II) VESA(0): VESA VBE OEM: Intel(r)845G/845GL/845GE/845GV Graphics Chip Accelerated VGA BIOS
[    29.980] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    29.980] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    29.980] (II) VESA(0): VESA VBE OEM Product: Intel(r)845G/845GL/845GE/845GV Graphics Controller
[    29.980] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    30.337] (**) VESA(0): Depth 24, (--) framebuffer bpp 32
[    30.337] (==) VESA(0): RGB weight 888
[    30.337] (==) VESA(0): Default visual is TrueColor
[    30.337] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.337] (II) Loading sub module "ddc"
[    30.337] (II) LoadModule: "ddc"
[    30.337] (II) Module "ddc" already built-in
[    30.452] (II) VESA(0): VESA VBE DDC supported
[    30.452] (II) VESA(0): VESA VBE DDC Level 2
[    30.452] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    30.544] (II) VESA(0): VESA VBE DDC read successfully
[    30.544] (II) VESA(0): Manufacturer: HWP  Model: 2904  Serial#: 16843009
[    30.544] (II) VESA(0): Year: 2010  Week: 25
[    30.544] (II) VESA(0): EDID Version: 1.3
[    30.544] (II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    30.544] (II) VESA(0): Sync:  Separate
[    30.544] (II) VESA(0): Max Image Size [cm]: horiz.: 44  vert.: 25
[    30.544] (II) VESA(0): Gamma: 2.20
[    30.544] (II) VESA(0): DPMS capabilities: Off; RGB/Color Display
[    30.544] (II) VESA(0): Default color space is primary color space
[    30.544] (II) VESA(0): First detailed timing is preferred mode
[    30.544] (II) VESA(0): redX: 0.648 redY: 0.336   greenX: 0.294 greenY: 0.607
[    30.544] (II) VESA(0): blueX: 0.145 blueY: 0.064   whiteX: 0.313 whiteY: 0.329
[    30.544] (II) VESA(0): Supported established timings:
[    30.544] (II) VESA(0): 720x400@70Hz
[    30.544] (II) VESA(0): 640x480@60Hz
[    30.544] (II) VESA(0): 800x600@60Hz
[    30.544] (II) VESA(0): 1024x768@60Hz
[    30.544] (II) VESA(0): Manufacturer's mask: 0
[    30.544] (II) VESA(0): Supported standard timings:
[    30.544] (II) VESA(0): #0: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    30.544] (II) VESA(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    30.544] (II) VESA(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    30.544] (II) VESA(0): #3: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[    30.544] (II) VESA(0): Supported detailed timing:
[    30.544] (II) VESA(0): clock: 108.0 MHz   Image Size:  443 x 249 mm
[    30.544] (II) VESA(0): h_active: 1600  h_sync: 1624  h_sync_end 1704 h_blank_end 1800 h_border: 0
[    30.544] (II) VESA(0): v_active: 900  v_sync: 901  v_sync_end 904 v_blanking: 1000 v_border: 0
[    30.544] (II) VESA(0): Ranges: V min: 50 V max: 76 Hz, H min: 24 H max: 83 kHz, PixClock max 175 MHz
[    30.545] (II) VESA(0): Monitor name: HP S2031
[    30.545] (II) VESA(0): Serial No: 3CQ0250DGC
[    30.545] (II) VESA(0): EDID (in hex):
[    30.545] (II) VESA(0):     00ffffffffffff0022f0042901010101
[    30.545] (II) VESA(0):     19140103682c19782e0625a6564b9b25
[    30.545] (II) VESA(0):     105054a1080081c081809500a9c00101
[    30.545] (II) VESA(0):     010101010101302a40c8608464301850
[    30.545] (II) VESA(0):     1300bbf91000001e000000fd00324c18
[    30.545] (II) VESA(0):     5311000a202020202020000000fc0048
[    30.545] (II) VESA(0):     502053323033310a20202020000000ff
[    30.545] (II) VESA(0):     00334351303235304447430a20200074
[    30.545] (II) VESA(0): EDID vendor "HWP", prod id 10500
[    30.545] (II) VESA(0): Using EDID range info for horizontal sync
[    30.545] (II) VESA(0): Using EDID range info for vertical refresh
[    30.545] (II) VESA(0): Printing DDC gathered Modelines:
[    30.545] (II) VESA(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz eP)
[    30.545] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    30.545] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    30.545] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    30.545] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    30.545] (II) VESA(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    30.545] (II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    30.545] (II) VESA(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    30.561] (II) VESA(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    30.561] (II) VESA(0): Searching for matching VESA mode(s):
[    30.566] Mode: 160 (0x0)
[    30.566]     ModeAttributes: 0x0
[    30.566]     WinAAttributes: 0x0
[    30.566]     WinBAttributes: 0x0
[    30.566]     WinGranularity: 0
[    30.566]     WinSize: 0
[    30.566]     WinASegment: 0x0
[    30.566]     WinBSegment: 0x0
[    30.566]     WinFuncPtr: 0x0
[    30.566]     BytesPerScanline: 0
[    30.566]     XResolution: 0
[    30.566]     YResolution: 0
[    30.566]     XCharSize: 0
[    30.566]     YCharSize: 0
[    30.566]     NumberOfPlanes: 0
[    30.566]     BitsPerPixel: 0
[    30.566]     NumberOfBanks: 0
[    30.566]     MemoryModel: 0
[    30.566]     BankSize: 0
[    30.566]     NumberOfImages: 0
[    30.566]     RedMaskSize: 0
[    30.566]     RedFieldPosition: 0
[    30.566]     GreenMaskSize: 0
[    30.566]     GreenFieldPosition: 0
[    30.566]     BlueMaskSize: 0
[    30.566]     BlueFieldPosition: 0
[    30.566]     RsvdMaskSize: 0
[    30.566]     RsvdFieldPosition: 0
[    30.566]     DirectColorModeInfo: 0
[    30.566]     PhysBasePtr: 0x0
[    30.566]     LinBytesPerScanLine: 0
[    30.566]     BnkNumberOfImagePages: 0
[    30.566]     LinNumberOfImagePages: 0
[    30.566]     LinRedMaskSize: 0
[    30.566]     LinRedFieldPosition: 0
[    30.566]     LinGreenMaskSize: 0
[    30.567]     LinGreenFieldPosition: 0
[    30.567]     LinBlueMaskSize: 0
[    30.567]     LinBlueFieldPosition: 0
[    30.567]     LinRsvdMaskSize: 0
[    30.567]     LinRsvdFieldPosition: 0
[    30.567]     MaxPixelClock: 0
[    30.567] Mode: 161 (0x0)
[    30.567]     ModeAttributes: 0x0
[    30.567]     WinAAttributes: 0x0
[    30.567]     WinBAttributes: 0x0
[    30.567]     WinGranularity: 0
[    30.567]     WinSize: 0
[    30.567]     WinASegment: 0x0
[    30.567]     WinBSegment: 0x0
[    30.567]     WinFuncPtr: 0x0
[    30.568]     BytesPerScanline: 0
[    30.568]     XResolution: 0
[    30.568]     YResolution: 0
[    30.568]     XCharSize: 0
[    30.568]     YCharSize: 0
[    30.568]     NumberOfPlanes: 0
[    30.568]     BitsPerPixel: 0
[    30.568]     NumberOfBanks: 0
[    30.568]     MemoryModel: 0
[    30.568]     BankSize: 0
[    30.568]     NumberOfImages: 0
[    30.568]     RedMaskSize: 0
[    30.568]     RedFieldPosition: 0
[    30.568]     GreenMaskSize: 0
[    30.568]     GreenFieldPosition: 0
[    30.568]     BlueMaskSize: 0
[    30.568]     BlueFieldPosition: 0
[    30.568]     RsvdMaskSize: 0
[    30.568]     RsvdFieldPosition: 0
[    30.568]     DirectColorModeInfo: 0
[    30.568]     PhysBasePtr: 0x0
[    30.568]     LinBytesPerScanLine: 0
[    30.568]     BnkNumberOfImagePages: 0
[    30.568]     LinNumberOfImagePages: 0
[    30.568]     LinRedMaskSize: 0
[    30.568]     LinRedFieldPosition: 0
[    30.568]     LinGreenMaskSize: 0
[    30.568]     LinGreenFieldPosition: 0
[    30.568]     LinBlueMaskSize: 0
[    30.568]     LinBlueFieldPosition: 0
[    30.568]     LinRsvdMaskSize: 0
[    30.568]     LinRsvdFieldPosition: 0
[    30.568]     MaxPixelClock: 0
[    30.569] Mode: 162 (0x0)
[    30.569]     ModeAttributes: 0x0
[    30.569]     WinAAttributes: 0x0
[    30.569]     WinBAttributes: 0x0
[    30.569]     WinGranularity: 0
[    30.569]     WinSize: 0
[    30.569]     WinASegment: 0x0
[    30.569]     WinBSegment: 0x0
[    30.569]     WinFuncPtr: 0x0
[    30.569]     BytesPerScanline: 0
[    30.569]     XResolution: 0
[    30.569]     YResolution: 0
[    30.569]     XCharSize: 0
[    30.569]     YCharSize: 0
[    30.569]     NumberOfPlanes: 0
[    30.569]     BitsPerPixel: 0
[    30.569]     NumberOfBanks: 0
[    30.569]     MemoryModel: 0
[    30.569]     BankSize: 0
[    30.569]     NumberOfImages: 0
[    30.569]     RedMaskSize: 0
[    30.569]     RedFieldPosition: 0
[    30.586]     GreenMaskSize: 0
[    30.586]     GreenFieldPosition: 0
[    30.586]     BlueMaskSize: 0
[    30.586]     BlueFieldPosition: 0
[    30.586]     RsvdMaskSize: 0
[    30.586]     RsvdFieldPosition: 0
[    30.586]     DirectColorModeInfo: 0
[    30.586]     PhysBasePtr: 0x0
[    30.586]     LinBytesPerScanLine: 0
[    30.586]     BnkNumberOfImagePages: 0
[    30.586]     LinNumberOfImagePages: 0
[    30.586]     LinRedMaskSize: 0
[    30.586]     LinRedFieldPosition: 0
[    30.586]     LinGreenMaskSize: 0
[    30.586]     LinGreenFieldPosition: 0
[    30.586]     LinBlueMaskSize: 0
[    30.586]     LinBlueFieldPosition: 0
[    30.586]     LinRsvdMaskSize: 0
[    30.586]     LinRsvdFieldPosition: 0
[    30.586]     MaxPixelClock: 0
[    30.587] Mode: 163 (0x0)
[    30.587]     ModeAttributes: 0x0
[    30.587]     WinAAttributes: 0x0
[    30.587]     WinBAttributes: 0x0
[    30.587]     WinGranularity: 0
[    30.587]     WinSize: 0
[    30.587]     WinASegment: 0x0
[    30.587]     WinBSegment: 0x0
[    30.587]     WinFuncPtr: 0x0
[    30.587]     BytesPerScanline: 0
[    30.587]     XResolution: 0
[    30.587]     YResolution: 0
[    30.587]     XCharSize: 0
[    30.587]     YCharSize: 0
[    30.587]     NumberOfPlanes: 0
[    30.587]     BitsPerPixel: 0
[    30.587]     NumberOfBanks: 0
[    30.587]     MemoryModel: 0
[    30.587]     BankSize: 0
[    30.587]     NumberOfImages: 0
[    30.587]     RedMaskSize: 0
[    30.587]     RedFieldPosition: 0
[    30.587]     GreenMaskSize: 0
[    30.587]     GreenFieldPosition: 0
[    30.587]     BlueMaskSize: 0
[    30.587]     BlueFieldPosition: 0
[    30.587]     RsvdMaskSize: 0
[    30.587]     RsvdFieldPosition: 0
[    30.587]     DirectColorModeInfo: 0
[    30.587]     PhysBasePtr: 0x0
[    30.587]     LinBytesPerScanLine: 0
[    30.587]     BnkNumberOfImagePages: 0
[    30.587]     LinNumberOfImagePages: 0
[    30.587]     LinRedMaskSize: 0
[    30.587]     LinRedFieldPosition: 0
[    30.587]     LinGreenMaskSize: 0
[    30.587]     LinGreenFieldPosition: 0
[    30.587]     LinBlueMaskSize: 0
[    30.587]     LinBlueFieldPosition: 0
[    30.587]     LinRsvdMaskSize: 0
[    30.587]     LinRsvdFieldPosition: 0
[    30.587]     MaxPixelClock: 0
[    30.588] Mode: 164 (0x0)
[    30.588]     ModeAttributes: 0x0
[    30.588]     WinAAttributes: 0x0
[    30.588]     WinBAttributes: 0x0
[    30.588]     WinGranularity: 0
[    30.588]     WinSize: 0
[    30.588]     WinASegment: 0x0
[    30.588]     WinBSegment: 0x0
[    30.588]     WinFuncPtr: 0x0
[    30.588]     BytesPerScanline: 0
[    30.588]     XResolution: 0
[    30.588]     YResolution: 0
[    30.588]     XCharSize: 0
[    30.588]     YCharSize: 0
[    30.588]     NumberOfPlanes: 0
[    30.588]     BitsPerPixel: 0
[    30.588]     NumberOfBanks: 0
[    30.588]     MemoryModel: 0
[    30.588]     BankSize: 0
[    30.588]     NumberOfImages: 0
[    30.588]     RedMaskSize: 0
[    30.588]     RedFieldPosition: 0
[    30.588]     GreenMaskSize: 0
[    30.588]     GreenFieldPosition: 0
[    30.588]     BlueMaskSize: 0
[    30.588]     BlueFieldPosition: 0
[    30.588]     RsvdMaskSize: 0
[    30.589]     RsvdFieldPosition: 0
[    30.589]     DirectColorModeInfo: 0
[    30.589]     PhysBasePtr: 0x0
[    30.589]     LinBytesPerScanLine: 0
[    30.589]     BnkNumberOfImagePages: 0
[    30.589]     LinNumberOfImagePages: 0
[    30.589]     LinRedMaskSize: 0
[    30.589]     LinRedFieldPosition: 0
[    30.589]     LinGreenMaskSize: 0
[    30.589]     LinGreenFieldPosition: 0
[    30.589]     LinBlueMaskSize: 0
[    30.589]     LinBlueFieldPosition: 0
[    30.589]     LinRsvdMaskSize: 0
[    30.589]     LinRsvdFieldPosition: 0
[    30.589]     MaxPixelClock: 0
[    30.604] Mode: 165 (0x0)
[    30.604]     ModeAttributes: 0x0
[    30.604]     WinAAttributes: 0x0
[    30.604]     WinBAttributes: 0x0
[    30.604]     WinGranularity: 0
[    30.604]     WinSize: 0
[    30.604]     WinASegment: 0x0
[    30.604]     WinBSegment: 0x0
[    30.604]     WinFuncPtr: 0x0
[    30.604]     BytesPerScanline: 0
[    30.604]     XResolution: 0
[    30.604]     YResolution: 0
[    30.604]     XCharSize: 0
[    30.604]     YCharSize: 0
[    30.604]     NumberOfPlanes: 0
[    30.604]     BitsPerPixel: 0
[    30.604]     NumberOfBanks: 0
[    30.604]     MemoryModel: 0
[    30.604]     BankSize: 0
[    30.604]     NumberOfImages: 0
[    30.604]     RedMaskSize: 0
[    30.604]     RedFieldPosition: 0
[    30.604]     GreenMaskSize: 0
[    30.604]     GreenFieldPosition: 0
[    30.604]     BlueMaskSize: 0
[    30.604]     BlueFieldPosition: 0
[    30.604]     RsvdMaskSize: 0
[    30.604]     RsvdFieldPosition: 0
[    30.604]     DirectColorModeInfo: 0
[    30.604]     PhysBasePtr: 0x0
[    30.604]     LinBytesPerScanLine: 0
[    30.604]     BnkNumberOfImagePages: 0
[    30.604]     LinNumberOfImagePages: 0
[    30.604]     LinRedMaskSize: 0
[    30.604]     LinRedFieldPosition: 0
[    30.604]     LinGreenMaskSize: 0
[    30.604]     LinGreenFieldPosition: 0
[    30.604]     LinBlueMaskSize: 0
[    30.604]     LinBlueFieldPosition: 0
[    30.604]     LinRsvdMaskSize: 0
[    30.604]     LinRsvdFieldPosition: 0
[    30.604]     MaxPixelClock: 0
[    30.608] Mode: 166 (0x0)
[    30.608]     ModeAttributes: 0x0
[    30.609]     WinAAttributes: 0x0
[    30.609]     WinBAttributes: 0x0
[    30.609]     WinGranularity: 0
[    30.609]     WinSize: 0
[    30.609]     WinASegment: 0x0
[    30.609]     WinBSegment: 0x0
[    30.609]     WinFuncPtr: 0x0
[    30.609]     BytesPerScanline: 0
[    30.609]     XResolution: 0
[    30.609]     YResolution: 0
[    30.609]     XCharSize: 0
[    30.609]     YCharSize: 0
[    30.609]     NumberOfPlanes: 0
[    30.609]     BitsPerPixel: 0
[    30.609]     NumberOfBanks: 0
[    30.609]     MemoryModel: 0
[    30.609]     BankSize: 0
[    30.609]     NumberOfImages: 0
[    30.609]     RedMaskSize: 0
[    30.609]     RedFieldPosition: 0
[    30.609]     GreenMaskSize: 0
[    30.609]     GreenFieldPosition: 0
[    30.609]     BlueMaskSize: 0
[    30.609]     BlueFieldPosition: 0
[    30.609]     RsvdMaskSize: 0
[    30.609]     RsvdFieldPosition: 0
[    30.609]     DirectColorModeInfo: 0
[    30.609]     PhysBasePtr: 0x0
[    30.609]     LinBytesPerScanLine: 0
[    30.609]     BnkNumberOfImagePages: 0
[    30.609]     LinNumberOfImagePages: 0
[    30.609]     LinRedMaskSize: 0
[    30.609]     LinRedFieldPosition: 0
[    30.609]     LinGreenMaskSize: 0
[    30.609]     LinGreenFieldPosition: 0
[    30.609]     LinBlueMaskSize: 0
[    30.609]     LinBlueFieldPosition: 0
[    30.609]     LinRsvdMaskSize: 0
[    30.609]     LinRsvdFieldPosition: 0
[    30.609]     MaxPixelClock: 0
[    30.610] Mode: 167 (0x0)
[    30.610]     ModeAttributes: 0x0
[    30.610]     WinAAttributes: 0x0
[    30.610]     WinBAttributes: 0x0
[    30.610]     WinGranularity: 0
[    30.610]     WinSize: 0
[    30.610]     WinASegment: 0x0
[    30.610]     WinBSegment: 0x0
[    30.610]     WinFuncPtr: 0x0
[    30.610]     BytesPerScanline: 0
[    30.610]     XResolution: 0
[    30.610]     YResolution: 0
[    30.610]     XCharSize: 0
[    30.610]     YCharSize: 0
[    30.610]     NumberOfPlanes: 0
[    30.610]     BitsPerPixel: 0
[    30.610]     NumberOfBanks: 0
[    30.610]     MemoryModel: 0
[    30.610]     BankSize: 0
[    30.610]     NumberOfImages: 0
[    30.610]     RedMaskSize: 0
[    30.610]     RedFieldPosition: 0
[    30.610]     GreenMaskSize: 0
[    30.610]     GreenFieldPosition: 0
[    30.610]     BlueMaskSize: 0
[    30.610]     BlueFieldPosition: 0
[    30.610]     RsvdMaskSize: 0
[    30.610]     RsvdFieldPosition: 0
[    30.611]     DirectColorModeInfo: 0
[    30.611]     PhysBasePtr: 0x0
[    30.611]     LinBytesPerScanLine: 0
[    30.611]     BnkNumberOfImagePages: 0
[    30.611]     LinNumberOfImagePages: 0
[    30.611]     LinRedMaskSize: 0
[    30.611]     LinRedFieldPosition: 0
[    30.611]     LinGreenMaskSize: 0
[    30.611]     LinGreenFieldPosition: 0
[    30.611]     LinBlueMaskSize: 0
[    30.611]     LinBlueFieldPosition: 0
[    30.611]     LinRsvdMaskSize: 0
[    30.611]     LinRsvdFieldPosition: 0
[    30.611]     MaxPixelClock: 0
[    30.612] Mode: 168 (0x0)
[    30.612]     ModeAttributes: 0x0
[    30.612]     WinAAttributes: 0x0
[    30.612]     WinBAttributes: 0x0
[    30.612]     WinGranularity: 0
[    30.612]     WinSize: 0
[    30.612]     WinASegment: 0x0
[    30.612]     WinBSegment: 0x0
[    30.612]     WinFuncPtr: 0x0
[    30.612]     BytesPerScanline: 0
[    30.612]     XResolution: 0
[    30.612]     YResolution: 0
[    30.612]     XCharSize: 0
[    30.612]     YCharSize: 0
[    30.612]     NumberOfPlanes: 0
[    30.612]     BitsPerPixel: 0
[    30.612]     NumberOfBanks: 0
[    30.612]     MemoryModel: 0
[    30.612]     BankSize: 0
[    30.612]     NumberOfImages: 0
[    30.612]     RedMaskSize: 0
[    30.612]     RedFieldPosition: 0
[    30.612]     GreenMaskSize: 0
[    30.612]     GreenFieldPosition: 0
[    30.612]     BlueMaskSize: 0
[    30.612]     BlueFieldPosition: 0
[    30.612]     RsvdMaskSize: 0
[    30.612]     RsvdFieldPosition: 0
[    30.612]     DirectColorModeInfo: 0
[    30.612]     PhysBasePtr: 0x0
[    30.612]     LinBytesPerScanLine: 0
[    30.612]     BnkNumberOfImagePages: 0
[    30.612]     LinNumberOfImagePages: 0
[    30.612]     LinRedMaskSize: 0
[    30.612]     LinRedFieldPosition: 0
[    30.612]     LinGreenMaskSize: 0
[    30.612]     LinGreenFieldPosition: 0
[    30.612]     LinBlueMaskSize: 0
[    30.612]     LinBlueFieldPosition: 0
[    30.612]     LinRsvdMaskSize: 0
[    30.612]     LinRsvdFieldPosition: 0
[    30.612]     MaxPixelClock: 0
[    30.615] Mode: 13c (1920x1440)
[    30.615]     ModeAttributes: 0x9b
[    30.615]     WinAAttributes: 0x7
[    30.615]     WinBAttributes: 0x0
[    30.616]     WinGranularity: 64
[    30.616]     WinSize: 64
[    30.616]     WinASegment: 0xa000
[    30.616]     WinBSegment: 0x0
[    30.616]     WinFuncPtr: 0xc0005a0c
[    30.616]     BytesPerScanline: 1920
[    30.616]     XResolution: 1920
[    30.616]     YResolution: 1440
[    30.616]     XCharSize: 8
[    30.616]     YCharSize: 16
[    30.616]     NumberOfPlanes: 1
[    30.616]     BitsPerPixel: 8
[    30.616]     NumberOfBanks: 1
[    30.616]     MemoryModel: 4
[    30.616]     BankSize: 0
[    30.616]     NumberOfImages: 1
[    30.616]     RedMaskSize: 0
[    30.616]     RedFieldPosition: 0
[    30.616]     GreenMaskSize: 0
[    30.616]     GreenFieldPosition: 0
[    30.616]     BlueMaskSize: 0
[    30.616]     BlueFieldPosition: 0
[    30.616]     RsvdMaskSize: 0
[    30.616]     RsvdFieldPosition: 0
[    30.616]     DirectColorModeInfo: 0
[    30.616]     PhysBasePtr: 0xe0000000
[    30.616]     LinBytesPerScanLine: 1920
[    30.616]     BnkNumberOfImagePages: 1
[    30.616]     LinNumberOfImagePages: 1
[    30.616]     LinRedMaskSize: 0
[    30.616]     LinRedFieldPosition: 0
[    30.616]     LinGreenMaskSize: 0
[    30.616]     LinGreenFieldPosition: 0
[    30.616]     LinBlueMaskSize: 0
[    30.616]     LinBlueFieldPosition: 0
[    30.616]     LinRsvdMaskSize: 0
[    30.616]     LinRsvdFieldPosition: 0
[    30.616]     MaxPixelClock: 230000000
[    30.620] Mode: 14d (1920x1440)
[    30.620]     ModeAttributes: 0x9b
[    30.620]     WinAAttributes: 0x7
[    30.620]     WinBAttributes: 0x0
[    30.620]     WinGranularity: 64
[    30.620]     WinSize: 64
[    30.620]     WinASegment: 0xa000
[    30.620]     WinBSegment: 0x0
[    30.620]     WinFuncPtr: 0xc0005a0c
[    30.620]     BytesPerScanline: 3840
[    30.620]     XResolution: 1920
[    30.620]     YResolution: 1440
[    30.620]     XCharSize: 8
[    30.620]     YCharSize: 16
[    30.620]     NumberOfPlanes: 1
[    30.620]     BitsPerPixel: 16
[    30.620]     NumberOfBanks: 1
[    30.620]     MemoryModel: 6
[    30.620]     BankSize: 0
[    30.620]     NumberOfImages: 0
[    30.620]     RedMaskSize: 5
[    30.620]     RedFieldPosition: 11
[    30.620]     GreenMaskSize: 6
[    30.620]     GreenFieldPosition: 5
[    30.620]     BlueMaskSize: 5
[    30.620]     BlueFieldPosition: 0
[    30.620]     RsvdMaskSize: 0
[    30.620]     RsvdFieldPosition: 0
[    30.620]     DirectColorModeInfo: 0
[    30.620]     PhysBasePtr: 0xe0000000
[    30.620]     LinBytesPerScanLine: 3840
[    30.620]     BnkNumberOfImagePages: 0
[    30.620]     LinNumberOfImagePages: 0
[    30.620]     LinRedMaskSize: 5
[    30.620]     LinRedFieldPosition: 11
[    30.620]     LinGreenMaskSize: 6
[    30.620]     LinGreenFieldPosition: 5
[    30.621]     LinBlueMaskSize: 5
[    30.621]     LinBlueFieldPosition: 0
[    30.621]     LinRsvdMaskSize: 0
[    30.621]     LinRsvdFieldPosition: 0
[    30.621]     MaxPixelClock: 230000000
[    30.623] Mode: 15c (0x0)
[    30.623]     ModeAttributes: 0x0
[    30.623]     WinAAttributes: 0x0
[    30.623]     WinBAttributes: 0x0
[    30.623]     WinGranularity: 0
[    30.623]     WinSize: 0
[    30.623]     WinASegment: 0x0
[    30.623]     WinBSegment: 0x0
[    30.623]     WinFuncPtr: 0x0
[    30.623]     BytesPerScanline: 0
[    30.623]     XResolution: 0
[    30.623]     YResolution: 0
[    30.623]     XCharSize: 0
[    30.623]     YCharSize: 0
[    30.623]     NumberOfPlanes: 0
[    30.623]     BitsPerPixel: 0
[    30.623]     NumberOfBanks: 0
[    30.623]     MemoryModel: 0
[    30.623]     BankSize: 0
[    30.623]     NumberOfImages: 0
[    30.623]     RedMaskSize: 0
[    30.623]     RedFieldPosition: 0
[    30.623]     GreenMaskSize: 0
[    30.623]     GreenFieldPosition: 0
[    30.623]     BlueMaskSize: 0
[    30.623]     BlueFieldPosition: 0
[    30.623]     RsvdMaskSize: 0
[    30.623]     RsvdFieldPosition: 0
[    30.623]     DirectColorModeInfo: 0
[    30.623]     PhysBasePtr: 0x0
[    30.623]     LinBytesPerScanLine: 0
[    30.623]     BnkNumberOfImagePages: 0
[    30.623]     LinNumberOfImagePages: 0
[    30.623]     LinRedMaskSize: 0
[    30.623]     LinRedFieldPosition: 0
[    30.623]     LinGreenMaskSize: 0
[    30.623]     LinGreenFieldPosition: 0
[    30.623]     LinBlueMaskSize: 0
[    30.623]     LinBlueFieldPosition: 0
[    30.623]     LinRsvdMaskSize: 0
[    30.623]     LinRsvdFieldPosition: 0
[    30.623]     MaxPixelClock: 0
[    30.626] Mode: 13a (1600x1200)
[    30.626]     ModeAttributes: 0x9b
[    30.626]     WinAAttributes: 0x7
[    30.626]     WinBAttributes: 0x0
[    30.626]     WinGranularity: 64
[    30.626]     WinSize: 64
[    30.626]     WinASegment: 0xa000
[    30.626]     WinBSegment: 0x0
[    30.626]     WinFuncPtr: 0xc0005a0c
[    30.626]     BytesPerScanline: 1600
[    30.626]     XResolution: 1600
[    30.626]     YResolution: 1200
[    30.626]     XCharSize: 8
[    30.626]     YCharSize: 16
[    30.626]     NumberOfPlanes: 1
[    30.627]     BitsPerPixel: 8
[    30.627]     NumberOfBanks: 1
[    30.627]     MemoryModel: 4
[    30.627]     BankSize: 0
[    30.627]     NumberOfImages: 3
[    30.627]     RedMaskSize: 0
[    30.627]     RedFieldPosition: 0
[    30.627]     GreenMaskSize: 0
[    30.627]     GreenFieldPosition: 0
[    30.627]     BlueMaskSize: 0
[    30.627]     BlueFieldPosition: 0
[    30.627]     RsvdMaskSize: 0
[    30.627]     RsvdFieldPosition: 0
[    30.627]     DirectColorModeInfo: 0
[    30.627]     PhysBasePtr: 0xe0000000
[    30.627]     LinBytesPerScanLine: 1600
[    30.627]     BnkNumberOfImagePages: 3
[    30.627]     LinNumberOfImagePages: 3
[    30.627]     LinRedMaskSize: 0
[    30.627]     LinRedFieldPosition: 0
[    30.627]     LinGreenMaskSize: 0
[    30.627]     LinGreenFieldPosition: 0
[    30.627]     LinBlueMaskSize: 0
[    30.627]     LinBlueFieldPosition: 0
[    30.627]     LinRsvdMaskSize: 0
[    30.627]     LinRsvdFieldPosition: 0
[    30.627]     MaxPixelClock: 230000000
[    30.631] Mode: 14b (1600x1200)
[    30.631]     ModeAttributes: 0x9b
[    30.631]     WinAAttributes: 0x7
[    30.631]     WinBAttributes: 0x0
[    30.631]     WinGranularity: 64
[    30.631]     WinSize: 64
[    30.631]     WinASegment: 0xa000
[    30.631]     WinBSegment: 0x0
[    30.631]     WinFuncPtr: 0xc0005a0c
[    30.631]     BytesPerScanline: 3200
[    30.631]     XResolution: 1600
[    30.631]     YResolution: 1200
[    30.631]     XCharSize: 8
[    30.631]     YCharSize: 16
[    30.631]     NumberOfPlanes: 1
[    30.631]     BitsPerPixel: 16
[    30.631]     NumberOfBanks: 1
[    30.631]     MemoryModel: 6
[    30.631]     BankSize: 0
[    30.631]     NumberOfImages: 1
[    30.631]     RedMaskSize: 5
[    30.631]     RedFieldPosition: 11
[    30.631]     GreenMaskSize: 6
[    30.631]     GreenFieldPosition: 5
[    30.631]     BlueMaskSize: 5
[    30.631]     BlueFieldPosition: 0
[    30.631]     RsvdMaskSize: 0
[    30.631]     RsvdFieldPosition: 0
[    30.631]     DirectColorModeInfo: 0
[    30.631]     PhysBasePtr: 0xe0000000
[    30.631]     LinBytesPerScanLine: 3200
[    30.631]     BnkNumberOfImagePages: 1
[    30.631]     LinNumberOfImagePages: 1
[    30.631]     LinRedMaskSize: 5
[    30.631]     LinRedFieldPosition: 11
[    30.631]     LinGreenMaskSize: 6
[    30.631]     LinGreenFieldPosition: 5
[    30.631]     LinBlueMaskSize: 5
[    30.631]     LinBlueFieldPosition: 0
[    30.631]     LinRsvdMaskSize: 0
[    30.631]     LinRsvdFieldPosition: 0
[    30.631]     MaxPixelClock: 230000000
[    30.636] *Mode: 15a (1600x1200)
[    30.636]     ModeAttributes: 0x9b
[    30.636]     WinAAttributes: 0x7
[    30.636]     WinBAttributes: 0x0
[    30.636]     WinGranularity: 64
[    30.636]     WinSize: 64
[    30.636]     WinASegment: 0xa000
[    30.636]     WinBSegment: 0x0
[    30.636]     WinFuncPtr: 0xc0005a0c
[    30.636]     BytesPerScanline: 6400
[    30.636]     XResolution: 1600
[    30.636]     YResolution: 1200
[    30.636]     XCharSize: 8
[    30.636]     YCharSize: 16
[    30.636]     NumberOfPlanes: 1
[    30.636]     BitsPerPixel: 32
[    30.636]     NumberOfBanks: 1
[    30.636]     MemoryModel: 6
[    30.636]     BankSize: 0
[    30.636]     NumberOfImages: 0
[    30.636]     RedMaskSize: 8
[    30.636]     RedFieldPosition: 16
[    30.636]     GreenMaskSize: 8
[    30.636]     GreenFieldPosition: 8
[    30.636]     BlueMaskSize: 8
[    30.636]     BlueFieldPosition: 0
[    30.636]     RsvdMaskSize: 8
[    30.636]     RsvdFieldPosition: 24
[    30.636]     DirectColorModeInfo: 0
[    30.636]     PhysBasePtr: 0xe0000000
[    30.636]     LinBytesPerScanLine: 6400
[    30.636]     BnkNumberOfImagePages: 0
[    30.636]     LinNumberOfImagePages: 0
[    30.636]     LinRedMaskSize: 8
[    30.636]     LinRedFieldPosition: 16
[    30.636]     LinGreenMaskSize: 8
[    30.636]     LinGreenFieldPosition: 8
[    30.637]     LinBlueMaskSize: 8
[    30.637]     LinBlueFieldPosition: 0
[    30.637]     LinRsvdMaskSize: 8
[    30.637]     LinRsvdFieldPosition: 24
[    30.637]     MaxPixelClock: 230000000
[    30.640] Mode: 107 (1280x1024)
[    30.640]     ModeAttributes: 0x9b
[    30.640]     WinAAttributes: 0x7
[    30.640]     WinBAttributes: 0x0
[    30.640]     WinGranularity: 64
[    30.640]     WinSize: 64
[    30.640]     WinASegment: 0xa000
[    30.640]     WinBSegment: 0x0
[    30.640]     WinFuncPtr: 0xc0005a0c
[    30.640]     BytesPerScanline: 1280
[    30.640]     XResolution: 1280
[    30.640]     YResolution: 1024
[    30.640]     XCharSize: 8
[    30.640]     YCharSize: 16
[    30.640]     NumberOfPlanes: 1
[    30.640]     BitsPerPixel: 8
[    30.640]     NumberOfBanks: 1
[    30.640]     MemoryModel: 4
[    30.640]     BankSize: 0
[    30.640]     NumberOfImages: 5
[    30.640]     RedMaskSize: 0
[    30.640]     RedFieldPosition: 0
[    30.640]     GreenMaskSize: 0
[    30.640]     GreenFieldPosition: 0
[    30.640]     BlueMaskSize: 0
[    30.640]     BlueFieldPosition: 0
[    30.640]     RsvdMaskSize: 0
[    30.640]     RsvdFieldPosition: 0
[    30.640]     DirectColorModeInfo: 0
[    30.640]     PhysBasePtr: 0xe0000000
[    30.640]     LinBytesPerScanLine: 1280
[    30.640]     BnkNumberOfImagePages: 5
[    30.640]     LinNumberOfImagePages: 5
[    30.640]     LinRedMaskSize: 0
[    30.640]     LinRedFieldPosition: 0
[    30.640]     LinGreenMaskSize: 0
[    30.640]     LinGreenFieldPosition: 0
[    30.640]     LinBlueMaskSize: 0
[    30.640]     LinBlueFieldPosition: 0
[    30.640]     LinRsvdMaskSize: 0
[    30.640]     LinRsvdFieldPosition: 0
[    30.640]     MaxPixelClock: 230000000
[    30.644] Mode: 11a (1280x1024)
[    30.644]     ModeAttributes: 0x9b
[    30.644]     WinAAttributes: 0x7
[    30.644]     WinBAttributes: 0x0
[    30.644]     WinGranularity: 64
[    30.644]     WinSize: 64
[    30.644]     WinASegment: 0xa000
[    30.644]     WinBSegment: 0x0
[    30.644]     WinFuncPtr: 0xc0005a0c
[    30.644]     BytesPerScanline: 2560
[    30.644]     XResolution: 1280
[    30.644]     YResolution: 1024
[    30.644]     XCharSize: 8
[    30.644]     YCharSize: 16
[    30.644]     NumberOfPlanes: 1
[    30.644]     BitsPerPixel: 16
[    30.644]     NumberOfBanks: 1
[    30.644]     MemoryModel: 6
[    30.644]     BankSize: 0
[    30.644]     NumberOfImages: 2
[    30.644]     RedMaskSize: 5
[    30.644]     RedFieldPosition: 11
[    30.644]     GreenMaskSize: 6
[    30.644]     GreenFieldPosition: 5
[    30.644]     BlueMaskSize: 5
[    30.644]     BlueFieldPosition: 0
[    30.644]     RsvdMaskSize: 0
[    30.644]     RsvdFieldPosition: 0
[    30.644]     DirectColorModeInfo: 0
[    30.644]     PhysBasePtr: 0xe0000000
[    30.644]     LinBytesPerScanLine: 2560
[    30.644]     BnkNumberOfImagePages: 2
[    30.644]     LinNumberOfImagePages: 2
[    30.644]     LinRedMaskSize: 5
[    30.644]     LinRedFieldPosition: 11
[    30.644]     LinGreenMaskSize: 6
[    30.644]     LinGreenFieldPosition: 5
[    30.644]     LinBlueMaskSize: 5
[    30.644]     LinBlueFieldPosition: 0
[    30.644]     LinRsvdMaskSize: 0
[    30.644]     LinRsvdFieldPosition: 0
[    30.644]     MaxPixelClock: 230000000
[    30.649] *Mode: 11b (1280x1024)
[    30.649]     ModeAttributes: 0x9b
[    30.649]     WinAAttributes: 0x7
[    30.649]     WinBAttributes: 0x0
[    30.649]     WinGranularity: 64
[    30.649]     WinSize: 64
[    30.649]     WinASegment: 0xa000
[    30.649]     WinBSegment: 0x0
[    30.649]     WinFuncPtr: 0xc0005a0c
[    30.649]     BytesPerScanline: 5120
[    30.649]     XResolution: 1280
[    30.649]     YResolution: 1024
[    30.649]     XCharSize: 8
[    30.649]     YCharSize: 16
[    30.649]     NumberOfPlanes: 1
[    30.649]     BitsPerPixel: 32
[    30.649]     NumberOfBanks: 1
[    30.649]     MemoryModel: 6
[    30.649]     BankSize: 0
[    30.649]     NumberOfImages: 0
[    30.649]     RedMaskSize: 8
[    30.649]     RedFieldPosition: 16
[    30.649]     GreenMaskSize: 8
[    30.649]     GreenFieldPosition: 8
[    30.649]     BlueMaskSize: 8
[    30.649]     BlueFieldPosition: 0
[    30.649]     RsvdMaskSize: 8
[    30.649]     RsvdFieldPosition: 24
[    30.649]     DirectColorModeInfo: 0
[    30.649]     PhysBasePtr: 0xe0000000
[    30.649]     LinBytesPerScanLine: 5120
[    30.649]     BnkNumberOfImagePages: 0
[    30.649]     LinNumberOfImagePages: 0
[    30.649]     LinRedMaskSize: 8
[    30.649]     LinRedFieldPosition: 16
[    30.649]     LinGreenMaskSize: 8
[    30.649]     LinGreenFieldPosition: 8
[    30.649]     LinBlueMaskSize: 8
[    30.649]     LinBlueFieldPosition: 0
[    30.649]     LinRsvdMaskSize: 8
[    30.649]     LinRsvdFieldPosition: 24
[    30.650]     MaxPixelClock: 230000000
[    30.652] Mode: 105 (1024x768)
[    30.652]     ModeAttributes: 0x9b
[    30.652]     WinAAttributes: 0x7
[    30.652]     WinBAttributes: 0x0
[    30.652]     WinGranularity: 64
[    30.652]     WinSize: 64
[    30.652]     WinASegment: 0xa000
[    30.652]     WinBSegment: 0x0
[    30.653]     WinFuncPtr: 0xc0005a0c
[    30.653]     BytesPerScanline: 1024
[    30.653]     XResolution: 1024
[    30.653]     YResolution: 768
[    30.653]     XCharSize: 8
[    30.653]     YCharSize: 16
[    30.653]     NumberOfPlanes: 1
[    30.653]     BitsPerPixel: 8
[    30.653]     NumberOfBanks: 1
[    30.653]     MemoryModel: 4
[    30.653]     BankSize: 0
[    30.653]     NumberOfImages: 9
[    30.653]     RedMaskSize: 0
[    30.653]     RedFieldPosition: 0
[    30.653]     GreenMaskSize: 0
[    30.653]     GreenFieldPosition: 0
[    30.653]     BlueMaskSize: 0
[    30.653]     BlueFieldPosition: 0
[    30.653]     RsvdMaskSize: 0
[    30.653]     RsvdFieldPosition: 0
[    30.653]     DirectColorModeInfo: 0
[    30.653]     PhysBasePtr: 0xe0000000
[    30.653]     LinBytesPerScanLine: 1024
[    30.653]     BnkNumberOfImagePages: 9
[    30.653]     LinNumberOfImagePages: 9
[    30.653]     LinRedMaskSize: 0
[    30.653]     LinRedFieldPosition: 0
[    30.653]     LinGreenMaskSize: 0
[    30.653]     LinGreenFieldPosition: 0
[    30.653]     LinBlueMaskSize: 0
[    30.653]     LinBlueFieldPosition: 0
[    30.653]     LinRsvdMaskSize: 0
[    30.653]     LinRsvdFieldPosition: 0
[    30.653]     MaxPixelClock: 230000000
[    30.656] Mode: 117 (1024x768)
[    30.657]     ModeAttributes: 0x9b
[    30.657]     WinAAttributes: 0x7
[    30.657]     WinBAttributes: 0x0
[    30.657]     WinGranularity: 64
[    30.657]     WinSize: 64
[    30.657]     WinASegment: 0xa000
[    30.657]     WinBSegment: 0x0
[    30.657]     WinFuncPtr: 0xc0005a0c
[    30.657]     BytesPerScanline: 2048
[    30.657]     XResolution: 1024
[    30.657]     YResolution: 768
[    30.657]     XCharSize: 8
[    30.657]     YCharSize: 16
[    30.657]     NumberOfPlanes: 1
[    30.657]     BitsPerPixel: 16
[    30.657]     NumberOfBanks: 1
[    30.657]     MemoryModel: 6
[    30.657]     BankSize: 0
[    30.657]     NumberOfImages: 4
[    30.657]     RedMaskSize: 5
[    30.657]     RedFieldPosition: 11
[    30.657]     GreenMaskSize: 6
[    30.657]     GreenFieldPosition: 5
[    30.657]     BlueMaskSize: 5
[    30.657]     BlueFieldPosition: 0
[    30.657]     RsvdMaskSize: 0
[    30.657]     RsvdFieldPosition: 0
[    30.657]     DirectColorModeInfo: 0
[    30.657]     PhysBasePtr: 0xe0000000
[    30.657]     LinBytesPerScanLine: 2048
[    30.657]     BnkNumberOfImagePages: 4
[    30.657]     LinNumberOfImagePages: 4
[    30.657]     LinRedMaskSize: 5
[    30.657]     LinRedFieldPosition: 11
[    30.657]     LinGreenMaskSize: 6
[    30.657]     LinGreenFieldPosition: 5
[    30.657]     LinBlueMaskSize: 5
[    30.657]     LinBlueFieldPosition: 0
[    30.657]     LinRsvdMaskSize: 0
[    30.657]     LinRsvdFieldPosition: 0
[    30.657]     MaxPixelClock: 230000000
[    30.662] *Mode: 118 (1024x768)
[    30.662]     ModeAttributes: 0x9b
[    30.662]     WinAAttributes: 0x7
[    30.662]     WinBAttributes: 0x0
[    30.662]     WinGranularity: 64
[    30.662]     WinSize: 64
[    30.662]     WinASegment: 0xa000
[    30.662]     WinBSegment: 0x0
[    30.662]     WinFuncPtr: 0xc0005a0c
[    30.662]     BytesPerScanline: 4096
[    30.662]     XResolution: 1024
[    30.662]     YResolution: 768
[    30.662]     XCharSize: 8
[    30.662]     YCharSize: 16
[    30.662]     NumberOfPlanes: 1
[    30.662]     BitsPerPixel: 32
[    30.662]     NumberOfBanks: 1
[    30.662]     MemoryModel: 6
[    30.662]     BankSize: 0
[    30.662]     NumberOfImages: 1
[    30.662]     RedMaskSize: 8
[    30.662]     RedFieldPosition: 16
[    30.662]     GreenMaskSize: 8
[    30.662]     GreenFieldPosition: 8
[    30.662]     BlueMaskSize: 8
[    30.662]     BlueFieldPosition: 0
[    30.662]     RsvdMaskSize: 8
[    30.662]     RsvdFieldPosition: 24
[    30.662]     DirectColorModeInfo: 0
[    30.662]     PhysBasePtr: 0xe0000000
[    30.662]     LinBytesPerScanLine: 4096
[    30.662]     BnkNumberOfImagePages: 1
[    30.662]     LinNumberOfImagePages: 1
[    30.662]     LinRedMaskSize: 8
[    30.662]     LinRedFieldPosition: 16
[    30.662]     LinGreenMaskSize: 8
[    30.662]     LinGreenFieldPosition: 8
[    30.662]     LinBlueMaskSize: 8
[    30.662]     LinBlueFieldPosition: 0
[    30.662]     LinRsvdMaskSize: 8
[    30.662]     LinRsvdFieldPosition: 24
[    30.662]     MaxPixelClock: 230000000
[    30.666] *Mode: 112 (640x480)
[    30.666]     ModeAttributes: 0x9b
[    30.666]     WinAAttributes: 0x7
[    30.666]     WinBAttributes: 0x0
[    30.666]     WinGranularity: 64
[    30.666]     WinSize: 64
[    30.667]     WinASegment: 0xa000
[    30.667]     WinBSegment: 0x0
[    30.667]     WinFuncPtr: 0xc0005a0c
[    30.667]     BytesPerScanline: 2560
[    30.667]     XResolution: 640
[    30.667]     YResolution: 480
[    30.667]     XCharSize: 8
[    30.667]     YCharSize: 16
[    30.667]     NumberOfPlanes: 1
[    30.667]     BitsPerPixel: 32
[    30.667]     NumberOfBanks: 1
[    30.667]     MemoryModel: 6
[    30.667]     BankSize: 0
[    30.667]     NumberOfImages: 5
[    30.667]     RedMaskSize: 8
[    30.667]     RedFieldPosition: 16
[    30.667]     GreenMaskSize: 8
[    30.667]     GreenFieldPosition: 8
[    30.667]     BlueMaskSize: 8
[    30.667]     BlueFieldPosition: 0
[    30.667]     RsvdMaskSize: 8
[    30.667]     RsvdFieldPosition: 24
[    30.667]     DirectColorModeInfo: 0
[    30.667]     PhysBasePtr: 0xe0000000
[    30.667]     LinBytesPerScanLine: 2560
[    30.667]     BnkNumberOfImagePages: 5
[    30.667]     LinNumberOfImagePages: 5
[    30.667]     LinRedMaskSize: 8
[    30.667]     LinRedFieldPosition: 16
[    30.667]     LinGreenMaskSize: 8
[    30.667]     LinGreenFieldPosition: 8
[    30.667]     LinBlueMaskSize: 8
[    30.667]     LinBlueFieldPosition: 0
[    30.667]     LinRsvdMaskSize: 8
[    30.667]     LinRsvdFieldPosition: 24
[    30.667]     MaxPixelClock: 230000000
[    30.671] Mode: 114 (800x600)
[    30.671]     ModeAttributes: 0x9b
[    30.671]     WinAAttributes: 0x7
[    30.671]     WinBAttributes: 0x0
[    30.671]     WinGranularity: 64
[    30.671]     WinSize: 64
[    30.671]     WinASegment: 0xa000
[    30.671]     WinBSegment: 0x0
[    30.671]     WinFuncPtr: 0xc0005a0c
[    30.671]     BytesPerScanline: 1600
[    30.671]     XResolution: 800
[    30.671]     YResolution: 600
[    30.671]     XCharSize: 8
[    30.671]     YCharSize: 16
[    30.671]     NumberOfPlanes: 1
[    30.671]     BitsPerPixel: 16
[    30.671]     NumberOfBanks: 1
[    30.671]     MemoryModel: 6
[    30.671]     BankSize: 0
[    30.671]     NumberOfImages: 7
[    30.671]     RedMaskSize: 5
[    30.671]     RedFieldPosition: 11
[    30.671]     GreenMaskSize: 6
[    30.671]     GreenFieldPosition: 5
[    30.671]     BlueMaskSize: 5
[    30.671]     BlueFieldPosition: 0
[    30.671]     RsvdMaskSize: 0
[    30.671]     RsvdFieldPosition: 0
[    30.671]     DirectColorModeInfo: 0
[    30.671]     PhysBasePtr: 0xe0000000
[    30.671]     LinBytesPerScanLine: 1600
[    30.671]     BnkNumberOfImagePages: 7
[    30.671]     LinNumberOfImagePages: 7
[    30.671]     LinRedMaskSize: 5
[    30.671]     LinRedFieldPosition: 11
[    30.671]     LinGreenMaskSize: 6
[    30.671]     LinGreenFieldPosition: 5
[    30.671]     LinBlueMaskSize: 5
[    30.671]     LinBlueFieldPosition: 0
[    30.671]     LinRsvdMaskSize: 0
[    30.671]     LinRsvdFieldPosition: 0
[    30.671]     MaxPixelClock: 230000000
[    30.675] *Mode: 115 (800x600)
[    30.675]     ModeAttributes: 0x9b
[    30.675]     WinAAttributes: 0x7
[    30.675]     WinBAttributes: 0x0
[    30.675]     WinGranularity: 64
[    30.675]     WinSize: 64
[    30.675]     WinASegment: 0xa000
[    30.675]     WinBSegment: 0x0
[    30.675]     WinFuncPtr: 0xc0005a0c
[    30.675]     BytesPerScanline: 3200
[    30.675]     XResolution: 800
[    30.675]     YResolution: 600
[    30.675]     XCharSize: 8
[    30.675]     YCharSize: 16
[    30.676]     NumberOfPlanes: 1
[    30.676]     BitsPerPixel: 32
[    30.676]     NumberOfBanks: 1
[    30.676]     MemoryModel: 6
[    30.676]     BankSize: 0
[    30.676]     NumberOfImages: 3
[    30.676]     RedMaskSize: 8
[    30.676]     RedFieldPosition: 16
[    30.676]     GreenMaskSize: 8
[    30.676]     GreenFieldPosition: 8
[    30.676]     BlueMaskSize: 8
[    30.676]     BlueFieldPosition: 0
[    30.676]     RsvdMaskSize: 8
[    30.676]     RsvdFieldPosition: 24
[    30.676]     DirectColorModeInfo: 0
[    30.676]     PhysBasePtr: 0xe0000000
[    30.676]     LinBytesPerScanLine: 3200
[    30.676]     BnkNumberOfImagePages: 3
[    30.676]     LinNumberOfImagePages: 3
[    30.676]     LinRedMaskSize: 8
[    30.676]     LinRedFieldPosition: 16
[    30.676]     LinGreenMaskSize: 8
[    30.676]     LinGreenFieldPosition: 8
[    30.676]     LinBlueMaskSize: 8
[    30.676]     LinBlueFieldPosition: 0
[    30.676]     LinRsvdMaskSize: 8
[    30.676]     LinRsvdFieldPosition: 24
[    30.676]     MaxPixelClock: 230000000
[    30.679] Mode: 101 (640x480)
[    30.679]     ModeAttributes: 0x9b
[    30.679]     WinAAttributes: 0x7
[    30.679]     WinBAttributes: 0x0
[    30.679]     WinGranularity: 64
[    30.679]     WinSize: 64
[    30.679]     WinASegment: 0xa000
[    30.679]     WinBSegment: 0x0
[    30.679]     WinFuncPtr: 0xc0005a0c
[    30.679]     BytesPerScanline: 640
[    30.679]     XResolution: 640
[    30.679]     YResolution: 480
[    30.679]     XCharSize: 8
[    30.679]     YCharSize: 16
[    30.679]     NumberOfPlanes: 1
[    30.679]     BitsPerPixel: 8
[    30.679]     NumberOfBanks: 1
[    30.679]     MemoryModel: 4
[    30.679]     BankSize: 0
[    30.679]     NumberOfImages: 24
[    30.679]     RedMaskSize: 0
[    30.679]     RedFieldPosition: 0
[    30.679]     GreenMaskSize: 0
[    30.679]     GreenFieldPosition: 0
[    30.679]     BlueMaskSize: 0
[    30.679]     BlueFieldPosition: 0
[    30.679]     RsvdMaskSize: 0
[    30.679]     RsvdFieldPosition: 0
[    30.679]     DirectColorModeInfo: 0
[    30.679]     PhysBasePtr: 0xe0000000
[    30.679]     LinBytesPerScanLine: 640
[    30.679]     BnkNumberOfImagePages: 24
[    30.679]     LinNumberOfImagePages: 24
[    30.679]     LinRedMaskSize: 0
[    30.679]     LinRedFieldPosition: 0
[    30.679]     LinGreenMaskSize: 0
[    30.679]     LinGreenFieldPosition: 0
[    30.679]     LinBlueMaskSize: 0
[    30.679]     LinBlueFieldPosition: 0
[    30.679]     LinRsvdMaskSize: 0
[    30.679]     LinRsvdFieldPosition: 0
[    30.679]     MaxPixelClock: 230000000
[    30.682] Mode: 103 (800x600)
[    30.682]     ModeAttributes: 0x9b
[    30.682]     WinAAttributes: 0x7
[    30.682]     WinBAttributes: 0x0
[    30.682]     WinGranularity: 64
[    30.682]     WinSize: 64
[    30.682]     WinASegment: 0xa000
[    30.682]     WinBSegment: 0x0
[    30.682]     WinFuncPtr: 0xc0005a0c
[    30.682]     BytesPerScanline: 800
[    30.682]     XResolution: 800
[    30.682]     YResolution: 600
[    30.682]     XCharSize: 8
[    30.682]     YCharSize: 16
[    30.682]     NumberOfPlanes: 1
[    30.682]     BitsPerPixel: 8
[    30.682]     NumberOfBanks: 1
[    30.682]     MemoryModel: 4
[    30.682]     BankSize: 0
[    30.682]     NumberOfImages: 16
[    30.682]     RedMaskSize: 0
[    30.682]     RedFieldPosition: 0
[    30.682]     GreenMaskSize: 0
[    30.682]     GreenFieldPosition: 0
[    30.682]     BlueMaskSize: 0
[    30.682]     BlueFieldPosition: 0
[    30.682]     RsvdMaskSize: 0
[    30.682]     RsvdFieldPosition: 0
[    30.682]     DirectColorModeInfo: 0
[    30.682]     PhysBasePtr: 0xe0000000
[    30.682]     LinBytesPerScanLine: 800
[    30.683]     BnkNumberOfImagePages: 16
[    30.683]     LinNumberOfImagePages: 16
[    30.683]     LinRedMaskSize: 0
[    30.683]     LinRedFieldPosition: 0
[    30.683]     LinGreenMaskSize: 0
[    30.683]     LinGreenFieldPosition: 0
[    30.683]     LinBlueMaskSize: 0
[    30.683]     LinBlueFieldPosition: 0
[    30.683]     LinRsvdMaskSize: 0
[    30.683]     LinRsvdFieldPosition: 0
[    30.683]     MaxPixelClock: 230000000
[    30.686] Mode: 111 (640x480)
[    30.686]     ModeAttributes: 0x9b
[    30.686]     WinAAttributes: 0x7
[    30.686]     WinBAttributes: 0x0
[    30.686]     WinGranularity: 64
[    30.686]     WinSize: 64
[    30.686]     WinASegment: 0xa000
[    30.686]     WinBSegment: 0x0
[    30.686]     WinFuncPtr: 0xc0005a0c
[    30.686]     BytesPerScanline: 1280
[    30.686]     XResolution: 640
[    30.686]     YResolution: 480
[    30.686]     XCharSize: 8
[    30.686]     YCharSize: 16
[    30.686]     NumberOfPlanes: 1
[    30.686]     BitsPerPixel: 16
[    30.686]     NumberOfBanks: 1
[    30.686]     MemoryModel: 6
[    30.686]     BankSize: 0
[    30.686]     NumberOfImages: 12
[    30.686]     RedMaskSize: 5
[    30.686]     RedFieldPosition: 11
[    30.686]     GreenMaskSize: 6
[    30.686]     GreenFieldPosition: 5
[    30.686]     BlueMaskSize: 5
[    30.686]     BlueFieldPosition: 0
[    30.686]     RsvdMaskSize: 0
[    30.686]     RsvdFieldPosition: 0
[    30.686]     DirectColorModeInfo: 0
[    30.686]     PhysBasePtr: 0xe0000000
[    30.686]     LinBytesPerScanLine: 1280
[    30.686]     BnkNumberOfImagePages: 12
[    30.687]     LinNumberOfImagePages: 12
[    30.687]     LinRedMaskSize: 5
[    30.687]     LinRedFieldPosition: 11
[    30.687]     LinGreenMaskSize: 6
[    30.687]     LinGreenFieldPosition: 5
[    30.687]     LinBlueMaskSize: 5
[    30.687]     LinBlueFieldPosition: 0
[    30.687]     LinRsvdMaskSize: 0
[    30.687]     LinRsvdFieldPosition: 0
[    30.687]     MaxPixelClock: 230000000
[    30.687] 
[    30.687] (II) VESA(0): Total Memory: 125 64KB banks (8000kB)
[    30.687] (II) VESA(0): <default monitor>: Using hsync range of 24.00-83.00 kHz
[    30.687] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-76.00 Hz
[    30.687] (II) VESA(0): <default monitor>: Using maximum pixel clock of 175.00 MHz
[    30.687] (II) VESA(0): Not using mode "1600x900" (no mode of this name)
[    30.687] (II) VESA(0): Not using mode "1280x720" (no mode of this name)
[    30.687] (II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
[    30.860] (--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
[    30.860] (**) VESA(0):  Built-in mode "1280x1024"
[    30.860] (**) VESA(0):  Built-in mode "1024x768"
[    30.860] (**) VESA(0):  Built-in mode "800x600"
[    30.860] (**) VESA(0):  Built-in mode "640x480"
[    30.860] (**) VESA(0): Display dimensions: (440, 250) mm
[    30.860] (**) VESA(0): DPI set to (73, 104)
[    30.860] (**) VESA(0): Using "Shadow Framebuffer"
[    30.860] (II) Loading sub module "shadow"
[    30.860] (II) LoadModule: "shadow"
[    30.860] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    30.861] (II) Module shadow: vendor="X.Org Foundation"
[    30.861]     compiled for 1.14.5, module version = 1.1.0
[    30.861]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.861] (II) Loading sub module "fb"
[    30.861] (II) LoadModule: "fb"
[    30.861] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.862] (II) Module fb: vendor="X.Org Foundation"
[    30.862]     compiled for 1.14.5, module version = 1.0.0
[    30.862]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.862] (II) UnloadModule: "modesetting"
[    30.862] (II) Unloading modesetting
[    30.862] (II) UnloadModule: "fbdev"
[    30.862] (II) Unloading fbdev
[    30.862] (II) UnloadSubModule: "fbdevhw"
[    30.862] (II) Unloading fbdevhw
[    30.863] (==) Depth 24 pixmap format is 32 bpp
[    30.863] (II) Loading sub module "int10"
[    30.863] (II) LoadModule: "int10"
[    30.863] (II) Loading /usr/lib/xorg/modules/libint10.so
[    30.863] (II) Module int10: vendor="X.Org Foundation"
[    30.863]     compiled for 1.14.5, module version = 1.0.0
[    30.863]     ABI class: X.Org Video Driver, version 14.1
[    30.863] (II) VESA(0): initializing int10
[    30.871] (II) VESA(0): Bad V_BIOS checksum
[    30.871] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    30.872] (II) VESA(0): VESA BIOS detected
[    30.872] (II) VESA(0): VESA VBE Version 3.0
[    30.872] (II) VESA(0): VESA VBE Total Mem: 8000 kB
[    30.872] (II) VESA(0): VESA VBE OEM: Intel(r)845G/845GL/845GE/845GV Graphics Chip Accelerated VGA BIOS
[    30.872] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    30.872] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    30.873] (II) VESA(0): VESA VBE OEM Product: Intel(r)845G/845GL/845GE/845GV Graphics Controller
[    30.873] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    30.873] (II) VESA(0): virtual address = 0xb6163000,
    physical address = 0xe0000000, size = 8192000
[    30.894] (II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)
[    30.951] (==) VESA(0): Default visual is TrueColor
[    30.951] (==) VESA(0): Backing store disabled
[    30.951] (==) VESA(0): DPMS enabled
[    30.952] (==) RandR enabled
[    30.964] (II) SELinux: Disabled on system
[    30.966] (II) AIGLX: Screen 0 is not DRI2 capable
[    30.966] (II) AIGLX: Screen 0 is not DRI capable
[    31.317] (II) AIGLX: Loaded and initialized swrast
[    31.317] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    31.347] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.354] (II) config/udev: Adding input device Chicony Multimedia Keyboard (/dev/input/event1)
[    31.354] (**) Chicony Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[    31.354] (II) LoadModule: "evdev"
[    31.354] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.372] (II) Module evdev: vendor="X.Org Foundation"
[    31.372]     compiled for 1.14.1, module version = 2.7.3
[    31.373]     Module class: X.Org XInput Driver
[    31.373]     ABI class: X.Org XInput driver, version 19.1
[    31.373] (II) Using input driver 'evdev' for 'Chicony Multimedia Keyboard'
[    31.373] (**) Chicony Multimedia Keyboard: always reports core events
[    31.373] (**) evdev: Chicony Multimedia Keyboard: Device: "/dev/input/event1"
[    31.373] (--) evdev: Chicony Multimedia Keyboard: Vendor 0x4f2 Product 0x736
[    31.373] (--) evdev: Chicony Multimedia Keyboard: Found keys
[    31.373] (II) evdev: Chicony Multimedia Keyboard: Configuring as keyboard
[    31.373] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input1/event1"
[    31.373] (II) XINPUT: Adding extended input device "Chicony Multimedia Keyboard" (type: KEYBOARD, id 6)
[    31.373] (**) Option "xkb_rules" "evdev"
[    31.373] (**) Option "xkb_model" "pc105"
[    31.373] (**) Option "xkb_layout" "us"
[    31.375] (II) config/udev: Adding input device Chicony Multimedia Keyboard (/dev/input/event2)
[    31.375] (**) Chicony Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[    31.375] (II) Using input driver 'evdev' for 'Chicony Multimedia Keyboard'
[    31.375] (**) Chicony Multimedia Keyboard: always reports core events
[    31.375] (**) evdev: Chicony Multimedia Keyboard: Device: "/dev/input/event2"
[    31.375] (--) evdev: Chicony Multimedia Keyboard: Vendor 0x4f2 Product 0x736
[    31.375] (--) evdev: Chicony Multimedia Keyboard: Found keys
[    31.375] (II) evdev: Chicony Multimedia Keyboard: Configuring as keyboard
[    31.375] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input2/event2"
[    31.375] (II) XINPUT: Adding extended input device "Chicony Multimedia Keyboard" (type: KEYBOARD, id 7)
[    31.375] (**) Option "xkb_rules" "evdev"
[    31.375] (**) Option "xkb_model" "pc105"
[    31.375] (**) Option "xkb_layout" "us"
[    31.377] (II) config/udev: Adding input device GenPS/2 Genius Mouse (/dev/input/event0)
[    31.377] (**) GenPS/2 Genius Mouse: Applying InputClass "evdev pointer catchall"
[    31.377] (II) Using input driver 'evdev' for 'GenPS/2 Genius Mouse'
[    31.377] (**) GenPS/2 Genius Mouse: always reports core events
[    31.377] (**) evdev: GenPS/2 Genius Mouse: Device: "/dev/input/event0"
[    31.377] (--) evdev: GenPS/2 Genius Mouse: Vendor 0x2 Product 0x4
[    31.377] (--) evdev: GenPS/2 Genius Mouse: Found 9 mouse buttons
[    31.377] (--) evdev: GenPS/2 Genius Mouse: Found scroll wheel(s)
[    31.377] (--) evdev: GenPS/2 Genius Mouse: Found relative axes
[    31.377] (--) evdev: GenPS/2 Genius Mouse: Found x and y relative axes
[    31.377] (II) evdev: GenPS/2 Genius Mouse: Configuring as mouse
[    31.377] (II) evdev: GenPS/2 Genius Mouse: Adding scrollwheel support
[    31.377] (**) evdev: GenPS/2 Genius Mouse: YAxisMapping: buttons 4 and 5
[    31.377] (**) evdev: GenPS/2 Genius Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.378] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input0/event0"
[    31.378] (II) XINPUT: Adding extended input device "GenPS/2 Genius Mouse" (type: MOUSE, id 8)
[    31.378] (II) evdev: GenPS/2 Genius Mouse: initialized for relative axes.
[    31.378] (**) GenPS/2 Genius Mouse: (accel) keeping acceleration scheme 1
[    31.378] (**) GenPS/2 Genius Mouse: (accel) acceleration profile 0
[    31.378] (**) GenPS/2 Genius Mouse: (accel) acceleration factor: 2.000
[    31.378] (**) GenPS/2 Genius Mouse: (accel) acceleration threshold: 4
[    31.379] (II) config/udev: Adding input device GenPS/2 Genius Mouse (/dev/input/mouse0)
[    31.379] (II) No input driver specified, ignoring this device.
[    31.379] (II) This device may have been added with another device file.

```

---

### Post by Yellow Pasque on 2014-03-11
> (EE) open /dev/dri/card0: No such file or directory
So the kernel modesetting is failing and X is falling back on VESA driver (which won't give you widescreen resolutions). I would suggest booting with nomodeset, but IIRC, intel ripped out the old userspace modesetting (UMS) code.

---

### Post by snazzierella on 2014-03-11
Okay, tried putting nomodeset, and nothing is different. Same error.

---

### Post by mörgæs on 2014-03-11
13.10 is known to have problems with your graphics card. I don't know about resolution but for other problems the solution is adding an [xorg.conf]("https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006117.html") file.

---

### Post by snazzierella on 2014-03-11
So what am I supposed to do? This is what my xorg.conf file looks like now (and I still get the same errors):
```
Section "Screen"    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1600x900" "1280x720" # Add other resolutions you might need here in same pattern
    EndSubSection
EndSection


Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
    Option "AccelMethod" "uxa"
EndSection
```

---


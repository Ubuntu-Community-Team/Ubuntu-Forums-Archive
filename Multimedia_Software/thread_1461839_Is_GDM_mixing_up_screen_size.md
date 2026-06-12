---
title: "Is GDM mixing up screen size?"
date: 2010-04-24
forum: Multimedia Software
---

### Post by ccprog on 2010-04-24
Hardware: Graphics Intel G41 chipset, Monitor Samsung SyncMaster P2270HD
System: karmic, kernel 2.6.31-20, Graphics driver intel 2.9.0

When connecting my new monitor to the computer via VGA, screen resolutions and physical monitor size get read from EDID data just fine. When I use a HDMI connection, also EDID is still read, and, fortunately, screen resolutions still fit. There is only one thing missing: the physical screen size. Somehow a default value gets introduced, and xrandr shows the following:
```
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080      60.0*+
   1280x1024      75.0  
   1152x864       75.0  
   1280x720       50.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DP2 disconnected (normal left inverted right x axis y axis)

```
In reality, the size is not 160mm x 90mm, but 476mm x 268mm. This screws up the dpi value badly.

The first thing I tried was injecting the missing information via xorg.conf:
```
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Samsung"
	ModelName    "SyncMaster"
	DisplaySize  476 268
EndSection

```
Initially, this seems to work. In Xorg.0.log, the following lines can be found (shortened, but still a bit longish. Sorry for that.):
```
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
<...>
(II) intel(0): Creating default Display subsection in Screen section
	"Screen0" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) G41
(--) intel(0): Chipset: "G41"
(II) intel(0): Output VGA1 using monitor section Monitor0
(II) intel(0): Output HDMI1 has no monitor section
(II) intel(0): Output DP1 has no monitor section
(II) intel(0): Output HDMI2 using monitor section SAM-HDMI
(II) intel(0): Output DP2 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output HDMI1
(II) intel(0): EDID for output DP1
(II) Quirked EDID physical size to 0x0 cm
(II) intel(0): EDID for output HDMI2
(II) intel(0): Manufacturer: SAM  Model: 579  Serial#: 0
(II) intel(0): Year: 2009  Week: 11
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Indeterminate output size
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
(II) intel(0): blueX: 0.143 blueY: 0.070   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
<...>
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
<...>
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  160 x 90 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
(II) intel(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
(II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
(II) intel(0): Ranges: V min: 24 V max: 75 Hz, H min: 26 H max: 81 kHz, PixClock max 230 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Number of EDID sections to follow: 1
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2d790500000000
(II) intel(0): 	0b130103801009780a3581a656489a24
(II) intel(0): 	125054bfef80714f81408180a9408100
(II) intel(0): 	b30095000101023a801871382d40582c
(II) intel(0): 	4500a05a0000001e011d00bc52d01e20
(II) intel(0): 	b8285540a05a0000001e000000fd0018
(II) intel(0): 	4b1a5117000a202020202020000000fc
(II) intel(0): 	0053796e634d61737465720a20200172
(II) intel(0): Printing probed modes for output HDMI2
(II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
<...>
(II) intel(0): EDID for output DP2
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output HDMI1 disconnected
(II) intel(0): Output DP1 disconnected
(II) intel(0): Output HDMI2 connected
(II) intel(0): Output DP2 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output HDMI2 using initial mode 1920x1080
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (476, 268) mm
(**) intel(0): DPI set to (102, 102)
(II) Loading sub module "fb"
<...>
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 476 x 268
<...>

```
The problem is, the protocoll does not stop there. When everything is up and running and I am logged in, EDID data have been read again. The following lines appear in the log *three more times*:
```
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output HDMI1
(II) intel(0): EDID for output DP1
(II) Quirked EDID physical size to 0x0 cm
(II) intel(0): EDID for output HDMI2
(II) intel(0): Manufacturer: SAM  Model: 579  Serial#: 0
(II) intel(0): Year: 2009  Week: 11
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Indeterminate output size
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
(II) intel(0): blueX: 0.143 blueY: 0.070   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
<...>
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
<...>
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  160 x 90 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
(II) intel(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
(II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
(II) intel(0): Ranges: V min: 24 V max: 75 Hz, H min: 26 H max: 81 kHz, PixClock max 230 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Number of EDID sections to follow: 1
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2d790500000000
(II) intel(0): 	0b130103801009780a3581a656489a24
(II) intel(0): 	125054bfef80714f81408180a9408100
(II) intel(0): 	b30095000101023a801871382d40582c
(II) intel(0): 	4500a05a0000001e011d00bc52d01e20
(II) intel(0): 	b8285540a05a0000001e000000fd0018
(II) intel(0): 	4b1a5117000a202020202020000000fc
(II) intel(0): 	0053796e634d61737465720a20200172
(II) intel(0): EDID vendor "SAM", prod id 1401
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
<...>
(II) intel(0): Printing probed modes for output HDMI2
(II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
<...>
(II) intel(0): EDID for output DP2

```
The same lines get added again each time xrandr (or gnome-display-properties) is called. Even when I do

xrandr --output HDMI2 --fbmm 476x268

although applications working with dpi information pick up correct values afterwards.

My guess is that gdm calls xrandr after the initial setup, but I can't find when and how. Inserting the above tweak line at /etc/gdm/PreSession did not help. Any other ideas?

---

### Post by ccprog on 2010-04-25
I found it:

gconf has two settings responsible for calling xrandr,
apps > gdm > simple-greeter > settings-manager-plugins > xrandr
apps > gnome_settings_daemon > plugin > xrandr

I needed to set the keys active=false for both, and the spurious calls ended. This does not mean, btw, that you cannot call xrandr directly. But now the only place where I still get false size information is gnome-display-properties, which reports the screen size at 7 inches. I can live with that.

---


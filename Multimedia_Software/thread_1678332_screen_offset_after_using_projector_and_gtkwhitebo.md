---
title: "screen offset after using projector and gtkwhiteboard"
date: 2011-01-30
forum: Multimedia Software
---

### Post by peppeprof on 2011-01-30
Ubuntu 10.10
Asus UL30A
graphic chipset Intel GMA 4500 MHD

Native LVDS1 display resolution is 1366x768, but my laptop now boots at 800x600. Using xrandr to set resolution at 1366x768, I get the right dot pitch but the screen is still 800x600 px wide, left-top aligned on a 1366x768 display, so that I see a 168px black belt on bottom and a 566 black belt on the right. A vertical screen offset of 168 px affects also the pointer (touchpad) in the following way - I can move and see the pointer arrow all the display wide including the black region, but input (click) is taken for a position 168 px above the pointer visible position.
This is happening after having used the laptop with an external projector and gtkwhiteboard (wiimote based infrared pointer management). I then removed gtkwhiteboard to no effect.

Everything works fine when booting in failsafeX, recovery mode. 

Here is output of **uname -a**
```
Linux bidolino 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 
x86_64 GNU/Linux
```
the relevant part of **dmesg**
```
[   21.223998] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[   21.226034] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[   21.671324] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000

```
the output of **xrandr** at boot
```
Screen 0: minimum 320 x 200, current 800 x 600, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 800x600+0+0 (normal left inverted right x axis y axis) 293mm x 164mm
   1366x768       60.0 +
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3*    56.2  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
```
[IMG]https://docs.google.com/leaf?id=0ByetO80-uuTaMDk0MDFhNWItZThkNS00ZjEzLTlhYzctZDYyZTc5YjE2ODk3&hl=en[/IMG]
and after the command **xrandr -s 1366x768**
```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 293mm x 164mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

```
[IMG]https://docs.google.com/leaf?id=0ByetO80-uuTaOTQ0ZWZhODctY2U2NS00YzVjLTkwMGQtNjlhNzc3OWFmYWIy&hl=en[/IMG]
Finally, the content of **/var/log/Xorg.0.log** at boot
```
[    20.844] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    20.844] X Protocol Version 11, Revision 0
[    20.844] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    20.844] Current Operating System: Linux bidolino 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64
[    20.844] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=6f044c97-0cbd-4f2c-bb68-67ec2473024c ro quiet splash
[    20.844] Build Date: 09 January 2011  12:14:27PM
[    20.844] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    20.844] Current version of pixman: 0.18.4
[    20.844] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    20.844] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.844] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 30 10:44:45 2011
[    20.909] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.965] (==) No Layout section.  Using the first Screen section.
[    20.965] (==) No screen section available. Using defaults.
[    20.965] (**) |-->Screen "Default Screen Section" (0)
[    20.965] (**) |   |-->Monitor "<default monitor>"
[    20.966] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    20.966] (==) Automatically adding devices
[    20.966] (==) Automatically enabling devices
[    21.011] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.011] 	Entry deleted from font path.
[    21.046] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    21.046] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.046] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.046] (II) Loader magic: 0x7d17a0
[    21.046] (II) Module ABI versions:
[    21.046] 	X.Org ANSI C Emulation: 0.4
[    21.046] 	X.Org Video Driver: 8.0
[    21.046] 	X.Org XInput driver : 11.0
[    21.046] 	X.Org Server Extension : 4.0
[    21.048] (--) PCI:*(0:0:2:0) 8086:2a42:1043:1862 rev 7, Mem @ 0xfe400000/4194304, 0xd0000000/268435456, I/O @ 0x0000dc00/8
[    21.048] (--) PCI: (0:0:2:1) 8086:2a43:1043:1862 rev 7, Mem @ 0xfe800000/1048576
[    21.048] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    21.048] (II) LoadModule: "extmod"
[    21.051] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.060] (II) Module extmod: vendor="X.Org Foundation"
[    21.060] 	compiled for 1.9.0, module version = 1.0.0
[    21.060] 	Module class: X.Org Server Extension
[    21.060] 	ABI class: X.Org Server Extension, version 4.0
[    21.060] (II) Loading extension MIT-SCREEN-SAVER
[    21.060] (II) Loading extension XFree86-VidModeExtension
[    21.060] (II) Loading extension XFree86-DGA
[    21.060] (II) Loading extension DPMS
[    21.060] (II) Loading extension XVideo
[    21.060] (II) Loading extension XVideo-MotionCompensation
[    21.060] (II) Loading extension X-Resource
[    21.060] (II) LoadModule: "dbe"
[    21.061] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.066] (II) Module dbe: vendor="X.Org Foundation"
[    21.066] 	compiled for 1.9.0, module version = 1.0.0
[    21.066] 	Module class: X.Org Server Extension
[    21.066] 	ABI class: X.Org Server Extension, version 4.0
[    21.066] (II) Loading extension DOUBLE-BUFFER
[    21.066] (II) LoadModule: "glx"
[    21.066] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.083] (II) Module glx: vendor="X.Org Foundation"
[    21.083] 	compiled for 1.9.0, module version = 1.0.0
[    21.083] 	ABI class: X.Org Server Extension, version 4.0
[    21.083] (==) AIGLX enabled
[    21.083] (II) Loading extension GLX
[    21.084] (II) LoadModule: "record"
[    21.085] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.098] (II) Module record: vendor="X.Org Foundation"
[    21.098] 	compiled for 1.9.0, module version = 1.13.0
[    21.098] 	Module class: X.Org Server Extension
[    21.098] 	ABI class: X.Org Server Extension, version 4.0
[    21.098] (II) Loading extension RECORD
[    21.098] (II) LoadModule: "dri"
[    21.099] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.132] (II) Module dri: vendor="X.Org Foundation"
[    21.132] 	compiled for 1.9.0, module version = 1.0.0
[    21.132] 	ABI class: X.Org Server Extension, version 4.0
[    21.132] (II) Loading extension XFree86-DRI
[    21.132] (II) LoadModule: "dri2"
[    21.132] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.159] (II) Module dri2: vendor="X.Org Foundation"
[    21.159] 	compiled for 1.9.0, module version = 1.2.0
[    21.159] 	ABI class: X.Org Server Extension, version 4.0
[    21.159] (II) Loading extension DRI2
[    21.159] (==) Matched intel as autoconfigured driver 0
[    21.159] (==) Matched vesa as autoconfigured driver 1
[    21.159] (==) Matched fbdev as autoconfigured driver 2
[    21.159] (==) Assigned the driver to the xf86ConfigLayout
[    21.159] (II) LoadModule: "intel"
[    21.159] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    21.172] (II) Module intel: vendor="X.Org Foundation"
[    21.172] 	compiled for 1.9.0, module version = 2.12.0
[    21.172] 	Module class: X.Org Video Driver
[    21.172] 	ABI class: X.Org Video Driver, version 8.0
[    21.172] (II) LoadModule: "vesa"
[    21.172] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.185] (II) Module vesa: vendor="X.Org Foundation"
[    21.185] 	compiled for 1.8.99.905, module version = 2.3.0
[    21.185] 	Module class: X.Org Video Driver
[    21.185] 	ABI class: X.Org Video Driver, version 8.0
[    21.185] (II) LoadModule: "fbdev"
[    21.185] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.189] (II) Module fbdev: vendor="X.Org Foundation"
[    21.189] 	compiled for 1.8.99.905, module version = 0.4.2
[    21.189] 	ABI class: X.Org Video Driver, version 8.0
[    21.189] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    21.190] (II) VESA: driver for VESA chipsets: vesa
[    21.190] (II) FBDEV: driver for framebuffer: fbdev
[    21.190] (++) using VT number 7

[    21.190] (WW) Falling back to old probe method for vesa
[    21.190] (WW) Falling back to old probe method for fbdev
[    21.190] (II) Loading sub module "fbdevhw"
[    21.190] (II) LoadModule: "fbdevhw"
[    21.191] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.204] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.204] 	compiled for 1.9.0, module version = 0.0.2
[    21.204] 	ABI class: X.Org Video Driver, version 8.0
[    21.206] drmOpenDevice: node name is /dev/dri/card0
[    21.206] drmOpenDevice: open result is 8, (OK)
[    21.206] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    21.206] drmOpenDevice: node name is /dev/dri/card0
[    21.206] drmOpenDevice: open result is 8, (OK)
[    21.206] drmOpenByBusid: drmOpenMinor returns 8
[    21.206] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    21.207] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    21.207] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    21.207] (==) intel(0): RGB weight 888
[    21.207] (==) intel(0): Default visual is TrueColor
[    21.207] (II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[    21.207] (--) intel(0): Chipset: "GM45"
[    21.207] (==) intel(0): video overlay key set to 0x101fe
[    21.242] (II) intel(0): Output VGA1 has no monitor section
[    21.242] (II) intel(0): Output LVDS1 has no monitor section
[    21.242] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    21.252] (II) intel(0): Output HDMI1 has no monitor section
[    21.252] (II) intel(0): Output DP1 has no monitor section
[    21.253] (II) intel(0): Output DP2 has no monitor section
[    21.292] (II) intel(0): EDID for output VGA1
[    21.292] (II) intel(0): EDID for output LVDS1
[    21.292] (II) intel(0): Manufacturer: AUO  Model: 102c  Serial#: 0
[    21.292] (II) intel(0): Year: 2008  Week: 1
[    21.292] (II) intel(0): EDID Version: 1.3
[    21.292] (II) intel(0): Digital Display Input
[    21.292] (II) intel(0): Max Image Size [cm]: horiz.: 29  vert.: 16
[    21.292] (II) intel(0): Gamma: 2.20
[    21.292] (II) intel(0): No DPMS capabilities specified
[    21.292] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    21.292] (II) intel(0): First detailed timing is preferred mode
[    21.292] (II) intel(0): redX: 0.607 redY: 0.351   greenX: 0.330 greenY: 0.619
[    21.292] (II) intel(0): blueX: 0.149 blueY: 0.104   whiteX: 0.302 whiteY: 0.321
[    21.292] (II) intel(0): Manufacturer's mask: 0
[    21.292] (II) intel(0): Supported detailed timing:
[    21.293] (II) intel(0): clock: 72.0 MHz   Image Size:  293 x 164 mm
[    21.293] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1494 h_border: 0
[    21.293] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
[    21.293] (II) intel(0): Unknown vendor-specific block f
[    21.293] (II) intel(0):  AUO
[    21.293] (II) intel(0):  B133XW01 V0
[    21.293] (II) intel(0): EDID (in hex):
[    21.293] (II) intel(0): 	00ffffffffffff0006af2c1000000000
[    21.293] (II) intel(0): 	01120103801d10780aba659b59549e26
[    21.293] (II) intel(0): 	1a4d5200000001010101010101010101
[    21.293] (II) intel(0): 	010101010101201c5680500023303020
[    21.293] (II) intel(0): 	360025a4100000180000000f00000000
[    21.293] (II) intel(0): 	00000000000000000020000000fe0041
[    21.293] (II) intel(0): 	554f0a202020202020202020000000fe
[    21.293] (II) intel(0): 	004231333358573031205630200a00bc
[    21.293] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    21.293] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    21.293] (II) intel(0): Printing probed modes for output LVDS1
[    21.294] (II) intel(0): Modeline "1366x768"x60.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    21.294] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    21.294] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    21.294] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    21.294] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    21.294] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    21.294] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    21.303] (II) intel(0): EDID for output HDMI1
[    21.303] (II) intel(0): EDID for output DP1
[    21.304] (II) intel(0): EDID for output DP2
[    21.304] (II) intel(0): Output VGA1 disconnected
[    21.304] (II) intel(0): Output LVDS1 connected
[    21.304] (II) intel(0): Output HDMI1 disconnected
[    21.304] (II) intel(0): Output DP1 disconnected
[    21.304] (II) intel(0): Output DP2 disconnected
[    21.304] (II) intel(0): Using exact sizes for initial modes
[    21.304] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    21.304] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    21.304] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    21.304] (==) intel(0): DPI set to (96, 96)
[    21.304] (II) Loading sub module "fb"
[    21.304] (II) LoadModule: "fb"
[    21.305] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.599] (II) Module fb: vendor="X.Org Foundation"
[    21.614] 	compiled for 1.9.0, module version = 1.0.0
[    21.614] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.614] (II) UnloadModule: "vesa"
[    21.614] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.614] (II) UnloadModule: "fbdev"
[    21.614] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.614] (II) UnloadModule: "fbdevhw"
[    21.614] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    21.614] (==) Depth 24 pixmap format is 32 bpp
[    21.614] (II) intel(0): [DRI2] Setup complete
[    21.614] (II) intel(0): [DRI2]   DRI driver: i965
[    21.614] (**) intel(0): Tiling enabled
[    21.614] (**) intel(0): SwapBuffers wait enabled
[    21.614] (==) intel(0): VideoRam: 262144 KB
[    21.614] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    21.880] (II) UXA(0): Driver registered support for the following operations:
[    21.880] (II)         solid
[    21.880] (II)         copy
[    21.880] (II)         composite (RENDER acceleration)
[    21.880] (II)         put_image
[    21.880] (II)         get_image
[    21.880] (==) intel(0): Backing store disabled
[    21.880] (==) intel(0): Silken mouse enabled
[    21.880] (II) intel(0): Initializing HW Cursor
[    21.920] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.922] (==) intel(0): DPMS enabled
[    21.922] (==) intel(0): Intel XvMC decoder enabled
[    21.922] (II) intel(0): Set up textured video
[    21.922] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    21.922] (II) intel(0): direct rendering: DRI2 Enabled
[    21.922] (--) RandR disabled
[    21.922] (II) Initializing built-in extension Generic Event Extension
[    21.922] (II) Initializing built-in extension SHAPE
[    21.922] (II) Initializing built-in extension MIT-SHM
[    21.922] (II) Initializing built-in extension XInputExtension
[    21.922] (II) Initializing built-in extension XTEST
[    21.922] (II) Initializing built-in extension BIG-REQUESTS
[    21.922] (II) Initializing built-in extension SYNC
[    21.922] (II) Initializing built-in extension XKEYBOARD
[    21.922] (II) Initializing built-in extension XC-MISC
[    21.922] (II) Initializing built-in extension SECURITY
[    21.922] (II) Initializing built-in extension XINERAMA
[    21.922] (II) Initializing built-in extension XFIXES
[    21.922] (II) Initializing built-in extension RENDER
[    21.922] (II) Initializing built-in extension RANDR
[    21.922] (II) Initializing built-in extension COMPOSITE
[    21.922] (II) Initializing built-in extension DAMAGE
[    21.922] (II) Initializing built-in extension GESTURE
[    22.168] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    22.168] (II) AIGLX: enabled GLX_INTEL_swap_event
[    22.168] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    22.168] (II) AIGLX: enabled GLX_SGI_make_current_read
[    22.168] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    22.168] (II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
[    22.168] (II) GLX: Initialized DRI2 GL provider for screen 0
[    22.169] (II) intel(0): Setting screen physical size to 361 x 203
[    22.442] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.465] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    22.466] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.466] (II) LoadModule: "evdev"
[    22.466] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.488] (II) Module evdev: vendor="X.Org Foundation"
[    22.488] 	compiled for 1.9.0, module version = 2.3.2
[    22.488] 	Module class: X.Org XInput Driver
[    22.488] 	ABI class: X.Org XInput driver, version 11.0
[    22.488] (**) Power Button: always reports core events
[    22.488] (**) Power Button: Device: "/dev/input/event2"
[    22.510] (II) Power Button: Found keys
[    22.510] (II) Power Button: Configuring as keyboard
[    22.510] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.510] (**) Option "xkb_rules" "evdev"
[    22.510] (**) Option "xkb_model" "evdev"
[    22.510] (**) Option "xkb_layout" "it"
[    22.513] (II) XKB: reuse xkmfile /var/lib/xkb/server-35DF0DEC488035CD7337E5EF69F018BFAFADCAC5.xkm
[    22.514] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    22.514] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    22.514] (**) Video Bus: always reports core events
[    22.514] (**) Video Bus: Device: "/dev/input/event7"
[    22.540] (II) Video Bus: Found keys
[    22.540] (II) Video Bus: Configuring as keyboard
[    22.540] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    22.540] (**) Option "xkb_rules" "evdev"
[    22.540] (**) Option "xkb_model" "evdev"
[    22.540] (**) Option "xkb_layout" "it"
[    22.543] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    22.543] (II) No input driver/identifier specified (ignoring)
[    22.544] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    22.544] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    22.544] (**) Sleep Button: always reports core events
[    22.544] (**) Sleep Button: Device: "/dev/input/event0"
[    22.570] (II) Sleep Button: Found keys
[    22.570] (II) Sleep Button: Configuring as keyboard
[    22.570] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    22.570] (**) Option "xkb_rules" "evdev"
[    22.570] (**) Option "xkb_model" "evdev"
[    22.570] (**) Option "xkb_layout" "it"
[    22.573] (II) config/udev: Adding input device USB2.0 0.3M UVC WebCam (/dev/input/event5)
[    22.573] (**) USB2.0 0.3M UVC WebCam: Applying InputClass "evdev keyboard catchall"
[    22.573] (**) USB2.0 0.3M UVC WebCam: always reports core events
[    22.573] (**) USB2.0 0.3M UVC WebCam: Device: "/dev/input/event5"
[    22.592] (II) USB2.0 0.3M UVC WebCam: Found keys
[    22.592] (II) USB2.0 0.3M UVC WebCam: Configuring as keyboard
[    22.592] (II) XINPUT: Adding extended input device "USB2.0 0.3M UVC WebCam" (type: KEYBOARD)
[    22.592] (**) Option "xkb_rules" "evdev"
[    22.592] (**) Option "xkb_model" "evdev"
[    22.592] (**) Option "xkb_layout" "it"
[    22.598] (II) config/udev: Adding input device Asus Laptop extra buttons (/dev/input/event4)
[    22.598] (**) Asus Laptop extra buttons: Applying InputClass "evdev keyboard catchall"
[    22.598] (**) Asus Laptop extra buttons: always reports core events
[    22.598] (**) Asus Laptop extra buttons: Device: "/dev/input/event4"
[    22.622] (II) Asus Laptop extra buttons: Found keys
[    22.622] (II) Asus Laptop extra buttons: Configuring as keyboard
[    22.622] (II) XINPUT: Adding extended input device "Asus Laptop extra buttons" (type: KEYBOARD)
[    22.622] (**) Option "xkb_rules" "evdev"
[    22.622] (**) Option "xkb_model" "evdev"
[    22.622] (**) Option "xkb_layout" "it"
[    22.623] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    22.623] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    22.623] (**) AT Translated Set 2 keyboard: always reports core events
[    22.623] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    22.640] (II) AT Translated Set 2 keyboard: Found keys
[    22.640] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    22.640] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    22.640] (**) Option "xkb_rules" "evdev"
[    22.640] (**) Option "xkb_model" "evdev"
[    22.640] (**) Option "xkb_layout" "it"
[    22.640] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[    22.640] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    22.640] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    22.640] (II) LoadModule: "synaptics"
[    22.641] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    22.743] (II) Module synaptics: vendor="X.Org Foundation"
[    22.743] 	compiled for 1.9.0, module version = 1.2.2
[    22.743] 	Module class: X.Org XInput Driver
[    22.743] 	ABI class: X.Org XInput driver, version 11.0
[    22.743] (II) Synaptics touchpad driver version 1.2.2
[    22.743] (**) Option "Device" "/dev/input/event6"
[    22.850] (II) ETPS/2 Elantech Touchpad: x-axis range 8 - 1144
[    22.850] (II) ETPS/2 Elantech Touchpad: y-axis range 8 - 760
[    22.850] (II) ETPS/2 Elantech Touchpad: device does not report pressure, will use touch data.
[    22.850] (II) ETPS/2 Elantech Touchpad: finger width range 0 - 0
[    22.850] (II) ETPS/2 Elantech Touchpad: buttons: left right double triple
[    22.950] (--) ETPS/2 Elantech Touchpad: touchpad found
[    22.950] (**) ETPS/2 Elantech Touchpad: always reports core events
[    23.000] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD)
[    23.000] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    23.000] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 0
[    23.000] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    23.000] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    23.090] (--) ETPS/2 Elantech Touchpad: touchpad found
[    23.090] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    23.090] (II) No input driver/identifier specified (ignoring)
[    28.730] (II) intel(0): EDID vendor "AUO", prod id 4140
[    28.730] (II) intel(0): Printing DDC gathered Modelines:
[    28.730] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    28.890] (II) intel(0): EDID vendor "AUO", prod id 4140
[    28.890] (II) intel(0): Printing DDC gathered Modelines:
[    28.890] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    28.962] (II) intel(0): EDID vendor "AUO", prod id 4140
[    28.962] (II) intel(0): Printing DDC gathered Modelines:
[    28.962] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    29.254] (II) intel(0): Allocated new frame buffer 832x600 stride 3584, tiled
[    34.650] (II) intel(0): EDID vendor "AUO", prod id 4140
[    34.650] (II) intel(0): Printing DDC gathered Modelines:
[    34.650] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    37.370] (II) intel(0): EDID vendor "AUO", prod id 4140
[    37.370] (II) intel(0): Printing DDC gathered Modelines:
[    37.370] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
```

---

### Post by peppeprof on 2011-02-01
**Created a new user!**
Starting a session as the new user all goes really ok, resolution, projector use, even gtkwhiteboard which was reinstalled.
Since I was not able to reproduce the problem, I would just appreciate any help to solve it for the old user, thanks!

---

### Post by peppeprof on 2011-02-05
Oops, I didn't notice that the links to the snapshots I had added to first post are not working - maybe because google documents address uses https protocol - so here they are as an attachment.

I just notice that in the snapshot I took at 1366x768 with the printscreen key you can see the whole physical display, while in the one at 800x600 the two black lateral stripes (1366-800)/2 px wide are absent. 

So I guess the screen is correctly defined in both cases. Could it be a GDM problem, which could also explain the fact that the whole issue is user dependent?

Any clue, hint or even simply correcting the words I am using would be appreciated, thanks!

---

### Post by peppeprof on 2011-02-10
**Problem Solved** by brute force...
I just **deleted the file /home/username/.config/monitors.xlm** and everything works now.

It was a gnome problem indeed, not Xorg. And I guess the messed up monitors.xlm was an effect of some circumstances in the use of external projector.

The guilty monitors.xlm:
```
<monitors version="1">
  <configuration>
      <clone>yes</clone>
      <output name="VGA1">
          <vendor>BNQ</vendor>
          <product>0x7101</product>
          <serial>0x00000adf</serial>
          <width>1024</width>
          <height>768</height>
          <rate>60</rate>
          <x>1366</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="LVDS1">
          <vendor>AUO</vendor>
          <product>0x102c</product>
          <serial>0x00000000</serial>
          <width>1024</width>
          <height>768</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="HDMI1">
      </output>
      <output name="DP1">
      </output>
      <output name="DP2">
      </output>
  </configuration>
  <configuration>
      <clone>yes</clone>
      <output name="VGA1">
          <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>1360</width>
          <height>768</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="LVDS1">
          <vendor>AUO</vendor>
          <product>0x102c</product>
          <serial>0x00000000</serial>
          <width>1360</width>
          <height>768</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="HDMI1">
      </output>
      <output name="DP1">
      </output>
      <output name="DP2">
      </output>
  </configuration>
  <configuration>
      <clone>no</clone>
      <output name="VGA1">
          <vendor>BNQ</vendor>
          <product>0x9a01</product>
          <serial>0x00000747</serial>
          <width>1024</width>
          <height>768</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="LVDS1">
          <vendor>AUO</vendor>
          <product>0x102c</product>
          <serial>0x00000000</serial>
      </output>
      <output name="HDMI1">
      </output>
      <output name="DP1">
      </output>
      <output name="DP2">
      </output>
  </configuration>
  <configuration>
      <clone>no</clone>
      <output name="VGA1">
      </output>
      <output name="LVDS1">
          <vendor>AUO</vendor>
          <product>0x102c</product>
          <serial>0x00000000</serial>
          <width>800</width>
          <height>600</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="HDMI1">
      </output>
      <output name="DP1">
      </output>
      <output name="DP2">
      </output>
  </configuration>
</monitors>
```

---


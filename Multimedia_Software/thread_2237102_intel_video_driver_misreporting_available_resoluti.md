---
title: "intel video driver misreporting available resolutions"
date: 2014-07-30
forum: Multimedia Software
---

### Post by Lathan_Bidwell on 2014-07-30
I have a Dell Lattitude E6510 with a Intel® HD Graphics instead of the NVIDIA option.

The laptop came with windows 7 running 1920x1080 resolution, and I've doublechecked the specs for my dell service tag, the video card should support 1920x1080.

I am running 14.04.1, using the intel-graphics-installer ... 1.05 in an attempt to get this working.

The driver only reports resolutions up to 1336x768 as available.

I have gone over the walkthroughs on how to use xrandr to add unrecognized resolutions, but it gives an error on a critical step.

So, here is what I have done:
```
xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
eDP1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+   40.0  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

So, I see the 1336x768 resolution on eDP1, so I go to create a new mode and attach it to eDP1

```
cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
```
```
xrandr --newmode 1920x1080 173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
```
```
xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
eDP1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+   40.0  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
  1920x1080 (0xbb)  173.0MHz
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz
        v: height 1080 start 1083 end 1088 total 1120           clock   60.0Hz

```
```
xrandr --addmode eDP1 1920x1080
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  42
  Current serial number in output stream:  43
```

From my research on forums and walkthroughs, I've managed to understand that this means it thinks a mode is incorrect / out of bounds of something. And it is my belief that the intel driver is saying that mode can't work because its outside of the bounds of what it thinks the card can handle. (even though the card can handle full 1920x1080)

Here is my xorg.0.log:
```
[    18.555] X.Org X Server 1.15.1
Release Date: 2014-04-13
[    18.555] X Protocol Version 11, Revision 0
[    18.555] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    18.555] Current Operating System: Linux 5700c-lathanlaptop 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64
[    18.555] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=85ba0ba2-5129-418a-94f5-a69c6c235efb ro quiet splash vt.handoff=7
[    18.555] Build Date: 16 April 2014  01:36:29PM
[    18.555] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    18.555] Current version of pixman: 0.30.2
[    18.555]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    18.555] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.555] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 30 16:40:23 2014
[    18.555] (==) Using config file: "/etc/X11/xorg.conf"
[    18.555] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.577] (==) ServerLayout "X.org Configured"
[    18.577] (**) |-->Screen "Screen0" (0)
[    18.577] (**) |   |-->Monitor "Monitor0"
[    18.577] (**) |   |-->Device "Card0"
[    18.577] (**) |-->Input Device "Mouse0"
[    18.577] (**) |-->Input Device "Keyboard0"
[    18.577] (==) Automatically adding devices
[    18.577] (==) Automatically enabling devices
[    18.577] (==) Automatically adding GPU devices
[    18.577] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.577]     Entry deleted from font path.
[    18.577] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.577]     Entry deleted from font path.
[    18.577] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.577]     Entry deleted from font path.
[    18.577] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.577]     Entry deleted from font path.
[    18.577] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.577]     Entry deleted from font path.
[    18.577] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.577]     Entry deleted from font path.
[    18.577] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.577]     Entry deleted from font path.
[    18.577] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.577]     Entry deleted from font path.
[    18.577] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.577]     Entry deleted from font path.
[    18.577] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.577]     Entry deleted from font path.
[    18.577] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    18.577] (**) ModulePath set to "/usr/lib/xorg/modules"
[    18.577] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    18.577] (WW) Disabling Mouse0
[    18.577] (WW) Disabling Keyboard0
[    18.577] (II) Loader magic: 0x7f1c1423bd60
[    18.577] (II) Module ABI versions:
[    18.577]     X.Org ANSI C Emulation: 0.4
[    18.577]     X.Org Video Driver: 15.0
[    18.577]     X.Org XInput driver : 20.0
[    18.577]     X.Org Server Extension : 8.0
[    18.577] (II) xfree86: Adding drm device (/dev/dri/card0)
[    18.579] (--) PCI:*(0:0:2:0) 8086:0046:1028:040b rev 2, Mem @ 0xf0000000/4194304, 0xe0000000/268435456, I/O @ 0x000070b0/8
[    18.579] Initializing built-in extension Generic Event Extension
[    18.579] Initializing built-in extension SHAPE
[    18.579] Initializing built-in extension MIT-SHM
[    18.579] Initializing built-in extension XInputExtension
[    18.579] Initializing built-in extension XTEST
[    18.579] Initializing built-in extension BIG-REQUESTS
[    18.579] Initializing built-in extension SYNC
[    18.579] Initializing built-in extension XKEYBOARD
[    18.579] Initializing built-in extension XC-MISC
[    18.579] Initializing built-in extension SECURITY
[    18.579] Initializing built-in extension XINERAMA
[    18.579] Initializing built-in extension XFIXES
[    18.579] Initializing built-in extension RENDER
[    18.579] Initializing built-in extension RANDR
[    18.579] Initializing built-in extension COMPOSITE
[    18.579] Initializing built-in extension DAMAGE
[    18.579] Initializing built-in extension MIT-SCREEN-SAVER
[    18.579] Initializing built-in extension DOUBLE-BUFFER
[    18.579] Initializing built-in extension RECORD
[    18.579] Initializing built-in extension DPMS
[    18.579] Initializing built-in extension Present
[    18.579] Initializing built-in extension DRI3
[    18.579] Initializing built-in extension X-Resource
[    18.579] Initializing built-in extension XVideo
[    18.579] Initializing built-in extension XVideo-MotionCompensation
[    18.579] Initializing built-in extension SELinux
[    18.579] Initializing built-in extension XFree86-VidModeExtension
[    18.579] Initializing built-in extension XFree86-DGA
[    18.579] Initializing built-in extension XFree86-DRI
[    18.579] Initializing built-in extension DRI2
[    18.579] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    18.579] (WW) "xmir" is not to be loaded by default. Skipping.
[    18.579] (II) LoadModule: "glx"
[    18.579] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.794] (II) Module glx: vendor="X.Org Foundation"
[    18.794]     compiled for 1.15.1, module version = 1.0.0
[    18.794]     ABI class: X.Org Server Extension, version 8.0
[    18.794] (==) AIGLX enabled
[    18.794] Loading extension GLX
[    18.794] (II) LoadModule: "intel"
[    18.794] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    18.803] (II) Module intel: vendor="X.Org Foundation"
[    18.803]     compiled for 1.15.0, module version = 2.99.910
[    18.803]     Module class: X.Org Video Driver
[    18.803]     ABI class: X.Org Video Driver, version 15.0
[    18.803] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    18.803] (II) intel: Driver for Intel(R) HD Graphics: 2000-5000
[    18.803] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100
[    18.803] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200
[    18.803] (++) using VT number 7


[    18.803] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1 (Timo Aaltonen <tjaalton@ubuntu.com>)
[    18.804] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics
[    18.804] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2
[    18.804] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    18.804] (==) intel(0): RGB weight 888
[    18.804] (==) intel(0): Default visual is TrueColor
[    18.804] (**) intel(0): Framebuffer tiled
[    18.804] (**) intel(0): Pixmaps tiled
[    18.804] (**) intel(0): "Tear free" disabled
[    18.804] (**) intel(0): Forcing per-crtc-pixmaps? no
[    18.804] (II) intel(0): Output eDP1 using monitor section Monitor0
[    18.804] (**) intel(0): Option "PreferredMode" "1920x1080_60.00"
[    18.820] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')
[    18.820] (II) intel(0): Output VGA1 has no monitor section
[    18.820] (II) intel(0): Output HDMI1 has no monitor section
[    18.820] (II) intel(0): Output DP1 has no monitor section
[    18.820] (II) intel(0): Output HDMI2 has no monitor section
[    18.820] (II) intel(0): Output HDMI3 has no monitor section
[    18.820] (II) intel(0): Output DP2 has no monitor section
[    18.820] (II) intel(0): Output DP3 has no monitor section
[    18.820] (II) intel(0): Output VIRTUAL1 has no monitor section
[    18.820] (II) intel(0): EDID for output eDP1
[    18.820] (II) intel(0): Manufacturer: LGD  Model: 24b  Serial#: 0
[    18.820] (II) intel(0): Year: 2010  Week: 0
[    18.820] (II) intel(0): EDID Version: 1.4
[    18.820] (II) intel(0): Digital Display Input
[    18.820] (II) intel(0): 6 bits per channel
[    18.820] (II) intel(0): Digital interface is DisplayPort
[    18.820] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    18.820] (II) intel(0): Gamma: 2.20
[    18.820] (II) intel(0): No DPMS capabilities specified
[    18.820] (II) intel(0): Supported color encodings: RGB 4:4:4 
[    18.820] (II) intel(0): First detailed timing is preferred mode
[    18.820] (II) intel(0): Preferred mode is native pixel format and refresh rate
[    18.820] (II) intel(0): redX: 0.622 redY: 0.365   greenX: 0.340 greenY: 0.607
[    18.820] (II) intel(0): blueX: 0.145 blueY: 0.100   whiteX: 0.313 whiteY: 0.329
[    18.820] (II) intel(0): Manufacturer's mask: 0
[    18.820] (II) intel(0): Supported detailed timing:
[    18.820] (II) intel(0): clock: 72.0 MHz   Image Size:  344 x 194 mm
[    18.820] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1520 h_border: 0
[    18.820] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    18.820] (II) intel(0): Supported detailed timing:
[    18.820] (II) intel(0): clock: 48.0 MHz   Image Size:  344 x 194 mm
[    18.820] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1520 h_border: 0
[    18.820] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    18.820] (II) intel(0):  G7W62\81156WH2
[    18.820] (II) intel(0): Unknown vendor-specific block 0
[    18.820] (II) intel(0): EDID (in hex):
[    18.820] (II) intel(0):     00ffffffffffff0030e44b0200000000
[    18.820] (II) intel(0):     00140104952213780262259f5d579b25
[    18.820] (II) intel(0):     19505400000001010101010101010101
[    18.820] (II) intel(0):     010101010101201c569a500016303020
[    18.820] (II) intel(0):     350058c21000001ac012569a50001630
[    18.820] (II) intel(0):     3020350058c21000001a000000fe0047
[    18.820] (II) intel(0):     37573632813135365748320a00000000
[    18.820] (II) intel(0):     00004101160000000009010a20200056
[    18.820] (II) intel(0): Not using mode "1920x1080_60.00" (exceeds panel dimensions)
[    18.820] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    18.820] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    18.820] (II) intel(0): Printing probed modes for output eDP1
[    18.820] (II) intel(0): Modeline "1366x768"x60.0   72.00  1366 1414 1446 1520  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    18.820] (II) intel(0): Modeline "1366x768"x40.0   48.00  1366 1414 1446 1520  768 771 776 790 +hsync -vsync (31.6 kHz e)
[    18.820] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    18.820] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    18.820] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    18.820] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    18.820] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    18.820] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    18.821] (II) intel(0): EDID for output VGA1
[    18.821] (II) intel(0): EDID for output HDMI1
[    18.821] (II) intel(0): EDID for output DP1
[    18.821] (II) intel(0): EDID for output HDMI2
[    18.822] (II) intel(0): EDID for output HDMI3
[    18.822] (II) intel(0): EDID for output DP2
[    18.822] (II) intel(0): EDID for output DP3
[    18.822] (II) intel(0): EDID for output VIRTUAL1
[    18.822] (II) intel(0): Output eDP1 connected
[    18.822] (II) intel(0): Output VGA1 disconnected
[    18.822] (II) intel(0): Output HDMI1 disconnected
[    18.822] (II) intel(0): Output DP1 disconnected
[    18.822] (II) intel(0): Output HDMI2 disconnected
[    18.822] (II) intel(0): Output HDMI3 disconnected
[    18.822] (II) intel(0): Output DP2 disconnected
[    18.822] (II) intel(0): Output DP3 disconnected
[    18.822] (II) intel(0): Output VIRTUAL1 disconnected
[    18.822] (II) intel(0): Using exact sizes for initial modes
[    18.822] (II) intel(0): Output eDP1 using initial mode 1366x768
[    18.822] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    18.822] (==) intel(0): DPI set to (96, 96)
[    18.822] (II) Loading sub module "dri2"
[    18.822] (II) LoadModule: "dri2"
[    18.822] (II) Module "dri2" already built-in
[    18.822] (==) Depth 24 pixmap format is 32 bpp
[    18.823] (II) intel(0): SNA initialized with Ironlake (gen5) backend
[    18.823] (==) intel(0): Backing store enabled
[    18.823] (==) intel(0): Silken mouse enabled
[    18.823] (II) intel(0): HW Cursor enabled
[    18.823] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    18.823] (==) intel(0): DPMS enabled
[    18.823] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    18.823] (II) intel(0): [DRI2] Setup complete
[    18.823] (II) intel(0): [DRI2]   DRI driver: i965
[    18.823] (II) intel(0): [DRI2]   VDPAU driver: i965
[    18.823] (II) intel(0): direct rendering: DRI2 Enabled
[    18.823] (WW) intel(0): Option "PreferredMode" is not used
[    18.823] (==) intel(0): hotplug detection: "enabled"
[    18.823] (--) RandR disabled
[    18.827] (II) SELinux: Disabled on system
[    18.832] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    18.832] (II) AIGLX: enabled GLX_ARB_create_context
[    18.832] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    18.832] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    18.832] (II) AIGLX: enabled GLX_INTEL_swap_event
[    18.832] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    18.832] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    18.832] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    18.832] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    18.832] (II) AIGLX: Loaded and initialized i965
[    18.832] (II) GLX: Initialized DRI2 GL provider for screen 0
[    18.841] (II) intel(0): switch to mode 1366x768@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    18.889] (II) intel(0): Setting screen physical size to 361 x 203
[    18.898] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.901] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    18.901] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.901] (II) LoadModule: "evdev"
[    18.901] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.924] (II) Module evdev: vendor="X.Org Foundation"
[    18.924]     compiled for 1.15.0, module version = 2.8.2
[    18.924]     Module class: X.Org XInput Driver
[    18.924]     ABI class: X.Org XInput driver, version 20.0
[    18.924] (II) Using input driver 'evdev' for 'Power Button'
[    18.924] (**) Power Button: always reports core events
[    18.924] (**) evdev: Power Button: Device: "/dev/input/event3"
[    18.924] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.924] (--) evdev: Power Button: Found keys
[    18.924] (II) evdev: Power Button: Configuring as keyboard
[    18.924] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    18.924] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    18.924] (**) Option "xkb_rules" "evdev"
[    18.924] (**) Option "xkb_model" "pc105"
[    18.924] (**) Option "xkb_layout" "us"
[    18.925] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[    18.925] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    18.925] (II) Using input driver 'evdev' for 'Video Bus'
[    18.925] (**) Video Bus: always reports core events
[    18.925] (**) evdev: Video Bus: Device: "/dev/input/event9"
[    18.925] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    18.925] (--) evdev: Video Bus: Found keys
[    18.925] (II) evdev: Video Bus: Configuring as keyboard
[    18.925] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:02/input/input10/event9"
[    18.925] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    18.925] (**) Option "xkb_rules" "evdev"
[    18.925] (**) Option "xkb_model" "pc105"
[    18.925] (**) Option "xkb_layout" "us"
[    18.925] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    18.925] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.925] (II) Using input driver 'evdev' for 'Power Button'
[    18.925] (**) Power Button: always reports core events
[    18.925] (**) evdev: Power Button: Device: "/dev/input/event1"
[    18.925] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.925] (--) evdev: Power Button: Found keys
[    18.925] (II) evdev: Power Button: Configuring as keyboard
[    18.925] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    18.925] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    18.925] (**) Option "xkb_rules" "evdev"
[    18.925] (**) Option "xkb_model" "pc105"
[    18.925] (**) Option "xkb_layout" "us"
[    18.925] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    18.925] (II) No input driver specified, ignoring this device.
[    18.925] (II) This device may have been added with another device file.
[    18.926] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    18.926] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    18.926] (II) Using input driver 'evdev' for 'Sleep Button'
[    18.926] (**) Sleep Button: always reports core events
[    18.926] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    18.926] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    18.926] (--) evdev: Sleep Button: Found keys
[    18.926] (II) evdev: Sleep Button: Configuring as keyboard
[    18.926] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    18.926] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    18.926] (**) Option "xkb_rules" "evdev"
[    18.926] (**) Option "xkb_model" "pc105"
[    18.926] (**) Option "xkb_layout" "us"
[    18.926] (II) config/udev: Adding drm device (/dev/dri/card0)
[    18.926] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    18.926] (II) config/udev: Adding input device Laptop_Integrated_Webcam_3M (/dev/input/event7)
[    18.926] (**) Laptop_Integrated_Webcam_3M: Applying InputClass "evdev keyboard catchall"
[    18.926] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_3M'
[    18.926] (**) Laptop_Integrated_Webcam_3M: always reports core events
[    18.926] (**) evdev: Laptop_Integrated_Webcam_3M: Device: "/dev/input/event7"
[    18.926] (--) evdev: Laptop_Integrated_Webcam_3M: Vendor 0x5ca Product 0x1814
[    18.926] (--) evdev: Laptop_Integrated_Webcam_3M: Found keys
[    18.926] (II) evdev: Laptop_Integrated_Webcam_3M: Configuring as keyboard
[    18.926] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input8/event7"
[    18.926] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_3M" (type: KEYBOARD, id 10)
[    18.926] (**) Option "xkb_rules" "evdev"
[    18.926] (**) Option "xkb_model" "pc105"
[    18.926] (**) Option "xkb_layout" "us"
[    18.927] (II) config/udev: Adding input device HDA Intel MID Dock Mic (/dev/input/event16)
[    18.927] (II) No input driver specified, ignoring this device.
[    18.927] (II) This device may have been added with another device file.
[    18.927] (II) config/udev: Adding input device HDA Intel MID Mic (/dev/input/event15)
[    18.927] (II) No input driver specified, ignoring this device.
[    18.927] (II) This device may have been added with another device file.
[    18.927] (II) config/udev: Adding input device HDA Intel MID Dock Line Out (/dev/input/event14)
[    18.927] (II) No input driver specified, ignoring this device.
[    18.927] (II) This device may have been added with another device file.
[    18.927] (II) config/udev: Adding input device HDA Intel MID Headphone (/dev/input/event13)
[    18.927] (II) No input driver specified, ignoring this device.
[    18.927] (II) This device may have been added with another device file.
[    18.927] (II) config/udev: Adding input device HDA Intel MID HDMI/DP,pcm=3 (/dev/input/event12)
[    18.928] (II) No input driver specified, ignoring this device.
[    18.928] (II) This device may have been added with another device file.
[    18.928] (II) config/udev: Adding input device HDA Intel MID HDMI/DP,pcm=7 (/dev/input/event11)
[    18.928] (II) No input driver specified, ignoring this device.
[    18.928] (II) This device may have been added with another device file.
[    18.928] (II) config/udev: Adding input device HDA Intel MID HDMI/DP,pcm=8 (/dev/input/event10)
[    18.928] (II) No input driver specified, ignoring this device.
[    18.928] (II) This device may have been added with another device file.
[    18.928] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    18.928] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.928] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    18.928] (**) AT Translated Set 2 keyboard: always reports core events
[    18.928] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    18.928] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    18.928] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    18.928] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    18.928] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    18.928] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    18.928] (**) Option "xkb_rules" "evdev"
[    18.928] (**) Option "xkb_model" "pc105"
[    18.928] (**) Option "xkb_layout" "us"
[    18.929] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event6)
[    18.929] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
[    18.929] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
[    18.929] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "Default clickpad buttons"
[    18.929] (II) LoadModule: "synaptics"
[    18.929] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.929] (II) Module synaptics: vendor="X.Org Foundation"
[    18.929]     compiled for 1.15.0, module version = 1.7.4
[    18.929]     Module class: X.Org XInput Driver
[    18.929]     ABI class: X.Org XInput driver, version 20.0
[    18.929] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS DualPoint TouchPad'
[    18.929] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    18.929] (**) Option "Device" "/dev/input/event6"
[    18.948] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: ignoring touch events for semi-multitouch device
[    18.948] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 2000 (res 0)
[    18.948] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 1400 (res 0)
[    18.948] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
[    18.948] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: device does not report finger width.
[    18.948] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle double triple
[    18.948] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: Vendor 0x2 Product 0x8
[    18.948] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: invalid finger width range.  defaulting to 0 - 15
[    18.948] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    18.948] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    18.980] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    18.980] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD, id 12)
[    18.980] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    18.980] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MaxSpeed is now 1.75
[    18.980] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) AccelFactor is now 0.082
[    18.980] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
[    18.980] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 1
[    18.980] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
[    18.980] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
[    18.980] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    18.980] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse1)
[    18.980] (**) AlpsPS/2 ALPS DualPoint TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    18.980] (II) config/udev: Adding input device DualPoint Stick (/dev/input/event5)
[    18.980] (**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
[    18.980] (**) DualPoint Stick: Applying InputClass "trackpoint catchall"
[    18.980] (II) Using input driver 'evdev' for 'DualPoint Stick'
[    18.980] (**) DualPoint Stick: always reports core events
[    18.980] (**) evdev: DualPoint Stick: Device: "/dev/input/event5"
[    18.981] (--) evdev: DualPoint Stick: Vendor 0x2 Product 0x8
[    18.981] (--) evdev: DualPoint Stick: Found 3 mouse buttons
[    18.981] (--) evdev: DualPoint Stick: Found relative axes
[    18.981] (--) evdev: DualPoint Stick: Found x and y relative axes
[    18.981] (II) evdev: DualPoint Stick: Configuring as mouse
[    18.981] (**) Option "Emulate3Buttons" "true"
[    18.981] (**) Option "EmulateWheel" "true"
[    18.981] (**) Option "EmulateWheelButton" "2"
[    18.981] (**) Option "YAxisMapping" "4 5"
[    18.981] (**) evdev: DualPoint Stick: YAxisMapping: buttons 4 and 5
[    18.981] (**) Option "XAxisMapping" "6 7"
[    18.981] (**) evdev: DualPoint Stick: XAxisMapping: buttons 6 and 7
[    18.981] (**) evdev: DualPoint Stick: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.981] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event5"
[    18.981] (II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE, id 13)
[    18.981] (II) evdev: DualPoint Stick: initialized for relative axes.
[    18.981] (**) DualPoint Stick: (accel) keeping acceleration scheme 1
[    18.981] (**) DualPoint Stick: (accel) acceleration profile 0
[    18.981] (**) DualPoint Stick: (accel) acceleration factor: 2.000
[    18.981] (**) DualPoint Stick: (accel) acceleration threshold: 4
[    18.981] (II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse0)
[    18.981] (II) No input driver specified, ignoring this device.
[    18.981] (II) This device may have been added with another device file.
[    18.982] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event8)
[    18.983] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    18.983] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    18.983] (**) Dell WMI hotkeys: always reports core events
[    18.983] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event8"
[    18.983] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    18.983] (--) evdev: Dell WMI hotkeys: Found keys
[    18.983] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    18.983] (**) Option "config_info" "udev:/sys/devices/virtual/input/input9/event8"
[    18.983] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 14)
[    18.983] (**) Option "xkb_rules" "evdev"
[    18.983] (**) Option "xkb_model" "pc105"
[    18.983] (**) Option "xkb_layout" "us"
[    26.317] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.312] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.325] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.163] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[  1309.588] (II) intel(0): switch to mode 1366x768@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
```

I did a Xorg :1 --configure to get a full xorg.conf, and then I added the modeline few other lines to set the resolution to 1920x1080
```
Section "ServerLayout"    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection


Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "built-ins"
EndSection


Section "Module"
    Load  "glx"
EndSection


Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection


Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection


Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
#    Modeline "1336x768_60.00"   83.00  1336 1400 1536 1736  768 771 781 798 -hsync +vsync


#It didn't like PreferredMode, said so in xorg.0.log
#    Option    "PreferredMode" "1920x1080_60.00"


EndSection


Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "Backlight"              # <str>
        #Option     "DRI"                    # <str>
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "VSync"                  # [<bool>]
        #Option     "PageFlip"               # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "TripleBuffer"           # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "ReprobeOutputs"         # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "VirtualHeads"           # <i>
        #Option     "TearFree"               # [<bool>]
        #Option     "PerCrtcPixmaps"         # [<bool>]
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "BufferCache"            # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection


Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
        Modes    "1920x1080" "1336x768"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
        Modes    "1920x1080" "1336x768"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
        Modes    "1920x1080" "1336x768"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
        Modes    "1920x1080" "1336x768"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes    "1920x1080" "1336x768"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1920x1080" "1336x768"
    EndSubSection
EndSection

```

if I live boot a Ubuntu 12.04 image from USB, the xrandr sequence works properly, and the screen goes to 1920x1080.

If you'd like, I can load it into 12.04 liveusb and copy logs from there if that would help.

Thank you for your help, I have gotten quite frusterated because nearly everything I've found is either people who don't know how to use xrandr, or who have a different hardware problem that is resolved differently.

---

### Post by papibe on 2014-07-30
Hi Lathan_Bidwell. Welcome to the forum ):P

For what I can see, your EDID info is corrupted.
```
00ffffffffffff0030e44b0200000000
00140104952213780262259f5d579b25
19505400000001010101010101010101
010101010101201c569a500016303020
350058c21000001ac012569a50001630
3020350058c21000001a000000fe0047
37573632813135365748320a00000000
00004101160000000009010a20200056

```
That data gives this results:
```
Checksum Correct

Section "Monitor"
	Identifier "&#65533;
                     @"
	ModelName "&#65533;
                    @"
	VendorName "LGD"
	# Monitor Manufactured week 0 of 2010
	# EDID version 1.4
	# Digital Display
	DisplaySize 340 190
	Gamma 2.20
	Option "DPMS" "false"
	Modeline 	"Mode 0" 72.00 1366 1414 1446 1520 768 771 776 790 +hsync -vsync 
	Modeline 	"Mode 1" 48.00 1366 1414 1446 1520 768 771 776 790 +hsync -vsync 
EndSection

```
It would interesting to test if you can get the same EDID using the package 'read-edid'.

As these problems usually affect a set of computers, there are chances that you can get the correct file for your display. I would search either the manufacture forums, or sites like laptopvideo2go (main site  [http://www.laptopvideo2go.com/](http://www.laptopvideo2go.com/) and forums   [http://forums.laptopvideo2go.com/](http://forums.laptopvideo2go.com/)).

Another alternative is, in case you are dual booting, try to get timings and resolutions details from Windows utilities.

Finally you may want to try an upstream version of the Intel driver as described [here]("http://ubuntuforums.org/showthread.php?t=1967201&highlight=nvidia+ppa+xorg").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Lathan_Bidwell on 2014-07-30
```
 sudo get-edid This is read-edid version 3.0.1. Prepare for some fun.
Attempting to use i2c interface
Looks like no busses have an EDID. Sorry!
Attempting to use the classical VBE interface


    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful


    VBE version 300
    VBE string at 0x11100 "Intel(R)Ironlake Mobile Graphics Chipset Accelerated VGA BIOS"


VBE/DDC service about to be called
    Report DDC capabilities


    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful


    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination supports DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer


Reading next EDID block


VBE/DDC service about to be called
    Read EDID


    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call successful


&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0&#65533;K&#65533;"xb%&#65533;]W&#65533;%PT V&#65533;P00 5X&#65533;&#65533;V&#65533;P00 5X&#65533;&#65533;G7W62&#65533;156WH2
A    
  VLooks like VBE was successful. Have a good day.

```

```
sudo get-edid | sudo parse-edid
Section "Monitor"
    Identifier "ª@"
    ModelName "ª@"
    VendorName "LGD"
    # Monitor Manufactured week 0 of 2010
    # EDID version 1.4
    # Digital Display
    DisplaySize 340 190
    Gamma 2.20
    Option "DPMS" "false"
    Modeline     "Mode 0" 72.00 1366 1414 1446 1520 768 771 776 790 +hsync -vsync 
    Modeline     "Mode 1" 48.00 1366 1414 1446 1520 768 771 776 790 +hsync -vsync 
EndSection
```

---

### Post by Lathan_Bidwell on 2014-08-01
Hello,

Thank you for your help identifying this issue.

I just confirmed that 1333x768 is the highest resolution for the LCD, while the dell specs say the graphics card can do 1920x1080 for an external monitor.

I swapped the laptop out with my employeer, so I no longer need to work on this problem.

Please mark this as solved.

Lathan

---


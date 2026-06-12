---
title: "Flash halts/freezes on video websites"
date: 2011-06-13
forum: Multimedia Software
---

### Post by j00z76 on 2011-06-13
Hi,

I have installed Kubuntu Natty on a Toshiba laptop with an Intel Card on i386. Sites with flash video content (youtube, vimeo and the BBC's iplayer site) however don't work as expected: the video track stops while the sound carries on. Pressing the right mouse button in the video player screen makes the video continue immediately, but this is not the expected behaviour! I have also tried with Windows, and it works fine, so it is not a network problem. Audio seems to work fine. I'm attaching the output from lspci and that of Xorg.0.log that appears relevant to the intel driver.


```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
```

```

[    29.175] (II) LoadModule: "intel"
[    29.176] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    29.176] (II) Module intel: vendor="X.Org Foundation"
[    29.176]    compiled for 1.10.1, module version = 2.14.0
[    29.176]    Module class: X.Org Video Driver
[    29.176]    ABI class: X.Org Video Driver, version 10.0
[    29.176] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
        Sandybridge, Sandybridge
[    29.177] (++) using VT number 7

[    29.179] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    29.179] drmOpenDevice: node name is /dev/dri/card0
[    29.179] drmOpenDevice: open result is 9, (OK)
[    29.179] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    29.180] drmOpenDevice: node name is /dev/dri/card0
[    29.180] drmOpenDevice: open result is 9, (OK)
[    29.180] drmOpenByBusid: drmOpenMinor returns 9
[    29.180] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    29.180] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    29.180] (==) intel(0): RGB weight 888
[    29.180] (==) intel(0): Default visual is TrueColor
[    29.180] (II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[    29.180] (--) intel(0): Chipset: "965GM"
[    29.180] (**) intel(0): Relaxed fencing enabled
[    29.180] (**) intel(0): Tiling enabled
[    29.180] (**) intel(0): SwapBuffers wait enabled
[    29.180] (==) intel(0): video overlay key set to 0x101fe
[    29.180] (II) intel(0): Output LVDS1 using monitor section Monitor0
[    29.182] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    29.196] (II) intel(0): Output VGA1 has no monitor section
[    29.196] (II) intel(0): EDID for output LVDS1
[    29.196] (II) intel(0): Manufacturer: APP  Model: 9c5e  Serial#: 0
[    29.196] (II) intel(0): Year: 2006  Week: 9
[    29.196] (II) intel(0): EDID Version: 1.3
[    29.196] (II) intel(0): Digital Display Input
[    29.196] (II) intel(0): Max Image Size [cm]: horiz.: 29  vert.: 19
[    29.196] (II) intel(0): Gamma: 2.20
[    29.196] (II) intel(0): No DPMS capabilities specified
[    29.196] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    29.196] (II) intel(0): First detailed timing is preferred mode
[    29.196] (II) intel(0): redX: 0.622 redY: 0.346   greenX: 0.333 greenY: 0.528
[    29.196] (II) intel(0): blueX: 0.164 blueY: 0.162   whiteX: 0.312 whiteY: 0.329
[    29.196] (II) intel(0): Manufacturer's mask: 0
[    29.196] (II) intel(0): Supported detailed timing:
[    29.196] (II) intel(0): clock: 71.0 MHz   Image Size:  286 x 178 mm
[    29.196] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[    29.196] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[    29.196] (II) intel(0): Unknown vendor-specific block 1
[    29.196] (II) intel(0):  N133I1-L01
[    29.196] (II) intel(0): Monitor name: Color LCD
[    29.196] (II) intel(0): EDID (in hex):
[    29.196] (II) intel(0):     00ffffffffffff0006105e9c00000000
[    29.196] (II) intel(0):     09100103801d13780a65219f5855872a
[    29.196] (II) intel(0):     29505400000001010101010101010101
[    29.196] (II) intel(0):     010101010101bc1b00a0502017303020
[    29.196] (II) intel(0):     36001eb2100000180000000100061020
[    29.196] (II) intel(0):     00000000000000000a20000000fe004e
[    29.196] (II) intel(0):     31333349312d4c30310a2020000000fc
[    29.196] (II) intel(0):     00436f6c6f72204c43440a2020200061
[    29.196] (II) intel(0): EDID vendor "APP", prod id 40030
[    29.196] (II) intel(0): Printing DDC gathered Modelines:
[    29.196] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    29.197] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    29.197] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    29.197] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    29.197] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    29.197] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    29.197] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    29.197] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    29.197] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    29.197] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    29.197] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    29.197] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    29.197] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    29.197] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    29.197] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    29.197] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    29.197] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    29.197] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    29.197] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    29.197] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    29.197] (II) intel(0): Printing probed modes for output LVDS1
[    29.197] (II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    29.197] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    29.197] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    29.197] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    29.197] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    29.212] (II) intel(0): EDID for output VGA1
[    29.212] (II) intel(0): Output LVDS1 connected
[    29.212] (II) intel(0): Output VGA1 disconnected
[    29.212] (II) intel(0): Using exact sizes for initial modes
[    29.212] (II) intel(0): Output LVDS1 using initial mode 1280x800
[    29.212] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    29.212] (II) intel(0): Kernel page flipping support detected, enabling
[    29.212] (**) intel(0): Display dimensions: (290, 190) mm
[    29.212] (**) intel(0): DPI set to (112, 106)
[    29.212] (II) Loading sub module "fb"
[    29.212] (II) LoadModule: "fb"
[    29.212] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.213] (II) Module fb: vendor="X.Org Foundation"
[    29.213]    compiled for 1.10.1, module version = 1.0.0
[    29.213]    ABI class: X.Org ANSI C Emulation, version 0.4
[    29.213] (==) Depth 24 pixmap format is 32 bpp
[    29.213] (==) intel(0): VideoRam: 262144 KB
[    29.213] (II) intel(0): [DRI2] Setup complete
[    29.213] (II) intel(0): [DRI2]   DRI driver: i965
[    29.213] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[    29.229] (II) UXA(0): Driver registered support for the following operations:
[    29.229] (II)         solid
[    29.230] (II)         copy
[    29.230] (II)         composite (RENDER acceleration)
[    29.230] (II)         put_image
[    29.230] (II)         get_image
[    29.230] (==) intel(0): Backing store disabled
[    29.230] (==) intel(0): Silken mouse enabled
[    29.230] (II) intel(0): Initializing HW Cursor
[    29.256] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    29.264] (==) intel(0): DPMS enabled
[    29.264] (==) intel(0): Intel XvMC decoder enabled
[    29.264] (II) intel(0): Set up textured video
[    29.264] (II) intel(0): Set up overlay video
[    29.264] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    29.264] (II) intel(0): direct rendering: DRI2 Enabled
[    29.264] (==) intel(0): hotplug detection: "enabled"

```

---

### Post by lovinglinux on 2011-06-15
Install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and run the extension wizard. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance.

---

### Post by j00z76 on 2011-06-15
> **lovinglinux said:**
> Install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) 

Forgot to mention that I had already done that, but the problem is still there.

---

### Post by lovinglinux on 2011-06-15
> **j00z76 said:**
> Forgot to mention that I had already done that, but the problem is still there.

Sometimes deleting YouTube cookies and the browser cache solve many problems.

Have you tried to disable hardware acceleration in flash settings?

Does your CPU usage reaches 100%?

You might want to try my [FlashVideoReplacer]("http://www.webgapps.org/add-ons/flashvideoreplacer") extension, that allows to watch YouTube, Vimeo and a few other sites with a different plugin like gecko-mediaplayer.

---


---
title: "VGA to LG TV resolution"
date: 2010-12-22
forum: Multimedia Software
---

### Post by eekfonky on 2010-12-22
Is it possible to up the resolution to the TV's full potential of 1080p? It will currently only go as high as 1360 x 768.

I am using a VGA cable form my laptop to the TV

---

### Post by efflandt on 2010-12-23
As long as it is not a low end laptop from awhile ago, you should be able to do 1080p with VGA.  But how you do that depends upon what video card/chip you have and whether you are using default or proprietary drivers for it.  For default drivers you can use xrandr to try different modelines.  I had trouble getting a good modeline from **cvt 1920 1080 60** or **gtf 1920 1080 60** (horizontally squashed).  So for my VGA laptop I used a modeline that I got from Xorg.0.log of my old PC connected to it with DVI to HDMI.  However, when I tried that modeline recently. it seemed like the image was shifted to one side.

I am currently using a newer PC with HDMI cable, but the nvidia drivers don't show the modeline in Xorg.0.log.  I checked Kubuntu Natty development that I have on USB flash using the nouveau driver (or framebuffer) which works fine, but that was not very enlightening, it just says: Built-in mode "current"

This looks promising (more at [http://www.mythtv.org/wiki/Modeline_Database](http://www.mythtv.org/wiki/Modeline_Database) )
```
ModeLine "ATSC-1080-60p" 148.5 1920 1960 2016 2200 1080 1082 1088 1125

ModeLine  "1920x1080" 138.500 1920 1968 2000 2080 1080 1083 1088 1111 +hsync -vsync

ModeLine "1920x1080" 148.35 1920 2008 2052 2200 1080 1084 1089 1125 +HSync +VSync

ModeLine "ATSC-1080-59.94p" 148.352 1920 1960 2016 2200 1080 1082 1088 1125

ModeLine "ATSC-1080-60p" 148.5 1920 1960 2016 2200 1080 1082 1088 1125
```Although, if you are in Europe you might be looking for something 50 Hz.  Note that I have one old low end laptop from about 5 years ago, and its video was limited to 1360x1360, so 1360x768 was the best it could do.  My other laptop from 2006 can do up to 4096x4096 (not really both at same time) so it has no problem doing 1080p.

See: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by tgalati4 on 2010-12-23
VGA tends to top out at 1600x1200 due to bandwidth issues and the analog nature of the signals.  To get stable, higher resolutions (like 1920x1080) you need a DVI connection.

---

### Post by eekfonky on 2010-12-31
I need a simple solution, last time I messed with modelines bad things happened and it wasn't recoverable by the likes of me as I only have 1 computer so no way to post or read solutions. I just thought that the VGA cable would go as high res as possible 1360x768 seems a little poor

---

### Post by realzippy on 2010-12-31
...more infos?
graphics card/driver/ubuntu version ?
/var/log/Xorg.0.log ?

---

### Post by eekfonky on 2010-12-31
How do I post that info? which commands in a terminal?

---

### Post by realzippy on 2010-12-31
```
lspci | grep VGA
```

```
cat /var/log/Xorg.0.log
```
or
```
gedit /var/log/Xorg.0.log 
```

---

### Post by eekfonky on 2011-01-01
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```

[    14.037] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    14.037] X Protocol Version 11, Revision 0
[    14.037] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    14.037] Current Operating System: Linux Oor-laptop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64
[    14.037] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=b5cc4339-3b20-4d65-963c-04a7c2d9426a ro quiet splash
[    14.037] Build Date: 16 September 2010  06:18:41PM
[    14.037] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    14.037] Current version of pixman: 0.18.4
[    14.037] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    14.037] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.038] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan  1 18:46:03 2011
[    14.103] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.130] (==) No Layout section.  Using the first Screen section.
[    14.130] (==) No screen section available. Using defaults.
[    14.130] (**) |-->Screen "Default Screen Section" (0)
[    14.130] (**) |   |-->Monitor "<default monitor>"
[    14.131] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    14.131] (==) Automatically adding devices
[    14.131] (==) Automatically enabling devices
[    14.131] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.131] 	Entry deleted from font path.
[    14.131] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    14.131] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.131] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.131] (II) Loader magic: 0x7d0200
[    14.131] (II) Module ABI versions:
[    14.131] 	X.Org ANSI C Emulation: 0.4
[    14.131] 	X.Org Video Driver: 8.0
[    14.131] 	X.Org XInput driver : 11.0
[    14.131] 	X.Org Server Extension : 4.0
[    14.133] (--) PCI:*(0:0:2:0) 8086:2a02:1179:ff01 rev 12, Mem @ 0xf4000000/1048576, 0xd0000000/268435456, I/O @ 0x00001800/8
[    14.133] (--) PCI: (0:0:2:1) 8086:2a03:1179:ff01 rev 12, Mem @ 0xf4100000/1048576
[    14.133] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.133] (II) LoadModule: "extmod"
[    14.207] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.208] (II) Module extmod: vendor="X.Org Foundation"
[    14.208] 	compiled for 1.9.0, module version = 1.0.0
[    14.208] 	Module class: X.Org Server Extension
[    14.208] 	ABI class: X.Org Server Extension, version 4.0
[    14.208] (II) Loading extension MIT-SCREEN-SAVER
[    14.208] (II) Loading extension XFree86-VidModeExtension
[    14.208] (II) Loading extension XFree86-DGA
[    14.208] (II) Loading extension DPMS
[    14.208] (II) Loading extension XVideo
[    14.208] (II) Loading extension XVideo-MotionCompensation
[    14.208] (II) Loading extension X-Resource
[    14.208] (II) LoadModule: "dbe"
[    14.208] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.208] (II) Module dbe: vendor="X.Org Foundation"
[    14.208] 	compiled for 1.9.0, module version = 1.0.0
[    14.208] 	Module class: X.Org Server Extension
[    14.208] 	ABI class: X.Org Server Extension, version 4.0
[    14.208] (II) Loading extension DOUBLE-BUFFER
[    14.208] (II) LoadModule: "glx"
[    14.208] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.208] (II) Module glx: vendor="X.Org Foundation"
[    14.208] 	compiled for 1.9.0, module version = 1.0.0
[    14.208] 	ABI class: X.Org Server Extension, version 4.0
[    14.208] (==) AIGLX enabled
[    14.208] (II) Loading extension GLX
[    14.209] (II) LoadModule: "record"
[    14.209] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.209] (II) Module record: vendor="X.Org Foundation"
[    14.209] 	compiled for 1.9.0, module version = 1.13.0
[    14.209] 	Module class: X.Org Server Extension
[    14.209] 	ABI class: X.Org Server Extension, version 4.0
[    14.209] (II) Loading extension RECORD
[    14.209] (II) LoadModule: "dri"
[    14.209] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.209] (II) Module dri: vendor="X.Org Foundation"
[    14.209] 	compiled for 1.9.0, module version = 1.0.0
[    14.209] 	ABI class: X.Org Server Extension, version 4.0
[    14.209] (II) Loading extension XFree86-DRI
[    14.209] (II) LoadModule: "dri2"
[    14.210] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.210] (II) Module dri2: vendor="X.Org Foundation"
[    14.210] 	compiled for 1.9.0, module version = 1.2.0
[    14.210] 	ABI class: X.Org Server Extension, version 4.0
[    14.210] (II) Loading extension DRI2
[    14.210] (==) Matched intel as autoconfigured driver 0
[    14.210] (==) Matched vesa as autoconfigured driver 1
[    14.210] (==) Matched fbdev as autoconfigured driver 2
[    14.210] (==) Assigned the driver to the xf86ConfigLayout
[    14.210] (II) LoadModule: "intel"
[    14.303] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    14.305] (II) Module intel: vendor="X.Org Foundation"
[    14.305] 	compiled for 1.9.0, module version = 2.12.0
[    14.305] 	Module class: X.Org Video Driver
[    14.305] 	ABI class: X.Org Video Driver, version 8.0
[    14.305] (II) LoadModule: "vesa"
[    14.305] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.305] (II) Module vesa: vendor="X.Org Foundation"
[    14.305] 	compiled for 1.8.99.905, module version = 2.3.0
[    14.305] 	Module class: X.Org Video Driver
[    14.306] 	ABI class: X.Org Video Driver, version 8.0
[    14.306] (II) LoadModule: "fbdev"
[    14.306] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.306] (II) Module fbdev: vendor="X.Org Foundation"
[    14.306] 	compiled for 1.8.99.905, module version = 0.4.2
[    14.306] 	ABI class: X.Org Video Driver, version 8.0
[    14.306] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    14.307] (II) VESA: driver for VESA chipsets: vesa
[    14.307] (II) FBDEV: driver for framebuffer: fbdev
[    14.307] (++) using VT number 7

[    14.307] (WW) Falling back to old probe method for vesa
[    14.307] (WW) Falling back to old probe method for fbdev
[    14.307] (II) Loading sub module "fbdevhw"
[    14.307] (II) LoadModule: "fbdevhw"
[    14.307] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.307] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.307] 	compiled for 1.9.0, module version = 0.0.2
[    14.307] 	ABI class: X.Org Video Driver, version 8.0
[    14.310] drmOpenDevice: node name is /dev/dri/card0
[    14.310] drmOpenDevice: open result is 9, (OK)
[    14.310] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    14.310] drmOpenDevice: node name is /dev/dri/card0
[    14.310] drmOpenDevice: open result is 9, (OK)
[    14.310] drmOpenByBusid: drmOpenMinor returns 9
[    14.310] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    14.310] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    14.310] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    14.310] (==) intel(0): RGB weight 888
[    14.310] (==) intel(0): Default visual is TrueColor
[    14.310] (II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[    14.310] (--) intel(0): Chipset: "965GM"
[    14.310] (==) intel(0): video overlay key set to 0x101fe
[    14.337] (II) intel(0): Output VGA1 has no monitor section
[    14.337] (II) intel(0): Output LVDS1 has no monitor section
[    14.337] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    14.339] (II) intel(0): Output TV1 has no monitor section
[    14.357] (II) intel(0): EDID for output VGA1
[    14.357] (II) intel(0): Not using default mode "640x350" (vrefresh out of range)
[    14.357] (II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "640x400" (vrefresh out of range)
[    14.357] (II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "720x400" (vrefresh out of range)
[    14.357] (II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    14.357] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    14.357] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    14.357] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    14.357] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    14.357] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    14.357] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "1024x768i" (interlace mode not supported)
[    14.357] (II) intel(0): Not using default mode "512x384i" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    14.357] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    14.357] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    14.357] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    14.357] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "1280x960" (hsync out of range)
[    14.357] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
[    14.357] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "1280x1024" (hsync out of range)
[    14.357] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
[    14.357] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
[    14.357] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    14.357] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    14.357] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    14.357] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1792x1344" (hsync out of range)
[    14.358] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1856x1392" (hsync out of range)
[    14.358] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1920x1440" (hsync out of range)
[    14.358] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "832x624" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1152x864" (hsync out of range)
[    14.358] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    14.358] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[    14.358] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1440x900" (hsync out of range)
[    14.358] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1600x1024" (hsync out of range)
[    14.358] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    14.358] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    14.358] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1920x1080" (hsync out of range)
[    14.358] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1920x1200" (hsync out of range)
[    14.358] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "2048x1536" (hsync out of range)
[    14.358] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    14.358] (II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
[    14.358] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    14.359] (II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
[    14.359] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    14.359] (II) intel(0): Printing probed modes for output VGA1
[    14.359] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    14.359] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.359] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.359] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    14.359] (II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    14.359] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    14.359] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.359] (II) intel(0): EDID for output LVDS1
[    14.359] (II) intel(0): Manufacturer: SEC  Model: 3847  Serial#: 0
[    14.359] (II) intel(0): Year: 2006  Week: 0
[    14.359] (II) intel(0): EDID Version: 1.3
[    14.359] (II) intel(0): Digital Display Input
[    14.359] (II) intel(0): Max Image Size [cm]: horiz.: 37  vert.: 23
[    14.359] (II) intel(0): Gamma: 2.20
[    14.359] (II) intel(0): No DPMS capabilities specified
[    14.359] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    14.359] (II) intel(0): First detailed timing is preferred mode
[    14.359] (II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[    14.359] (II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[    14.359] (II) intel(0): Manufacturer's mask: 0
[    14.359] (II) intel(0): Supported detailed timing:
[    14.359] (II) intel(0): clock: 96.3 MHz   Image Size:  367 x 230 mm
[    14.359] (II) intel(0): h_active: 1440  h_sync: 1504  h_sync_end 1536 h_blank_end 1760 h_border: 0
[    14.359] (II) intel(0): v_active: 900  v_sync: 903  v_sync_end 906 v_blanking: 912 v_border: 0
[    14.359] (II) intel(0): Unknown vendor-specific block f
[    14.359] (II) intel(0):  SAMSUNG
[    14.359] (II) intel(0):  LTN170X2-L02
[    14.359] (II) intel(0): EDID (in hex):
[    14.359] (II) intel(0): 	00ffffffffffff004ca3473800000000
[    14.359] (II) intel(0): 	00100103802517780a87f594574f8c27
[    14.359] (II) intel(0): 	27505400000001010101010101010101
[    14.359] (II) intel(0): 	0101010101019f25a04051840c304020
[    14.359] (II) intel(0): 	33006fe6100000190000000f00000000
[    14.359] (II) intel(0): 	000000000078e6022300000000fe0053
[    14.359] (II) intel(0): 	414d53554e470a2020202020000000fe
[    14.359] (II) intel(0): 	004c544e31373058322d4c30320a00f1
[    14.359] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    14.359] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    14.359] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    14.359] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    14.360] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    14.360] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    14.360] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    14.360] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    14.360] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    14.360] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    14.360] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    14.360] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    14.360] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    14.360] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    14.360] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    14.360] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    14.360] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    14.360] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    14.360] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    14.360] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    14.360] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    14.360] (II) intel(0): Printing probed modes for output LVDS1
[    14.360] (II) intel(0): Modeline "1440x900"x60.0   96.31  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
[    14.360] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    14.360] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    14.360] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    14.360] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    14.360] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.360] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.360] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    14.360] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.360] (II) intel(0): EDID for output TV1
[    14.360] (II) intel(0): Output VGA1 connected
[    14.360] (II) intel(0): Output LVDS1 connected
[    14.360] (II) intel(0): Output TV1 disconnected
[    14.360] (II) intel(0): Using fuzzy aspect match for initial modes
[    14.360] (II) intel(0): Output VGA1 using initial mode 1024x768
[    14.360] (II) intel(0): Output LVDS1 using initial mode 1024x768
[    14.360] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    14.360] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    14.360] (==) intel(0): DPI set to (96, 96)
[    14.360] (II) Loading sub module "fb"
[    14.360] (II) LoadModule: "fb"
[    14.360] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.361] (II) Module fb: vendor="X.Org Foundation"
[    14.361] 	compiled for 1.9.0, module version = 1.0.0
[    14.361] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.361] (II) UnloadModule: "vesa"
[    14.361] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.361] (II) UnloadModule: "fbdev"
[    14.361] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.361] (II) UnloadModule: "fbdevhw"
[    14.361] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    14.361] (==) Depth 24 pixmap format is 32 bpp
[    14.361] (II) intel(0): [DRI2] Setup complete
[    14.361] (II) intel(0): [DRI2]   DRI driver: i965
[    14.361] (**) intel(0): Tiling enabled
[    14.361] (**) intel(0): SwapBuffers wait enabled
[    14.361] (==) intel(0): VideoRam: 262144 KB
[    14.361] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    14.375] (II) UXA(0): Driver registered support for the following operations:
[    14.375] (II)         solid
[    14.375] (II)         copy
[    14.375] (II)         composite (RENDER acceleration)
[    14.375] (II)         put_image
[    14.375] (II)         get_image
[    14.375] (==) intel(0): Backing store disabled
[    14.375] (==) intel(0): Silken mouse enabled
[    14.375] (II) intel(0): Initializing HW Cursor
[    15.065] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    15.072] (==) intel(0): DPMS enabled
[    15.072] (==) intel(0): Intel XvMC decoder enabled
[    15.072] (II) intel(0): Set up textured video
[    15.072] (II) intel(0): Set up overlay video
[    15.072] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    15.072] (II) intel(0): direct rendering: DRI2 Enabled
[    15.072] (--) RandR disabled
[    15.072] (II) Initializing built-in extension Generic Event Extension
[    15.072] (II) Initializing built-in extension SHAPE
[    15.072] (II) Initializing built-in extension MIT-SHM
[    15.072] (II) Initializing built-in extension XInputExtension
[    15.072] (II) Initializing built-in extension XTEST
[    15.072] (II) Initializing built-in extension BIG-REQUESTS
[    15.072] (II) Initializing built-in extension SYNC
[    15.072] (II) Initializing built-in extension XKEYBOARD
[    15.072] (II) Initializing built-in extension XC-MISC
[    15.072] (II) Initializing built-in extension SECURITY
[    15.072] (II) Initializing built-in extension XINERAMA
[    15.072] (II) Initializing built-in extension XFIXES
[    15.072] (II) Initializing built-in extension RENDER
[    15.072] (II) Initializing built-in extension RANDR
[    15.072] (II) Initializing built-in extension COMPOSITE
[    15.072] (II) Initializing built-in extension DAMAGE
[    15.072] (II) Initializing built-in extension GESTURE
[    15.083] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    15.083] (II) AIGLX: enabled GLX_INTEL_swap_event
[    15.083] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    15.083] (II) AIGLX: enabled GLX_SGI_make_current_read
[    15.083] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    15.083] (II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
[    15.083] (II) GLX: Initialized DRI2 GL provider for screen 0
[    15.084] (II) intel(0): Setting screen physical size to 270 x 203
[    15.106] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.117] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    15.117] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.117] (II) LoadModule: "evdev"
[    15.117] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.117] (II) Module evdev: vendor="X.Org Foundation"
[    15.118] 	compiled for 1.9.0, module version = 2.3.2
[    15.118] 	Module class: X.Org XInput Driver
[    15.118] 	ABI class: X.Org XInput driver, version 11.0
[    15.118] (**) Power Button: always reports core events
[    15.118] (**) Power Button: Device: "/dev/input/event2"
[    15.140] (II) Power Button: Found keys
[    15.140] (II) Power Button: Configuring as keyboard
[    15.140] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    15.140] (**) Option "xkb_rules" "evdev"
[    15.140] (**) Option "xkb_model" "evdev"
[    15.140] (**) Option "xkb_layout" "us"
[    15.142] (II) XKB: reuse xkmfile /var/lib/xkb/server-D378AD8F86E560F712A83EE36E4E5E92C595B9BD.xkm
[    15.143] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    15.143] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    15.143] (**) Video Bus: always reports core events
[    15.143] (**) Video Bus: Device: "/dev/input/event5"
[    15.172] (II) Video Bus: Found keys
[    15.172] (II) Video Bus: Configuring as keyboard
[    15.172] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    15.172] (**) Option "xkb_rules" "evdev"
[    15.172] (**) Option "xkb_model" "evdev"
[    15.172] (**) Option "xkb_layout" "us"
[    15.175] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    15.175] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.175] (**) Power Button: always reports core events
[    15.175] (**) Power Button: Device: "/dev/input/event1"
[    15.202] (II) Power Button: Found keys
[    15.202] (II) Power Button: Configuring as keyboard
[    15.202] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    15.202] (**) Option "xkb_rules" "evdev"
[    15.202] (**) Option "xkb_model" "evdev"
[    15.202] (**) Option "xkb_layout" "us"
[    15.203] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    15.203] (II) No input driver/identifier specified (ignoring)
[    15.204] (II) config/udev: Adding input device Chicony USB 2.0 Camera (/dev/input/event4)
[    15.204] (**) Chicony USB 2.0 Camera: Applying InputClass "evdev keyboard catchall"
[    15.204] (**) Chicony USB 2.0 Camera: always reports core events
[    15.204] (**) Chicony USB 2.0 Camera: Device: "/dev/input/event4"
[    15.242] (II) Chicony USB 2.0 Camera: Found keys
[    15.242] (II) Chicony USB 2.0 Camera: Configuring as keyboard
[    15.242] (II) XINPUT: Adding extended input device "Chicony USB 2.0 Camera" (type: KEYBOARD)
[    15.242] (**) Option "xkb_rules" "evdev"
[    15.242] (**) Option "xkb_model" "evdev"
[    15.242] (**) Option "xkb_layout" "us"
[    15.248] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    15.248] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    15.248] (**) AT Translated Set 2 keyboard: always reports core events
[    15.248] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    15.282] (II) AT Translated Set 2 keyboard: Found keys
[    15.282] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    15.282] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    15.282] (**) Option "xkb_rules" "evdev"
[    15.282] (**) Option "xkb_model" "evdev"
[    15.282] (**) Option "xkb_layout" "us"
[    15.283] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    15.283] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    15.283] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    15.283] (II) LoadModule: "synaptics"
[    15.283] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    15.283] (II) Module synaptics: vendor="X.Org Foundation"
[    15.283] 	compiled for 1.9.0, module version = 1.2.2
[    15.284] 	Module class: X.Org XInput Driver
[    15.284] 	ABI class: X.Org XInput driver, version 11.0
[    15.284] (II) Synaptics touchpad driver version 1.2.2
[    15.284] (**) Option "Device" "/dev/input/event6"
[    15.380] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    15.380] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    15.380] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    15.380] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    15.380] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[    15.480] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    15.480] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    15.520] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    15.520] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    15.520] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    15.520] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    15.520] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    15.600] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    15.600] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    15.600] (II) No input driver/identifier specified (ignoring)
[    34.456] (II) intel(0): Allocated new frame buffer 2816x900 stride 11264, tiled
```

---


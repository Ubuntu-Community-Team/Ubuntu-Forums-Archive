---
title: "Where is my xorg.conf file?"
date: 2010-09-25
forum: Multimedia Software
---

### Post by david_215 on 2010-09-25
I recently built a mythbuntu system on the VIA EPIA LN10000-series motherboard.  The mobo has on-board TV out (composite and s-video), but while I can get the bios screen to display ok via composite video (nothing at all s-video), the video fails once mythbuntu fully boots up.  Googling around the openChrome site has led me to the idea of editing my xorg.conf file, however it is not to be found!  Is this intentional in the mythbuntu distro, or is something amiss?

Many thanks.

---

### Post by mikewhatever on 2010-09-25
There is no xorg.conf by default in Ubuntu, but, you can generate one with **Xorg -configure** .

---

### Post by david_215 on 2010-09-25
OK, Xorg -configure didn't work for me, but I can easily gedit a new xorg.conf.

Here's my new question: since TV out works perfectly through the bios phase of the boot up (bios splash screen displayed on both my monitor and TV), how can I easily transfer these bios parameters to mythbuntu 10.04?

Sorry to beg for step-by-step instructions, but in my wife's eyes I have already spent way too much time on this Myth TV project!

---

### Post by Yellow Pasque on 2010-09-25
Possibly useful info that you can provide:
```
/var/log/Xorg.0.log
xrandr -q
```

---

### Post by david_215 on 2010-09-25
Here's the output from /var/log/Xorg.0.log

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux david-desktop 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=f65f9970-b75b-42ae-a599-0a8c842deccf ro quiet splash
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep 25 19:10:38 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI: (0:0:20:0) 14f1:5b7a:0070:7444 Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder rev 0, Mem @ 0xf0000000/67108864
(--) PCI:*(0:1:0:0) 1106:3344:1106:3344 VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] rev 1, Mem @ 0xf4000000/67108864, 0xfb000000/16777216, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
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
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched openchrome as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "openchrome"
(II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
(II) Module openchrome: vendor="http://openchrome.org/"
	compiled for 1.7.5, module version = 0.2.904
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
	K8M800/K8N800, PM800/PM880/CN400, VM800/P4M800Pro/VN800/CN700,
	K8M890/K8N890, P4M900/VN896/CN896, CX700/VX700, P4M890, VX800/VX820,
	VX855/VX875
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(!!) VIA Technologies does not support this driver in any way.
(!!) For support, please refer to [http://www.openchrome.org/](http://www.openchrome.org/).
(!!) (development build, compiled on Mon Mar 22 20:33:42 2010)
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) CHROME(0): VIAPreInit
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) CHROME(0): VIAGetRec
(II) CHROME(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) CHROME(0): Depth 24, (--) framebuffer bpp 32
(==) CHROME(0): RGB weight 888
(==) CHROME(0): Default visual is TrueColor
(--) CHROME(0): Chipset: VM800/P4M800Pro/VN800/CN700
(--) CHROME(0): Chipset revision: 0
(--) CHROME(0): Probed amount of VideoRAM = 65536 kB
(II) CHROME(0): Setting up default chipset options.
(II) CHROME(0): VIASetupDefaultOptions
(II) CHROME(0): Reading config file...
(II) CHROME(0): Starting to parse config file options...
(==) CHROME(0): Shadow framebuffer is disabled.
(==) CHROME(0): Hardware acceleration is enabled.
(==) CHROME(0): Using XAA acceleration architecture.
(==) CHROME(0): Using hardware two-color cursors and software full-color cursors.
(==) CHROME(0): GPU virtual command queue will be enabled.
(==) CHROME(0): DRI IRQ will be enabled if DRI is enabled.
(==) CHROME(0): AGP DMA will be enabled if DRI is enabled.
(==) CHROME(0): AGP DMA will be used for 2D acceleration.
(==) CHROME(0): PCI DMA will be used for XV image transfer if DRI is enabled.
(==) CHROME(0): Will not enable VBE modes.
(==) CHROME(0): VBE VGA register save & restore will not be used
	if VBE modes are enabled.
(==) CHROME(0): Xv Bandwidth check is enabled.
(==) CHROME(0): Will not impose a limit on video RAM reserved for DRI.
(==) CHROME(0): Will try to allocate 32768 kB of AGP memory.
(==) CHROME(0): Digital output bus width is 12 bits.
(==) CHROME(0): DVI Center is disabled.
(==) CHROME(0): Panel size is not selected from config file.
(==) CHROME(0): Panel will not be forced.
(==) CHROME(0): TV dotCrawl is disabled.
(==) CHROME(0): TV deflicker is set to 0.
(==) CHROME(0): No default TV type is set.
(==) CHROME(0): No default TV output signal type is set.
(==) CHROME(0): No default TV output port is set.
(II) CHROME(0): VIAMapMMIO
(--) CHROME(0): mapping MMIO @ 0xfb000000 with size 0x9000
(--) CHROME(0): mapping BitBlt MMIO @ 0xfb200000 with size 0x200000
(II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) CHROME(0): Will not print VGA registers.
(==) CHROME(0): Will not scan I2C buses.
(II) CHROME(0): ...Finished parsing config file options.
(WW) CHROME(0): Manufacturer plainly copied main PCI IDs to subsystem/card IDs.
(--) CHROME(0): Detected VIA VT3344 (VM800) - EPIA EN. Card-Ids (1106|3344)
(II) CHROME(0): Detected MemClk 7
(II) CHROME(0): ViaGetMemoryBandwidth. Memory type: 7
(II) CHROME(0): Detected TV standard: NTSC.
(==) CHROME(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) CHROME(0): ViaI2CInit
(II) CHROME(0): ViaI2CBus1Init
(II) CHROME(0): I2C bus "I2C bus 1" initialized.
(II) CHROME(0): ViaI2cBus2Init
(II) CHROME(0): I2C bus "I2C bus 2" initialized.
(II) CHROME(0): ViaI2CBus3Init
(II) CHROME(0): I2C bus "I2C bus 3" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) CHROME(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
(II) CHROME(0): ViaOutputsDetect
(II) CHROME(0): VIATVDetect
(II) CHROME(0): ViaVT162xDetect
(II) CHROME(0): I2C device "I2C bus 2:VT162x" registered at address 0x40.
(--) CHROME(0): Detected VIA Technologies VT1622A/VT1623 TV Encoder
(II) CHROME(0): ViaTVInit
(II) CHROME(0): ViaVT162xInit
(II) CHROME(0): VT162xSave
(II) CHROME(0): VT1622DACSense
(--) CHROME(0): VT162x: Nothing connected.
(II) CHROME(0): ViaOutputsSelect
(II) CHROME(0): ViaOutputsSelect: X Configuration: 0x00
(II) CHROME(0): ViaOutputsSelect: BIOS Initialised register: 0x00
(II) CHROME(0): ViaOutputsSelect: CRT.
(II) CHROME(0): ViaModesAttach
(II) CHROME(0): <default monitor>: Using default hsync range of 31.50-37.90 kHz
(II) CHROME(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
(WW) CHROME(0): Unable to estimate virtual size
(II) CHROME(0): Clock range:  20.00 to 230.00 MHz
(II) CHROME(0): ViaValidMode: Validating 640x350 (Clock: 31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "640x350" (vrefresh out of range)
(II) CHROME(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x400 (Clock: 31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "640x400" (vrefresh out of range)
(II) CHROME(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 720x400 (Clock: 35500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "720x400" (vrefresh out of range)
(II) CHROME(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 25175)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "640x480" (vrefresh out of range)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "640x480" (vrefresh out of range)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "640x480" (hsync out of range)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 40000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 50000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "800x600" (hsync out of range)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 49500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "800x600" (hsync out of range)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 56300)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "800x600" (hsync out of range)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 44900)
(II) CHROME(0): Not using default mode "1024x768" (interlace mode not supported)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 65000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 75000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 78750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 94500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (Clock: 108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1280x960" (hsync out of range)
(II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (Clock: 148500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1280x960" (hsync out of range)
(II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1280x1024" (hsync out of range)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 135000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1280x1024" (hsync out of range)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 157500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1280x1024" (hsync out of range)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 162000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 175500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 189000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 202500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 229500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1792x1344 (Clock: 204800)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1792x1344" (hsync out of range)
(II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1856x1392 (Clock: 218300)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1856x1392" (hsync out of range)
(II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 832x624 (Clock: 57284)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "832x624" (hsync out of range)
(II) CHROME(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 81620)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 96770)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 104990)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 119650)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 121500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 143470)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1360x768 (Clock: 72000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1360x768" (hsync out of range)
(II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1360x768 (Clock: 84750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1360x768" (hsync out of range)
(II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (Clock: 122000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1400x1050" (hsync out of range)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (Clock: 145060)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1400x1050" (hsync out of range)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (Clock: 155800)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1400x1050" (horizontal sync too wide)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (Clock: 179260)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1400x1050" (hsync out of range)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1440x900 (Clock: 106500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1440x900" (hsync out of range)
(II) CHROME(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1024 (Clock: 103125)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1600x1024" (hsync out of range)
(II) CHROME(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 119000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 146250)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 174000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 187000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 214750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1920x1080 (Clock: 138500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1920x1080" (hsync out of range)
(II) CHROME(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1920x1200 (Clock: 154000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1920x1200" (hsync out of range)
(II) CHROME(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 40000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 25175)
(II) CHROME(0): ViaFirstCRTCModeValid
(--) CHROME(0): Virtual size is 800x600 (pitch 800)
(**) CHROME(0): *Default mode "800x600": 40.0 MHz (scaled from 0.9 MHz), 37.9 kHz, 60.3 Hz
(II) CHROME(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) CHROME(0): *Default mode "800x600": 36.0 MHz (scaled from 0.8 MHz), 35.2 kHz, 56.2 Hz
(II) CHROME(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) CHROME(0): *Default mode "640x480": 25.2 MHz (scaled from 0.5 MHz), 31.5 kHz, 59.9 Hz
(II) CHROME(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(==) CHROME(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.1
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) CHROME(0): VIAUnmapMem
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) CHROME(0): VIAScreenInit
(II) CHROME(0): VIAMapFB
(--) CHROME(0): mapping framebuffer @ 0xf4000000 with size 0x4000000
(--) CHROME(0): Frame buffer start: 0xb371a000, free start: 0x1d4c00 end: 0x4000000
(II) CHROME(0): VIAMapMMIO
(--) CHROME(0): mapping MMIO @ 0xfb000000 with size 0x9000
(--) CHROME(0): mapping BitBlt MMIO @ 0xfb200000 with size 0x200000
(II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) CHROME(0): VIASave
(II) CHROME(0): Primary
(II) CHROME(0): Primary Adapter! saving VGA_SR_ALL !!
(II) CHROME(0): Non-Primary Adapter! saving VGA_SR_MODE only !!
(II) CHROME(0): Crtc...
(II) CHROME(0): TVSave...
(II) CHROME(0): VT162xSave
(II) CHROME(0): VIAWriteMode
(II) CHROME(0): ViaModeSet
(II) CHROME(0): Name: 800x600
(II) CHROME(0): Clock: 40000
(II) CHROME(0): VRefresh: 60.316540
(II) CHROME(0): HSync: 37.878788
(II) CHROME(0): HDisplay: 800
(II) CHROME(0): HSyncStart: 840
(II) CHROME(0): HSyncEnd: 968
(II) CHROME(0): HTotal: 1056
(II) CHROME(0): HSkew: 0
(II) CHROME(0): VDisplay: 600
(II) CHROME(0): VSyncStart: 601
(II) CHROME(0): VSyncEnd: 605
(II) CHROME(0): VTotal: 628
(II) CHROME(0): VScan: 0
(II) CHROME(0): Flags: 5
(II) CHROME(0): CrtcHDisplay: 0x320
(II) CHROME(0): CrtcHBlankStart: 0x320
(II) CHROME(0): CrtcHSyncStart: 0x348
(II) CHROME(0): CrtcHSyncEnd: 0x3c8
(II) CHROME(0): CrtcHBlankEnd: 0x420
(II) CHROME(0): CrtcHTotal: 0x420
(II) CHROME(0): CrtcHSkew: 0x0
(II) CHROME(0): CrtcVDisplay: 0x258
(II) CHROME(0): CrtcVBlankStart: 0x258
(II) CHROME(0): CrtcVSyncStart: 0x259
(II) CHROME(0): CrtcVSyncEnd: 0x25d
(II) CHROME(0): CrtcVBlankEnd: 0x274
(II) CHROME(0): CrtcVTotal: 0x274
(II) CHROME(0): ViaDisplaySetStreamOnCRT
(II) CHROME(0): ViaDisplayEnableCRT
(II) CHROME(0): ViaModeFirstCRTC
(II) CHROME(0): ViaFirstCRTCSetMode
(II) CHROME(0): Setting up 800x600
(II) CHROME(0): ViaSetPrimaryFIFO
(II) CHROME(0): ViaSetDotclock to 0x0860cd
(II) CHROME(0): ViaSetUseExternalClock
(II) CHROME(0): ViaDisplayDisableSimultaneous
(II) CHROME(0): VIAAdjustFrame 0x0
(II) CHROME(0): VIAAdjustFrame 0x0
(II) CHROME(0): - Blanked
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] loaded kernel module for "via" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) CHROME(0): [drm] Using the DRM lock SAREA also for drawables.
(II) CHROME(0): [drm] framebuffer handle = 0xf4000000
(II) CHROME(0): [drm] added 1 reserved context for kernel
(II) CHROME(0): X context handle = 0x1
(II) CHROME(0): [drm] installed DRM signal handler
(II) CHROME(0): [dri] visual configs initialized.
(II) CHROME(0): [drm] register handle = 0xfb000000
(II) CHROME(0): [drm] framebuffer handle = 0xf4000000
(II) CHROME(0): [drm] mmio Registers = 0xfb000000
(II) CHROME(0): [dri] mmio mapped.
(II) CHROME(0): - Visuals set up
(II) CHROME(0): VIAInternalScreenInit
(II) CHROME(0): - B & W
(II) CHROME(0): CursorStart: 0x3fc0000
(II) CHROME(0): Frame Buffer From (0,0) To (800,2400)
(II) CHROME(0): Using 1800 lines for offscreen memory.
(II) CHROME(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	8x8 color pattern filled rectangles
	Solid Lines
	Dashed Lines
	Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		13 256x256 slots
		32 8x8 color pattern slots
(==) CHROME(0): Backing store disabled
(II) CHROME(0): - Backing store set up
(II) CHROME(0): - SW cursor set up
(II) CHROME(0): VIAHWCursorInit
(II) CHROME(0): - Def Color map set up
(II) CHROME(0): VIALoadPalette: numColors: 256
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): - Palette loaded
(==) CHROME(0): DPMS enabled
(II) CHROME(0): - DPMS set up
(II) CHROME(0): - Color maps etc. set up
(II) CHROME(0): [drm] Detected AGP vendor 0x1106, device 0x0314
(II) CHROME(0): [drm] Found AGP v3 compatible device. Trying AGP 8X mode.
(II) CHROME(0): [drm] Trying to enable AGP fast writes.
(II) CHROME(0): [drm] drmAgpEnabled succeeded
(II) CHROME(0): [drm] agpAddr = 0xe8000000
(II) CHROME(0): [drm] agpBase = (nil)
(II) CHROME(0): [drm] agpAddr = 0xe8000000
(II) CHROME(0): [drm] agpSize = 0x01e00000
(II) CHROME(0): [drm] agp physical addr = 0x00000000
(II) CHROME(0): [dri] Using AGP.
(II) CHROME(0): [drm] Using 59160288 bytes for DRM memory heap.
(II) CHROME(0): [dri] Frame buffer initialized.
(II) CHROME(0): [DRI] installation complete
(II) CHROME(0): [dri] Kernel data initialized.
(II) CHROME(0): [drm] IRQ handler installed, using IRQ 16.
(II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
(II) CHROME(0): direct rendering enabled
(II) CHROME(0): [Xv] Using PCI DMA for Xv image transfer.
Fulfilled via DRI at 7683200
(II) CHROME(0): Benchmarking video copy.  Less time is better.
(--) CHROME(0): Timed   libc YUV420 copy... 1778232. Throughput: 332.8 MiB/s.
(--) CHROME(0): Timed kernel YUV420 copy... 1695540. Throughput: 349.0 MiB/s.
(--) CHROME(0): Timed    SSE YUV420 copy... 964384. Throughput: 613.6 MiB/s.
(--) CHROME(0): Timed    MMX YUV420 copy... 1562032. Throughput: 378.9 MiB/s.
(--) CHROME(0): Ditching 3DNow! YUV420 copy. Not supported by CPU.
(--) CHROME(0): Timed   MMX2 YUV420 copy... 1035442. Throughput: 571.5 MiB/s.
Freed 7683200 (pool 2)
(--) CHROME(0): Using SSE YUV42X copy for video.
(II) CHROME(0): [XvMC] Registering chromeXvMC.
(II) CHROME(0): [XvMC] Initialized XvMC extension.
(II) CHROME(0): - Done
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
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: Loaded and initialized /usr/lib/dri/unichrome_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Sleep Button (/dev/input/event1)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/event5)
(**) ImPS/2 Logitech Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Logitech Wheel Mouse: always reports core events
(**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Logitech Wheel Mouse: Found relative axes
(II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
(**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Logitech Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) CHROME(0): ViaDisplayEnableCRT
```

---

### Post by david_215 on 2010-09-25
Here's the output from xrandr -q

Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0 


I can already see there is much useful stuff here and in the xorg.0.log file!

Thanks for the help so far!

---

### Post by david_215 on 2010-09-25
Thanks for the code tags, overdrank!  I was wondering how to do that!  :)

---

### Post by david_215 on 2010-09-25
OK, this xorg.conf results in good TV out, however it throws mythbuntu into "low graphics mode" with stuttering video playback.
Disconnecting my monitor and just running the TV did not improve the playback

```


Section "Device"
    Identifier "Videocard0"
    Driver "openchrome"
    BusID "0:1:0:0"
    Screen 0
    Option "ActiveDevice" "CRT,TV"
    Option "TVType" "NTSC"
    Option "TVOutput" "Composite"
EndSection
```

---


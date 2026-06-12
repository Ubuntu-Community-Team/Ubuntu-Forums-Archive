---
title: "Ubuntu 10.10 Wrong Resolution"
date: 2011-06-12
forum: Multimedia Software
---

### Post by SketchMan3 on 2011-06-12
I'm running a live USB of Ubuntu 10.10 on an HP Pavilion a735w, because I don't have a hard drive right now. Everything was working fine until today. My default resolution is 1024 x 768. Sometimes the computer freezes up if I'm watching a video on Firefox and the persistence file gets used up. Well, this happened today, so I shut my computer down the hard way.When I booted it back up, the resolution was decreased to 800 x 600, or 640 x 480. 

There is no xorg.conf. And no propietary drivers.

I ran lspci and got this:

01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)


I ran sudo get-edid|parse-edid and got this:

```

parse-edid: parse-edid version 2.0.0
get-edid: get-edid version 2.0.0

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0xc40e8 "VIA KM400
"

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

parse-edid: EDID checksum passed.

    # EDID version 1 revision 3
Section "Monitor"
    # Block type: 2:0 3:fd
    # Block type: 2:0 3:fc
    Identifier "hp vx74"
    VendorName "HWP"
    ModelName "hp vx74"
    # Block type: 2:0 3:fd
    HorizSync 30-70
    VertRefresh 50-160
    # Max dot clock (video bandwidth) 110 MHz
    # Block type: 2:0 3:fc
    # Block type: 2:0 3:ff
    # DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

    Mode     "1024x768"    # vfreq 84.997Hz, hfreq 68.677kHz
        DotClock    94.500000
        HTimings    1024 1072 1168 1376
        VTimings    768 769 772 808
        Flags    "+HSync" "+VSync"
    EndMode
    # Block type: 2:0 3:fd
    # Block type: 2:0 3:fc
    # Block type: 2:0 3:ff
EndSection

```Let me know if you need anymore information. I'm guessing something got messed up when I powered off my computer.

---

### Post by Yellow Pasque on 2011-06-12
Post contents of /var/log/Xorg.0.log. Please use [ code ][ /code ] tags.

---

### Post by SketchMan3 on 2011-06-12
```

[   222.581] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   222.581] X Protocol Version 11, Revision 0
[   222.581] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   222.581] Current Operating System: Linux ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[   222.581] Kernel command line: noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[   222.581] Build Date: 16 September 2010  05:39:22PM
[   222.581] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[   222.581] Current version of pixman: 0.18.4
[   222.581]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   222.581] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   222.582] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jun 12 05:05:20 2011
[   222.583] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   222.583] (==) No Layout section.  Using the first Screen section.
[   222.583] (==) No screen section available. Using defaults.
[   222.583] (**) |-->Screen "Default Screen Section" (0)
[   222.583] (**) |   |-->Monitor "<default monitor>"
[   222.584] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   222.584] (==) Automatically adding devices
[   222.584] (==) Automatically enabling devices
[   222.585] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   222.585]     Entry deleted from font path.
[   222.586] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   222.586] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   222.586] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   222.586] (II) Loader magic: 0x81f8e00
[   222.586] (II) Module ABI versions:
[   222.586]     X.Org ANSI C Emulation: 0.4
[   222.586]     X.Org Video Driver: 8.0
[   222.586]     X.Org XInput driver : 11.0
[   222.586]     X.Org Server Extension : 4.0
[   222.587] (--) PCI:*(0:1:0:0) 1106:7205:1043:8118 rev 1, Mem @ 0xe4000000/67108864, 0xe8000000/16777216, BIOS @ 0x????????/65536
[   222.587] (II) Open ACPI successful (/var/run/acpid.socket)
[   222.588] (II) LoadModule: "extmod"
[   222.590] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   222.590] (II) Module extmod: vendor="X.Org Foundation"
[   222.590]     compiled for 1.9.0, module version = 1.0.0
[   222.590]     Module class: X.Org Server Extension
[   222.590]     ABI class: X.Org Server Extension, version 4.0
[   222.590] (II) Loading extension MIT-SCREEN-SAVER
[   222.590] (II) Loading extension XFree86-VidModeExtension
[   222.590] (II) Loading extension XFree86-DGA
[   222.590] (II) Loading extension DPMS
[   222.590] (II) Loading extension XVideo
[   222.590] (II) Loading extension XVideo-MotionCompensation
[   222.591] (II) Loading extension X-Resource
[   222.591] (II) LoadModule: "dbe"
[   222.591] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   222.591] (II) Module dbe: vendor="X.Org Foundation"
[   222.591]     compiled for 1.9.0, module version = 1.0.0
[   222.591]     Module class: X.Org Server Extension
[   222.591]     ABI class: X.Org Server Extension, version 4.0
[   222.591] (II) Loading extension DOUBLE-BUFFER
[   222.591] (II) LoadModule: "glx"
[   222.592] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   222.592] (II) Module glx: vendor="X.Org Foundation"
[   222.592]     compiled for 1.9.0, module version = 1.0.0
[   222.592]     ABI class: X.Org Server Extension, version 4.0
[   222.592] (==) AIGLX enabled
[   222.592] (II) Loading extension GLX
[   222.592] (II) LoadModule: "record"
[   222.593] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   222.593] (II) Module record: vendor="X.Org Foundation"
[   222.593]     compiled for 1.9.0, module version = 1.13.0
[   222.593]     Module class: X.Org Server Extension
[   222.593]     ABI class: X.Org Server Extension, version 4.0
[   222.593] (II) Loading extension RECORD
[   222.593] (II) LoadModule: "dri"
[   222.594] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   222.594] (II) Module dri: vendor="X.Org Foundation"
[   222.594]     compiled for 1.9.0, module version = 1.0.0
[   222.594]     ABI class: X.Org Server Extension, version 4.0
[   222.594] (II) Loading extension XFree86-DRI
[   222.594] (II) LoadModule: "dri2"
[   222.595] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   222.595] (II) Module dri2: vendor="X.Org Foundation"
[   222.595]     compiled for 1.9.0, module version = 1.2.0
[   222.595]     ABI class: X.Org Server Extension, version 4.0
[   222.595] (II) Loading extension DRI2
[   222.595] (==) Matched openchrome as autoconfigured driver 0
[   222.595] (==) Matched vesa as autoconfigured driver 1
[   222.595] (==) Matched fbdev as autoconfigured driver 2
[   222.595] (==) Assigned the driver to the xf86ConfigLayout
[   222.595] (II) LoadModule: "openchrome"
[   222.595] (II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
[   222.596] (II) Module openchrome: vendor="http://openchrome.org/"
[   222.596]     compiled for 1.8.99.905, module version = 0.2.904
[   222.596]     Module class: X.Org Video Driver
[   222.596]     ABI class: X.Org Video Driver, version 8.0
[   222.596] (II) LoadModule: "vesa"
[   222.596] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   222.597] (II) Module vesa: vendor="X.Org Foundation"
[   222.597]     compiled for 1.8.99.905, module version = 2.3.0
[   222.597]     Module class: X.Org Video Driver
[   222.597]     ABI class: X.Org Video Driver, version 8.0
[   222.597] (II) LoadModule: "fbdev"
[   222.597] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   222.597] (II) Module fbdev: vendor="X.Org Foundation"
[   222.597]     compiled for 1.8.99.905, module version = 0.4.2
[   222.597]     ABI class: X.Org Video Driver, version 8.0
[   222.597] (II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
    K8M800/K8N800, PM800/PM880/CN400, VM800/P4M800Pro/VN800/CN700,
    K8M890/K8N890, P4M900/VN896/CN896, CX700/VX700, P4M890, VX800/VX820,
    VX855/VX875
[   222.598] (II) VESA: driver for VESA chipsets: vesa
[   222.598] (II) FBDEV: driver for framebuffer: fbdev
[   222.598] (++) using VT number 7

[   222.599] (!!) VIA Technologies does not support this driver in any way.
[   222.599] (!!) For support, please refer to http://www.openchrome.org/.
[   222.599] (!!) (development build, compiled on Tue 10 Aug 2010 10:07:16 EST)
[   222.599] (WW) Falling back to old probe method for vesa
[   222.599] (WW) Falling back to old probe method for fbdev
[   222.599] (II) Loading sub module "fbdevhw"
[   222.599] (II) LoadModule: "fbdevhw"
[   222.600] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   222.600] (II) Module fbdevhw: vendor="X.Org Foundation"
[   222.600]     compiled for 1.9.0, module version = 0.0.2
[   222.600]     ABI class: X.Org Video Driver, version 8.0
[   222.600] (EE) open /dev/fb0: No such file or directory
[   222.600] (II) CHROME(0): VIAPreInit
[   222.600] (II) Loading sub module "vgahw"
[   222.600] (II) LoadModule: "vgahw"
[   222.601] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[   222.601] (II) Module vgahw: vendor="X.Org Foundation"
[   222.601]     compiled for 1.9.0, module version = 0.1.0
[   222.601]     ABI class: X.Org Video Driver, version 8.0
[   222.601] (II) CHROME(0): VIAGetRec
[   222.601] (II) CHROME(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   222.601] (==) CHROME(0): Depth 24, (--) framebuffer bpp 32
[   222.601] (==) CHROME(0): RGB weight 888
[   222.601] (==) CHROME(0): Default visual is TrueColor
[   222.601] (--) CHROME(0): Chipset: KM400/KN400
[   222.602] (--) CHROME(0): Chipset revision: 132
[   222.602] (--) CHROME(0): Probed amount of VideoRAM = 65536 kB
[   222.602] (II) CHROME(0): VIASetupDefaultOptions - Setting up default chipset options.
[   222.602] (==) CHROME(0): Shadow framebuffer is disabled.
[   222.602] (==) CHROME(0): Hardware acceleration is enabled.
[   222.602] (==) CHROME(0): Using XAA acceleration architecture.
[   222.602] (==) CHROME(0): Using hardware two-color cursors and software full-color cursors.
[   222.602] (==) CHROME(0): GPU virtual command queue will be enabled.
[   222.602] (==) CHROME(0): DRI IRQ will be disabled if DRI is enabled.
[   222.602] (==) CHROME(0): AGP DMA will be enabled if DRI is enabled.
[   222.602] (==) CHROME(0): AGP DMA will be used for 2D acceleration.
[   222.602] (==) CHROME(0): PCI DMA will be used for XV image transfer if DRI is enabled.
[   222.602] (==) CHROME(0): Will not enable VBE modes.
[   222.602] (==) CHROME(0): VBE VGA register save & restore will not be used
    if VBE modes are enabled.
[   222.602] (==) CHROME(0): Xv Bandwidth check is enabled.
[   222.602] (==) CHROME(0): Will not impose a limit on video RAM reserved for DRI.
[   222.602] (==) CHROME(0): Will try to allocate 32768 kB of AGP memory.
[   222.602] (==) CHROME(0): Digital output bus width is 12 bits.
[   222.602] (==) CHROME(0): DVI Center is disabled.
[   222.602] (==) CHROME(0): Panel size is not selected from config file.
[   222.602] (==) CHROME(0): Panel will not be forced.
[   222.602] (==) CHROME(0): TV dotCrawl is disabled.
[   222.602] (==) CHROME(0): TV deflicker is set to 0.
[   222.602] (==) CHROME(0): No default TV type is set.
[   222.602] (==) CHROME(0): No default TV output signal type is set.
[   222.602] (==) CHROME(0): No default TV output port is set.
[   222.602] (II) CHROME(0): VIAMapMMIO
[   222.602] (--) CHROME(0): mapping MMIO @ 0xe8000000 with size 0x9000
[   222.602] (--) CHROME(0): mapping BitBlt MMIO @ 0xe8200000 with size 0x200000
[   222.603] (II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[   222.603] (==) CHROME(0): Will not print VGA registers.
[   222.603] (==) CHROME(0): Will not scan I2C buses.
[   222.603] (II) CHROME(0): ...Finished parsing config file options.
[   222.603] (--) CHROME(0): Detected Asustek A7V8X-MX SE / A7V400-MX. Card-Ids (1043|8118)
[   222.603] (II) CHROME(0): Detected MemClk 5
[   222.603] (II) CHROME(0): ViaGetMemoryBandwidth. Memory type: 5
[   222.603] (II) CHROME(0): Detected TV standard: NTSC.
[   222.603] (==) CHROME(0): Using gamma correction (1.0, 1.0, 1.0)
[   222.603] (II) Loading sub module "i2c"
[   222.603] (II) LoadModule: "i2c"
[   222.603] (II) Module "i2c" already built-in
[   222.603] (II) CHROME(0): ViaI2CInit
[   222.603] (II) CHROME(0): ViaI2CBus1Init
[   222.603] (II) CHROME(0): I2C bus "I2C bus 1" initialized.
[   222.603] (II) CHROME(0): ViaI2cBus2Init
[   222.603] (II) CHROME(0): I2C bus "I2C bus 2" initialized.
[   222.603] (II) CHROME(0): ViaI2CBus3Init
[   222.603] (II) CHROME(0): I2C bus "I2C bus 3" initialized.
[   222.603] (II) Loading sub module "ddc"
[   222.603] (II) LoadModule: "ddc"
[   222.603] (II) Module "ddc" already built-in
[   222.603] (II) CHROME(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
[   222.789] (II) CHROME(0): ViaOutputsDetect
[   222.789] (II) CHROME(0): VIATVDetect
[   222.790] (II) CHROME(0): ViaOutputsSelect
[   222.790] (II) CHROME(0): ViaOutputsSelect: X Configuration: 0x00
[   222.790] (II) CHROME(0): ViaOutputsSelect: BIOS Initialised register: 0x00
[   222.790] (II) CHROME(0): ViaOutputsSelect: CRT.
[   222.790] (II) CHROME(0): ViaModesAttach
[   222.790] (II) CHROME(0): <default monitor>: Using default hsync range of 31.50-37.90 kHz
[   222.790] (II) CHROME(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[   222.790] (WW) CHROME(0): Unable to estimate virtual size
[   222.790] (II) CHROME(0): Clock range:  20.00 to 230.00 MHz
[   222.790] (II) CHROME(0): ViaValidMode: Validating 640x350 (Clock: 31500)
[   222.790] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.790] (II) CHROME(0): ViaComputeDotClock 31500 : c558 : 050b
[   222.790] (II) CHROME(0): Not using default mode "640x350" (vrefresh out of range)
[   222.790] (II) CHROME(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
[   222.790] (II) CHROME(0): ViaValidMode: Validating 640x400 (Clock: 31500)
[   222.790] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.791] (II) CHROME(0): ViaComputeDotClock 31500 : c558 : 050b
[   222.791] (II) CHROME(0): Not using default mode "640x400" (vrefresh out of range)
[   222.791] (II) CHROME(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
[   222.791] (II) CHROME(0): ViaValidMode: Validating 720x400 (Clock: 35500)
[   222.791] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.791] (II) CHROME(0): ViaComputeDotClock 35500 : 5877 : c677
[   222.791] (II) CHROME(0): Not using default mode "720x400" (vrefresh out of range)
[   222.791] (II) CHROME(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
[   222.791] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 25175)
[   222.791] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.791] (II) CHROME(0): ViaComputeDotClock 25175 : 0000 : 0407
[   222.791] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   222.791] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
[   222.791] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.791] (II) CHROME(0): ViaComputeDotClock 31500 : c558 : 050b
[   222.791] (II) CHROME(0): Not using default mode "640x480" (vrefresh out of range)
[   222.792] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   222.792] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
[   222.792] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.792] (II) CHROME(0): ViaComputeDotClock 31500 : c558 : 050b
[   222.792] (II) CHROME(0): Not using default mode "640x480" (vrefresh out of range)
[   222.792] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   222.792] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 36000)
[   222.792] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.792] (II) CHROME(0): ViaComputeDotClock 36000 : 5879 : c679
[   222.792] (II) CHROME(0): Not using default mode "640x480" (hsync out of range)
[   222.792] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   222.792] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 36000)
[   222.792] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.792] (II) CHROME(0): ViaComputeDotClock 36000 : 5879 : c679
[   222.792] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   222.793] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 40000)
[   222.793] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.793] (II) CHROME(0): ViaComputeDotClock 40000 : 515f : 8643
[   222.793] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   222.793] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 50000)
[   222.793] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.793] (II) CHROME(0): ViaComputeDotClock 50000 : c354 : 0207
[   222.793] (II) CHROME(0): Not using default mode "800x600" (hsync out of range)
[   222.793] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   222.793] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 49500)
[   222.793] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.793] (II) CHROME(0): ViaComputeDotClock 49500 : c353 : 8653
[   222.793] (II) CHROME(0): Not using default mode "800x600" (hsync out of range)
[   222.793] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   222.793] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 56300)
[   222.793] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.794] (II) CHROME(0): ViaComputeDotClock 56300 : 4f76 : 4737
[   222.794] (II) CHROME(0): Not using default mode "800x600" (hsync out of range)
[   222.794] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   222.794] (II) CHROME(0): ViaValidMode: Validating 1024x768i (Clock: 44900)
[   222.794] (II) CHROME(0): Not using default mode "1024x768i" (interlace mode not supported)
[   222.794] (II) CHROME(0): Not using default mode "512x384i" (bad mode clock/interlace/doublescan)
[   222.794] (II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 65000)
[   222.794] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.794] (II) CHROME(0): ViaComputeDotClock 65000 : 0d3b : 866d
[   222.794] (II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
[   222.794] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   222.794] (II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 75000)
[   222.794] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.794] (II) CHROME(0): ViaComputeDotClock 75000 : 156e : 0415
[   222.794] (II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
[   222.795] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   222.795] (II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 78750)
[   222.795] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.795] (II) CHROME(0): ViaComputeDotClock 78750 : 0000 : 020b
[   222.795] (II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
[   222.795] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   222.795] (II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 94500)
[   222.795] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.795] (II) CHROME(0): ViaComputeDotClock 94500 : 4542 : 0521
[   222.795] (II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
[   222.795] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   222.795] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 108000)
[   222.795] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.795] (II) CHROME(0): ViaComputeDotClock 108000 : 0b53 : 8479
[   222.795] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   222.796] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   222.796] (II) CHROME(0): ViaValidMode: Validating 1280x960 (Clock: 108000)
[   222.796] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.796] (II) CHROME(0): ViaComputeDotClock 108000 : 0b53 : 8479
[   222.796] (II) CHROME(0): Not using default mode "1280x960" (hsync out of range)
[   222.796] (II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[   222.796] (II) CHROME(0): ViaValidMode: Validating 1280x960 (Clock: 148500)
[   222.796] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.796] (II) CHROME(0): ViaComputeDotClock 148500 : 0853 : 4453
[   222.796] (II) CHROME(0): Not using default mode "1280x960" (hsync out of range)
[   222.796] (II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[   222.796] (II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 108000)
[   222.796] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.796] (II) CHROME(0): ViaComputeDotClock 108000 : 0b53 : 8479
[   222.796] (II) CHROME(0): Not using default mode "1280x1024" (hsync out of range)
[   222.796] (II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[   222.797] (II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 135000)
[   222.797] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.797] (II) CHROME(0): ViaComputeDotClock 135000 : 0742 : 0742
[   222.797] (II) CHROME(0): Not using default mode "1280x1024" (hsync out of range)
[   222.797] (II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[   222.797] (II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 157500)
[   222.797] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.797] (II) CHROME(0): ViaComputeDotClock 157500 : 422c : 0216
[   222.797] (II) CHROME(0): Not using default mode "1280x1024" (hsync out of range)
[   222.797] (II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[   222.797] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 162000)
[   222.797] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.797] (II) CHROME(0): ViaComputeDotClock 162000 : 0a71 : 4571
[   222.797] (II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
[   222.797] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   222.798] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 175500)
[   222.798] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.798] (II) CHROME(0): ViaComputeDotClock 175500 : 4231 : 0431
[   222.798] (II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
[   222.798] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   222.798] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 189000)
[   222.798] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.798] (II) CHROME(0): ViaComputeDotClock 189000 : 0542 : 0542
[   222.798] (II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
[   222.798] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   222.798] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 202500)
[   222.798] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.798] (II) CHROME(0): ViaComputeDotClock 202500 : 0763 : 0763
[   222.798] (II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
[   222.798] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   222.798] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 229500)
[   222.798] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.799] (II) CHROME(0): ViaComputeDotClock 229500 : 0660 : 0220
[   222.799] (II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
[   222.799] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   222.799] (II) CHROME(0): ViaValidMode: Validating 1792x1344 (Clock: 204800)
[   222.799] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.799] (II) CHROME(0): ViaComputeDotClock 204800 : 0764 : 0764
[   222.799] (II) CHROME(0): Not using default mode "1792x1344" (hsync out of range)
[   222.799] (II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[   222.799] (II) CHROME(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
[   222.799] (II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[   222.799] (II) CHROME(0): ViaValidMode: Validating 1856x1392 (Clock: 218300)
[   222.799] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.799] (II) CHROME(0): ViaComputeDotClock 218300 : 043d : 043d
[   222.799] (II) CHROME(0): Not using default mode "1856x1392" (hsync out of range)
[   222.799] (II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[   222.800] (II) CHROME(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
[   222.800] (II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[   222.800] (II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[   222.800] (II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[   222.800] (II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[   222.800] (II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[   222.800] (II) CHROME(0): ViaValidMode: Validating 832x624 (Clock: 57284)
[   222.800] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.800] (II) CHROME(0): ViaComputeDotClock 57284 : 4e70 : 0208
[   222.800] (II) CHROME(0): Not using default mode "832x624" (hsync out of range)
[   222.800] (II) CHROME(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
[   222.800] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 81620)
[   222.800] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.800] (II) CHROME(0): ViaComputeDotClock 81620 : 0000 : 4539
[   222.800] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   222.800] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   222.800] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 96770)
[   222.800] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.801] (II) CHROME(0): ViaComputeDotClock 96770 : 0000 : 041b
[   222.801] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   222.801] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   222.801] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 104990)
[   222.801] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.801] (II) CHROME(0): ViaComputeDotClock 104990 : 0000 : 0316
[   222.801] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   222.801] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   222.801] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 119650)
[   222.801] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.801] (II) CHROME(0): ViaComputeDotClock 119650 : 0000 : 4775
[   222.801] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   222.801] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   222.801] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 121500)
[   222.801] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.802] (II) CHROME(0): ViaComputeDotClock 121500 : 0000 : 0211
[   222.802] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   222.802] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   222.802] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 143470)
[   222.802] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.802] (II) CHROME(0): ViaComputeDotClock 143470 : 0000 : 0214
[   222.802] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   222.802] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   222.802] (II) CHROME(0): ViaValidMode: Validating 1360x768 (Clock: 72000)
[   222.802] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.802] (II) CHROME(0): ViaComputeDotClock 72000 : 0000 : 8679
[   222.802] (II) CHROME(0): Not using default mode "1360x768" (hsync out of range)
[   222.802] (II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[   222.802] (II) CHROME(0): ViaValidMode: Validating 1360x768 (Clock: 84750)
[   222.802] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.803] (II) CHROME(0): ViaComputeDotClock 84750 : 0000 : 4647
[   222.803] (II) CHROME(0): Not using default mode "1360x768" (hsync out of range)
[   222.803] (II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[   222.803] (II) CHROME(0): ViaValidMode: Validating 1400x1050 (Clock: 122000)
[   222.803] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.803] (II) CHROME(0): ViaComputeDotClock 122000 : 0d6f : 0211
[   222.803] (II) CHROME(0): Not using default mode "1400x1050" (hsync out of range)
[   222.803] (II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   222.803] (II) CHROME(0): ViaValidMode: Validating 1400x1050 (Clock: 145060)
[   222.803] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.803] (II) CHROME(0): ViaComputeDotClock 145060 : 0000 : 4451
[   222.803] (II) CHROME(0): Not using default mode "1400x1050" (hsync out of range)
[   222.803] (II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   222.803] (II) CHROME(0): ViaValidMode: Validating 1400x1050 (Clock: 155800)
[   222.803] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.803] (II) CHROME(0): Not using default mode "1400x1050" (horizontal sync too wide)
[   222.803] (II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   222.803] (II) CHROME(0): ViaValidMode: Validating 1400x1050 (Clock: 179260)
[   222.803] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.804] (II) CHROME(0): ViaComputeDotClock 179260 : 0000 : 0219
[   222.804] (II) CHROME(0): Not using default mode "1400x1050" (hsync out of range)
[   222.804] (II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   222.804] (II) CHROME(0): ViaValidMode: Validating 1440x900 (Clock: 106500)
[   222.804] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.804] (II) CHROME(0): ViaComputeDotClock 106500 : 0000 : 8477
[   222.804] (II) CHROME(0): Not using default mode "1440x900" (hsync out of range)
[   222.804] (II) CHROME(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
[   222.804] (II) CHROME(0): ViaValidMode: Validating 1600x1024 (Clock: 103125)
[   222.804] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.804] (II) CHROME(0): ViaComputeDotClock 103125 : 0000 : 0524
[   222.804] (II) CHROME(0): Not using default mode "1600x1024" (hsync out of range)
[   222.804] (II) CHROME(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
[   222.804] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 119000)
[   222.804] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.805] (II) CHROME(0): ViaComputeDotClock 119000 : 0000 : 4553
[   222.805] (II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
[   222.805] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   222.805] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 146250)
[   222.805] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.805] (II) CHROME(0): ViaComputeDotClock 146250 : 0000 : 0533
[   222.805] (II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
[   222.805] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   222.805] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 174000)
[   222.805] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.805] (II) CHROME(0): ViaComputeDotClock 174000 : 0000 : 0755
[   222.805] (II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
[   222.805] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   222.805] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 187000)
[   222.805] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.806] (II) CHROME(0): ViaComputeDotClock 187000 : 0000 : 021a
[   222.806] (II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
[   222.806] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   222.806] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 214750)
[   222.806] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.806] (II) CHROME(0): ViaComputeDotClock 214750 : 0000 : 021e
[   222.806] (II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
[   222.806] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   222.806] (II) CHROME(0): ViaValidMode: Validating 1920x1080 (Clock: 138500)
[   222.806] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.806] (II) CHROME(0): ViaComputeDotClock 138500 : 0000 : 031d
[   222.806] (II) CHROME(0): Not using default mode "1920x1080" (hsync out of range)
[   222.806] (II) CHROME(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
[   222.806] (II) CHROME(0): ViaValidMode: Validating 1920x1200 (Clock: 154000)
[   222.806] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.807] (II) CHROME(0): ViaComputeDotClock 154000 : 0000 : 042b
[   222.807] (II) CHROME(0): Not using default mode "1920x1200" (hsync out of range)
[   222.807] (II) CHROME(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
[   222.807] (II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[   222.807] (II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[   222.807] (II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[   222.807] (II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[   222.807] (II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[   222.807] (II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[   222.807] (II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[   222.807] (II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[   222.807] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 40000)
[   222.807] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.807] (II) CHROME(0): ViaComputeDotClock 40000 : 515f : 8643
[   222.807] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 36000)
[   222.807] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.807] (II) CHROME(0): ViaComputeDotClock 36000 : 5879 : c679
[   222.807] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 25175)
[   222.807] (II) CHROME(0): ViaFirstCRTCModeValid
[   222.808] (II) CHROME(0): ViaComputeDotClock 25175 : 0000 : 0407
[   222.808] (--) CHROME(0): Virtual size is 800x600 (pitch 800)
[   222.808] (**) CHROME(0): *Default mode "800x600": 40.0 MHz (scaled from 106560.0 MHz), 37.9 kHz, 60.3 Hz
[   222.808] (II) CHROME(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   222.808] (**) CHROME(0): *Default mode "800x600": 36.0 MHz (scaled from 95904.0 MHz), 35.2 kHz, 56.2 Hz
[   222.808] (II) CHROME(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   222.808] (**) CHROME(0): *Default mode "640x480": 25.2 MHz (scaled from 67066.2 MHz), 31.5 kHz, 59.9 Hz
[   222.808] (II) CHROME(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   222.808] (==) CHROME(0): DPI set to (96, 96)
[   222.808] (II) Loading sub module "fb"
[   222.808] (II) LoadModule: "fb"
[   222.809] (II) Loading /usr/lib/xorg/modules/libfb.so
[   222.809] (II) Module fb: vendor="X.Org Foundation"
[   222.809]     compiled for 1.9.0, module version = 1.0.0
[   222.809]     ABI class: X.Org ANSI C Emulation, version 0.4
[   222.809] (II) Loading sub module "xaa"
[   222.809] (II) LoadModule: "xaa"
[   222.810] (II) Loading /usr/lib/xorg/modules/libxaa.so
[   222.810] (II) Module xaa: vendor="X.Org Foundation"
[   222.810]     compiled for 1.9.0, module version = 1.2.1
[   222.810]     ABI class: X.Org Video Driver, version 8.0
[   222.810] (II) Loading sub module "ramdac"
[   222.810] (II) LoadModule: "ramdac"
[   222.810] (II) Module "ramdac" already built-in
[   222.810] (II) CHROME(0): VIAUnmapMem
[   222.810] (II) UnloadModule: "vesa"
[   222.811] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   222.811] (II) UnloadModule: "fbdev"
[   222.811] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   222.811] (II) UnloadModule: "fbdevhw"
[   222.811] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[   222.811] (--) Depth 24 pixmap format is 32 bpp
[   222.811] (II) CHROME(0): VIAScreenInit
[   222.811] (II) CHROME(0): VIAMapFB
[   222.811] (--) CHROME(0): mapping framebuffer @ 0xe4000000 with size 0x4000000
[   222.819] (--) CHROME(0): Frame buffer start: 0xb37b7000, free start: 0x1d4c00 end: 0x4000000
[   222.819] (II) CHROME(0): VIAMapMMIO
[   222.819] (--) CHROME(0): mapping MMIO @ 0xe8000000 with size 0x9000
[   222.819] (--) CHROME(0): mapping BitBlt MMIO @ 0xe8200000 with size 0x200000
[   222.819] (II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[   222.819] (II) CHROME(0): VIASave
[   222.819] (II) CHROME(0): Primary
[   222.926] (II) CHROME(0): Primary Adapter! saving VGA_SR_ALL !!
[   222.927] (II) CHROME(0): Crtc...
[   222.927] (II) CHROME(0): TVSave...
[   222.927] (II) CHROME(0): VIAWriteMode
[   222.927] (II) CHROME(0): ViaModePrimaryLegacy
[   222.927] (II) CHROME(0): Name: 800x600
[   222.927] (II) CHROME(0): Clock: 40000
[   222.927] (II) CHROME(0): VRefresh: 60.316540
[   222.927] (II) CHROME(0): HSync: 37.878788
[   222.927] (II) CHROME(0): HDisplay: 800
[   222.927] (II) CHROME(0): HSyncStart: 840
[   222.927] (II) CHROME(0): HSyncEnd: 968
[   222.927] (II) CHROME(0): HTotal: 1056
[   222.927] (II) CHROME(0): HSkew: 0
[   222.927] (II) CHROME(0): VDisplay: 600
[   222.927] (II) CHROME(0): VSyncStart: 601
[   222.927] (II) CHROME(0): VSyncEnd: 605
[   222.927] (II) CHROME(0): VTotal: 628
[   222.927] (II) CHROME(0): VScan: 0
[   222.927] (II) CHROME(0): Flags: 5
[   222.927] (II) CHROME(0): CrtcHDisplay: 0x320
[   222.927] (II) CHROME(0): CrtcHBlankStart: 0x320
[   222.927] (II) CHROME(0): CrtcHSyncStart: 0x348
[   222.927] (II) CHROME(0): CrtcHSyncEnd: 0x3c8
[   222.927] (II) CHROME(0): CrtcHBlankEnd: 0x420
[   222.927] (II) CHROME(0): CrtcHTotal: 0x420
[   222.927] (II) CHROME(0): CrtcHSkew: 0x0
[   222.927] (II) CHROME(0): CrtcVDisplay: 0x258
[   222.927] (II) CHROME(0): CrtcVBlankStart: 0x258
[   222.927] (II) CHROME(0): CrtcVSyncStart: 0x259
[   222.927] (II) CHROME(0): CrtcVSyncEnd: 0x25d
[   222.927] (II) CHROME(0): CrtcVBlankEnd: 0x274
[   222.927] (II) CHROME(0): CrtcVTotal: 0x274
[   222.927] (II) CHROME(0): ViaFirstCRTCSetMode
[   222.927] (II) CHROME(0): Setting up 800x600
[   222.928] (II) CHROME(0): ViaComputeDotClock 40000 : 515f : 8643
[   222.928] (II) CHROME(0): ViaTVPower: Off.
[   222.928] (II) CHROME(0): ViaSetPrimaryFIFO
[   222.928] (II) CHROME(0): ViaSetPrimaryExpireNumber
[   222.928] (II) CHROME(0): ViaSetDotclock to 0x008643
[   222.928] (II) CHROME(0): ViaSetUseExternalClock
[   222.928] (II) CHROME(0): VIAAdjustFrame 0x0
[   222.928] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[   222.928] (II) CHROME(0): VIAAdjustFrame 0x0
[   222.928] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[   222.928] (II) CHROME(0): - Blanked
[   222.928] drmOpenDevice: node name is /dev/dri/card0
[   222.928] drmOpenDevice: open result is 11, (OK)
[   222.928] drmOpenDevice: node name is /dev/dri/card0
[   222.928] drmOpenDevice: open result is 11, (OK)
[   222.928] drmOpenByBusid: Searching for BusID PCI:1:0:0
[   222.928] drmOpenDevice: node name is /dev/dri/card0
[   222.928] drmOpenDevice: open result is 11, (OK)
[   222.928] drmOpenByBusid: drmOpenMinor returns 11
[   222.928] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   222.928] (II) [drm] DRM interface version 1.3
[   222.929] (II) [drm] DRM open master succeeded.
[   222.929] (II) CHROME(0): [drm] Using the DRM lock SAREA also for drawables.
[   222.929] (II) CHROME(0): [drm] framebuffer handle = 0xe4000000
[   222.929] (II) CHROME(0): [drm] added 1 reserved context for kernel
[   222.929] (II) CHROME(0): X context handle = 0x1
[   222.929] (II) CHROME(0): [drm] installed DRM signal handler
[   222.929] (II) CHROME(0): [dri] visual configs initialized.
[   222.929] (II) CHROME(0): [drm] register handle = 0xe8000000
[   222.929] (II) CHROME(0): [drm] framebuffer handle = 0xe4000000
[   222.930] (II) CHROME(0): [drm] mmio Registers = 0xe8000000
[   222.930] (II) CHROME(0): [dri] mmio mapped.
[   222.930] (II) CHROME(0): - Visuals set up
[   222.930] (II) CHROME(0): VIAInternalScreenInit
[   222.930] (II) CHROME(0): - B & W
[   222.930] (II) CHROME(0): CursorStart: 0x3fc0000
[   222.930] (II) CHROME(0): Frame Buffer From (0,0) To (800,2400)
[   222.930] (II) CHROME(0): Using 1800 lines for offscreen memory.
[   222.930] (II) CHROME(0): Using XFree86 Acceleration Architecture (XAA)
[   222.930]     Screen to screen bit blits
[   222.930]     Solid filled rectangles
[   222.930]     8x8 mono pattern filled rectangles
[   222.930]     8x8 color pattern filled rectangles
[   222.930]     Solid Lines
[   222.930]     Dashed Lines
[   222.930]     Image Writes
[   222.930]     Setting up tile and stipple cache:
[   222.930]         32 128x128 slots
[   222.930]         13 256x256 slots
[   222.930]         32 8x8 color pattern slots
[   222.930] (==) CHROME(0): Backing store disabled
[   222.930] (II) CHROME(0): - Backing store set up
[   222.930] (II) CHROME(0): - SW cursor set up
[   222.930] (II) CHROME(0): VIAHWCursorInit
[   222.931] (II) CHROME(0): - Def Color map set up
[   222.931] (II) CHROME(0): VIALoadPalette: numColors: 256
[   222.931] (II) CHROME(0): - Palette loaded
[   222.931] (==) CHROME(0): DPMS enabled
[   222.931] (II) CHROME(0): - DPMS set up
[   222.931] (II) CHROME(0): - Color maps etc. set up
[   222.931] (II) CHROME(0): [drm] Detected AGP vendor 0x1106, device 0x3205
[   222.931] (II) CHROME(0): [drm] Didn't find any AGP v3 compatible device. Trying AGP 4X mode.
[   222.931] (II) CHROME(0): [drm] Trying to enable AGP fast writes.
[   222.931] (II) CHROME(0): [drm] drmAgpEnabled succeeded
[   223.008] (II) CHROME(0): [drm] agpAddr = 0xe0000000
[   223.012] (II) CHROME(0): [drm] agpBase = (nil)
[   223.012] (II) CHROME(0): [drm] agpAddr = 0xe0000000
[   223.012] (II) CHROME(0): [drm] agpSize = 0x01e00000
[   223.012] (II) CHROME(0): [drm] agp physical addr = 0x00000000
[   223.012] (II) CHROME(0): [dri] Using AGP.
[   223.012] (II) CHROME(0): [drm] Using 59160288 bytes for DRM memory heap.
[   223.012] (II) CHROME(0): [dri] Frame buffer initialized.
[   223.012] (II) CHROME(0): [DRI] installation complete
[   223.012] (II) CHROME(0): [dri] Kernel data initialized.
[   223.013] (II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
[   223.013] (II) CHROME(0): direct rendering enabled
[   223.014] (II) CHROME(0): [Xv] Using PCI DMA for Xv image transfer.
[   223.015] Fulfilled via DRI at 7683200
[   223.015] (II) CHROME(0): Benchmarking video copy.  Less time is better.
[   223.022] (--) CHROME(0): Timed   libc YUV420 copy... 3570460. Throughput: 348.9 MiB/s.
[   223.028] (--) CHROME(0): Timed kernel YUV420 copy... 3771525. Throughput: 330.3 MiB/s.
[   223.034] (--) CHROME(0): Timed    SSE YUV420 copy... 3207457. Throughput: 388.4 MiB/s.
[   223.040] (--) CHROME(0): Timed    MMX YUV420 copy... 3382720. Throughput: 368.3 MiB/s.
[   223.046] (--) CHROME(0): Timed 3DNow! YUV420 copy... 3175650. Throughput: 392.3 MiB/s.
[   223.053] (--) CHROME(0): Timed   MMX2 YUV420 copy... 3639794. Throughput: 342.3 MiB/s.
[   223.053] Freed 7683200 (pool 2)
[   223.053] (--) CHROME(0): Using 3DNow! YUV42X copy for video.
[   223.053] (WW) CHROME(0): [XvMC] XvMC is not supported on this chipset.
[   223.053] (II) CHROME(0): - Done
[   223.053] (==) RandR enabled
[   223.053] (II) Initializing built-in extension Generic Event Extension
[   223.053] (II) Initializing built-in extension SHAPE
[   223.053] (II) Initializing built-in extension MIT-SHM
[   223.054] (II) Initializing built-in extension XInputExtension
[   223.054] (II) Initializing built-in extension XTEST
[   223.054] (II) Initializing built-in extension BIG-REQUESTS
[   223.054] (II) Initializing built-in extension SYNC
[   223.054] (II) Initializing built-in extension XKEYBOARD
[   223.054] (II) Initializing built-in extension XC-MISC
[   223.054] (II) Initializing built-in extension SECURITY
[   223.054] (II) Initializing built-in extension XINERAMA
[   223.054] (II) Initializing built-in extension XFIXES
[   223.054] (II) Initializing built-in extension RENDER
[   223.054] (II) Initializing built-in extension RANDR
[   223.054] (II) Initializing built-in extension COMPOSITE
[   223.054] (II) Initializing built-in extension DAMAGE
[   223.054] (II) Initializing built-in extension GESTURE
[   223.068] (II) AIGLX: Screen 0 is not DRI2 capable
[   223.068] drmOpenDevice: node name is /dev/dri/card0
[   223.068] drmOpenDevice: open result is 12, (OK)
[   223.068] drmOpenByBusid: Searching for BusID PCI:1:0:0
[   223.068] drmOpenDevice: node name is /dev/dri/card0
[   223.068] drmOpenDevice: open result is 12, (OK)
[   223.068] drmOpenByBusid: drmOpenMinor returns 12
[   223.068] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   223.098] (II) AIGLX: enabled GLX_SGI_make_current_read
[   223.098] (II) AIGLX: Loaded and initialized /usr/lib/dri/unichrome_dri.so
[   223.098] (II) GLX: Initialized DRI GL provider for screen 0
[   223.133] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   223.150] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   223.150] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   223.150] (II) LoadModule: "evdev"
[   223.151] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   223.153] (II) Module evdev: vendor="X.Org Foundation"
[   223.153]     compiled for 1.9.0, module version = 2.3.2
[   223.153]     Module class: X.Org XInput Driver
[   223.153]     ABI class: X.Org XInput driver, version 11.0
[   223.153] (**) Power Button: always reports core events
[   223.153] (**) Power Button: Device: "/dev/input/event1"
[   223.153] (II) Power Button: Found keys
[   223.153] (II) Power Button: Configuring as keyboard
[   223.153] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   223.153] (**) Option "xkb_rules" "evdev"
[   223.153] (**) Option "xkb_model" "pc105"
[   223.153] (**) Option "xkb_layout" "us"
[   223.156] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   223.156] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   223.156] (**) Power Button: always reports core events
[   223.156] (**) Power Button: Device: "/dev/input/event0"
[   223.156] (II) Power Button: Found keys
[   223.156] (II) Power Button: Configuring as keyboard
[   223.156] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   223.156] (**) Option "xkb_rules" "evdev"
[   223.156] (**) Option "xkb_model" "pc105"
[   223.156] (**) Option "xkb_layout" "us"
[   223.160] (II) config/udev: Adding input device Generic X-Box pad (/dev/input/event3)
[   223.160] (II) No input driver/identifier specified (ignoring)
[   223.160] (II) config/udev: Adding input device Generic X-Box pad (/dev/input/js0)
[   223.160] (II) No input driver/identifier specified (ignoring)
[   223.168] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[   223.168] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   223.168] (**) AT Translated Set 2 keyboard: always reports core events
[   223.168] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[   223.168] (II) AT Translated Set 2 keyboard: Found keys
[   223.168] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   223.168] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   223.168] (**) Option "xkb_rules" "evdev"
[   223.168] (**) Option "xkb_model" "pc105"
[   223.168] (**) Option "xkb_layout" "us"
[   223.169] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event4)
[   223.169] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[   223.169] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[   223.169] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event4"
[   223.169] (II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[   223.169] (II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[   223.169] (II) ImPS/2 Generic Wheel Mouse: Found relative axes
[   223.169] (II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[   223.169] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[   223.169] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[   223.169] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   223.169] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[   223.169] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[   223.170] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[   223.170] (II) No input driver/identifier specified (ignoring)
[   318.872] (II) CHROME(0): VIASwitchMode
[   318.872] (II) CHROME(0): [drm] Cleaning up DMA ring-buffer.
[   318.872] (II) CHROME(0): VIAWriteMode
[   318.872] (II) CHROME(0): ViaModePrimaryLegacy
[   318.872] (II) CHROME(0): Name: 640x480
[   318.872] (II) CHROME(0): Clock: 25175
[   318.872] (II) CHROME(0): VRefresh: 59.940475
[   318.872] (II) CHROME(0): HSync: 31.468750
[   318.873] (II) CHROME(0): HDisplay: 640
[   318.873] (II) CHROME(0): HSyncStart: 656
[   318.873] (II) CHROME(0): HSyncEnd: 752
[   318.873] (II) CHROME(0): HTotal: 800
[   318.873] (II) CHROME(0): HSkew: 0
[   318.873] (II) CHROME(0): VDisplay: 480
[   318.873] (II) CHROME(0): VSyncStart: 490
[   318.873] (II) CHROME(0): VSyncEnd: 492
[   318.873] (II) CHROME(0): VTotal: 525
[   318.873] (II) CHROME(0): VScan: 0
[   318.873] (II) CHROME(0): Flags: 10
[   318.873] (II) CHROME(0): CrtcHDisplay: 0x280
[   318.873] (II) CHROME(0): CrtcHBlankStart: 0x280
[   318.873] (II) CHROME(0): CrtcHSyncStart: 0x290
[   318.873] (II) CHROME(0): CrtcHSyncEnd: 0x2f0
[   318.873] (II) CHROME(0): CrtcHBlankEnd: 0x320
[   318.873] (II) CHROME(0): CrtcHTotal: 0x320
[   318.873] (II) CHROME(0): CrtcHSkew: 0x0
[   318.873] (II) CHROME(0): CrtcVDisplay: 0x1e0
[   318.873] (II) CHROME(0): CrtcVBlankStart: 0x1e0
[   318.873] (II) CHROME(0): CrtcVSyncStart: 0x1ea
[   318.873] (II) CHROME(0): CrtcVSyncEnd: 0x1ec
[   318.873] (II) CHROME(0): CrtcVBlankEnd: 0x20d
[   318.873] (II) CHROME(0): CrtcVTotal: 0x20d
[   318.873] (II) CHROME(0): ViaFirstCRTCSetMode
[   318.873] (II) CHROME(0): Setting up 640x480
[   318.873] (II) CHROME(0): ViaComputeDotClock 25175 : 0000 : 0407
[   318.873] (II) CHROME(0): ViaTVPower: Off.
[   318.873] (II) CHROME(0): ViaSetPrimaryFIFO
[   318.873] (II) CHROME(0): ViaSetPrimaryExpireNumber
[   318.873] (II) CHROME(0): ViaSetDotclock to 0x000407
[   318.873] (II) CHROME(0): ViaSetUseExternalClock
[   318.874] (II) CHROME(0): VIAAdjustFrame 0x0
[   318.874] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[   318.874] (II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
[   318.874] (II) CHROME(0): VIALoadPalette: numColors: 256
[   318.874] (II) CHROME(0): VIAAdjustFrame 0x0
[   318.874] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[   318.874] (II) CHROME(0): VIAAdjustFrame 1x1
[   318.874] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[   318.874] (II) CHROME(0): VIAAdjustFrame 0x0
[   318.874] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[   321.859] (II) CHROME(0): VIASwitchMode
[   321.860] (II) CHROME(0): [drm] Cleaning up DMA ring-buffer.
[   321.860] (II) CHROME(0): VIAWriteMode
[   321.860] (II) CHROME(0): ViaModePrimaryLegacy
[   321.860] (II) CHROME(0): Name: 800x600
[   321.860] (II) CHROME(0): Clock: 40000
[   321.860] (II) CHROME(0): VRefresh: 60.316540
[   321.860] (II) CHROME(0): HSync: 37.878788
[   321.860] (II) CHROME(0): HDisplay: 800
[   321.860] (II) CHROME(0): HSyncStart: 840
[   321.860] (II) CHROME(0): HSyncEnd: 968
[   321.860] (II) CHROME(0): HTotal: 1056
[   321.860] (II) CHROME(0): HSkew: 0
[   321.860] (II) CHROME(0): VDisplay: 600
[   321.860] (II) CHROME(0): VSyncStart: 601
[   321.860] (II) CHROME(0): VSyncEnd: 605
[   321.860] (II) CHROME(0): VTotal: 628
[   321.860] (II) CHROME(0): VScan: 0
[   321.860] (II) CHROME(0): Flags: 5
[   321.860] (II) CHROME(0): CrtcHDisplay: 0x320
[   321.860] (II) CHROME(0): CrtcHBlankStart: 0x320
[   321.860] (II) CHROME(0): CrtcHSyncStart: 0x348
[   321.860] (II) CHROME(0): CrtcHSyncEnd: 0x3c8
[   321.860] (II) CHROME(0): CrtcHBlankEnd: 0x420
[   321.860] (II) CHROME(0): CrtcHTotal: 0x420
[   321.860] (II) CHROME(0): CrtcHSkew: 0x0
[   321.860] (II) CHROME(0): CrtcVDisplay: 0x258
[   321.860] (II) CHROME(0): CrtcVBlankStart: 0x258
[   321.860] (II) CHROME(0): CrtcVSyncStart: 0x259
[   321.860] (II) CHROME(0): CrtcVSyncEnd: 0x25d
[   321.860] (II) CHROME(0): CrtcVBlankEnd: 0x274
[   321.860] (II) CHROME(0): CrtcVTotal: 0x274
[   321.860] (II) CHROME(0): ViaFirstCRTCSetMode
[   321.861] (II) CHROME(0): Setting up 800x600
[   321.861] (II) CHROME(0): ViaComputeDotClock 40000 : 515f : 8643
[   321.861] (II) CHROME(0): ViaTVPower: Off.
[   321.861] (II) CHROME(0): ViaSetPrimaryFIFO
[   321.861] (II) CHROME(0): ViaSetPrimaryExpireNumber
[   321.861] (II) CHROME(0): ViaSetDotclock to 0x008643
[   321.861] (II) CHROME(0): ViaSetUseExternalClock
[   321.861] (II) CHROME(0): VIAAdjustFrame 0x0
[   321.861] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[   321.861] (II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
[   321.861] (II) CHROME(0): VIALoadPalette: numColors: 256
[   321.861] (II) CHROME(0): VIAAdjustFrame 0x0
[   321.861] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[   321.861] (II) CHROME(0): VIAAdjustFrame 1x1
[   321.862] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[   321.862] (II) CHROME(0): VIAAdjustFrame 0x0
[   321.862] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[  3422.997] (II) CHROME(0): ViaDisplayDisableCRT
[  3430.501] (II) CHROME(0): ViaDisplayEnableCRT
[  4426.997] (II) CHROME(0): ViaDisplayDisableCRT
[  4843.251] (II) CHROME(0): ViaDisplayEnableCRT
[  6569.997] (II) CHROME(0): ViaDisplayDisableCRT
[  6693.793] (II) CHROME(0): ViaDisplayEnableCRT
[  6770.270] Freed 0 (pool 0)
[  6770.270] Fulfilled via DRI at 7683200
[  6770.270] Freed 0 (pool 0)
[  6770.270] Fulfilled via DRI at 8297600
[  6796.040] Freed 7683200 (pool 2)
[  6796.041] Freed 8297600 (pool 2)
[  6796.628] Freed 7683200 (pool 0)
[  6796.628] Fulfilled via DRI at 7683200
[  6796.634] Freed 8297600 (pool 0)
[  6796.634] Fulfilled via DRI at 8297600
[  8049.845] Freed 7683200 (pool 2)
[  8049.845] Freed 8297600 (pool 2)
[  8050.456] Freed 7683200 (pool 0)
[  8050.456] Fulfilled via DRI at 7683200
[  8050.456] Freed 8297600 (pool 0)
[  8050.456] Fulfilled via DRI at 8297600
[  9552.603] Freed 7683200 (pool 2)
[  9552.603] Freed 8297600 (pool 2)
[  9553.171] Freed 7683200 (pool 0)
[  9553.171] Fulfilled via DRI at 7683200
[  9553.172] Freed 8297600 (pool 0)
[  9553.172] Fulfilled via DRI at 8297600
[ 10912.700] Freed 7683200 (pool 2)
[ 10912.700] Freed 8297600 (pool 2)
[ 10913.548] Freed 7683200 (pool 0)
[ 10913.548] Fulfilled via DRI at 7683200
[ 10913.548] Freed 8297600 (pool 0)
[ 10913.548] Fulfilled via DRI at 8297600
[ 12381.065] Freed 7683200 (pool 2)
[ 12381.065] Freed 8297600 (pool 2)
[ 12381.639] Freed 7683200 (pool 0)
[ 12381.639] Fulfilled via DRI at 7683200
[ 12381.640] Freed 8297600 (pool 0)
[ 12381.640] Fulfilled via DRI at 8297600
[ 13847.455] Freed 7683200 (pool 2)
[ 13847.456] Freed 8297600 (pool 2)
[ 13848.024] Freed 7683200 (pool 0)
[ 13848.024] Fulfilled via DRI at 7683200
[ 13848.025] Freed 8297600 (pool 0)
[ 13848.025] Fulfilled via DRI at 8297600
[ 15197.717] Freed 7683200 (pool 2)
[ 15197.717] Freed 8297600 (pool 2)
[ 15198.554] Freed 7683200 (pool 0)
[ 15198.554] Fulfilled via DRI at 7683200
[ 15198.554] Freed 8297600 (pool 0)
[ 15198.554] Fulfilled via DRI at 8297600
[ 16564.095] Freed 7683200 (pool 2)
[ 16564.095] Freed 8297600 (pool 2)
[ 16564.691] Freed 7683200 (pool 0)
[ 16564.691] Fulfilled via DRI at 7683200
[ 16564.691] Freed 8297600 (pool 0)
[ 16564.691] Fulfilled via DRI at 8297600
[ 17980.457] Freed 7683200 (pool 2)
[ 17980.458] Freed 8297600 (pool 2)
[ 17981.011] Freed 7683200 (pool 0)
[ 17981.011] Fulfilled via DRI at 7683200
[ 17981.012] Freed 8297600 (pool 0)
[ 17981.012] Fulfilled via DRI at 8297600
[ 19318.945] Freed 7683200 (pool 2)
[ 19318.945] Freed 8297600 (pool 2)
[ 19319.580] Freed 7683200 (pool 0)
[ 19319.580] Fulfilled via DRI at 7683200
[ 19319.580] Freed 8297600 (pool 0)
[ 19319.580] Fulfilled via DRI at 8297600
[ 20469.499] Freed 7683200 (pool 2)
[ 20469.499] Freed 8297600 (pool 2)
[ 20470.079] Freed 7683200 (pool 0)
[ 20470.079] Fulfilled via DRI at 7683200
[ 20470.079] Freed 8297600 (pool 0)
[ 20470.079] Fulfilled via DRI at 8297600
[ 21793.684] Freed 7683200 (pool 2)
[ 21793.684] Freed 8297600 (pool 2)
[ 21794.206] Freed 7683200 (pool 0)
[ 21794.206] Fulfilled via DRI at 7683200
[ 21794.207] Freed 8297600 (pool 0)
[ 21794.207] Fulfilled via DRI at 8297600
[ 23066.097] Freed 7683200 (pool 2)
[ 23066.097] Freed 8297600 (pool 2)
[ 23066.672] Freed 7683200 (pool 0)
[ 23066.672] Fulfilled via DRI at 7683200
[ 23066.673] Freed 8297600 (pool 0)
[ 23066.673] Fulfilled via DRI at 8297600
[ 24297.437] Freed 7683200 (pool 2)
[ 24297.437] Freed 8297600 (pool 2)
[ 24298.020] Freed 7683200 (pool 0)
[ 24298.020] Fulfilled via DRI at 7683200
[ 24298.021] Freed 8297600 (pool 0)
[ 24298.023] Fulfilled via DRI at 8297600
[ 25633.746] Freed 7683200 (pool 2)
[ 25633.746] Freed 8297600 (pool 2)
[ 25634.306] Freed 7683200 (pool 0)
[ 25634.306] Fulfilled via DRI at 7683200
[ 25634.307] Freed 8297600 (pool 0)
[ 25634.307] Fulfilled via DRI at 8297600
[ 26736.778] Freed 7683200 (pool 2)
[ 26736.778] Freed 8297600 (pool 2)
[ 26737.656] Freed 7683200 (pool 0)
[ 26737.656] Fulfilled via DRI at 7683200
[ 26737.656] Freed 8297600 (pool 0)
[ 26737.656] Fulfilled via DRI at 8297600
[ 28350.301] Freed 7683200 (pool 2)
[ 28350.301] Freed 8297600 (pool 2)
[ 28350.865] Freed 7683200 (pool 0)
[ 28350.865] Fulfilled via DRI at 7683200
[ 28350.865] Freed 8297600 (pool 0)
[ 28350.865] Fulfilled via DRI at 8297600
[ 29679.686] Freed 7683200 (pool 2)
[ 29679.687] Freed 8297600 (pool 2)
[ 29680.215] Freed 7683200 (pool 0)
[ 29680.215] Fulfilled via DRI at 7683200
[ 29680.215] Freed 8297600 (pool 0)
[ 29680.215] Fulfilled via DRI at 8297600
[ 31387.395] Freed 7683200 (pool 2)
[ 31387.396] Freed 8297600 (pool 2)
[ 31387.927] Freed 7683200 (pool 0)
[ 31387.927] Fulfilled via DRI at 7683200
[ 31387.928] Freed 8297600 (pool 0)
[ 31387.928] Fulfilled via DRI at 8297600
[ 32570.683] Freed 7683200 (pool 2)
[ 32570.683] Freed 8297600 (pool 2)
[ 32571.324] Freed 7683200 (pool 0)
[ 32571.324] Fulfilled via DRI at 7683200
[ 32571.325] Freed 8297600 (pool 0)
[ 32571.325] Fulfilled via DRI at 8297600
[ 33956.613] Freed 7683200 (pool 2)
[ 33956.613] Freed 8297600 (pool 2)
[ 33957.178] Freed 7683200 (pool 0)
[ 33957.178] Fulfilled via DRI at 7683200
[ 33957.179] Freed 8297600 (pool 0)
[ 33957.179] Fulfilled via DRI at 8297600
[ 35348.410] Freed 7683200 (pool 2)
[ 35348.410] Freed 8297600 (pool 2)
[ 35348.971] Freed 7683200 (pool 0)
[ 35348.972] Fulfilled via DRI at 7683200
[ 35348.972] Freed 8297600 (pool 0)
[ 35348.972] Fulfilled via DRI at 8297600
[ 36708.561] Freed 7683200 (pool 2)
[ 36708.561] Freed 8297600 (pool 2)
[ 36709.397] Freed 7683200 (pool 0)
[ 36709.397] Fulfilled via DRI at 7683200
[ 36709.398] Freed 8297600 (pool 0)
[ 36709.398] Fulfilled via DRI at 8297600
[ 38176.961] Freed 7683200 (pool 2)
[ 38176.961] Freed 8297600 (pool 2)
[ 38177.568] Freed 7683200 (pool 0)
[ 38177.568] Fulfilled via DRI at 7683200
[ 38177.568] Freed 8297600 (pool 0)
[ 38177.569] Fulfilled via DRI at 8297600
[ 39643.400] Freed 7683200 (pool 2)
[ 39643.400] Freed 8297600 (pool 2)
[ 39643.973] Freed 7683200 (pool 0)
[ 39643.974] Fulfilled via DRI at 7683200
[ 39643.974] Freed 8297600 (pool 0)
[ 39643.974] Fulfilled via DRI at 8297600

```

Also, when I plug in my monitor it shows up as "unknown". I don't know if it was doing that before, or whether I had an xorg.conf to begin with, because I didn't explore that part of the system.

---

### Post by Yellow Pasque on 2011-06-12
Try using this for your /etc/X11/xorg.conf file:
```
Section "Monitor"
  Identifier   "Monitor[0]"
  HorizSync 30 - 82
  VertRefresh 50 - 75
EndSection

Section "Device"
  Driver       "openchrome"
  Identifier   "Device[0]"
EndSection

Section "Screen"
  SubSection "Display"
    Depth      24
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection
```

---

### Post by SketchMan3 on 2011-06-12
So I create an "xorg.conf" file and paste that into it? 

Edit: Then do I have to restart?

---

### Post by Yellow Pasque on 2011-06-12
> So I create an "xorg.conf" file and paste that into it? 
Yes.
```
gksu gedit /etc/X11/xorg.conf
```
Copy/paste, save the file, and log out to restart the Xserver.

---

### Post by SketchMan3 on 2011-06-12
Thanks, that did it! =D

I'm so glad it was such a simple solution. Thank God, lol.

---


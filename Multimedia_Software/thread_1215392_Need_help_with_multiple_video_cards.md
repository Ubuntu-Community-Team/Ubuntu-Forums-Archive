---
title: "Need help with multiple video cards"
date: 2009-07-17
forum: Multimedia Software
---

### Post by w23 on 2009-07-17
So a few days ago, I got a nice projector for watching videos coming from my computer.  After about an hour of tweaking my xorg.conf, I finally got it to work.  Only, I'm using the second port on my Nvidia Quadro 900XGL, which is normally plugged into my secondary monitor.  So I searched ebay and bought a Matrox G450 and figured I could throw it in and use one of the four DVI outputs for the projector.  

Well, didn't turn out to be that easy.  From what I can tell searching the forums, using multiple grahpics cards isn't very easy.  Anyway, first few attempts kept crashing X and gave me "MGA(0): cannot read VGA_BIOS".  Some googling told me that this is due to a bios bug that limits OS access to only one card at a time.  I checked my bios and sure enough, I can select between AGP (nvidia card) and PCI (Matrox card).  Ignoring the error, I played with xorg.conf some more and eventually got X to start, only the screen went black and ctrl-alt-f1 stopped responding.  I checked the feed from both cards and they were both blank.  However, I can still SSH in and ps shows X still running.  Killing X doesn't fix ctrl-alt-f1, only a reboot will.

xorg.conf

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    Screen    2  "Screen2" LeftOf "Screen1"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "AIGLX" "true"
EndSection

Section "Files"
    ModulePath      "/usr/lib/xorg/modules"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "extmod"
    Load           "dbe"
    Load           "glx"
    Load           "record"
    Load           "xtrap"
    Load           "type1"
    Load           "nvidia"
EndSection

Section "ServerFlags"
    Option         "DontZap" "False"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "PTS"
    ModelName      "770"
    HorizSync       30.0 - 80.0
    VertRefresh     60.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    Option  "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    #ModeLine       "1024x768" 65.0 1024 1048 1184 1344 768 771 777 806
EndSection

Section "Device"
    Identifier     "Card0"
    Driver         "nvidia"
    VendorName     "nVidia Corporation"
    BoardName      "NV28GL [Quadro4 980 XGL]"
    BusID          "AGP:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Card1"
    Driver         "nvidia"
    BusID          "AGP:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier  "Card2"
        Driver      "mga"  
        VendorName  "Matrox Graphics, Inc."
        BoardName   "MGA G400/G450"
        BusID       "PCI:4:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Card0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "FlatPanel" "True"
    Option         "XAANoOffscreenPixmaps" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "TripleBuffer" "true"
    Option         "NvAGP" "1"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Viewport    0 0
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection

Section "Screen"

    #Option         "AddARGBGLXVisuals" "True"
    #Option         "NvAGP" "1"
    #Option         "NoLogo" "True"
    Identifier     "Screen1"
    Device         "Card1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Viewport    0 1
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

Section "Screen"
        Identifier "Screen2"
        Device     "Card2"  
        Monitor    "Monitor2"
        SubSection "Display" 
                Viewport   0 0
                Depth     24  
        EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "enable"
EndSection
```Xorg.0.log

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux novaprospeckt 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 17 02:21:32 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Card1"
(**) |-->Screen "Screen2" (2)
(**) |   |-->Monitor "Monitor2"
(**) |   |-->Device "Card2"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "DontZap" "False"
(**) Option "AIGLX" "true"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 2

(--) PCI:*(0@1:0:0) nVidia Corporation NV28GL [Quadro4 980 XGL] rev 161, Mem @ 0xf5000000/16777216, 0xd8000000/134217728, BIOS @ 0x????????/131072
(--) PCI: (0@4:0:0) Matrox Graphics, Inc. MGA G400/G450 rev 133, Mem @ 0xe0000000/33554432, 0xe8000000/16384, 0xe9000000/8388608, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  96.43.10  Sat Jan 24 20:04:30 PST 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "xtrap"
(WW) Warning, couldn't open module xtrap
(II) UnloadModule: "xtrap"
(EE) Failed to load module "xtrap" (module does not exist, 0)
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Reloading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) UnloadModule: "nvidia"
(II) Failed to load module "nvidia" (already loaded, 158941024)
(II) LoadModule: "mga"
(II) Loading /usr/lib/xorg/modules/drivers//mga_drv.so
(II) Module mga: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 1.4.9
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) NVIDIA dlloader X Driver  96.43.10  Sat Jan 24 19:52:47 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) MGA: driver for Matrox chipsets: mga2064w, mga1064sg, mga2164w,
    mga2164w AGP, mgag100, mgag100 PCI, mgag200, mgag200 PCI,
    mgag200 SE A PCI, mgag200 SE B PCI, mgag200 Maxim, mgag200 Winbond,
    mgag400, mgag550
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] 1    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [5] 1    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [6] 1    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [9] 1    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [10] 1    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 2.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "NvAGP" "1"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Option "TripleBuffer" "true"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Use of NVIDIA internal AGP requested
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU Quadro4 980 XGL at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.28.20.19.15
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on Quadro4 980 XGL at PCI:1:0:0:
(--) NVIDIA(0):     Proview (CRT-0)
(--) NVIDIA(0):     Gateway (CRT-1)
(--) NVIDIA(0): Proview (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Gateway (CRT-1): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1440x900"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(WW) NVIDIA(0): UBB is incompatible with the Composite extension.  Disabling
(WW) NVIDIA(0):     UBB.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU Quadro4 980 XGL at PCI:1:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 131072 kBytes
(--) NVIDIA(1): VideoBIOS: 04.28.20.19.15
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on Quadro4 980 XGL at PCI:1:0:0:
(--) NVIDIA(1):     Proview (CRT-0)
(--) NVIDIA(1):     Gateway (CRT-1)
(--) NVIDIA(1): Proview (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(1): Gateway (CRT-1): 350.0 MHz maximum pixel clock
(II) NVIDIA(1): Assigned Display Device: CRT-1
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "1024x768"
(II) NVIDIA(1): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(1): DPI set to (89, 92); computed from "UseEdidDpi" X config
(--) NVIDIA(1):     option
(WW) NVIDIA(1): UBB is incompatible with the Composite extension.  Disabling
(WW) NVIDIA(1):     UBB.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(--) MGA(2): Chipset: "mgag400" (G450)
(==) MGA(2): Depth 24, (--) framebuffer bpp 32
(==) MGA(2): RGB weight 888
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) MGA(2): Initializing int10
(EE) MGA(2): Cannot read V_BIOS (3) Input/output error
(==) MGA(2): Using AGP 1x mode
(==) MGA(2): Using HW cursor
(==) MGA(2): Using XAA acceleration
(--) MGA(2): Linear framebuffer at 0xE0000000
(--) MGA(2): MMIO registers at 0xE8000000
(--) MGA(2): Pseudo-DMA transfer window at 0xE9000000
(WW) MGA(2): Could not retrieve video BIOS!
(--) MGA(2): VideoRAM: 2048 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) MGA(2): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) MGA(2): DDC1 disabled - chip not in VGA mode
(II) MGA(2): I2C bus "DDC P1" initialized.
(II) MGA(2): I2C device "DDC P1:E-EDID segment register" registered at address 0x60.
(II) MGA(2): I2C device "DDC P1:ddc2" registered at address 0xA0.
(II) MGA(2): I2C Monitor info: (nil)
(II) MGA(2): end of I2C Monitor info
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) MGA(2): initializing int10
(EE) MGA(2): Cannot read V_BIOS (3) Input/output error
(==) MGA(2): Using gamma correction (1.0, 1.0, 1.0)
(==) MGA(2): Min pixel clock is 17 MHz
(--) MGA(2): Max pixel clock is 252 MHz
(II) MGA(2): Monitor2: Using default hsync range of 31.50-37.90 kHz
(II) MGA(2): Monitor2: Using default vrefresh range of 50.00-70.00 Hz
(WW) MGA(2): Unable to estimate virtual size
(II) MGA(2): Clock range:  17.75 to 252.00 MHz
(II) MGA(2): Not using default mode "640x350" (vrefresh out of range)
(II) MGA(2): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) MGA(2): Not using default mode "640x400" (vrefresh out of range)
(II) MGA(2): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) MGA(2): Not using default mode "720x400" (vrefresh out of range)
(II) MGA(2): Not using default mode "360x200" (vrefresh out of range)
(II) MGA(2): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(2): Not using default mode "640x480" (vrefresh out of range)
(II) MGA(2): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(2): Not using default mode "640x480" (vrefresh out of range)
(II) MGA(2): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(2): Not using default mode "640x480" (hsync out of range)
(II) MGA(2): Not using default mode "320x240" (hsync out of range)
(II) MGA(2): Not using default mode "800x600" (hsync out of range)
(II) MGA(2): Not using default mode "400x300" (hsync out of range)
(II) MGA(2): Not using default mode "800x600" (hsync out of range)
(II) MGA(2): Not using default mode "400x300" (hsync out of range)
(II) MGA(2): Not using default mode "800x600" (hsync out of range)
(II) MGA(2): Not using default mode "400x300" (hsync out of range)
(II) MGA(2): Not using default mode "1024x768" (insufficient memory for mode)
(II) MGA(2): Not using default mode "512x384" (vrefresh out of range)
(II) MGA(2): Not using default mode "1024x768" (insufficient memory for mode)
(II) MGA(2): Not using default mode "512x384" (hsync out of range)
(II) MGA(2): Not using default mode "1024x768" (insufficient memory for mode)
(II) MGA(2): Not using default mode "512x384" (hsync out of range)
(II) MGA(2): Not using default mode "1024x768" (insufficient memory for mode)
(II) MGA(2): Not using default mode "512x384" (hsync out of range)
(II) MGA(2): Not using default mode "1024x768" (insufficient memory for mode)
(II) MGA(2): Not using default mode "512x384" (hsync out of range)
(II) MGA(2): Not using default mode "1152x864" (insufficient memory for mode)
(II) MGA(2): Not using default mode "576x432" (hsync out of range)
(II) MGA(2): Not using default mode "1280x960" (insufficient memory for mode)
(II) MGA(2): Not using default mode "640x480" (hsync out of range)
(II) MGA(2): Not using default mode "1280x960" (insufficient memory for mode)
(II) MGA(2): Not using default mode "640x480" (hsync out of range)
(II) MGA(2): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MGA(2): Not using default mode "640x512" (hsync out of range)
(II) MGA(2): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MGA(2): Not using default mode "640x512" (hsync out of range)
(II) MGA(2): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MGA(2): Not using default mode "640x512" (hsync out of range)
(II) MGA(2): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MGA(2): Not using default mode "800x600" (hsync out of range)
(II) MGA(2): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MGA(2): Not using default mode "800x600" (hsync out of range)
(II) MGA(2): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MGA(2): Not using default mode "800x600" (hsync out of range)
(II) MGA(2): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MGA(2): Not using default mode "800x600" (hsync out of range)
(II) MGA(2): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MGA(2): Not using default mode "800x600" (hsync out of range)
(II) MGA(2): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MGA(2): Not using default mode "896x672" (insufficient memory for mode)
(II) MGA(2): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MGA(2): Not using default mode "896x672" (insufficient memory for mode)
(II) MGA(2): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MGA(2): Not using default mode "928x696" (insufficient memory for mode)
(II) MGA(2): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MGA(2): Not using default mode "928x696" (insufficient memory for mode)
(II) MGA(2): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MGA(2): Not using default mode "960x720" (insufficient memory for mode)
(II) MGA(2): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MGA(2): Not using default mode "960x720" (insufficient memory for mode)
(II) MGA(2): Not using default mode "832x624" (hsync out of range)
(II) MGA(2): Not using default mode "416x312" (hsync out of range)
(II) MGA(2): Not using default mode "1152x864" (insufficient memory for mode)
(II) MGA(2): Not using default mode "576x432" (hsync out of range)
(II) MGA(2): Not using default mode "1152x864" (insufficient memory for mode)
(II) MGA(2): Not using default mode "576x432" (hsync out of range)
(II) MGA(2): Not using default mode "1152x864" (insufficient memory for mode)
(II) MGA(2): Not using default mode "576x432" (hsync out of range)
(II) MGA(2): Not using default mode "1152x864" (insufficient memory for mode)
(II) MGA(2): Not using default mode "576x432" (hsync out of range)
(II) MGA(2): Not using default mode "1152x864" (insufficient memory for mode)
(II) MGA(2): Not using default mode "576x432" (hsync out of range)
(II) MGA(2): Not using default mode "1152x864" (insufficient memory for mode)
(II) MGA(2): Not using default mode "576x432" (hsync out of range)
(II) MGA(2): Not using default mode "1360x768" (insufficient memory for mode)
(II) MGA(2): Not using default mode "680x384" (hsync out of range)
(II) MGA(2): Not using default mode "1360x768" (insufficient memory for mode)
(II) MGA(2): Not using default mode "680x384" (hsync out of range)
(II) MGA(2): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MGA(2): Not using default mode "700x525" (hsync out of range)
(II) MGA(2): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MGA(2): Not using default mode "700x525" (hsync out of range)
(II) MGA(2): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MGA(2): Not using default mode "700x525" (hsync out of range)
(II) MGA(2): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MGA(2): Not using default mode "700x525" (hsync out of range)
(II) MGA(2): Not using default mode "1440x900" (insufficient memory for mode)
(II) MGA(2): Not using default mode "720x450" (hsync out of range)
(II) MGA(2): Not using default mode "1600x1024" (insufficient memory for mode)
(II) MGA(2): Not using default mode "800x512" (hsync out of range)
(II) MGA(2): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MGA(2): Not using default mode "840x525" (hsync out of range)
(II) MGA(2): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MGA(2): Not using default mode "840x525" (hsync out of range)
(II) MGA(2): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MGA(2): Not using default mode "840x525" (hsync out of range)
(II) MGA(2): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MGA(2): Not using default mode "840x525" (hsync out of range)
(II) MGA(2): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MGA(2): Not using default mode "840x525" (hsync out of range)
(II) MGA(2): Not using default mode "1920x1080" (insufficient memory for mode)
(II) MGA(2): Not using default mode "960x540" (hsync out of range)
(II) MGA(2): Not using default mode "1920x1200" (insufficient memory for mode)
(II) MGA(2): Not using default mode "960x600" (insufficient memory for mode)
(II) MGA(2): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MGA(2): Not using default mode "960x720" (insufficient memory for mode)
(II) MGA(2): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MGA(2): Not using default mode "1024x768" (insufficient memory for mode)
(II) MGA(2): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MGA(2): Not using default mode "1024x768" (insufficient memory for mode)
(II) MGA(2): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MGA(2): Not using default mode "1024x768" (insufficient memory for mode)
(--) MGA(2): Virtual size is 800x600 (pitch 800)
(**) MGA(2): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MGA(2): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) MGA(2): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) MGA(2): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) MGA(2): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MGA(2): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MGA(2): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) MGA(2): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) MGA(2): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) MGA(2): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(==) MGA(2): DPI set to (96, 96)
(II) MGA(2): YDstOrg is set to 0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules//libfb.so
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.2.1
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] 1    0    0x000a0000 - 0x000affff (0x10000) MS[b](OprD)
    [5] 1    0    0x000b0000 - 0x000b7fff (0x8000) MS[b](OprD)
    [6] 1    0    0x000b8000 - 0x000bffff (0x8000) MS[b](OprD)
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [9] 1    0    0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
    [10] 1    0    0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "1440x900"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "FlatPanel" is not used
(WW) NVIDIA(0): Option "XAANoOffscreenPixmaps" is not used
(==) RandR enabled
(II) NVIDIA(1): Initialized GART.
(II) NVIDIA(1): Setting mode "1024x768"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(1): DPMS enabled
(==) RandR enabled
(II) MGA(2): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
```I'm running Jaunty.

---


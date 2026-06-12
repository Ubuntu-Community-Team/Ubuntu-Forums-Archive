---
title: "Tablet/All in One w/ Intel 855 Screen Fades to White"
date: 2009-08-24
forum: Multimedia Software
---

### Post by lorsungcu on 2009-08-24
I have a tablet with an intel 855 adapter.  I installed Ubuntu Netbook on it.  Booting is fine, until it tries to load X, at which point the screen goes black, then fades into white and back to black.  Occasionally you can see the cursor for brief periods.  Loading the standard VESA driver will let me into gdm, but it is not useable.  

Output of uname -a:

```

Linux route61 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

```Output of sudo lshw -C display:

```

$ sudo lshw -C display
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

```Output of lspci  | grep VGA:

```

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

```Here is the xorg.conf I created for it:

```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "TouchScreen"
EndSection

Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        VideoRam        130560
        Option          "AccelMethod"                   "UXA"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
    Modeline "1024x768@60" 64.56 1024 1056 1296 1328 768 783 791 807
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation 82852/855GM Integrated Graphics Device"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection "Display"
        Depth        16                                                                                                                             
        Virtual        1024 768
    EndSubSection
EndSection

Section "InputDevice"
    Identifier "TouchScreen"
    Driver "mutouch"
    Option "Type" "finger"
    Option "Device" "/dev/ttyS1"
    Option "ScreenNo" "0"
    Option "MinX" "0"
    Option "MaxX" "16383"
    Option "MinY" "0"
    Option "MaxY" "16383"
    Option "SendCoreEvents" "yes"
EndSection

```And here is /var/log/Xorg.0.log:

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux route61 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 24 20:58:26 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Intel Corporation 82852/855GM Integrated Graphics Device"
(**) |-->Input Device "TouchScreen"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xd8000000/134217728, 0xe8180000/524288, I/O @ 0x0000e300/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
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
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
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
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.7.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "mutouch"
(II) Loading /usr/lib/xorg/modules/input//mutouch_drv.so
(II) Module mutouch: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.2.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, IGD_GM, IGD_G, 965G, G35,
    965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    Mobile Intel® GM45 Express Chipset,
    Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
(II) Primary Device is: PCI 00@00:02:0
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
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) intel(0): Depth 16, (--) framebuffer bpp 16
(==) intel(0): RGB weight 565
(==) intel(0): Default visual is TrueColor
(**) intel(0): Option "AccelMethod" "UXA"
(II) intel(0): Integrated Graphics Chipset: Intel(R) 855GME
(--) intel(0): Chipset: "852GM/855GM"
(--) intel(0): Linear framebuffer at 0xD8000000
(--) intel(0): IO registers at addr 0xE8180000
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(**) intel(0): Using UXA for acceleration
(II) intel(0): 2 display pipes available.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Generic Monitor
(II) intel(0): I2C bus "DVODDC_D" initialized.
(II) Loading sub module "sil164"
(II) LoadModule: "sil164"
(II) Loading /usr/lib/xorg/modules/drivers//sil164.so
(II) Module sil164: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) intel(0): I2C device "DVOI2C_E:SIL164 TMDS Controller" registered at address 0x70.
(II) intel(0): Output TMDS has no monitor section
(II) intel(0): Resizable framebuffer: available (1 4)
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C device "DVODDC_D:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "DVODDC_D:ddc2" registered at address 0xA0.
(II) intel(0): Output VGA disconnected
(II) intel(0): Output TMDS connected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output TMDS using initial mode 1024x768
(II) intel(0): detected 128 kB GTT.
(II) intel(0): detected 32636 kB stolen memory.
(==) intel(0): video overlay key set to 0x83e
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) intel(0): Comparing regs from server start up to After PreInit
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b](OprD)
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b](OprD)
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b](OprD)
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(WW) intel(0): VideoRam configuration found, which is no longer recommended.
(II) intel(0): Continuing with default 131072kB VideoRam instead of 130560 kB.
(II) intel(0): Kernel reported 45056 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 180220 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(**) intel(0): VideoRam: 131072 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(WW) intel(0): xf86AllocateGARTMemory: allocation of 1536 pages failed
    (Cannot allocate memory)
(WW) intel(0): Allocation error, framebuffer compression disabled
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
    (Cannot allocate memory)
(II) intel(0): Tiled allocation successful.
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(WW) intel(0): drmDropMaster failed: Unknown error 4294967295
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x079f4000 (pgoffset 31220)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x079f5000 (pgoffset 31221)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x079f9000 (pgoffset 31225)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x079fa000 (pgoffset 31226)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x079fe000 (pgoffset 31230)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x01fdf000:            end of stolen memory
(II) intel(0): 0x01fdf000-0x079f3fff: DRI memory manager (92244 kB)
(II) intel(0): 0x079f4000-0x079f4fff: Core cursor (4 kB, 0x000000000bca5000 physical
)
(II) intel(0): 0x079f5000-0x079f8fff: ARGB cursor (16 kB, 0x000000000cee8000 physical
)
(II) intel(0): 0x079f9000-0x079f9fff: Core cursor (4 kB, 0x000000000bca9000 physical
)
(II) intel(0): 0x079fa000-0x079fdfff: ARGB cursor (16 kB, 0x000000000bcb0000 physical
)
(II) intel(0): 0x079fe000-0x079fefff: overlay registers (4 kB, 0x000000000bc9c000 physical
)
(II) intel(0): 0x08000000:            end of aperture
(II) intel(0): BO memory allocation layout:
(II) intel(0): 0x01fdf000:            start of memory manager
(II) intel(0): 0x02000000-0x021fffff: front buffer (2048 kB) X tiled
(II) intel(0): 0x079f4000:            end of memory manager
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output TMDS is connected to pipe A
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(**) Option "dpms"
(**) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
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
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 270 x 203
(**) MicroTouch FINGER input device: /dev/ttyS1
(**) Option "SendCoreEvents" "yes"
(**) FINGER: always reports core events
(**) Microtouch X device name: FINGER
(**) Option "ScreenNo" "0"
(**) Microtouch associated screen: 0
(**) Option "MaxX" "16383"
(**) Microtouch maximum x position: 16383
(**) Option "MinX" "0"
(**) Microtouch minimum x position: 0
(**) Option "MaxY" "16383"
(**) Microtouch maximum y position: 16383
(**) Option "MinY" "0"
(**) Microtouch minimum y position: 0
(**) Microtouch ThruGlass frequency is: 0
(**) Microtouch device will work in Landscape mode
(II) XINPUT: Adding extended input device "FINGER" (type: MicroTouch Finger)
(**) Option "Device" "/dev/ttyS1"
(**) Option "BaudRate" "9600"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "10"
(**) Option "Vtime" "1"
(**) Option "FlowControl" "None"
(--) MicroTouch touchscreen is a , connected through a serial port.
(--) MicroTouch controller firmware revision is 1.6.
(--) MicroTouch status of errors: 00.
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device HID 04d9:1203
(**) HID 04d9:1203: always reports core events
(**) HID 04d9:1203: Device: "/dev/input/event4"
(II) HID 04d9:1203: Found keys
(II) HID 04d9:1203: Configuring as keyboard
(II) XINPUT: Adding extended input device "HID 04d9:1203" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) HID 04d9:1203: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) HID 04d9:1203: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) HID 04d9:1203: xkb_layout: "us"
(II) config/hal: Adding input device HID 04d9:1203
(**) HID 04d9:1203: always reports core events
(**) HID 04d9:1203: Device: "/dev/input/event5"
(II) HID 04d9:1203: Found keys
(II) HID 04d9:1203: Configuring as keyboard
(II) XINPUT: Adding extended input device "HID 04d9:1203" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) HID 04d9:1203: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) HID 04d9:1203: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) HID 04d9:1203: xkb_layout: "us"
(II) config/hal: Adding input device HID 1241:1177
(**) HID 1241:1177: always reports core events
(**) HID 1241:1177: Device: "/dev/input/event3"
(II) HID 1241:1177: Found 3 mouse buttons
(II) HID 1241:1177: Found x and y relative axes
(II) HID 1241:1177: Configuring as mouse
(**) HID 1241:1177: YAxisMapping: buttons 4 and 5
(**) HID 1241:1177: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HID 1241:1177" (type: MOUSE)
(**) HID 1241:1177: (accel) keeping acceleration scheme 1
(**) HID 1241:1177: (accel) filter chain progression: 2.00
(**) HID 1241:1177: (accel) filter stage 0: 20.00 ms
(**) HID 1241:1177: (accel) set acceleration profile 0
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_D" initialized.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_D:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_D:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_D" removed.
(II) intel(0): I2C bus "CRTDDC_E" initialized.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_E:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_E:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_E" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_D" initialized.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_D:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_D:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_D" removed.
(II) intel(0): I2C bus "CRTDDC_E" initialized.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_E:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_E:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_E" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_D" initialized.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_D:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_D:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_D" removed.
(II) intel(0): I2C bus "CRTDDC_E" initialized.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_E:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_E:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_E" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_D" initialized.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_D:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_D:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_D" removed.
(II) intel(0): I2C bus "CRTDDC_E" initialized.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_E:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_E:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_E" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_D" initialized.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_D:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_D:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_D" removed.
(II) intel(0): I2C bus "CRTDDC_E" initialized.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_E:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_E:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_E" removed.

```Here is xorg.conf after  sudo dpkg-reconfigure -phigh xserver-xorg:

```

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```And the log after booting with VESA:

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux route61 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 24 21:03:51 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7
(--) PCI:*(0@0:2:0) Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xd8000000/134217728, 0xe8180000/524288, I/O @ 0x0000e300/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
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
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
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
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 1.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) VESA(0): initializing int10
(II) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 32576 kB
(II) VESA(0): VESA VBE OEM: Intel(r)852MG/852MGE/855MG/855MGE Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r)852MG/852MGE/855MG/855MGE Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 17c (0x0)
    ModeAttributes: 0x0
    WinAAttributes: 0x0
    WinBAttributes: 0x0
    WinGranularity: 0
    WinSize: 0
    WinASegment: 0x0
    WinBSegment: 0x0
    WinFuncPtr: 0x0
    BytesPerScanline: 0
    XResolution: 0
    YResolution: 0
    XCharSize: 0
    YCharSize: 0
    NumberOfPlanes: 0
    BitsPerPixel: 0
    NumberOfBanks: 0
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 0
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 0

## TRUNCATED
(II) VESA(0): Total Memory: 509 64KB banks (32576kB)
(II) VESA(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(WW) VESA(0): No valid modes left. Trying less strict filter...
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 32576 kB
(II) VESA(0): VESA VBE OEM: Intel(r)852MG/852MGE/855MG/855MGE Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r)852MG/852MGE/855MG/855MGE Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): virtual address = 0xb5775000,
    physical address = 0xd8000000, size = 33357824
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
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
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device HID 04d9:1203
(**) HID 04d9:1203: always reports core events
(**) HID 04d9:1203: Device: "/dev/input/event4"
(II) HID 04d9:1203: Found keys
(II) HID 04d9:1203: Configuring as keyboard
(II) XINPUT: Adding extended input device "HID 04d9:1203" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) HID 04d9:1203: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) HID 04d9:1203: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) HID 04d9:1203: xkb_layout: "us"
(II) config/hal: Adding input device HID 04d9:1203
(**) HID 04d9:1203: always reports core events
(**) HID 04d9:1203: Device: "/dev/input/event5"
(II) HID 04d9:1203: Found keys
(II) HID 04d9:1203: Configuring as keyboard
(II) XINPUT: Adding extended input device "HID 04d9:1203" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) HID 04d9:1203: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) HID 04d9:1203: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) HID 04d9:1203: xkb_layout: "us"
(II) config/hal: Adding input device HID 1241:1177
(**) HID 1241:1177: always reports core events
(**) HID 1241:1177: Device: "/dev/input/event3"
(II) HID 1241:1177: Found 3 mouse buttons
(II) HID 1241:1177: Found x and y relative axes
(II) HID 1241:1177: Configuring as mouse
(**) HID 1241:1177: YAxisMapping: buttons 4 and 5
(**) HID 1241:1177: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HID 1241:1177" (type: MOUSE)
(**) HID 1241:1177: (accel) keeping acceleration scheme 1
(**) HID 1241:1177: (accel) filter chain progression: 2.00
(**) HID 1241:1177: (accel) filter stage 0: 20.00 ms
(**) HID 1241:1177: (accel) set acceleration profile 0

```I've never completely grasped xorg configuration files, but i'm determined to get this going, as I have some money invested at this point :)  Any help would be really appreciated.  If you can get me up and running tonight, a paypal thanks will be yours.

Thanks
Cullen

---

### Post by lorsungcu on 2009-08-25
anyone?  suggestions?  I know i've seen this problem elsewhere, someone must have some insight.

---

### Post by lorsungcu on 2009-08-25
Attempted to use X to reconfigure my xorg.conf file.  Here is the result of sudo X -configure:

```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
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
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load  "glx"
    Load  "record"
    Load  "dri"
    Load  "dri2"
    Load  "dbe"
    Load  "extmod"
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
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82852/855GM Integrated Graphics Device"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card1"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82852/855GM Integrated Graphics Device"
    BusID       "PCI:0:2:1"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"

    SubSection "Display"
        Depth 24
        Modes "1024x768"
        Virtual 2048 2048
    EndSubSection

EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"

        SubSection "Display"
                Depth 24
                Modes "1024x768"
                Virtual 2048 2048
        EndSubSection

EndSection

```The screen sections used to have about 8 entries of this:

```

        SubSection "Display"
                Depth 24
                Modes 0 0
        EndSubSection

```or similar.  After looking around a bit i found someone with a similar problem had luck with my current configuration so i tried that.  No luck.  I've tried the intel and intel 2.4 drivers with no difference in output.  Does anyone have any ideas? 
I noticed a few lines in the /var/log/Xorg.0.log file:

```

(EE) intel(1): No valid FB address in PCI config space
(EE) AIGLX error: drmMap of framebuffer failed (Invalid argument)(EE) AIGLX: reverting to software rendering
(EE) intel(0): underrun on pipe A!

```Googling these doesn't yield any pertinent fixes, or anything I haven't tried.  I don't think, anyway.  I will try booting with an earlier kernel and see what happens.

---

### Post by lorsungcu on 2009-08-27
Bump.  Anyone have ANYTHING?  Am I missing something?

---

### Post by lorsungcu on 2009-09-11
I filed a bug report, but i'm still really needing this to work.  Does anyone have any insight?  or a similar problem?

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/425992](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/425992)

---


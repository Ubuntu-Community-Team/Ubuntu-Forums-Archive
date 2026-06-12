---
title: "Screen resolution gets reset to 800x600"
date: 2009-12-30
forum: Mythbuntu
---

### Post by yzfr1 on 2009-12-30
I recently upgraded to 9.10 and I now my resolution is getting automatically set to 800x600.

I am using a HDTV through a DVI connection with max 1080i resolution.

I have tried disabling many options to get this to work.  I spent a long time on 9.04 to get my tv to work with mythbuntu and I don't want to spend another several months to get it work right..  please help someone..

Here is the last part of my xorg log.

```
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[b]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "UseEDID" "FALSE"
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP"
(**) NVIDIA(0): Option "UseEdidFreqs" "FALSE"
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1920x1080_60 +0+0; 1024x768_60 +0+0"
(**) NVIDIA(0): Option "ExactModeTimingsDVI" "TRUE"
(**) NVIDIA(0): Option "DPI" "96 x 96"
(**) NVIDIA(0): Option "ModeValidation" "NoHorizSyncCheck,NoVertRefreshCheck,NoTotalSizeCheck,NoVirtualSizeCheck,NoMaxSizeCheck,AllowInterlacedModes"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(**) NVIDIA(0): ConnectedMonitor string: "DFP"
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(GPU-0): Not probing EDID on DFP-0.
(II) NVIDIA(0): NVIDIA GPU GeForce 7900 GT/GTO (G71) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.71.22.12.03
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7900 GT/GTO at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Single Link TMDS
(II) NVIDIA(0): Mode Validation Overrides for DFP-0:
(II) NVIDIA(0):     AllowInterlacedModes
(II) NVIDIA(0):     NoMaxSizeCheck
(II) NVIDIA(0):     NoHorizSyncCheck
(II) NVIDIA(0):     NoVertRefreshCheck
(II) NVIDIA(0):     NoVirtualSizeCheck
(II) NVIDIA(0):     NoTotalSizeCheck
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1920x1080_60+0+0"
(II) NVIDIA(0):     "1024x768_60+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(**) NVIDIA(0): DPI set to (96, 96); computed from "DPI" X config option
(==) NVIDIA(0): Disabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[b]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "1920x1080_60+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(WW) NVIDIA(0): Option "NoVirtualSizeCheck" is not used
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
(II) Initializing extension GLX
(II) config/hal: Adding input device Logitech USB Receiver
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 2.2.5
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0

(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found 12 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
(II) Logitech USB Receiver: initialized for relative axes.
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
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
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) NVIDIA(0): Setting mode "800x600"
```
xorg.conf file .. (re-written several times by nvidia-settings)
```
Section "Monitor"
        Identifier     "Configured Monitor"
        DisplaySize     487    274
        ModeLine       "ATSC-720-59.94p" 73.69 1280 1312 1592 1624 720 735 742 757
        ModeLine       "ATSC-1080-59.94i" 74.176 1920 1960 2016 2200 1080 1082 1088 1125 interlace
EndSection

Section "Monitor"
        Identifier     "Monitor0"
        VendorName     "Unknown"
        ModelName      "DFP-0"
        ModeLine       "ATSC-1080-59.94i" 74.176 1920 1960 2016 2200 1080 1082 1088 1125 interlace +vsync +hsync
        #HorizSync       28.0 - 33.0
        #VertRefresh     43.0 - 72.0
EndSection

Section "Screen"
        Identifier     "Default Screen"
        Device         "Configured Video Device"
        Monitor        "Configured Monitor"
        Option         "NoLogo" "True"
        Option         "ConnectedMonitor" "DFP"
        Option  "AddARGBGLXVisuals"     "True"
        DefaultDepth    24
        SubSection "Display"
                Depth       24
                Modes      "ATSC-1080-59.94i"
        EndSubSection
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Device0"
        Monitor        "Monitor0"
        DefaultDepth    24
        Option         "ConnectedMonitor" "DFP"
        Option         "UseEDIDFreqs" "FALSE"
        Option     "NoVirtualSizeCheck"
        Option         "ExactModeTimingsDVI" "TRUE"
        Option         "TwinView" "0"
        Option         "DPI" "96 x 96"
        Option         "metamodes" "1920x1080_60 +0+0; 1024x768_60 +0+0"
        Option         "ModeValidation" "NoHorizSyncCheck,NoVertRefreshCheck,NoTotalSizeCheck,NoVirtualSizeCheck,NoMaxSizeCheck,AllowInterlacedModes"
        # Removed Option "metamodes" "DFP: 1920x1080 +0+0"
        # Removed Option "metamodes" "1024x768d60 +0+0"
        # Removed Option "metamodes" "1280x720d60 +0+0"
        # Removed Option "metamodes" "1024x768_60 +0+0; 1920x1080_60 +0+0"
        SubSection "Display"
                Depth       24
                Modes       "ATSC-1080-59.94i"
        EndSubSection
EndSection

Section "Module"
        Load           "glx"
EndSection

Section "InputDevice"
        Identifier     "Keyboard0"
        Driver         "kbd"
EndSection

Section "InputDevice"
        Identifier     "Mouse0"
        Driver         "mouse"
        Option         "Protocol" "auto"
        Option         "Device" "/dev/psaux"
        Option         "Emulate3Buttons" "no"
        Option         "ZAxisMapping" "4 5"
        # generated from default
EndSection

Section "Extensions"
        Option         "Composite" "Disable"
EndSection

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "Screen0" 0 0
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Mouse0" "CorePointer"
# commented out by update-manager, HAL is now used and auto-detects devices
        # Keyboard settings are now read from /etc/default/console-setup
        #       InputDevice    "Keyboard0" "CoreKeyboard"
        # commented out by update-manager, HAL is now used and auto-detects devices
        # Keyboard settings are now read from /etc/default/console-setup
        #       InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
        Identifier     "Configured Video Device"
        Driver         "nvidia"
        Option         "DPI" "96 x 96"
        Option         "UseEDIDFreqs" "FALSE"
        Option         "ExactModeTimingsDVI" "TRUE"
        Option         "ModeValidation" "NoHorizSyncCheck"
        Option         "NoLogo" "True"
        #Option          "UseEDIDDpi" "FALSE"
        #Option          "ModeValidation" "NoEdidModes"
        #Option "MetaModes"     "ATSC-1080-59.94i"
EndSection

Section "Device"
        Identifier     "Device0"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce 7900 GT/GTO"
        Option     "UseEdid" "FALSE"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

Section "ServerFlags"
        Option         "Xinerama" "0"
EndSection
```

---


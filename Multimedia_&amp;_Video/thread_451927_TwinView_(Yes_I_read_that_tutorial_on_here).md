---
title: "TwinView (Yes I read that tutorial on here)"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by wiseguy8575 on 2007-05-22
Okay so I've been through tutorials, tried the nvidia-settings, tried editing the xorg.conf file manually, and even tried Xinerama but every single time, my external monitor seems to not detect any input.

Check it out:

```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEdidFreqs" "True"
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "MetaModes" "DFP: 1400x1050 +0+0, CRT: 1024x768 +1400+0"
(**) NVIDIA(0): Option "UseDisplayDevice" "string"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     enabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(WW) NVIDIA(0): Invalid UseDisplayDevice string token: "string"; discarding
(WW) NVIDIA(0):     token.
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX Go5200 32M/64M at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 32768 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.50.ab
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX Go5200 32M/64M at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     RDS RadiusS-3F (CRT-0)
(--) NVIDIA(0):     TOSHIBA Internal Panel (DFP-0)
(--) NVIDIA(0): RDS RadiusS-3F (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): TOSHIBA Internal Panel (DFP-0): 270.0 MHz maximum pixel clock
(--) NVIDIA(0): TOSHIBA Internal Panel (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-0, DFP-0
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "DFP:1400x1050+0+0,CRT:1024x768+1400+0"
(II) NVIDIA(0): Virtual screen size determined to be 2424 x 1050
(--) NVIDIA(0): DPI set to (86, 84); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfcefe000 - 0xfcefefff (0x1000) MX[B]
	[7] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[8] -1	0	0x44000a00 - 0x44000aff (0x100) MX[B]
	[9] -1	0	0x44000800 - 0x440009ff (0x200) MX[B]
	[10] -1	0	0x44000400 - 0x440007ff (0x400) MX[B]
	[11] -1	0	0x44000000 - 0x440003ff (0x400) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0xfce01000 - 0xfce011ff (0x200) MX[B]
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[22] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[23] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[24] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[25] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[26] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[32] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[33] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "DFP:1400x1050+0+0,CRT:1024x768+1400+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Keyboard0: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: Core Pointer
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
(II) NVIDIA(0): Setting mode "CRT-0:1024x768@1024x768+0+0"
(II) NVIDIA(0): Setting mode "DFP:1400x1050+0+0,CRT:1024x768+1400+0"
(II) NVIDIA(0): Setting mode "DFP-0:1400x1050@1400x1050+0+0"

```

What exactly am I supposed to do to get my card to send the signal to both the laptop monitor and the external monitor?  If I enable the external monitor and disable my laptop's screen, the external monitor works as the default screen.

Thanks for your help guys.

---

### Post by olejorgen on 2007-09-23
I have the same problem with Toshiba Tecra M7. I suspect it 's an toshiba issue. You could try **toshset -video both**. Didn't work for me though. (I hate toshiba)

---

### Post by wiseguy8575 on 2007-09-23
Thanks for the response.  Unfortunately due to school, I had to switch back to Windows XP.

If I ever go back to Ubuntu though, I'll give that a shot.

---


---
title: "xorg.conf nvidia 7150 - samsung LE37M87"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by Mntz on 2008-04-06
I'm trying to get 1920x1080@60 output on my samsung LE37M87 tv screen.
It defaults to 1920x1080@50 because of nvidia-auto-select and this mode isn't supported by my television :(

After installing de latest nvidia beta drivers i have 640x480@60 this is supported but off course i want my full HD resolution. I can see the other resolutions in the Screens and Graphics window but when i change it, nothing happens and when i reopen the window the settings are back to 640x480@60

I tried to edit my xorg.conf by first doing **cvt -v 1920 1080 60.0Hz**:
```
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
```
Then i added this modline to my xorg.conf and changed the **Section "Screen"**
from:
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Virtual     640 480
        Modes      "640x480@60"
    EndSubSection
EndSection
```
to:
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth   24
    SubSection     "Display"
        Depth      24
        Virtual    1920 1080
        Modes      "1920x1080@60"
    EndSubSection
EndSection
```

The entire xorg.conf looks like this:
```
Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "be"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    modeline  "1920x1080@60"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
    modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
    Identifier     "Generic Monitor"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    BoardName      "VESA driver (generic)"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth   24
    SubSection     "Display"
        Depth      24
        Virtual    1920 1080
        Modes      "1920x1080@60"
    EndSubSection
EndSection
```

When i check /var/log/Xorg.0.log:
```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7150 / NVIDIA nForce 630i (C73) at
(II) NVIDIA(0):     PCI:0:16:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.32.09.16
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7150 / NVIDIA nForce
(--) NVIDIA(0):     630i at PCI:0:16:0:
(--) NVIDIA(0):     SAMSUNG (CRT-0)
(--) NVIDIA(0):     SAMSUNG (DFP-0)
(--) NVIDIA(0): SAMSUNG (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): SAMSUNG (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): SAMSUNG (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1920x1080@60"; removing.
(WW) NVIDIA(0):
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0):
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(**) NVIDIA(0): Virtual screen size configured to be 1920 x 1080
(--) NVIDIA(0): DPI set to (47, 48); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfebfec00 - 0xfebfec7f (0x80) MX[B]
        [5] -1  0       0xfebff000 - 0xfebff07f (0x80) MX[B]
        [6] -1  0       0xfebff400 - 0xfebff47f (0x80) MX[B]
        [7] -1  0       0xfebff800 - 0xfebfffff (0x800) MX[B]
        [8] -1  0       0xfea7e400 - 0xfea7e40f (0x10) MX[B]
        [9] -1  0       0xfea7e800 - 0xfea7e8ff (0x100) MX[B]
        [10] -1 0       0xfea77000 - 0xfea77fff (0x1000) MX[B]
        [11] -1 0       0xfea7c000 - 0xfea7dfff (0x2000) MX[B]
        [12] -1 0       0xfea78000 - 0xfea7bfff (0x4000) MX[B]
        [13] -1 0       0xfea7ec00 - 0xfea7ecff (0x100) MX[B]
        [14] -1 0       0xfea7f000 - 0xfea7ffff (0x1000) MX[B]
        [15] -1 0       0xfea40000 - 0xfea5ffff (0x20000) MX[B](B)
        [16] -1 0       0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
        [17] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [18] -1 0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [19] -1 0       0xfea80000 - 0xfeafffff (0x80000) MX[B]
        [20] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [21] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [22] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [23] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [24] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [25] -1 0       0x0000d880 - 0x0000d887 (0x8) IX[B]
        [26] -1 0       0x0000dc00 - 0x0000dc0f (0x10) IX[B]
        [27] -1 0       0x0000e000 - 0x0000e003 (0x4) IX[B]
        [28] -1 0       0x0000e080 - 0x0000e087 (0x8) IX[B]
        [29] -1 0       0x0000e400 - 0x0000e403 (0x4) IX[B]
        [30] -1 0       0x0000e480 - 0x0000e487 (0x8) IX[B]
        [31] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [32] -1 0       0x00004e00 - 0x00004e3f (0x40) IX[B]
        [33] -1 0       0x00004d00 - 0x00004d3f (0x40) IX[B]
        [34] -1 0       0x00004900 - 0x0000493f (0x40) IX[B]
        [35] -1 0       0x00004f00 - 0x00004fff (0x100) IX[B]
        [36] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [37] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
```

You can find in the log:
(WW) NVIDIA(0): No valid modes for "1920x1080@60"; removing.
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".

So something must be wrong in my xorg.conf. I never edited my xorg.conf before so there might be something i forgot to do.
Does anyone have an idea what i'm doing wrong

---

### Post by chewearn on 2008-04-07
Have you try:
```
nvidia-settings
```

Use this to generate an xorg.conf.

---

### Post by Mntz on 2008-04-08
It's frustrating the nvidia-settings screen is bigger then 640x480 and can't be resized.
So i'm not able to push any buttons on the lower part of the window.

Now if found [these settings]("http://users.edpnet.be/desertstorm/le37m87.gif") in the manual. But when i enter the values for 1920x1080 in the [http://xtiming.sourceforge.net](http://xtiming.sourceforge.net) generator, i get a lot of warnings :(
Maybe i'm entering the wrong values? Anyone that can check this?

It's so stupid on my Windows pc with nvidia 7900, i just set the slider to 1920x1080 and it works :(

---

### Post by chewearn on 2008-04-08
> **Mntz said:**
> It's frustrating the nvidia-settings screen is bigger then 640x480 and can't be resized.
So i'm not able to push any buttons on the lower part of the window.
Use ALT+mouse-leftclick to move the window.

> Now if found [these settings]("http://users.edpnet.be/desertstorm/le37m87.gif") in the manual. But when i enter the values for 1920x1080 in the [http://xtiming.sourceforge.net](http://xtiming.sourceforge.net) generator, i get a lot of warnings :(
Maybe i'm entering the wrong values? Anyone that can check this?
I will help you look into this later.

> It's so stupid on my Windows pc with nvidia 7900, i just set the slider to 1920x1080 and it works :(
You are frustrated, but there is no need to make this statement,  It doesn't help coming to your final solution.

---

### Post by Mntz on 2008-04-10
I've now connected the pc to the television with HDMI and have been able to generate a working conf file with nvidia-settings. Thanks for your help/time AstalaVista :)

---


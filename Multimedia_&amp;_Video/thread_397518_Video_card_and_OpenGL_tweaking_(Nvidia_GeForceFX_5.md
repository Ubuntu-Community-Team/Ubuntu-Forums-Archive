---
title: "Video card and OpenGL tweaking (Nvidia GeForceFX 5200)"
date: 2007-03-30
forum: Multimedia &amp; Video
---

### Post by x1a4 on 2007-03-30
Hi, 

I'm tweaking my Xubuntu Edgy and could use some advice.  

**First the hardware:** 

I've a MSI video card with a Nvidia GeForce FX 5200 GPU, sporting 128MB of video RAM, sitting in a 8xAGP slot on a SiS 741GX motherboard with 1GB of system RAM and an AMD Sempron 2400 CPU running at 1.666GHz.  I've the latest Nvidia drivers installed.  

**Now the questions:** 

1) What's better, enabling Nvidia's AGP module (NVAGP), or the kernel's AGP module (AGPGART)?  I'm currently using AGPGART and it works fine but some 3D applications tend to be choppy.  

2) Where should I set OpenGL environment variables, in _~/.login_ or _/etc/login.defs_?

3) Does syncing **glXSwapBuffers** to my monitor's vertical refresh rate improve performance/display quality?  

4) This is my _/etc/X11/xorg.conf_ file, how do I improve it? 

```

# /etc/X11/xorg.conf
#
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Sceptre" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Motion Gyration"
    Option         "AIGLX" "true"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
    
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    # Load           "GLCore"
    Load           "dbe"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    Load           "glx"
    Load           "v4l"
    # Load           "dri"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Motion Gyration"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
EndSection

Section "Monitor"
    Identifier     "Sceptre"
    VendorName     "Sceptre, Inc."
    ModelName      "Sceptre X5S-Naga"
    HorizSync       24.0 - 62.0
    VertRefresh     50.0 - 75.0
    Gamma           1
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "MSI GeForce FX 5200"
    Screen          0
    Option         "NoLogo" "false"
    # AGP support
    # 0 disables AGP support
    # 1 use NVAGP, if possible
    # 2 use AGPGART (kernel AGP support), if possible
    # 3 try AGPGART; if that fails, try NVAGP (nvidia default)
    Option "NvAgp" "3"
EndSection

Section "Screen"
    Identifier     "Sceptre"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "Sceptre"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "true"
    Option         "metamodes" "1024x768_75 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
    Option         "Accel" "true"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "XAANoOffscreenPixmaps" "true"
    Option         "DigitalVibrance" "0"
    Option         "Overlay" "true"
    Option         "CIOverlay" "true"
    Option         "TransparentIndex" "60"
    Option         "OverlayDefaultVisual" "false"
    Option         "SWCursor" "false"
    Option         "HWCursor" "true"
    Option         "CursorShadow" "off"
    Option         "CursorShadowAlpha" "64"
    Option         "CursorShadowXOffset" "4"
    Option         "CursorShadowYOffset" "2"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

# Section "DRI"
#   Mode 0666 
# EndSection

```

Thank you.

---

### Post by francisco_athens on 2007-03-30
```

Section "Screen"
    Identifier     "Sceptre"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "Sceptre"
    DefaultDepth    24
....

```
Off the bat, you can usually improve 3D perfomance by using 16bit depth instead of 24bit in your xorg.conf.  For most applications you wont notice much of a quality difference and the speedup will often be significant.

---

### Post by hikaricore on 2007-03-30
> **francisco_athens said:**
> ```

Section "Screen"
    Identifier     "Sceptre"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "Sceptre"
    DefaultDepth    24
....

```
Off the bat, you can usually improve 3D perfomance by using 16bit depth instead of 24bit in your xorg.conf.  For most applications you wont notice much of a quality difference and the speedup will often be significant.

Just note that this *may* cause issues with certain gaming titles that don't support 16bit depth.
I've had games segfault in 16bit and run perfectly in 24bit colour.  It ranges from bad coding to lack of mode support or other underlying bugs.

You'll just have to check the games you have after making the change to verify you can stick with it.

---

### Post by x1a4 on 2007-03-30
Hi,

Thank you both.  It's not so much that I want to improve performance, I want to improve my system.  This includes performance and/or display quality, with preferance on display quality.  I definitely won't be using 16-bit colour depth, just like I won't be using 16x antialiasing.  

What I want is to squeeze every ounce of power out of my hardware, and at this particular time I'm focusing on graphics/display.

---


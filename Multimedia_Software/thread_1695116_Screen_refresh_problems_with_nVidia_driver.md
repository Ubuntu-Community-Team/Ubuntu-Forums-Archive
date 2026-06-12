---
title: "Screen refresh problems with nVidia driver"
date: 2011-02-25
forum: Multimedia Software
---

### Post by zolero on 2011-02-25
**Hi all.**

I have an annoying postinstall experience with the nVidia 265.35 driver from the developer's page **.run** package. After I've managed how to install it for every kernel I have on my Hardy (3 stock kernels 2.6.24-27 in 386, gen, and srv flavors, and a self built 2.6.30) now my newly installed driver works, but I've got some keyboard and mouse delays. I think that should be some screen refresh problem, but unsure about this. I had done a screenshot to show this to you. When I go with my mouse on menus, searching for the needed one,it lets behind the traces as in picture. Also my keyboard cursor gets delays when I'm typing, like if it freezed for few seconds, but continuing to type, it jumps to the actual position.
I don't know what's the problem here, and can't think on a solution. I post/attach also my xorg.conf, nvidia-settings-rc, .xsession-errors, nvidia-installer.log, and the xserver log below, in the hope anyone comes up with a tip, or with the solution. If anything else helps identifying, or solving the trouble, just let me know, and I'll post it.
Please help me to debug this very annoying behavior. Thanks in advance for any tip, solution, help, or trial.

Now the files...
**xorg.conf**
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
    ModulePath      "/usr/lib/xorg/modules"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "keyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "hu"
    Option         "XkbVariant" "qwerty"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "BenQ"
    ModelName      "G2200W"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 240"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "UseDisplayDevice" "DFP"
    Option         "XAANoOffscreenPixmaps"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```**nvidia-settings-rc**
```
#
# /home/zolero/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Fri Feb 25 14:44:30 2011
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = Yes
ShowQuitDialog = No
Timer = Thermal_Monitor_(GPU_0),Yes,1000
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000

# Attributes:

bluestorm:0.0/CursorShadow=0
bluestorm:0.0/CursorShadowAlpha=64
bluestorm:0.0/CursorShadowRed=0
bluestorm:0.0/CursorShadowGreen=0
bluestorm:0.0/CursorShadowBlue=0
bluestorm:0.0/CursorShadowXOffset=4
bluestorm:0.0/CursorShadowYOffset=2
bluestorm:0.0/SyncToVBlank=0
bluestorm:0.0/LogAniso=0
bluestorm:0.0/FSAA=0
bluestorm:0.0/TextureSharpen=0
bluestorm:0.0/AllowFlipping=1
bluestorm:0.0/FSAAAppControlled=1
bluestorm:0.0/LogAnisoAppControlled=1
bluestorm:0.0/OpenGLImageSettings=1
bluestorm:0.0/FSAAAppEnhanced=0
bluestorm:0.0/RedBrightness=0.000000
bluestorm:0.0/GreenBrightness=0.000000
bluestorm:0.0/BlueBrightness=0.000000
bluestorm:0.0/RedContrast=0.000000
bluestorm:0.0/GreenContrast=0.000000
bluestorm:0.0/BlueContrast=0.000000
bluestorm:0.0/RedGamma=1.000000
bluestorm:0.0/GreenGamma=1.000000
bluestorm:0.0/BlueGamma=1.000000
bluestorm:0.0/DigitalVibrance[CRT-1]=0
bluestorm:0.0/OverscanCompensation[CRT-1]=0
bluestorm:0.0/XVideoTextureBrightness=0
bluestorm:0.0/XVideoTextureContrast=0
bluestorm:0.0/XVideoTextureHue=0
bluestorm:0.0/XVideoTextureSaturation=0
bluestorm:0.0/XVideoTextureSyncToVBlank=1
bluestorm:0.0/XVideoSyncToDisplay=2
```

---

### Post by realzippy on 2011-02-25
Same here when I used to try 270.xx...
Went back to 260.xx ....too lazy to figure it out,also no benefits for my card according changelog.
Will test your solution when it is done..    :)

---

### Post by zolero on 2011-02-25
**For ****_tseliot_ mod - ****dedicated** ('pologise for this, coz I'm desperate to have a solution...)

**Hi, Alberto.**

As you're the master guru in such problems, please take a look at this post, if you have the time and mood for... Really appreciate, and thanks in advance.

Zolero.

---


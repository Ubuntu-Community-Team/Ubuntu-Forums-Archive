---
title: "Another NVidia xorg.conf"
date: 2010-03-02
forum: Multimedia Software
---

### Post by DarthScape on 2010-03-02
Just started using KDE 4.3 with the NVidia 195.22 driver. Please don't hate me for the OS: PC-BSD. So far the only reason I use it is for the video not tearing like it does on every distro of linux. There is just one problem, I can't get the dual monitors to work; and I don't have nvidia-settings on this system. I do have an xorg.conf, it shows the second monitor, but the monitor stays completely off. Since this is kind of generic towards unix nvidia drivers, I though someone here might be able to help.

```

# Xorg.conf file generated for PC-BSD

Section "ServerLayout"
    Identifier     "XFree86 Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "ServerFlags"
        Option "AutoAddDevices" "False"
        Option "AllowEmptyInput" "Off"
EndSection

Section "Files"
    ModulePath      "/usr/local/lib/xorg/modules"
    FontPath        "/Programs/fonts/"
    FontPath        "/usr/local/lib/X11/fonts/cyrillic/"
    FontPath        "/usr/local/lib/X11/fonts/TrueType/"
    FontPath        "/usr/local/lib/X11/fonts/webfonts/"
    FontPath        "/usr/local/lib/X11/fonts/misc/"
    FontPath        "/usr/local/lib/X11/fonts/TTF/"
    FontPath        "/usr/local/lib/X11/fonts/Type1/"
    FontPath        "/usr/local/lib/X11/fonts/CID/"
    FontPath        "/usr/local/lib/X11/fonts/75dpi/"
    FontPath        "/usr/local/lib/X11/fonts/100dpi/"
    FontPath        "/usr/local/lib/X11/fonts/dejavu/"
    FontPath        "/usr/local/lib/X11/fonts/local/"
EndSection

Section "Module"
    Load           "ddc"
    Load           "dbe"
    Load           "extmod"
    Load	   "glx"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "keyboard"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbVariant" ""
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/sysmouse"
    Option         "Buttons" "6"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons"
EndSection

Section "Extensions" 
    Option	"Composite" "Enable"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection



Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection


Section "ServerFlags"
    Option         "Xinerama" "0"
    Option "AutoAddDevices" "False"
    Option "AllowEmptyInput" "Off"
EndSection


Section "Device"
    Identifier      "Card0"
    Screen           0
#    Option         "AllowGLXWithComposite" "true"
#    Option         "RenderAccel" "true"
#    Option         "AddARGBGLXVisuals" "true"
#    Option         "UseEvents" "false"
#    Option         "TripleBuffer" "1"
#    Option         "DamageEvents" "1"
#    Option         "BackingStore" "1"
#    Option         "PixmapCacheSize" "70000"
#    Option         "OnDemandVBlankInterrupts" "true"
#    Option         "XAANoOffscreenPixmaps" "true"
    Option         "NoLogo" "True"
    Driver         "nvidia"
    VendorName     "nVidia Corporation"
    BusID      "PCI:1:0:0"
EndSection

Section "Device"
    Identifier      "Card1"
    Screen           1
#    Option         "AllowGLXWithComposite" "true"
#    Option         "RenderAccel" "true"
#    Option         "AddARGBGLXVisuals" "true"
#    Option         "UseEvents" "false"
#    Option         "TripleBuffer" "1"
#    Option         "DamageEvents" "1"
#    Option         "BackingStore" "1"
#    Option         "PixmapCacheSize" "70000"
#    Option         "OnDemandVBlankInterrupts" "true"
#    Option         "XAANoOffscreenPixmaps" "true"
    Option         "NoLogo" "True"
    Driver         "nvidia"
    VendorName     "nVidia Corporation"
    BusID      "PCI:1:0:0"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Card0"
    Monitor        "Monitor0"
    DefaultDepth   24
    SubSection     "Display"
        Depth      24 
        Modes      "1920x1080"
    EndSubSection
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: 1920x1080 +0+0, DFP-1: 1920x1080 +1920+0"
EndSection


Section "Screen"
    Identifier     "Screen1"
    Device         "Card1"
    Monitor        "Monitor1"
    DefaultDepth   24
    SubSection     "Display"
        Depth      24 
        Modes      "1680x1050"
    EndSubSection
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: 1680x1050 +0+0"
EndSection



```

---

### Post by RedRat on 2010-03-02
Is there some reason you don't have nvidia-settings on your system?? Can't you get it with apt-get or Synaptic?

---

### Post by lyall on 2010-03-02
check out this link
a place to start
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Install_Latest_Nvidia.2FATI_drivers]("http://ubuntuguide.org/wiki/Ubuntu:Karmic#Install_Latest_Nvidia.2FATI_drivers")

to set up the video card

then scroll down to see **Configure Dual Monitors with nVidia**


hope this helps
good luck and have fun learning

---

### Post by mosshorn on 2010-03-03
get nvidia-settings (I could have sworn you needed it now, regardless of OS 0.o)

Idk exactly how BSD works compared to any other distro, but I'll just give the same advice that I used from someone else. Backup your config file, run nvidia-settings as root, and you should be able to save.

P.S.- google? ;D

---


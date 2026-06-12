---
title: "Black screen except when launching gnome through recovery"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by MetalAZ on 2007-09-13
I decided to ditch my Radeon X1900XT for nVidia in hopes that my display issues would be a thing of the past.  I picked up a GeForce 8800 GST last night and did a re-install of Ubuntu 7.04 64-bit.

First I installed the nvidia driver package through apt-get.  It was the one with -new after it, can't remember the name.  But I was getting a black screen when booting so I uninstalled it and installed the ones from nVidia's web site.

I have the same black screen, but if I boot into recovery mode and type "startx" it loads fine.  Also if I type telinit 3 it loads the GUI login and I can login as any other user on the machine.

My Xorg.0.log is free from video related errors (only mouse or keyboard errors) and everything seems to be fine once I'm in Gnome.  Both of my monitors display at 1600x1200 (my second is setup as a separate x screen).

I wasn't able to find a solution searching on here or the nVidia forum.

Here's my xorg.conf (it was edited by the nVidia GUI tool
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
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
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
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
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP-1: 1600x1200 +0+0; DFP-1: 800x600 +0+0; DFP-1: 640x480 +0+0"
# Removed Option "metamodes" "DFP-0: 1600x1200 +1600+0, DFP-1: 1600x1200 +0+0; DFP-1: 800x600 +0+0; DFP-1: 640x480 +0+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "DFP-0: 1600x1200 +1600+0, DFP-1: 1600x1200 +0+0; DFP-0: nvidia-auto-select +800+0, DFP-1: 800x600 +0+0; DFP-0: nvidia-auto-select +640+0, DFP-1: 640x480 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseDisplayDevice" "DFP-1"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: 1600x1200 +0+0; DFP-1: 800x600 +0+0; DFP-1: 640x480 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "UseDisplayDevice" "DFP-0"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: 1600x1200 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```

Before the screen goes black on boot, I see a message about not being able to allocate memory.  Unfortunately it goes by so fast that I don't know what the whole line says or even it's a problem related to this.  In the dmesg I see a similiar line "PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:01:00.0", but I don't know it's the same error or not.

Anyone have any ideas on what might be causing this issue?

---


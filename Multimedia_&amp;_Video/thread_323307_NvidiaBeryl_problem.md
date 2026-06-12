---
title: "Nvidia/Beryl problem"
date: 2006-12-21
forum: Multimedia &amp; Video
---

### Post by navilon on 2006-12-21
I have installed the legacy binary drivers (1.0-7184) for my GeForce MX-400 PCI card. 

When I start beryl-manager, here is the error it returns:
```
Xlib:  extension GLX missing on display :0.0.
Error: couldn't find RGB GLX visual
Segmentation fault (core dumped)
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD=NOTHING
XGL Absent, checking for NVIDIA
Nvidia Present
Xlib:  extension GLX missing on display :0.0.
beryl: Root visual is not a GL visual
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

xorg.conf
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
Option "AIGLX" "True"
EndSection

Section "Files"

	# path to defoma fonts
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
	Load "i2c"
	Load "bitmap"
	Load "ddc"
	Load "dbe"
	Load "dri"
	Load "extmod"
	Load "freetype"
	Load "glx"
	Load "int10"
	Load "type1"
	Load "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "DELL P991"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nvidia"
    Driver         "nvidia"
	Option          "TripleBuffer" "true"

# Enable 32-bit ARGB GLX Visuals
Option "AddARGBGLXVisuals" "True"
Option "XAANoOffscreenPixmaps"

EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nvidia"
    Monitor        "DELL P991"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768"
    EndSubSection

# Enable 32-bit ARGB GLX Visuals
    Option "AddARGBGLXVisuals" "True"

# If you are using an older version of compiz that
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
    Option "DisableGLXRootClipping" "True"

EndSection

```

---

### Post by ingo on 2006-12-22
try the beryl forum

[http://forum.beryl-project.org/index.php](http://forum.beryl-project.org/index.php)

they are pretty helpful.

---

### Post by kgdjianhua on 2006-12-22
I think that your PCI card is too old.

---

### Post by tseliot on 2006-12-22
AFAIK there's no need to install the legacy driver.

Here is the compatibility list of the latest driver:
[http://download.nvidia.com/XFree86/Linux-x86/1.0-9746/README/appendix-a.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-9746/README/appendix-a.html)

It says that you should use a 1.0-96xx driver for your card

---

### Post by xyrer on 2006-12-26
I have been looking for that 1.0.96xx legacy driver but had no luck, anyone would mind pointing me to one link or something?

Edit: Never mind, followed tseliot's link and found it, thanks.

---


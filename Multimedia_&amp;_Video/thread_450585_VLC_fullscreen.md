---
title: "VLC fullscreen"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by Tehut on 2007-05-21
(Kubuntu 7.04 64)
When switching to fullscreen in vlc, it remains a window, that is the title bar at the top is still visible.
With mplayer it works just fine.
So, does anyone know that problem and a solution for it?
Thank you.

---

### Post by earobinson on 2007-05-21
how are you changing to full screen? are you clicking the box to the left of the X? or are you double clicking the video?

---

### Post by Kobalt on 2007-05-21
It's a [known bug]("http://ubuntuforums.org/showthread.php?t=87085") of the 64bit VLC. Try to go in the Pref. and select the alternate full screen option in the video settings.

---

### Post by Tehut on 2007-05-21
Then the video isn't visible at all, though it is played, as the sound does work.

---

### Post by stchman on 2007-05-21
> **Tehut said:**
> (Kubuntu 7.04 64)
When switching to fullscreen in vlc, it remains a window, that is the title bar at the top is still visible.
With mplayer it works just fine.
So, does anyone know that problem and a solution for it?
Thank you.

Double click on the playing video.  This will toggle you to fullscreen.  I believe there is a View-->Full Screen but I could be mistaken.  The double click works.  When it is full screen you can double click on the video to exit full screen.  Selecting the Maximize does not command fullscreen.

---

### Post by Tehut on 2007-05-21
Guess how I switched to fullscreen. That is exactly what's not working.

---

### Post by david_2001 on 2007-05-21
> **Tehut said:**
> Guess how I switched to fullscreen. That is exactly what's not working.

See if this works:  In vlc, select Settings | Preferences then Video > Output Modules, check "Advanced options", check that "Video output module" is set to "Default", then check "Alternate Fullscreen Method" for XVideo and, to cover all bases, OpenGL(GLX).  Click "Save" then close and restart vlc (don't skip this last step).

---

### Post by Tehut on 2007-05-22
> **david_2001 said:**
> See if this works:  In vlc, select Settings | Preferences then Video > Output Modules, check "Advanced options", check that "Video output module" is set to "Default", then check "Alternate Fullscreen Method" for XVideo and, to cover all bases, OpenGL(GLX).  Click "Save" then close and restart vlc (don't skip this last step).
->
> **Tehut said:**
> Then the video isn't visible at all, though it is played, as the sound does work.

---

### Post by david_2001 on 2007-05-22
> **Tehut said:**
> ->

Then you're going to have to provide some useful information such as video hardware and video driver, and whether or not you are using a composite window manager (Beryl or Compiz).  If you are using Beryl or Compiz, take a look at [http://ubuntuforums.org/showpost.php?p=2696622&postcount=10](http://ubuntuforums.org/showpost.php?p=2696622&postcount=10).  In the meantime, I'm happily using vlc with Compiz and have no problems at all with fullscreen windows.

EDIT: And I'm running Feisty AMD64 too.

---

### Post by Tehut on 2007-05-23
> **david_2001 said:**
> Then you're going to have to provide some useful information such as video hardware and video driver, and whether or not you are using a composite window manager (Beryl or Compiz).  If you are using Beryl or Compiz, take a look at [http://ubuntuforums.org/showpost.php?p=2696622&postcount=10](http://ubuntuforums.org/showpost.php?p=2696622&postcount=10).  In the meantime, I'm happily using vlc with Compiz and have no problems at all with fullscreen windows.

EDIT: And I'm running Feisty AMD64 too.
nvidia geforce 6800 GT, current repository version of nvidia-glx-new, neither beryl, nor compiz

---

### Post by david_2001 on 2007-05-23
Ok, I have a GeForce 7100GS and am also running the nvidia-glx-new driver (now - I was using nvidia-glx until I read your last post).  Before delving into xorg.conf, reset vlc with a "Settings | Preferences | Reset All" and then, while you're in the Settings dialog, set the "Video | Output modules" options as in the two attached screenshots.  No need to change anything else.  Click Save then close and restart vlc.  If this doesn't work, please post your complete /etc/X11/xorg.conf.

---

### Post by Tehut on 2007-05-24
Does not work.

xorg:

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
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
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "type1"
    Load           "v4l"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "de"
    Option         "XkbVariant" "nodeadkeys"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 65.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6800 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "NoLogo"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

---

### Post by david_2001 on 2007-05-24
I'll take a closer look this evening but there are items that are not necessary, not complete and not in the correct place.  Preliminary edit:

Section "ServerLayout"
    Identifier     "Default Layout"
# Deleted the "0 0", which should not be necessary
    Screen         "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
# Delete the following three lines if you don't have the corresponding devices
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
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

# Module section amended
Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "de"
    Option         "XkbVariant" "nodeadkeys"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
# Delete this section if you don't have the corresponding device
# /dev/input/event
# for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
# Delete this section if you don't have the corresponding device
# /dev/input/event
# for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
# Delete this section if you don't have the corresponding device
# /dev/input/event
# for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 65.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6800 GT]"
    Driver         "nvidia"
# The following two were in the wrong place.  AddARGBGLXVisuals is commented
# out because it should not be necessary when not running Compiz/Beryl.
    Option         "NoLogo" "True"
#    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
# Display options that should not be necessary deleted
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by brodiepearce on 2007-05-27
I was having this same problem on Feisty AMD64 with an A64 3200+ and ATI Sapphire X800GTO^2.  This [fix]("http://ubuntuforums.org/showpost.php?p=1287709&postcount=2") worked for me.  Good luck.

---

### Post by hasimir44 on 2007-05-27
the alternate fullscreen works for the bottom taskbar, but the top one remains... good enough for now, I guess..

---

### Post by hasimir44 on 2007-05-27
ok.. 

do the alternate fullscreen as mentioned above, then hide the top taskbar - this gives a true fullscreen for vlc 64

---

### Post by pathorn on 2007-10-05
I'm getting this as well in Feisty.

It works perfectly fine on my 32-bit machine running Debian Etch... but it doesn't seem like the type of bug that would be caused by this.

I have tried using the alternate fullscreen method, but that window fails to open after flashing the screen black and VLC shows up grey.

I'm going to try compiling my own version of VLC.


I'm sure Alternate Fullscreen Method is not the proper option.  VLC itself says it will "bypass the window manager, and nothing can show on top".  However I know that MPlayer works perfectly fine on x86_64 Ubuntu without using some weird X11 hack (i.e. I can alt-tab and do anything)

When I run xwininfo on the MPlayer and VLC windows I get the difference being:
xwininfo: Window id: 0x3200012 (has no name) -- This is VLC... not sure why it's blank.
  Absolute upper-left X:  1
  Absolute upper-left Y:  24
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Corners:  +1+24  -1+24  -1--21  +1--21
  -geometry 1598x1197+0+0

xwininfo: Window id: 0x2800001 "MPlayer"
  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1600x1200+0+0



When I run VLC with Alternate fullscreen I get:
=======
[00000355] xvideo video output debug: entering fullscreen mode
XSetInputFocus failed
[00000358] main private debug: decoded 103/105 pictures
=======

Here are the relevant bits of xorg.conf (I cut out InputDevice, Files and ServerLayout).
==============
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

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 2001FP"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GTS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
EndSection
===============

---


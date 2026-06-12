---
title: "TwinView MetaMode shortcuts sets wrong resolution"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by TwoD on 2007-12-30
Switching MetaModes (Ctrl+Alt+minus ort Ctrl+Alt+plus) to one with lower resolution than my normal one (3200x1200) creates undesired panning when left screen is turned off.
Icons and windoes remain in their positions relative the X screen.
A black area appears below the desktop area previously on the left monitor, which used to be inaccessible (unpannable) due to resolution differences.

To me, it looks like whatever reacts on the shortcut fails to change the resolution of the X screen before moving it to the single main monitor, keeping the resolution at 3600x1200 with a panning viewport of 1920x1200.

The same thing happen when a game changes the resolution, the left monitor turns off, the right (main) pans a bit to the left to stay centered, the game is thus offset to the right and left partially off screen, unplayable.

But...

It all works perfectly if I switch MetaModes via within nvidia-settings. The left screen turns off, all my icons move to the main screen, resolution changes on main screen, no panning.

Are the keyboard shortcuts  buggy, or am I missing something?

Btw, are there more of these **extremely well hidden** shortcuts (Google couldn't find any references at all)?


I've set up my two displays like this:

GFX Card: nVidia Geforce 7800 GTX with two DVI outputs.

Screen 1 is an LG L2930BQ 19", normally running at 1280x1024. (Left screen)
Screen 2 is a BenQ T23IWA 24", normally running at 1920x1200. (Right/Main screen, uses VGA converter)

I want to run fullscreen apps (mostly games) on the 24" screen. Preferably, the left screen should still show the desktop (so I can monitor stuff while playing games), but it seems to be easier to simply turn it off.


My xorg.conf looks like this:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
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
    Option         "XkbLayout" "se"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

Section "Monitor"
    Identifier     "L1930B"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "BenQ T241WA"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7800 GTX]"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:5:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GTX"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7800 GTX]"
    Monitor        "L1930B"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0;CRT: 1920x1200; CRT: 1280x1024; CRT: 1024x768; CRT: 800x600"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

Sorry for the wall

---

### Post by barakaspeed on 2008-05-05
I am having the very SAME issue!  I also noted that if I also change the resolution manually by (System->Preferences->Screen Resolution) I will get the desired result of my left monitor turning off and the right one without any panning.

Anyone have any insight on this?



I've set up my two displays like this:

Inspiron 9300
Nvidia Driver: 169.12
GFX Card: nVidia Geforce Go 6800 with laptop screen and two other outputs DVI and VGA.

Screen 1 is a Westinghouse L2410NM 24", normally running at 1920X1200. (Left screen, using VGA connection)
Screen 2 is also a Westinghouse L2410NM 24", normally running at 1920x1200. (Right/Main screen, using DVI connection)

xorg.conf
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Tue Mar  4 20:24:34 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option         "SHMConfig" "on"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "WDE L2410NM"
    HorizSync       30.0 - 80.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6800"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: 1920x1200, DFP-1: 1920x1200; CRT: NULL, DFP-1: 1680x1050; CRT: NULL, DFP-1: 1440x900; CRT: NULL, DFP-1: 1280x768; CRT: NULL, DFP-1: 800x600"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
#    Option         "TwinViewOrientation" "RightOf"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "CRT: 1920x1200 +0+0, DFP-1: 1920x1200 +1920+0; CRT: NULL, DFP-1: 1920x1200 +0+0; CRT: NULL, DFP-1: 1680x1050 +0+0; CRT: NULL, DFP-1: 1600x1024 +0+0; CRT: NULL, DFP-1: 1440x900 +0+0; CRT: NULL, DFP-1: 1400x1050 +0+0; CRT: NULL, DFP-1: 1280x1024 +0+0; CRT: NULL, DFP-1: 1280x960 +0+0; CRT: NULL, DFP-1: 1280x800 +0+0; CRT: NULL, DFP-1: 1280x720 +0+0; CRT: NULL, DFP-1: 1152x864 +0+0; CRT: NULL, DFP-1: 1024x768 +0+0; CRT: NULL, DFP-1: 960x600 +0+0; CRT: NULL, DFP-1: 832x624 +0+0; CRT: NULL, DFP-1: 800x600 +0+0; CRT: NULL, DFP-1: 800x512 +0+0; CRT: NULL, DFP-1: 720x480 +0+0; CRT: NULL, DFP-1: 720x450 +0+0; CRT: NULL, DFP-1: 640x512 +0+0; CRT: NULL, DFP-1: 640x480 +0+0; CRT: NULL, DFP-1: 640x400 +0+0; CRT: NULL, DFP-1: 640x384 +0+0; CRT: NULL, DFP-1: 576x432 +0+0; CRT: NULL, DFP-1: 512x384 +0+0; CRT: NULL, DFP-1: 416x312 +0+0; CRT: NULL, DFP-1: 400x300 +0+0; CRT: NULL, DFP-1: 320x240 +0+0"
EndSection
```

Update:  I tried going back to legacy nvidia drivers 96.43.05 and still I have the same issue

---

### Post by ptumik on 2008-05-05
I have the same problem.
I'm trying to use my TV as second output and it does support 1360x768 resolution, but in nvidia-settings I have only two options: 640x480 and 320x240 which is ridiculous. 
I've tried to manually change xorg.conf to proper resolution but in that case I have just black screen on TV, and looks like driver just disabling second output. 

So, anyone know how to set a proper resolution for a second output? 

Thanks in advance.

---

### Post by barakaspeed on 2008-05-05
After too many hours of searching...

I have found that this is a feature and not a bug.

See [http://en.wikibooks.org/wiki/NVidia/Twin_View](http://en.wikibooks.org/wiki/NVidia/Twin_View)

Snippet from it:
> The default meta mode is the left most one. You can switch through the modes in two ways whilst X is running. The first method is to use the Ctrl-Alt-+/- key combination to change native resolution of the screen **whilst keeping the virtual screen size the same**, this is sometimes called a **virtual desktop**. The other method only available on modern distributions is to use the xrandr command which changes resolution without creating a virtual desktop, xrandr with no arguments gives a list of all the available modes, to change to mode two use "xrandr -s 2", more details about xrandr can be found on its man page.

So you see, when either the game makes the request for resolution change or by Switching MetaModes (Ctrl+Alt+minus or Ctrl+Alt+plus) you are stuck with the Virtual Desktop that is stuck at the maximum pixel size.

Now using xrandr or changing the resolution via (System->Preferences->Screen Resolution) will yeild the desired result if you are not using compiz.  I say "not using compiz" because you'll find you will 'lose' some of your windows in the WindowList applet when you have multiple windows open up on each screen!  Surely a bug with compiz.  Not sure how to file that and really explain it well enough for a bug report with them.

---

### Post by TwoD on 2008-05-06
Hmm, even if it's not a bug, it's still a very undesirable "feature".

Barakaspeed, thank you very much for looking that up and sharing it!


This might get a bit off topic, but since the matter is somewhat resolved, I'll just share some of my other experience with TwinView vs Xinerama.

I spent several hours last night battling with xorg.conf and testing numerous variations of my settings to try to get the most out of the nVidia driver. (Driver manager said it was installed but not in use, and I was getting weird artifacts on progressbars and some texts.) I also decided to try Xinerama in the same run as TwinView had some undesierable side effects (mainly that icons were constantly placed "below" my left screen completely out of view, as well as the issue this thread's about).

(One has to disable TwinView before being allowed to enable Xinerama since it needs to be in "separate x screens" mode for Xinerama to be able to merge them to one. The option simply doesn't show while using TwinView, which confused me at first when others said they saw it.)

Changing things such as disabling TwinView via the nvidia settings tool didn't work well when saving and merging xorg.conf, I kept getting lowres mode after reboot and the popup saying that  the graphics card could not be identified and that it's now set to VESA mode (or was it VGA, i forgot). It also asks if you wish to select a driver, but no matter what I select there will either have no effect or make my screens useless for 15 seconds until it resets after testing, so I just skipped that dialogue whenever it came up.

I tried the EnvyNg tool, both autodetection and manually switching drivers, all gave me lowres mode after reboot as well as mangling my xorg.conf unrecognizeable (ALWAYS keep plenty of backups!).

I manually edited xorg.conf based on other people's working setups but after each reboot I kept getting lowres mode.
I did get one version up and running, without Xinerama or Twinview enabled, by having two Device, Monitor and Screen sections in xorg.conf and most of my old settings like mouse and keyboard working.
So I had two separate X desktops, one on each monitor, but you're not allowed to move windows between them, which I need.
I didn't try to just enable Xinerama at that point (which should have worked) for some reason I forgot, but I kept testing settings. 99% of them lead to lowres mode after reboot...

Checked the xorg logs but it just said "loading xorg.conf.failsafe" or similar right from the start. Only error I found was one about not being able to init GLX because of missing drivers, but then it had already loaded the failsafes, which confused me a bit more.

Anyway, my last attemt was once again with the nvidia settings tool. This time I restored my working TwinView setup. Disabled TwinView in nvidia settings by setting it to separate x screens, enabled Xinerama. Saved settings to xorg.conf but I did NOT merge my old xorg.conf in there. (I ran it with sudo, otherwise you might need to copy/paste yourself).

What I ended up with was this:
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Tue Mar  4 20:28:57 UTC 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" RightOf "Screen1"
    Screen      1  "Screen1" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "LG L1930B"
    HorizSync       30.0 - 71.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "BenQ T241WA"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GTX"
    BusID          "PCI:5:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GTX"
    BusID          "PCI:5:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard1"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1920x1200 +0+0; CRT: nvidia-auto-select +0+0; CRT: 1280x1024 +0+0; CRT: 1024x768 +0+0; CRT: 800x600 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

That of course Nuked my two extra mouse buttons (and maybe my keyboard's Swedish characters, don't remember), but I did have a working Xinerama setup with correct resolutions etc.

In Xinerama, the cursor cannot move outside my left (smaller) screen which is great as I assume that means icons won't be placed there either. I can move windows between screens and I have only one set of panels etc.
"Great!" I though and was just going to check a few things on the net before going to bed. Stumbled upon an article comparing the performance (NOT features) between Xinerama and TwinView. Seems TwinView beats Xinerama in pure FPS in most games...Not strange since Xinerama wasn't developed by nVidia, unlike Twinview. But it was enough to make me doubt switching hehe.

When I get home today, I'll do some more digging to re-enable mousebuttons etc and evaluate Xinerama some more...

Enough from me now...
Thanks again for your input guys!

---


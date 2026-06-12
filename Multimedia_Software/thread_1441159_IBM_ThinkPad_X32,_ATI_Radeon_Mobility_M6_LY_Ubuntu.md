---
title: "IBM ThinkPad X32, ATI Radeon Mobility M6 LY Ubuntu 9.10 xorg.conf AccelMethod problem"
date: 2010-03-28
forum: Multimedia Software
---

### Post by padnoter on 2010-03-28
I'm running Ubuntu 9.10 on an oldish IBM Thinkpad X32 (12.1in 1024x768 LCD, 16MB ATI Radeon).
On the initial install of 9.10 I couldn't get any higher resolutions working, following the instructions in [https://bugs.launchpad.net/ubuntu/+bug/466066/](https://bugs.launchpad.net/ubuntu/+bug/466066/) things improved;

1024x768 resolution is running ok but some graphics are noticeably slow - a prime example is the "File Browser", switching from one app to this app, you see a grey window for a second, and then finally the File Manager displays.

Here is my current xorg.conf

> 
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
#    Screen        "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dri2"
    Load  "dbe"
    Load  "dri"
    Load  "record"
    Load  "extmod"
    Load  "glx"
    Load    "GLcore"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    Option "DPMS"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "radeon"
#
# WITHOUT THE NEXT LINE EXA, BLACK MSGS (E.G NETWORK CONNECTED) ARE CORRUPTED, BUT THIS ALSO SLOWS DOWN FILE BROWSER.. try XAA/UXA... XAA/UXA=BLACKMSGS CORRUPT& FAST FILEBROWSER
    Option     "AccelMethod"    "EXA"
    VendorName  "ATI Technologies Inc"
    BoardName   "Radeon Mobility M6 LY"
    BusID       "PCI:1:0:0"
    Option "AGPMode" "4"
    Option "AGPSize" "64"
#
#    Option "AGPFastWrite" "on"
#    Option "EnablePageFlip" "on"
#    Option "XAANoOffscreenPixmaps" "on"
#    Option "DisableGLXRootClipping" "on"
#    Option "AddARGBGLXVisuals" "on"
#    Option "AllowGLXWithComposite" "on"
#
#        Driver "ati"
#        Option "RingSize" "8"
#        Option "BufferSize" "2"
#        Option "EnablePageFlip" "True"
#        Option "EnableDepthMoves" "True"
# Option "SWcursor" "off" #Faster than default (on)
# Option "AccelMethod" "EXA" # or XAA, which is the default and may be more stable
# Option "DynamicClocks" "on"
# Option "BIOSHotkeys" "on"
#        Option "RenderAccel" "true" # Enables hardware acceleration
#        Option "DynamicClocks" "on" # Adds clock scalability / power management for the video card

#
#    Option          "AccelMethod"       "XAA"
#    Option          "EnablePageFlip"    "true"
#    Option          "TripleBuffer"      "true"
#       Option          "AGPMode"        "4"
#    Option        "DRI"            "true"
#    Option        "AGPFastWrite"        "yes"
#    Option        "RenderAccel"        "true"
#    Option        "DynamicClocks"        "true"
#    Option        "BIOSHotkeys"        "true"
#
#    Identifier    "ATI Technologies Inc Radeon Mobility M6 LY"
#    Driver        "ati"
#    BusID        "PCI:1:0:0"
#    Option        "UseFBDev"        "true"
#       Option          "AGPMode" "4"
#       Option          "AGPSize" "64" # default: 8
#        Option          "RingSize" "8"
#        Option          "BufferSize" "2"
#        Option          "EnablePageFlip" "True"
#       Option          "EnableDepthMoves" "True"
#        Option          "RenderAccel" "true"
#

EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
#
# NEXT LINE CAUSES VLC TO BLUE SCREEN IF USED
#    DefaultDepth 16
#
    SubSection "Display"
        Depth 8
        Modes "1024x768"
    EndSubSection
    SubSection "Display"
        Depth 16
        Modes "1024x768"
    EndSubSection
    SubSection "Display"
        Depth 24
        Modes "1024x768"
    EndSubSection
EndSection
I can speed up the "grey" File Manager display by setting;
Option     "AccelMethod"    "XAA" # or "UXA"

- but then I have the side effect of corrupted messages;
(see non-EXA.png attachment)

- the only way to remove the corruption seems to be using EXA for AccelMethod.

All the "options" in the Device section that are commented out are ones that I've tried to use to increase performance.

One last bit of information. Lots of the forum entries ask for glxinfo output, mine gives errors (in case this helps anyone help me);

> x32@x32-laptop:~$ sudo glxinfo
[sudo] password for x32: 
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  137 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16

Any help appreciated.
Cheers
pn

---

### Post by padnoter on 2010-03-28
update;
from [https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492)
I have added;
> [FONT=Courier New]    Option    "MigrationHeuristic" "greedy"[/FONT]
to the Device section in xorg.conf and performance of File Browser is now improved.

But,
I'd still appreciate any comments/help/solutions about the video drivers on my X32?

---

### Post by davecc on 2010-08-30
Hi, not sure if this will help you however I have Kubuntu running on a X32 and had similar issues with the graphics performance.  After a bit of googling I came up with the following xorg.conf entries for the card:

[INDENT]Section "Device"
	[INDENT]Identifier	"ATI"
	Driver		"radeon"
	Option		"AccelMethod" "XAA"
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "yes"
	Option		"EnablePageFlip" "on"
	Option		"RenderAccel" "on"
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys" "on"[/INDENT]
EndSection[/INDENT]

Good luck!

---

### Post by padnoter on 2010-09-17
Thanks davecc for that. I tried it, and it works as well as the final config I settled on, which is mentioned above, but for clarity - here it is;

    Identifier  "Card0"
    Driver      "ati"
    Option     "AccelMethod"    "EXA"
    Option    "MigrationHeuristic" "greedy"
    VendorName  "ATI Technologies Inc"
    BoardName   "Radeon Mobility M6 LY"
    BusID       "PCI:1:0:0"
    Option "AGPMode" "4"
    Option "AGPSize" "64"

If anyone knows the (dis)advantages of either setup it would be good to hear. They both work well on my ibm thinkpad x32
Thanks

---


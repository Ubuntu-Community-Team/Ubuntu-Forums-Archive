---
title: "Nvidia display help"
date: 2009-04-04
forum: Mythbuntu
---

### Post by KeefTM on 2009-04-04
Ok, for starters, here is my HTPC build:

E5200 2.5 Wolfdale
Gigabyte GA-E7AUM-DSH2 w/ GeForce 9400
4GB Corsair ram
Mythbuntu 8.10 x86_64
Nvidia 180.44 x86_64
Samsung HD DLP HL-S5086W using HDMI

I also am not very familiar with linux, so I probably missed something simple. Now, when the system starts, I get all the way to the NVidia splash screen, then the TV says there is no signal. The computer is still running cause I can ssh in and hit Ctrl-Alt-F1 to get to the prompt. I'm assuming that the TV doesn't like the resolution that the driver is selecting, because using the VESA mode works fine. I need help configuring xorg.conf. I really have no clue what the correct settings and options would be. According to the TV manual, I should use:

1280 x 720p
Horiz 45.00
Vert 60
Pixel Clock 74.25

I have attatched the xorg.0.log and the xorg.conf files. Thanks for any help you can give.

---

### Post by nickrout on 2009-04-04
Only thing I can see from those files is that horizsync and vertrefresh figures are not quoted, but I am not sure if that will make a difference.

---

### Post by KeefTM on 2009-04-04
> **nickrout said:**
> Only thing I can see from those files is that horizsync and vertrefresh figures are not quoted, but I am not sure if that will make a difference.

I'll try it. At this point I'll try anything :)

Guess that wasn't it:

```
Parse error on line 41 of section Monitor in file /etc/X11/xorg.conf
        The HorizSync keyword must be followed by a list of numbers or ranges.
```

Oh well. Thanks for the suggestion though!

---

### Post by nickrout on 2009-04-04
I don't see any obvious errors in your log file. can't work that one out at all.

---

### Post by KeefTM on 2009-04-04
> **nickrout said:**
> I don't see any obvious errors in your log file. can't work that one out at all.

Yeah, the log doesn't show any errors either. I'm just lost on this one.

---

### Post by nickrout on 2009-04-04
You could try taking the modes line out of xorg.conf and see what it auto detects. For example in my log file it simply shows as using he highest available mode vis nvidia-auto-select like this:

> (II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(==) NVIDIA(0): Disabling 32-bit ARGB GLX visuals.


If your TV is providing good edid info it may "just work"

my screen as defined in xorg.conf says:

> Section "Screen"
         Identifier     "Screen0"
         Device         "Device0"
         Monitor        "Monitor0"
         DefaultDepth    24
         SubSection     "Display"
              Depth       24
         EndSubSection
EndSection


---

### Post by KeefTM on 2009-04-05
> **nickrout said:**
> You could try taking the modes line out of xorg.conf and see what it auto detects. For example in my log file it simply shows as using he highest available mode vis nvidia-auto-select like this:



If your TV is providing good edid info it may "just work"

my screen as defined in xorg.conf says:

I tried that first, but no dice. I only put the Modes in because the nvidia-auto-detect wasn't working. The auto detect was picking the correct resolution though. If I don't use the nvidia driver everything works, I can use the tv no problems. So odd.

---

### Post by KeefTM on 2009-04-05
Oddest thing. My TV has a 'Game Mode' and if I switch it on to that, I can see the window manager. But there still is a big "No signal" warning and if I switch the tv I lose the picture. I'm starting to think that this video card and my TV just aren't going to work together.

---

### Post by Monsieur Gonzalez on 2009-04-05
Well, my TV is a Panasonic, and I use it in 720p mode, with an Nvidia card (8400). I adapted it following some advice in the XBMC forums.

If you want to give it a try, the relevant parts of my xorg.conf are : 


Section "Monitor"
        Identifier     "Monitor0"
        VendorName     "Unknown"
        ModelName      "Panasonic-TV"
        HorizSync       15.0 - 68.0
        VertRefresh     23.0 - 61.0
        Option         "DPMS"
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Device0"
        Monitor        "Monitor0"
        Option         "NoLogo"
        Option         "DynamicTwinView" "false"
        Option     "ExactModeTimingsDVI" "True"
        Option         "FlatPanelProperties" "Scaling = Native"
        DefaultDepth    24
        SubSection "Display"
                Depth       24
        EndSubSection
EndSection

---

### Post by KeefTM on 2009-04-05
I tried those, no luck either. I'm sending an email to Nvidia, hopefully I can get in touch with someone that can help me. I can't figure out why the vesa drivers work at 1280x720 and nvidia's does not.

---

### Post by nickrout on 2009-04-05
nvnews.net run some good forums too.

---

### Post by KeefTM on 2009-04-05
> **nickrout said:**
> nvnews.net run some good forums too.

Cool, thanks!

---

### Post by KeefTM on 2009-04-08
Solved it! Here's how in case anyone wants to know.

The Nvidia drivers where picking the wrong settings for the TV. What I did was switched to the Nouveau drivers. These, of course, didn't work for the onboard 9400, but what they did do was give me the correct Modeline for my TV (in the Xorg.0.log file). I then used that Modeline with the official Nvidia driver. Success!

---

### Post by nickrout on 2009-04-08
> **KeefTM said:**
> Solved it! Here's how in case anyone wants to know.

The Nvidia drivers where picking the wrong settings for the TV. What I did was switched to the Nouveau drivers. These, of course, didn't work for the onboard 9400, but what they did do was give me the correct Modeline for my TV (in the Xorg.0.log file). I then used that Modeline with the official Nvidia driver. Success!

For future reference you should share your modeline with the forum!

Perhaps too the steps to get that modeline (your description is a little vague).

---

### Post by KeefTM on 2009-04-09
> **nickrout said:**
> For future reference you should share your modeline with the forum!

Perhaps too the steps to get that modeline (your description is a little vague).

Sure thing:

Modeline     "1280x720"  74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync

1) change driver to "nouveau" where it is currently "nvidia"
2) restart system (or just X)
3) check the Xorg.0.log file for a list of lines that contains "Modeline". It only found a few for my set, and it was after all the resolutions it tested. 
4) insert those modelines into the "Monitor" section of the xorg.conf
5) Add this to the "Device" section:

Option "UseEDID" "FALSE"
Option "UseEdidFreqs" "FALSE"

6) change driver back to "nvidia"
7) Under SubSection "Display", add 

Modes    "name of modeline you want to use (it's the resolution in quotes right after the word 'Modeline')"

8) reboot (or restart X)

That's what I did to get it working.

---

### Post by chong on 2012-02-02
Found this thread today after struggling with getting my new tv (same model as the OP) working last night. If you happen to still be monitoring this thread would you mind posting up your full xorg.conf file? I'll be trying your steps tonight. If I get it working I'll post up my full config too in case others have issues.

---

### Post by chong on 2012-02-02
I actually have the same motherboard as the OP. After trying the modeline in the last post on this thread I still get nowhere. The best I can get the nvidia driver to do is 640x480. This is in Ubuntu (mythbuntu i guess) 9.10.

---

### Post by nickrout on 2012-02-02
> **chong said:**
> I actually have the same motherboard as the OP. After trying the modeline in the last post on this thread I still get nowhere. The best I can get the nvidia driver to do is 640x480. This is in Ubuntu (mythbuntu i guess) 9.10.

look in the log

---

### Post by chong on 2012-02-02
So after pouring through logs and documentation for the past 4 hours here's what I came up with. My problem was that for whatever reason the driver wouldn't honor the modeline. It kept bailing with the following error:

```
(WW) NVIDIA(0): No valid modes for "1280x720"; removing.
```

So after pouring through google and the docs I found this little tidbit:

```
Option "ConnectedMonitor" "DFP"
Option "ExactModeTimingsDVI" "TRUE"
```

What those options do is to turn off the autodetect when the driver loads (I know I plugged it into HDMI, I don't need the driver to figure that out for me) and to actually force the Modeline that was posted above.

For the most part the modeline makes sense with what's in the TV manual. What doesn't make sense is the +hsync +vsync options. The TV manual for our TV states that for 1280x720 that these options are extraneous. So far it doesn't appear to be hurting anything so I'll keep it.

As promised here's my xorg.conf file:


```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#    InputDevice    "Keyboard0" "CoreKeyboard"
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"

#    # generated from default
#    Identifier     "Keyboard0"
#    Driver         "kbd"
#EndSection

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#    # generated from default
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
#    ModelName      "SHARP HDMI"
    HorizSync       15.0 - 46.0
    VertRefresh     59.0 - 61.0
        ModelName       "Samsung DLP"
        Modeline "1280x720"   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync
#       Option "ModeDebug" "TRUE"
EndSection

#Section "Device"
#    Identifier     "Configured Video Device"
#    Driver         "nvidia"
#    Option         "UseEvents" "1"
#    Option         "DPI" "100x100"
#    Option         "NoLogo" "1"
#       Option  "UseDisplayDevice"      "DFP"
#EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400"
#       Option  "DPI"   "100x100"
        Option "UseEDID" "FALSE"
        Option "UseEdidFreqs" "FALSE"
#       Option  "UseDisplayDevice"      "DFP"
#       Option  "NoLogo"        "1"
EndSection

#Section "Screen"
#    Identifier     "Default Screen"
#    Device         "Configured Video Device"
#    Monitor        "Configured Monitor"
#    DefaultDepth    24
#EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
        Option  "ConnectedMonitor"      "DFP"
        Option  "ExactModeTimingsDVI"   "TRUE"
#    Option         "metamodes" "1280x720 +0+0"
    SubSection     "Display"
        Depth       24
        Modes   "1280x720"
#       Modes   "1280x720_60.00"
    EndSubSection
EndSection

```

---

### Post by nickrout on 2012-02-02
> **chong said:**
> So after pouring through logs and documentation for the past 4 hours here's what I came up with. My problem was that for whatever reason the driver wouldn't honor the modeline. It kept bailing with the following error:

```
(WW) NVIDIA(0): No valid modes for "1280x720"; removing.
```

So after pouring through google and the docs I found this little tidbit:

```
Option "ConnectedMonitor" "DFP"
Option "ExactModeTimingsDVI" "TRUE"
```

What those options do is to turn off the autodetect when the driver loads (I know I plugged it into HDMI, I don't need the driver to figure that out for me) and to actually force the Modeline that was posted above.

For the most part the modeline makes sense with what's in the TV manual. What doesn't make sense is the +hsync +vsync options. The TV manual for our TV states that for 1280x720 that these options are extraneous. So far it doesn't appear to be hurting anything so I'll keep it.

As promised here's my xorg.conf file:


Excellent information, thanks for posting :)

---


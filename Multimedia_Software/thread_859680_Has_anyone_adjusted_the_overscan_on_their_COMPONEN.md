---
title: "Has *anyone* adjusted the overscan on their COMPONENT output with proprietary nvidia?"
date: 2008-07-14
forum: Multimedia Software
---

### Post by yonkiman on 2008-07-14
I've got a nice but old rear-projection HDTV.  The best quality inputs it has are component (no HDMI, no DVI).  I used it for years in 720p mode with WinXP with a custom modeline (1158x648), but the proprietary nvidia driver seems to insist on 1280x720.  This is a big inconvenience because it means the gnome menu bar and edges of large windows are not visible!

People have recommended I use the **Option  "TVOverScan" "0.8"** option in xorg.conf, and I've tried it many times, but it seems to be ignored - nothing ever changes.

From the reading I've done, it's starting to look like perhaps the "TVOverScan" function is only for svideo or composite.  I just want to know if that's correct.  

So...  Has *anyone* ever been able to adjust the overscan of their nvidia card using the proprietary nvidia driver *on the component output*?

---

### Post by brokenLockpick on 2008-07-15
I've adjusted it through the nvidia "x server settings" gui panel but it never saves to the xorg.conf.  8 is the default setting btw, takes me 13 to get rid of the black bars which I would guess is 1.3 in the conf file.

As an aside I have other problems with the component cable, the red channel seems not to be sending data so everything is like a washed out green/blue color (Cables are good they work fine when I boot into XP)

---

### Post by yonkiman on 2008-07-16
> **brokenLockpick said:**
> I've adjusted it through the nvidia "x server settings" gui panel

I've been all over that panel before and just went through it again tonight, and I can't find an overscan adjustment anywhere.  In advanced mode, basic mode - I don't see it.  Maybe I've got a blind spot - could you be a bit more specific about exactly where it shows up in your control panel?  

Maybe there's a config file for the x server settings GUI I need to track down...

Thanks for the response...it's given me SOME hope...

---

### Post by brokenLockpick on 2008-07-16
In my xserver control panel it's the last line from the bottom under the heading for GPU 0 subheading: TV-0. At the top of the menu that comes up to on the right half when you highlight tv-0 on the left half.

I can send you a screen shot if my description is unclear

---

### Post by yonkiman on 2008-07-17
> **brokenLockpick said:**
> In my xserver control panel it's the last line from the bottom under the heading for GPU 0 subheading: TV-0. At the top of the menu that comes up to on the right half when you highlight tv-0 on the left half.

Nope - it's not there for me.  I have:
TV Encoder: NVIDIA
TV Refresh Rate: 60.02Hz

Then a slider for Digital Vibrance (I hear that's still illegal in some states) and a slider for Image Sharpening.

I don't know if I need a screenshot, but I'd love to see your xorg.conf!

Thanks,
Fred

---

### Post by brokenLockpick on 2008-07-17
Part of my problem is that it doesn't seem to be writing to the xorg.conf file. I have to adjust the overscan each time I long on, if you know what section of the menu the overscan option is supposed to go under I can try to make it work manually and then let you know (would it be under the screen section?). I won't be able to post the file till after 4pm eastern time when I'm done with work.

---

### Post by yonkiman on 2008-07-17
> **brokenLockpick said:**
> if you know what section of the menu the overscan option is supposed to go under I can try to make it work manually and then let you know (would it be under the screen section?).

I'm pretty sure it's supposed to go under the screen section.  Good luck!

---

### Post by brokenLockpick on 2008-07-17
success! what it looks like you need is a bigger number than ".8"

when I put in 1.3 however the slider is now at twenty at boot maybe the number needs to go inside the quotes
Edit: I'm going to search to get the syntax right putting the number in the quotes put it back to 8 as the default

---

### Post by brokenLockpick on 2008-07-17
Ok I've managed to figure this out:

If you had the slider it would go between 1-20
I noticed for TVOverScan that

Slider       .conf
6              .3
14             .7
13             .65

and 13 was my target so I stopped it would seem that .5=1 .1=2 etc all the way to 1.0=20

so here's my xorg.conf file for ref
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
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

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NUL"
    HorizSync       31.5 - 80.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
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
    BoardName      "GeForce 7800 GT"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GT"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1280x1024 +0+0; CRT: nvidia-auto-select +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    Option	   "TVOverScan" ".65"
EndSection

```

If you wouldn't mind posting yours I'd appriciated it as it may help me iron out this blue tint prob (seems like the red channel sends nothing at all)

Edit: When I fixed my blueish screen problem the TVOverscan option seems to have ceased to have an effect. I am now stuck with my tv overscanning by itself further than I want it to. I will try to find a workaround. I'm already thinking a custom resolution may be the solution (you said it didn't work but I've gotta try something), because I noticed that after I forced HD component out to work properly with
```

    Option         "TVOutFormat" "Component" 
    Option         "TVStandard" "HD720p"

```
the resolution was automatically set to 800x600 which was surrounded by blank space.

It'll take me a while to post the solution I want to try and force 1080i/p as well to see if overtaxes my system before I bother tweaking a custom rez as a fix.

---

### Post by yousillygoose on 2008-07-17
I have a thread alive that asks pretty much the same question.  My theory behind it is that if the linux Nvidia driver for your given card doesn't detect that your model card has the overscan ability than it omits the option in nvidia-option.  I know, though, that my card has the ability because it can do it in windows.  This leads me to the conclusion that linux nvidia drivers are still far behind for some cards and we will not be able to adjust overscan no matter how hard we try until they update the drivers to solve the problem.

---

### Post by brokenLockpick on 2008-07-17
@ yousillygoose:

yeah I'm coming to that conclusion myself, for now I just put in two side toolbars with nothing on them so that I can get at the scroll bar when maximized 

and an empty one at the very top and very bottom so that the default toolbars are now on the screen, had to unlock the objects/menues on them and move them in a bit but it will work for now

---

### Post by yousillygoose on 2008-07-17
Yea.  The only reason I want to do this is so I can output movies onto a tv that is bigger than my laptops screen so my family can watch it.  I know that the overscanning that is happening is minimal and probably won't ruin a movie but the OCD side of me doesn't want to risk it.

---

### Post by brokenLockpick on 2008-07-17
> **yousillygoose said:**
>  ...OCD side... 

I hear ya. I've got a workaround that makes it look normal for computing purposes, I'm actually more worried about screwing up the temporary fix because it was irritating to set up and my goal is to have a multiseat  that is essentially an HTPC and normal desktop simultaneously. (ie two monitors tied to one keyboard/mouse combo and the tv paird with another set of input devices). Getting this properly sorted will make the rest of the configuration loads easier.

---

### Post by yousillygoose on 2008-07-17
Hahaha, sounds all like a good plan.  I want to eventually set up an entertainment center that flows through a crappy old computer as a server.  I would be able to just my laptop as a remote controller and it would be pretty nice.

---

### Post by TacticalTurtle on 2009-05-31
Okay, I'm still slightly new to the whole Ubuntu thing but I am experiencing the same issue. My second monitor is a TV and I have it working but I too have the same blue tint on the tv. When booted in windows the component cable works fine, so my cable is good. I'm really lost with that whole override option you all are discussing. Where do I manually add in the override option at in the xorg.conf?

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Thu Jun  5 09:27:12 UTC 2008

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
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "VIZ VW26L HDTV10F"
    HorizSync       31.0 - 70.0
    VertRefresh     50.0 - 85.0
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
    BoardName      "GeForce Go 6150"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: nvidia-auto-select +1440+0, DFP: nvidia-auto-select +0+0"
EndSection

```

---


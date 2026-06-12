---
title: "nvidea 9500gt tv out problems"
date: 2011-07-24
forum: Multimedia Software
---

### Post by jrbless on 2011-07-24
This weekend, I decided to upgrade my (very old) ubuntu 9.04 box all the way up to 11.04.  This computer is used as a mythtv frontend/backend system.  In 9.04, the video-out to tv worked fine, but in 11.04 I'm not able to get it configured correctly.

What I'm getting after it loads X is this:
1. The tv output is all black and white
2. The screen is refreshing very poorly (shakes and has a "ghost" of everything being drawn about 2-3 inches to the right of the brighter image)

Here are the details of what I have (and used to have):
nVidea 9500GT pci-e graphics card
tv-out is through component output (the red/green/blue cables)

dkms status
nvidia-current, 270.41.06, 2.6.38-10-generic, i686: installed

Here is my old /etc/X11/xorg.conf (that used to work perfectly in 9.04):
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "TVOutFormat"   "COMPONENT"
        Option  "NoLogo"        "1"
        Option  "UseEvents"     "1"
        Option  "ConnectedMonitor"      "TV"
        Option  "DPI"   "100x100"
        Option  "TVStandard"    "HD720p"
EndSection


Here is the new /etc/X11/xorg.conf that I'm not able to get configured correctly:
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
        Option  "TVStandard"    "HD720p"
        Option  "TVOutFormat"   "COMPONENT"
        Option "UseDisplayDevice" "TV"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


I don't see any errors in /var/log/Xorg.0.log (I can provide output if necessary).  It does show that it loaded the options w/o any problems.

Trying to simply use the 9.04 xorg.conf doesn't work (I don't get a picture at all).  I've also tried removing the line "option DPMS" with no results.  I'm out of ideas and could really use some help.  Anyone have an idea?

Thanks in advance,
James

---

### Post by papibe on 2011-07-24
How this xorg.conf was generated? Is it the one you had before?

If that's the case, I would back it up, and try to generate a new one by using the updated version of the nvidia control panel:
```
$ gksudo nvidia-settings
```
Once you have a working configuration, save it by choosing 'Save X Configuration File'.

BTW, Which output are you using to connect to the TV? Which kind of cable? Which TV input are you using?

I also have a 9500GT :) I'm using one of the DVI outputs, a DVI to HDMI cable, to my Sony Bravia's HDMI input reserved for a PC. The audio is going in a separate cable (a miniplug to an stereo RCA).

I hope it helps.

---

### Post by BicyclerBoy on 2011-07-25
It would make sense to post the /var/log/Xorg.0.log..
You probably have done this but..can you check the cable is plugged in completely at both ends..

Have you tried commenting out the metamode line ?
The TVOut video mode pool is fixed & ignores the horz & vertical freq data & you have specified 720p60..

Have you tried "HD480p" ?

The B&W image you have sounds like the incorrect TV standard (althou meaningless for HD).

Likely makes no difference but Xorg doc implies that the lines:
1. Option  "TVStandard"    "HD720p"
        2. Option  "TVOutFormat"   "COMPONENT"
        3. Option "UseDisplayDevice" "TV"
should not be in the monitor section
1. & 2. & 3. should be in the screen section.

In the old xorg file the Option "DPI" should been in the screen section.

---

### Post by jrbless on 2011-07-25
I figured it out.  The xorg.conf that I'm using is good.  The problem ended up being a loose cable connection on the video card.  I feel really foolish...

Thank you for asking about the type of cable connection.  It got me pointed in the right direction :)

James

---


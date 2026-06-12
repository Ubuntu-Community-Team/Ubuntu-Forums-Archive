---
title: "xorg.conf USB2VGA bafflement"
date: 2009-11-03
forum: Multimedia Software
---

### Post by jezzah on 2009-11-03
I've been trying to get a duel display working using a usb2vga adapter for a minimac running ubuntu 9.10

I attempted to follow what was implied here,

[https://help.ubuntu.com/community/USB2VGA](https://help.ubuntu.com/community/USB2VGA)

and when that didn't do as expected (I got the second screen displaying my default background image but nothing else would work in that screen) I followed this.

[http://ubuntuforums.org/showthread.php?t=260863](http://ubuntuforums.org/showthread.php?t=260863)

After messing around and reinstalling drivers I eventually got to the point where both screens now display. Only instead of what I was expecting (a large desktop where I can drag windows from one screen to another) I've somehow ended up with two xsessions each with there own desktops and incapable of talking to each other (the only thing that moves between the two is the mouse).

Somehow using two graphics cards I'd like to change the behaviour to have a large desktop spanning two screens rather than what appears as two separate sessions.

Thanks in advance,

attached is my xorg.conf file

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Section "ServerFlags"
     Option        "DontZap" "false"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
        Option         "AccelMethod"         "EXA"
        Option         "MigrationHeuristic"     "greedy"
EndSection

Section "Device"
 Identifier "Device[SISUSBVGA]"
 VendorName "SiS" # Value does not matter
 BoardName "SiS" # Value does not matter
 Driver "sisusb"
 Option "DesktopSetup" "horizontal"
 Option "Mode2" "1280x1024"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Monitor"
 Identifier "Monitor[SISUSBVGA]"
 VendorName "Monitor Vendor" # value does not matter
 ModelName "Monitor Model" # value does not matter
 VertRefresh 50-75
 HorizSync 30-90
EndSection

Section "Screen"
    Identifier    "Screen0"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "Screen"
 Identifier "Screen1"
 Device "Device[SISUSBVGA]"
 Monitor "Monitor[SISUSBVGA]"
 DefaultDepth 16
 SubSection "Display"
  Depth 16
  Modes "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth 8
  Modes "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth 24
  Modes "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen 0 "Screen0"
        Screen 1 "Screen1" RightOf "Screen0"
EndSection

---


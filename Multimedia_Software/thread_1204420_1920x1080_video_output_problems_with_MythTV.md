---
title: "1920x1080 video output problems with MythTV"
date: 2009-07-04
forum: Multimedia Software
---

### Post by ethereal on 2009-07-04
Happy 4th all,

I'm having issues configuring video output on my mythtv box.  I've been working on this issue on and off for a year, and I usually get frustrated with it and give up.  I'm trying to output 1080P video (although 720P would be acceptable if I could get that to work even) to my samsung HLS-5087W TV via my nvidia 6200 card.  At the present I have no capture cards installed, I'm only interested in video playback for now.

I can connect (& have tried) both vga connection to the tv, and a dvi->hdmi connection.  The vga seems to work better as I can achieve 1280X1024 output, the dvi->hdmi connection stops at 640x480 as of yet.

I have the nvidia drivers installed and in use.  I've tried editing my xorg.conf to reflect this helpful conf that matches my tv: [http://www.mythtv.org/wiki/Samsung_HL-S5087W]("http://www.mythtv.org/wiki/Samsung_HL-S5087W").  I've also tried the suggestions from this post: [http://ubuntuforums.org/archive/index.php/t-676701.html]("http://ubuntuforums.org/archive/index.php/t-676701.html").  Neither have worked well for me.

I'll take any advice you've got, guides for dummies, whatever.  Everything I've tried has failed, and I'm about to give up and try knoppmyth, but I prefer to stick with mythbuntu, as I use ubuntu for my desktop, and just have more experience with it.

Thanks for your help!

Here are the system specs in case its relevant:
CHAINTECH AV-710 7.1 Channels PCI Interface Sound Card - 
XFX PVT44AWANG GeForce 6200 256MB 64-bit GDDR2 AGP 8X
1GB ram
GIGABYTE GA-K8VM800M 754 VIA K8M800 Micro ATX AMD Motherboard
AMD Athlon 64 3400+ Venice 2.4GHz

---

### Post by ethereal on 2009-07-04
here's my current xorg.conf, based on the second link in my previous post:
```
Section "ServerFlags"
Option "Xinerama" "0"

# 9/13/07 Added due to howto:
# http://www.mythtv.org/docs/mythtv-HOWTO-22.html
AllowMouseOpenFail # allows the server to start up even if the mouse doesn't work
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
Option "NoPM" "1"
EndSection

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
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
EndSection

Identifier "Monitor0"
VendorName "Unknown"
ModelName "SAMSUNG"
HorizSync 30.0 - 68.0
VertRefresh 59.0 - 61.0
ModeLine "1800x980" 146.5 1800 1912 2104 2408 980 981 984 1014 -hsync +vsync
Modeline "1800x1000" 149.54 1800 1912 2104 2408 1000 1001 1004 1035 -HSync +Vsync
Modeline "1920x1020" 163.22 1920 2040 2248 2576 1020 1021 1024 1056 -HSync +Vsync
Modeline "1920x1080" 172.80 1920 2040 2248 2576 1080 1081 1084 1118 -HSync +Vsync

## Added 20070922, source: http://gentoo-wiki.com/HOWTO_nVidia_Drivers#Unable_to_validate_video_mode s
# Option "Metamodes" "1920x1080"

# 9/13/07 Disabled due to howto:
# http://www.mythtv.org/docs/mythtv-HOWTO-22.html
#Option "DPMS"
EndSection

Section "Device"
Identifier "Videocard0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "All"
Option "DPI" "100 x 100"

# Added 20070922, source: https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/105957
#Option "UseEDID" "False"
#Option "UseEDID" "False"
Option "ModeValidation" "NoDFPNativeResolutionCheck, NoMaxSizeCheck"
Option "NoLogo" "True"
Option "ConnectedMonitor" "DFP"
Option "TVStandard" "HD1080p"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
#Option "metamodes" "1800x980_60.00 +0+0; 1024x768 +0+0"
#Option "metamodes" "1920x1080"
SubSection "Display"
Depth 24
Modes "1920x1080" "1800x1000" "1800x980" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
# The Samsung doesn't overscan if you turn on the 'just scan' setting, 1x1 pixel mapping.
##Virtual 1800 1000
Virtual 1920 1080
EndSubSection
EndSection

```

---

### Post by ethereal on 2009-07-05
Anyone have any good ideas?  I keep trying various ideas I see in other forums, but nothings helped yet.  I've wasted a solid 8 hours of the holiday weekend on this project.  Is there a definitive guide or technique I can use?  :confused:

---


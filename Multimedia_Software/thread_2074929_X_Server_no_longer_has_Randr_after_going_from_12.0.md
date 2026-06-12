---
title: "X Server no longer has Randr after going from 12.04 to 12.10"
date: 2012-10-22
forum: Multimedia Software
---

### Post by _glook on 2012-10-22
Hello,

I recently updated to 12.10 on Kubuntu and have run into a strange issue. I have a setup where I have a laptop with a vertical monitor attached. I'm running this on a MacBook Pro 6,2 and am using nvidia's proprietary driver. After upgrading, my vertical monitor no longer is rotated vertically.

So I tried running xrandr directly and it returns immediately while printing out the text "RandR extension is missing". I decided to try going to the system settings. When I go into System Settings > Display and Monitor, it takes me to "Size & Orientation", which, instead of options and such, simply has the text "Your X Server does not support resizing and rotating the display. Please update to version 4.3 or greater. You need the X Resize, Rotate, and Reflect extension (RANDR) version 1.1 or greater to use this feature." I thought maybe Compiz was messing things up and somehow got enabled when I upgraded, so when I went to Desktop Effects, it tells me "Required X extensions (XComposite and XDamage) are not available."

Everything has been pointing to somehow my X server being borked. So I go into Muon and try and update xorg and server and all of them say they are installed and the latest version. I went ahead and marked for reinstallation some packages, including xorg, nvidia-current, xserver-xorg, xserver-xorg-core, and xserver-common. Reinstalling these didn't seem to do anything.

This leads me to believe that the upgrade broke X-server, and re-installation is not actually reinstalling. Does anyone have any ideas?

This is what my xorg.conf looks like.

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      1  "Screen1" 0 1050
    Screen      2  "Screen2" 1440 0
    Option         "Xinerama" "1"
EndSection


Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Apple Color LCD"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "NEC PA271W"
    HorizSync       31.0 - 94.0
    VertRefresh     50.0 - 87.0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
    BusID          "PCI:1:0:0"
    Screen          0
    Option  "Coolbits" "1"
    Option  "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerLevel=0x3; PowerMizerDefaultAC=0x3"
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
    BusID          "PCI:1:0:0"
    Screen          1
    Option "Rotate" "Left"
    Option  "Coolbits" "1"
    Option  "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerLevel=0x3; PowerMizerDefaultAC=0x3"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-2: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```


Edit: So I managed to get to a certain point. I reinstalled xserver using this: [http://john-willis.com/2010/01/remove-and-reinstall-xserver-on-ubuntu-9-10/](http://john-willis.com/2010/01/remove-and-reinstall-xserver-on-ubuntu-9-10/) and I'm no longer getting the issue in Display & Orientation. It hasn't fixed my issue, but I'm at least moving forward. I'm going to take a look at the xorg and see if it's changed.

If anyone else is looking at this and trying to get to the command line without xorg, hit CTRL+ALT+F1 on your desktop. Do "sudo init 3" to get rid of the current running xserver and then follow the directions in the website listed above.

---

### Post by _glook on 2012-10-22
So, what worked for me was to not have an xorg.conf. My nvidia driver is "active but not currently in use" which is fine with me, honestly. I ended up using the Size and Orientation in the settings menu and ignoring the nvidia xserver tool entirely.

So yeah, after 4 hours, I'm finally where I started before the upgrade and can get back to work :).

Marking as fixed.

---

### Post by Phasmus on 2012-10-22
I'm not 100% sure this is related to your issue, but it looks like as of a couple days ago xinerama and xrandr are no longer allowed to be used at the same time: [http://www.nvidia.com/object/linux-display-ia32-304.60-driver.html](http://www.nvidia.com/object/linux-display-ia32-304.60-driver.html)

---


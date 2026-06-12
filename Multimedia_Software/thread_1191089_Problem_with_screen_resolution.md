---
title: "Problem with screen resolution"
date: 2009-06-18
forum: Multimedia Software
---

### Post by indistinguishible on 2009-06-18
Hi all.
I've installed Ubuntu 9.04 (i've been used Debian before) and got a problem.
I have Nvidia FX 5500 video and an LCD TV Elenberg instead of monitor and always run it at 1024x768 in Win.
After the installation was complete Gnome successfully started with 800x600 resolution. I've tried to set the resolution to 1024x768 but there wasn't such choice. Then Ubuntu suggested me to use native NVidia driver (173) and i tried to use it. After the driver was installed and PC rebooted Gnome started at 640x480 and only two modes I can select: 640x480 and 320x240. After a long time trying to install/uninstall different drivers and searching different forums I've decided that the problem's not in driver I use (when XServer starts in failsafe mode it has 800x600 and when it starts normally - only 640x480 or 320x240) but rather in TV that I use instead of monitor - it just can't correctly autotune.
So I tried to test 1024x768 resolution with xrandr and get next results:
```
  1024x768_60.00 (0x1a8)   63.5MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.8KHz
        v: height  768 start  771 end  775 total  798           clock   59.9Hz
```Then I tried to edit xorg.conf file but it doesn't effect at all. Here it is:
```
Section "Monitor"
    Identifier    "Configured Monitor"
    Modeline    "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
    Option    "PreferredMode" "1024x768_60.00"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes           "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
EndSection
```Probably I've missed something in xorg.conf or somewhere else. Need help.

---

### Post by xc3RnbFO8P on 2009-06-18
Try System> Preferences> Display (choose No) and change the resolution

---

### Post by indistinguishible on 2009-06-18
Already tried. Only 320x240 and 640x480 avaliable. I've even tried completely remove NVidia drivers and use default driver - works at 800x600 but the same 640x480 and 320x240 are only avaliable.
P.S. System>Preferences>Display says that Display is unknown.

---

### Post by indistinguishible on 2009-06-18
Somewhere on the WEB I've seen that somebody had had the same problem too and that he'd used displayconfig-gtk to solve it. But display-config-gtk is not in Ubunta any more and even can't be installed on it.

---

### Post by indistinguishible on 2009-06-20
Finally I've fixed it. In fact I was missing something in xorg.conf.
It appeared that HorizSync and VertRefresh are required in section "Monitor". So I've just got that values from xrandr output and set HorizSync and VertRefresh to the small range which includes that values. Final xorg.conf looks like this:
```
Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync 32.0 - 55.0
    VertRefresh 43.0 - 60.0
    Modeline    "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
    Option    "PreferredMode" "1024x768_60.00"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes           "1024x768"
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
EndSection
```

---


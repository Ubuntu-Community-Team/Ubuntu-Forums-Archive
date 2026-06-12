---
title: "Custom Resolution"
date: 2011-02-14
forum: Multimedia Software
---

### Post by jonnymd on 2011-02-14
I have researched to find a way to create a custom resolution (most helpful info I found was here: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)).  Here is what I am able to do successfully.

```

xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
xrandr --addmode VGA-1 "1600x900_60.00"
xrandr --output VGA-1 --mode "1600x900_60.00"

```

This changes my resolution dynamically and it looks great.  However, no matter how I try to modify settings I cannot find a way to make the changes persist.  I have included the above exactly as written in a file I created named .xprofile.

I created the following  /etc/X11/xorg.conf file.

```

Section "Monitor"
    Identifier      "External VGA"
    Modeline        "1600x900_60.00"  118.25 1600 1696 1856 2112 900 903 908 934 -hsync +vsync
    Option          "PreferredMode" "1600x900_60.00"
EndSection
Section "Device"
    Identifier      "Device0"
    Driver          "nouveau"
    Option          "External VGA"
EndSection
Section "Screen"
    Identifier      "Primary Screen"
    Device          "Device0"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1600x900" "1024x768" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Primary Screen"
EndSection

```

Niether seems to have any effect. The computer just reboots into 1024x768.  I also modified the mode in screen section to read "1600x900_60.00" because I am not sure of the convention needed there.  Neither method works.  I am not using the nvidia binary (closed) driver at this point.  I have tried that and found it breaks xrandr and just complicates the process.

Any ideas or tips to keep this setting persistent.  Frustrating that I know my monitor can handle it yet it is not in a GUI drop down.  Any help is appreciated.  I'm relatively new to Linux but well versed in technology and can follow even complex directions (Deep knowledge of Windows/Mac)...

I'm running Ubuntu 10.10 on an HP Laptop with an NVidia card and RGB connection to a Vizio 37" flat panel tv.  I don't care about the laptop screen, just the tv.

---

### Post by BicyclerBoy on 2011-02-15
There is no link between the monitor  & screen sections..
You list other internal named modes in the screen section.

Try this type of arrangement of modes section (named) using your setup..

```

Section "Modes"
    Identifier         "myHDTV"
##    Modeline     "2048x1152i50"  72.75 2048 2080 2368 2400 1152 1176 1187 1211 +hsync +vsync interlace
    ModeLine     "1920x1080i60" 88.7   1920 2208 2252 2600 1080 1092 1100 1135 +hsync +vsync interlace
    Modeline     "1920x1080i50" 70.25 1920 1952 2440 2472 1080 1101 1113 1135  +hsync +vsync interlace
    ModeLine     "1280x720p60"  73.78  1280 1312 1592 1624  720  735  742  757 +hsync +vsync
    ModeLine     "1024x576p50"  37.19  1024 1056 1192 1224  576  588  593  605 +hsync +vsync
    ModeLine     "848x480p60"   31.23   848  880  992 1024  480  490  495  505 +hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Philips"
    ModelName      "32PW8808"
    UseModes       "myHDTV"
    HorizSync       22.0 - 47.0
    VertRefresh     48.0 - 65.0
#    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 240"
    Screen         1
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "ModeValidation" "AllowInterlacedModes"
    Option         "UseEDID" "FALSE"
    Option         "UseDisplayDevice" "CRT-0"
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080i60" "2048x1152i50" "1280x720p60" "1024x576p50" "848x480p60"
        Option     "PreferredMode" "1920x1080i60"
    EndSubSection
EndSection

```

You do not necessarily need the EDID mode validation nonsense...
Custom modeline "names" must be unique (not same as internally defined ones).

---

### Post by jonnymd on 2011-02-15
Thanks for the input.  I can't believe after all the manipulating I left out the monitor section.  The 1920x1080i setting didn't work on startup.  However, by putting 1440x900 I got it to boot twice.  It froze each time then wouldn't boot thereafter.  Finally, the 1920x1080 section was available in the settings>monitor section, which I selected, then set as default.  That did the trick.  My xorg.conf still reads completely different but it's working so I'm not changing a thing.  I don't get it but it's stable and exactly how I want.  Thank you.

---

### Post by BicyclerBoy on 2011-02-16
My xorg.conf was just a template...

You must put your modeline in place of mine...
All my modelines are custom weird timings for CRT widescreen geometry etc..

If you do not need a custom modeline then use the internal defined mode names..

Again: It is just a template for a working arrangement

---


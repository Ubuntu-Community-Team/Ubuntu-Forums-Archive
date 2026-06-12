---
title: "multiple monitors - strange behavior"
date: 2010-06-23
forum: Multimedia Software
---

### Post by OmahaVike on 2010-06-23
Hoping someone can help me understand, and perhaps correct.  I am trying to set up three monitors into a single desktop environment (similar to what xinerama did) but I'm trying to use the included radeon driver and configure it all through xorg.conf.

In searching, I ran across this very helpful thread:  [http://ubuntuforums.org/showthread.php?t=1431893](http://ubuntuforums.org/showthread.php?t=1431893)

I have functionality, which we'll get to in a minute, in all three monitors, but I'm experiencing some very strange results which I'm praying someone will be able to assist in clearing up.

Physical configuration:  Left monitor and right monitor hooked up to a PCIE dual head card.  Middle monitor hooked up to onboard VGA.  All ATI radeons.  Proprietary driver not installed (yay!).

Here is what I experience as I drag my mouse from left to right, and then back again....

On left monitor, the mouse traverses fine.  Upon reaching the rightside of the monitor, the mouse icon skips over the middle monitor and then onto the right monitor.  If I do not traverse the entire width of my right monitor, and then drag the mouse to the left, the mouse icon shows up in the left monitor.  One might think "okay! so, the middle monitor is not being recognized by X".  Well, get this:  If I continue to pull my mouse all the way over to the right hand side of my right monitor, and then bring it back left again, it shows up into the middle monitor.

Long and short - mouse icon skips over the middle monitor if it's traveling east, but only lands back in the middle monitor if, and only if, the mouse goes all the way to the east and then back west again.

I have included my xorg.conf file below.

I *really* appreciate anyone who has any insight.  THANK YOU!!!!

```

Section "ServerLayout"
    Identifier     "Basic Setup"
    Screen      0  "Screen1"
    Screen        "Screen2" RightOf "Screen1"
    Screen        "Screen3" RightOf "Screen2"
EndSection

Section "Device"
    Identifier  "DeviceLeft"
    Driver      "radeon"
    BusID       "PCI:2:0:0"
EndSection
Section "Device"
    Identifier  "DeviceCenter"
    Driver      "radeon"
    BusID       "PCI:1:5:0"
EndSection
Section "Device"
    Identifier  "DeviceRight"
    Driver      "radeon"
    BusID       "PCI:2:0:1"
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "DeviceLeft"
    DefaultDepth  24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection
Section "Screen"
    Identifier "Screen2"
    Device     "DeviceCenter"
    DefaultDepth  24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection
Section "Screen"
    Identifier "Screen3"
    Device     "DeviceRight"
    DefaultDepth  24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

```

---


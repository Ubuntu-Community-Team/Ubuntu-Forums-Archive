---
title: "video and graphics settings"
date: 2008-11-15
forum: Multimedia Software
---

### Post by emanresu on 2008-11-15
i'm mostly a new user. i was trying to use a statistics program and when i implemented the graphics device for the program, i could not see the image that was supposed to be in the device's window. these were my settings:
> from xdpyinfo:
screen #0:
  dimensions:    1280x800 pixels (289x21 millimeters)
  resolution:    112x968 dots per inch

and> 
from xorg.conf
Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "*Generic* Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Monitor         "*Configured* Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

and according to /var/log/Xorg.0.log: 
DPI set to (96,96)

after some advice, i went and changed xorg.conf by adding this:
        > DisplaySize     "339x212"

now it looks like this:
> Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express 
Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "*Configured* Monitor"
        [B][I]DisplaySize     "339x212"
[/I][/B]        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Monitor         "*Configured* Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

so now xdpyinfo says this too:
> 
screen #0:
  dimensions:    1280x800 pixels (*332x212* millimeters)
  resolution:    *98x96* dots per inch


this alteration has allowed me to use the graphics device window with the stat program. 

when i restarted Ubuntu, it gave me a warning about being in a low resolution. i put the computer on suspend and when i tried to restart it, the login window was so dim, i didn't the computer was waking up. now that i've tried to explain the changes, can someone tell me, are these changes to the video/graphics settings gonna set me up for a problem? or should i assume that since i've restarted a couple of times and nothing else appears altered that it will all be fine?

---


---
title: "Resolution won't go higher than 1024x768"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by kuriharu on 2006-06-04
Hello,

My laptop supports up to 1680x1050 resolution in Windows. I can choose resolutions higher than 1024x768 in Ubuntu, but the screen gets distorted. I have an ATI Mobility Raedon 9700 and I am using the ati driver in xorg.conf. The only refresh rate I can choose in Dapper is 61 Hz.

If anyone has any clues, please let me know. This is what's set in xorg.conf:

Section "Device"
        Identifier      "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

---

### Post by kuriharu on 2006-06-04
Found the solution; link for installing binary drivers for ATI fixed it. Thanks, Ubuntu!

---


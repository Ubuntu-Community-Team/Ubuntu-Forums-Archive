---
title: "ACER AL2016WS 20&quot; with Intel Corporation 82865G (widescreen problem)"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by nirux on 2006-09-05
Can't get the widescreen 1680x1050 resolution working :(
1600x1200 is working but I want widescreen...

Please help me with easy instructions to get this thing to work.

Monitor: ACER AL2016WS 20"
Computer: Dell Optiplex with Intel Corporation 82865G graphic controller

```

...
Section "Device"
        Identifier      "Intel Corporation 82865G Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "AL2016W"
        Option          "DPMS"
        HorizSync       31-84
        VertRefresh     56-86
        #did not work: "1680x1050_60.00" 214.51 1680 1800 1984 2288 1050 1051 1054 1103 -HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82865G Integrated Graphics Controller"
        Monitor         "AL2016W"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1600x1200" "1280x1024"
        EndSubSection
EndSection
...

```

---

### Post by nirux on 2006-09-06
anyone? please help

---

### Post by nirux on 2006-09-06
new try with sudo dpkg-reconfigure xserver-xorg

did not work ](*,) 

in the gnome -> system -> resolution it's still 1600x1200 1280x1024 ...

please help

```

...
Section "Device"
        Identifier      "Intel Corporation 82865G Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "AL2016W"
        Option          "DPMS"
        HorizSync       30-82
        VertRefresh     56-76
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82865G Integrated Graphics Controller"
        Monitor         "AL2016W"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050" "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050" "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050" "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050" "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1680x1050" "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1440x900"
        EndSubSection
EndSection
...

```

---

### Post by bigblondbear on 2006-09-06
See if 915resolution works for you.

---

### Post by nirux on 2006-09-07
> **bigblondbear said:**
> See if 915resolution works for you.

installed 915 from synaptic, did not work :(

still 1600x1200

---

### Post by nirux on 2006-09-07
anyone got 1680x1050 widescreen to work with Intel 82865G ?? can't find any solution :-?

---


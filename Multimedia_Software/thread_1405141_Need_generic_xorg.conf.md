---
title: "Need generic xorg.conf"
date: 2010-02-12
forum: Multimedia Software
---

### Post by weaver4 on 2010-02-12
I am looking for a generic vesa driver xorg.conf file that will work with most any 1024x768 monitor.  This is for a network appliance and our field people have many different type of monitors.  This product will mostly be used "headless" but sometimes our field people will plug in a monitor.  The intel driver will not even start x without a monitor plugged in so I found it necessary to go to the vesa driver.

```

Section "Device"
        Identifier      "Configured Device"
        Driver  "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 31-61  
        VertRefresh 50-75
        Modeline "1024x768" 25.20 640 688 784 800 350 410 412 449
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Device"
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

```

---

### Post by weaver4 on 2010-02-15
bounce

---


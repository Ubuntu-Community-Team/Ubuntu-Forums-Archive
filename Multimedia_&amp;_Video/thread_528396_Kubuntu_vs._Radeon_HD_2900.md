---
title: "Kubuntu vs. Radeon HD 2900"
date: 2007-08-17
forum: Multimedia &amp; Video
---

### Post by jdeisenberg on 2007-08-17
I'm trying to get Kubuntu to display wide screen resolutions with a Sapphire Radeon HD 2900XT with 1GB video RAM. Here's the relevant portion of xorg.conf:

Section "Device"
        Identifier      "ATI Technologies Inc ATI Default Card"
        Driver          "vesa"
        BusID           "PCI:7:0:0"
        Option          "UseFBDev"              "true"
EndSection


Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc ATI Default Card"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Yet, whenever I go to System Settings -> Monitor and Display, I see only 1280x1024 as the largest available setting.  Where have I gone wrong?

---

### Post by bakster on 2007-08-17
I just checked.There is no driver  support  for ATi X2000 series card yet,so you r stuck with vesa driver.I'm not sure if is it even possible to change vesa xorg settings.

---

### Post by hughjake on 2007-09-12
AMD ATI have now released drivers for Linux for the 2000 series cards!!

---


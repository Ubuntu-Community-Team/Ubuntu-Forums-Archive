---
title: "Twinview dual monitor refresh rate stuck at 50Hz?"
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by monkeylytics on 2006-06-25
After much head-banging, Googling, etc, I finally got a dual monitor Twinview working on my Cornerstone p1450 CRT and my Samsung SyncMaster 940B LCD with a GeForce 6600.

The problem though is that the refresh rate seems to be stuck at 50Hz. ](*,) The Cornerstone p1450 CRT was the first monitor running on Dapper. It ran at 85Hz fine with minimal Monitor setup.

Section "Monitor"
        Identifier      "p1450"
        Option          "DPMS"
EndSection

When I added the SyncMaster 940B and finally got Twinview working, now, the Gnome Screen Resolution Panel is showing 2560x1024 (1280 x2 and 1024) which is correct but the 50Hz has me baffled. I'd rather not burn out my eyes at 1280x1024 at 50Hz on the CRT. :(

Are both monitors really running at 50Hz? I'd like the CRT to be running at 85Hz and the LCD running at 60Hz. Where can I check to find the real refresh rates? I can't find it in the Nvidia Settings application. Can't find it in Xorg.0.log either.

More importantly, how do I set the CRT at 85Hz and the LCD at 60? Even if I set my xorg.conf manually with _85 on the resolutions or setting the VertRefresh manually, I still get this 50Hz issue. A few hours Googling or searching the forums hasn't helped.

The relevant parts of my xorg.conf are below. Any help appreciated.


Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "TwinView"      "yes"
        Option          "TwinViewOrientation"   "CRT LeftOf DFP"
        #Option         "ConnectedMonitor"      "p1450,Monitor1"
        Option          "MetaModes" "1280x1024_85,1280x1024;1024x768_85,1024x768"
        #Option "UseEdidFreqs" "FALSE"
        #Option "UseEDID" "FALSE"
        #Option "ModeValidation" "NoEdidModes"

EndSection

Section "Monitor"
        Identifier      "p1450"
        Option          "DPMS"
        HorizSync       31-96
        VertRefresh     85
EndSection

Section "Monitor"
        Identifier   "Monitor1"
        VendorName   "Samsung"
        ModelName    "Samsung"
        Option      "DPMS"
        VertRefresh     60

EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV43 [GeForce 6600]"
        Monitor         "p1450"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024_85" "1024x768_85" "800x600" "640x480"
        EndSubSection
EndSection

---

### Post by monkeylytics on 2006-06-26
Eh. It turns out that the monitors are running at the proper frequency after all. Still couldn't find a way to exactly see what rates the monitors were running at through Linux, but I just checked the monitors directly via their respective monitor control panels, and the video card is running the CRT at 85 and the LCD at 75. 

I'm surprised that this sort of information and setting the refresh rates weren't available in the Nvidia Settings application though.

---

### Post by Yfrwlf on 2006-12-16
> **monkeylytics said:**
> Eh. It turns out that the monitors are running at the proper frequency after all. Still couldn't find a way to exactly see what rates the monitors were running at through Linux, but I just checked the monitors directly via their respective monitor control panels, and the video card is running the CRT at 85 and the LCD at 75. 

I'm surprised that this sort of information and setting the refresh rates weren't available in the Nvidia Settings application though.

This seems to be a common problem.  The resolution setting program in Gnome not showing you what your real refresh rate is.  Mine shows 50 as well, but I know it's around 85 from how smooth it looks.

---


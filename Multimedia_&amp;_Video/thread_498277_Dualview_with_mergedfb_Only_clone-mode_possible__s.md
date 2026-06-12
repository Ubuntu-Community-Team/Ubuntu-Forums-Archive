---
title: "Dualview with mergedfb: Only clone-mode possible / scrolling problem"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by Meister_Eder on 2007-07-11
Hi, I am trying to setup Dualview (laptop screen + 19" CRT) with an ATI X300 card, open source drivers. When I cycle through resolutions only the clone modes are available so I never get an extended desktop. 
Second problem: Using the clone modes I have to scroll on the screen with the lower resolution or scroll on both screens. I'd really appreciate some help.
System is Feisty Kubuntu with mesa 7.0

Here is part of my xorg.conf:

```

Option  "MonitorLayout"                 "LVDS, CRT"
        Option  "CRT2Position"                  "RightOf"
        Option  "MetaModes"                     "1400x1050-640x480 1024x768-1024x768 1024x768 1400x1050+1024x768  1280x1024"$
        Option  "MergedXinerama"                "off"
        Option  "MergedNonRectangular"          "true"
        Option  "MergedFB"                      "true"
        #Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen
        #Option "OverlayOnCRTC2" "true"
        Option "CRT2VRefresh" "50.0-200.0"
        Option "CRT2HSync" "30-132"
.....
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050" "1024x768" "1280x1024" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "1400x1050"  "1280x1024" "640x480"
        EndSubSection
EndSection


```

---


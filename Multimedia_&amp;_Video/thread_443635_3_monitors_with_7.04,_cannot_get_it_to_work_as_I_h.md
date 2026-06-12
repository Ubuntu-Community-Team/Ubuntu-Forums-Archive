---
title: "3 monitors with 7.04, cannot get it to work as I hoped"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by B3rt on 2007-05-14
I have 3 TFT monitors on 2 ATI video cards, they are used as following:

AGP Radeon 9800 on monitor1 (middle of the 3, generic monitor 1) using DVI
PCI Radeon 9200 on monitor2 using DVI (left of 1) and monitor3 using sub-d (on the right of 1) 
In the BIOS it is set to use PCI as first boot.

The problem I am having is that monitor 2 and 3 are clones of each other, monitor 1 and 2/3 are both 1 desktop

What I want is that I get 1 desk top with monitor 1 in the middle (with the clock.program menu etc), monitor 2 on the left as an extension of monitor 1 and monitor 3 on the right of 1 as an extension of 1
Simple said as: 2 - 1 - 3

I tried several setups but I cannot get monitor 2 and 3 to work indecently, note all 3 monitors work!

This is my xorg.config, could someone please tell me what I do wrong?
```

Section "Device"
        Identifier      "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
        Driver          "ati"
        Busid           "PCI:1:0:0"
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)"
        Driver          "ati"
        Busid           "PCI:1:0:1"
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)"
        Driver          "ati"
        Busid           "PCI:2:2:0"
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)"
        Driver          "ati"
        Busid           "PCI:2:2:1"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor 1"
        Option          "DPMS"
        ModelName       "CML174SXW"
        Horizsync       28-64
        Vertrefresh     43-70
EndSection

Section "Monitor"
        Identifier      "Generic Monitor 2"
        Option          "DPMS"
        ModelName       "CML174SXW"
        Horizsync       28-64
        Vertrefresh     43-70
EndSection

Section "Monitor"
        Identifier      "Generic Monitor 3"
        Option          "DPMS"
        ModelName       "philips"
        Horizsync       28-64
        Vertrefresh     43-70
EndSection

Section "Screen"
        Identifier      "Default Screen 1"
        Device          "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
        Monitor         "Generic Monitor 1"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1280x1024"     "1024x768"      "832x624"       "800x600"       "720x40$
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1280x1024"     "1024x768"      "832x624"       "800x600"       "720x40$
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1280x1024"     "1024x768"      "832x624"       "800x600"       "720x40$
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1280x1024"     "1024x768"      "832x624"       "800x600"       "720x40$
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1280x1024"     "1024x768"      "832x624"       "800x600"       "720x40$
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1280x1024"     "1024x768"      "832x624"       "800x600"       "720x40$
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Default Screen 2"
        Device          "ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)"
        Monitor         "Generic Monitor 2"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1280x1024"     "1024x768"      "832x624"       "800x600"       "720x40$
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1280x1024"     "1024x768"      "832x624"       "800x600"       "720x40$
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1280x1024"     "1024x768"      "832x624"       "800x600"       "720x40$
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1280x1024"     "1024x768"      "832x624"       "800x600"       "720x40$
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1280x1024"     "1024x768"      "832x624"       "800x600"       "720x40$
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1280x1024"     "1024x768"      "832x624"       "800x600"       "720x40$
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Default Screen 3"
        Device          "ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)"
        Monitor         "Generic Monitor 3"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1280x1024"     "1024x768"      "832x624"       "800x600"       "720x40$
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1280x1024"     "1024x768"      "832x624"       "800x600"       "720x40$
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1280x1024"     "1024x768"      "832x624"       "800x600"       "720x40$
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1280x1024"     "1024x768"      "832x624"       "800x600"       "720x40$
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1280x1024"     "1024x768"      "832x624"       "800x600"       "720x40$
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1280x1024"     "1024x768"      "832x624"       "800x600"       "720x40$
        EndSubSection
EndSection


Section "ServerLayout"
        Identifier      "Default Layout"
        screen "Default Screen 1"
        screen "Default Screen 3" RightOf "Default Screen 1"
        screen "Default Screen 2" LeftOf "Default Screen 1"
        Option "Xinerama""true"
        Option "Clone""false"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
EndSection

```

Hope someone can help, I so not see what I do wrong, this same setup works in Windows which I run as dual boot, I do not what to change a lot and I hope I can use it the same way as in XP

---


---
title: "Twin View issues"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by allmightyspiff on 2007-03-03
Alright, first here is my setup
I am running the newst version of kubuntu (6.10)
I have an nvidia 7600 (dual head)
Monitor A (1400x900)
Monitor B (1280x1024)

I installed the nvidia drivers as suggested in the dual monitor howto thread. Setup my xorg but now only Monitor B displays anything.

Here is my xorg log file (the part where it turns on the monitors anyway)
```

(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:5:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (CRT-1)
(--) NVIDIA(0):     WDE LTV-19w3 (DFP-0)
(--) NVIDIA(0): Samsung SyncMaster (CRT-1): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): WDE LTV-19w3 (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): WDE LTV-19w3 (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Devices: CRT-1, DFP-0
(WW) NVIDIA(0): No valid modes for "1400x900,1280x1024"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024,1400x900"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024

```

```

Section "Device"
        Identifier      "nvidia7200"
        Driver          "nvidia"
        BusID           "PCI:5:0:0"
        Option "TwinView" "True"
#       Option "TwinViewOrientation" "LeftOf"
        Option "UseEdidFreqs" "True"
        Option "MetaModes" "1280x1024,1400x900; 1400x900,1280x1024"
        #Option "ConnectedMonitor" "DFP-1,DFP-0"
        Option "NoPowerConnectorCheck"
        Option "SecondMonitorHorizSync" "UseEdidFreqs"
        Option "SecondMonitorVertRefresh" "UseEdidFreqs"
        Option "HWcursor"
        Option "CursorShadow" "On"
        Option "CursorShadowAlpha" "32"
        Option "CursorShadowXOffset" "3"
        Option "CursorShadowYOffset" "3"
        Option "TripleBuffer" "true"
        # XGL stuff
        Option "Accel" "On"
        Option "RenderAccel" "On"
        Option "AddARGBGLXVisuals" "True"
        Option "AllowGLXWithComposite" "On"

EndSection
Section "Device"
        Identifier      "nvidia7200"
        Driver          "nvidia"
        BusID           "PCI:5:0:0"
        Option "TwinView" "True"
       Option "TwinViewOrientation" "LeftOf"
        Option "UseEdidFreqs" "True"
        Option "MetaModes" "1280x1024,1400x900; 1400x900,1280x1024"
        Option "ConnectedMonitor" "CRT-1,DFP-0"
        Option "NoPowerConnectorCheck"
        Option "SecondMonitorHorizSync" "UseEdidFreqs"
        Option "SecondMonitorVertRefresh" "UseEdidFreqs"
        Option "HWcursor"
        Option "CursorShadow" "On"
        Option "CursorShadowAlpha" "32"
        Option "CursorShadowXOffset" "3"
        Option "CursorShadowYOffset" "3"
        Option "TripleBuffer" "true"

        # XGL stuff
        Option "Accel" "On"
        Option "RenderAccel" "On"
        Option "AddARGBGLXVisuals" "True"
        Option "AllowGLXWithComposite" "On"

EndSection
Section "Screen"
        Identifier      "WideScreen"
        Device          "nvidia7200"
        Monitor         "wide"
        DefaultDepth    24
        SubSection "Display"
        SubSection "Display"
                Depth           16
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          0 "WideScreen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```
                                                  

So, it sees both monitors, but wont display on both in X (they both get images in the command line w/o X). If anyone could point out what I am doing wrong I would really appreciate it. I have been banging my head against this Xorg.conf file for the better part of today to no avail. 

Thanks for the help

---

### Post by kerry_s on 2007-03-03
Have you tried running> sudo nvidia-xconfig --twinview
Restart X (ctrl+alt+backspace}
Let it set it up, then you can add options, most of them are done automatically, just look through your log and add the extra ones you want.

Press alt+f2> nvidia-settings
For the gui

Here's the manual so you no exactly what they do and if you need it.-> [http://http.download.nvidia.com/solaris/1.0-8762/README/index.html](http://http.download.nvidia.com/solaris/1.0-8762/README/index.html)

Also since you got 2 different size monitors(like me :)  ) you might want to try panning. It's a feature that allows you to set the screen to settings beyond what they can do by sliding the screen around. Mine is like this->

1st monitor has a max of 1280x1024 is 15'
2nd monitor has a max of 1600x1200 is 18'

my current setup:

```
    Option         "MetaModes" "1280x1024 @1940x1024, 1280x1024"
```

I have my small screen set to a wide screen and my bigger screen running at a decent size. I needed more space :) 

I also use/used

```
    Option         "MetaModes" "1280x1024 @1600x1200, 1600x1200"
Option         "MetaModes" "1280x1024 @1600x1024, 1600x1200"
Option         "MetaModes" "1280x1024 @1600x1200, 1600x1200 @1940x1200"
etc....

```

It's just 1 of those things to play with. :lolflag:

---

### Post by allmightyspiff on 2007-03-03
The nvidia-xconfig --twinview actually worked pretty well.

I think my problem ended up being a resolution issue is all.

```

(WW) NVIDIA(0): No valid modes for "1400x900,1280x1024"; removing.
(WW) NVIDIA(0):
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0):
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 2720 x 1024

```
It seems not to like that mode, but the auto-select guesses just fine, the resolutions look about what I expect so no worries.

Thanks for your help :P

---


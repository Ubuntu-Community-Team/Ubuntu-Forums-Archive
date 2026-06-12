---
title: "show only overlay on TV - possible in linux?"
date: 2006-12-17
forum: Multimedia &amp; Video
---

### Post by pickarooney on 2006-12-17
Is it possible in Linux to send only the video overlay to a TV and leave the PC screen usable for other things while a video runs in fullscreen on the television? 
If so, how would one do this with an nVidia card. Mine is currently set up in clone mode, but it's not the most practical option.

---

### Post by mirak63 on 2006-12-17
bot the theatre mode like with windows drivers, but I read somewhere you can run two X, and run two sessions, one for the TV and one for your desktop.
In fact by using dual screen.

---

### Post by pickarooney on 2006-12-18
That sounds cool. I'll have a look at how to install theatre mode. I don't think I could handle two X sessions, my performance is woeful enough with one!

---

### Post by pickarooney on 2006-12-19
Heh, that was pretty easy. Just changed the second monitor orientation to RightOf and unstretched my desktop and it's all gravy :)

---

### Post by God.Jr on 2006-12-19
hey there i was also wondering the same thing but i couldn't find where the monitor setup is.....can someone point me in the right direction plz

---

### Post by pickarooney on 2006-12-19
The Screen section of /etc/X11/xorg.conf should look something like this, depending on what type of card you've got
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "SecondMonitorHorizSync" "30-50"
    Option         "SecondMonitorVertRefresh" "60"
    Option         "MetaModes" "1024x768, 1024x768; 800x600, 800x600;"
    Option         "TVStandard" "PAL-B"
    Option         "TVOutFormat" "SVIDEO"
    Option         "ConnectedMonitor" "CRT, TV"
    Option         "TVOverScan" "0.4"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---


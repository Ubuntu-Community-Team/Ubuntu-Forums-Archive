---
title: "Screen Resolution w/ Samsung 204B"
date: 2006-08-09
forum: Multimedia &amp; Video
---

### Post by maeltor on 2006-08-09
Hi everyone,

I just setup Ubuntu 6.06 AMD64 with the Nvidia GLX drivers and everything is working fine, except I can't seem to get my monitors default resolution to work correctly.

I have a Samsung 204B (20.1 in) LCD that UBUNTU has defaulted to 1280x1024 but the monitor default is 1600x1200.

When I go to System / Preferences / Screen Resolution, I can see that mode listed, but selecting it and applying does NOTHING.  It just brings up the screen asking me if I want to revert or keep but it never changed, and even if I say keep and go back into that settings window, its back to 1280.

Here is the relevant portion of my xorg config:
```
Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Driver          "nvidia"
        BusID           "PCI:2:0:0"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666

```

Also, glxgears runs smooth and so does tuxracer but glxgears doesn't output my FPS so I can't really tell if everything works ok (I thought its supposed to output >1000fps if you truly have 3d working correctly)


```
(II) NVIDIA(0): Setting mode "1280x1024"
(II) NVIDIA(0): Setting mode "800x600"
(II) NVIDIA(0): Setting mode "1280x1024"

```
The above is the last entries i see in my Xorg.0.log.  It seems to me that its not even trying to enter that resolution mode.

---

### Post by tseliot on 2006-08-09
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---


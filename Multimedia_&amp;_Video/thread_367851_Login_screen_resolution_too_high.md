---
title: "Login screen resolution too high"
date: 2007-02-22
forum: Multimedia &amp; Video
---

### Post by Chevalric on 2007-02-22
Without too much trouble, I've been able to get TwinView working on my Nvidia 7800GT, together with my TFT monitor and my LCD TV. I use my TV only to watch video on, so most of the time I don't have it turned on. By using a null value in the TwinView metamodes, I managed to turn it off by default and can turn it on by changing my resolution. Works like a charm.

I have only problem with this setup: my login screen seems to use a virtual screen resolution that is wider than my TFT screen resolution, which means that I can scroll my login screen from left to right. I have looked around for a solution to this issue, but whatever I tried, it didn't work. It either had no effect on the login screen, or it screwed up my display after logging in.

Can anyone help me out with this, as it's pretty annoying ;).

For completion's sake, here are the relevant parts from my xorg.conf

```

Section "Monitor"
    Identifier     "SyncMaster"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "DFP-0 RightOf DFP-1"   
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "DFP-0: 1280x1024, DFP-1: null;DFP-0: 1024x768,DFP-1: 1024x768"
    Option "UseDisplayDevice" "DFP" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---


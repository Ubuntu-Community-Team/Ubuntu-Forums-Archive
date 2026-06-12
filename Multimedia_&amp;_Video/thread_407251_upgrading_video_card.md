---
title: "upgrading video card"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by code-breaker on 2007-04-11
I am trying to upgrade my video card. I have a geforce 5500, and I bought a 6800xt. I have a 20" lcd with 1600x1200 resolution. Since both used nvidia chips, I just swapped them out and powered up. Nothing showed up. So I swapped back, and the resolution was down to 1024x768. I edited xorg.conf, and added the lcd's native resolution, and I'm back to where I started. 

My question is how do I upgrade to the new video card? I an't find a tutorial or howto, and the nvidia drivers seem to be pretty generic, meaning there aren't many settings I can play around with. Any ideas?

Here is the relevant section of my xorg.conf:

> Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection



---

### Post by RomeReactor on 2007-04-12
Hi. Are you using the nvidia-glx-legacy driver with your 5500? If so, you may need to change the driver back to **nv** before inserting the 6800, as the newer card is not going to use those; you'll need **nvidia-glx**. Also, perhaps you'll need to run **sudo dpkg-reconfigure xserver-xorg** in the terminal after the new card is installed so the system reconfigures your xorg.conf file.

---


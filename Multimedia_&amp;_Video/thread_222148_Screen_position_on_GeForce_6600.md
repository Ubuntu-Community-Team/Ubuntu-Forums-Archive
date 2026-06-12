---
title: "Screen position on GeForce 6600"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by cracker on 2006-07-24
Hello all, thanks to this forum I finally got my monitor to use the correct resolutions. Now, I have a different problem. I share this monitor via KVM switch with a PII running Windows 98. At the same resolution and color depth, each machine places the screen in a different place. Windows 98 is off to the left, and Ubuntu is off to the right. Is there any way in Ubuntu to adjust where the graphics card draws the screen?

Here is the relevant portion of my xorg.conf:
```
Section "Monitor"
    Identifier     "Dell D1028L"
    HorizSync       30.0 - 69.0
    VertRefresh     50.0 - 120.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

My monitor is a Dell D1028L, and my graphics card is a GeForce 6600 256MB AGP 8x. I use the nvidia-glx package shown in Synaptic.

---

### Post by coffeecat on 2006-07-24
I have three machines - each a multi-boot - connected via a KVM switch to the same LCD monitor, and I get the same thing - sometimes from different distros/OSs running on the same machine. All I do is to press the 'auto' button on the monitor and it auto-centres itself.

---

### Post by cracker on 2006-07-25
Unfortunately, due to this being an old CRT, reconfiguring the monitor every switch is simply not practical. I know that ForceWare for 2000/XP has software screen position adjustments, but I need it for Ubuntu. The Windows 98 box has an nVidia Riva 128 in it, which doesn't use traditional ForceWare, and therefore neither has nView nor the position adjustment,

---


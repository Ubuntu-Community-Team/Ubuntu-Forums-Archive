---
title: "Nvidia Clone Screen resolution on second screen"
date: 2009-02-08
forum: Multimedia Software
---

### Post by kestal on 2009-02-08
I finally set up my clone screen on nvidia and it works the way I want, except for one small detail. On the second screen (Toshiba TV), it seems to cut off about 50px off of each side. Ubuntu does not let the resolution of the TV go above 1024x768 so I set it to that.

Its fine on my desktop, but on the cloned screen I cannot see my taskbar, or maximized window title bars, or scroll bars. And in a way, as a form of presentation, it would kind of defeat the purpose.

Is there anything I can do? With that said, I think I may have doubled something up accidently in my xorg.conf file. It is as follows:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "STAC Electronics KDS XF-70"
    HorizSync       30.0 - 72.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    Option         "MetaModes" "1280×1024 1280×1024"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1024x768 +0+0, TV: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by xc3RnbFO8P on 2009-02-08
> Ubuntu does not let the resolution of the TV go above 1024x768 so I set it to that.
Did you try to set your monitor to 1024x768?

---

### Post by doas777 on 2009-02-08
I had a simmillar problem for a while. 

you prolly  need to adjust overscan in your nvidia-settings or in your xorg.conf.

the problem I have was not ultimatly resolvable without getting a new vid card, because overscan control was not supported for the geforce 8500 with the driver available.

in order to make the overscan settings take affect with my new card, I had to add 
```
gksu nvidia-settings -l
``` to my System->Preferences->Sessions list


good luck

---

### Post by doas777 on 2009-02-08
heres a link to my thread on my experience. it *might* help...
[http://ubuntuforums.org/showthread.php?t=851626](http://ubuntuforums.org/showthread.php?t=851626)

good luck

---

### Post by kestal on 2009-02-08
> **Ringi said:**
> Did you try to set your monitor to 1024x768?

well, its cloned.. though yes, my monitor is set to 1024x768.

---

### Post by xc3RnbFO8P on 2009-02-09
What resolution do you have in: System> Preferences> Screen Resolution
> Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    Option         "MetaModes" "1280×1024 1280×1024"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1024x768 +0+0, TV: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by kestal on 2009-02-10
1024x768

---

### Post by xc3RnbFO8P on 2009-02-10
Maybe change this line: 
Option "MetaModes" "1280×1024 1280×1024" to
Option "MetaModes""1280x1024 1024x768" or
Option "Metamodes" "1024x768 1024x768"

---

### Post by kestal on 2009-02-10
> **Ringi said:**
> Maybe change this line: 
Option "MetaModes" "1280×1024 1280×1024" to
Option "MetaModes""1280x1024 1024x768" or
Option "Metamodes" "1024x768 1024x768"

I did that, restarted, but no change. I am hoping that its just not an overlay problem that is with the current drivers limitations, as this card isn't exactly at the bottom of the barrel.

Just mentioning, I did test it out on my Windows partition and it works (vista). It didn't quite work in Windows 7 beta, either (same problem with the 50px on each side not being shown).

---

### Post by xc3RnbFO8P on 2009-02-10
Try it with ","
Option "MetaModes" "1280×1024,1280×1024" to
Option "MetaModes""1280x1024,1024x768" or
Option "Metamodes" "1024x768,1024x768"

---


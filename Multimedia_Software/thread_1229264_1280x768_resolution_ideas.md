---
title: "1280x768 resolution ideas?"
date: 2009-08-01
forum: Multimedia Software
---

### Post by Semmelweis on 2009-08-01
I am trying to get my desktop resolution to 1280x768, and after no small amount of google searches and tinkering around with it, I am coming here for more ideas. 

Here are some of the details: 

* Ubuntu 9.04
* Card - Nvidia 9800+ GTX
* Driver - 180.44-0ubuntu1 (installed via Envy)

Thanks!

---

### Post by Semmelweis on 2009-08-02
TTT! Here are some of the xorg.conf entries: 

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection 

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GTX/9800 GTX+"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "metamodes" "1280x768 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1152x864 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by xc3RnbFO8P on 2009-08-02
Check System> Preferences> Display> choose NO, and see if you can change the resolution there.

---

### Post by Semmelweis on 2009-08-02
Thanks for the reply, I checked that out and had no luck, 1152x864 is the closest that utility will come.

---

### Post by Semmelweis on 2009-08-02
Bumped

---

### Post by TekMuzik on 2009-08-02
> **Semmelweis said:**
> TTT! Here are some of the xorg.conf entries: 

Section "Screen"

**# Removed Option "metamodes" "1280x768 +0+0"**
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
 **   Option         "metamodes" "1152x864 +0+0"**
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

I'm no expert..but that seems weird to me. Have you tried just changing the metamode line to  "1280x768 +0+0". Make sure you have the original file backed up so you can easily restore it from the command line in case you kill X.

---

### Post by Semmelweis on 2009-08-02
> **TekMuzik said:**
> I'm no expert..but that seems weird to me. Have you tried just changing the metamode line to  "1280x768 +0+0". Make sure you have the original file backed up so you can easily restore it from the command line in case you kill X. 

Yeah I tried that, and once I rebooted, X had set itself to 1024x768 (1024 is the default res, I normally run at 1152x864). I opened the xorg.config and seen that it had reverted itself back to default and placed that "removed" entry at the very bottom of the config.

---


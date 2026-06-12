---
title: "Dualmonitor setup with Opens Source ATi driver"
date: 2009-07-02
forum: Multimedia Software
---

### Post by Rovanion on 2009-07-02
I have tried my best to search around the internet for a solution. I've asked around in #Ubuntu and searched the forums but nothing has worked out this far for me.

I want to set up my now seven year old computer to the TV that I may watch some movies trough my computer on it. The connection is via a S-Video cable, and it works good in Windows.

So is there anyone here who knows how to do a dualmonitor setup with the Open Source driver for ATi cards in Ubuntu 9.04? Using the proprietary driver is no option since the support for my legacy card was dropped long time ago.

Additional info:
```
#lspci | grep VGA
#01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]

```And here's my /etc/X11/xorg.conf
```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "ServerFlags"
    Option    "DontZap"    "False"
EndSection
```

---


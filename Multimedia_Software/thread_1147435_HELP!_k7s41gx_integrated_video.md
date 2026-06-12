---
title: "HELP! k7s41gx integrated video"
date: 2009-05-03
forum: Multimedia Software
---

### Post by eptexas on 2009-05-03
This is my first time writing to the forum and I need help configuring the Integrated video on my ASROCK K7S41GX.  I have read many forums but information on all seems to be different and really doesn't help me out.   I know I have to configure the xorg.conf file but as to what I have to add, im not sure.  I known that the SIS driver comes with ubuntu but when trying to configure my display, it does not let me.

THIS IS A COPY OF MY XORG.CONF:

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


ALSO, MY MONITOR IS A DELL 1704FPVt

---


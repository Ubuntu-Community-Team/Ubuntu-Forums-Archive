---
title: "Where are the display settings stored?"
date: 2009-12-15
forum: Multimedia Software
---

### Post by 337 on 2009-12-15
The title pretty much says it all.  Gnome neither detects my monitor type nor allows a 1440x900 resolution.

What file stores the display settings?

Whish is the better editor, vim or emacs?

Thanks, Lee

---

### Post by 337 on 2009-12-16
Okay, I've stumbled around and found /etc/x11/xorg.conf and it looks like this:

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


For hardware I have an Intel G33/G31 Express Chipset on the motherboard driving a Dell S199WFP(Analog) monitor with a 1440x900 native resolution.

I would like Gnome to recognise these settings.

I would really appreciate some help.  Until then I will keep looking.

Thanks.

(did I really type "tital"?!?! sheesh!)

---


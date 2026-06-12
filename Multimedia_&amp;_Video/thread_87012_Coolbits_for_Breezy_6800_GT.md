---
title: "Coolbits for Breezy 6800 GT"
date: 2005-11-07
forum: Multimedia &amp; Video
---

### Post by hone on 2005-11-07
Hi, I have a eVGA 6800 GT and I can't seem to get coolbits working, I don't have the overclocking option in nvidia-setting, is there a specific thing I have to do?  I added Coolbits in my xorg.conf

```

Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6800 GT]"
        Driver          "nvidia"
        BusID           "PCI:2:0:0"
        Option          "Coolbits"      "1"
EndSection

```

---

### Post by Paulus on 2005-11-07
I have the same problem, and have since breezy, probably a coincidence.

I assume you checked out [http://www.phoronix.com/scan.php?page=article&item=197&num=1]("http://www.phoronix.com/scan.php?page=article&item=197&num=1")

pretty much telling you what u already know.

anyone else having problems?  (I am too)

here's my xorg sample:
```
Section "Device"
    Identifier    "NVIDIA Corporation NV38 [GeForce FX 5950 Ultra]"
    Driver        "nvidia"
    BusID        "PCI:2:0:0"
    Option         "RenderAccel"         "true"
    Option         "AllowGLXWithComposite" "true" 
    Option        "Coolbits"        "1"
EndSection
```

---

### Post by hone on 2005-11-07
yeah I did.  That's howI found out about Coolbits on linux.

---


---
title: "Too many displays?"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by digimars on 2006-10-27
I changed my default color depth to 24 in my xorg.conf file and found this:

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection

```

Am I supposed to have that many displays even though this is just a laptop?

---

### Post by jd65pl on 2006-10-27
They are for different colour depths.

---

### Post by digimars on 2006-10-27
Ah, that makes sense.  I was wondering if that was what was causing my clunky performance on my display.

---


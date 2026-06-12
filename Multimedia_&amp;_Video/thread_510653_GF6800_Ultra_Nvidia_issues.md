---
title: "GF6800 Ultra Nvidia issues"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by David C on 2007-07-26
New Ubuntu Fiesty Fawn user here.

I'm using:

```

05:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT] (rev a2)

```

and my lspci -n | grep 0300 shows,
```
05:00.0 0300: 10de:00f9 (rev a2)

```

Snippets of my xorg.conf:
```

Section "Device"
        Identifier      "nVidia Corporation NV40 [GeForce 6800 Series GPU]"
        Driver          "nv"
        BusID           "PCI:5:0:0"
EndSection

```

On my "Restricted Drivers Manager", I can only see:
```

NVIDIA accelerated graphics driver (legacy card)

```

When I enable it and reboot, my screen resolution is locked to 640X480 and 800X600. 

I have a couple of questions.

1) I'm on a GF6800 Ultra, why is it that they chose legacy for me.
2) How do I get it to work with 1024X768.

Thanks guys!

---

### Post by dabl on 2007-07-26
Where it says "nv" in your xorg.conf file, change it to "nvidia", save it, and restart x with Ctrl-Alt-Backspace.

I'll cross my fingers .....

:)

---

### Post by David C on 2007-07-26
> **dabl said:**
> Where it says "nv" in your xorg.conf file, change it to "nvidia", save it, and restart x with Ctrl-Alt-Backspace.

I'll cross my fingers .....

:)

I've disabled my legacy drivers. Should I re-enable it and then change it to nvidia?

---


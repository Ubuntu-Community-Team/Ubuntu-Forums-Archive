---
title: "Is this a normal xorg.conf?"
date: 2009-05-12
forum: Multimedia Software
---

### Post by MadCatmkII on 2009-05-12
I'm trying to figure out if my graphics card is properly configured or not. I can run glxgears, but when I wanted to tweak my settings I discovered that my xorg.conf was almost empty. The only thing it contains is this:
```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

Is this normal? I'm running xubuntu 9.04 and I have an Ati 1950 (one of the newly legacied chips).

---

### Post by VMC on 2009-05-12
It's the default xorg.conf. Since you have an ATI chip set you might look for how to configure that. I have aIntel chip set so I needed to revert to the old 2.4 version

---


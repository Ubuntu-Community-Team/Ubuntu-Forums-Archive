---
title: "vga out problem"
date: 2006-10-05
forum: Multimedia &amp; Video
---

### Post by zjcim on 2006-10-05
i have a laptop ibm x24 with ATI m6 ly video card

The monitor's resolution is 1024*768

i connected a external lcd monitor ,i want a 1440*900 output .

howto ??

thanks!

Debian etch ,ati open source driver

2.6.17 manully-built kernel

---

### Post by enigma_0Z on 2006-10-05
krandrtray should get you where you want to go,

You could also modify your /etc/X11/xorg.conf file, there should be a section similar to:

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NVIDIA Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

```

The line that says "Modes" add the modes that you want, then ctrl+alt+keypad_plus or minus changes between resolutions.

HOWEVER, krandrtray would prolly work better.

---

### Post by zjcim on 2006-10-05
but my laptop's lcd monitor dont't support 1280*800  1440*900 etc 

i only want to get a output to A External monitor with resolution 1440*900

through vgaout port.

thx anyway

---

### Post by Ziox on 2006-10-05
> **zjcim said:**
> but my laptop's lcd monitor dont't support 1280*800  1440*900 etc 

i only want to get a output to A External monitor with resolution 1440*900

through vgaout port.

thx anyway
Like enigma_0z said...you need to edit your xorg.conf file.  Change the things in bold:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NVIDIA Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           24
                **Modes           "1440x900" "1280x800"**
        EndSubSection
EndSection
```

---


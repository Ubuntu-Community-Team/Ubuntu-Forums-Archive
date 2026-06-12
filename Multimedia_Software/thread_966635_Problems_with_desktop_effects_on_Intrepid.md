---
title: "Problems with desktop effects on Intrepid"
date: 2008-11-01
forum: Multimedia Software
---

### Post by rasca7 on 2008-11-01
Hi, this is my first post in this forums. I haven't got a clue on what should I do. I've upgraded to Kubuntu 8.10 and can't get the desktop effects working.
In the System Settings Desktop window it says "Compositing is not supported on your system. Required X extensions (XComposite and XDamage) are not available."
I have a Ati Radeon X1200 (onboard a MSI K9AGM2-L) with the ATI/AMD propietary FGLRX graphics driver active.
I checked and libxcomposite1 and libxdamage1 are installed.
Some more info:

:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.1.8087 Release


And when I try to turn on compiz:
:~$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA:
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: not present.
aborting and using fallback: /usr/bin/kwin
kwin(8890) KDecorationPlugins::loadPlugin: kwin : path  "/usr/lib/kde4/kwin3_oxygen.so"  for  "kwin3_oxygen"


I've no idea why it isn't working. What should I do? Thank you very much,
    Rasca

---

### Post by smethurst on 2008-11-03
Try adding/modifying these options in /etc/X11/xorg.conf:

```
Section "ServerFlags"
        Option      "AIGLX" "on"
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

That did the trick for me.

---

### Post by rasca7 on 2008-11-03
Thanks!! It's working now. Any idea why they were disabled? :confused:
Thank you,
    Rasca

---


---
title: "[SOLVED] LOL! help! I killed xsession after installing Envy"
date: 2007-12-12
forum: Multimedia &amp; Video
---

### Post by schmildo on 2007-12-12
.

---

### Post by schmildo on 2007-12-12
My problem is this: (after uninstalling the ATI driver and Envy, then attempting to reinstall the ATI driver via the restricted drivers manager)

1) Xubuntu fails to detect my monitor and video card settings when I boot, and asks me to configure it.

2) ATI drivers are no longer in use or enabled. (even after ticking it.. watching the download, and rebooting)

[COLOR="DarkSlateGray"]xorg.conf:[/COLOR]
[COLOR="Sienna"]Section "Device"
        Identifier      "ATI Technologies Inc RV350 AS [Radeon 9550]"
        Driver          "fglrx"
        Busid           "PCI:2:0:0"
        Option          "TripleBUffer"  "true"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       30-70
        Vertrefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV350 AS [Radeon 9550]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
EndSection
[/COLOR]

**tim@lister:/etc/X11$** [COLOR="DarkSlateBlue"]fglrxinfo[/COLOR]
[COLOR="Sienna"]Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual![/COLOR]

**tim@lister:/var/log$** [COLOR="DarkSlateBlue"]cat Xorg.0.log |grep WW[/COLOR]
 [COLOR="Sienna"]       (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) "dbe" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "glx" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "vbe" will not be loaded unless you've specified it to be loaded elsewhere.[/COLOR]

**tim@lister:~$** [COLOR="DarkSlateBlue"]aticonfig --initial --input=/etc/X11/xorg.conf[/COLOR]
[COLOR="Sienna"]Found fglrx primary device section
Nothing to do, terminating.
[/COLOR]

I just want to go back to the default settings, can anyon ehelp?

---

### Post by steefjeqv on 2007-12-12
Hi there,

You can try changing your xorg.conf as follows :

Section "Device"

Change 
Driver "fglrx"

To
Driver "radeon"

This will (hopefully) enable the open source ati driver.

Greetings,
Steven

---

### Post by schmildo on 2007-12-16
Thanks for your help, nothing seemed to be working, so I finally gave in and reinstalled the OS.

Thanks for trying.

---


---
title: "Nvidia GT540M and Compiz"
date: 2011-12-28
forum: Multimedia Software
---

### Post by infest86 on 2011-12-28
Compiz is not working on my video Nvidia GT540M 

Here are some results when I type them in terminal

**compiz**[I]
compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.[/I]

**nvidia-xconfig**
[I]Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.


ERROR: Unable to write to directory '/etc/X11'.[/I]

**xorg.conf file**
[I]Section "Device"
    Identifier    "Default Device"
    Option "RegistryDwords" "EnableBrightnessControl=1"
    Option    "NoLogo"    "True"
EndSection[/I]

---


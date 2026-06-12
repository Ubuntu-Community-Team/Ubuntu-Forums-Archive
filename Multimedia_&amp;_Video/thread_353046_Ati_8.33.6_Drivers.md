---
title: "Ati 8.33.6 Drivers"
date: 2007-02-04
forum: Multimedia &amp; Video
---

### Post by marcus174 on 2007-02-04
I've just reinstall Ubuntu 6.10 on my system and trying to get everything working again. In the past I was able to get the drivers for my Radeon 9800pro working pretty good. But after I've downloaded the new drivers from the amd site (8.33.6) and it's saying in console.

Detected configuration:
Architecture: i686 (32-bit)
X Server: Unknown X Window
cp: cannot stat `x710/usr/X11R6/bin/*': No such file or directory
find: install/usr/bin/fireglcontrolpanel* : No such file or directory
Removing temporary directory: fglrx-install

When the gui appears.
Install Driver 8.33.6 on Unknown X Window

It let me continue the driver install still isn't succesful. Before this I tried the usual way i did by following the online guides which create debian packages from the ati installer.

Also the output from fglxinfo shows it's not being installed and the first line is odd.

Xlib: extension "XFree86-DRI" missing on display ":0.0".
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

Anyone know what the problem is?

---

### Post by happy-and-lost on 2007-02-04
Which shell are you using? (dash/bash?) I've encountered many problems with dash and the ATi drivers.

---

### Post by marcus174 on 2007-02-04
bash

---

### Post by happy-and-lost on 2007-02-04
Have you tried blacklisting/unblacklisting the fglrx module and adding the lines:

```
Section "Extensions"
        Option "Composite" "Disable"
EndSection
```

to the xorg.conf?

EDIT: Have you tried AIGLX? I get much better performance from it (1500fps) than the official fglrx (275fps) on my x300 card.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by marcus174 on 2007-02-04
Yep i have tried them, i might give those other drivers a go and see if they work, got nothing to lose with them.

---


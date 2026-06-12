---
title: "Xorg fails to become DRM master -&gt; incredibly slow karmic"
date: 2009-11-02
forum: Multimedia Software
---

### Post by sonnemonster on 2009-11-02
Hello, please help,

after i updated my Kubuntu 9.04 to 9.10 my Laptop (Asus K50IJ) is incredibly slow. Using the top command, i found out, that Xorg is eating up all my CPU power. Just redisplaying the console-screen for top uses 30% CPU power, moving a window will lead to 99%, new windows need about 10 seconds to be displayed. This is unbearable! :(

It seems to be related to this bug:
[https://launchpad.net/bugs/446641](https://launchpad.net/bugs/446641)

In the Xorg.0.log file i found these lines
```

drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card2
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card3
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card4
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card5
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card6
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card7
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card8
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card9
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card10
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card11
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card12
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card13
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card14
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: node name is /dev/dri/card0
(EE) intel(0): [drm] Failed to open DRM device for : No such file or directory
(EE) intel(0): Failed to become DRM master.

```

Do you know any fix to this bug??

Thank you very much in advance!

---

### Post by sonnemonster on 2009-11-02
I'm thinking about adding the ppa's from the ubuntu-x team to my sources.lst. In the latest updates it says, they have uploaded a new version of xserver-xorg-video-intel which - i guess - is doing the troubles on my graphics.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

I know, ppa's are unstable, but i would like to try this before reinstalling my ubuntu. Or would you recommend me to stay away from unstable sources? Could a broken Xorg do harm to my hardware?

---

### Post by sonnemonster on 2009-11-03
Ok,

i followed the instructions here
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

and installed Kernel 2.6.30 and it works. I think, my trouble has been, that i've been running an old Kernel, since i mixed up my grub menu.lst . Sadly the 2.6.31-Kernel leaves me with a blank screen... but i'll post this in another thread.

Thank you very much.

---


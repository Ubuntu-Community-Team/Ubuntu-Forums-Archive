---
title: "Video problem with Ubuntu 11.10 + Nvidia GT 220"
date: 2011-10-25
forum: Multimedia Software
---

### Post by BEaSTFX on 2011-10-25
I use ubuntu 11.10 and my video card is nvidia gt 220
I activated wobble in compiz and it obviously freezes when it moves. Then i stopped it and it kinda does the same normaly. I tought that is the problem with the drivers but they look okay.

Here is some info:
```
uname -a
Linux Lemuria 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

```
egrep -i " connected|card detect|primary dev" /var/log/Xorg.0.log
[    17.842] (--) NVIDIA(0): Connected display device(s) on GeForce GT 220 at PCI:1:0:0

```

```
glxinfo | grep -i vendor
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation

```

```
grep LoadModule /var/log/Xorg.0.log
[    16.574] (II) LoadModule: "extmod"
[    16.575] (II) LoadModule: "dbe"
[    16.575] (II) LoadModule: "glx"
[    16.584] (II) LoadModule: "record"
[    16.584] (II) LoadModule: "dri"
[    16.585] (II) LoadModule: "dri2"
[    16.585] (II) LoadModule: "nvidia"
[    16.586] (II) LoadModule: "nouveau"
[    16.817] (II) LoadModule: "nv"
[    16.817] (II) LoadModule: "vesa"
[    16.933] (II) LoadModule: "fbdev"
[    17.102] (II) LoadModule: "fb"
[    17.103] (II) LoadModule: "wfb"
[    17.103] (II) LoadModule: "ramdac"
[    17.103] (II) LoadModule: "fbdevhw"
[    17.991] (II) LoadModule: "dri2"
[    18.014] (II) LoadModule: "evdev"


```

If you what else could be the problem please share :)

Regards

---


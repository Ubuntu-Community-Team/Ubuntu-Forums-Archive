---
title: "MSI K8N Neo Platinum with nVidia3 Chipset and AGP Problems"
date: 2005-11-25
forum: Multimedia &amp; Video
---

### Post by Scrambler on 2005-11-25
Hello,

can someone help me in understanding why I have an amd64_agp module loaded instead of an nvidia_agp? I have a weird behaviour in X, it being very slow but working quite well nevertheless. syslog says:

[INDENT]Nov 25 10:24:44 localhost kernel: [4294729.260000] Linux agpgart interface v0.101 (c) Dave Jones
Nov 25 10:24:44 localhost kernel: [4294729.270000] agpgart: Detected AGP bridge 0
Nov 25 10:24:44 localhost kernel: [4294729.270000] agpgart: Setting up Nforce3 AGP.
Nov 25 10:24:44 localhost kernel: [4294729.285000] agpgart: AGP aperture is 256M @ 0xc0000000
Nov 25 10:24:49 localhost kernel: [4294746.430000] [drm] Initialized mga 3.1.0 20021029 on minor 0: Matrox Graphics, Inc. MGA G550 AGP
[/INDENT]

but lsmod says:

[INDENT]root@panacea:/var/log# lsmod | grep agp
amd64_agp              11464  1
agpgart                32328  2 drm,amd64_agp
[/INDENT]

but the kernel seems to have the module for nvidia compiled in:

[INDENT]root@panacea:/var/log# modprobe -l *agp*
...
/lib/modules/2.6.12-10-386/kernel/drivers/char/agp/nvidia-agp.ko
...
[/INDENT]

Is my AGP setup correct? Wouldn't I have to use the nvidia module? Why is it using  AMD64? Thanks for your help,

     Uwe

---


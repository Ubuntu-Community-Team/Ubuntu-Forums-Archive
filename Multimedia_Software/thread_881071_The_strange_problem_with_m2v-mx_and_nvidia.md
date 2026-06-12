---
title: "The strange problem with m2v-mx and nvidia"
date: 2008-08-05
forum: Multimedia Software
---

### Post by jcarlosn on 2008-08-05
Hi, I have a very strange problem with my hardware configuration, related to the Xorg server.

First of all, my system is:

CPU: AMD 64x 6400
MOBO: Asus m2v-mx
MEMORY: Kingston 400 2x2gb mobules
STORAGE: 160gb SATA2 disk
GRAPHICS: NVIDIA 8800gt 1gb (vendor: Asus)

I also have a NVIDIA 8600gs for test.

The problem is that since I bought this mother board, I'm not able to start ANY xorg server in ANY distro (including ubuntu).

I'm only able to start xorg using the vesa driver, but not using NV or NVIDIA drivers.

If I start xorg with NVIDIA or NV drivers, the screen shows random colors, or strange shapes, and sometimes freezes the computer.

Both cards and Mother board works perfect in Windows.

I have read that is a common problem with m2v-mx + nvidia:

[http://kubuntuforums.net/forums/index.php?topic=3089644.0](http://kubuntuforums.net/forums/index.php?topic=3089644.0)
[https://answers.launchpad.net/ubuntu/+question/23410](https://answers.launchpad.net/ubuntu/+question/23410)
[http://ubuntuforums.org/showthread.php?t=670378](http://ubuntuforums.org/showthread.php?t=670378)

etc etc.

It doesn't matter the distro, the way to install the nvidia drivers, etc. It keeps crashing.

I have tested changing the aperture size from 64 to 256mb, with no success.

I would appreciate any idea or suggestion on this issue, almost all the other people with this problem, finally solved it replacing the motherboard for another model, but I would like to know whats happening.

Thanks.

---


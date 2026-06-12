---
title: "AGP based Nvidia cards no longer supported?"
date: 2010-09-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by TBerk on 2010-09-22
It seems I can just get used to running the latest ubuntu release in whats known as 'low graphics mode', if what I'm learning is true, that there is no current support for 'early' Nvidia video cards.


TBerk
whose default GRUB entry drops him at a command line...

---

### Post by FuturePilot on 2010-09-22
Which driver are you using? The 96.xx and 173.xx drivers are currently broken because they haven't been updated for Xserver 1.9.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974")
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/616394]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/616394")

You could use the Nouveau driver for now.

---


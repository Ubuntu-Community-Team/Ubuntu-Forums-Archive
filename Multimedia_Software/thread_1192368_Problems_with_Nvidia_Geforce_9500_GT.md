---
title: "Problems with Nvidia Geforce 9500 GT"
date: 2009-06-20
forum: Multimedia Software
---

### Post by 7iu on 2009-06-20
I've recently purchased an Nvidia Geforce 9500 GT card, for PCI, not PCIe, and I have all the drivers, so it should be working fine, but it isn't.  Whenever I try to watch any video in more than about 800x800 resolution, it goes very slow and I can barely watch it.
I bought this card as a replacement for my Geforce 6150 LE, so it should be running faster,  but it's running much, much, slower.
Can someone help me?
Oh, and I'm using Ubuntu 9.04, if that's a factor.

---

### Post by Arup on 2009-06-20
> **7iu said:**
> I've recently purchased an Nvidia Geforce 9500 GT card, for PCI, not PCIe, and I have all the drivers, so it should be working fine, but it isn't.  Whenever I try to watch any video in more than about 800x800 resolution, it goes very slow and I can barely watch it.
I bought this card as a replacement for my Geforce 6150 LE, so it should be running faster,  but it's running much, much, slower.
Can someone help me?
Oh, and I'm using Ubuntu 9.04, if that's a factor.

You need to use vdpau enabled mplayer, add this repo and install mplayer and smplayer, you will then see the power of your 9500GT, if possible, try and use the latest 185.18.14 drivers from nvidia.

[https://launchpad.net/~brandonsnider/+archive/ppa](https://launchpad.net/~brandonsnider/+archive/ppa)

follow the instructions listed there for smplyer config.

---


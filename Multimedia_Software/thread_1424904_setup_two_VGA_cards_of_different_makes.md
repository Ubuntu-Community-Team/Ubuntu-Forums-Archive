---
title: "setup two VGA cards of different makes"
date: 2010-03-08
forum: Multimedia Software
---

### Post by pxhai on 2010-03-08
Hello,

My old motherboard died, and I replaced it with a 2nd-hand mobo ECS 865GV-M3.
This mobo doesn't have standard AGP, so the ECS guys have devised a way to simulate AGP bus on PCI bus called AGPpro, hence I can use my old Geforce4 MX460 with it. But this mobo doesn't allow me to turn off the integrated Intel Extreme Graphics 2 either, so I always have two VGA cards available all the time (Intel on PCI bus 0, nvidia on PCI bus 1). On Windows XP, these two can live happily together without any problems, and I use the Geforce as my primary VGA card. But, Ubuntu, right from the installation, only allows the integrated Intel as the primary card. I install Ubuntu and nvidia driver, after that I restart and change primary VGA to Geforce in BIOS. Then Ubuntu fails to start :sad: I have tried modifying xorg.conf but with no success yet.
It will be enough if anyone tell me it's possible to use two VGA cards of different makes on Ubuntu (to encourage me to continue trying my luck with xorg.conf :-|) and I would be more pleased if anyone show me the method to handle this problem.

Thanks in advance,
pxhai

---


---
title: "Install Ubuntu 11.04 with Wubi"
date: 2011-01-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by retskrad on 2011-01-20
HI!

I'm just wondering how I can install Ubuntu 11.04 Natty with Wubi?

---

### Post by bcbc on 2011-01-20
You can't. Easily. 

You need a copy of a working wubildr (e.g. from a maverick install) that you can copy over the Natty version prior to booting and you'll need to mount the root.disk to fix the grub.cfg after installing (it fails a syntax check on a new wubi install and leaves it as /boot/grub/grub.cfg.new so you have to rename it to get it to boot through the wubildr, or alternatively you can boot manually from a grub prompt instead).

You can try upgrading to Natty from a maverick wubi install. That's easier.

---


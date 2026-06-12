---
title: "Nvidia propietary drivers don't works. Mountall: can't connect to plymouth"
date: 2011-04-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by oasick on 2011-04-11
Nvidia propietary drivers don't works for me since I updated Ubuntu natty from 10.10 1 mounth ago...

I have a Nvidia GeForce 6600 card, install nvidia-current drivers but restarting always get the following error message:
mountall: can't connect to plymouth

any solution? thanks

---

### Post by Harry33 on 2011-04-12
> **oasick said:**
> Nvidia propietary drivers don't works for me since I updated Ubuntu natty from 10.10 1 mounth ago...
I have a Nvidia GeForce 6600 card, install nvidia-current drivers but restarting always get the following error message:
mountall: can't connect to plymouth
any solution? thanks

So you are using fully upgraded/updated Natty now with xserver-xorg-core_1.10.0.902-1ubuntu1 and nvidia-current_270.30.
The issues with Nvidia proprietary drivers and gfxboot (gfxpayload) with Plymouth should have been fixed with the latest grub update.
Do you have grub 1.99~rc1-12ubuntu1 installed?
See that you have the package grub-gfxpayload-lists installed too.

---


---
title: "no sound for laptop"
date: 2008-06-30
forum: Multimedia Software
---

### Post by gamer4lyf3 on 2008-06-30
Hey everyone I have a HP pavilion dv6000 laptop. when I first installed Ubuntu I had sound working. then after a restart (I think I installed a different Kernel but didn't really know what i was doing so I don't know if this is the problem) i lost sound. when I click on the little speaker in the top panal it says 

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

anyone know how I can fix this?

---

### Post by eryksun on 2008-07-01
> **gamer4lyf3 said:**
> Hey everyone I have a HP pavilion dv6000 laptop. when I first installed Ubuntu I had sound working. then after a restart (I think I installed a different Kernel but didn't really know what i was doing so I don't know if this is the problem) i lost sound.

Try the following command:

```
ls -la /dev/snd
```

If it doesn't list some sound devices, you may not have the kernel modules installed to properly access your sound system. Try the following command:

```
dpkg -l linux-ubuntu-modules-`uname -r`
```

This checks to see that you have the modules package installed for your currently running kernel. If it says "No packages found", install the modules package for your kernel with the following command:

```
sudo apt-get install linux-ubuntu-modules-`uname -r`
```

Reboot your laptop.

---


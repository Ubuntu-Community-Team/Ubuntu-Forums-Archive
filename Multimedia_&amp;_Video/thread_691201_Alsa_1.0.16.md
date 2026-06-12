---
title: "Alsa 1.0.16"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by krylon on 2008-02-08
I have an Auzentech X-Meridian which uses the CMI8788 chipset.  I have tried compiling the latest 1.0.16 ALSA from source which worked fine. However I am unable to install the driver properly.  When I try to load snd-oxygen module I get a bunch of unrecognized symbol errors.  If I reboot and try to load the same module, I ge an error about the module does not exist.  I've tried the Hardy deb packages without any luck.

When I try to cat /proc/asound the directory doesn't exist.
However when I lspci the sound card is detected.

I followed this guide
[http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen](http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen)

Has anyone had luck getting the latest 1.0.16 ALSA compiled and installed on 7.04 Feisty?

---

### Post by Dandeloreon on 2008-02-08
I went and found out that this is related to a backport/update request posted on the launchpad.

**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/189581](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/189581) [br].[/br] ---------------------------- [br].[/br] [br].[/br]

---


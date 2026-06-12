---
title: "Ubuntu 8.04 and 64studio"
date: 2008-05-08
forum: Multimedia Software
---

### Post by K.Morgan on 2008-05-08
Hi, i am wanting to try out 64studio but i'm having problems.

I have Ubuntu 8.04 installed on one of my partitions, Windows XP installed on another so therefore i already have grub installed.  I now want to install 64studio on another partition.  I boot off the 64studio install DVD and everything works fine during the installation until it gets to the part where it tries to install Grub.  The installation recognizes that Ubuntu 8.04 and Windows XP exists and then continues to try and install grub, to which it gives me an error message telling me that it was unable to install grub and that this is a fatal error.

Can Ubuntu and 64studio run on the same machine or can i only have one OS install grub?

Kristian

---

### Post by ethanay on 2008-05-20
I am currently trying to setup an Ubuntu/64studio dual boot.  I am runnign 32-bit generic Hardy and 64-bit studio on a Dell XPS m1330.  Install went OK except for poor hardware detection compared to Ubuntu.  So I know it is possible to have them working together.

---

### Post by Yellow Pasque on 2008-05-20
If you're going to have multiple Ubuntu systems, it would probably be wise to have a seperate /boot partition. However, If the install DVD has installed the entire UbuntuStudio system and is just having problems installing GRUB, you can manually edit the boot menu on Ubuntu 8.04 to point to the system image.

Boot into Ubuntu 8.04 and post your /boot/grub/menu.lst
Also mount your ubuntu studio partition and post the content of its /boot directory.

---


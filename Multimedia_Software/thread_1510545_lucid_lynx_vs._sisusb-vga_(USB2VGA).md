---
title: "lucid lynx vs. sisusb-vga (USB2VGA)"
date: 2010-06-15
forum: Multimedia Software
---

### Post by rabby_ on 2010-06-15
Hi,

With the new Ubuntu 10.04, I worry about my sisusbvga device to fail without any comment or error message.

"modprobe sisusbvga" promts no error and after that, I can find the module in "lsmod".
lsusb => "Bus 002 Device 002: ID 0711:5100 Magic Control Technology Corp."

"ls /dev/sis*" returns nothing :-( I tried the mknod trick already, but after restart the /dev entries are gone again.

In the xorg.conf I tried any suggested settings, but I guess they are all outdated.
However, I still have the device ([UA0076]("http://www.2direkt.de/i-sell2u/images/driver/UA0076.zip") - windows driver available)

Is there something I forgot to setup to get the sisusbvga to run? Even after modprobe, the device's status lamp is off. (When using it on a windows machine, the lamp turns into yellow.)

Please give me some advice to get the display to show some vga data. Is this sisusbvga module working with anyone at Ubuntu LTS - all i found when searching for this, were (unsolved) problems and no solution so far.

Is there at least a alternative module which allows to use the windows driver?


Thanks a lot!

---


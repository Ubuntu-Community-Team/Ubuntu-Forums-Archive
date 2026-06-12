---
title: "Trouble on the horizon for the Boot Info Script?"
date: 2011-01-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-01-18
Note to mods: I know this may seem to be a Natty problem but I know a lot of grub aficionados frequent this section of the forums and thought a heads up was in order ;)

I started a thread here:

[https://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4058900](https://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4058900)

> I first noticed with version 1.99~20101126-1ubuntu3 of grub-common and grub-pc the RESULTS.txt would post this: "Grub 2 is installed in the MBR of /dev/sda and looks for 9dem." With version 1.99~20110112-1ubuntu1 it's changed a bit more: "Grub 2 is installed in the MBR of /dev/sda and looks for :em." Of course with Natty being in early development I'm not too concerned but thought Meierfra would want to know. 

Just as it says, I've noticed that the newest versions of grub-pc and grub-common change the readout so you really can't tell what OS the MBR is assigned to, with the most current packages:

> => Grub 2 is installed in the MBR of /dev/sda and looks for :em.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

Not really sure how we'd work around that :confused:

Since I multi-boot a lot of distros I could presumably chroot any one OS and use "grub-probe -t device /boot/grub" to figure out which OS is controlling boot if I wasn't sure.

Any thoughts?

---


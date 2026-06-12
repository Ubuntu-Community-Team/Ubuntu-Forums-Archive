---
title: "sound problems when upgrading to 8.04"
date: 2008-06-17
forum: Multimedia Software
---

### Post by JDMF on 2008-06-17
I just upgraded to 8.04 from 7.10 and my sound stopped working.After extensive googling and desperate attempts it seems like i have found the problem, but not found a way how to solve it.

Seems like the drivers are missing from 

/lib/modules/2.6.24-19-generic/kernel/sound/

(it only lists ac97_bus.ko and soundcore.ko)

and if i boot to an earlier kernel, 2.6.22-14-generic, via grub the sound works fine. The /kernel/sound/ directory for that kernel version lists loads of things.

Any suggestions on how to get these drivers installed for my latest kernel? apt-get install linux-ubuntu-modules-2.6.24-19-generic will just say that its installed already.

Many thanks!

ps. Using Dell XPS M1330 laptop if that matters.

---

### Post by cotcot on 2008-06-17
I had this problem a couple of times and solved it by deleting the asound* files in the user directory (files might be hidden so .asound*). Hope this helps for you.

---

### Post by JDMF on 2008-06-18
yeah i think that could help if it was an individual user problem, but this was system wide.

But lo and behold, it works now! And the modules are still not in the location... go figure.

I think there must have been some kind of sequance problem with the upgrade, because the sound works now after 3 reboots, but didnt work after the first recommended reboot after upgrade.

Dont know what happened, but as long as it works, i wont complain!

:guitar:

---


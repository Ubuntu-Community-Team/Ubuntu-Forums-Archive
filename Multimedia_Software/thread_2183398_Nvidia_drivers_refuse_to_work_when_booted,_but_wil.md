---
title: "Nvidia drivers refuse to work when booted, but will load grub and shutdown screen?"
date: 2013-10-24
forum: Multimedia Software
---

### Post by adam_jones on 2013-10-24
Hi,

I recently upgraded my PC and i installed windows and my graphics card works fine.

When i installed ubuntu, it refuses to work with my graphics card at all, ubuntu starts up fine from my on-board graphics intel haswell (5000).

I have installed the OS multiple times and it still does not work. (12.4) (13.04).

Also when i re-install the OS it breaks GRUB and i have to run boot-repair every time to get the GRUB back, so i can then try a new method of trying to get my graphics card to work.

I have tried using the install third party drivers option for my card (by plugging one monitor into my motherboard so i can get the GUI up, then installing the graphics) but when i reboot i get a black screen.

When i have gone into recovery mode, failsafe graphics mode does not work.

I have also dropped into root and installed the latest kernel headers and nvidia-current. I am very new to ubuntu and command line, so i have been following tutorials. 

The card is a Nvidia 560TI (so not a new card) and 12.04 recommend i  install the 319 drives. 

This morning after trying many different options, i turned off the intel graphics on my motherboard (gigbyte uefi ) and now i can do ctrl + alt + f1 to get up a command line interface, so i would love if anybody could help me out with where to go from here so i can get my PC set up and begin using Ubuntu! As i love the OS!

When i shutdown via shutdown -p now (newbie) the screen then pops up at a low resolution (through the graphics card) and displays the killing all processes message etc.

I will be happy to provide any information i have missed (newbie) 

Thank you for taking the time to read this, i hope you can help me out.

Regards,

Adam

---

### Post by adam_jones on 2013-10-28
Hi,

i have fixed the issue!

i disabled the intel on board graphics in my BIOS, like stated above.

Then if your ubuntu crashes on startup you can do ctrl + alt + delete to try and restart it and get to a terminal, if you start up to a blank screen do ctrl + alt + F1-7, this can bring up a tty window for you to use. You could also drop into root through the recovery mode in grub (i did not have to do this, so i am not sure if it will work).

Once you have this window, you need to re-install xorg, google this and there a plenty of guides to follow, i hope this helps, it is a little vague, but i managed to get mine working well and i did not install the nvidia drivers. You could try this, but i did not want to take the risk of re-installing again.

---


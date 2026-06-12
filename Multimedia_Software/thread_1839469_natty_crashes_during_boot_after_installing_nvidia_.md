---
title: "natty crashes during boot after installing nvidia driver"
date: 2011-09-05
forum: Multimedia Software
---

### Post by redmaniac on 2011-09-05
Hey all,

I just got my new PC today. I installed natty and after that went through and everything seemed to work fine I installed the proprietary nvidia drivers (using the "addition drivers" feature). After that the machine freezes during boot: just a slightly pink (?? dunno, i'm a little color blind) screen and nothing else. I had to do a cold restart (not even magic sysrq worked). The first time I was able to get into the system by removing "quiet splash". But that only worked once. Then ubuntu insalled even more updates and since then nothing works at all. I reckon one of the cold shutdowns messed up the kernel, cause the failsafe mode now hangs with a kernel panick. Graphics chip is nvidia gt 440. 
Is there any way to fix this, or to prevent it from happening again after i reinstall ubuntu?

Cheers
redmaniac

---

### Post by drs305 on 2011-09-05
Before getting the kernel panic, my advice would have been to press "e" at the Grub menu with the kernel you want to boot highlighted. Remove all the options at the end of the 'linux' line and replace with "nomodeset" so no drivers are loaded. Then press CTRL-x to boot it.

You can still try this, but the kernel panic may make this moot. You mention updates. Do you have the option to try a previous kernel - perhaps the one which was originally installed (if your updates included a newer linux-image)?

---

### Post by redmaniac on 2011-09-05
hmm no i do not think ubuntu had installed a newer kernel than that on the image yet. at any rate, i never had an option for another kernel in grub. 

this whole thing leaves me puzzled because the driver itself seemed to be running fine once the system had managed to get past the boot splash.

---

### Post by redmaniac on 2011-09-06
ok, so it's not the nvidia diver i think. I did a clean reinstall last night and everything worked fine after that (just like the first time). This I did not install the nvidia driver but I did install the updates. Now the same symptoms. Pink screen, nohting else. I installed an openssh server on the machine first thing after the reinstall, but it's unreachable (ssh definitely worked after I installed it). Well I have no idea how to get out of this mess... seeing that I can't even get a terminal. The only way I'd know to get the machine out of this state is to just switch it off, which probably messed up the last install... anybody got any ideas?

---

### Post by redmaniac on 2011-09-06
I did another cold reboot and went into recovery mode. Now it at least gives me error messages... the kernel panick is there (but i'm almost sure it wasn't the cold reboot that caused it this time). The message that strikes me is this:  "Kernel panic - npt syncing: VFS unable to mount root fs on unknown block (0,0)"  Does this mean that the kernel is looking for the systen on the wrong hard drive or is there something wrong with the ramdisk?

---

### Post by redmaniac on 2011-09-07
Ok, this is solved. My RAM was faulty. After it was replaced the whole thing worked like a charm.

redmaniac

---


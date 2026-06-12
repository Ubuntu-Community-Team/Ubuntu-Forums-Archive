---
title: "Boot Hang:  Video Problem?"
date: 2011-11-17
forum: Multimedia Software
---

### Post by svtguy88 on 2011-11-17
Okay, I had no idea what forum to post this in, as I'm really not entirely sure what the root problem is here. I'm reasonably sure it's video driver related, but I'm not sure.

I rebooted my system last night for the first time in about two weeks (it runs as my router, so it's always up). I'm sure a whole host of updates got installed since the last reboot.

I got as far into the boot process as to get stuck at a purple-ish/brown-ish screen (the one that would appear right after the Grub menu, had it shown up, but I think it was set to skip on reboot or something).

I let it sit there for a few minutes and then tried rebooting with the Grub splash screen disabled (so I could see the text output). The boot process was hanging at "Running: /scripts/init-bottom"

I was able to boot to recovery mode, however and then tried a few solutions I found through Google (basically it came down to broken packages, and I tried repairing them - both through the recovery menu and through a terminal once booted into recovery mode. The whole process removed something like six obsolete packages and that's it).

I also tried removing/reinstalling the radeon driver and the Xserver, as a few other posts pointed to. Now my system gets about a half a step farther - it shows "Running: /sripts/init-bottm" and then it appears to remount the filesystem as read/write and then just stops again.

I'm still able to boot to recovery. The recovery menu pops up, I choose "remount as read/write," which it does successfully, and then choose "resume boot" to continue booting.

What's interesting is when I continue booting into recovery mode, the system shows "Starting load fallback graphics device [fail]" and then boots using VESA.

I'm really at a loss where to go from here. Luckily, the majority of my system functions fine from recovery mode, but I'd like to get rid of VESA and get a normal resolution back.

By the way, before this whole ordeal, I had Radeon installed, and everything worked fine... I had been creating a virtual container to run a web server in, and when I restarted my networking service, my pretty desktop went away, so I just decided to reboot, as it had been quite a while since I took the system down....

---

### Post by svtguy88 on 2011-11-17
More oddities.  I fooled around with the Grub boot arguments, comparing what the recovery mode had for arguments with what the (non bootable) regular Ubuntu image had for arguments.

I was able to get the regular image to boot by adding "recovery" and "nomodeset" to Grub.  The system begins booting, and shows the recovery menu.  I then mounted the files system as RW, and then selected "resume boot."  What is strange is that it throws an error when trying to activate the swap partition, but then continues to boot normally.

Anyone have any clue as to what my problem is?  Something with KMS?

---

### Post by MoreOrLess on 2011-11-17
Getting /var/log/Xorg.0.log after a failed attempt to start X might give you a clue..

---


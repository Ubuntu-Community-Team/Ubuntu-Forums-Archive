---
title: "Realy slow boot"
date: 2010-08-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by wingnux on 2010-08-05
I'm running Ubuntu 10.10 32bit alpha 3 and the boot is really slow! It takes about 70" to boot, according to bootchart.
My root partition is formatted to btrfs with bz compression enabled and my boot partition is formatted to ext3.

Here's my fstab content:

> proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=95c3ecad-5a93-4e13-a8fd-a577328f843f /               btrfs   defaults,compress        0       1
/dev/sdb1       /boot           ext3    defaults        0       2
# /home was on /dev/sdb6 during installation
UUID=295ecd0e-8f54-43c4-9f56-53a0b4ca74bb /home           ext4    defaults        0       2
# /home/wingnux/ide60gb was on /dev/sda1 during installation
UUID=54174DAD1EC023BB /home/wingnux/ide60gb ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sdb5 during installation
UUID=29c9bae1-e43f-45d2-93b5-fd59c266bde8 none            swap    sw              0       0

Bootchart image is attached.

---

### Post by cariboo on 2010-08-05
@wingnux I would suggest you use an image hosting service like [imgur]("http:///imgur.com/") or [ImageShack]("http://imageshack.us/"), your image is to small to be readable.

---

### Post by scradock on 2010-08-06
I have noticed that boot times have been creeping up, from a low around 40 sec early in the meerkat roll-out to over 60 in the last few days. I'm not using btrfs, or compression - just a standard ext4 single partition, 64-bit install upgraded from lucid from day 1.

I know this is not a priority at this stage, but I hope it gets some attention in the last few weeks.....

---

### Post by wingnux on 2010-08-06
Here it is the image on the original size ;)

[http://yfrog.com/2owingnuxdesktopmaverick2p](http://yfrog.com/2owingnuxdesktopmaverick2p)

---

### Post by linux18 on 2010-08-06
btrfs is still way behind ext2,3,4 in benchmarks because it is still in heavy development, if you haven't noticed, your disk throughput was about 50% through the entire boot up process. To fix this, use boot up manager " sudo apt-get bum " then profile your boot up

---

### Post by wingnux on 2010-08-06
Thanks for the tips guys but even after boot profiling my boot is only 1 sec faster =/ I guess I'll have to wait for more btrfs optimizations.

---


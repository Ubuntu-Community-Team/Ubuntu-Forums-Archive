---
title: "BTRFS compress option in live or alternate installers?"
date: 2011-02-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by vishalrao on 2011-02-07
Hi,

I just started installing the alpha 2 alternate ISO because I wanted to try btrfs with the compress option (to see how it helps with SSD space/speed) but, alas, the mount options seem to be some standard options such as "noatime" and so on with no way to specify "compress".

I STFW and came across pointers like [http://askubuntu.com/questions/6197/trick-installer-to-use-btrfs-root-with-compression](http://askubuntu.com/questions/6197/trick-installer-to-use-btrfs-root-with-compression) which I have yet to try but in the mean time what's the best way to request this option show up in the LiveCD and/or alternate installers? File a bug marked as wishlist?

Apparently adding the compress option to fstab post install does enable compression though only for files not already existing in there.

Thanks,
Vishal

---

### Post by msktje on 2011-02-08
Hello there is already a bugreport for this feature. [https://bugs.launchpad.net/ubuntu/+source/partman-btrfs/+bug/611585](https://bugs.launchpad.net/ubuntu/+source/partman-btrfs/+bug/611585)

If you manage to get it to work with the workaround you mentioned, would you please explain a little more on how to do it exactly?

ps: you have to download the daily build of today 08 febr 2011 or even the one tomorrow in order to get GRUB 2 working after installation.
There was today an update that makes is boot to btrfs root. [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/712029](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/712029)

---

### Post by Helkaluin on 2011-02-09
I suppose that, in the meantime, you can specify the compress mount option in fstab, and then run # btrfs fi defragment -c /dev/sdxn

---

### Post by vishalrao on 2011-02-10
Thanks for the comments, I will try again this weekend.

---

### Post by vishalrao on 2011-02-12
Nope, cant figure out how to add the compress option after its mounted but before the installation begins. The alternate installer seems to immediate mount/format/install in one step.

Will try adding the compress flag post-install to see if that makes any difference, maybe try some kind of benchmarks.

---

### Post by b1gp0ppa on 2011-02-12
This is a total hack but has worked for me on both lucid and maverick.  Of course, I had a separate ext2 /boot partition on those versions.

This blog post:
[http://www.moritzmolch.de/2010/08/01/installing-ubuntu-10-10-on-a-compressed-btrfs/](http://www.moritzmolch.de/2010/08/01/installing-ubuntu-10-10-on-a-compressed-btrfs/)

Outlines booting to Live session; mv /bin/mount /bin/mount.bin; create new /bin/mount shell script that contains...

[INDENT]#!/bin/sh
if echo $@ | grep "btrfs" >/dev/null; then
    /bin/mount.bin $@ -o compress
else
    /bin/mount.bin $@
fi[/INDENT]

...and install as normal.  This article forgets to tell you to make your new /bin/mount executable (chmod 755 /bin/mount).  I took a little poetic license and made my options "defaults,noatime,compress-force,space_cache".  I was able to mount the partition with those options from the Live session (just to test, need to unmount prior to starting the install).  The whole installation went through no problem but would not boot afterwards.  Sounds like grub's just been updated so I'm going to download the daily and try again sometime.

Hope this helps.

---

### Post by vishalrao on 2011-02-12
Thanks bigpoppa! Seems like a simple, elegant, creative solution! Why didn't I think of something like this myself? :lolflag:

Will try it out today and update this post...

---

### Post by b1gp0ppa on 2011-02-13
Today's daily looks better.  2 important notes:
1. User home dir encryption is definitely not working yet.
B. <heh> Subvol named @ is being created to be mounted as /.  Permissions on it are 700 so save yourself a headache by fixing during install before reboot:
ctrl-alt-F1 to get to shell
mkdir /tmp/mnt
/bin/mount.bin -o subvol=. /dev/sda1(or whatever) /tmp/mnt
chmod 755 /tmp/mnt/@
umount /tmp/mnt
ctl-alt-F7 to get back to gui

Today's AMD64 install went very much faster than Alpha2 also.  I went back to compress rather than compress-force in my btrfs mount opts.  Wonder if that could be why...

There's still a "sparse file" error when I reboot but otherwise working as expected.

---

### Post by vishalrao on 2011-02-13
I think I've got it too, after a bit of mucking about. I included the "nodatacow" option. "thread_pool=x" did not seem to make any differences in the numbers or even CPU usage.

Also made sure I edited /etc/fstab to include the same options "defaults,ssd,noatime,compress-force,space_cache,nodatacow" before rebooting for the first time post install.

Apparenlty 2.6.38 accepts the LZO compress/force option even though the wiki says >.38 - must be a typo or the kernel is silently ignoring this - couldn't feel/see any difference - must be the fs buffercache again.

I was getting mixed numbers trying to "benchmark" using commands like "dd if=/dev/zero of=/btrfsmount/file.dat bs=128M count=1" then realised filesystem buffer cache must be at play.

Also tried "dd if=/dev/urandom..." and also storing the random data files in TMPFS heh.

Trying the above silly tests comparing ext4 against btrfs on the same disk, it SEEMS I am getting about 50% higher read speed and same or slower write speeds, but my methodoly is TOTAL PSEUDO SCIENCE - just like Astrology :lolflag:

I tried running phoronix iozone bench but it prints ridiculous numbers like 500 MB/s write and 3000 MB/s read haha.

I tried downloading bonnie++ which seems sane, it shows believable numbers for ext4 but when I try btrfs is panics the kernel and me too.

Also for checking compression space saving, if I have a 8 GB partition and fill it up with files containing only zeros I still get "no space on device" after about 8 GB, I would have expected some extra storage space - but I did read btrfs does not have a way of telling the other components real vs. logical space usage.

Now what can I do to see if my SSDs (well the high level filesystem operations) are experiencing any higher speed and/or space savings?

---

### Post by cjwatson on 2011-02-15
> **b1gp0ppa said:**
> B. <heh> Subvol named @ is being created to be mounted as /.  Permissions on it are 700

This should be fixed in tomorrow's daily, assuming it builds.

> There's still a "sparse file" error when I reboot but otherwise working as expected.

This will continue to be the case for a while; we need to come up with a new location for the GRUB environment block in btrfs rather than storing it in /boot/grub/grubenv, because btrfs is sufficiently complicated that GRUB can't safely write to it.  I've agreed a strategy for this with the upstream maintainer, but it will take a while to code.  I'm not sure whether we'll have it fixed for Natty or not.

The practical effects are: (a) an annoying error message; (b) the system for automatically showing the GRUB menu in the event of a boot failure won't work properly, so you may have to hold down Shift; (c) grub-set-default and grub-reboot won't work.

---

### Post by b1gp0ppa on 2011-02-15
> **cjwatson said:**
> This should be fixed in tomorrow's daily, assuming it builds.

There's a different problem with the 14's build.  I've seen this behavior messing around with btrfs on my own: permissions set to 700 on a mounted subvol.  That is happening to / in the Feb 14 build so installations can't complete.  I'll pull down Feb 15 and check it.

---

### Post by cjwatson on 2011-02-15
> **b1gp0ppa said:**
> There's a different problem with the 14's build.  I've seen this behavior messing around with btrfs on my own: permissions set to 700 on a mounted subvol.  That is happening to / in the Feb 14 build so installations can't complete.

Um - that's the same problem you reported a couple of posts up, and it's what I was replying to, saying that it should be fixed in **tomorrow's** daily build (**not** the one from the 15th).

---


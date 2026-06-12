---
title: "Mythbuntu 12.04 desktop amd 64 vs. IDE drive"
date: 2013-01-22
forum: Mythbuntu
---

### Post by Panhead Bill on 2013-01-22
I get an "error: out of disk" when I reboot after loading 12.04 amd64 on my IDE drive.  The MB is an ASUS A8N-SLI delux.

If I load 12.04 onto one of the two 2TB sata that I have for storage, the system fires up fine.

Now the simple answer would be to can the IDE drive, but the reason I tried this was to determine why I can't load the i386 version on another motherboard, an Asrock K7VT6 that worked fine as my old master backend, and now is intended to be my main frontend.  This board is pre-sata.

In other words both the i386 and AMD64 versiond of 12.04 do not seem to work an IDE drive.

Amy ideas?

---

### Post by PhilWig on 2013-01-23
Search 'ubuntu 12.04 ide drive'.  Might this be the problem?

[http://mark.koli.ch/2012/07/fixing-ubuntu-1204-grub-boot-error-out-of-disk-with-older-ataide-disks.html](http://mark.koli.ch/2012/07/fixing-ubuntu-1204-grub-boot-error-out-of-disk-with-older-ataide-disks.html)

Phil

---

### Post by Panhead Bill on 2013-02-15
Looks like the right direction.  

The problem becomes how to update-grub when I can't boot the drive until after i have updated grub; kind of an endless loop.

I was able to find /etc/default/grub and after "apt-get install gedit", I was able to add GRUB_PRELOAD_MODULES="ata" to grub.

So my difficulty is how to mount the drive, change to the mounted drive and then "update-grub"

From one set of instructions:
1 Mount your partition:
 sudo mount /dev/sda2 /mnt
                           (that seems to work)

2 Bind mount some other necessary stuff:
 for i in /sys /proc /run /dev; do sudo mount --bind "$i" "/mnt$i"
                           (WTF? Does that mean to do:
             sudo mount --bind /sys /mnt/sys
             sudo mount --bind /proc /mnt/proc
             sudo mount --bind /run /mnt/run
             sudo mount --bind /dev /mnt/dev     )

3 chroot into your Ubuntu install:
sudo chroot /mnt

4 update grub:
update-grub

Since I'm stuck so far at step 2, I'll keep searching . . .

---

### Post by daone on 2013-02-16
Have never really had the patience or experience with fixing grub with the terminal.

When grub2 is messed up, I usually end up using a Ubuntu CD installer or USB stick to boot into Ubuntu live version. Then apt-get install  Boot-Repair in the live version.

If you get as far as using Boot-Repair and it updates grub, make sure your bios is configured to boot from the IDE drive First.

If all is attempted and your IDE boot drive still gives errors, their is the strong possibility your IDE drive is failing and you have bad sectors. That would be a physical problem and have nothing to do with Ubuntu or what-ever operating system you chose to use with the drive.

---

### Post by PhilWig on 2013-02-18
Have you tried boot repair disk?

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It's been magic for everything I've tried.  There are two options - simple and advanced.  Use simple! 
I will give one warning.  If you have two disks which you want to switch booting between via bios changes, then unplug the one you do not want altering before trying the repair.

Phil

---

### Post by Panhead Bill on 2013-02-18
Command line efforts - Fail.

Boot repair disk efforts - Fail.

Reload 12.04 64 bit - completes load, Fails "error: out of disk".
 
Boot repair disk on newly loaded 12.04 (from above) seems to repair grub untill reboot, then: "No system disk" (about 6 times) followed by "error: out of disk".

---

### Post by PhilWig on 2013-02-20
Ouch!!  being really stubborn.  There do seem to be opportunities for chickens and eggs.

In the old days Supergrub would mend things.  With Grub2 the corresponding supergrub2 disk I understand is a read-only thing.  Theory is that you boot sg2, then piggy-back boot Ubuntu from your IDE and then run update-grub.

If that fails too then it might be worth trying a specialised supergrub forum:
[http://www.supergrubdisk.org/forum/index.php](http://www.supergrubdisk.org/forum/index.php)

or even the general ubuntu one:
[http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

Best wishes - please let us know the outcome.
Phil

---


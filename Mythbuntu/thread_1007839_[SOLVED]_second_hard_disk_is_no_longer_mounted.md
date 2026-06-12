---
title: "[SOLVED] second hard disk is no longer mounted"
date: 2008-12-10
forum: Mythbuntu
---

### Post by ub40d on 2008-12-10
A few months ago my mythbuntu box filled up with
recordings and stopped working. I'm trying to get it
going again. In another thread, scary_jeff kindly
helped me out with the main problem. Here's another
one.

The machine started with an 80 GB disk and I later
added a 300 GB second disk, which worked fine as part
of a storage group. Now, however, the recordings on
that larger disk are no longer accessible. Indeed, if
I do (from the terminal)...

 ls /mnt/maxtor300

...I get nothing, as if the drive were not
mounted. And if I say...

 sudo mount

...then it doesn't appear to be mounted! But it's
still there in fstab, where it appears with the UUID
string. See the last line in the following:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a0f5ff9a-4d15-44f5-94c5-fa315e56e338 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ea0e35be-be8b-4275-938b-1e070656d17a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/sdb1
UUID=7f20b751-75ef-4760-b0cd-71cb7a9aeaac /mnt/maxtor300 jfs defaults 0 0


If I try mounting it by hand with...
 
 sudo mount /mnt/maxtor300

...I get the following response:

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

But
  dmesg | tail 
has nothing relevant, so instead I do 

 dmesg | fgrep sdb
which shows a few lines but none that gives me a clue:

[   23.865370] sd 1:0:1:0: [sdb] 586114704 512-byte hardware sectors (300091 MB)
[   23.866535] sd 1:0:1:0: [sdb] Write Protect is off
[   23.866542] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   23.868841] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.870825] sd 1:0:1:0: [sdb] 586114704 512-byte hardware sectors (300091 MB)
[   23.870854] sd 1:0:1:0: [sdb] Write Protect is off
[   23.870859] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   23.870892] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.870899]  sdb: sdb1
[   23.889226] sd 1:0:1:0: [sdb] Attached SCSI disk


Why isn't the fstab entry sufficient to mount the disk
(especially since it was sufficient a few months ago)? Could it be that the metadata of the 300 GB disk somehow got damaged when it filled up? How should I check for that? And how should I repair it if needed?

What else should I do to have the disk mounted?

Thanks in advance

---

### Post by modmadmike on 2008-12-10
Try finding the drive in GParted (search for it in synaptic and then find it in the system menu) try finding out if JFS is proprely installed through synaptic, I got the same error when I tried to mount a NFS file system w/o NFS-common.

---

### Post by modmadmike on 2008-12-10
worst comes to worst open your pc's case and unplug the SATA cabe while it is running and plug it back in (SATA is hot-swappable so you can do this while it is on). Also make sure the Drives real UUID did not change, if you resize the Partition or move it this will happen.

---

### Post by ub40d on 2008-12-11
THANKS, modmadmike! All working now.

First of all, I checked whether the uuid had changed:

  sudo blkid

but that gave the same value as in fstab.

Then I ran synaptic: was jfs installed? Well, synaptic didn't really say. Searching for jfs there were only 4 entries, two totally unrelated (chinese characters stuff), one for some jfs tools and one for some developer library. None to indicate basic jfs support. Anyway, I did install the jfs utilities just in case. Then I also installed gparted.

Ran gparted. It saw /dev/sdb1 without problems and showing no errors. Since I had nothing better to do I told it to recheck and fix the partition. It finished in 13 seconds and the detail view said nothing about having fixed any errors. Nonetheless, after that I tried mounting the partition with

  sudo mount /mnt/maxtor300

and I got no complaints! Whoah! And, sure enough,

  ls /mnt/maxtor300

now showed some files, and going into the mythtv frontend now showed the other recordings I could not access yesterday. Yay!

I guess the gparted "check and fix" did something beneficial even if it was too modest to mention it.

Last step was to check that the maxtor300 would automount again on reboot, and it did. So, all fixed.

Thanks a lot again!

---


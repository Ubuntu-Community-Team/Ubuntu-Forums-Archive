---
title: "problem with large partition and 10.04BETA"
date: 2010-03-22
forum: Mythbuntu
---

### Post by BullCreek on 2010-03-22
I downloaded the alternate cd for 10.04 BETA because I assumed that the mythbuntu download being a "desktop" build didn't have support for mdadm in it.  The mdadm part worked fine, but when I go to put a filesystem (any kind of filesystem) on the 7.5TB partition, it craps out.  I filed a bug here:

[http://bugs.launchpad.net/bugs/543838](http://bugs.launchpad.net/bugs/543838)

In doing a little more reading, it strikes me that the bug may be with partman rather than the kernel.  Anyone else run into this and know of a workaround?

---

### Post by ian dobson on 2010-03-22
Hi,

Looks as if the good old "fdisk/dos partition table" can't handle a partiton larger than 2Tb.

I have a 4Tb RAID5 array:-

```

Disk /dev/md0: 20.0 GB, 20012007424 bytes
2 heads, 4 sectors/track, 4885744 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 3960.8 GB, 3960767250432 bytes
2 heads, 4 sectors/track, 966984192 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

```

I just formated the drive (md2) without creating a partition table. Maybe you can use partd with GUID partition table format (GPT) but I can't help you there.

Regards
Ian Dobson

---

### Post by BullCreek on 2010-03-22
Yes, I agree that GPT might work if I wasn't lazy and wanted to take the time to figure that out by trial and error - but what is puzzling is that this has not been a problem in prior releases (I have an intrepid box running a 2.9TB raid6 array and a karmic one running a 7.5TB array with no problems).  Hopefully someone will chime in with answers...

---

### Post by ian dobson on 2010-03-23
So is your 7.5Tb array partitioned?

can you do a fdisk -l and post the results from the large array here. 

Regards
Ian Dobson

---

### Post by ian dobson on 2010-03-23
Hi,

In afew days I'll be getting several 2Tb/4k sector WD drives for some tests. Although the end user doesn't run ubuntu I'll "test"  them over the weekend on my ubuntu backed as a RAID array.

I'll try dos partitions/gpt partions with fdisk/gpartd and add my findings here.

Regards
Ian Dobson

---

### Post by BullCreek on 2010-03-23
Thanks for the comments.  I think this is a problem with the alternate CD installer and not the kernel, as if I do "mkfs.ext4 /dev/md0" or "mkfs.xfs /dev/md0" on the command line it works fine and I can mount the resulting filesystem and use it.  

I guess my setup is a little different than yours in that I'm not partitioning the mdadm block device per se - just using the whole device as a single partition which is also the way the alternate CD installer has done it traditionally.  Hopefully someone will pick up the bug I filed and run with it.

At some point before too long, I'm probably going to switch my 750GB drives to 2TB or whatever is biggest at the time so I'd definitely be interested in hearing your results on the new 4k sector drives.

---

### Post by ian dobson on 2010-03-23
Hi,

You can format a block device (/dev/md0) without creating a partition, thats how I created my ext4 4Tb MythTV recordings drive.

You wanted to create a partition table on your 7Tb array, but the good old DOS compatible partition table can only support 2Tb partitions. Larger partitions can be created using gpartd/gpt partition format.

I do not think this is a bug (unless you want to open a bug report with MS for msdos 6.2), this is a limitation of the dos compatibility.

You said you have a "karmic one running a 7.5TB", please attach a fdisk -l if you want to prove me wrong.


 
Regards
Ian Dobson

---

### Post by BullCreek on 2010-03-23
I don't have access to the karmic machine right now, but here is an older intrepid machine with a 3TB /dev/md1 array with no partition table that is working fine - a block device is a block device is it not?

root@mythtv:~# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdg1             11535344   7989936   2959440  73% /
tmpfs                  1036156         0   1036156   0% /lib/init/rw
varrun                 1036156       356   1035800   1% /var/run
varlock                1036156         0   1036156   0% /var/lock
udev                   1036156      2872   1033284   1% /dev
tmpfs                  1036156         0   1036156   0% /dev/shm
lrm                    1036156      2204   1033952   1% /lib/modules/2.6.27-14-g
eneric/volatile
/dev/sdg6             84926264  73404672  11521592  87% /var/lib
/dev/md1             2930156544 2570752924 359403620  88% /var/lib/mythtv
root@mythtv:~# fdisk -l /dev/md1

Disk /dev/md1: 3000.6 GB, 3000614518784 bytes
2 heads, 4 sectors/track, 732571904 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table
root@mythtv:~# uname -a
Linux mythtv 2.6.27-14-generic #1 SMP Tue Aug 18 16:25:45 UTC 2009 i686 GNU/Linux
root@mythtv:~#

---

### Post by ian dobson on 2010-03-24
Hi,

I think partman tries to create a partition table on the block device, but as the block device is larger than 2Tb it fails.

Formatting a block device (without a partition table) is supported on linux no problems, other operating systems might not see it and think the drive is empty. To reduce the chance of a mixup I always partition the drives that end up in the array and tell mdadm to use the partitioned device (/dev/sda1 and not /dev/sda).

Regards
Ian Dobson

---

### Post by ian dobson on 2010-03-25
Hi,

OK, I've just picked up 2 4K sector 2Tb drives. Using fdisk with the -u option I've created a partition that starts on sector 64 (4Kb boundry). I then created a RAID0 block device over the 2 drives and formated the block device with ext4.

I'm currently formatting/copying data over to the array, this takes a while to copy 2.5Tb :o

Regards
Ian Dobson

---


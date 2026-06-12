---
title: "Not enough space on dev/sda1?"
date: 2009-09-19
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-09-19
I just tried to download some regular updates via the update manager, and it failed, telling me that there was no disk space.

This surprised me, as I have 2 x 1TB disks, and have plenty of room on them.

On further investigation, I see that part of my disk is in a rather small partition, which was full. This is /dev/sda1. I'm a bit of a Linux newbie, and can't claim a detailed knowledge of partitions and the like, so I just accepted the defaults when I installed Mythbuntu. This partition seems to be about 11 GB. It's no longer full, as I emptied my wastebasket and deleted some files I don't need from my personal home directory, and this allowed the updates to install. However, I only have about 2GB of the 11 GB free, and I'm worried that something is making the disk fill up, and will cause problems again.

So, to my questions:

Is the default of 11 GB sensible, or is it in fact too small?

If it's too small, is it possible to resize it without a complete new installation?

If it should be plenty of space, are there any likely reasons why I'm filling it so quickly? I don't have very much now in my personal home folder.

I'm using Mythbuntu 8.10.

Many thanks
NM

---

### Post by hal10000 on 2009-09-19
```
sudo apt-get clean
```
Then run your update-manager again. Can you post the outputs of the command
```

df -h

```
to see how many space you have?

---

### Post by NautiusMaximus on 2009-09-19
Thanks for that. This is what the output looks like when I run df -h:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  8.3G  2.2G  80% /
tmpfs                 1.9G     0  1.9G   0% /lib/init/rw
varrun                1.9G  348K  1.9G   1% /var/run
varlock               1.9G     0  1.9G   0% /var/lock
udev                  1.9G  2.9M  1.9G   1% /dev
tmpfs                 1.9G     0  1.9G   0% /dev/shm
lrm                   1.9G  2.6M  1.9G   1% /lib/modules/2.6.27-14-generic/volatile
/dev/sda6             920G  334G  586G  37% /var/lib
/dev/sdb1             932G   13G  920G   2% /media/disk2

```

---

### Post by miamizsun on 2009-09-19
I need to resize also, actually shrink my partition if possible.

Any and all help/info would be appreciated.

Thx

---

### Post by hal10000 on 2009-09-19
@NautiusMaximus:

```

/dev/sda1              12G  8.3G  2.2G  80% /

```
I guess this is the space after you run apt-get clean, and 2.2 G seems to be enough by now. 
Maybe you can get a little bit more free space if you empty your trash.

But there is another line in your output which makes me wonder:
```

/dev/sda6             920G  334G  586G  37% /var/lib

```
On my system the /var/lib directory (which is not in a different partition but resides just under the same partition as my /) has a size of about 300MB and your's is more than a thousand times bigger. You must have some really big mysql databases, am i right?


@miamizsun:
> I need to resize also, actually shrink my partition if possible
can you post the output of
```
sudo fdisk -l
```
and explain which partitions you want to shrink/enlarge?

---

### Post by NautiusMaximus on 2009-09-19
Do I need to do anything else with clean after typing sudo apt-get clean? My limited understanding of Ubuntu suggests that that merely installs something, and doesn't run it.

I believe that the reason that /var/lib is so huge is because it's got all my MythTV media files in it. I dare say I have enough TV recordings to fill up 300 GB.

Having said all that, I've just had another idea about what the problem might be.

I have set a cron job to back up my files to an external hard drive. I can do that perfectly happily once the external hard drive is mounted, and I can happily manually mount the external hard drive. However, my attempts to mount the external drive automatically via /etc/fstab have so far beeu unsuccessful. I therefore have to remember to remount the drive after each reboot.

I'm thinking that if I forgot to do that at some stage, would the cron job just back up things to the mount point and write files to the local disk instead of the external disk that should have been mounted there? That would certainly use up a lot of space.

NM

---

### Post by mrand on 2009-09-19
What is the actual error message?

You might go into synaptic (package manager) and see if shows that you still have a bunch of kernel's installed.  If so, remove all but the latest ones.

Good luck,

[INDENT]Marc[/INDENT]

---

### Post by drs305 on 2009-09-19
Yes, backups to the wrong location are often a problem. One way to find out what's taking up the space is to umount all non-system drives and then inspect what's left. This will reveal backups that should have been made to a mounted backup partition but were instead written to the system partition. Here are couple of links that might help you:

[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

[ Expanding an Ubuntu System Partition  ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by NautiusMaximus on 2009-09-20
Many thanks drs305, the link to "HOWTO: recover lost disk space" was very helpful.

The problem was indeed writing backups to the system partition when the device that should have been mounted there wasn't. I've now deleted all the extraneous backups from the system partition, emptied my wastebasket, and lo and behold I now have about 8GB of my 12GB partition free again.

That, no doubt, is how things should be.

---

### Post by miamizsun on 2009-09-20
> **hal10000 said:**
> 
@miamizsun:

can you post the output of
```
sudo fdisk -l
```
and explain which partitions you want to shrink/enlarge?
I'm very new to Ubuntu/Linux, I partitioned my Windows machine to give it a try. I currently need to recover (or down-size my Ubuntu partition) the space for work related activity. In the near future I'm hoping to get an older machine or get an entire drive to devote to Ubuntu.

Thx


> Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


---

### Post by drs305 on 2009-09-20
miamizsun, 

That's a lowercase L, not a 1 (One). It's often confused.
```

sudo fdisk -l

```

---

### Post by miamizsun on 2009-09-20
I apologize, sorry about that.


> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9985ee5c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1264    10153048+   7  HPFS/NTFS
/dev/sda2   *        1265       23743   180556800    7  HPFS/NTFS
/dev/sda3           23743       30134    51336192   83  Linux
/dev/sda4           30134       30402     2149376+   f  W95 Ext'd (LBA)
/dev/sda5           30134       30402     2149376   82  Linux swap / Solaris

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x838559d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       60801   488384001    7  HPFS/NTFS


I believe that also includes a 500 gig HD back up too.

---

### Post by miamizsun on 2009-09-21
shameless bump

---

### Post by drs305 on 2009-09-21
miamizsun,

What exactly do you want to do - shrink your Linux partition or eliminate it?

I wrote this guide about expanding your Ubuntu system partition, but you could do the reverse as well. The principles would be the same.
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by hal10000 on 2009-09-22
@miamizsun:
There should be no problem if you shrink your windows system partition (/dev/sda2) and expand the linux partition (/dev/sda3).

But before shrinking you have to boot windows and do a defragmentation of your windows system (if you never have done this, it may take a long time). I found, that it's better to do that two or thee times one after the other.

After you have done this, then boot your ubuntu live-cd, start gparted and shrink/enlarge your partitions.

---

### Post by jb5 on 2009-09-22
I successfully expanded and shrunk partitions on a 500G SATA II drive. 
(ext3 shrink & XFS expand).

If you have a lot of data on the disk, be prepared for a L O N G wait. 
The procedure was successful, but put aside most of the day to do it! 
IIRC it took 10+ hours. I think I may have also cloned the disk beforehand as well, just in case!

HTH

---

### Post by miamizsun on 2009-09-23
I'd like to eliminate my Ubuntu partition on this drive altogether and go Windows all the way.

I recently found another box at work that I'm bringing home on Friday that I plan to devote solely to Linux :)

---


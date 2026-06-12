---
title: "Need help to move mythbuntu from 3 drives to one 500GB"
date: 2010-09-12
forum: Mythbuntu
---

### Post by Mad_Professor on 2010-09-12
I need to move all of recordings and configurations from 3 small drives 40/80/200 in LVM to a 500GB drive.

I tried to clone the small 10GB O/S partition on 40GB to the 500GB and then expand it, then moved all the stuff from /storage/lib of the lvm to/var/lib on the 500GB.

It won't boot.. well it will boot the sata card but it resets the machine if it tries to boot the 500GB drive, I think I need to do some additional configuration on grub or the kernel. Not sure which.

Now I'm not sure what to do...

I might want to do a fresh install but not sure how to backup and restore myth.

Any help appreciated.

---

### Post by frego on 2010-09-12
I would try setting up your partitions with sizes and file system type and format them on the 500GB drive.  Once that is done, boot with a live cd and use rsync to copy each partition over.  Beware to preserve permissions and all that.  You might wanna google or read man page to get the exact flags.  Then use gparted from your Ubuntu live CD to mark the root (or /boot) partition as bootable.  If this succeeds, you won't have to worry about resizing.  All in all, a fresh install probably would be easier.

---

### Post by itlarson on 2010-09-14
If you decide to re- install, here is the page which tells you how to do the database backup and restore:

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

---

### Post by ian dobson on 2010-09-14
Hi,

When I went over to using a CF card for my frontend I did almost the same thing.I just did:-

1) dd old drive to new drive
2) ran fdisk on the new drive, deleted the partition table and recreated it with the full size of the CF card. Note fdisk doesn't delete the data on the drive, it just changes partition table and aslong as the start doesn't change everything should be OK.
3) Booted from a live cd and ran resizefs to expand the file system to fill the new partition.
4) Manually installed grub.
5) Rebooted and the system started from the CF card.

The whole thing took about 2hours, well actually 4 attempts to get grub installed without screwing up the partition, and everytime it screwed up I had to go through the whole process again.

Regards
Ian Dobson

---


---
title: "Installing Mythbuntu onto an mdraid1/LVM setup"
date: 2011-12-07
forum: Mythbuntu
---

### Post by kenyee on 2011-12-07
Has anyone done this before?
I'm probably looking at a reinstall since I borked my system trying to migrate root into a RAID/LVM setup ([http://ubuntuforums.org/showthread.php?p=11520014](http://ubuntuforums.org/showthread.php?p=11520014)).

Looks like the best way to do it is grab the Ubuntu Alternate ISO ([http://www.ubuntu.com/download/ubuntu/alternative-download#alternate](http://www.ubuntu.com/download/ubuntu/alternative-download#alternate)) but not the Ubuntu Server ISO because that has no GUI,
then add the Mythbuntu control center ([http://mythbuntu.org/existing-ubuntu](http://mythbuntu.org/existing-ubuntu))

I normally set up my Linux systems as
/dev/md0 (raid1 /boot)
/dev/md1 (LVM w/ the rest of root, the data partitions, etc.)
so if one drive fails, the other is fine...

---

### Post by nickrout on 2011-12-07
> **kenyee said:**
> Has anyone done this before?
I'm probably looking at a reinstall since I borked my system trying to migrate root into a RAID/LVM setup ([http://ubuntuforums.org/showthread.php?p=11520014](http://ubuntuforums.org/showthread.php?p=11520014)).

Looks like the best way to do it is grab the Ubuntu Alternate ISO ([http://www.ubuntu.com/download/ubuntu/alternative-download#alternate](http://www.ubuntu.com/download/ubuntu/alternative-download#alternate)) but not the Ubuntu Server ISO because that has no GUI,
then add the Mythbuntu control center ([http://mythbuntu.org/existing-ubuntu](http://mythbuntu.org/existing-ubuntu))

I normally set up my Linux systems as
/dev/md0 (raid1 /boot)
/dev/md1 (LVM w/ the rest of root, the data partitions, etc.)
so if one drive fails, the other is fine...

either alternate or server will do it, and then I would add mythbuntu-desktop, which will drag in everything you need, including a gui.

Why LVM? myth certainly doesn't benefit from it, and it has the problem that if you lose one disk in an LVM group, you lose the whole group.

storage groups are the myth way of spanning data across multiple disks.

---

### Post by kenyee on 2011-12-07
> **nickrout said:**
> 
Why LVM? myth certainly doesn't benefit from it, and it has the problem that if you lose one disk in an LVM group, you lose the whole group.

storage groups are the myth way of spanning data across multiple disks.

LVM for easy expansion/contraction of the Linux root file system (it's used for VMs as well as being a Myth backend).
It's RAID1 underneath, so if you lose a disk, you have time to replace it before the array goes down ;-)
I'm actually wondering if I should put the multimedia array in a distributed file system instead of RAID1 since I have multiple backend servers.

I don't have nearly as much data as some of the guys around here ;)

---

### Post by nickrout on 2011-12-07
> **kenyee said:**
> LVM for easy expansion/contraction of the Linux root file system (it's used for VMs as well as being a Myth backend).
It's RAID1 underneath, so if you lose a disk, you have time to replace it before the array goes down ;-)
I'm actually wondering if I should put the multimedia array in a distributed file system instead of RAID1 since I have multiple backend servers.

I don't have nearly as much data as some of the guys around here ;)

Certainly it is good practice to put the main OS and database files on a different drive to where you are recording (a little difficult in the default mythbuntu setup as by default the database is in /var/lib/mysql and the recording files are in /var/lib/mythtv, easiest to move the recording files to a different drive, say, /mnt/sdb1 and delete the default recording storage group and specify it as /mnt/sdb1/recordings.

when you add disks, add /mnt/sdc1/recordings, etc a storage groups.

You need to specify a directory within the mount point (ie the mount point is /mnt/sdb1 and the SG definitiion is /mnt/sdb1/recordings) - that way if the disk is not mounted for some reason like a fault or boot error, the system does not record to the underlying root file system.

Hope that makes sense.

---

### Post by kenyee on 2011-12-08
> **nickrout said:**
> Certainly it is good practice to put the main OS and database files on a different drive to where you are recording (a little difficult in the default mythbuntu setup as by default the database is in /var/lib/mysql and the recording files are in /var/lib/mythtv, easiest to move the recording files to a different drive, say, /mnt/sdb1 and delete the default recording storage group and specify it as /mnt/sdb1/recordings.

Thanks...I try to do the same thing.  The OS and /boot is on a mirrored raid1 device (/boot on mdraid1 partition and the rest of the OS in an LVM/mdraid1 partition.  I usually put my mythdata into an LVM stacked onto another mdraid1 partition then mount to /mythtv.

I've actually been wondering if it'd work to put the myth data on something like these distributed filesystems:
[http://www.ibm.com/developerworks/linux/library/l-ceph/](http://www.ibm.com/developerworks/linux/library/l-ceph/)
[http://www.openafs.org/](http://www.openafs.org/)
OpenAFS should work even if it's limited to read-only copies of the data since multimedia is static.  It'd be an alternative to using mdraid to make the data reliable and would survive if your entire system died.

Or even btrfs:
[http://www.linux-mag.com/id/7308/](http://www.linux-mag.com/id/7308/)

---

### Post by kenyee on 2011-12-09
FYI, did a fresh install w/o issues using the Ubuntu Alternate Desktop ISO...only gripe is that none of the pendrivelinux flash installers seemed to be able to handle it so I had to burn an actual CD :D
The Alternate ISO had a Repair Boot option that I tried as well, but that failed miserably too (same blank screen).

I used btrfs for my /multimedia partition instead of mdraid/lvm that I'm using for the kernel/apps/root partitions to see how well it works.  I'm not sure I believe it's mature enough to handle operating system usage yet.

---

### Post by nickrout on 2011-12-09
xfs is generally thought to be pretty good for mythtv data. There are plenty of threads on the mailing list archive.

---


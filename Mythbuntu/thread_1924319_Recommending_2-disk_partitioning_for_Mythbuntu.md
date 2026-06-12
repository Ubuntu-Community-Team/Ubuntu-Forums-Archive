---
title: "Recommending 2-disk partitioning for Mythbuntu?"
date: 2012-02-12
forum: Mythbuntu
---

### Post by wo_shi_big_stomach on 2012-02-12
Greetings. What are the recommended disk partitions for a new Mythbuntu system with these requirements:

2 x 1.5T hard drives

1.9T of .nuv recordings from old Myth system

Initially I thought of just doing RAID0 with both disks but could only get software RAID to boot with RAID1. I also thought of using mythtv's storage groups (with different partitions on each disk) but I don't know how I would rysnc the .nuv files from the old system (i.e., what's the target on the new system?). A non-bootable RAID0 partition across both disks works fine but wastes some space on the second disk.

Thanks in advance for best-practice recommendations for Mythbuntu on a two-disk system.

---

### Post by nickrout on 2012-02-12
25G for /

balance of disk 1 as xfs for recordings

disk 2 as xfs for recordings

---

### Post by wo_shi_big_stomach on 2012-02-19
Thanks. Hadn't considered XFS before, but it appears to have some big performance benefits for large files.

How to combine two XFS partitions to appear as one? I did not see this in the mkfs.xfs manpage. 

The requirement here is to restore > 1.5T of recordings (around 1.9T total) onto two 1.5 drives. How would you do this? Just spread them across the two XFS partitions and define a storage group? Or is the some way of combining XFS partitions? Or something else?

Thanks again!

---

### Post by nickrout on 2012-02-19
> **wo_shi_big_stomach said:**
> Thanks. Hadn't considered XFS before, but it appears to have some big performance benefits for large files.

How to combine two XFS partitions to appear as one? I did not see this in the mkfs.xfs manpage. 

The requirement here is to restore > 1.5T of recordings (around 1.9T total) onto two 1.5 drives. How would you do this? Just spread them across the two XFS partitions and define a storage group? Or is the some way of combining XFS partitions? Or something else?

Thanks again!

Do the storage group thing. Other schemes such as LVM suffer from the problem that if you lose one partition due to a disk error or something, you lose everything across the whole filesystem. SG's do not suffer from this problem. once both directories are in the same storage group you can move files between the two (or more) directories and the backend will find them (not sure this would work for a file actually in the middle of being recorded, but that's a very edge case).

One point to note is that there is no redundancy with storage groups, but hey it's only TV, not mission critical stuff. if you want redundancy you can look at some sort of RAID system, and then add the raided filesystems to an SG. But you need more disks then (obviously) and as I say, it's just TV.

If you have videos too (ie files that are not as a result of mythtv recording them) you need to factor this in. You might want to make some of your second drive into another partition and allocate it to the videos storage group.

Last time I added a (2TB) drive I allocated 0.5TB to my recordings SG and 1.5TB to my videos SG (as separate partitions), because I am trying to centralise the videos I have on servers all over the house into the backend.

When you set up a storage group mount point make sure of this: make a directory inside the mount point, eg

my mount point is /mnt/sda1
my storage group is pointed to /mnt/sda1/recordings

This means that if, for example, something goes wrong on boot and /mnt/sda1 doesn't get mounted then myth will not record to my root partition (as it would if my SG was pointed to /mnt/sda1). It will notice that the SG point is not available and record to another SG, avoiding / being filled up - usually a recipe for disaster.

---


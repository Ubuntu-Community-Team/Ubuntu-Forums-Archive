---
title: "fsck challenges"
date: 2015-02-23
forum: Mythbuntu
---

### Post by meadrocks on 2015-02-23
I have a myth server based on mythbuntu 14.04, it created 2 partitions, /boot & /. I have fsck errors on the / partition.
root@myth-server01:~# fsck -v -n -f /dev/sda2
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
Warning!  /dev/sda2 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 172752900 has zero dtime.  Fix? no

Inodes that were part of a corrupted orphan linked list found.  Fix? no

Inode 172752901 was part of the orphaned inode list.  IGNORED.
Inode 172752902 was part of the orphaned inode list.  IGNORED.
Inode 172752903 was part of the orphaned inode list.  IGNORED.
Inode 172752904 was part of the orphaned inode list.  IGNORED.
Inode 172752912 was part of the orphaned inode list.  IGNORED.
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -(198164890--198164942)
Fix? no

Free blocks count wrong for group #6047 (9687, counted=9634).
Fix? no

Free blocks count wrong for group #22251 (31139, counted=30938).
Fix? no

Free blocks count wrong (190947358, counted=190947099).
Fix? no

Inode bitmap differences:  -(172752900--172752904) -172752912
Fix? no

Free inodes count wrong for group #6016 (30, counted=29).
Fix? no

Free inodes count wrong (182324032, counted=182324023).
Fix? no


/dev/sda2: ********** WARNING: Filesystem still has errors **********


      578752 inodes used (0.32%, out of 182902784)
        1318 non-contiguous files (0.2%)
         439 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 535987/1920/78
   540649442 blocks used (73.90%, out of 731596800)
           0 bad blocks
         170 large files

      446533 regular files
       83702 directories
          59 character device files
          25 block device files
           0 fifos
          13 links
       48394 symbolic links (40645 fast symbolic links)
          33 sockets
------------
      578759 files

I booted from a Fedora 21 live USB dist to fsck the partition, but it doesn't see any errors.
[root@localhost ~]# fsck.ext4 -p -f -v -C0 /dev/sda2
                                                                              
      578752 inodes used (0.32%, out of 182902784)
        1320 non-contiguous files (0.2%)
         439 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 535982/1922/78
   540649442 blocks used (73.90%, out of 731596800)
           0 bad blocks
         170 large files

      446530 regular files
       83702 directories
          59 character device files
          25 block device files
           0 fifos
          13 links
       48395 symbolic links (40646 fast symbolic links)
          32 sockets
------------
      578756 files

I've also booted a gparted live USB & it also gives the same results, no errors. 

Should I assume there's nothing wrong with the partition? Could it be a journal problem? This is a 3TB Seagate disk, 1 year old, server runs 24/7/365.

Thanks.

---

### Post by TheFu on 2015-02-23
Is / really ext4?  Normally when a /boot is created then LVM or encryption are on the other partitions.

---

### Post by meadrocks on 2015-02-23
Yes. I just built a new server, Mythbuntu 14.04-1, it made a /dev/sda1 /  partition, & a /dev/sda5 swap partition. Maybe LVM & encryption are select-able options, but this is the default. Either way it doesn't explain the fsck problems I'm having.

---

### Post by TheFu on 2015-02-23
Can you boot off an Ubuntu desktop disk and run it without any options?
**sudo fsck /dev/sda1**
I'm confused by you running against sda2 ... but saying > Mythbuntu 14.04-1, it made a /dev/sda1 / partition

Please post the output from **sudo fdisk -l** so we are certain.

---

### Post by meadrocks on 2015-02-23
If you look closely at the origional post you'll see the "578752 inodes used (0.32%, out of 182902784)" in both scans are the same, I am fsck'ing the same partition both times. I'm a UNIX/Linux sys admin with many years of experience. So I built a new Myth server w/ 14.04-1 & will bring in the problem disk (built with 14.04) tomorrow, it'll be /dev/sdb in the new server. It should be the exact same version of fsck as the one thats seeing the problems, maybe it can fix the issue.

---


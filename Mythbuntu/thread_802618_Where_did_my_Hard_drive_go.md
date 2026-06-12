---
title: "Where did my Hard drive go??"
date: 2008-05-21
forum: Mythbuntu
---

### Post by dcwdrum on 2008-05-21
Hi everybody, Long time reader, first time poster.

I just upgraded to .21 using a fresh install from the Alternate CD and I'm having trouble getting Myth to recognize my storage space.  My system has 4 (160gb) drives that are partitioned like this:

```
fstab
  GNU nano 2.0.7                                                      File: fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
# /dev/sda1	 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2	 none            swap    sw              0       0
# /dev/sda3	 /fileserver     xfs     relatime        0       2
# /dev/sda4	 /mythtv/disk1   xfs     relatime        0       2
# /dev/sdb1	 /mythtv/disk2   xfs     relatime        0       2
# /dev/sdc1	 /mythtv/disk3   xfs     relatime        0       2
# /dev/sdd1	 /mythtv/disk4   xfs     relatime        0       2

```

When I set up the backend, Under > Storage Groups > Default, I added the following Storage Group directories for my recordings:
```
/mythtv/disk1/recordings
/mythtv/disk2/recordings
/mythtv/disk3/recordings
/mythtv/disk4/recordings
```

Once the backend setup was complete and the database was updated, I used MythWeb to check the system information and I saw that the 4th hard drive is not showing up right.


```
Disk Usage:

    * MythTV Drive #1:
          o Directory: mythBox:/mythtv/disk1/recordings
          o Total Space: 89,639 MB
          o Space Used: 4 MB
          o Space Free: 89,634 MB
    * MythTV Drive #2:
          o Directory: mythBox:/mythtv/disk2/recordings
          o Total Space: 152,550 MB
          o Space Used: 2,242 MB
          o Space Free: 150,308 MB
    * MythTV Drive #3:
          o Directories: mythBox:/mythtv/disk3/recordings, mythBox:/mythtv/disk4/recordings
          o Total Space: 152,550 MB
          o Space Used: 4 MB
          o Space Free: 152,546 MB
    * Total Disk Space:
          o Total Space: 394,740 MB
          o Space Used: 2,251 MB
          o Space Free: 392,489 MB

```

Does anyone have any idea why it might be doing this?  Any help is welcome!

Thanks

---

### Post by volkswagner on 2008-05-21
Did you set up logical or primary partitions?  I believe there is a limit of 4 primary partitions.

---

### Post by dcwdrum on 2008-05-21
They are all primary partitions... partially because I didn't know the difference between primary/logical.  Do you have any recommendations about how they should be partitioned?

---

### Post by volkswagner on 2008-05-21
> **dcwdrum said:**
> They are all primary partitions... partially because I didn't know the difference between primary/logical.  Do you have any recommendations about how they should be partitioned?

Post the output of

```
sudo fdisk -l
```

---

### Post by dcwdrum on 2008-05-21
Output of sudo fdisk -l



```
dcw177@mythBox:/$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ca615

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1580    12691318+  83  Linux
/dev/sda2            1581        1945     2931862+  82  Linux swap / Solaris
/dev/sda3            1946        8024    48829567+  83  Linux
/dev/sda4            8025       19457    91835572+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d6db6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dc7c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321   83  Linux

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e98e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       19457   156288321   83  Linux

dcw177@mythBox:/$

```

---

### Post by dcwdrum on 2008-05-22
Any thoughts?  If I can't figure this out I think I might wipe the system and go back to LVM.  Storage Groups sounds like a good concept, but I'm not sure what I'm doing wrong.

---

### Post by volkswagner on 2008-05-22
If you are happy with mythtv on your system, I would not reinstall or upgrade.

Take a look at the how to on lvm.

[http://ubuntuforums.org/showthread.php?t=584473]("http://ubuntuforums.org/showthread.php?t=584473")

Can you just repartition the last two drives and set them as logical, with the whole drive partitioned as one extended drive?

---

### Post by dcwdrum on 2008-05-22
I'm definitely happy with Mythtv.  I'll try your suggestion to repartition the drives as logical.  Thanks for your help so far!

---

### Post by dcwdrum on 2008-05-22
So I just repartitioned the system using logical partitions.  Below is the current fdisk -l.  By the way, the 4 hard drives are all SATA if that can help you.

```

dcw177@mythBox:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ca615

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1580    12691318+  83  Linux
/dev/sda2            1581       19457   143597002+   5  Extended
/dev/sda5            1581        1823     1951866   82  Linux swap / Solaris
/dev/sda6            1824        7902    48829536   83  Linux
/dev/sda7            7903       19457    92815506   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d6db6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    5  Extended
/dev/sdb5               1       19457   156288289+  83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dc7c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    5  Extended
/dev/sdc5               1       19457   156288289+  83  Linux

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e98e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       19457   156288321    5  Extended
/dev/sdd5               1       19457   156288289+  83  Linux
dcw177@mythBox:~$

```

When I partitioned the hard drives, I mounted them as:
```
/mythtv/disk1
/mythtv/disk2
/mythtv/disk3
/mythtv/disk4
```

When I set up the Storage Groups in mythtv-setup, I set them like this:

```
/mythtv/disk1/recordings
/mythtv/disk2/recordings
/mythtv/disk3/recordings
/mythtv/disk4/recordings
```

After all of that, when I check the backend status in MythWeb (below), all of the hard drives are still not showing up.  Disk1 and disk2 show up, but the other 2 disks are shown underneath Disk2 and not as independent drives.  I don't know what to do.  Could this be a permissions issue?  Should the drives be mounted in the /var/lib directory?  All I know is that I'm missing 320gb of storage because of this.:(

```
Machine information
This machine's load average:

    * 1 Minute: 0
    * 5 Minutes: 0.03
    * 15 Minutes: 0.11

Disk Usage:

    * MythTV Drive #1:
          o Directory: mythBox:/mythtv/disk1/recordings
          o Total Space: 90,595 MB
          o Space Used: 4 MB
          o Space Free: 90,591 MB
    * MythTV Drive #2:
          o Directories: mythBox:/mythtv/disk2/recordings, mythBox:/mythtv/disk3/recordings, mythBox:/mythtv/disk4/recordings
          o Total Space: 152,550 MB
          o Space Used: 4 MB
          o Space Free: 152,546 MB
    * Total Disk Space:
          o Total Space: 243,146 MB
          o Space Used: 9 MB
          o Space Free: 243,137 MB

Last mythfilldatabase run started on 2008-05-22 21:04 and ended on 2008-05-22 21:04. Successful.
Suggested next mythfilldatabase run: 2008-05-23 13:10.
There's guide data until 2008-06-05 02:00 (14 days).
DataDirect Status: Your subscription expires on 11/23/2008 12:19:49 PM
```

---

### Post by dcwdrum on 2008-05-22
So I think I may have found what was happening.  Up until this point, the system has been fresh and no recordings have been made yet.  Out of pure curiosity and a slight hunch, I decided to record a show just to see what would happen.

After the recording started I checked the machine information in MythWeb again and I saw that the 3rd drive has now been defined, leaving only the 4th drive still missing.  So I'm thinking that when using Storage Groups in MythTV, the groups that you define will not actually show up until there is data stored in that group.

Has anyone else experienced this to be true?  Is so, this might be worth documenting because it wasn't so obvious to me.](*,)

Thanks everyone!

---

### Post by OldGaf on 2008-05-31
Just out of curiosity...... do you use MythWeb? If so, are you able to see all the recording on all these groups? Can you click on them all and not get an error?

---

### Post by dcwdrum on 2008-06-04
Yes, I do use MythWeb and I am able to see/ view all of my recordings.  What happened was this... I have 4 hard drives in my MythBox and after everything was said and done, I had 4 partitions that I wanted to use for recordings.  I added all 4 partitions under the "Default" storage group during Myth-Backend setup, however when I was looking at my system statistics on MythWeb, not all of the partitions were showing up.  It wasn't until the system started recording shows and using space in each partition that they showed up.  So currently everything is fine and dandy, but it was confusing to me at first because I couldn't figure out why my drives were not showing up as available storage space.

---


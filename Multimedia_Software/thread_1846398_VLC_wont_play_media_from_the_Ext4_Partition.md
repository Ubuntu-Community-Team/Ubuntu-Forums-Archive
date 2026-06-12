---
title: "VLC wont play media from the Ext4 Partition"
date: 2011-09-19
forum: Multimedia Software
---

### Post by fantab on 2011-09-19
VLC MEDIA PLAYER does not open media files from a dedicated media only ext4 partition.

In my Lucid Lynx_amd64 I use VLC MEDIA PLAYER only and I have successfully removed all the other defaut media players. I have media mostly in "restricted formats" so I just use VLC instead. 

I have a seperate partition on my HDD especially dedicated to my media and this partition is neither dedicated to "/", "/home", "/data" or anything else. It is formatted as EXT4 nevertheless. 
Here is the Partition in question:

```
$ ls -l /dev/disk/by-uuid
lrwxrwxrwx 1 root root 10 Sep 19 08:17 37e3b0f7-3ade-4f6d-b85d-94adf7725d5b -> ../../sdb1

```                          Now here is the issue;** VLC media player DOES NOT OPEN media files** from this particular partition... even when I have all the "necessary permissions". (I mount the said partition, and open it with *gksu nautilus*).

I also use LINUX MINT DEBIAN EDITION, where all the so called "restricted formats" are installed by default, and where the TOTEM MOVIE PLAYER opens the media files from the said partition without any issue. Even here however, ie in LMDE, VLC does not play the same media files from the same said partition.

I request the forum to help me resolve this issue for me...
Thanks

---

### Post by fantab on 2011-09-19
Bump... it has been 8 hrs. 
Help please!

---

### Post by sisco311 on 2011-09-19
Please don't BUMP your posts too often. Wait at least 24-48 hours.

---

### Post by BicyclerBoy on 2011-09-19
This may not be the correct way but it is tidy..
I would mount any removable HDD into the filesystem at /media/my_ext_hdd

Create the folder /media/my_ext_hdd (use any name).
Set the ownership/permissions.
Mount the HDD at the above mount-point with terminal cmd mount.

Or this tool looks nice..
[http://www.howtogeek.com/60817/how-to-auto-mount-partitions-at-linux-startup-the-easy-way/](http://www.howtogeek.com/60817/how-to-auto-mount-partitions-at-linux-startup-the-easy-way/)

I use /mnt/some_name as the mount-points for fixed/permanent HDD partitions.

This concept of mount-points is very different to old windows/dos.

---


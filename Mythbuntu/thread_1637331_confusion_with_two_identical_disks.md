---
title: "confusion with two identical disks"
date: 2010-12-04
forum: Mythbuntu
---

### Post by jape42 on 2010-12-04
Hi All,

I recently did a clean install of 10.10 and mythtv 0.24 and it seems there is some confusion related to storage.  I've added 3 dirs/disks to to the default storage profile, but for some reason the system is confused by two identical disks/partitions (sda6 and sdb6).  Has anyone else seen this?


jp


root@vcr:/home/jape# mount
<snip>
/dev/sdc6 on /data/disk3 type ext4 (rw,commit=0)
/dev/sda6 on /data/disk1 type ext3 (rw,commit=0)
/dev/sdb6 on /data/disk2 type ext3 (rw,commit=0)


root@vcr:/home/jape# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             19236308   3295780  14963376  19% /
none                   1859868       388   1859480   1% /dev
none                   1899700         0   1899700   0% /dev/shm
none                   1899700       340   1899360   1% /var/run
none                   1899700         0   1899700   0% /var/lock
/dev/sdc6            1863230168  72014272 1696569320   5% /data/disk3
/dev/sda6            421082124 399692568         0 100% /data/disk1
/dev/sdb6            421082124 399692544         0 100% /data/disk2




myth reports:

Disk Usage Details:

    * MythTV Drive #1:
          o Directories: vcr:/data/disk1/recordings, vcr:/data/disk2/recordings
          o Total Space: 411,213 MB
          o Space Used: 411,213 MB
          o Space Free: 0 MB
    * MythTV Drive #2:
          o Directory: vcr:/data/disk3/recordings
          o Total Space: 1,819,560 MB
          o Space Used: 162,754 MB
          o Space Free: 1,656,806 MB
    * MythTV Drive #3:
          o Directory: vcr:/var/lib/mythtv/livetv
          o Total Space: 18,785 MB
          o Space Used: 4,172 MB
          o Space Free: 14,612 MB

---


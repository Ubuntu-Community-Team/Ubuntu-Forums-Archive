---
title: "Disk usage incorrectly reported by backend"
date: 2011-09-27
forum: Mythbuntu
---

### Post by Bloodrule on 2011-09-27
I know from using du that my system has 50G of 500G in use.  Mythweb reports from the backend that 90G of disk space is used.  I cannot determine why the backend number is being incorrectly reported.  mythtv-status returns the same error from the backend.

Any clues?

---

### Post by ian dobson on 2011-09-27
Hi,

Simply put, is anything else on the same file system as mythtv uses for it recordings?

For example:-

Myth web says that I have used 3,756,816Mb for my recordings (on /data/mythtv/recordings) when in du I see /data/mythtv/recordings is only 2955343912Mb

df shows that my mount point /data is  7400Gb in size and 3,756,997Mb used. So mythtv reports the space used for all files on the mount point, not just the recordings mythtv has made.

Regards
Ian Dobson

---

### Post by nickrout on 2011-09-27
Is it the difference between MB and MiB and GB vs GiB?

What options are you giving to df and du? -h or -H?

---

### Post by Bloodrule on 2011-09-27
Thanks for your replies.

The MythTV Backend status page in Mythweb reports: 

Total Disk Space:
Total Space: 466,502 MB
Space Used: 93,497 MB

If I run mythtv-status from the command line I get the same result, where it reports 91.3G in use.

If I run du -h from my home directory the last line reads 51G
If I run du -h as root from the root from / the last line reads 68G

It means mythtv thinks I have >90G in use, root thinks it is 68G and as a user I get 51G.

Which is correct?

---

### Post by nickrout on 2011-09-27
> **Bloodrule said:**
> Thanks for your replies.

The MythTV Backend status page in Mythweb reports: 

Total Disk Space:
Total Space: 466,502 MB
Space Used: 93,497 MB

If I run mythtv-status from the command line I get the same result, where it reports 91.3G in use.

If I run du -h from my home directory the last line reads 51G

that is how much is in your home directory> 

If I run du -h as root from the root from / the last line reads 68G
 that is how much is on the whole filesystem> 
It means mythtv thinks I have >90G in use, root thinks it is 68G and as a user I get 51G.

Which is correct?

without knowing your disk setup and where you are storing stuff it is hard to say.

---

### Post by Bloodrule on 2011-09-27
My recordings and videos are all in /var/lib/mythtv/recordings or /var/lib/mythtv/videos etc.  It is a single 500G disk formatted to ext4.  I can't understand why, if du indicates that I have 68G in the entire filesystem, the backend says I have 91.3G in use.

---

### Post by nickrout on 2011-09-27
> **Bloodrule said:**
> My recordings and videos are all in /var/lib/mythtv/recordings or /var/lib/mythtv/videos etc.  It is a single 500G disk formatted to ext4.  I can't understand why, if du indicates that I have 68G in the entire filesystem, the backend says I have 91.3G in use.

OK I see where you are coming from now :)

I am not sure why there is a difference, but they may be counting different things.

Consider a file that is one byte long. du (I think) reports it as one byte long, but it takes a whole disk block (ie 512 bytes or 4k bytes depending on your disk's block size)

---

### Post by Bloodrule on 2011-09-28
Thanks - that's the first explanation that gives me some hope!  Do you know any command I can use to differentiate bytes in use versus blocks in use?  When I run df I get this:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            477699032  73026808 380406496  17% /
none                    506612       300    506312   1% /dev
none                    512212         0    512212   0% /dev/shm
none                    512212       900    511312   1% /var/run
none                    512212         0    512212   0% /var/lock

---

### Post by thatguruguy on 2011-09-28
I have a theory.

ext4, ext3 and ext2 file systems reserve 5% of your disk for superuser use.  On a 500 GB hard drive, that would be 25 GB.  It's possible that the myth backend sees that space on your hard drive as "occupied" space.  You can change the percentage of reserved space by following [this]("https://help.ubuntu.com/community/InstallingANewHardDrive#Modify_Reserved_Space_.28Optional.29").  Make sure you put in the correct name of your hard drive; it's probably /dev/sda1, but check first.

Try to knock the reserved space down to 1% and see if that changes how much of the hard drive myth backend is reporting as being used.

---

### Post by Bloodrule on 2011-09-29
I am impressed!  Your are spot on. The difference between df and the backend figure was accounted for by the 5% reserved for su as you predicted.  I changed it to 1% as per the link you kindly provided and your theory was immediately proved by a corresponding reduction in the disk space usage being reported by the backend.

My humble gratitude!

---

### Post by nickrout on 2011-09-29
It's worth knowing that this figure is reserved for root to enable a bit of emergency disk space. 5% is way too much when we are talking 1/2 TB disks these days. 1% should be sufficient for a main OS disk. For a storage disk you can lower it to zero.

---

### Post by thatguruguy on 2011-09-29
> **Bloodrule said:**
> I am impressed!  Your are spot on. The difference between df and the backend figure was accounted for by the 5% reserved for su as you predicted.  I changed it to 1% as per the link you kindly provided and your theory was immediately proved by a corresponding reduction in the disk space usage being reported by the backend.

My humble gratitude!

Happy to help.

---


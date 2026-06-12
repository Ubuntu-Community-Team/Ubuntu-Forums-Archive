---
title: "Raid + nas"
date: 2010-09-30
forum: Multimedia Software
---

### Post by emoguitarist06 on 2010-09-30
I was thinking of purchasing my first NAS
particularly the Buffalo Technology LinkStation Mini 1 TB
([http://www.amazon.com/Buffalo-Technology-LinkStation-LS-WSX1-0TL-R1/dp/B00365MF68/ref=sr_1_6?s=pc&ie=UTF8&qid=1285867060&sr=1-6](http://www.amazon.com/Buffalo-Technology-LinkStation-LS-WSX1-0TL-R1/dp/B00365MF68/ref=sr_1_6?s=pc&ie=UTF8&qid=1285867060&sr=1-6))

This NAS is RAID1 and RAID0 compatible. I personally know very little about RAID and I learned what I do know from [http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID) I decided I probably will not care for redundancy and since this unit is only 1TB if did RAID1 I would only have 500GB of storage so I believe I will go RAID0

**However here's my question. I understand that RAID0 helps the overall performance of read/write access correct? but does RAID0 increase the chances of disk failure? If so by how much on average would RAID0 decrease the life of the disks?**

"[COLOR="Red"]Any disk failure destroys the array, and the likelihood of failure increases with more disks in the array (at a minimum, catastrophic data loss is twice as likely compared to single drives without RAID)[/COLOR]" - **WIKIPEDIA**


Also I have another thought.

What if I initially run RAID0 and then let's say a few year down the road I start getting concerned of the possible failures of one of the drives, would it be possible to connect another 1tb or greater external hardrive (using the usb 2.0 on this nas) and change the RAID0 to RAID1 and back up all of the initial 1TB of files on the orginal NAS to the new External?

---

### Post by whoop on 2010-09-30
It can be faster, if two people are requesting or writing to different parts of the array two disk could be utilised at the same time, which is faster than if both people where  accessing a single drive...
RAID 0 isn't actually real raid. It does not decrease the lifespan of a drive, but if a drive has a theoretical chance of failure, adding a partition (another drive) to a raid 0  array will increase the chance of failure for the array.
So having a raid 0 array with two partitions (on two drives) will double your chance of (hardware) failure (in theory) compared to having the data on one partition.

I can't think of any way you could convert from raid 0 to raid 1...

---

### Post by emoguitarist06 on 2010-09-30
I understand it isn't TRUE RAID as there is no redundancy with RAID0 but because it shares a lot of RAID characteristic I believe that's why we still call it RAID0?? LOL anyway off topic

You use the word partitions... I understand (maybe not fully) what a partition is as I have my Ubuntu setup as / /home swap 3 separate partitions. But when running RAID0 would I need to setup separate partitions?

That particular NAS box is 2 x 500GB harddrives which any operating system will detect as 1 x 1TB harddrive correct? so the entire "1 harddrive" would share the same partition of FAT32 (or whatever file system this NAS uses) right?

---

### Post by emoguitarist06 on 2010-10-04
Bump bumpity bump ;)

---

### Post by whoop on 2010-10-04
If the NAS has real (hardware) RAID 0, then any OS will see the two hard disks as one partition.
If it has some fake raid technology I advise against using that and just go for a software raid setup.

Software raid is similar as fake raid only without proprietary software. So with software raid and fake raid the raid stuff is being done by your cpu and with real (hardware) raid it is done by the raid controller.

So in your case with two hard disks in one machine (no matter what type of raid) both hard disks will probably have 1 partition (so that's 2 in total) which both are part of a raid 0 array. The OS only sees one partition (under normal usage).

---

### Post by emoguitarist06 on 2010-10-11
Thanks for the help. With this information and thanks to [www.category5.tv](www.category5.tv) I understand and I decided to not go RAID0

Basically running RAID0 is like doubling your chance of a harddrive failure and RAID1 (with two harddrives) is reducing that chance by 50% ;)

---


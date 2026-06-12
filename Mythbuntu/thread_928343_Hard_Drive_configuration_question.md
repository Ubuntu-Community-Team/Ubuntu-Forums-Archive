---
title: "Hard Drive configuration question"
date: 2008-09-23
forum: Mythbuntu
---

### Post by seattlebuoy on 2008-09-23
I will be installing a build of the 8.04 onto a new system.

Besides letting Mythbuntu format and install onto format hard drives, are there any preferred configurations? Mobo supports RAID options. I have two 500GB SATA drives.

This will be a front end/back end machine being used to record HD 720p for the most part. Dedicated to Mythbuntu.

Thanks so much for your insight and advice.

---

### Post by nasha on 2008-09-23
The configuration you select really is upto your needs. Go with RAID if you require redundancy (RAID5). I dont think you would see much perfomance gain with Raid1. Theres also the option of going with RAID0 to combine both drives into one pool.

RAID aside, you could install the OS onto one drive, and also store any videos on this drive. And add the other HDD to the default storage group, and mount to /var/lib/mythtv/recordings, and use it purely for recordings. That way your system drive is copping less read/write cycles.

Good luck!

---

### Post by mrand on 2008-09-24
Note: there is not really any good reason to use the RAID that is built into the motherboard.  There are mixed benchmarks (and debates) about how much it helps or hurts performance.  Not only that, but it potentially limits your migration options later (either planned migration, or unplanned due to hardware failure).  My recommendation is to use pure software raid.

> **nasha said:**
> The configuration you select really is upto your needs. Go with RAID if you require redundancy (RAID5). I dont think you would see much perfomance gain with Raid1. Theres also the option of going with RAID0 to combine both drives into one pool.You can't do RAID 5 with only two drives.  Well, technically you can create the RAID 5 group, but you won't have any protection until you add the third drive.  RAID 1 (mirroring) would be what you want if you want hard drive redundancy in a two drive setup.

> RAID aside, you could install the OS onto one drive, and also store any videos on this drive. And add the other HDD to the default storage group, and mount to /var/lib/mythtv/recordings, and use it purely for recordings. 

Lots of ways to skin this cat. I happen to mount my XFS filesystem at /var/lib.
But if you are going to use storage groups (I don't), my understanding is that you don't need to mount it at mythtv/recordings.  You can mount it just about anywhere and just let Myth know that it is there.  In fact, if you mount it at mythtv/recordings, I'm thinking there is no reason to add it to the default storage group.

> That way your system drive is copping less read/write cycles.
Good luck!

I currently only have one tuner, but my understanding is that modern SATA drives and controllers have no problem dealing with many streams being recorded and played simultaneously.

[INDENT]Marc[/INDENT]

---


---
title: "Mythbuntu System Partition Size Recommendation"
date: 2018-01-05
forum: Multimedia Software
---

### Post by jamoody on 2018-01-05
I've been running 32-bit Mythbuntu since 11.04 (2011) on what is now 10 year old hardware (currently at 14.04.5) as a dedicated MythTV frontend/backend machine.  My disk configuration is a 50G system partition with recordings directories in their own partitions which allows me to more easily (and quickly) do a backup partition clone of the system partition.  Currently only 20G of the 50G system partition is in use.

It's time to do a fresh 64-bit install on all new hardware.  Is a 50G system partition sufficient for, say, the next 10 years of upgrades or should I increase the size to 100G before starting the install?  Thanks.

---

### Post by yancek on 2018-01-05
If you have separate partitions for your data, 50GB should be more than enough.  If you have a large enough drive.  I would think even 25GB would be enough but it depends on the amount of software you install.

---

### Post by jamoody on 2018-01-09
Thanks a bunch.

---

### Post by jamoody on 2018-01-30
The Mythbuntu install took only 5G out of the allocated 50G partition.  I mounted /var/lib/mythtv to a different partition so only system files (and MythTV logs) are going into the 50G partition so I have lots of growth room for the future.

---


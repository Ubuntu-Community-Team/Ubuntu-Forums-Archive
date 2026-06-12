---
title: "Partitioner recipes"
date: 2008-11-28
forum: Mythbuntu
---

### Post by Panhead Bill on 2008-11-28
I read in a thread "Mythbuntu Partitioning" that partitioner recipes were to be included with 8.10.

My attempt to set a 2 drive pc up with the desktop disk didn't get me to where I could format the two drives in one try.

I did format the larger drive as one large xfs partition, but then had to restart the install to get the smaller drive formatted and loaded with mythtv.

Where do I find the recipes?

Panhead Bill

---

### Post by tgm4883 on 2008-11-28
The partitioner recipes are only available for a single drive system.  This is a limitation of the Ubuntu installer.

What you need to do is manual partitioning.  Partition your smaller drive with 500mb - 1000mb of swap and the rest as / (ext3).  Then Partition the other drive with a single XFS partition and mount it at /var/lib

---


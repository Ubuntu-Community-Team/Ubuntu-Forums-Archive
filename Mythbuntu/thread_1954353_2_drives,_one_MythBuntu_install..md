---
title: "2 drives, one MythBuntu install."
date: 2012-04-07
forum: Mythbuntu
---

### Post by drewdin on 2012-04-07
I just installed 64bit MythBuntu onto my machine, i have two drives, one 64gb and one 500gb drive. Im using the 64gb drive for the os, but i can't seem to get the os to see the 500gb drive.

I'm guessing that i need to partition and format the 2nd drive but all the tutorials i have found seem to be outdated, do i use fdisk, lvm, Is there a better way to do it?

Any help pointing me in the right direction would be awesome, I'm a semi-linux noob and could use some help. Thanks in advance!

---

### Post by Bucky Ball on 2012-04-07
Boot from the LiveCD, 'Try Ubuntu', open Gparted and format the drive (partition it how you like; I always make a plan first).

Don't know much about the Mythbuntu desktop (whether Gparted is available) but if it is you could probably use that (if it can see the drive).

If you can't 'Try Ubuntu' from the Mythbuntu install CD then you can download the Gparted ISO, make a CD and boot that. ([http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php))

Remember: All partitions on a drive need to be unmounted before resizing/manipulating partitions. As this sounds like a new drive (with nothing on it) this shouldn't be an issue.

---

### Post by drewdin on 2012-04-07
thanks for the reply, i have gparted up and going and I'm ready to create a partition. 

I have a question tho, do I want to create a Primary or Extended Partition? I have been googling around but everything i read is unclear. I am guessing extended but before i format it I want to make sure. 

Thanks again!

---

### Post by drewdin on 2012-04-07
I created a primary partition, seems to work fine. Thanks again for the help!

---

### Post by Bucky Ball on 2012-04-07
No problem. 

Primary partition or an extended partition with logical partitions inside that (the extended partition is like a holder for logical partitions). Either/or.

Remember: One physical drive can have a maximum of four primary partitions. The way around this is three primary partitions and the fourth an extended. Theoretically, you can then put as many logical partitions inside that extended partition as your hardware can handle ...

If you have solved your problem please mark thread as 'Solved' from 'Thread Tools' at the right above the first post to help others. ;)

---

### Post by drewdin on 2012-04-07
will do, so i guess having a primary partition is fine, i was thinking that it can only have one primary partition and the rest would have to be extended. but you can have as many primary as you want but they can only have 4 partitions each, where an extended partition can have as many as you want, is that correct? 

Thanks

---

### Post by Bucky Ball on 2012-04-08
> **drewdin said:**
> ... i was thinking that it can only have one primary partition and the rest would have to be extended. but you can have as many primary as you want but they can only have 4 partitions each, where an extended partition can have as many as you want, is that correct? 

Thanks

Yes to primary partition for your purpose being fine but no to the rest. ;)

Primary partition = one partition.
One physical drive = four primary partitions maximum.
Extended partition = a holder for logical partitions (theoretically as many logical partitions as your hardware can handle). So;

One physical hard drive can = three primary partitions + one extended containing x amount of logical partitions INSIDE it. 

A primary partition is NOT a holder for other partitions, logical or otherwise. It is one, single, standalone partition. Windows needs to be on one. Ubuntu does not; will happily live on a logical partition INSIDE an extended partition.

There is no 'inside' a primary partition. It is not a holder. 

A quick example: If an extended partition is 400Gb, then you can create four 100Gb logical partitions inside that. If a primary partition is 400Gb, then you have one 400Gb partition and that's that.

Hope that explains it ... ;)

---

### Post by drewdin on 2012-04-12
@Bucky Ball

Thanks for the response, that makes perfect sense. So for my setup, the primary is for the OS drive and my storage can be a primary as long as I don't plan on partitioning the drive with more than 4 partitions. If I wanted to partition a 500g drive into five 100g partitions I should use extended.

So either is fine to use as long as I use it for what i need.

---

### Post by Bucky Ball on 2012-04-13
> **drewdin said:**
> @Bucky Ball

... for my setup, the primary is for the OS drive and my storage can be a primary as long as I don't plan on partitioning the drive with more than 4 partitions..

Yes.


> **drewdin said:**
>  If I wanted to partition a 500g drive into five 100g partitions I should use extended.

Yes. How many logical drives you want to put in to the extended partition and how many primary you want is up to you and circumstance ... ;)

> **drewdin said:**
> So either is fine to use as long as I use it for what i need.

Yes. Make it what you want to work with. What it's all about.

... which is why I get a pencil and paper and work out how I am going to split the drive up before launching into it ...

---

### Post by drewdin on 2012-04-13
awesome, you have been a big help! thanks again

---


---
title: "HDD and SDD questions"
date: 2011-03-27
forum: Mythbuntu
---

### Post by itlarson on 2011-03-27
I would like to move my data to a RAID 1 consisting of two 2tb drives, and my root directory to a SSD.  What do I need to know about partition alignment, 4k sector sizes and other partitioning issues?  There's alot of stuff about this on the internet, and it's all very confusing.  The gist of it it seems to be that if this isn't taken into consideration at partitioning time, there can be a performance penalty.  

I am considering using [SAMSUNG Spinpoint F4 HD204UI]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152245") drives for storage, and [Corsair Nova CSSD-V32GB2-BRKT]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820233122") for the operating system.  In the past I have always used WD green drives, but I have heard so many bad things about them with RAID and linux in general, that I have decided against them.  When I searched the feedback on the Samsung for "linux raid" Every review was five stars.  Hopefully they are close to being as quiet as the WD drives, since this is for a combined system which sits in the livingroom.

---

### Post by ian dobson on 2011-03-28
Hi,

Yep the wd drives are really quiet, I have 7 of them in my backend server.

For 4K drives just manually partition them using fdisk -u /dev/sdX and set the start address for the partition to a sector number divisable by 8 (64 for example).

If you don't align the partition to a 4K sector boundry when linux writes a 4K block to the disk, part of the data lands on one sector and the other part lands on the next sector. So you have 2 read,modify,write cycles for the 2 sectors which really slows down writing.

Regards
Ian Dobson

---

### Post by itlarson on 2011-03-29
Thanks- that helps.  The storage drives will each be one big partition, but I will do the /8 thing for the ssd.  Are you using the WD drives for RAID?  Newegg reviews are very mixed on using them for this.  If you are, have you done any firmware updates, or special configuration?  Is the head park issue no longer a problem?  What model are they?

---

### Post by ian dobson on 2011-03-29
> **itlarson said:**
> Thanks- that helps.  The storage drives will each be one big partition, but I will do the /8 thing for the ssd.  Are you using the WD drives for RAID?  Newegg reviews are very mixed on using them for this.  If you are, have you done any firmware updates, or special configuration?  Is the head park issue no longer a problem?  What model are they?

I have 4 (sometime soon 5) wd20eads in a RAID5 array and 3 (sometime soon 4) wd20ears in a RAID0. The RAID5 array is my main data array and the RAID0 is just a backup array for unimportant data. I've not done anything special (appart from partitioning the wd20ears so that the partion starts on a 4K boundry). I think the problems your thinking about with large wd drives and RAID are when you use a Hardware RAID controller, which in my case isn't relevant as I'm using mdadm.

Regards
Ian Dobson

---

### Post by itlarson on 2011-03-30
Thanks for the info- I think I'll use the WD green drives after all.  I've had good luck with their 1 tb drives.

---


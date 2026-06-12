---
title: "SSD or not?"
date: 2014-05-30
forum: Mythbuntu
---

### Post by itlarson2 on 2014-05-30
My 12.04 combined frontend/backend has a RAID 1 array for storage with the OS on a SSD.  I have decided the raid is more trouble than it is worth, and that for 14.04 I will use a single new drive for storage, and reformat one of the drives from the old RAID array to use for nightly backups of recordings.  So my question is should I reuse the SSD, or just install the OS on a partition on the new storage drive?  I don't think the speed of the SSD is very noticeable for this application, and it would reduce cable crowding in my HTPC case to eliminate it.  Also, the SSD drive is old, and don't they have a limited number of writes before they fail?  On the other hand, using the SSD reduces wear and tear on the spinning drive.  

Opinions?

---

### Post by WogBoy on 2014-05-30
>   Also, the SSD drive is old, and don't they have a limited number of writes before they fail?
SSD for me everytime.
How old?  Read this. [http://www.anandtech.com/show/6459/samsung-ssd-840-testing-the-endurance-of-tlc-nand](http://www.anandtech.com/show/6459/samsung-ssd-840-testing-the-endurance-of-tlc-nand)
From what I understand SSd's are not as delicate as people think. Mine cost 140 AUD it has a 3 year warranty I think it will last at least twice that, Now given that I use Kubuntu 14 LTS and installed it on a new SSD, Worst case I figure in 5 years time I will install a new SSD with the new LTS of Kubuntu , The speed alone is worth a new drive every 5 years. And in 5 years I think we will see 1TBSSD for under 100 AUD

AUD = Australian Dollars.

Even this is quite cheap.
[URL="http://www.ebay.com.au/itm/SAMSUNG-840-EVO-MZ-7TE1T0BW-2-5-1TB-SATA-III-TLC-Internal-Solid-State-Drive-/350859678002?pt=US_Solid_State_Drives&hash=item51b0ddd132"]http://www.ebay.com.au/itm/SAMSUNG-840-EVO-MZ-7TE1T0BW-2-5-1TB-SATA-III-TLC-Internal-Solid-State-Drive-/350859678002?pt=US_Solid_State_Drives&hash=item51b0ddd132


[/URL]
The HDD is dead, Long live the SSD.
Please note this is just my opinion.

---

### Post by oldfred on 2014-05-31
I added an inexpensive 60GB SSD to my old system almost 3 years ago now and will include an SSD in almost all new systems. 

But I also boot from a flash drive with a full install on occasion. Which is much slower than a hard drive especially for writes. But once an app is in RAM it runs just as fast. And RAM caches recent activity so recent apps can be reused just from RAM.

So if not rebooting a lot and you have a fair amount of RAM so it does not have to frequently load new software apps from drive, SSD may not offer a lot of speed.

---

### Post by blm-ubunet on 2014-05-31
Definitely yes..

The last couple of mythtv releases have had terrible mysql database transaction overhead.
This was especially noticeable playback of in-progress recordings.
Worse if you auto commflagged.
A SSD for mythtv / mysql database tables was almost mandatory (IMO).

Recent changes in master (& maybe 0.27.1) could well have solved this.

SSD can be physically small/low power & quiet, also makes compiling large projects (like mythtv) much faster.

A SSD would also make a great temp recording storage in conjunction with housekeeping job to move recordings off to another folder (same storage group) on HDD.
Might be able to get rotating storage to spin down.

---

### Post by itlarson2 on 2014-06-02
Thanks everyone.  I bowed to the consensus and installed on the SSD.  I did create an extra partition on my new drive, though, so I can install there if the SSD dies.  I shrunk the old root partition on the SSD, and created a second partition on it for 14.04.  That way I was able to leave 12.04 in place in case I had problems with the new install.  Good thing I did.  All my database backups were bad.  I had to boot back into 12.04, run a repair on the database, and make a new backup of it.  Then I was able to restore it in 14.04.

---


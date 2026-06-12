---
title: "Backend Hard Drive setup/configuration? RAID 5?"
date: 2008-06-09
forum: Mythbuntu
---

### Post by elliott6 on 2008-06-09
(Background a couple paragraphs down at the bottom)

My questions for this post surround the hard drive configuration.  I am thinking of having the backend use 3 500GB hard drives in Raid 5, to give me 1TB of backend space.  
Is this then expandable, so that if I add a 4th drive I simply format the drive, add to the raid configuration, and I get that 1TB to 1.5TB?  Or do I need to add LVM to this mix?  I did search and found nothing definitive.  I will add another drive for the "system" to make it independant of the "storage."

My goals are the following:
- Record - currently one PVR150, but adding an HDHomeRun, as well as connecting cable box to firewire.
- Videos - store and serve downloaded TV shows that I have missed recording, as well as they are already cut and compressed.
- Music - looking to catalog my CD collection to FLAC, while simultaneously or post process transferring to my windows box transcoded so I can load them on iTunes and sync with the wife and my iPods.  
- DVDs - possibly, and just possibly, due to the huge filesizes and vast collection I have, store DVDs.
- Redundancy - in the case of a drive failure I will not want to reencode my cds, as well as lose recordings/videos; just want to pop in a working disk and continue on.

Does the 3 500GB drives in raid 5 make sense?  Is there a better option for me, using storage groups?  I am still reading up on this and haven't done anything further with 8.04 other than running the live CD on the frontend to be sure it works.  I am looking for the redundancy in the event of a drive failure, which is why storage groups doesn't seem like a perfect fit.  

Background - 

I have been successfully running Mythbuntu 7.10 since the launch.  Of course, I have become a little bit more ambitous and come here seeking your thoughts/insights.  Looking to expand on the media centre and server capability by separating the frontend and backend.  Currently I can record just fine with the PVR-150 and serve videos in my current fe/be.  I am looking to move this to work as a primary BE.  I am also looking to tempt the "ain't broke/don't fix" mantra by upgrading the backend to 8.04, as this is what I will install on the FE.  Will backup mySQL db first of course.

I know one can never have enough hard drive space, thus my approach.  I am still on socket 939 tech, as I started this journey 3 years ago, and don't plan to change anytime soon.  I currently have the following setup(s) - 

Frontend/Backend (moving to primary Backend)
MB - Abit AV8-3rd Eye
CPU - AMD64 3000+
Memory - 2GB
Video - 6600GT
Tuner - PVR150
HD - 500GB
DVD-RW drive
Mythbuntu 7.10

Frontend 
MB - Foxconn 6150BK8MC-KRSH
CPU - AMD64 X2 4200+
Memory - 1GB
Video - 8800GT (with fanless heatsink)
HD - 60GB 2.5"
Mythbuntu 8.04
DVD drive
Xbox360 HD-DVD usb

I will purchase an additional tuner(s) - HDHomeRun and connect my cable box via firewire - as well as a 3rd 500GB hard drive to make the RAID 5 storage (I have a second in my Windows box with videos and DVDs on it).  I also have the following drives - 80GB, 160GB, and 300GB all decent enough to use (SATA, quiet, and relatively newer).

Sorry for the length, as I have tried to pare it down.  Trying to juggle providing enough detail without the rambling I tend to do.  Thanks for making it this far, and I welcome your suggestions!

---

### Post by bah1976 on 2008-06-09
That looks remarkably similar to what I wanted / have done, so I'll share my results.  As to the question of RAID5 vs storage groups - Storage groups don't mitigate any drive failures - as far as I could tell.  My understanding is that it allows you to add space to Myth by adding an extra disk and putting it into the storage "pool" but doesn't provide any redundancy.  If you have 3 disks in storage groups, you get 1.5T of space to play with, but if a drive fails, you lose whatever's on it.  With that in mind, I ended up with the following relevant setup:

4xSATA port motherboard (biostar TF560+, if you care)
AMD 4400+ CPU
IDE CD/DVD drive
1x80GB for system/boot/virtual machine storage (WD800JD from newegg - cheapest I could find)
3x500GB in mdadm RAID5/LVM/JFS (WD5000AACS - from best buy because I had a gift card - otherwise newegg is cheaper)  The greenpower / variable speed intrigued me...
MythBuntu 8.04 x64
2xKworld 115 tuners for OTA use
This is a master BE / FE.  When I upgrade to an HDTV next year, I'm planning on building a dedicated FE just for the better HD video.  This BE/FE will continue to use the modulated A/V to the TV upstairs via coax.

I've recorded 2 ATSC feeds  at the same time without any problems.  Keep in mind ATSC streams about 8GB/hour.  So roughly I'm writing 16GB/hour.  I have not had a chance to record 2 and watch a pre-recorded at the same time yet - so I can't report on that kind of performance.  I don't expect any issues.

I ended up using LVM on top of the RAID array.  I think I could have done it without LVM, just using RAID5 and JFS on top of it, but in the odd chance that I end up expanding (who needs more than 1TB, really?) I figured I could handle the small overhead of LVM.  I symlinked to the new drive so I didn't have to change anything in the myth setup.  I also installed smartctl and configured it to proactively email me if there are any smart errors.  Glad I did - my 30-day old /dev/sdb starting generating errors already.  I have to folders off the top - /mythtv & /storage - I have /storage shared via samba for my wife's XP machine so it's also redundant.  I'm trying to think of what else I changed - this has been a long process of an hour or two each day to do a thing or two.

Anyway, check out these links:
[http://mythtv.org/wiki/index.php/LVM_on_RAID]("http://mythtv.org/wiki/index.php/LVM_on_RAID")

[http://www.gagme.com/greg/linux/raid-lvm.php]("http://www.gagme.com/greg/linux/raid-lvm.php")

I can't find the smartctl link - I think I used combined info from a bunch of google searches.

Of course - if you have money to spare, a hardware RAID card is much more efficient.  Look into LSI or 3ware raid cards - if I remember right they were be pretty well supported.  The ones I found were in the $300 range, so I went with the software raid to balance the cost vs WAF.

I'll keep an eye on this thread - let me know if you have trouble and I'll try to help.

---

### Post by blackoper on 2008-06-10
you do not need to use lvm to expand your raid 5 array. I have used mdadm grown/online capacity expansion multiple times. I wrote a section on the mythtv wiki on how to do it:

[Raid Online Capacity Expansion for XFS]("http://mythtv.org/wiki/index.php/RAID#Software_Raid_Online_Capacity_Expansion_.28OCE.29_.28for_raid_5_with_XFS.29")

what you want to do is easily done without lvm. Lvm is just an annoyance to me and I don't use it on either of my raid 5 arrays.

---

### Post by ian dobson on 2008-06-10
Hi,

Sounds alot like my system. I have 4 500Gb drives in a RAID5 array. You can expand/grow an array if your using mdadm.

I'm actually going to grow my array some time soon, I'm slowly running out of disk space :eek:

I can record on channel from my PVR150 and 2 from my DVB-C card and watch a recorded program at the same time without any problems (Writing about 8Gb/Hour, reading 2.5Gb/Hour).

Save your money and don't buy a hardware raid controller, buy extra memory/a good backup system (RAID doesn't help if you delete the wrong files by mistake.)

Regards
Ian Dobson

---

### Post by bah1976 on 2008-06-10
So if the expansion can be done with pure mdadm, why is lvm recommended?  I'm thinking I'm going to start over before I'm too far into this and just go with raid and remove the LVM part.  Is the LVM part recommended to allow the file system to expand?  So if I have 3 disks in raid5, formatted with JFS.  If I add a disk, I then use mdadm to expand the physical size, then is there a way to grow JFS?  Or when I start over, should I go with XFS instead?  I know about storage groups, but i'd prefer to have it all in one big place if I can.  I don't remember right now what the difference is, or why I went with JFS.

The LVM/JFS setup was one of the parts I was a bit fuzzy on, and finally decided it would work so I went with it - but I'm not married to the config if there's a better way.

---

### Post by blackoper on 2008-06-10
It depends on the file system that you use. I believe JFS can grow and shrink without lvm. You can only grow XFS (last time I checked) which is fine with me since I"m always adding more to it and never removing drives.

---

### Post by elliott6 on 2008-06-12
Thanks all for your insights.  So I think I will actually do this RAID 5 array for all of my media on the backend.  Basically have 3 500GB drives to start that will give me 1TB (just under, I know).  Adding a fourth disk, which is all the SATA ports I have, will then give me 1.5TB.  I also think I can salvage a smaller IDE drive for the system install to save the fourth port for later.

I should then have - 

system - 
6GB / ext3
3GB swap
31GB /var xfs

media - 
1TB RAID 5 array for /media xfs

This will house recordings, videos from downloads, and my ripped music, possibly ripped DVDs.

Does that sound right?  And from the posted, it seems as if I won't have a problem recording 2 HD programs while serving another?  I will also probably format as XFS because I probably won't ever care to shrink the array.  Was going to do LVM, but looks like I won't need it.

I will have the PVR-150 and HDHomeRun, and the most I probably will record is 2 at a time.  

Thanks again.  I will be getting to this in the next week or so when the 3rd hard drive comes in.  I guess I have some reading to do on RAID install, mdadm, and smartctl.  Will keep you posted!

---


---
title: "Optimal HD Use/Partitioning for MythTV FE+BE"
date: 2009-08-19
forum: Mythbuntu
---

### Post by jalyst on 2009-08-19
Hi All,

Just seeking some general advice on how best to approach this!

I'm building a Mytbuntu HTPC/PVR...
To begin with it will be the Media Front-end "AND" Back-end...

Longer term I hope to move the Back-end/PVR into a VM on a Native VMM system that I'll be building.

My system specs are:

Gigabyte GA-P35-DQ6
Antec TruePower 3.0 650w
Intel E6420 2.13Ghz ----------------------- [Core2Duo;Conroe]
Generic 1GB DDR2-800 (PC6400)
DNTV Live QuattroS Dual-Hybrid DVB-T/S
Asus EN8600GTS 256MB DDR3 ----------- [HDCP] 
The following SATA 1.5/2 drives:
-1x 1TB WD Caviar Black
-1x 250GB Seagate ------------------------ [I think? YTBD]
-1x 150GB WD Raptor
-1x 74GB WD Raptor

How do you think I should use my HDD's and what way do you feel I should partition them? 
Any other general advice is most welcome!

I've been "planning to" build a HTPC/PVR for over 6yrs now.
Finally I'm getting round to it! *touch-wood* ;-P

All the best,
j.

---

### Post by jalyst on 2009-08-20
Anyone?
Thoughts greatly appreciated.

Cheers

---

### Post by stevanbt on 2009-08-20
Hi,
For what it's worth... I have separate FE & BE, my BE is partitioned as per screen shots, but this is not ideal!! 

I suppose I would put my boot and root partitions on the 320, together with a single partition for pictures, videos and music.  Then have all recording (inc HD in my case) on the 1TB drive.

Keeping the root partition relatively small means that you can back it up easily.  And it makes sense to keep everything else separate.  I'm sure someone must have written a guide to partitioning.

I can't comment on whether your hardware will work - but raptor drives appear a little excessive?

Hope this helps, Steve.

---

### Post by jalyst on 2009-08-20
Thanks for your thoughts!

Good idea, i will see if there's some guides for MythTV FE/BE partitioning. 

Yeah I know the drives are a little excessive they;re just left overs from a prior workstation

---

### Post by jalyst on 2009-08-21
Is there a MythTV/Linux centric one?
Haven't been able to find one thus far.
It's for this
[http://ubuntuforums.org/showthread.php?p=7812980](http://ubuntuforums.org/showthread.php?p=7812980)

Cheers,
J.

---

### Post by jalyst on 2009-08-21
anyone? advice very much appreciated.

---

### Post by xinix on 2009-08-21
Is this going to be a system you use as a desktop for web ,email, music, photos, document writing?  Or is this going to strictly be a htpc that only records tv or plays movies?

It would be easier to suggest a partition scheme based on the exact intended use of the system.  On mine I have 10G for root, 10G for my home partition, and the rest of the space (220G) for recorded stuff.  I only use this to watch recordings and playing DVDs.  I have this on two drives that I joined as LVM (two drives, one partition) so that I could maximize my storage for tv. I Really like keeping my recordings and database in a partition that is separate from my system so that I can clean install the OS when I upgrade to a new version, or I don't lose my recordings and DB if something bad happens.

 If you are going to use the system for photos and music you should figure out how much how much space you are currently using and then create a partition with plenty of room to grow, or just dedicate one of the drives for that.

---

### Post by jalyst on 2009-08-21
Hi Xinix, thanks for chiming in! It is "purely" a HTPC/PVR.

I've realised that the tuner card is almost useless in 'GNU/Linux' but I'm hoping to find something with a similar feature-set. 
[http://www.xpmediacentre.com.au/community/tuners/38563-dntv-live-quattros-simialr-linux-support.html](http://www.xpmediacentre.com.au/community/tuners/38563-dntv-live-quattros-simialr-linux-support.html)

At the time I bought it driver dev. support looked promising, but apparently it's stalled...

So I'm in the midst of finding something that suits my requirements. 
That may mean the PVR component is moved to an entirely separate machine, still trying to determine if this will be necessary.
[http://forum.doom9.org/showthread.php?p=1317048](http://forum.doom9.org/showthread.php?p=1317048)

I was hoping my hardware was already bedded-down! :-)
This is where it gets painful as I can be extremely anal about selecting components and spend way to long researching :-(

---

### Post by tgm4883 on 2009-08-21
I would do 

10-15 GB for / (if you have a small drive just use it for /)
1-2 GB Swap
All other drives mounted and setup as recording directories. I'd mount the drive and then have multiple directories under the mount point (recordings/, videos/).

Then just have a healthy setting for free disk space (10 GB) and you should be able to add file to it no problem, and always have 10 GB free space, unless you fill it up with videos, MythTV will only auto expire recordings.

---

### Post by xinix on 2009-08-21
As a DVR you'll want the bulk of your drive capacity dedicated to recording storage.  Here's what I would do if I had that group of drives.  Hopefully others will suggest what they would do as well as they may think of something else important that I don't.

With the 74GB drive:
10GB for the root partition / (a basic install will really take up about 2.5 - 3GB)
5-10GB for a /home partition (plenty of storage for user files this much is kind of overkill)

If you stick to the 1GB RAM (I'd maybe go up to two or three, ddr-800 is fairly cheap now, but one will suffice) then about 2GB for swap.  If you are going to let the system go into standby  you need enough swap space to hold what is currently in RAM plus the used swap.  So scale your swap based on ram.  I'd love to let my system go into stanby but resuming sucks.

stevanbt has a partition for live tv.  I think this is a great idea and will do something like this next time I add more space.  This way live tv won't push out any expired shows in order to have space. I'd use up the rest of the drive for this partition.

Then I'd dedicate the other drives as storage for your recordings.  You should be able to set each drive as a storage space or you could join them into a single "partition" using LVM.  I do this for my storage, but it does add a bit of complexity.

The bottom line is that you have a ton of storage space.  The OS and user files don't need very much space.  So dedicate as much as you can to the purpose of the machine, recordings.

If you really want you could pair down to one drive and send the rest to me, just kidding.

---

### Post by jalyst on 2009-08-22
> With the 74GB drive:
10GB for the root partition / (a basic install will really take up about 2.5 - 3GB)
5-10GB for a /home partition (plenty of storage for user files this much is kind of overkill)

I suppose if I eventually need more than 10GB I can always resize. 
/home = /"default non-root user" ?  Same for this partition too.

> If you stick to the 1GB RAM (I'd maybe go up to two or three, ddr-800 is fairly cheap now, but one will suffice) then about 2GB for swap.  If you are going to let the system go into standby  you need enough swap space to hold what is currently in RAM plus the used swap.  So scale your swap based on ram.  I'd love to let my system go into stanby but resuming sucks.

So the general rule is; swap space = total RAM x2

> stevanbt has a partition for live tv.  I think this is a great idea and will do something like this next time I add more space.  This way live tv won't push out any expired shows in order to have space. I'd use up the rest of the drive for this partition.

Some interesting ideas thanks!

The 74GB is an old drive, also part of the sata plug on the drive snapped-off inside it's original cable (a widely reported issue for this drive). 
It still plugs in but not as firmly as other drives. I don't think it's an issue as it happened soon after I got it, and I used it for a few years in another workstation. 
But I'm reluctant to use it as my _system drive_ because of this, and prolly more so because of its age!

So I'll prolly employ what you've suggested on the 2nd smallest drive; the 150GB Raptor, this also isn't very new but it's hardly been used.
I thought if I'm transcoding up-to-four streams whilst watching one or two at the same time... 
Then _both_ of the fastest drives would _have_ to be employed, but hopefully that wont be necessary.

> Then I'd dedicate the other drives as storage for your recordings.  You should be able to set each drive as a storage space or you could join them into a single "partition" using LVM.  I do this for my storage, but it does add a bit of complexity.

So 74gb, 250gb, & 1TB into one extended partition? I know of this parlance but never really understood the significance.
Why is it better than just having three drives, each with their own discrete partition?

> The bottom line is that you have a ton of storage space.  The OS and user files don't need very much space.  So dedicate as much as you can to the purpose of the machine, recordings.
If you really want you could pair down to one drive and send the rest to me, just kidding.

Makes sense, at least on the surface. Hehe, well if you ever happen to be in Brisbane/Australia, then at the very least I owe you a beer or two!

jed.

---

### Post by jalyst on 2009-08-22
Thanks, one of the links i provided in my 1st post outlines my drives but here they are:

The following SATA 1.5/2 drives:
-1x 1TB WD Caviar Black
-1x 250GB Seagate ------------------------ [I think? YTBD]
-1x 150GB WD Raptor
-1x 74GB WD Raptor

> **tgm4883 said:**
> I would do... 10-15 GB for / (if you have a small drive just use it for /)
1-2 GB Swap

Have root/swap on the smallest drive or swap on a separate one?

> All other drives mounted and setup as recording directories. I'd mount the drive and then have multiple directories under the mount point (recordings/, videos/).

Should I merge all the drives into one extended partition, then mnt, then create all the sub-dirs you speak of. 
Or do you reckon it's better just to keep them all as sep. drives/partitions?

> Then just have a healthy setting for free disk space (10 GB) and you should be able to add file to it no problem, and always have 10 GB free space, unless you fill it up with videos, MythTV will only auto expire recordings.

Could you please clarify?

Assuming you do answer these remaining Qns, it's prolly best to put your response in this thread
[http://ubuntuforums.org/showthread.php?p=7812980](http://ubuntuforums.org/showthread.php?p=7812980)

Cheers!

---

### Post by xinix on 2009-08-22
Yes, you can increase and decrease partition sizes.  I've done it before using the live cd.  Be sure to backup any important files before doing this. If you are only using this as a DVR/PVR, then your system and /home space needs won't increase very much.  

You're right, /home is where non root user files are held.  It will have a folder for each user on the system.

Swap = 2x RAM is a formula that was commonly used when RAM was a precious resource and programs needed swap space.  But, now that it is much more affordable (depending on type) to have large amounts of RAM, 2x RAM seems a bit much for me.  I have 2.5 GB and I hardly ever use swap.  I've only seen maybe 3-50MB of swap being used.  I personally use swap = RAM + 1GB to decide on a swap size.   

LVM vs multiple directories.  I don't quite see a need for LVM on a current MythTV system.  Older versions only used one directory for storage.  So LVM was a handy way too increase the space for your recordings.  I don't have a good reason to keep using LVM any more.  The arguable advantage of LVM is that you can merge all storage into a single space that you can carve up as you like.  This makes it so that partitions are not confined by the size of each drive, just the total sum of the drives.

---

### Post by tgm4883 on 2009-08-22
> **jalyst said:**
> Thanks, one of the links i provided in my 1st post outlines my drives but here they are:

The following SATA 1.5/2 drives:
-1x 1TB WD Caviar Black
-1x 250GB Seagate ------------------------ [I think? YTBD]
-1x 150GB WD Raptor
-1x 74GB WD Raptor



Have root/swap on the smallest drive or swap on a separate one?


You can put root and swap on the same drive

> 
Should I merge all the drives into one extended partition, then mnt, then create all the sub-dirs you speak of. 
Or do you reckon it's better just to keep them all as sep. drives/partitions?


I'd keep them as separate drives. That way if you want to add drives or replace drives in the future it is easier. Instead of the subdirectories, you could also just dedicate certain drives for recordings, and certain ones for media.

> 
Could you please clarify?

Assuming you do answer these remaining Qns, it's prolly best to put your response in this thread
[http://ubuntuforums.org/showthread.php?p=7812980](http://ubuntuforums.org/showthread.php?p=7812980)

Cheers!

If you do subdirectories, you will need a free disk space amount so you can put new videos in there. There is a setting in mythtv that will autoexpire recordings so that you always have at least the minimum free disk space that you want. If you do sub directories then set this amount to slightly larger than what your average movie size is. Then if you add one it shouldn't be a problem with free disk space. 

Although I would probably dedicate a specific drive for this so you can use all your disk space.

---

### Post by tgm4883 on 2009-08-22
I merged the other thread in here since it was related. No reason for 2 threads.

---


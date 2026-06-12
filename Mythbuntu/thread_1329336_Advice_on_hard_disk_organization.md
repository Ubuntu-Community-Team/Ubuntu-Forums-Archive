---
title: "Advice on hard disk organization"
date: 2009-11-17
forum: Mythbuntu
---

### Post by bcg30506 on 2009-11-17
I have a good working mythtv be/fe box in our living room that has been plugging along nicely for years.  I'm still running 9.04 as it is stable and currently meets my needs.  I only have SD cable TV service.  One day we will get HD then I'll have to buy the HD-PVR 1212 boxes and upgrade to 9.10+ to support them.  For now, our PVR-150s are fine.

Anyway, I say all that as background.  This box only has one HD that is 300GB.  We store all our camcorder videos, digital pictures, videos from the internet, and of course, TV shows on it so needless to say, I'm starting to run out of space.  I only have about 24% available now.  So I was looking at purchasing a 1TB hard drive I found for only $85.  Sounds like a good deal to me?

Now my question is should I replace the smaller drive with the new one or add the new one to the system as a 2nd drive?  If I add it, how would you recommend I organize things to make the most of the space in the years to come?  Our current usage pattern looks like this:

49G     Canon (HD camcorder videos)
2.1G    music (few music files, most are on Apple via iTunes)
42G     pictures (all digital camera pictures)
65G     tv (TV recordings)
7.6M    video-images (video cover art)
45G     videos (videos from DVD rips or web downloads)
202G    total

This is the bulk of it and all data mythtv uses.  The OS is also on another partition and the /home directory is on another partition.  The above /myth partition is formatted as xfs using LVM so I guess I could "add" a new drive to the volume with LVM but don't know how and if that is better or not than just moving some or all of the above folders to a newly mounted partition.

Any thoughts?  All tips are appreciated.

---

### Post by blackoper on 2009-11-17
I'd use your old 300GB drive as a backup drive for important files in case the hard drive ever dies. Right now you have no recourse if your drive dies (raid levels of 1 or 5 help with this).

For your 1tb drive, I'd probably double or triple all the non myth recordings partitions and then use the rest for myth recordings.

---

### Post by bcg30506 on 2009-11-17
I guess I failed to mention that I do have the box being regularly backed up onto a NAS RAID-5 unit, so I'm covered there.

If I were to just "add" the new drive to the LVM pool(?) how would I go about this, and does it do what I think - that is, will it make it look like one larger disk that would get used seamlessly within the existing directory layout?

---

### Post by nickrout on 2009-11-18
> **bcg30506 said:**
> I guess I failed to mention that I do have the box being regularly backed up onto a NAS RAID-5 unit, so I'm covered there.

If I were to just "add" the new drive to the LVM pool(?) how would I go about this, and does it do what I think - that is, will it make it look like one larger disk that would get used seamlessly within the existing directory layout?

LVM is a trap. Lose one disk and you lose the lot.

Add the new disk to your storage group and move all your recording files there.

---

### Post by chipppy on 2009-11-18
Good Morning

Taking into account the problems with storage groups under myth 0.22 (Mythubuntu 9.10), may I suggest skipping the storage group idea for the moment. 
Under my 9.04 setup I had a 500GB + 1000GB drive 
500GB for OS and TV recordings
1000Gb drive for everything else.

My trick was to mount the 1000GB drive into the default location for myth storage of files eg
default storage path in mythtv for video files
```
/var/lib/mythtv/videos
```
my 1000GB har drive mount point path
```
/var/lib/mythtv/hdd2
``` and then extending for video storage
```
/var/lib/mythtv/hdd2/videos
.../pictures
.../coverart
.../music
etc
```

This means that you only really need to remember one path as it is all in the same spot just one hdd2 folder extra as required.  Simple and neat.
I have a cron to backup entire 'hdd2' and OS, ignoring tv recording folder, to NAS once per fornight

Just my humble suggestion though

Cheers
chipppy

---

### Post by SiHa on 2009-11-18
+1 to Chipppy's suggestion.

I have my OS on an old 40GB drive (which I will transfer to the 250GB drive that has my 'Emergency' 8.04 install on, now that 9.10seems stable), and a 500GB drive mounted at /var/lib/mythtv

---

### Post by elgordo123 on 2009-11-18
I have one 500Gig Drive.  I put a nice 40Gig partition for "/"  (OS) and then created a second one of the rest of the drive (except for swap of course - about 2Gig) is my var "/var".
 That way I have my OS only on first partition and the rest is the mysql database, recordings, music, tv, videos, etc.

---

### Post by bcg30506 on 2009-11-18
Thanks to all for the replies and GREAT ideas!  I do like the idea of having the OS and home directories in separate partitions/drives as well as the mythtv data.  Is there any reason why everyone seems to separate TV recordings from the other items like videos and pictures?  Just curious what the thoughts are on this.

Okay, so it seems LVM is not the way to go.  Since my system is already setup to use it and it was a prepackaged box that I did not originally setup but now maintain on my own, how in the world do I "undo" the LVM mount and make it be a normal partition?  Should I leave it as xfs or is ext3 preferred?

---

### Post by novellahub on 2009-11-18
All of my machines are partitioned the following way:

Disk 1:  /    (10 GB)
         swap (2 GB) 
         /myth2 (Left over space)
Disk 2:  /myth


All of my recordings / videos are on the /myth partitions under various folders that are owned by the mythtv user and group. Also make sure the folders are writable as well (All of mine I set to 775).  You can see my signature for more details.

---

### Post by chipppy on 2009-11-19
Good Evening

In answer to why seperate the Tv recording and all the other stuff.

TV recording as add to hard disk, watch, and then delete from hard disk.
This is a lot of work on the hard disk and therefore an increased risk of damage due to the amount writes.  really if the hard drive fails and you losse s the OS and all those Tv recording do you care.  Not really, just rebuild the OS from the back up and catch up via next weeks eposide.

The videos, music, pictures, personal video on the other hand are more constant and also 99% reads.  Less risk of damage to hard disk, but far more press-ious.  Reduced risk of data loss.  
Yes mine is backed up but you tell my wife that all the home movies of the babies will be back there in a couple of days when she realises that the hard drive has failed 'again'.

Anyway hope that help you.

Cheers
chipppy

---

### Post by bcg30506 on 2009-11-19
> **chipppy said:**
> Good Evening

In answer to why seperate the Tv recording and all the other stuff.

TV recording as add to hard disk, watch, and then delete from hard disk.
This is a lot of work on the hard disk and therefore an increased risk of damage due to the amount writes.  really if the hard drive fails and you losse s the OS and all those Tv recording do you care.  Not really, just rebuild the OS from the back up and catch up via next weeks eposide.

The videos, music, pictures, personal video on the other hand are more constant and also 99% reads.  Less risk of damage to hard disk, but far more press-ious.  Reduced risk of data loss.  
Yes mine is backed up but you tell my wife that all the home movies of the babies will be back there in a couple of days when she realises that the hard drive has failed 'again'.

Anyway hope that help you.

Cheers
chipppy

This is a great explanation!  Thanks a bunch.  I had never thought of the "stress" placed on a HD with the constant R/W of TV and the risk that involves.  That would be a good reason to isolate it from other stuff.

As far as backups go, I do also backup our TV recordings so we don't lose them before watching, especially specials that we can't get back or see reruns/Hulu.  But even with backing everything up, I like the idea of separating TV recordings from videos, pictures, and music.

Now I just need to know how to get rid of the LVM setup to use "normal" partitions.  Also, xfs or ext3?

---

### Post by ian dobson on 2009-11-19
Hi,

Stick with ext3, xfs is OK but if you have a crash and the filesystem isn't clean you can have really bad corruption that is really hard to fix. ext3 may not be really quick but it's a well supported maintained code base.

I've had really bad problems with xfs, my backend server crashed and the ext3 partition with 1tb videos was OK, my test partition with about 200gb videos and "large" data files (20-30gb in size)was totally corrupt and no data could be recovered.

Regards
Ian Dobson

---

### Post by bcg30506 on 2009-11-19
> **ian dobson said:**
> Hi,

Stick with ext3, xfs is OK but if you have a crash and the filesystem isn't clean you can have really bad corruption that is really hard to fix. ext3 may not be really quick but it's a well supported maintained code base.

I've had really bad problems with xfs, my backend server crashed and the ext3 partition with 1tb videos was OK, my test partition with about 200gb videos and "large" data files (20-30gb in size)was totally corrupt and no data could be recovered.

Regards
Ian Dobson

Good to know.  Thanks for the tip!

---

### Post by nickrout on 2009-11-19
> **ian dobson said:**
> Hi,

Stick with ext3, xfs is OK but if you have a crash and the filesystem isn't clean you can have really bad corruption that is really hard to fix. ext3 may not be really quick but it's a well supported maintained code base.

I've had really bad problems with xfs, my backend server crashed and the ext3 partition with 1tb videos was OK, my test partition with about 200gb videos and "large" data files (20-30gb in size)was totally corrupt and no data could be recovered.

Regards
Ian Dobson

OTOH many people prefer xfs for its speed at deleting files (among other things) and have no problems at all with it. It seems the most often recommended filesystem for your recordings.

---

### Post by blackoper on 2009-11-19
split the difference and use ext4. It's better in every category than ext3 and it's stable now. If I had it to do over again, I'd be using ext4 for my raid arrays.

---

### Post by ian dobson on 2009-11-20
> **blackoper said:**
> split the difference and use ext4. It's better in every category than ext3 and it's stable now. If I had it to do over again, I'd be using ext4 for my raid arrays.

Naaaa, ext4 is still abit too new. Let the code ripen abit before trusting your data to it.

Regards
Ian Dobson

---


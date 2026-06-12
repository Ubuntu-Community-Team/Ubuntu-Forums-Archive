---
title: "DVD regions"
date: 2010-03-10
forum: Multimedia Software
---

### Post by RasterBurn on 2010-03-10
hello all, a topic just recently popped up here at home and well, i am in search for the answer on here, we have movies of both region 1 and region 2, the other night my wife was watching some movies on her computer and of course, switching back and forth from region 1 dvds to region 2 dvds, what we are wondering, is Ubuntu 9.10 automatically running the regionset command when she changes the disk or did Ubuntu 9.10 automatically set things to region free?

i understand that dvd drives allow you to change their region code 5 times before the code is locked into the drive permanently... in windows when you put a movie in that isnt of the code that is set it will ask you if you want to change the code to watch the movie, but in Ubuntu there wasnt the dialog asking that, so we were just wondering for some information on this (hate to keep switching disks back and forth between the 2 regions only to have the drive lock itself on region 2) we live in region 1 for dvd codes

---

### Post by ron999 on 2010-03-10
Hi
I'm pretty sure that Ubuntu isn't running the regionset command covertly.
Look in the repository for the program 'regionset' and install it.
Then when you run regionset from the command line it will tell you how many lives you have remaining and will ask you if you really do want to change the region.

---

### Post by mc4man on 2010-03-10
> my wife was watching some movies on her computer and of course, switching back and forth from region 1 dvds to region 2 dvds, 

Opensource, unlicensed players don't enforce region coding so for the most part you are able to watch dvd's from any region.

The only exceptions would be some extras may not be able to be decoded properly when there is a region mismatch though that's rare (when there is a region mismatch libdvdcss2 uses a different decrypting method than can fail on small samples

The other exception is laptop dvd drives made bu Matshita (panasonic). Most of them enforce region coding and will not allow access to encypted sectors when there is a region mismatch

Drive manufacturers are not required to do this - panasonic has done so because,... well I don't know - the same says it all
matSHITa

---

### Post by RasterBurn on 2010-03-10
well, at the moment i am still not fully understanding the whole region system, her computer has a BenQ dvd rewriter (only important part is the name), i believe she is using MPlayer with libcss (i dont remember what version it is) with Ubuntu 9.10 does this mean that the system is running region free?

---

### Post by pickarooney on 2010-03-10
I can't seem to play DVDs from *any* region.

---

### Post by RasterBurn on 2010-03-10
playing DVD movies pops up in the forums regularly by users asking how to enable the support (more or less new users who fail to search out the answers) anyways, this site will tell you how to play most of the store bought disks:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("http://https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

both my wifes computer and my computer (though hers is 32bit and mine is 64bit) have had that page loaded in the browser to enable libdvdcss you will also need to get the gstreamer plugins to play the video formats (if you dont already have them)

---

### Post by wojox on 2010-03-10
> **RasterBurn said:**
> well, at the moment i am still not fully understanding the whole region system, her computer has a BenQ dvd rewriter (only important part is the name), i believe she is using MPlayer with libcss (i dont remember what version it is) with Ubuntu 9.10 does this mean that the system is running region free?

Have you looked into [regionset]("http://linvdr.org/projects/regionset/") ? It's in the repo's.

---

### Post by mc4man on 2010-03-10
> well, at the moment i am still not fully understanding the whole region system, ............... does this mean that the system is running region free?

In essence yes , or 'all-regions", just a matter of words.

If the player and the drive don't enforce  a region match between the drive and disk then you can play disks from any region, the only thing affected is libdvdcss2

When there is a region match - region 1 disk in region 1 drive it uses one method to crack the keys.
If there is a mismatch, region 2 disk in a region 1 drive (or drive with no region set), then it uses another method

Generally speaking the former is slightly more effective than the latter in successfully cracking keys.


( the former means the default disk key method, the latter is the title key method

---

### Post by RasterBurn on 2010-03-10
ok i think i get what you are saying, as for the regionset prog. in the repos, if its not set or enforced on the computer why set it? i dont really want the drive to become locked to a different region from the standard in my area and end up possibly having to buy a new drive for the computer to properly run the standard region code disks (god knows decryption software seems to be slightly unreliable these days)

---

### Post by ron999 on 2010-03-10
> **RasterBurn said:**
> ok i think i get what you are saying, as for the regionset prog. in the repos, if its not set or enforced on the computer why set it? i dont really want the drive to become locked to a different region from the standard in my area .....

You have the option y/n
Just choose **n**

---


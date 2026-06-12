---
title: "formatting  large drives"
date: 2010-10-03
forum: Mythbuntu
---

### Post by benlyboy on 2010-10-03
hi all 


I was looking at fitting a 2tb drive to my system, as I intend to turn it in a backend and build a new frontend.

I was reading through the feed back for the drive that i am thinking of using, and I came across one post that said this "Not suitable for versions of Linux that force disc format to start at Sector 63."

Would this be the case with ubuntu...?

---

### Post by ian dobson on 2010-10-03
Hi,

Just partition the drive using fdisk with the -u option and start the partitions at a sector number divisable by 8 (64).

The drive you're looking at uses 4Kb sectors and uptil now all harddisks have used 512byte sectors. Linux uses 4Kb blocks for file systems by default and if the 4Kb blocks aren't aligned to the 4Kb sectors on the drive a write would involve reading and writing 2 sectors rather than just writing one.

I have 2x 2Tb wd drives in my mythtv backend and don't have any problems with them.

Regards
Ian Dobson

---

### Post by benlyboy on 2010-10-03
Thanks again Ian

Will go ahead and order one then.

You have two of them in your back end wow. I thought I had gone nuts when I fitted 500gb a couple of years back and now it's not enough. It seems like it was only a few years ago that I got my first gb drive and paid a kings ransom for it I might add. At the time I thought I would never fill it. now we are into tb whats next...:)

---

### Post by ian dobson on 2010-10-03
> **benlyboy said:**
> Thanks again Ian

Will go ahead and order one then.

You have two of them in your back end wow. I thought I had gone nuts when I fitted 500gb a couple of years back and now it's not enough. It seems like it was only a few years ago that I got my first gb drive and paid a kings ransom for it I might add. At the time I thought I would never fill it. now we are into tb whats next...:)

Well I actually have 6 2Tb wd drives in my backend. 4 in a RAID5 array for my data and the 2 4K sector drives in a RAID0 which are part of my backup system.

Regards
Ian Dobson

---

### Post by LowSky on 2010-10-04
I'm running a 2TB drive as well and is seems to be fine. I used Gparted to formate it, Not one problem.

---


---
title: "any benefit to ssd on a backend with sata storage ?"
date: 2012-12-20
forum: Mythbuntu
---

### Post by jeremycobert on 2012-12-20
I am going to get new WD red 3TB sata hard drive and I have an unused 80GB SSD sata drive. would there be any benefit to using the SSD as my backends drive 0 and store all the Myhbuntu files on it and just use the SATA drive for storing the shows. will there be any benefit to it or will any added ssd performace just bottle neck with the regular SATA drive.

currently i use a 320gb as my OS and a 1TB for storage.

opinions welcome !

---

### Post by AlecJ on 2012-12-20
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

sounds like its' good for a swap drive, but maybe overkill for Myth?

My OS is on an old 250Gb ISA ribbon type disk, but has 4Tb's of Sata drives for storage.
I'm normally waiting for the TV cards to lock up not the OS, the system has no trouble with a backend/frontend and a remote frontend plus all the shared drives.

I don't like sata drives, I have lost a few, they over heat and have head read errors and die.
I have them mounted with a fan on each and some water cooled mounting brackets. the newer drives run cooler, but I think the testing was done in the field at our expense.
So I guess SSD is the next step, as ever its the lost data not the hardware

---

### Post by diesel48 on 2012-12-21
I just did this. I am changing out my masterbackend from a mythdora installation to a mythbuntu install. I have a 64gig SSD and  3TB sata drive. I put the swap, root and boot on the ssd. It is so much faster. I think the frontend launched in about 15-20 seconds. Guide listings are much faster as well.

---

### Post by nickrout on 2012-12-22
There is a very real benefit to using the ssd for / and the sata drive for media storage. Do it.

---

### Post by chadk5utc on 2012-12-22
I agree you cant beat the performance. I love mine!

---

### Post by PhilWig on 2012-12-31
Sorry to spoil the party but I was skeptical even before I read this:

[http://www.mythtv.org/pipermail/mythtv-users/2012-June/335174.html](http://www.mythtv.org/pipermail/mythtv-users/2012-June/335174.html)

Time from boot to 'ready' state would undoubtedly be much faster, but in steady state plain SATA is fine.  I run two SATA drives - one for root plus swap plus backup, the other for media (/var/lib/mythtv).  They are limited to SATA2 by the mobo.

When making six simultaneous SD recordings and one playback the disk traffic is pretty evenly spread with each disk doing about 5 or 6 transfers/sec.  That's way within SATA drive capabilities with seeks of under 10mSec and a raw capability of several tens of transfer/sec.  Swap traffic is nil with 2Gb of ram - if you do start swapping then more RAM is more effective than putting swap on SSD.

In my case, having two drives is thus more about resilience than performance.  My concerns with SSD are those of wear and degraded write performance due to need for trimming.  Unless new drives overcome this (or the problem is overstated) then I'd have thought that neither swap nor database would be suitable for SSD.

Having said that, I don't have SSD so I watch this debate with interest!

Phil

---

### Post by topcat5 on 2013-01-01
I'm using a 64G SSD for my OS. I did not want my OS on a data drive and 64G SSDs have gotten cheap.  They don't make any noise and generate almost no, if any, heat.  Plus they are very fast as I can boot this system to desktop in less than 15 seconds.  Admittedly the fast boot time won't be that important in an always running system, but since I'm also using the server as a front end for one of my TVs, the heat and noise reduction are priorities.  

Make sure you modify /etc/fstab with parameters optimized for SSD drives.  The wiki has some notes on this.  

My recommendation, if you take this approach, is to mount /var/log on it's own partition on a mechanical drive.  Use a file system that's good for small files.   I also created another partition on a mechanical drive for the mysql DB.   Don't place either in the same partition as your data drives.  It should be optimized for very large files.

---


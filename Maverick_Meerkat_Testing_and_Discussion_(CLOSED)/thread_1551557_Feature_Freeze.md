---
title: "Feature Freeze"
date: 2010-08-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-08-12
As [announced]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2010-August/000745.html") by Robbie Williamson today,  [Feature Freeze]("https://wiki.ubuntu.com/FeatureFreeze") is now in effect for Maverick.

---

### Post by andrewabc on 2010-08-12
I really hope someone updates gparted. It is important to use for partitioning.

Current version in 10.10 is old. Debian had newer version since June 30.

This gparted is needed in order to work with larger sector sizes (>512byte).
Otherwise when people partition 2048byte sector size HDD, they need to use command line and a bunch of complicated stuff.

I'm not sure if *Disk Utility* can do partitioning and stuff to replace gparted usefulness (GUI partitioning).

---

### Post by krazyd on 2010-08-13
have you filed a bug?

---

### Post by andrewabc on 2010-08-13
Just did.
[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617359](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617359)

---

### Post by dino99 on 2010-08-15
vote +1

---

### Post by ricsi-pontaz on 2010-08-16
+1

---

### Post by Col-1023 on 2010-08-16
+1.

---

### Post by andrewabc on 2010-08-16
No need to spam +1.
Make sure in the bug report to click the thing to say it affects you.

Writing sentences here about how important a new version of gparted is would look better than +1 as well.

No support for 2048 byte devices in gparted would be a pretty bad thing to not ship with.

I have no idea if default installer can detect 2048 byte devices and align properly.
But if you are like me, sometimes it is easier to use gparted (which is installed by default on liveusb/livecd) to make partitions. Shipping with an out of date version will only anger lots of people and make them fill up support forums with questions about 2048 byte support.

I still have no idea if ubuntu by default supports properly aligning SSD. Yes the kernel supports TRIM, but if not aligned properly there is severe performance degradation. Same thing for 2048 byte HDD that are not aligned properly.

---

### Post by cariboo on 2010-08-16
I not that sure alignment is all that important, I've got a WD 1TB green drive (WD10EARS), during testing, starting the partiton at sector 63 and creating a 1Gb file gave an approximate write speed of 96MB/sec. Starting at sector 64 gave me an aproximate write speed of 98MB/sec, for a gain of only 2MB/sec. 

If there was a huge gain in write speeds, I could see it, but for such a small gain I don't know if it was really worth it.

Using fdisk you can set the sector start using -u option eg:

```
sudo fdisk -u /dev/sda
```

There is a thread in the Cafe with all the details, that I can't seem to find at the moment, too many posts. :(

---

### Post by Longinus00 on 2010-08-16
> I not that sure alignment is all that important, I've got a WD 1TB green drive (WD10EARS), during testing, starting the partiton at sector 63 and creating a 1Gb file gave an approximate write speed of 96MB/sec. Starting at sector 64 gave me an aproximate write speed of 98MB/sec, for a gain of only 2MB/sec.

If there was a huge gain in write speeds, I could see it, but for such a small gain I don't know if it was really worth it.


The write penalty for unaligned partitions depends highly on what type of workload you're putting on the drives. Doing big sequential write tests doesn't show the whole picture. Large writes will be hitting sequential sectors anyway so there is very little overhead from unaligned partitions. [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

---

### Post by andrewabc on 2010-08-16
yes, unaligned does not affect sequential as much.

But if you were say writing say 2 mb non sequential of small files all over the hard drive (or even in one area, say 1gb area), with small files you could end up writing nearly twice as much as needed, which is really bad.

[Western Digital&#8217;s Advanced Format: The 4K Sector Transition Begins](http://www.anandtech.com/show/2888)

I don't think people want to have to use fdisk to properly align their disks. I had to use it for my 1tb western digital EARS and I spent several hours doing research and figuring out how to make sure properly aligned. GUI apps should do this by default.

[4K-sector drives and Linux](http://lwn.net/Articles/377895/).

[Corsair Force F120 SSD Review](http://www.storagereview.com/corsair_force_f120_ssd_review)
Has benchmarks showing 4k aligned vs non aligned. Aligned is much better. Especially for SSD where it has limited writes, so you don't want to be writing more for no reason.

Alignment also allows for more I/O (along with increased mb/s).

To summarize, as far as I know there is no downside to having proper alignment. Improper alignment has many downsides (varies by device and what type of benchmark done). So I think lots should be done to make sure everything is always properly aligned by having up to date software to support it. Using terminal to properly align is not a solution, as no one wants to learn to do it and do calculations to figure out proper alignment. GUI tools must also work with proper alignment.

---

### Post by cariboo on 2010-08-16
I ripped my dvd collection using vobcopy, the smallest file on that drive is just over 1.6Gb, so many small files aren't a concern.

I was more concerned with slow transfer speeds, as there were reports of transfer rates as low as 14Mb/sec on the WD forums, even the first time I partitioned the drive starting at sector 63, transfer rates of large files was never less than 90MB/sec, like I said starting at sector 64 boosted the transfer rate by only 2MB/sec, which is really beside the point, as the sector of my network that computer is on only runs at 100Mb/sec, the best transfer rate I've on the network was about 11MB/sec.

I agree there should be a gui tool for those that have a hard time with the command line, especially as ssd's are getting more prevalent.

---


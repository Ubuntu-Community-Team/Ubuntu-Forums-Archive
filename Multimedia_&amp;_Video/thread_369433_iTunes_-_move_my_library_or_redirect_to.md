---
title: "iTunes - move my library or redirect to?"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by zami on 2007-02-24
My husband wants to give Ubuntu a try (he's been watching me enjoy it for a year now) but we've got one big road-block.  An enormous iTunes collection in WindowsXP.  About 25 gigs of music.

So, I have a few questions!

1 - Is there any easy way to MOVE these files?  Re-ripping them all really just isn't an option.  

2 - Even better, is it possible to have his new linux player read files from his old Windows iTunes directory?  This seems logical to me, but I'd have no idea how to do it.  Obviously that would involve a Windows partition left behind (no problem) but it's in NTFS format (potential problem?  Is it possible to convert a Windows partition from NTFS to FAT32 without destroying the information?  Have I even got that right, that linux can read FAT32 but not NTFS?  Uhg...)

Any advice or pointers to howtos, etc, would be VERY appreciated!

Thanks
-zami

---

### Post by christhemonkey on 2007-02-24
Linux can read/write FAT32 but by default can only read ntfs (you can enable write support easily but its not by default atm).

However music downloaded with itunes (from the itunes shop) is covered with DRM (digital rights management) so you probably will be unable to play it on linux.


Basically DRM means you dont actually own the music, theyr just letting you listen to it on their player (and that license can be revoked at any time).
See here:
[http://en.wikipedia.org/wiki/Digital_Rights_Management](http://en.wikipedia.org/wiki/Digital_Rights_Management)
and here:
[http://www.gnu.org/philosophy/right-to-read.html](http://www.gnu.org/philosophy/right-to-read.html)
and maybe here:
[http://en.wikipedia.org/wiki/QTFairUse](http://en.wikipedia.org/wiki/QTFairUse)

---

### Post by pete on 2007-02-24
Zami, it is possible to convert NTFS to FAT32 (using a utility like Partition Magic).  PM can do it without destroying data.  

However, messing around with partitions can be a risky business, so I'd probably go with something more like:

1. Install Ubuntu, leaving existing NTFS partition intact.
2. Copy files from NTFS partition to Ubuntu/EXT3 partition.
3. Wipe out NTFS partition.

If there's not enough room on the drive for copying 25GB worth of files, you could always stick a second drive in the box.

---

### Post by zami on 2007-02-24
Excellent.  Thank you both for your responses!

I'm glad I had a general misunderstanding about how Linux handles FAT32 and NTFS.

If Linux can read either format then I am wholly unconcerned with converting.  (And thank goodness, because that sounds like a whole potential mess I was NOT looking forward to getting into.)

I'm going to try for setting up a dual-boot, leaving the existing Windows in place, and pointing Banshee/Listen/Whatever to the existing iTunes directory within Windows.  If it can just read the files I'm hoping that will be enough - I'm banking that I can have it save any playlist or program specific files somewhere within the linux partition.

Failing that I'll just move the files.  

So, SO relieved Linux can read NTFS!!

Thankfully only a very small portion of the 'library' is DRM'd.  Mabye I can even wrestle iTunes into submission under Wine - but that is a battle for another day.

Thanks again for the help!

-zami

---


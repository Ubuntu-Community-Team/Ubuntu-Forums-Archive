---
title: "Help with partitioning - stuck"
date: 2008-02-24
forum: Mythbuntu
---

### Post by kyfehr on 2008-02-24
I am really needing some help. I have a fully working system based off of 7.10 (not weekly builds). 

My current setup is a 500 GB hard drive with only one partition. I also have an external 500 GB hard drive that I have placed all of my ripped videos on to. The problem is that the external hard drive does not mount properly and as such the videos are not shareable to the remote frontend.

Here is my question and where I need the help.

I purchased a 80 GB and a 500 GB hard drive. In total that would be 2 500 GB internals a 80GB internal and a 500GB external (which I want to use for backup).

I want to use the 80GB for the Root and Swap and the 2 500GB for the storage. I am not sure if going to LVM is worth it because .21 is going to be coming out soon enough. But I want it to be setup in a way that one of the 500 GB's is for recordings and the other for Videos

The extra space on the 80GB would be for music and what not.. 

So I am assuming that I would have to do like 3 partitions on the 80GB.

But have not been able to figure out a good setup despite reading the multitude of posting in the forum.. I am not sure how to mount the 500 GB to the folders..

Any help would be great.. and very much appreciated.

Thanks

---

### Post by volkswagner on 2008-02-24
> I want to use the 80GB for the Root and Swap and the 2 500GB for the storage. I am not sure if going to LVM is worth it because .21 is going to be coming out soon enough. But I want it to be setup in a way that one of the 500 GB's is for recordings and the other for Videos

I would set up as follows

80gig 10-20gig ext3 mounted as /, 1-10gig ext3 mounted as /home, 1-2gig mounted as swap, remainder ext3 mounted as /var/lib/mythtv/music

500gig xfs mounted as /var/lib/mythtv/videos

500gig xfs mounted as /var/lib/mythtv/recordings

You will have to chmod when done to set permissions as they will be set to root when install is complete.

You can also create another partition mounted as /var/lib/mythtv/pictures
If you don't your pictures will be included on the 80gig file system part of the / partition you set up.

---

### Post by kyfehr on 2008-02-24
Thanks for that input.. 

I am still a little stuck on understanding the whole mounting a drive as a folder thing.. I have tried to edit the fstab before, but I have been unable to do it succesfully...

---

### Post by ubnewbie2 on 2008-02-24
> **kyfehr said:**
> Thanks for that input.. 

I am still a little stuck on understanding the whole mounting a drive as a folder thing.. I have tried to edit the fstab before, but I have been unable to do it succesfully...

All drives mount somewhere under root (/).  You can manually mount a drive from the command line.  Look up the mount command ```
man mount
```, will give you details.  You'll need to sudo to root user to use the mount command.  To unmount it, use umount (the 'n' is intentionally left out)

Pick a directory/folder as your mount point.  The drive REPLACES anything already there, so don't pick a directory that already has files and subdirectories in it, or else they'll become inaccessible.

If you want it to be mounted at boot time, you add an entry to fstab. Use ```
man fstab
``` to get some info on the format.

---


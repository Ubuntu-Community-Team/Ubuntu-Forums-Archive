---
title: "Repartitioning Mythbuntu W/Gparted-live for LVM"
date: 2007-10-24
forum: Mythbuntu
---

### Post by Panhead Bill on 2007-10-24
Before I try this and possibly trash my running mythbox, I'd like any alternatives.

My mythbox has the Mythbuntu rc with all the latest updates. It works!
(Kudos to the development team)

The problem is that the install doesn't have LVM so I can add my (4) 120 gig drives to the unused space (about 65 gigs) of my system drive.

If I understand the How-to correctly, I'm basically hosed since I should have partitioned my drive with Gparted prior to loading mythbuntu.

I also read that I "Might" be able to repartition the drive with gparted and might not corrupt the install.

So unless someone has a better idea, I'll try the repartitioning. If this works then I can use LVM to add the other drives.  If not at least I can have a good idea of the sizes I need when I start from scratch.

---

### Post by apauna on 2007-10-24
Did you see my post on lvm? :)

[http://ubuntuforums.org/showthread.php?t=584473](http://ubuntuforums.org/showthread.php?t=584473)

---

### Post by superm1 on 2007-10-24
Yeah even if you have existing recordings, you can always setup LVM on all the other drives, copy the recordings over and then set it up on the drive they were already on and 'extend' it over.

---

### Post by Panhead Bill on 2007-10-24
apauna:  I've been following yout how-to.  I hang at pvcreate; I get an error for the newly added partition,  /dev/hdb3, and also when I tried it on the first of my 120 gig drives, hde. 

superm1:  I erased all recordings and then repartitioned the free space on hdb (an 80 gig drive).  About 4.7gig was used for the install (frontend/master backend), so I left the boot partition at double that (10Gig)  I ended up with about 64 gig in the new partition.  As soon as I figure out why I can't pvcreate either the new partition or the other drives I should have it working.  It seems that I had this problem when I first did a LVM, and if I can find my notes maybe I can figure out how I fixed it last time.

---

### Post by apauna on 2007-10-25
> **Panhead Bill said:**
> apauna:  I've been following yout how-to.  I hang at pvcreate; I get an error for the newly added partition,  /dev/hdb5, and also when I tried it on the first of my 120 gig drives, hde. 

superm1:  I erased all recordings and then repartitioned the free space on hdb (an 80 gig drive).  About 4.7gig was used for the install (frontend/master backend), so I left the boot partition at double that (10Gig)  I ended up with about 64 gig in the new partition.  As soon as I figure out why I can't pvcreate either the new partition or the other drives I should have it working.  It seems that I had this problem when I first did a LVM, and if I can find my notes maybe I can figure out how I fixed it last time.

I seem to remember something about only having 4 primary partitions on a drive. I will have to check into this more.

Can you start with a drive that does not have 5 partitions? 
Are all of these primary?

Can you give a quick synopsis of drive and partition layout for your pc?

---

### Post by Panhead Bill on 2007-10-25
ARRGH!  (After composing a LONG response to this the board made me re-logon and ate my post)


I tried on two drives; hdb with 4 partitions and hde with onea single unused partition.
hdb1 boot 9.77gig primary
hdb2 3.08gig extended 
  hdb5 swap 3.08 gig (nested within hdb2 for some reason)
hdb3 lvm 61.68gig primary  (the new partition)

hde unassigned 111.4gig  (maybe I have to use gparted to partition it as lvm?)

Anyway today hdb3 did work with pvcreate vgcreate and vgdisplay, but not lvcreate - it errors that 'Volume group "vg" doesn't exist'  When I try vgcreate a second time it errors that 'A volume group called 'videolvm' already exists.'

onward . . .

---

### Post by dannyboy79 on 2007-10-25
doesn't mythbuntu have the storage groups built into it yet? no need for lvm if so.

---

### Post by apauna on 2007-10-25
> **dannyboy79 said:**
> doesn't mythbuntu have the storage groups built into it yet? no need for lvm if so.
Can you elaborate on this some more?

I enjoy learning about possible better ways to do things. So far LVM has been the best to span partitions. :)

---

### Post by superm1 on 2007-10-25
> **dannyboy79 said:**
> doesn't mythbuntu have the storage groups built into it yet? no need for lvm if so.
Storage groups are only in 0.21 (trunk).  Mythbuntu ships with 0.20.2.

---

### Post by apauna on 2007-10-26
May wish to attempt a disk wipe on partitions that you want in LVM. 
**Note: Be carefully here this will destroy all data on partition!!! If not done correctly could wipe entire drive and make unbootable!**

```
dd if=/dev/zero of=/dev/sdb1 bs=4k conv=notrunc,noerror
```

I have not tried it this way but just did entire drive sdc on my PC with it to see if it would work and it did.

---

### Post by Panhead Bill on 2007-11-11
I finally manually partitioned the drive during a re-install.  The partitions were then in numerical order and the nesting of swap was eliminated.  Then with only a few small problems, I was able to use the guide and set up a lvm with the 62 gig partition of the first drive and the four 120 gig drives.

---


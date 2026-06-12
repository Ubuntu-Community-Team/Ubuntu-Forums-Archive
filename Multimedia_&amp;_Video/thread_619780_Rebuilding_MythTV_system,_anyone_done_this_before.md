---
title: "Rebuilding MythTV system, anyone done this before?"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by josesanders on 2007-11-21
I've had a fully functional MythTV system running on a 1GHz machine with a 250 GB hard drive for a year now, and I've decided it's time to upgrade.  I bought a 3 GHz motherboard and processor, and a second 250 GB hard drive.  I don't want to lose all of the recordings on the old hard drive, but as I understand it, the only way for MythTV to use the two hard drives together is with LVM, which requires a full reformat, correct?  What is the best way to build the new system, and still preserve the recordings?

The only way that I have thought of to do this is to build the new system with a small hard drive for the OS, and then add the new 250 GB drive as an LVM drive.  Then I can copy the old recordings onto the new LVM drive, and then reformat the old drive and add it to the LVM partition.  Would this work?  Is there a better way?  Has anyone ever tried to do something like this before?

I wish MythTV version 0.21 were going to be out sometime soon.  As I understand it, with that version you will be able to record on multiple drives, which eliminates the need for LVM.

---

### Post by rmemm on 2007-11-22
I'm actually just building a MythTV box -- so I'm no expert on Myth -- but I think your question is more of a Linux upgrade question than a myth question.

Personally I'd buy a single SATA drive that was large enough for everything -- just to reduce the power consumption and the complexity of the system and to improve reliability.  You can get a good 750 GB drive for $250 these days -- and a cheap one for $200.

You can however do the LVM thing you want to do.  I would not get another drive for the OS myself -- unless you have some Myth reason to do this -- such as performance.  Instead I'd create an 8GB OS partician (to install ubuntu on and be the root partitian), what ever swap partitians you want, then I'd create an LVM partician out of the rest.  You can create the LVM partitian as a single large block, or as multiple sub-partitians.  Only reason to do the latter is it makes it easier to reallocate space later -- but otherwise does not matter.  

Anyway -- once you have lvm setup -- allocate and format a logical volume and copy the data from your old drive to it.  When your satisfied it works -- then reformat the old drive as an LVM volume -- again either as one or a few large blocks -- or as up to 16 smaller partitians if you want flexibility to remove them from lvm later.

Does that make any sense.

Rob

---


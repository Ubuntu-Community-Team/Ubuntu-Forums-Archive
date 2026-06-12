---
title: "Replace secondary hard drive"
date: 2016-04-25
forum: Mythbuntu
---

### Post by jonathan.k3 on 2016-04-25
I have three drives (A,B,C) in my Mythbuntu backend system. Unfortunately I can only connect three drives with this system's motherboard. I want to upgrade the secondary drive (B), in other words not the main drive (A) that Mythbuntu boots from. Is it as simple as physically replacing the old secondary drive (B) with the new one (B') and then going into mythbuntu and editing fstab as described here ([https://help.ubuntu.com/community/InstallingANewHardDrive)?](https://help.ubuntu.com/community/InstallingANewHardDrive)?) What happens to the recordings that were on B? Do I edit fstab to delete the removed hard disk (B)? I don't necessarily care about keeping those recordings but I do want to avoid the hassle of nuking everything and doing a fresh install.

---

### Post by TheFu on 2016-04-26
I don't know anything about mythbuntu, but bits-are-bits.  I would

0) make a backup of any data you can't lose. This could be settings, recordings, other media, everything you aren't willing to type back in.
a) get a new HDD that has the same sector sizes as the older drive - doesn't need to be the same total size.
b) get a live-Boot device ready with some version of Linux. Ubuntu is fine, but almost any of the really tiny versions are fine too.
c) open the case and unplug the disks you DO NOT WANT TO TOUCH (those you want to leave alone)
d) connect the new HDD somehow to the machine - that can be through the SATA, IDE, eSATA, USB ... doesn't really matter.
e) Boot using the live-CD/Boot version of Linux; if you don't login as root, become root with **sudo -s** in a terminal
f) install ddrescue into the "live" environment - **apt-get install ddrescue**
g) determine which of the 2 connected HDDs is the source and target disks.  I'd use **parted -l** to see the partitions and expect that would be clear to me.
h) Use ddrescue to mirror, bit-for-bit, everything on the physical SOURCE disk to the physical TARGET disk.  That would include the partition table.  Something like   **ddrescue /dev/sdY /dev/sdZ  /tmp/logfile** - that command will run for a long time, since it starts at the beginning of the SOURCE and copies every bit to the TARGET.  sdY=source  sdZ=target.  **If you mix these up, you will be wiping all the data you want to keep.** There is no protection if you get this wrong.  I'd leave it overnight. Shutdown the system when it finishes. 
i) unplug the old-disk-to-be-replaced. Connect the newly copied disk to that same SATA cable (probably want to put it into the same HDD slot inside the case first).
j) connect the other 2 disks back up.
k) Boot in the normal way. Since you did a bit-for-bit copy, the UUID should be the same.

If everything is working ... then you can do whatever is needed to stretch the partitions into the newly available extra space.  **gparted** is how I would do that.  Changing the size of a partition may change the UUID, so be prepared to edit the /etc/fstab if that happens. Lots of guide for that. **blkid** is the command to see the UUID-to-device mapping.  

There might be a better way to do this from inside the MythTV software. I dunno. Never seen it.  I say, why lose any recordings just because a drive swap is happening?

Of course, if the new HDD is huge and the old one wasn't, then you may need to swap MBR partitioning for GPT partitioning. That means you shouldn't use the ddrescue method at the whole-drive level and that you will have to change the UUID inside the fstab.  GPT is good, preferred for a number of reasons.

Also ... I think gparted has a way to copy entire partitions from 1 disk to another - do this from the live-boot device (CD/DVD/Flash drive), just like described above. gparted can make gpt disk formats too - this **must** be the first thing done on any disk, before any partitioning or data is copied over.

If you want more detailed help, post the output from **sudo parted -l** and please use **code tags**.

---

### Post by aelfric55 on 2016-04-26
You're not adding a drive, as per the document you referenced. You're only replacing a drive. So while the new drive B' will have to be physically installed, partitioned, and formatted, the fstab will not need to be altered unless the filesystem on B' is different than what was/is on B. Also, when you have partitioned, formatted, and mounted the new drive B' at old drive B's mount point for the first time, that new drive B' will still have its owner:group set as root:root, which is likely not what current drive B has. So the owner:group will need changing from root:root so that mythtv can access the new drive as it did the old drive.

Mythbackend can access the recordings equally well from any drive in the storage group. So if C is part of the storage group and you have enough space, move the recordings currently on B to there, temporarily or permanently. Otherwise, buy a cheap USB aluminum external drive shell for ca. $30, stick old drive B in there, mount this new external USB drive B somewhere and then move all your recordings files from external drive B to the new empty internal drive B' 

As an aside, at times I've also used USB external drives as permanent drives on backends where I had run out of MB SATA ports, but I found that for recording they seemed to work best if they were USB 3,  particularly for HD  to avoid recording flaws from slow disc writes. The permanent USB external backend drives were ideal if I moved already-recorded material from the internal drives to them to mostly fill them up, and then used the external drives only for playback while the internal drives did most of the actual recording.

---


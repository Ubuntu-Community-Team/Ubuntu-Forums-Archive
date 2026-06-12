---
title: "mounting hdd / editing fstab"
date: 2010-08-09
forum: Mythbuntu
---

### Post by bance on 2010-08-09
Hi guys, 

I'm building a mythbuntu system for my new house, and it's gradually coming together.

I have a be/fe machine that I want to add more storage to, I've read here and elsewhere that it's a good idea to,
mount the drive specifically so as to allow a clean install (if required) and thereby keeping recordings/configuration files intact.

So the questions are :-

1. Which folder should I mount these disks to ?

2. When editing fstab which options do I need to add ?

/mythtv seems to be the preferred option for the folder but I seem to have more than one (/etc/mythtv, /var/lib/mythtv....)

As far as editing fstab, so far I've managed to come up with:-

[label]    [mountpoint]    [type]    [options]     [dump]  [fsck]

charnock1    /mythtv           xfs      auto           0        0


charnock2    /mythtv           xfs      auto           0        0

I think I might have to add more options (re permissions etc)

anyone able to clarify things a little more?

thanks to all for getting me this far:D

---

### Post by klc5555 on 2010-08-09
Mythbuntu's initial default placement for recordings is /var/lib/mythtv/recordings

If you're adding a new storage drive (or partition) the simplest is to mount it under /var/lib/mythtv/  also, e.g.: /var/lib/mythtv/recordings2   ...or whatever.

You will need to properly partition the newly installed drive first and create the filesystem (xfs, or ext4, or ext3) for the partition(s). The are no shortage of guides on how to do this -one is: [http://www.skullbox.net/newsda.php](http://www.skullbox.net/newsda.php) Use it or find one you like better.  

You will need to add an empty directory "recordings2" to /var/lib/mythtv/  using the mkdir command. You will then want to test your new mountpoint by mounting your new device to this directory manually.

sudo mount /dev/sd[whatever]   /var/lib/mythtv/recordings2

If it works and you can read/write to and from it, then you can make it permanent in fstab, something like:

/dev/sd[whatever]  /var/lib/mythtv/recordings2  ext4  defaults  0   2

Use the actual device node of the device "sdb1", "sdc1" or whatever, and the actual filesystem on the partition (ext4, or xfs, or ext3, or ext2) "0" is for no backup with dump command, "2" is for no bootup root filesystem check.

Once you have the device automounting at boot, change the owner of /var/lib/mythtv/recordings2 to "mythtv" (from "root") and change the group to "mythtv". There will be problems if mythtv is not the owner and group of the recording directories. Set permissions on the directory to something like 775. 

Finally, set the mythtv storage directories to properly reflect the new directory. And it's done.

---

### Post by laffinet on 2010-08-09
You might also want to have a look at lvm.

I recently moved my backend to lvm for all my media, makes adding drives, managing space for recordings, videos etc. sooo much easier.

From another forum:
> So in the case of Linux a physical volume is either the entire drive or a partition on a drive.

So, you then have Physical Volumes (entire drives or partitions), that are grouped together to form a Volume Group. i.e. You can think of it as merging a number of drives or partitions together to form one big disk.

On that Volume Group we then can create what are called Logical Volumes. These Volumes can be any size up to the maximum space of all drives added together. On each Logical Volume you create a File System. So in essence you could think of a logical volume as a partition but it isn't really.

A logical volume is just a portion of disk on which a filesystem goes. You can have many logical volumes and many filesystems that either live entirely on one disk or can span multiple disks.

The filesystems and logical volumes can be grown on the fly easily, without unmounting them. This is where they differ greatly to partitions where resizing is simply not possible.


Google it or have a look [here]("http://www.howtoforge.com/linux_lvm").

---

### Post by bance on 2010-08-10
Thanks for your replies,



@klc5555 I had already managed to create the partition and format it using a live cd and gparted, during this process I labelled the drive. 

I was a little unsure about the options when editing fstab and I think you've cleared that up for me. Ta!

I'm still a little confused about the mount point though. I understand from your post, and the wiki, that the default location is /var/lib/mythtv. 

However further investigation brought up _[COLOR="Red"][this]("http://ubuntuforums.org/showthread.php?t=779498&page=2&highlight=Re:+Mythbuntu+Partitioning")[/COLOR]_ post No 11. Perhaps you could explain the logic to it ?



@laffinet Thanks, I have heard about LVM and your link was very informative, but I understand that disk failure could have serious consequences when using LVM. 

I had intended to go with storage groups, although I understand there are limitations to this also. Perhaps you could explain the pro's and con's.



Once again thanks for the help, I'm really glad I've got involved with OSS it's really exiting!

Steve

---

### Post by klc5555 on 2010-08-10
> **bance said:**
> Thanks for your replies,



@klc5555 I had already managed to create the partition and format it using a live cd and gparted, during this process I labelled the drive. 

I was a little unsure about the options when editing fstab and I think you've cleared that up for me. Ta!

I'm still a little confused about the mount point though. I understand from your post, and the wiki, that the default location is /var/lib/mythtv. 

However further investigation brought up _[COLOR="Red"]this[/COLOR]_ post No 11. Perhaps you could explain the logic to it ?



@laffinet Thanks, I have heard about LVM and your link was very informative, but I understand that disk failure could have serious consequences when using LVM. 

I had intended to go with storage groups, although I understand there are limitations to this also. Perhaps you could explain the pro's and con's.



Once again thanks for the help, I'm really glad I've got involved with OSS it's really exiting!

Steve

Can't address the logic of the mountpoint reference: there's no live link to the posting. 

Various Mythtv distros put the recordings in various places. You can mount the new device anywhere you want. The default in Mythbuntu is under /var/lib/mythtv/ The critical thing is that the device itself and the path to it be owned/grouped to "mythtv", and not to the user's account or to root. Many strange problems that are ultimately traced to ownership/permissions issues will be avoided this way. 

The current problems related to storage groups are not particularly relevant to the use of storage groups for television recordings, which was the original implementation of storage groups beginning with Mythtv 0.21. The reason one uses storage groups for tv recordings is that it is the only easy way to allow tv to be recorded and stored to more than one partition per backend. Sure, a single-partition 2T drive seems like a lot of storage, but it fills up more quickly than you think and you can't easily record/store to say, 4, 10, 16T of storage space on a single backend without setting up a storage group.

---

### Post by bance on 2010-08-10
Sorry, try the _[COLOR="Red"][link]("http://ubuntuforums.org/showthread.php?t=779498&page=2&highlight=Re:+Mythbuntu+Partitioning")[/COLOR]_ again please.

---

### Post by klc5555 on 2010-08-10
> **bance said:**
> Sorry, try the _[COLOR="Red"][link]("http://ubuntuforums.org/showthread.php?t=779498&page=2&highlight=Re:+Mythbuntu+Partitioning")[/COLOR]_ again please.

tgm4883 in the linked post says pretty much what we've all been saying. The default is under /var/lib/mythtv/ The sentence beginning "I myself think this is a bad location ..." refers specifically to single drive, single partition Mythbuntu installations, where the whole /var directory, including /var/lib/mythtv/recordings is reformatted if you reinstall Mythbuntu. In that single-drive configuration, recordings would be toast if not moved somewhere before reinstallation. 

But obviously, if you have added a second drive for your recordings, you can mount it anywhere you wish, including as /var/lib/mythtv/recordings1. A second drive does not get reformatted in a normal Mythbuntu reinstallation, regardless of where it may be mounted it in the current installation. 

I keep the recordings on my Mythbuntu master backend mounted under /var/lib/mythtv/recordings1 (...2, 3, 4) on 4 separate outside disks. On a mythbuntu machine, it's just simpler to do what the defaults expect. Why waste time devising a 5-sided wheel when there is a nice round one right at hand? It takes me about 45 minutes to blow away and restore the OS (and database) without touching the recordings --I've had to do it a couple of times over the last year.

For the secondary backends I have on Slackware, I don't have a "mythtv" user at all, so the tv recording directories on multiple drives are mounted under "/", with appropriate permissions, owners, and groups set up for those machines.

So perhaps try the easy way first, by mounting the storage in the default directory structure where Mythbuntu more-or-less expects it to be. If a better solution occurs to you later, change it. What will it cost, ten minutes configuration time?

---

### Post by laffinet on 2010-08-10
> **bance said:**
> @laffinet Thanks, I have heard about LVM and your link was very informative, but I understand that disk failure could have serious consequences when using LVM.

Yes, disk failure will have serious consequences. LVM is not a redundant system. Nor are storage groups, though.
I believe that most people are worried that when a disk within a volume group dies you lose all the data in that volume group. However I am told that you can recover the data from the disks within the volume group that haven't died, although it might take a bit of fiddling around.
I backup all the data that I absolutely do not want to lose (photos, homevideos) to another drive in a different machine. If I lose all my recordings, movies etc. I obviously wouldn't be happy, but it's not the end of the world. Plus backing them up requires way too much storage space.

The main advantage of lvm is that it's really easy to add new drives, increase and decrease storage space etc.

---

### Post by bance on 2010-08-11
OK, so it looks like I've got a plan. 

I'm going to go along with the recommended method using storage groups and mounting the disks at /var/lib/mythtv.

I'm sorry if I wore your patience a little, but I've put a lot of effort into this project and really want to get it right.

Keep up the good work, and once again thanks!

---

### Post by nickrout on 2010-08-12
> **laffinet said:**
> You might also want to have a look at lvm.

I recently moved my backend to lvm for all my media, makes adding drives, managing space for recordings, videos etc. sooo much easier.

From another forum:


Google it or have a look [here]("http://www.howtoforge.com/linux_lvm").

I counter that recommendation. LVM has problems - lose one drive you lose everything on the lvm group.

Use storage groups, it's specifically designed for mythtv.

---


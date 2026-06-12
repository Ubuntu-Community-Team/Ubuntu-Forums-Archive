---
title: "[SOLVED] Imac g3 tray loader blinking folder with question mark"
date: 2008-06-29
forum: Mac OSX
---

### Post by Super TWiT on 2008-06-29
I have an Imac g3 tray loader.  (yes the same one that has annoyed you in two other posts).  I have upgraded the ram to 384 mb and I have put in a 160 GB hard drive.  I also have a copy of Panther that I am trying to get running on it.  I have done an install making sure that the startup partition is 7 GB.  The hard drive itself shows up as only 128 GB.  However, after trying to boot panther, it shows a blinking folder with a question mark.  I have used the Startup Utility on the install disk to select the operating system.  However, it still boots up this way.  I have also gone ahead and replaced the pram battery, however, again this still happens.  I wonder if this has anything to do with the hard drive being bigger than it really supports.  I think it has the latest firmware updates but I am not sure, and couldn't install them anyway because I don't have OS x 9.  (Note: This is my first mac, so forgive me if I ask stupid or newbie questions).

---

### Post by stream303 on 2008-06-29
If you hold down the alt/option key upon startup, can you highlight the startup drive that way, and click on the right-arrow?

Have you zapped the pram - I know that sometimes when major upgrades are performed, especially since you changed the battery, hard drive, and ram, a pram reset is a nice way to start with a clean slate.  (hold down CMD-Option-P-R while powering up and waiting for TWO chimes)  CMD=cloverleaf, not Ctrl like I always get confused with in a hurry. :)

The great part is that your system recognizes 128gb for hd use!  I've got a feeling that you can reinstall to a much larger amount than 7gb, but I'd try to get this up and running first..

(Tip: if it comes up and immediately prompts you to upgrade, you may want to consider opting to manually download the "combo update" which will do it in one step to 10.3.9, rather than go through the laborious and sometimes error prone sequential-update routine. Check Apple's download site and look for "Mac OS X Combined Update 10.3.9" - at about 117mb, but it's a great thing to have on a CD in case you have to reinstall.)

---

### Post by Super TWiT on 2008-06-30
Thanks for responding.  I have zapped the pram.  I was wondering if this has to do with the fact that I have multiple partitions on this drive.  The reason I have to have 7 GB is because on tray loaders, that's the max size for the startup partition.  The other partitions on the system are another mac partition (for storage) and another partition partitioned as free space (this will be for Xubuntu later).  Could this be the reason I can't locate the startup disk?  P.S.  Thanks for the tip, although I can't boot the operating system yet, when I do, this will be useful.  The mac is so different!  When I first changed the pram battery, the mac wouldn't startup.  I began to suspect the worst, but I then realized that reseting the CUDA is all I had to do.

---

### Post by hellion0 on 2008-07-01
Multiple partitions shouldn't affect things.

The blinking folder at startup means that the machine can't find the OS in the first place. Quite possibly, a bad install occured.

When you were trying for the OSX install, did you select the proper startup disk?

---

### Post by Super TWiT on 2008-07-01
I have reinstalled OS X multiple times.  You are right, the partition doesn't change things, I have installed it with only one drive partitioned and this still happens.  I can't get past the part after my computer reboots.  I have upgraded my ram as well.  Could this be interfering with it?  I have installed 384 MB (256 MB in the upper bay, and 128 MB in the lower bay).  According to the OS X install logs all of the ram is recognized.  While looking at the logs, I did notice something that said there was an unknown error code after trying to install the boot loader.  I am not sure what that's about.  I still think that it is the hard drive being past the limit of the controller, even though it bumped it down.  Oh yeah, to answer your question hellion0 it never asked me to choose a startup disk.  However, I have chosen it in the startup disk utility.  P.S.  The operating system I am trying to install is OS X 10.3 Panther.

---

### Post by hellion0 on 2008-07-02
I don't think being past the limit would be the reason here. One of my Macs runs on such an "oversized" drive (a 160GB "startup" drive on an AGP Graphics G4 Power Mac) and has never given me any problems with startup. To be fair, though, it only has one partition.

---

### Post by Super TWiT on 2008-07-02
That's what's weird about my mac, because I have tried it with only one partition and this still happens.  When I get some time I think I will swap out the hard drive with an 80 gb one to see if that fixes it.

---

### Post by Super TWiT on 2008-07-08
That fixed it!  After I swapped out the hard drive it works just fine.  I guess I should have paid more attention to the size of drive this could handle.  Thanks to everyone who responded in this thread.  Cheers!

---


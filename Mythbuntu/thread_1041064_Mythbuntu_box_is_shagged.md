---
title: "Mythbuntu box is shagged"
date: 2009-01-16
forum: Mythbuntu
---

### Post by Crusty Juggler on 2009-01-16
Since my upgrade to 8.10, Mythbuntu has been giving me problems.  My remote ceased working, several times a day I got the error message that the frontend could not connect with the backend and to check IP addresses, even though it is a standalone frontend + backend system.  

Attempts to reinstall with a freshly burnt image failed, as the disk would load up and I would select "load in a livecd environment" but after it tried to load for a few mins, I got the following error:

```
 BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) buitl-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [     67.601538] end_request: I/O error, dev sr0, sector 1292704
[       67.601590] Buffer I/O error on device sr0, logical block 323176 
```
etc.

I thought I would be smart and boot up a "commercial" (e.g. Ship-It) Ubuntu livecd, which worked fine, and then format the Mythbuntu partition using gparted, while leaving my /var/lib partition alone.

So now here I am with an unbootable HDD and the Mythbuntu livecd still won't load.  I've tried changing the SATA port of my CD/DVD drive.  I've tried using an USB CD drive.  I've tried making a bootable USB drive.

I don't know what else to try.  Any suggestions?

---

### Post by utar on 2009-01-16
Have you tried reburning the CD as the disc could be corrupt and replacing your SATA cable?

Otherwise go into the bios and change the mode of the drive.  Different bioses call this different things but typically it will be set to auto, try other options such as ATA133 etc.

---

### Post by klc5555 on 2009-01-16
> **Crusty Juggler said:**
> Since my upgrade to 8.10, Mythbuntu has been giving me problems.  My remote ceased working, several times a day I got the error message that the frontend could not connect with the backend and to check IP addresses, even though it is a standalone frontend + backend system.  

Attempts to reinstall with a freshly burnt image failed, as the disk would load up and I would select "load in a livecd environment" but after it tried to load for a few mins, I got the following error:

```
 BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) buitl-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [     67.601538] end_request: I/O error, dev sr0, sector 1292704
[       67.601590] Buffer I/O error on device sr0, logical block 323176 
```
etc.

I thought I would be smart and boot up a "commercial" (e.g. Ship-It) Ubuntu livecd, which worked fine, and then format the Mythbuntu partition using gparted, while leaving my /var/lib partition alone.

So now here I am with an unbootable HDD and the Mythbuntu livecd still won't load.  I've tried changing the SATA port of my CD/DVD drive.  I've tried using an USB CD drive.  I've tried making a bootable USB drive.

I don't know what else to try.  Any suggestions?

I tried replying a couple of hours ago, but Our Lady of Perpetual Ubuntu Forum Maintenance nuked the text when I tried to post. (For all the maintenance, you'd think it would work better.)

If your /var/lib partition contains also your recordings directory, and therefore you don't want to destroy it (yes?), you could try:

Downgrade. Pull out the CD of your last-known-good installable Mythbuntu (8.04 or 7.10). Boot it. If it won't boot, you should look to hardware problems (Sorry :(  )

Assuming the 8.04/7.10 CD boots, format your trashed OS partition and install 8.04/7.10 to this partition. Install the whole Mythbuntu to this formerly trashed OS partition. Leave the partition that used to be mounted /var/lib alone!

Once you have a stable, bootable 8.04 installed, or a 7.10 with all the Mythtv 0.21 backports installed, make a new directory for your old "/var/lib" partition to be mounted to. Call it, say, /recordings

sudo mkdir /recordings

Now mount the partition there.

sudo mount /dev/sda<whatever-it-is>  /recordings

You should now be able to find your recordings somewhere in the directory structure under /recordings/...

You can neaten up the directory structure under /recordings, if you wish, and get rid of the leftover files that are not either recordings or mythconverg backups (if you have kept any of them there). If you're satisfied with the recordings being where they currently are, then you need to sudo chmod mythtv, and sudo chgrp mythtv the directories from /recordings down to where your recordings files are so that mythtv can use them; currently the directories will have been set to root. The directory with the actual recordings in them should also have permissions set sudo chmod 775 or 776 or 777, so that there will be no permissions glitches down the road with mythtv or, say, mytharchive.

/etc/fstab will have to be edited to add this partition and its mount point (/recordings) with its correct filesystem and "defaults   0    2"    so that the point will mount automatically at boot.

If you have a mythconverg backup, you can now restore from it, following the instructions in [http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance#The_database](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance#The_database)    

Thereafter, if you edit "Storage groups" in the backend setup to reflect where your recordings are actually at, Mythtv should have no problem finding them.

If you didn't have a database backup to restore, then you'll have to set up the whole backend again, set the "Storage groups" to reflect where your recordings now are, and then add the recordings manually using the myth.rebuilddatabase.pl script in /contrib

At least those would be the steps I'd expect troubleshooting a complete meltdown like yours to progress along. Life is generally easier when the recordings are not only on a separate partition, but also on a different hard disk than the bootup disk.

Good luck! (And I hope I can actually post before the forum goes down yet again...)

---

### Post by Crusty Juggler on 2009-01-17
I downloaded 8.04.1 and reinstalled, and besides issues with the newest NVIDIA drivers, it is all working.

What a pain in the ***.

---


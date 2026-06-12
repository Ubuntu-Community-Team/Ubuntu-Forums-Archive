---
title: "Missing recordings in myth database"
date: 2009-10-29
forum: Mythbuntu
---

### Post by zapstrap on 2009-10-29
I added a tuner card to the myth box, and due to a history of troublesome upgrades, my first move was to mirror the OS disc.  I then removed the 'golden' OS disc, and put in the 'copy'.  From this point, I felt free to experiment, with an easy way back to a working system if I made an unrecoverable mess.  There is also a second disc strictly for holding content.  This disc remained in the system during the whole process.

The rest of the machine is: ASUS P4P800E mobo, P4, 3GHz, 1GB RAM, Nvidia fx6200, Hauppauge PVR-150, and new HVR-1600, running mythbuntu 9.04.

The upgrade went well, and out of laziness, I left the copied OS drive in for a couple of days.  The 'copy' of the golden disc is an older drive, and it's a little noisy for the living room, so I swapped back to the golden disc and whipped through the upgrade process for the tuner card a second time.

All went smoothly, except for one thing.  During the period in which the copied OS disc was in use, a few recordings were made.  Now that the original golden OS disc is back, those recordings don't show up in the archive of recorded shows.  I checked the directory on the media disc, the recordings are definitely there.  I thought a simple database refresh would note the presence of new recordings and add them to the list. Not so.  I didn't see much on how to handle this on the mythtv site, so I'm not sure how to get everything back in sync.

Is there a simple way of handling this?  Perhaps a script for refreshing the database?

---

### Post by nickrout on 2009-10-29
> **zapstrap said:**
> I added a tuner card to the myth box, and due to a history of troublesome upgrades, my first move was to mirror the OS disc.  I then removed the 'golden' OS disc, and put in the 'copy'.  From this point, I felt free to experiment, with an easy way back to a working system if I made an unrecoverable mess.  There is also a second disc strictly for holding content.  This disc remained in the system during the whole process.

The rest of the machine is: ASUS P4P800E mobo, P4, 3GHz, 1GB RAM, Nvidia fx6200, Hauppauge PVR-150, and new HVR-1600, running mythbuntu 9.04.

The upgrade went well, and out of laziness, I left the copied OS drive in for a couple of days.  The 'copy' of the golden disc is an older drive, and it's a little noisy for the living room, so I swapped back to the golden disc and whipped through the upgrade process for the tuner card a second time.

All went smoothly, except for one thing.  During the period in which the copied OS disc was in use, a few recordings were made.  Now that the original golden OS disc is back, those recordings don't show up in the archive of recorded shows.  I checked the directory on the media disc, the recordings are definitely there.  I thought a simple database refresh would note the presence of new recordings and add them to the list. Not so.  I didn't see much on how to handle this on the mythtv site, so I'm not sure how to get everything back in sync.

Is there a simple way of handling this?  Perhaps a script for refreshing the database?

The database on the "golden" disk will not have been updated as the recordings were made. Two options:

Load up the copy disk and extract the required info from the database tables and then insert that stuff into the database tables on the golden disk.

OR (probably better)

use [http://www.mythtv.org/wiki/Myth.find_orphans.pl](http://www.mythtv.org/wiki/Myth.find_orphans.pl)

---

### Post by SiHa on 2009-10-30
Out of interest, what process did you use for cloning your OS disc? I'm about to do exactly the same prior to upgrade of my master BE/FE, but have been a little confused as to the options. Partimage looked promising, but I've seen quite a bit that seems to indicate that it's more of a backup tool, and will compress the image. I'm after a bootable clone, as you have done. 
I did try```
sudo dd if=/dev/sda1 of=/dev/sdb1
```
after booting to a liveCD session, but it chuntered on for about half an hour trying to copy a 4Gb partition, and I gave up.
Any advice appreciated.

---

### Post by jb5 on 2009-10-30
[Clonezilla](http://clonezilla.org/) works well. 
Will allow a disk to disk (or partition / partition) clone, or a compressed image of a disk or partition.

---

### Post by zapstrap on 2009-10-30
SiHa,

I used this CD:

[http://www.sysresccd.org](http://www.sysresccd.org)

to boot, which is the same concept as a liveCD session.  I put both drives in the machine, and used the dd command as you did.  If your drives are ATA drives, you will do a little better if you put each one on its own cable.  If they're SATA drives they should be pretty quick to copy.  I don't think I'd use an external USB or firewire connection, but both of those options should be pretty fast.  Just make sure it's a USB2 connection :)

It takes quite a while, but 4GB in 1/2 hour is really slow.  It should be faster than that, and I'm not sure why you'd see such slow performance.  It took slightly over one hour to copy 40GB without any options.

Also, there's one slight difference in the command:

dd if=/dev/sda of=/dev/sdb

This copies the entire disc, not just individual partitions.  You might try the ibs and obs options to increase the # of bytes being copied each read & write.  Bigger chunks should go faster.

If you're trying monitor the process, you can send a kill command like so:

kill -USR1 $pid

This will make dd show its progress without actually killing it.  This way you can figure out fairly quickly how it's doing.

HTH,
lj

---

### Post by SiHa on 2009-10-30
@Zapstrap:
Great, thanks for the advice. I thought I tried **dd if=/dev/sda of=/dev/sdb**, but it didn't work, so I went for the partitions instead, I'll try again.

The drive I was copying to was via a IDE->USB2 converter, which is usually very fast. Think I might try it on the internal IDE connector instead, though.

Also, great pointer for checking progress, thanks. I did see something about sending a USR1 signal in the manpages, but didn't really get it.

@JB5, thanks - I'll look at clonezilla as well.

Cheers.

---

### Post by zapstrap on 2009-10-30
SiHa,

Getting a little off topic of this thread but a good bit of fun nonetheless.  One thing about the kill -USR1 option, either run like so:

dd if=/dev/sda of=/dev/sdb &

to get the process to run in the background, then use the "kill -USR1 <pid>" option to see how it's doing, or if you're not so organized (like me), just run dd like you did before, and open a second terminal window so you can enter the kill command.  Note that progress will appear on the terminal running dd, not kill.

For the sake of a little performance boost, do dd if=... of=... bs=16k &

The bs=16k will speed up the process, but not by a huge amount.  I tried fooling around with duplicating a big file (~500MB) on an old (AMD K6-II+ 500MHz) machine, and the difference between the default block size of 512 bytes vs 16k was roughly 18%.  If it takes an hour with default options, you might shave 10 minutes(ish) off.  Go too big on the block size and it starts to slow down again, but it seemed like 16K was the sweet spot.

Cheers,
lj

---

### Post by zapstrap on 2009-10-30
nickrout,

Thanks for the suggestion, but it turns out what I really wanted was myth.rebuilddatabase.pl.  Your tip put me in the right place to find it, so all good.  That script found a lot of stuff I didn't realize was there.  The machine had a major meltdown several months ago (needed a new motherboard) and I just assumed all was well in the recordings directory.  It turns out there was a lot of fragmented bits of recordings in there.  The rebuilddatabase script seem to have cleaned it all up quite nicely.

cheers,
lj

---

### Post by SiHa on 2009-10-31
> **zapstrap said:**
> SiHa,

Getting a little off topic of this thread but a good bit of fun nonetheless.  One thing about the kill -USR1 option, either run like so:

dd if=/dev/sda of=/dev/sdb &

to get the process to run in the background, then use the "kill -USR1 <pid>" option to see how it's doing, or if you're not so organized (like me), just run dd like you did before, and open a second terminal window so you can enter the kill command.  Note that progress will appear on the terminal running dd, not kill.

For the sake of a little performance boost, do dd if=... of=... bs=16k &

The bs=16k will speed up the process, but not by a huge amount.  I tried fooling around with duplicating a big file (~500MB) on an old (AMD K6-II+ 500MHz) machine, and the difference between the default block size of 512 bytes vs 16k was roughly 18%.  If it takes an hour with default options, you might shave 10 minutes(ish) off.  Go too big on the block size and it starts to slow down again, but it seemed like 16K was the sweet spot.

Cheers,
lj

Thanks for the advice, I will almost certainly use it in the future. In the end though, I just did the new install on the old spare 60GB drive, and pulled the plug on my existing OS drive. When (if?) the new install proves stable, I'll just add the old drive back as storage. If not, I'll just boot of the old drive and keep the wife happy!

Cheers,

Simon

---


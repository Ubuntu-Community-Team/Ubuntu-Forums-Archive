---
title: "Howto clone &amp; restore system"
date: 2010-07-21
forum: Mythbuntu
---

### Post by bcg30506 on 2010-07-21
I'm very familiar with Carbon Copy Cloner for the Mac, but now I want to clone my working mythbuntu system in order to try the new MythTV .23 version.  I'd like to clone what I have in a manner that if the new install or version does not work with my hardware or to my wife's liking, I can revert back to exactly what I had in one step by restoring from the clone drive.

Is there anything that does this in the Ubuntu world as simply as CCC does in OS/X?  Can someone help point me in the right direction so I can attempt an upgrade to be more current (as I'm running 21-fixes still now) without risking loss of recording data or lots of downtime?

---

### Post by grandpaken on 2010-07-21
> **bcg30506 said:**
> I'm very familiar with Carbon Copy Cloner for the Mac, but now I want to clone my working mythbuntu system in order to try the new MythTV .23 version.  I'd like to clone what I have in a manner that if the new install or version does not work with my hardware or to my wife's liking, I can revert back to exactly what I had in one step by restoring from the clone drive.

Is there anything that does this in the Ubuntu world as simply as CCC does in OS/X?  Can someone help point me in the right direction so I can attempt an upgrade to be more current (as I'm running 21-fixes still now) without risking loss of recording data or lots of downtime?


   I use Clonezilla but it's most likely not what you're used to on the Mac.  It looks more like an old DOS application but it works.

---

### Post by dakota34 on 2010-07-21
just restored a frontend off a clonezillad image, worked fine, now backing up every pc in the house with a clonezilla-live cd.

---

### Post by laffinet on 2010-07-21
+1 for clonezilla

Doesn't have a shiny GUI but it's still easy enough to use and just works !

You have the option to work with image files or directly with partitions/drives.

---

### Post by bcg30506 on 2010-07-27
Thanks for the replies so far.  I'll look into Clonezilla.  I have written a bash script to backup my system years ago that I still use which uses "rsync -a --progress --numeric-ids --delete" from / to an external USB drive.

How would this method compare with Clonezilla?  I know the rsync method preserves "everything" and I can restore from the USB using rsync in the other direction, but I've never tried it on a system level, ie. across mythbuntu versions.

---

### Post by laffinet on 2010-07-27
Probably very similar.

I think under the bonnet clonezilla is just using "dd" to copy partitions or drives. It more or less provides a "frontend" to dd, determines the options and switches through a series of dialogues and then runs the dd command.
It even shows you the final command so next time you could just re-use it instead of having to go through the dialogue again.

---

### Post by alien878 on 2010-07-28
rsync vs. clonezilla:

rsync is good if you want to back up individual directories.  It is not so good for backup up the root partition (i.e. /):

[LIST]
[*]The partition is mounted when rsync runs, so files may change during the backup making a restore unstable.
[*]If you restore everything, you will restore dynamic system files which may cause problems booting.
[*]The MBR will have to probably be rebuilt as the files will change location on disk.
[/LIST]

The downsize of clonezilla is that it is difficult to automate.  rsync can be in a simple cron job.

I have a small root partition for the install and all the other video, music, home, etc. files are on separate partitions.  I use clonezilla manually on the small root partition before I upgrade anything (I've been burned by unstable upgrades in ubuntu too often).  I use rsync in a daily cron on a selection of directories in the other partitions.

---

### Post by sr_guy on 2010-07-29
Remastersys + unetbootin. Great for backing to a usb thumb drive. Remastersys to create the backup iso image, unetbootin to create a menu driven boot menu using the backup iso image. My entire install of apps, mythtv, boxee, asterisk + freepbx is about a 1.7Gig image

---

### Post by bcg30506 on 2010-07-30
> **alien878 said:**
> rsync vs. clonezilla:

rsync is good if you want to back up individual directories.  It is not so good for backup up the root partition (i.e. /):

[LIST]
[*]The partition is mounted when rsync runs, so files may change during the backup making a restore unstable.
[*]If you restore everything, you will restore dynamic system files which may cause problems booting.
[*]The MBR will have to probably be rebuilt as the files will change location on disk.
[/LIST]

The downsize of clonezilla is that it is difficult to automate.  rsync can be in a simple cron job.

I have a small root partition for the install and all the other video, music, home, etc. files are on separate partitions.  I use clonezilla manually on the small root partition before I upgrade anything (I've been burned by unstable upgrades in ubuntu too often).  I use rsync in a daily cron on a selection of directories in the other partitions.

This is the approach I decided upon and it worked great. Thanks!  I've been using rsync automated for quite some time to backup my data, but this was my first go at Clonezilla for cloning the OS partition.  As it turns out, my upgrade to 10.04 went smoothly so I didn't "need" it but it's nice to have it.  I've also backed up the new one after upgrading just to be safe.

---


---
title: "MythTV: Increase storage space for recordings"
date: 2007-08-29
forum: Multimedia &amp; Video
---

### Post by nattugglan on 2007-08-29
Hi!

I need to increase the storage space for my MythTV recordings.
Today recordings are saved in ~/recordings. This is set in the MythTV Backend Setup -> General -> Page 2, Directory to hold recordings.

If I change this to a new folder on a new drive, what will happen? Will the "old" recordings in ~/recordings still be accessible in MythTV Frontend & MythWeb as if nothing has happened? And will the new recordings made in the new folder on the new drive show up seamlessly together with the old recordings in MythTV Frontend and MythWeb?

I don't want to take a chance here and screw things up.

I guess the best thing would be if it is possible to increase ~/recordings with the available space on the new hard drive somehow..

How have You done?

nattugglan

---

### Post by bowmanr@mailcity.com on 2007-08-29
AFAIK (unless I have wasted several hours last night!), the recordings will NOT magically be accessible. MythFrontend will still display them in the recordings selection screen, but the files will be missing and gradually the items will all turn grey.

As I see it, you need to either :
1) copy all your recordings from the old to the new mount point, or,
2) extend ~/recordings by adding space (assuming you've set up LVM)

I've not used LVM, so can not assist there. 

Personally, I have a dedicated disk purely for MythTV recordings, which I have just replaced with a bigger drive. Last night I installed a new drive, copied the files from the old recordings area, changed fstab to mount the new drive in the same mount point as the old area, obviously removing the mount of the old disk in fstab. Therefore, I changed nothing in MythTV -- merely acquired additional space. The old drive has been removed and shall soon be commissioned in an alternate machine.

Hope that helps a little.
Robert

---

### Post by edward4130 on 2007-08-29
i have a separate 500gig SATA drive for mythtv/recordings and another for mythtv/videos.  if you add the hadrdrives you can add the mountpoints in your /etc/fstab file.  Make sure you copy all of the originals off and move them to the new drive after you have it mounted.

If you get stuck I will be on here tomorrow and check your progress.

---

### Post by nattugglan on 2007-09-01
Thank you for Your replies!

My current recordings are stored on a 500GB drive, and the largest drives I have are 500GB, so moving everything to a new drive won't help. :)

I have never used LVM either, but from what I've found when searching for a solution, LVM seems like the way to go. Besides getting a 1TB drive of course - but that will only solve the problem for a limited time..

This is a big problem, and I was surprised that this hasn't gotten more attention. It looks like it's being discussed however, and hopefully a solution will find its way into coming versions of MythTV.

One would think that the locations of already recorded shows would remain in the database, and still be available when changing the recording path to a new location. Thank you for sharing your findings.

I have no space to make a full backup of the system, so I don't dare to fiddle with it.. :)

---


---
title: "Add hard drive to existing system. How ?"
date: 2009-01-21
forum: Mythbuntu
---

### Post by laffinet on 2009-01-21
Hi all !

I've got a running Mythbuntu (8.10) system and need more storage space. I bought a new hard drive and need to add it to my existing system. 
I'd like to keep the old drive as the main drive (system files etc.), plus leave music and pictures/photos on it too. The new drive should be for recordings and videos only.

How do I go about it ? 

I found some pointers [here ]("http://ubuntuforums.org/showthread.php?t=837931&") (I think post #3 is what I need to do) but have a few questions/would like some explanation on what I'm doing here.

1. What file system do I format the drive to ? I'm assuming xfs. 

2. The way described in the link mounts the hard drive as /var/lib/mythtv. Does this also work in my case, where I only want to transfer videos & recordings ? What happens to the existing /var/lib/mythtv ?

3. Once created, do I simply copy existing videos/recordings to the new folders and they get picked up by mythbuntu ?

4. Or is this the complete wrong approach and I need to do all this via storage groups ? If so, how ?

Thanks for any help.

Edit:
Found another guide to [here]("http://egrets.wordpress.com/2008/03/07/mythbuntu-setting-up-a-2nd-drive-for-videos-and-recordings/"). Is this what I should be doing ?

---

### Post by teet on 2009-01-21
You might want to check out "gparted".  You should be able to format and mount your new harddrive using it.  I have all my recording in a folder on the root filesystem called "myth" (mount location is just /myth).  You can specify your recordings folder in the mythtv-setup ("mythtv backend setup")...not sure if the mythbuntu control center has that option.

I use JFS myself (as compared to XFS).  It runs great.

-teet

---

### Post by laffinet on 2009-01-21
Thanks. I'm aware of gparted and will definitely use it to format the drive.

It's the integration of the new folders for videos and recordings into mythbuntu and relocating the existing stuff that has me slightly worried, ie I'm not 100% sure how it's done.

I've done some more reading and it looks like it can be done via recording groups (which allows for multiple locations I think), but I guess I won't know until I try.

---

### Post by newlinux on 2009-01-21
yes, storage groups allow for multiple directories for recordings, so you can mount this new drive anywhere you'd like and then setup a storage group for it.

As for mythvideo files, you can store them in multiple directories as well, but you need to tell the mythvideo to look in two places in the frontend setup (separate the directories with a colon).

---

### Post by laffinet on 2009-01-21
Thanks. So the steps are:

1. Install and format drive
2. create directories, 1 for video, 1 for recordings
3. mount drive (edit fstab to make it permanent)
4. change settings for recording groups
5. change settings for videos

That's it ?

---

### Post by klc5555 on 2009-01-22
> **laffinet said:**
> Thanks. So the steps are:

1. Install and format drive
2. create directories, 1 for video, 1 for recordings
3. mount drive (edit fstab to make it permanent)
4. change settings for recording groups
5. change settings for videos

That's it ?

Somewhere along the way, chown and chgrp the new mount's directory structure to "mythtv" (from "root"). chmod the permissions in your  new directories to 775 or better. If "mythtv" doesn't have ownership & full write permissions on a recording directory, it will cause problems.

---

### Post by laffinet on 2009-01-22
> **klc5555 said:**
> Somewhere along the way, chown and chgrp the new mount's directory structure to "mythtv" (from "root"). chmod the permissions in your  new directories to 775 or better. If "mythtv" doesn't have ownership & full write permissions on a recording directory, it will cause problems.

Thanks. Figured that out along the way. 

All done now, works beautifully. So, to recap what I've done (in case someone's faced with the same task:

1. install and format drive
2. create mount point
3. create directories on new drive, 1 for video, 1 for recordings
4. change permissions for new directories
5. change fstab to mount new drive on boot
6. change settings for recording groups (backend setup)
7. change settings for videos (frontend setup)

Thanks everyone for the help.

---


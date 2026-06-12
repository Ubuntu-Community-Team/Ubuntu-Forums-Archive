---
title: "Adding Drive For Videos"
date: 2007-12-28
forum: Mythbuntu
---

### Post by Just4Fun20 on 2007-12-28
I want to add a second Hard Drive to my MythBuntu machine specifically for Videos.  I have no problem with mounting and formatting it.  I've already installed it and rebooted the machine.  

My question is on recommendations for mount point, etc.  I have two HD's.  The first is 120GB and is the MythBuntu drive I installed on.  I just added a 250GB drive.  

It seems to me that the best thing to do (most conventional) is to mount the drive as /mnt/videos.  Then reconfigure MythTV to point to /mnt/videos as the proper location.  Then I can add a symbolic link back to /var/lib/mythtv/videos and I should see my currently stored videos (and take maximum advantage of the existing storage).  

The other choice would be to move the videos to another location and mount the new drive as /var/lib/mythtv/videos.  This has the advantage of not altering a "standard" MythBuntu installation and so I won't get some strange scripting error (or some such) at some random future date, probably during an upgrade.  I could then create a symbolic link to wherever I moved the videos.  

Any wisdom on the preferred path?  TIA

---

### Post by kidders on 2007-12-30
Hi there,

Most of the time, the name of a mount point isn't particularly important, so there's no need to worry about violating any conventions. In my opinion, what to do depends on whether you want to *only* store videos on your new hard disk.

For instance, you might decide to put two filesystems on your new disk. You could mount one at /var/lib/mythtv/videos, and the other someplace else, for some other purpose.

Another option might be to move your entire /var directory onto the new disk.

Your o/p suggests you might want to use both new *and* pre-existing disk space for videos. I'm not a mythbuntu user, so I can't be 100% sure ... would this work? ...
[LIST]
[*]Move all your pre-existing videos to /var/lib/mythtv/videos/disk1
[*]Create /var/lib/mythtv/videos/disk2
[*]Mount your new disk to /var/lib/mythtv/videos/disk2[/LIST]Personally, I would find it preferable to keep all my videos on the same filesystem, but given disk space constraints, you might not be able to do that.

---

### Post by vanadium on 2007-12-30
In Linux, you can do it where and how you want, but indeed I recommend you follow your first suggestion, which is the most conventional approach. After that, you can customize all access points using symbolic links if needed.

---

### Post by newlinux on 2007-12-30
You can have multiple paths for mythvideo directory. Simply separate them with a colon in path specification field for your mythvideo files. Then you could mount your new drive anywhere and just add that path to your mythvideo path. Just another option.

---

### Post by voctikal on 2007-12-30
Not trying to steal anyones thread but if I were to add another hdd that I only wanted to put video on, what all would be involved. 

Once I have it installed that is.

---


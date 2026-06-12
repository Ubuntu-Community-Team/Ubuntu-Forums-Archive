---
title: "Unable to delete recordings"
date: 2009-09-04
forum: Mythbuntu
---

### Post by sschneidertx on 2009-09-04
I added a second hard drive to my mythbuntu system to store all of my recordings.  I moved the old recordings to the new drive, I edited the /etc/fstab, I mounted the drive, and I changed the storage group to my new drive in mythtv backend setup.  When I go into the mythtv frontend to view recording, I see all of the old recording and I can watch them without any problems.  I am also able to save new recordings to this new drive and watch them without any problems.  Problems arise when I try to delete any of the recordings from the mythtv frontend.  It will be removed for a few seconds and then come right back.  I need some help in getting the recording to be permanately deleted.

---

### Post by klc5555 on 2009-09-04
> **sschneidertx said:**
> I added a second hard drive to my mythbuntu system to store all of my recordings.  I moved the old recordings to the new drive, I edited the /etc/fstab, I mounted the drive, and I changed the storage group to my new drive in mythtv backend setup.  When I go into the mythtv frontend to view recording, I see all of the old recording and I can watch them without any problems.  I am also able to save new recordings to this new drive and watch them without any problems.  Problems arise when I try to delete any of the recordings from the mythtv frontend.  It will be removed for a few seconds and then come right back.  I need some help in getting the recording to be permanately deleted.

The recordings need to have their owner and group both changed back to "mythtv". When you copied them to their new location, the owner/group became whichever account/userid you used while copying them over.

---

### Post by novellahub on 2009-09-04
See this post for more details:

[http://ubuntuforums.org/showpost.php?p=6965380&postcount=2](http://ubuntuforums.org/showpost.php?p=6965380&postcount=2)

You can do a recursive chmod and chown as well using the -R option.

---


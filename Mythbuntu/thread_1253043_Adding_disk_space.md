---
title: "Adding disk space"
date: 2009-08-29
forum: Mythbuntu
---

### Post by HW_Hack on 2009-08-29
So what is the story on increasing storage space by popping in a second hard drive. I've got a mythTV combo system (frontend + backend) running nicely on a 100GB drive. If I pop in a second drive how does it get configured in mythTV ?

---

### Post by ktmom on 2009-08-29
I did this by mounting the drive via fstab, and then refering to the path from within the mythbackend setup > storage directories (item 6 in the backend setup).  The extra space for me was used not for live recording but for the video directories.  

[http://www.mythtv.org/docs/mythtv-HOWTO-9.html#storagegroups]("http://www.mythtv.org/docs/mythtv-HOWTO-9.html#storagegroups")

---

### Post by tgm4883 on 2009-08-29
Yep, you will need to add the drive in fstab, then add it to a storage group

---

### Post by laffinet on 2009-08-30
These are the necessary steps:

1. install and format drive
2. create mount point
3. create directories on new drive, eg 1 for video, 1 for recordings
4. change permissions for new directories (so that mythtv has write permission)
5. change fstab to mount new drive on boot
6. change settings for recording groups (backend setup)
7. change settings for videos (frontend setup)

---


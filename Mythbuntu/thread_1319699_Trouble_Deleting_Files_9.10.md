---
title: "Trouble Deleting Files 9.10"
date: 2009-11-08
forum: Mythbuntu
---

### Post by felizcortez on 2009-11-08
I just did a clean install of 9.10 last night and am having trouble deleting recordings after watching them.  In "Watch Recordings" menu I put hit "i" and then delete recording.  This removes the recording on that screen initially, but if I leave the watch recordings menu and come back the program reappears as if it was never deleted.  Another piece of information is that after I delete a recording the Television show title is still present (not removed).  For Example, if I delete a recording of The Office named Office Olympics, then the title The Office still shows up as a menu, but the recording is no longer there.  When i come back to Watch recordings later, the original recording reappears.  Logs are below.  Any help would be appreciated. 

[http://mythbuntu.pastebin.com/f50353206]("http://mythbuntu.pastebin.com/f50353206")

---

### Post by SiHa on 2009-11-08
Sounds like a permissions issue.

I had this when I installed 9.10. I imported some old recordings, and found that I couldn't delete them afterwards.

what does> ls -al /var/lib/mythtv/recordingsgive?

Or, do you have 'Auto-Expire instead of delete' checked in the frontend setup?

---

### Post by jMon54 on 2010-01-23
I am having this same issue.  Has anyone found a fix?  In my case, if I wait awhile before moving on to the next screen or item to delete, it will stay deleted.  And I think the bigger the file the longer it takes.  But it is frustrating to see the recording disappear off the screen after hitting delete, then have it re-appear next time I visit the screen.  And it is not a permissions issue.  In 9.04, when I deleted a recording, I could see the system was taking a while to do it.  Now it seems as if it's doing nothing.  Whether I do it from Mythtv or from Mythweb the behavior is the same.

---

### Post by newbie02 on 2010-01-23
Having same issue. I have at most keep X number of episodes which is helping but from what I am seeing all over the net about this issue is for some people this will continue until the drive becomes full.

I am going to manually delete the recording for now.

newbie02

---

### Post by jaakan on 2010-01-24
sounds like slow delete is on

---

### Post by jMon54 on 2010-01-28
> **jaakan said:**
> sounds like slow delete is on

Thanks!  Turning it off worked for me!  Much obliged!!

---

### Post by geolizardo on 2010-02-18
I looked through the setup and I could not find a slow delete setting. May I ask where I could find this?

Thanks very much!

---

### Post by novellahub on 2010-02-18
> **geolizardo said:**
> I looked through the setup and I could not find a slow delete setting. May I ask where I could find this?

Thanks very much!

The slow delete setting is under mythtv-setup.  Under the general settings.

---

### Post by mbleslie on 2010-03-07
This was exactly the problem I was having as well. With slow delete turned off and while using mythweb, I could actually delete recordings. I made sure that I wasn't set to auto-expire but actually to delete. I did notice that if I was trying to delete a bunch of recordings quickly, they would eventually all get deleted but some took a couple of tries. I think the backend was busy doing the delete when I refreshed my recordings list.

Nevertheless, I freed up 400GB of space that was all winter olympics!

---

### Post by Ubu_Fester on 2010-09-23
I was having the same problem.
Unchecking slow delete also worked for me.

---

### Post by ian dobson on 2010-09-24
Hi,

The slow delete option is there for a good reason. If you have your recordings on a ext3 file system, deleting large files takes forever and a day, which blocks the mythtv-backend. With the slow delete option enabled the backend truncates the recording (chops off the end from the file) until it's small enough and then deletes the rest of the file.

ext4/xfs/jfs doesn't have this problem. If your using ext3 but your kernel supports ext4 you can just change your fstab to mount the filesystem using ext4. Although this won't make use of all the ext4 improvements (extents etc) it'll use all improvements that don't change the file structure on disk.

Regards
Ian Dobson

---


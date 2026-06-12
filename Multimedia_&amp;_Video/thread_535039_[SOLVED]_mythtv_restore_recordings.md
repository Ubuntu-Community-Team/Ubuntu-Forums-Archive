---
title: "[SOLVED] mythtv restore recordings"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by a_posse_ad_esse on 2007-08-26
I recently did a reinstall of Ubuntu Server which I had running mythtv.  The system has two hard disks- one for the recordings, the other for the OS, backups, music, etc.  Prior to the reinstall, I backed up the media to the recordings folder, and restored everything to its original folders afterwards.

However, even though the old recordings are in the same place they were previously, mythtv does not view the older files as recordings, even though they are in the correct directory.  I am able to see them as videos in the video section, but there is no information listed about them.  Is there a way to restore the info and have them recognized again?  This would be very helpful for transcoding and commercial flagging, which I did not have configured to my liking last time.

Thanks

---

### Post by Scorpuk on 2007-08-26
You will need to import those recordings into the mythtv database.


You can see how to do that here: [http://www.myhdbox.com/mythtips/2006/05/tip-3-importing-downloaded-tv-shows.php](http://www.myhdbox.com/mythtips/2006/05/tip-3-importing-downloaded-tv-shows.php)

Also check this out if you can't find the script: [http://ubuntuforums.org/showthread.php?t=515225](http://ubuntuforums.org/showthread.php?t=515225)



For the next time you want to do a reinstall or move to another computer it would be advisabel to backup the mythtv database as well as your recordings. Mythtv will only see recordings it holds in its database.

You can see how to do that here: [http://www.mythtv.org/wiki/index.php/User_Manual:Periodic_Maintenance](http://www.mythtv.org/wiki/index.php/User_Manual:Periodic_Maintenance)

---

### Post by a_posse_ad_esse on 2007-08-26
The script works great, thank you for the pointer.

Now, the only problem I have is matching the recording names (i.e. 1005_20070817230000.mpg) to a name.

The channel listing (1005) isn't a problem, as I found a page with the codes [[COLOR="Red"]here[/COLOR]]("http://forums.sagetv.com/forums/showthread.php?p=233770").  I have not been so successful with finding the episode information however.  Does anyone know where I can find archived TV lineups (I need to go back to August 17th)?  It seems that everyone removes such things as they go.

Thank you.

---

### Post by a_posse_ad_esse on 2007-09-09
I abandoned the restoration effort.  There wasn't anything important in there anyway, so I just started again from scratch.

---


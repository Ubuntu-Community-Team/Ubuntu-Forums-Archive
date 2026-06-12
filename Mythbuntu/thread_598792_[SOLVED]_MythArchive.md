---
title: "[SOLVED] MythArchive"
date: 2007-10-31
forum: Mythbuntu
---

### Post by Meph1st0 on 2007-10-31
What more do I have to do to get MythArchive to work?  I noticed that I had to set a temp directory in the mytharchive settings.  I created a temp folder in /var/lib/mythtv/temp.  Do I have to do anything else to get it to work?  I tried exporting a recording and went through the usual steps but when it gets to the Log Viewer nothing happens.  It doesn't seem to be running any scripts like it's suppose to do.  Do I need to change the shared folder to anything as well?

---

### Post by axelsvag on 2007-11-01
My experience is that the folder have to in a place or have rights for the user mythtv or your own user. If you place the tempfolder in the home folder it should work or change the rights for /var/lib/mythtv/temp

---

### Post by dmfrey on 2007-11-01
I would be interested to know others experiences with MythArchive.  I have been having issues, specifically with HDTV Recordings and running them through MythArchive.  This is mostly with the Audio being out of sync.  It doesn't appear to affect SDTV recordings, however.

I think this affects Transcode as well as myth archive as I see similar issues when I just transcode an HDTV recording.  Transcoding to MP4 produces a much smaller file, but it also produces audio that is slightly out of sync and very choppy video playback.  By choppy I really mean intermittent flashing that occurs on transitions.

MythArchive, with transcoding turned on or off, produces a very nice dvd of the recording, but the audio is way out of sync.  I thought I had a fix by removing the --fix_sync flags in mythburn.pl.  I noticed in the logs that it was doubling the 'Fixing audio offset...".  By removing the flags, I now only see 1 message per recording during the multiplexing step.  Also the audio sync was better, but it is still not right.  I have had to resort to grabbing an avi from bittorrent for the recording I want to archive.  It is not the greatest either, but it is much better thank not being able to archive them at all.

Dan

---

### Post by Meph1st0 on 2007-11-01
Being completely new to linux I'm guessing the command to add rights to the /var/lib/mythtv/temp folder for user mythtv would be something like: chmod ...something?

---

### Post by axelsvag on 2007-11-02
As I said the easy way to do this, is to change the folder that mytharchive look for. 
Start to create a new folder inside /home/"youruser name". If you do that it, mythtv automatically gets the rights to write to that folder. Then change the information in mythfrontend/mytharchive so it looks in the new folder you just created.

---

### Post by Meph1st0 on 2007-11-02
The only thing about puting the folder in /home is that I only allocated 10GB to my / root partition.  How much space do I need for my mytharchive temp folder?  I wanted to put it in my /var/lib/mythtv folder since I know I've got plenty of space for it.

Last night I actually ran "gksudo thunar" and just opened the folder properties and added read & write permissions to the mythtv user account.  That seemed to be good enough as now I can actually see that it's running a script in the Log Viewer.  

Although, for some other reason, that I haven't determined yet, I still can't seem to burn a recording to disk.  Are there some logs I can look at to see where it errored out?

---

### Post by dmfrey on 2007-11-03
I believe the two logs for mytharchive are mythburn.log and progress.log.

---

### Post by Meph1st0 on 2007-11-22
The solution to this thread can be found here: [http://ubuntuforums.org/showthread.php?t=610856](http://ubuntuforums.org/showthread.php?t=610856)

---


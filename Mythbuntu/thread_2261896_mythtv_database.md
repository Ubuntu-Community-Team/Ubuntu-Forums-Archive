---
title: "mythtv database"
date: 2015-01-21
forum: Mythbuntu
---

### Post by deanie44 on 2015-01-21
Hi everyone.  I am doing a fresh install of Ubuntu 14.01 with MythTv.  I would like to have same mythtv database.  Unfortunately when I restore the database, I do not have any recordings or tuner cards.  I changed my username.  Is that the problem.  I have tried several times to follow instructions of the following website:
[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore). but I cannot get it to work,  What am I doing wrong?  Any help will be appreciated.  deanie44

---

### Post by nainsurvolte on 2015-01-21
Seems like we are on the same boat...

If you did like me (see here: [http://ubuntuforums.org/showthread.php?t=2261821](http://ubuntuforums.org/showthread.php?t=2261821)) which is basically back up the database, install the new mythtv (I made a fresh install of mythbuntu 14.04) your next step would be to do that:

```
[COLOR=black][FONT=monospace]mythconverg_restore.pl --drop_database --create_database --directory [Your directory where you have the backup] --filename [mythconverg backup file name].sql.gz[/FONT][/COLOR]
```

That is assuming you wish to keep the complete database as is and that your backup went well.

If you had some corruption in it prior to the backup ( as I had) you can also employ that

```
[COLOR=#000000][FONT=monospace]mythconverg_restore.pl --partial_restore --directory [Your directory where you have the backup] --filename [mythconverg backup file name].sql.gz[/FONT][/COLOR]
```

But then although everything seems back to normal, I have some trouble now with the link between the files and the recorded show entry in the database.

If you tried them ... then you will need to be more specific on what you get as error message or don't get and/or describe exactly what you are doing.

---

### Post by deanie44 on 2015-01-22
Hi	 nainsurvolte. Thank you for answering my post.  I restored a mythtv database backup from another host--deanie56.
I installed mythtv on ubuntu-gnome with the host name of sakkie56.  I had to manually redo the storage groups and turner cards.  Here's the thing--I have no audio what so ever.  I tried VLC to play the recording files and still no audio.  I receive an error message stating that oss cannot find the file or directory.  I have a hdmi cable attached to my tv.  Any help will be appreciated.  deanie44

---

### Post by nainsurvolte on 2015-01-22
If your problem is the audio, or the lack of audio, I would advise to change the title. The database is on the backend and their is absolutly no need to configure audio on a backend except if it also acts as a frontend. And even so, if the issue is with the frontend, you would most probably have an issue with the frontend configuration, not the database.

In my case, my frontends are Kodi machines and I barely configure Mythtv frontend if I ever install/use one.

Other point, through what action does VLC open the video file in the first place?
Do you go through a Mythweb and select ASX stream?
Do you open directly the video file with VLC (File\Open) on the machine or through the network?

---

### Post by deanie44 on 2015-01-24
Hi I downloaded VLC from the software center.  The problem was in the frontend.  It is solved.  Thank you. deanie44

---


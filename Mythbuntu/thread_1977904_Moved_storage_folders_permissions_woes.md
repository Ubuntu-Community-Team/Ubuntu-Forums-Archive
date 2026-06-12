---
title: "Moved storage folders permissions woes"
date: 2012-05-10
forum: Mythbuntu
---

### Post by singedwings on 2012-05-10
I have moved the location of my storage folders, by mounting the /var/lib/mythtv to /media/MythTag with ```
//192.168.0.5/MythTag /media/MythTag cifs auto,username=tv,password=****,uid=1000,umask=000,user 0 0
``` in /etc/fstab. This has resulted in the folders being not writable by myth - permission problem. ls -l of /var/lib/mythtv ```
drwxrwsrwx 2 mythtv mythtv  36864 May 11 01:22 banners
drwxrwsrwx 2 mythtv mythtv  73728 May 11 01:22 coverart
drwxrwsrwx 2 mythtv mythtv   4096 May  5 11:31 db_backups
drwxrwsrwx 2 mythtv mythtv  69632 May 11 01:22 fanart
drwxrwsrwx 2 mythtv mythtv   4096 May 11 02:15 livetv
drwxrwsrwx 2 mythtv mythtv   4096 Apr 10 10:49 music
drwxrwsrwx 2 mythtv mythtv   4096 May 11 01:22 recordings
drwxrwsrwx 2 mythtv mythtv 311296 May 11 01:22 screenshots
drwxrwsrwx 2 mythtv mythtv   4096 May 11 01:22 streaming
drwxrwsrwx 2 mythtv mythtv   4096 May 11 01:22 trailers
drwxrwsrwx 2 mythtv mythtv   4096 May  5 19:34 videos
``` but the mounted /media/MythTag has ```
drwxrwsrwx 2 tv mythtv 0 May 11 01:22 banners
drwxrwsrwx 2 tv mythtv 0 May 11 01:22 coverart
drwxrwsrwx 2 tv mythtv 0 May  5 11:31 db_backups
drwxrwsrwx 2 tv mythtv 0 May 11 01:22 fanart
drwxrwsrwx 2 tv mythtv 0 May 11 02:15 livetv
drwxrwsrwx 2 tv mythtv 0 Apr 10 10:49 music
drwxrwsrwx 2 tv mythtv 0 May 11 01:22 recordings
drwxrwsrwx 2 tv mythtv 0 May 11 01:22 screenshots
drwxrwsrwx 2 tv mythtv 0 May 11 01:22 streaming
drwxrwsrwx 2 tv mythtv 0 May 11 01:22 trailers
drwxrwsrwx 2 tv mythtv 0 May  5 19:34 videos

```How do I get the mounted user and group to be mythtv? Or is this all wrong?

---

### Post by klc5555 on 2012-05-11
Open a prompt and
```
sudo chown -R mythtv:mythtv /media/MythTag
```

This should allow mythtv to access the MythTag directory structure. But there may still be glitches depending on what the owner:group of /media itself is. As a root directory you may have set it up root:root, or (if your username is "tv") you may have it set up as tv:users These variants (particularly the first) will cause problems.

If you have nothing non-mythtv under /media you may wish to set the whole /media directory structure to mythtv:mythtv

Permissions glitches are the main rationale for having all myth-related media mounted under Mythbuntu's default /var/lib/mythtv/... Sometimes when I want userspace programs (like, say XBMC or what have you) to seamlessly access one of these directories (usually /var/lib/mythtv/videos or ../music) I'll keep the media mounted under /var/lib/mythtv/[whatever] per the default and create a symlink to the whole end directory in my userspace, so my /var/lib/mythtv/videos gets symlinked to /home/[mydirectory]/videos. But there are a lot of workable options here.

---

### Post by singedwings on 2012-05-11
Fixed it but myth still thinks it is broken.

First off I should point out that I am using Lubuntu 12.04 with myth 0.25fixes. I was trying to get to grips with fstab and then I checked the users and groups. I noticed that my username was not ticked in the mythtv group?? This has resolved the problem I can watch livetv etc, even with the permissions as```
drwxrwxrwx  13 tv mythtv    0 May 11 01:16 MythTag
``` however the mythbackend log still reckons the directories are unwritable even though they are. Just in case you are wondering /media/MythTag/livetv and others folders normally in /var/lib/mythtv are the only entries in the storage group settings.

Thank you for your help.

---

### Post by klc5555 on 2012-05-11
> **singedwings said:**
> Fixed it but myth still thinks it is broken.

First off I should point out that I am using Lubuntu 12.04 with myth 0.25fixes. I was trying to get to grips with fstab and then I checked the users and groups. I noticed that my username was not ticked in the mythtv group?? This has resolved the problem I can watch livetv etc, even with the permissions as```
drwxrwxrwx  13 tv mythtv    0 May 11 01:16 MythTag
``` however the mythbackend log still reckons the directories are unwritable even though they are. Just in case you are wondering /media/MythTag/livetv and others folders normally in /var/lib/mythtv are the only entries in the storage group settings.

Thank you for your help.

Mythbackend log entries are likely being generated because mythtv expects the whole path to the ../recordings directory to be owned mythtv:mythtv

You're probably able to watch livetv despite this because it appears the ../MythTag/... directory group is set to wide open permissions 777, universally readable/writeable/executable by everybody, which is not generally recommended for a machine that connects in any way to the net. 

Usually the mythtv-accessible directories would be set to 755, which would leave it read-write-execute by the owner (preferrably "mythtv") and root, but read-only for everyone else. 775 is also possible, extending read-write-execute also to the whole mythtv group, but keeping the non-group read-only. 

These permission options would help keep the bad guys out of your machine, but would require the entire mythtv recording directory structure ownership set to "mythtv:mythtv" in order to function.

If at some point you notice yourself having strange recordings scheduling, mythtv user job executing, or archive glitching problems that you can't otherwise account for, keep in mind that one of mythtv's routines or associated utilities may have had difficulties with the non-standard ownership/permissions on the path to the ../recordings directory.

---

### Post by singedwings on 2012-05-11
Thank you I shall keep it in mind, and thanks again for your help.

---

### Post by synapseattack on 2012-05-19
Thanks for this thread. I think I've been having the exact same problem since I started playing with 12.04 mythbuntu. I mounted a esata drive to store everything on and I made symlinks from /var/lib/mythtv/recordings (etc)  to /media/esata/mythtv/recordings (etc). As long as the actual destination folder on the esata drive has the same permissions it should still work right?

---

### Post by singedwings on 2012-05-19
Like I said for me myth still thinks it does not work, but so far for me no problems. However you may wish to glance at [http://ubuntuforums.org/showthread.php?t=1982364]("http://ubuntuforums.org/showthread.php?t=1982364")as my moving the folders does cause some metadata issues.

---


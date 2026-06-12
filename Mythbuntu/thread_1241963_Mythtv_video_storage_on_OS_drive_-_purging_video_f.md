---
title: "Mythtv video storage on OS drive - purging video files"
date: 2009-08-16
forum: Mythbuntu
---

### Post by narunas on 2009-08-16
Here is my issue:
Was running MythTv set-up well till the OS drive space came to an absolute 0. (of course, RTFM, put videos somewhere else but the OS drive).

I was under impression that "expiring Live TV stuff would keep the drive clear of all the Live recordings - suppose it did not.

I have now removed/purged/cleared mythtv manually, with deb manager and removed anything to do with mysql server and db's - my space is still >1% available.

/var/lib/mythtv - empty
/var/log/mythtv - empty

Is there anything that can be done to clear these orphan files or a complete system rebuild is in order. It is a major inconvenience for me to rebuild - and if I do - not sure I would ever again consider something as problematic as MythTv.

Thx 
Narunas

---

### Post by NTolerance on 2009-08-16
The way foward right now is to get more information to pinpoint the exact cause of your disk usage problem.  Assuming that you're running GNOME, my suggestion is to go to Applications->Accessories->Disk Usage Analyzer and select the "Scan Filesystem" option.  This will give you a graphical display of which directories are taking up space and exactly how much space is being consumed.  

We can't assume that MythTV is the source of this problem until we get more information.

---

### Post by narunas on 2009-08-16
replying my own thread here - feeling so relieved with the fix!

the orphaned mythtv files were here:

/root/.local/share/Trash/files$ 

to list the largest files on the /dev/sda1 I used this command :

sudo find / -type f -printf "%k %p\n" | sort -rn | head -10

the above will attempt to list the top ten largest files on the drive - some permission would need to be played with, of course -

then you would need to navigate to that Trash folder, temporarily changing permission on the way. 

/root/.local/share/Trash/files$ sudo rm *.mpg

this does the trick for the .mpg files
same for the .png 's


If there is a OS functionality to clear the shared resources and trash - please let me know!

Narunas

---


---
title: "userjobs"
date: 2014-10-31
forum: Mythbuntu
---

### Post by deanie44 on 2014-10-31
Hi everyone.  I did a userjob in Mythbuntu(cp "DIR"/%FILE%""/var/lib/mythtv/recording/%TITLE% - %SUBTITLE% - %STARTTIME%.mpg").  The files were copied to the directory, Unfortunately  when I did a new install and restored the database and recordings the files could not be found.  Does anyone know why this is not working?  Any help will be appreciated.  deanie44

---

### Post by aelfric55 on 2014-10-31
Well, at the very least you're reproducing title/subtitle text info as part of a file name. This works directly only if your title/subtitle has no spaces or special characters that would have to be escaped out if entered from a console as part of a Linux file name. For this in a user job, %TITLE%-%SUBTITLE% needs to be in quotes "%TITLE%-%SUBTITLE%". Or "%TITLE%"-"%SUBTITLE%"  Single quotes (') would work too, until the first time your title included some apostrophe word like "O'Reilly".

So I might try a test of a job that looks a bit more like```
cp %DIR%/%FILE%   /var/lib/mythtv/recording/"%TITLE%-%SUBTITLE%"-%STARTTIME%.mpg
``` No spaces on either side of the dash in front of %STARTTIME%

---

### Post by dannyboy79 on 2014-10-31
could you clarify what the goal was because i think you're making this harder than it needs to be. the database contains the information of where the file is located and all it's metadata like date, channel, time, etc etc. For example if you setup a storage group and used /var/lib/mythtv/recordings/ within that directory there could be 3242-35245452454325.mpg on a particular host. 

if you migrated your mythtv install to a new server/hardware or new mythtv version and you restored the database than mythtv is expected the files to be in the same location. within mythtv-setup do you have the same storage groups defined? i don't really understand what your goal was for using the cp command?

---

### Post by deanie44 on 2014-10-31
Thank you aelfric55 and dannyboy79 for answered my post.  The user job that I am using makes the files unusable in the database--/home/deanie56/programs/Haven - Nowhere Man - 20141025010000.mpg. I would really like to make a userjob the copy the files to usb hdd in case my database or operating system gets corrupt.  Thanks again.  deanie44

---

### Post by dannyboy79 on 2014-11-01
ok, so you want a copy made of your recordings and stored them off onto a usb drive and be able to understand the filename? if so, then maybe you could use mythlink.pl as your userjob which will create a symlink in a human readable form to whereever, could be /tmp/recordingcopies and then you could setup a rsync command to copy them from /tmp/recordingcopies onto your usb drive. i know it's a round about way of doing it but unless you want to use sometihng like mythweb and just download them one by one and store them on your usb drive is a possible other solution also. the mythlink.pl settings are here: [https://www.mythtv.org/wiki/Mythlink.pl](https://www.mythtv.org/wiki/Mythlink.pl)

---

### Post by aelfric55 on 2014-11-01
> **deanie44 said:**
> Thank you aelfric55 and dannyboy79 for answered my post.  The user job that I am using makes the files unusable in the database--/home/deanie56/programs/Haven - Nowhere Man - 20141025010000.mpg. I would really like to make a userjob the copy the files to usb hdd in case my database or operating system gets corrupt.  Thanks again.  deanie44

The userjob I use myself for a similar purpose puts the recording in a properly named folder, while leaving the recording file itself with its original unchanged filename inside the folder. Where the path and directory I save things to is called simply "/videostaging", the command line for the job is this:```
mkdir /videostaging/"%TITLE%"-"%SUBTITLE%";cp %DIR%/%FILE%  /videostaging/"%TITLE%"-"%SUBTITLE%"/%FILE%
```  

To protect against the potential loss of the database, you'd have whatever your daily mysqldump-based database backup script is put an extra copy of this daily backup also on the drive where you're storing the recordings.

---


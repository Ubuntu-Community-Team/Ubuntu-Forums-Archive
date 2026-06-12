---
title: "Something is Deleteing My Coverart"
date: 2009-11-15
forum: Mythbuntu
---

### Post by uncle hammy on 2009-11-15
OK, I am going to say straight up, I have not figured out WHAT is doing this....

About once a week, all of my fanart and coverart is deleted from their respective folders.  I am not using storage groups, because all my DVD rips are Video_TS or ISO.  

The only other piece of information I can offer is this.  I have a couple DVD rips that are .vob files, and for those 4 only, the cover/fan art is NEVER deleted...only all my Video_TS/ISO stuff is.

Anyone have any idea what's going on?  I have had to resort to keeping a backup of everything, and once a week copying it all back over.

---

### Post by tgm4883 on 2009-11-15
Jamu might be doing it. I think there is a mythvideo cron job for it in /etc/cron.weekly/

---

### Post by uncle hammy on 2009-11-15
I think you're right.  I found the log file /var/log/mythtv/jamu.log from reading the mythvideo entry in cron.weekly.

I that log file, I can see entries "Deleted Coverart Files"....then a big list of files.

So the question is, WHY??????  What does it not like about my Video_TS / ISO video entries that it thinks it's ok to delete all my artwork?

---

### Post by uncle hammy on 2009-11-15
OK, in piecing together what the jamu script does, my best guess is that because a VIDEO_TS entry is stored in the mythtv db with a filename entry that is just a directory (no extension), jamu sees it as an "orphan" because it doesn't match "known" extensions.  

For now, I have just removed the -J argument from the call to jamu.py in /etc/cron.weekly/mythvideo

If I find the time, I suppose I can find the place in jamu.py where it actually figures out what to delete.  Rather than deleting based on extensions (I think that's what it's doing), it would proabably be far more prudent to (and simpler for that matter) to simply delete files that don't have an entry in the coverfile or fanart column of the db.

I.E. (in pseudo "code" for clarity)
```

#loop through all the files in the coverart directory
# check to see if the current file has an entry in the db
SELECT * FROM videometadata
WHERE coverfile LIKE '%currentfile.Name'

#if a row was found, leave the file alone, otherwise delete it
# do the same thing for fanart

```

---

### Post by RDV on 2009-11-15
> **uncle hammy said:**
> OK, in piecing together what the jamu script does, my best guess is that because a VIDEO_TS ... 

I am the developer of Jamu, please supply a directory listing of the files in one of your VIDEO_TS directories.

I suspect you are right the VIDEO_TS files are being ignored so that when jamu is trying to account for graphics that are NOT orphaned the coverart and fanart is not being removed from the orphaned graphics list.

With a directory list I will be able to emulate the situation and develop a resolution.

I am surprised that iso files have the same problem. Please give me a single file name of one of your iso files.

In the mean time your solution of stopping the weekly Jamitor (-MJ) cron job is correct.

Thanks

Doug

---

### Post by uncle hammy on 2009-11-16
Thanks for the reply.  So, it would look something like this....

The myth db would have a filename of /media_storage/videos/XMEN

that directory would have 2 directories in it AUDIO_TS & VIDEO_TS

AUDIO_TS is pretty much always empty, and VIDEO_TS looks something like this....

drwxrwsrwx 2 mythtv mythtv        139 2009-03-11 20:31 .
drwxrwsrwx 4 mythtv mythtv         36 2009-03-11 21:48 ..
-rwxrwxrwx 1 mythtv mythtv       6144 2009-03-11 20:31 VIDEO_TS.BUP
-rwxrwxrwx 1 mythtv mythtv       6144 2009-03-11 20:31 VIDEO_TS.IFO
-rwxrwxrwx 1 mythtv mythtv      65536 2009-03-11 20:31 VTS_01_0.BUP
-rwxrwxrwx 1 mythtv mythtv      65536 2009-03-11 20:31 VTS_01_0.IFO
-rwxrwxrwx 1 mythtv mythtv 1073739776 2009-03-11 20:31 VTS_01_1.VOB
-rwxrwxrwx 1 mythtv mythtv 1073739776 2009-03-11 20:31 VTS_01_2.VOB
-rwxrwxrwx 1 mythtv mythtv  615458816 2009-03-11 20:31 VTS_01_3.VOB

In looking back, I misspoke.  ISOs are one of the files NOT being deleted.

---

### Post by RDV on 2009-11-16
uncle hammy,
   I know what the problem is and will need a different approach to eliminating graphics from the orphan list. That will take at least a few days. 

Until you see that a patch was committed please do not use the Janitor -MJ option or cron job as previously discussed.

When the patch has been created and committed I will post back on this thread.

Doug

---

### Post by uncle hammy on 2009-11-16
Thanks!

---

### Post by RDV on 2009-11-20
uncle hammy,
    FYI: I am finally getting to the fix discussed in this thread. It will still be a few days as additional changes need to go along with this patch. Just wanted to let you know that this issue has not been forgotten.

---

### Post by elgordo123 on 2009-11-20
Great - that happened to me multiple times and seriously freaked me out.  I though it was a ext4 thing - still a little leary about ext4 - thank goodness it's not.   So glad I had a backup - it took a very long time to assign those coverart images to my collection. 

Please let us know when you have a fix.

Note:  This should really be stickied until it gets fixed!

---

### Post by RDV on 2009-11-24
uncle hammy,
The fixes for the Jamu -MJ (Janitor) function erroneously deleting artwork for VIDEO_TS videos has been released to 0.22+fixes and trunk. Jamu v0.6.0 see: [http://svn.mythtv.org/trac/changeset/22899](http://svn.mythtv.org/trac/changeset/22899)

These changes are available right now in 0.22+fixes and trunk but will take a day or two to be available for Mythbuntu daily updates. See: [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)

You can try the jamu janitor function safely with the simulation option. Jamu will go through the motions but not actually do any deletions. 
> ./jamu -MJVs

If you find that the changes has corrected the issues in this thread then please rename the thread as [SOLVED] so others can find the solution.


The release includes these changes:
1) Changed The Janitor -MJ option to deal with graphics associated with a VIDEO_TS directory.
2) Stopped Jamu from processing any video files in a "VIDEO_TS" directory as it was leading to multiple  MythVideo entires for *.VOB files. Jamu does not process multi-part videos. Use MythVideo to add metadata for VIDEO_TS directories.
3) Added the use of PID files to prevent two instances of the same Jamu -M options running at the same time. This deals with issues when a meta data source is off line for an extended period of time and Jamu runs as a cronjob. Options effected are (-M, -MW and -MG).
4) Change to have jamu use the TMDB Movie title as is done in MythVideo rather than the file name.
5) Fixed a bug when TMDB genres are filtered and none remain they were still being added. This bug was spotted and correct by Mathieu Brabant (thanks).
6) Added the ability for a user to filter additional characters from a file name this is important for users using MS-Windows file systems as a CIFS mount. See the jamu-example.conf "filename_char_filter" variable.

Doug

---

### Post by uncle hammy on 2009-12-21
Sorry it took so long, I kinda lost track of this thread :)  Thanks for your work, I'll check it out.

Seems to be correct now!  Thanks again.

---

### Post by larsolav on 2010-01-04
I believe I updated my combined BE/FE recently, several fixes were applied (including the fix to the weird sound sync problem). I also followed the advice here: [http://www.baablogic.net/drupal/node/7](http://www.baablogic.net/drupal/node/7). I then went to download all the meta data for my ISOs using the "i" button. Then, yesterday (the next day) all the cool coverart stuff was gone! Anything in particular I should be looking for?

---


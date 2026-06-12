---
title: "Copy recorded shows from one HDD to another"
date: 2011-01-01
forum: Mythbuntu
---

### Post by Barry_IA on 2011-01-01
[FONT=Palatino Linotype]Hi Folks!

The process is probably a lot more simple than my imagination is allowing; did see some threads that were close but not quite.

What I want to do is copy my recorded shows from one hard drive to another.  What I had done is:

- Had Mythbuntu 10.04 installed on a 6 GB drive; the recordings on a 1 TB drive (/var).

- After months of no problems started having problems, so figured may as well upgrade to Mythbuntu 10.10.  Know from previous experience an install wipes the storage hard drive.  Didn't want to loose my programmes (recorded TV shows) so unplugged the 1 TB drive and temporarily installed a 2 TB drive.

- Installed Mythbuntu 10.10 on the 6 GB drive (performed a disk wipe first), using the 2 TB drive as /var.  (The 1 TB was unplugged - on purpose to save the data.)

So now what I want to do is copy the shows from the 2 TB drive to the 1 TB drive so I can remove the 2 TB drive and use for something else (like a back up!)  Is it as simple as issuing a COPY command (guessing *cp*, though also seen *dd*), or is there a little more involved because of all the data on the show's title, date recorded, etc., etc. etc.???

The 1TB and 2 TB drives are part of the same computer (in the same case).

TIA!  And please keep it simple and use somewhat expanded explanations as I am a newbie to Linux.

[/FONT]

---

### Post by nickrout on 2011-01-01
I assume you backed up your database before you re-installed, and have restored it.

So simply add all the directories that you want to hold recordings to the default storage group and it will be fine.

---

### Post by newlinux on 2011-01-02
Yes as mentioned above to get all the program information you will need to restore the database, and to be able to access teh recordings you will need to copy them to a directory specified in a storage group. The only thing I'll add is that to copy I recommend you use the rsync command. If your permissions are already correct on the files you are going to copy you might want to try something like:

```
rsync -pogvvPh <original_recordings> <new_location>

```
This will preserve the permissions and show you the progress of your copying and show if there were any errors in the copying. It has a lot of options (type man rsync for more info). cp will work okay as well, but I prefer rsync for these situations.

---

### Post by Barry_IA on 2011-01-02
> **nickrout said:**
> I assume you backed up your database before you re-installed, and have restored it.

[FONT=Palatino Linotype]Actually no.  What I did was unplug the (original) 1 TB drive and 'substituted' the 2 TB drive -- which now I have the funny feeling was not a Good Thing.  At the time was thinking all the programme information was with the shows on the /var director (on the 1 TB drive).  

The OS is on the 6 GB drive which was wiped and then a fresh install of Mythbuntu 10.10 was done.  (Some problems had developed, I think from having the slow 1.5 Mbps DSL service and some updates not completing due to time out.)
[/FONT]


> So simply add all the directories that you want to hold recordings to the default storage group and it will be fine.[FONT=Palatino Linotype]At worse I'll have to wait until summer for the reruns![/FONT]

---

### Post by Barry_IA on 2011-01-02
> **newlinux said:**
> Yes as mentioned above to get all the program information you will need to restore the database, and to be able to access teh recordings you will need to copy them to a directory specified in a storage group. The only thing I'll add is that to copy I recommend you use the rsync command. If your permissions are already correct on the files you are going to copy you might want to try something like:

```
rsync -pogvvPh <original_recordings> <new_location>

```This will preserve the permissions and show you the progress of your copying and show if there were any errors in the copying. It has a lot of options (type man rsync for more info). cp will work okay as well, but I prefer rsync for these situations.

[FONT=Palatino Linotype]I think I'll follow someone's advice who knows a lot more about these types of things and use *rsync*!
 
If the original recordings on the 1 TB drive are gone/not retrievable, well, guess just watch them during the summer!  (Or via the Internet.)
 [/FONT]

---

### Post by newlinux on 2011-01-03
The original recordings will be retrievable, but without the database restore myth won't know what to do with these files (it won't have any information on them). You'd have to import them manually back into myth manually or name the files properly and import them into mythvideo and scan for metadata. All of the metadata about recordings and videos in mythtv is stored in the database.

I believe by default mysql DBs are store in /var/lib/mysql - so you still may have a chance to get the DB and restore it if your /var was on the 1TB drive.

---

### Post by nickrout on 2011-01-03
you should also have the weekly backups of the database that mythbuntu saves for you. Look for files named mythconverg-1254-20101003064807.sql.gz or similar. ```
locate -r mythconverg.*gz
```

---

### Post by Barry_IA on 2011-01-04
> **newlinux said:**
> The original recordings will be retrievable, but without the database restore myth won't know what to do with these files (it won't have any information on them). You'd have to import them manually back into myth manually or name the files properly and import them into mythvideo and scan for metadata. All of the metadata about recordings and videos in mythtv is stored in the database.

I believe by default mysql DBs are store in /var/lib/mysql - so you still may have a chance to get the DB and restore it if your /var was on the 1TB drive.

[FONT=Palatino Linotype]Could you post the command to scan for the metadata?  Thanks!  

And just to doublecheck,  as I understand it the old TV show files would be relocated to the "Watch Videos" section.  These are the recordings on the original 1 TB drive (was disconnected during the installation of 10.10.)  

The TV shows currently on the 2 TB drive (intended as temporary) will be copied to the 1  TB drive and will still appear in "Watch Recordings" because the metadata thing is on the 6 GB "Operating System" drive.

(Not trying to confuse the issue, just realize what I did is probably a little unusual.  I'd rather ask questions and be certain than later get a "oh, we thought you did...")
[/FONT]

---

### Post by Barry_IA on 2011-01-04
> **nickrout said:**
> you should also have the weekly backups of the database that mythbuntu saves for you. Look for files named mythconverg-1254-20101003064807.sql.gz or similar. ```
locate -r mythconverg.*gz
```

[FONT=Palatino Linotype]Thanks!  The wildcard search will be a lot simpler![/FONT]

---

### Post by newlinux on 2011-01-04
> **Barry_IA said:**
> [FONT=Palatino Linotype]Could you post the command to scan for the metadata?  Thanks!  

And just to doublecheck,  as I understand it the old TV show files would be relocated to the "Watch Videos" section.  These are the recordings on the original 1 TB drive (was disconnected during the installation of 10.10.)  

The TV shows currently on the 2 TB drive (intended as temporary) will be copied to the 1  TB drive and will still appear in "Watch Recordings" because the metadata thing is on the 6 GB "Operating System" drive.

(Not trying to confuse the issue, just realize what I did is probably a little unusual.  I'd rather ask questions and be certain than later get a "oh, we thought you did...")
[/FONT]

Now you've confused me. Metadata for all shows (recordings and those in mythvideo) are stored in the database. If you have restored your database or if it never was gone then you won't need to rescan anything. Just copy the old recordings to a storage group that you've defined in mythtv-setup and all the metadata that was there before will be there again (all files that were recordings should be in a recordings storage group, and all files that were in Videos before should be in a videos storage group or share).

Or are you saying you  have the metadata for recordings you've made since you reinstalled on the 6GB OS partition but don't have any earlier data? In that case, even if you find the old database it will be a bit tricky to integrate them. If your plan is to take the old recordings and put them in mythvideo it may take some time. Scanning for metadata on files from recordings will be useless because the names used by default for recordings are numeric combinations of the channel ID in the DB and the date and time of the recording. The default metadata scanners use the title of the filename. You'd need to either rename all the files appropriately or modify the title of each file appropriately in the metadata and then scan.

In myth .24, once you scan the files into mythvideo (Press the m key in mythvideo and select scan for changes) it will automatically scan all files for metadata (but it won't find anything unless you used mythlink.pl before in your old install to give the recordings more user friendly namees). So the key is to properly name/title the files and then scan for metadata. You can rescan all the files for metadata using jamu (google it for more info if you go that route) or you can individually scan files for metadata by pressing the "w" key while a video is selected in mythvideo.

---

### Post by newlinux on 2011-01-04
> **Barry_IA said:**
> [FONT=Palatino Linotype]Thanks!  The wildcard search will be a lot simpler![/FONT]

Just reminder, if you do find your old DB and do a basic restore, you'll lose the metadata you have for your current recordings (they won't even show up in the recordings screen). It will overwrite your current information.

---


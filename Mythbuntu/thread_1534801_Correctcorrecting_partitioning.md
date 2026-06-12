---
title: "Correct/correcting partitioning"
date: 2010-07-20
forum: Mythbuntu
---

### Post by Macka01 on 2010-07-20
When I installed Mythbuntu 10.04, I was sure to make a partition for videos; I mounted it to /recordings - this created some permission problems which I fixed easily enough.

I had some issues with my installation (couldn't log in) and reinstalled. Being in a hurry (I had to record Days of Our Lives - don't ask) I decided to mount the partition to /var/lib/mythtv
The dialogue warned that if it was a system directory /usr/ etc/ var it would be formatted; I assumed that this would be fine as it wasn't /var and wasn't really a system folder.

Installation went smoothly (unlike the first time I installed 10.04) I booted the sstem to find all the recording I had were gone - no great loss.

What I want to know is was the loss of data due to:

[LIST=1]
[*]Changing the mounting point with the installers partition editor
[*]The position of mount point (/var/lib/mythtv)
[*]The installer clearing out/setting up the /var/lib/mythtv folder
[/LIST]
I want to avoid this problem next time, so if I know the cause then perhaps next time I can avoid it and keep the videos (and hopefully the auto DB backups too).

Also, if it is due 1 then then I think I should probably remount the partition and create symbolic links.

---

### Post by newlinux on 2010-07-20
I'm not sure I follow exactly what you did, but if you used the installer and changed the mount point from /recordings to /var/lib/mythtv AND you told it to reformat - that would have erased everything on what was previously your /recordings partition. All you really need to do was remount it after installing. There was also no reason you couldn't have kept it mounted as /recordings.

---

### Post by Macka01 on 2010-07-20
> **newlinux said:**
> I'm not sure I follow exactly what you did, but if you used the installer and changed the mount point from /recordings to /var/lib/mythtv AND you told it to reformat - that would have erased everything on what was previously your /recordings partition. All you really need to do was remount it after installing. There was also no reason you couldn't have kept it mounted as /recordings.

The only partition I elected to format was the system partition
Size        Mount point
10GB      /
10GB      SWAP
920GB    /recordings

I was in a hurry and did not want to have to reconfigure Myth TV to use the /recordings/* folders, so I changed the mount point to /var/lib/mythtv I also had to activate the partition as the default was not to mount it. I deleted the system partition and recreated it, which automatically ticked the format box. The former /recordings partition was not set to format. Which is why I am a little confused as to why I lost the recordings.

---

### Post by newlinux on 2010-07-20
Reconfiguring myth to use a different (or additional) directory than default for recordings is a less than 5 minute process with storage groups. If you didn't want to do that, you could have just had the installer ignore the /recordings partition and remount it yourself to /var/lib/mythtv after installing (for future reference if you want to avoid this). If you changed the mount point of the partition that used to be /recordings to /var/lib/mythtv during installation and you reformatted / - that could reformat what was your recordings partition. I still can't tell from what you are typing if that's what you did.

---

### Post by Macka01 on 2010-07-20
> **newlinux said:**
> Reconfiguring myth to use a different (or additional) directory than default for recordings is a less than 5 minute process with storage groups. 

I am aware of this, I was in a hurry and was cutting corners and simplifying things - not that it is likely to have made any difference because of the way I handled partitions.

> **newlinux said:**
> If you didn't want to do that, you could have just had the installer  ignore the /recordings partition and remount it yourself to  /var/lib/mythtv after installing (for future reference if you want to  avoid this).

That's a good point, I'll remember it for next time.

> **newlinux said:**
> If you changed the mount point of the partition that used  to be /recordings to /var/lib/mythtv during installation and you  reformatted / - that could reformat what was your recordings partition. I  still can't tell from what you are typing if that's what you did. 

That is exactly what I did, sorry if I'm being unclear. Ok, next time I'll go back to the old system of /recordings and setup a symbolic link between /var/lib/mythtv and /recordings

I'm basically wanting to keep the recordings off the main partition, after learning the hard way what a pain it was to backup all of the videos.

Thanks for your help, I think I've learnt a fair bit and I'll keep it in mind next time I need to perform a clean install/upgrade.

---

### Post by newlinux on 2010-07-20
You're welcome - glad I could help. I keep most of my recordings across my various backends in directories called /storage (usually they are separate drives), and then just add them as storage groups. I don't symlink them to /var/lib/mythtv. It's easy enough to do backups from /storage if I want to. If you get it all setup properly and then just save your DB you can do a clean install with the same partitions and restore your DB and not have to set anything up again

What pains did you run into with backups?

---

### Post by Macka01 on 2010-07-20
> **newlinux said:**
> You're welcome - glad I could help. I keep most of my recordings across my various backends in directories called /storage (usually they are separate drives), and then just add them as storage groups. I don't symlink them to /var/lib/mythtv. It's easy enough to do backups from /storage if I want to. If you get it all setup properly and then just save your DB you can do a clean install with the same partitions and restore your DB and not have to set anything up again

What pains did you run into with backups?

Unfortunately I don't have the luxury of multiple mythboxes and just run a single back end/front end, which is ok, you can only hear it when it is silent, you don't notice it at all if the TV is on.

I was thinking with the symlink I could get all directories including /var/lib/mythtv/DB backup, I have never actually checked the backup folder, but as far as I know it should auto backup - there is definitely an option to disallow auto backups in the backend settings. That's something I need to look in to I think.


The problem I had with backups was that the first time I installed MythTV (first time for installing and using linux too), I just used the MthTV installer defaults to partition my drive ie there was only a system and swap partitions. SAMBA was broken and I didn't have a portable (or otherwise) harddrive that was large or fast enough to copy the videos. So what I did was to go through and delete anything that was unwanted, then double check the comm flags and then transcode everything. After that I used MythWeb to download each video to my computer across 100Mb ethernet.

It took 2 days to do the whole lot, but it was worth it in the end.

If I had used my portable HDD I would have had to copy ~10 files to it at a time with a speed of around 12MB a second and then copy them on to my other computer at the same speed. Using MythWeb had the advantage of it naming the files properly instead of with MyTVs naming standard, which looks suspiciously like epoch time, though I don't think it is.

---

### Post by newlinux on 2010-07-20
My point about backing up and restoring applies whether you have one or multiple backends. If I want to keep my media with reinstalls or upgrades the key is to keep them on a separate partition and backup my DB. That partition isn't touched when I install or upgrade. 

Are your referring to autobackups of your videos/recordings? the only thing I know that is configurable to autobackup within myth's setup is the DB, which is relatively small.

When you had that backup problem were you building a new box and wanted to port recordings over or where you wanting to upgrade the existing box?

Where DB backups occur is configurable. you aren't constrained to doing them in /var/lib/mythtv/DB Backup. And once you set it up once, if you backup your DB regularly, you don't have to set it up again in the next install, you just restore your DB and all your settings are back. Make sure to keep media files on a separate  partition and restore your DB when you do a new install. You don't even have to worry about the filenames as when you restore your DB myth will retain all the metadata (including commercial flagging information) for those files (even if your recording directory is different). I'm guessing you figured all that out  which is why you now have a separate partition. You'd probably be better off backing up your DB to a partition separate from your root partition too. What I'm not understanding is what you need symlinks for.

Myth files are named based on the station id in the mythDB, and the date and time of the recording (cCHANID_YEARMONTHDATEHOUR...)

---

### Post by Macka01 on 2010-07-20
> **newlinux said:**
> Are your referring to autobackups of your videos/recordings? the only thing I know that is configurable to autobackup within myth's setup is the DB, which is relatively small.

I was referring to autobackups of the DB.

> **newlinux said:**
> When you had that backup problem were you building a new box and wanted to port recordings over or where you wanting to upgrade the existing box?

I was wanting to upgrade the existing box. I was originally going to copy the video across and backup the DB, but due to the restraints (SAMBA no longer working and portable HDD being too slow) I decided to just grab the videos I wanted and start completely fresh.

> **newlinux said:**
> Where DB backups occur is configurable. you aren't constrained to doing them in /var/lib/mythtv/DB Backup. And once you set it up once, if you backup your DB regularly, you don't have to set it up again in the next install, you just restore your DB and all your settings are back. Make sure to keep media files on a separate  partition and restore your DB when you do a new install. You don't even have to worry about the filenames as when you restore your DB myth will retain all the metadata (including commercial flagging information) for those files (even if your recording directory is different).

I haven't noticed a setting for the location or frequency of DB backups, but I will definitely have another look.

> **newlinux said:**
> I'm guessing you figured all that out  which is why you now have a separate partition. You'd probably be better off backing up your DB to a partition separate from your root partition too. What I'm not understanding is what you need symlinks for.

That's correct, I realised that it would be an issue when I did want to upgrade, but by that time I had several hundred gigs of video and didn't care to risk the whole system by repartitioning the drive.

With the symlinks I was planning on doing the following:
1) creating a partition mounted to /recordings/mythtv
2) moving the folders from /var/lib/mythtv to /recordings/mythtv
3) deleting /var/lib/mythtv
4) symlinking /var/lib/mythtv to /recordings/mythtv
5) writing a script that would delete /var/lib/mythtv and create the symlink mentioned in 4. The script would be stored in /recordings

Steps 1-5 would only ever be done once.
When I reinstalled the system I would be able to run the script to quickly setup the folders via a sym link.

However with DB backups the symlinks wouldn't be necessary, as the settings could be set once and stored.

> **newlinux said:**
> Myth files are named based on the station id in the mythDB, and the date and time of the recording (cCHANID_YEARMONTHDATEHOUR...)

That makes a lot of sense.


I am wondering though if I should use gparted to remount my partition under /recordings and then change the backend settings accordingly, or, will this create DB problems because the video has been moved?

When a video is played on the front end, does the backend look for the file in all video sources, or does it already know where to expect the file to be?

---

### Post by newlinux on 2010-07-21
I'd change the location of the mounted drive using the /etc/fstab file. If you add a storage group for /recordings and move files there myth will still find them as if you never moved them. You can move files to different storage groups without any problems. The frontend asks the backend to find the file, and the backend searches it's storage groups for the actual file. there is no need for you to do the symlink shuffle :) if you just want to move your recordings. That's exactly what storage groups are for. You could just add the /recordings storage group and move all the files to the separate partition, and then delete the storage group /var/lib/mythtv/recordings from mythtv-setup and you're done. you can similarly add storage groups for non-recordings as well, although there are some complications if you use external players.

I have a script that I run as a cron job to backup my DB (I have other databases I backup too so it's just easier to consolidate) so I never use myth's capability and can't help much there (assuming it exists). I believe you can use MCC to configure automatic backups (I think daily) and there is a DB backups storage group configurable in mythtv-setup (same place you'd add /recordings as a storage group for recordings). the official mythtdb backup script is mythconverg_backup.pl

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

---


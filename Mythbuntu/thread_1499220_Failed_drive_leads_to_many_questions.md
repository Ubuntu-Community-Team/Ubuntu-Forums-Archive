---
title: "Failed drive leads to many questions"
date: 2010-06-01
forum: Mythbuntu
---

### Post by waltm on 2010-06-01
I have been using mythbuntu mostly as a file server (no tuners installed) and moving all my dvds onto 1tb drives. Each drive formatted to jfs if I remember correctly and is just mounted as an individual drive (/media/video1, /media/video2, etc.). I've started on my fourth drive and just had my first drive fail on me. This is a considerable loss of time to re-rip all the movies. If I can get it to mount again are there any ways to recover some of the data on it if copping fails?

Is there a better way to handle storage like this in the future? Raid 5 perhaps, or is it not worth the effort? My understanding is I could grow the array to add new drives but if I were to get errors on multiple drives all would be lost.

Is there a way to read out the myth database and list all the files that were stored on that drive? Even a list of everything that I can cross out the ones on the other 3 drives would help.

If it makes a difference on setting up storage going forward I'm planning on moving my back end from my desktop case (which can't handle any more drives) to a rack unit in the basement. I have an IBM xseries eserver 236 that was given to me to run the back end. It's loaded with Ubuntu 10.04 to work out the bugs as this will be my first headless install.

I could use some suggestions on a drive mounting solution to hold SATA drives in the rack as well as tying everything together. SATA controller in the server to port multipliers in another case for the drives is one option I'm considering. Any other suggestions that might work out better?

One last question, is there an easy way to move the server from my current computer running 9.10 (myth .22) to the new one running 10.04 (myth .23)?

---

### Post by nickrout on 2010-06-01
The question of backing up media files is a vexed one. Many people say "it's only TV" and don't bother. The doubling of the storage requirements is the big bugbear. Raid can be a good solution, but there is the added hardware heat and complexity.

To discover what was on that disk try something like:

```
SELECT title,filename FROM videometadata WHERE filename LIKE '%/media/video1%';
```from within the mysql commandline of course.

If you want to put that in a file, run this from your normal commandline:

```
mysql -u root -p mythconverg -e "SELECT title,filename FROM videometadata WHERE filename LIKE '%/media/video1%';"> myvideolist
```

In relation to migration, you should back up your existing database and then restore it to the new system. The gory details are here:

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)


PS I would be encoding my DVD's to h.264 to massively reduce storage requirements.

PPS you don't need mythtv for serving media files. OK so if you want to do the tuner thing in future you are on the right track, but if you want to only ever use it as a fileserver, consider using XBMC as your front end and access your files over CIFS or NFS :)

---

### Post by tgalati4 on 2010-06-01
What was the model of the drive?  Consumer drives can fail after heavy writing sessions.  The heads get hot and delaminate causing failure.  The other issue is burn-in.  Did you do any burn-in for the new drives?  I run badblocks on my new drives to work them in a little before storing data.

RAID5 can work if you have enterprise-class drives and real RAID hardware.  Consumer drives with fakeRAID means you will spend even more time doing data recovery.

---

### Post by ian dobson on 2010-06-02
Hi tgalati4,

I don't totally agree with you. I've been running a RAID5 array for many years (mdadm controled) and even though drives have died (not more than a non-raided drives), and I've never lost data.

My main mythtv recordings drive what on 3 x 2Tb wd drives, about 3months ago I added a fourth drive, grew the array then grew the file system (3.8tb -> 5.8tb usable). Growig the array took about 14hours (still with the file system mounted/recording programs) and resizing the fs only took about 15minutes.

Note RAID is not a backup method, if you delete a file by mistake then is gone, even if you have a ARID array you still need a backup system.

Regards
Ian Dobson

---

### Post by nickrout on 2010-06-02
> **ian dobson said:**
> Hi tgalati4,

I don't totally agree with you. I've been running a RAID5 array for many years (mdadm controled) and even though drives have died (not more than a non-raided drives), and I've never lost data.

My main mythtv recordings drive what on 3 x 2Tb wd drives, about 3months ago I added a fourth drive, grew the array then grew the file system (3.8tb -> 5.8tb usable). Growig the array took about 14hours (still with the file system mounted/recording programs) and resizing the fs only took about 15minutes.

Note RAID is not a backup method, if you delete a file by mistake then is gone, even if you have a ARID array you still need a backup system.

Regards
Ian Dobson

It is still insurance against catastrophic drive failure. Backing up proper seems almost insurmountable once you accumulate a few TB of media data. If I spent more money on disks it would inevitably hold more data, not more backups :)

Then again I am a media kleptomaniac.

The OP still has the original DVD's which constitute his 'backup' :)

---

### Post by ian dobson on 2010-06-02
> **nickrout said:**
> It is still insurance against catastrophic drive failure. Backing up proper seems almost insurmountable once you accumulate a few TB of media data. If I spent more money on disks it would inevitably hold more data, not more backups :)

Then again I am a media kleptomaniac.

The OP still has the original DVD's which constitute his 'backup' :)

Hi,

If your data is valuable enough then you can invest money in backups. I have 6 2tb wd drives, 4 in a RAID5 array for recordings and the other two in a RAID1 (strip) as backup.

The backup drives where "cheap" at about 150euro each, that's not alot of money for a good bit of security. After backuping I remove the drives from their hot swap bays and store them in my celler, which is a atom bunker (don't ask, Swiss law was that every house has to have a bunker),

Regards
Ian Dobson

---

### Post by matt06 on 2010-06-02
> **nickrout said:**
> The OP still has the original DVD's which constitute his 'backup' :)
I'd say not having to manually insert and rip each disc over again must add some value to backing up a 4TB dvd collection. ;)  Granted, doubling your storage requirements isn't easy on the wallet either.

[QUOTE=ian dobson]Many people say "it's only TV" and don't bother.[/QUOTE]
True, it comes down to how you use your htpc.

Personally, the majority of shows I record are replayed many times by the networks and it is "just tv", but there are some unique showings that warrant saving.  Musical performances, sports finales, etc.  I also may let an entire season of a show record before watching a single episode and I would miss all of them in the case of a major drive failure.

---

### Post by waltm on 2010-06-02
Thanks for all the feedback.  I was able to finally mount the drive after cooling it down with a fan outside the case and started moving files onto a new drive.

> **nickrout said:**
> 

If you want to put that in a file, run this from your normal commandline:

```
mysql -u root -p mythconverg -e "SELECT title,filename FROM videometadata WHERE filename LIKE '%/media/video1%';"> myvideolist
```



I'm going to have to keep this around. I would like to keep a list of what I have done already and be able to print it out.  I used to use DVD profiler (under windows) before switching to hard drive storage and liked the ability to print out reports but I haven't updated that since 1/2008.  [http://www.invelos.com/DVDCollection.aspx/wjm]("http://www.invelos.com/DVDCollection.aspx/wjm") Would there be any sort of GUI utility to make custom reports from the database?



The drives I have are Samsung, 3 F1 (1tb), 1 F2 (1tb) and a new F3EG (2tb).  I didn't do any prep prior to using the drives.  I'll start on the next one I get.  Looks like I'll have to get 3 drives next time and set up a software raid.



I have done a database restore using those directions in the past but wasn't sure if that would work with a myth .22 backup being restored on myth .23 (or .24 depending on how long I put it off).  Is that all that is involved in the move, other than the drives mount points, etc.?  Would this carry the passwords as well or would I have to change the front ends to match the new setup?

---


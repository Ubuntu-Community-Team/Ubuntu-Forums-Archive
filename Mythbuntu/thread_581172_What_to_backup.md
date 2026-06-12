---
title: "What to backup??"
date: 2007-10-19
forum: Mythbuntu
---

### Post by dmfrey on 2007-10-19
I am looking to do a nightly backup of my mythbuntu box to my server.  I am looking to compile a list configuration files, etc. that would be useful in restoring the machine, should something happen to it.

The database backups are a given.  ( I actually would like to work on replicating it to my server, but that is another story ).

Any suggestions?

---

### Post by superm1 on 2007-10-19
this really depends on how automated of a restoration you are targeting.  The database is setup currently to backup already via a cron job, but I believe its a weekly backup rather than a nightly.  You probably just need to move that cron job over from cron.weekly to cron.daily.

So now if you are looking for a backup that you can literally press a key and restore the entire drive, I almost think you are better off using a full out rsync of the entire system partition.  Most installations are only 1-1.5gb so this is doable especially if you use compression.

Comparatively, you probably can get away with backing up  ~, as well as any config files that you have to tweak post installation.  All the information about your tuners, storage areas, etc are all stored in the mysql database.  You might want to record the options you chose during installation to make sure you remember to set them up next time, but otherwise I think this is the way to go.

---

### Post by dmfrey on 2007-10-19
My intension is to use rsync for a backup.  

I will take a look at the size of the system partition and see if there is anything else that needs to be backed up.

Luckily, the music and pictures are already on that server. The server has a mirrored raid configured.

---


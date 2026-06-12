---
title: "Backups: am I missing anything?"
date: 2009-08-25
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-08-25
I've recently been trying to make sure I have a comprehensive backup strategy in place.

This is what I've done so far:

Daily backups of the MySQL database using mysqldump, resulting files saved in /var/backups

Entire contents of /var/backups (ie the above backups of the database, plus whatever else Mythbuntu puts in there by default, backed up daily to an external hard drive.

Contents of /var/lib/mythtv backed up daily to external hard drive (ie all my pictures, recordings, videos, and music).

Contents of /home/mythtv backed up daily to external hard drive (not sure if there's anything of great importance in there, but if nothing else it contains the cover art for my movies).

Does that cover all the important things, or is there anything else I'm really going to wish I had backed up if it all goes tits up? I'm using the machine only for its MythTV functions: there's no email or anything like that.

Thanks
NM

Mythbuntu 8.10

---

### Post by stevanbt on 2009-08-25
Hi,
How about the OS?  This may only be required before applying fixes?

Also, are you backing up the DB while myth is running?  If so is the backup ok?

Thanks, Steve.

---

### Post by klc5555 on 2009-08-25
> **NautiusMaximus said:**
> I've recently been trying to make sure I have a comprehensive backup strategy in place.

This is what I've done so far:

Daily backups of the MySQL database using mysqldump, resulting files saved in /var/backups

Entire contents of /var/backups (ie the above backups of the database, plus whatever else Mythbuntu puts in there by default, backed up daily to an external hard drive.

Contents of /var/lib/mythtv backed up daily to external hard drive (ie all my pictures, recordings, videos, and music).

Contents of /home/mythtv backed up daily to external hard drive (not sure if there's anything of great importance in there, but if nothing else it contains the cover art for my movies).

Does that cover all the important things, or is there anything else I'm really going to wish I had backed up if it all goes tits up? I'm using the machine only for its MythTV functions: there's no email or anything like that.

Thanks
NM

Mythbuntu 8.10

Recorded contents and DB --you've got the important stuff. From this you can reconstruct a mythbox with everything safe and in place (or transfer to a new mythbox). If your recording directories, etc. are on separate drives from the OS, then the OS itself, its drive, and mythtv could melt down to slag and require no more of a restore (once the OS and mythtv are installed on a new drive) than just restoring the DB, since the recordings would remain untouched on their separate drives. 

Your daily database backup routine hopefully keeps a week's worth of database backups (at least). Sometimes, a really fatal unrepairable flaw in mythconverg doesn't get noticed or diagnosed for a few days --a shame if today's backup of a faulty mythconverg has overwritten a good one from yesterday, or 3 days ago. Mythbuntu also deposits its own once-weekly mythconverg backups in /var/backups

Anyway, the only thing that I would add is that if you have boatload of specialized scripts collected to handle various OS or mythtv tasks, you might want to make sure they're backed up to a safe place from time to time, to avoid the nuisance of re-collecting/re-writing/re-editing them. Ditto with the source for any specialized drivers you may have compiled, where the exact source may be difficult to retrieve again later (for example, a particularly successful daily snapshot of  V4L source, or a favorite rare successful version of ffmpeg).

And, to my mind, wherever your recordings are, or a backup of your recordings, that's where an additional copy of your database backup needs to be kept. Just two things that really ought to be kept together, because one without the other becomes ... troublesome.

Otherwise, you've covered everything. I don't think backing up the OS itself is particularly useful. I've always preferred a new, clean installation after a disaster.

Cheers! :)

---


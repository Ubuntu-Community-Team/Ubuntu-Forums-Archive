---
title: "Backend update question"
date: 2010-09-16
forum: Mythbuntu
---

### Post by justNiz on 2010-09-16
I have a box running a fairly old version of mythbuntu (not really sure but I think its the version based on ubuntu 9.10)

I've avoided doing any package updates, especially to a newer version of mythtv because it took a non-trivial amount of effort to get mythtv configured properly, mostly around getting all the tv channels figured out and set up with the correct XMLTV ids (I'm using schedules direct).

I'd now really like to update my backend as I also now have a laptop running ubuntu 10.04 that I want to run a myth frontend on, but am getting a protocol version mismatch error with my older myth backend. I'd also like to get this figured out so I can generally stay current too.

If I tell the package manager to update mythtv to the latest repository version, will the update also screw up/wipe out/invalidate the mysql mythtv database so I'll loose all my channel assignments, currently recorded shows, recording rules etc?

If so, is there a (simple) way to save and then restore the database contents before/after the update? Can I assume that if changes have been made to the database schema, it will still be 'backwards compatible' with my saved/restored data from an earlier version?

---

### Post by ian dobson on 2010-09-17
Hi,

When you update to a new version of mythtv, the first time the the new version starts, it'll see that the database schema is old and do an automatic update. All your channel data/recordings remain untouched.

An "easy" way to backup the database is to go to the terminal prompt and type:-

mysqldump -uUSER -pPASSWORD --all-databases --opt | bzip2 > /path/to/backupfile.bz2

I've updated my backend several times now (started with 8.10/MythTV 0.19) and am now running 23.1-fixes. Just reserve a day for the updates as it does take sometime :)

Regards
Ian Dobson

---

### Post by andree_b on 2010-09-17
Instead of dumping the whole mysql databases manually you could use the scripts provided by MythTV for this task:

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

I think recent Mythbuntu installation will backup your DB anyway on a regular schedule (daily?).

But anyway you only need the backups if the upgrade will fail.

---

### Post by nickrout on 2010-09-17
> **andree_b said:**
> Instead of dumping the whole mysql databases manually you could use the scripts provided by MythTV for this task:

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

I think recent Mythbuntu installation will backup your DB anyway on a regular schedule (daily?).

But anyway you only need the backups if the upgrade will fail.

precisely, use the provided tools!!

I think the default backup is weekly, see /etc/cron.weekly/mythtv-database

---


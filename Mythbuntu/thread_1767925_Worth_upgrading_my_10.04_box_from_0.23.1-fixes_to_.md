---
title: "Worth upgrading my 10.04 box from 0.23.1-fixes to 0.24.1?"
date: 2011-05-26
forum: Mythbuntu
---

### Post by bcg30506 on 2011-05-26
Now that the current TV viewing season is over, I'm thinking of updating my box.  I currently run mythtv 0.23.1-fixes under mythbuntu 10.04.  I want to stay on 10.04 of the OS but was wondering if it is worth the process to bring mythtv up to 0.24.1.

What would I gain versus what I may lose?  Any risks or should it be fairly straightforward using the update manager?  I already have the repository manager installed & configured, and I've backed up my entire system.

Thanks for any opinions or advice.

---

### Post by superm1 on 2011-05-26
It's quite easy to do.  Just install mythbuntu-repos (if you haven't already) and then choose 0.24 in MCC or in the debconf popup when you install.  If you don't have MCC installed, dpkg-reconfigure mythbuntu-repos will let you re-pick.

Once you pick the 0.24 repo, apt-get update && apt-get dist-upgrade and you've got 0.24.

As for changes, look through  [http://www.mythtv.org/wiki/Release_Notes_-_0.24](http://www.mythtv.org/wiki/Release_Notes_-_0.24) and decide if any of it is worthwhile for you.

---

### Post by bcg30506 on 2011-05-26
Okay, thanks.  I already have mythbuntu-repos installed and configured to 0.23.1-fixes but can reconfigure it to 0.24.1 as mythbuntu 10.04 does seem to support it. :)

That is a long release note.  Glancing over it, it seems there are some things I'd like and others I may not.  So I'm tempted to try it with the thought I can go back if need be.

So, how hard would it be to go back?  I've fully backed up the machine, OS and all with rsync from / to a USB drive.  I've also backed up the database using mysqldump.  If I don't like 24 and want my old system back, can I just use mysql to reimport the sql file mysqldump saved to get my old database back then copy the OS partition back from the USB drive using rsync to restore the 0.23.1-fixes?

It sounds like it should work, but I need verification from others before I dive in.  Please help.

---

### Post by nickrout on 2011-05-28
Use the provided tool, not mysqldump, to do your db backup. [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

One thing, any recordings you do in 0.24 will be orphaned if you go back to the backup database - ie the files will remain on disk but with no metadata.

---

### Post by bcg30506 on 2011-05-28
nickrout, thanks for the tip.  I was not aware of those tools although I did notice the mythconverg tar backup files showing up each time apt-get did a myth update over the past year or so.

I use mysqldump as mythtv is not the only database on this machine, although for just upgrading mythtv, the others would not be affected.  If I recall, the upgrade uses this tool and creates a db backup file before running.  Cool.

I went ahead and bit the bullet and did the 0.24 upgrade.  It overall was fairly painless and very fast.  I know anything I record may be orphaned if I go back, but we are between TV seasons now so I figured it was the time to try it out.

Pretty good so far.  The DVD internal player crashes a lot, so I'm using mplayer dvdnav:// now to watch them.  Not liking the new themes so I still use mythbuntu's theme which is very clean.  The biggest pain was getting my HDHomeRun to work with both tuners which worked fine in 0.23 before upgrading.  Plus we use cable QAM for free HD that comes from 2 SD lineups, so that is a pain to manually configure xmltvid's, icons, etc.

I love the new Flash video player in mythweb that lets you FF/Rew and pause successfully now!  We use this all the time over an ssh tunnel when traveling and it was always frustrating to not be able to skip commercials or rewind to watch something missed before.  Nice job.

---


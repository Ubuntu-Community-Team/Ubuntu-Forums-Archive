---
title: "MythTV complete backup and restore process"
date: 2010-05-05
forum: Mythbuntu
---

### Post by colinnwn on 2010-05-05
So I've given up trying to fix my upgraded Mythbuntu combined FE/BE. I went from 9.10 to 10.04, and the computer has become unusably slow after the transition, though it technically works.

I was planning to delete the hard drive and install Mythbuntu 10.04 from scratch, then restore MythTV files to hopefully make it exactly like it was before, minus the slow.

I've read [http://www.mythbuntu.org/upgrading](http://www.mythbuntu.org/upgrading) and searched the mythtv.org wiki. It sounds like the backup and restore script only does the database. Unless you copy and restore the actual recording files, none of your old recordings will be there, right?

So to do this, I just need to copy and restore the /var/lib/mythtv/recordings directory. And if I want the Myth installation to work exactly like it did before, also copy and restore my LIRC config file? Is there anything else I need to do, or files I need to grab? I don't think I use any of the features/plugins of Myth besides scheduled recording and playing back TV.

Thanks.

---

### Post by Lepy on 2010-05-05
> **colinnwn said:**
> I've read [http://www.mythbuntu.org/upgrading](http://www.mythbuntu.org/upgrading) and searched the mythtv.org wiki. It sounds like the backup and restore script only does the database. Unless you copy and restore the actual recording files, none of your old recordings will be there, right?

So to do this, I just need to copy and restore the /var/lib/mythtv/recordings directory. And if I want the Myth installation to work exactly like it did before, also copy and restore my LIRC config file? Is there anything else I need to do, or files I need to grab? I don't think I use any of the features/plugins of Myth besides scheduled recording and playing back TV.

Correct. You need to run the backup script first, and place the file somewhere safe so you can restore the database after the fresh isntall. You also need to backup your storage dirs (/var/lib/mythtv/recordings + any others you may have specified in the mythtv-setup), or the mythtv database will reference and try to play non-extant files.

A good practice is to create a separate partition and mount it under /var/lib/mythtv/recordings so if you ever have to reinstall, you only need to wipe the partition containing /

Also, if you are already backing up all of your recordings, go ahead and backup then restore your /home directory as many program/mythtv setting files are stored there, including custom lirc maps.

However, you may be stuck with 10.04/.23 as you have probably already updated your database schema.

---


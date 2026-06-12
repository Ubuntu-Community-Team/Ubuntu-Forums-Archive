---
title: "Missing Recordings"
date: 2008-11-13
forum: Mythbuntu
---

### Post by ercle88 on 2008-11-13
I recently installed Mythtv, and for a few days it worked without any problems. However starting last night all recordings except one have no files. The one that does have a file i watched live. I have run a script to check the Database configuration against the file system (credit to Ian Dobson. script can be found here: [http://www.planet-ian.com/MythTV/CheckMythDB.txt](http://www.planet-ian.com/MythTV/CheckMythDB.txt) ) Don't know how to go about fixing this, so any help will be apriciated

---

### Post by klc5555 on 2008-11-13
> **ercle88 said:**
> I recently installed Mythtv, and for a few days it worked without any problems. However starting last night all recordings except one have no files. The one that does have a file i watched live. I have run a script to check the Database configuration against the file system (credit to Ian Dobson. script can be found here: [http://www.planet-ian.com/MythTV/CheckMythDB.txt](http://www.planet-ian.com/MythTV/CheckMythDB.txt) ) Don't know how to go about fixing this, so any help will be apriciated

Open a terminal and check the directories manually you have set as your default storage group. If there are big files in there ending in *.mpg and/or *.nuv, then your recordings are still all there, and everything is OK. If  there are no *.mpg or *.nuv files in these directories, then something has likely gone wrong with your disk or the file system on it and you're busted. Permissions should be OK to these directories --if mythtv couldn't read/write to these directories, you couldn't watch live tv, either.

Have you done a clean shutdown and restart since the problem started? I've had myth "lose" all my recordings from time to time, particularly after a lot of activity on the auto-expire list, only to have myth suddenly "find" everything again after a clean restart.

If, after a clean restart, your recordings are still "lost", then something has probably gone awry with the somewhat fragile mythconverg database. At this point I would restore my mythconverg database from my most recent backup, and use the myth.rebuilddatabase.pl script from the /contrib directory (or here: [http://svn.mythtv.org/svn/trunk/mythtv/contrib/recovery/](http://svn.mythtv.org/svn/trunk/mythtv/contrib/recovery/)) to add recordings to the database that were made since my last backup.

If you have just been running mythtv for some days, you may have never backed up your database, but you may also not have too terribly many recordings either, and you can use myth.rebuilddatabase.pl to add them all back in. The script will require the libtimedate-perl package to run, if it's not already installed. The script will check each unknown recording against schedule information (which mythtv saves for 10 days), and if it doesn't find schedule information, allows you to type in data information. The script will also offer to commercial flag each recording as it re-adds it, which takes some time. The process works perfectly with recordings from analog sources, but occasionally has trouble with dvb sources, so that if your restored dvb recording cannot be skipped through properly when played back, you may later have to use "mythtranscode --buildindex --mpeg2" on these affected dvb recordings manually to give them usable indexes.

Thereafter be sure to set up a daily database backup as soon as possible, as described in: [http://mythtv.org/wiki/index.php/Backup_your_database](http://mythtv.org/wiki/index.php/Backup_your_database)
and other places. It will save you untold grief down the road. I usually end up relying on my stash of daily backups every month or so.

Good luck! :)

---

### Post by ercle88 on 2008-11-14
Thanks for the help. Not sure what did it, but it started working again later that afternoon. The recordings from that evening seem to be lost, but at least it is working now

---

### Post by klc5555 on 2008-11-14
> **ercle88 said:**
> Thanks for the help. Not sure what did it, but it started working again later that afternoon. The recordings from that evening seem to be lost, but at least it is working now

Your recordings from that evening are almost certainly still there. Use the myth.rebuilddatabase.pl script to add them back into your "post-amnesia" database. 

All the best!

---


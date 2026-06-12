---
title: "Clean install with database transfer"
date: 2010-10-17
forum: Mythbuntu
---

### Post by tonycollinet on 2010-10-17
I am currently running 0.21 with 9.04 (I think) 

I want to upgrade with a clean install of 10.10, but without losing the recordings (which are on a separate hard disk)

What is the best way of doing this (transferring the recordings database, or saving the files as videos with appropriate filenames)

And is there a howto anywhere.

Thanks.

---

### Post by andree_b on 2010-10-19
I did this with MythArchive [http://www.mythtv.org/wiki/MythArchive](http://www.mythtv.org/wiki/MythArchive) - the created raw/native archives contain all metadata and can be imported back in fresh install.
But might be only feaseable if you have only a few recordings to transfer.
 
You might as well upgrade your current system to 10.10 (or just MythTV to 23.1 via autobuilds if that is available for 9.04), make a DB backup [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore) and make a clean install afterwards and restore saved DB.

---

### Post by tonycollinet on 2010-10-19
Myht archive sounded good, but then I read......

> Run the top level configure script for mythplugins with --enable-mytharchive added to the list of parameters to make sure MythArchive will be compiled. Then compile and install the plugins in the usual way. 

Unfortunately like much Linux documentaiton - it assumes a level of knowledge ("the ususal way") which I don't posess.

Or is this already pre-installed in mythbuntu?


Regarding the second approach - can I just backup the data base, do a fresh install, then restore the database - or does the database need conversion? If conversion is required, how is that done?

Thanks for any help.

---

### Post by ahood on 2010-10-19
> **tonycollinet said:**
> I am currently running 0.21 with 9.04 (I think) 

I want to upgrade with a clean install of 10.10, but without losing the recordings (which are on a separate hard disk)

What is the best way of doing this (transferring the recordings database, or saving the files as videos with appropriate filenames)

And is there a howto anywhere.

Thanks.

Hello,

Last Saturday (3 days ago), I upgraded from Mythbuntu 8.04 LTS to Mythbuntu 10.04 LTS. I too was concerned and did not want to lose the recorded program information.

The basic steps I took were the following:
1. Backed up the mysql database using the mythconverg_backup.pl script onto a separate partition/disk (see [Clean Install of Mythbuntu, keeping old database]("http://www.mythbuntu.org/upgrading#")).

*Note: This will backup both backend and frontend settings information, which includes recorded program information.*


2. Copied /etc/fstab onto a separate partition/disk. Write down any customized directories that stores myth recordings, music, pictures, or video.

*Note: Step 2 can be skipped if there is only a single disk with a single partition and the default storage directories are used. Because I do not store recorded shows in the default directory (/var/lib/mythtv/), but rather in directories under /mnt that point to a separate partition/disk (e.g., /mnt/videos points to a separate disk that only contains videos ripped from DVD). *


3. Copy any other directory that contains information specific to your system. For example, I had video jacket images of DVDs I had imported stored in my user home directory.


4. If a single disk with a single partition is used, then back up all mythtv media (tv recordings, music, pictures, videos, etc.) onto a separate partition/disk.

*Note: This step is a must if only a single disk with a single partition is used.*


5. Do a clean install of Mythtv.

*Note: I could view most but not all of each of the installation screens on my TV (50" plasma), which was probably due to a resolution issue. I got through it and after the system rebooted, the resolution was not an issue.*


6. After rebooting, the first thing is to update the system, then restore the same storage folders if the defaults are not used by creating the storage folder and editing /etc/fstab so that the storage folder points to the correct disk/partition.


7. Restore the database following the instructions at [Clean Install of Mythbuntu, keeping old database]("http://www.mythbuntu.org/upgrading#").


I ended up with an updated system that had the correct recorded program information, backend and frontend settings. There was some tweaking I did due to new features.

Report back your experience and have fun! :)

---

### Post by tonycollinet on 2010-10-19
Thanks ahood

Just the info I was looking for. 

Will give it a go.

---

### Post by ahood on 2010-10-19
No problem.

A few tips for things that could happen and solutions.

1. If the frontend says that it cannot connect to the backend due to the database password is no longer current, re-install mysql-server and you will be prompted to enter a new password.

2. If you receive a message that the database is of a previous version and gives the option to update to a newer version, do the update.

---

### Post by andree_b on 2010-10-20
> **tonycollinet said:**
> Myht archive sounded good, but then I read......
 
Unfortunately like much Linux documentaiton - it assumes a level of knowledge ("the ususal way") which I don't posess.
 
Or is this already pre-installed in mythbuntu?
 
 
Regarding the second approach - can I just backup the data base, do a fresh install, then restore the database - or does the database need conversion? If conversion is required, how is that done?
 
Thanks for any help.
 
Mytharchive is included in mythbuntu - you will find it under CD/DVD menu entry in the frontend since it originally was intended to backup to DVDs.
 
DB must be converted therefore you should upgrade your current (running) system first since the conversion is done during upgrade - and backup than and re-install afterwards. 
Probably conversion is also done when you backup the old (not-converted) DB and restore it in new install but I am not sure this will work when you skip a release.

---

### Post by tonycollinet on 2010-10-20
OOps 

Too late - clean install nearly done. Old database backed up - lets hope it can convert it.......

If not - well never mind. I'll just copy the recordings to videos and we'll have to work out which is which.

---

### Post by Senkoboy on 2010-10-20
> **tonycollinet said:**
> OOps 

I'll just copy the recordings to videos and we'll have to work out which is which.

Been there, done that :lolflag:

---

### Post by tonycollinet on 2010-10-20
Uh oh - not booting up - will start new thread.

Thanks for all help so far.

---


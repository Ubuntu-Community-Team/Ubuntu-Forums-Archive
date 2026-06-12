---
title: "Clean install old database"
date: 2010-07-28
forum: Mythbuntu
---

### Post by axelsvag on 2010-07-28
I had a major problem with my setup (mythbuntu 8.04) so I was forced to make a reinstall. I choosed to make a clean install to mythbuntu 10.04 and hoped my database was possible to use on the new setup. installation went fine and the system worked as it supposed to, until I tried to use the old database according to this instructions [HTML]http://www.mythbuntu.org/upgrading[/HTML]. After that I got the message that the database was to old and had to be upgraded. I went through the mythbackend and said yes and all looked fine at the mythbackend. But when I try to connect to the frontend I get the message that the database is to old 40 behind or something and will not work until I go through the mythbackend. The problem is that I just did that in it did not seems to solve everything. Do I have to reinstall a 8.04 version to be able to use my old database?

---

### Post by klc5555 on 2010-07-28
I'm not certain about the best or the simplest way. I'm sure others will suggest some more elegant ones, in which case disregard the following.

But if all else fails, there are some ugly and brutal approaches that should get the job done. One of which is:

Temporarily reinstall 8.04 (or install 9.04, which is still at Mythtv 0.21) for the moment. (Or make a separate small temporary partition for this temporary 8.04 install). Restore your old database to this old version. Keep your backed-up copy of the database too, of course. Do a version upgrade(s) of this temp 8.04 (9.04) installation via Upgrade Manager until you get to 10.04 You don't actually have to really configure any intermediate Mythbuntus. The database version gets upgraded along with everything else. When you get to the current Mythbuntu version, back up the newly upgraded database, which should be at the correct version. Then wipe this version-upgraded 10.04 installation, do a clean 10.04 install the way you want (if necessary; or remove the temporary partition), and restore the freshly-done 10.04 database backup to this clean 10.04 install. And it should be fine, the database being already the correct version.

As I said, probably not the best way, but likely sufficient.

---

### Post by axelsvag on 2010-07-28
Ok it was my thought unfortunately I can not find any mythtbuntu 8.04 or 8.10 just a 9.04. Maybe I have to try that even if it is not that promising. Maybe someone have a mythbuntu 8.04 desktop amd64 iso-file laying around?

---

### Post by klc5555 on 2010-07-28
Canonical used to store old Mythbuntu versions along with Ubuntu's closer siblings. Apparently not any more.

But Mythbuntu 8.04.1 is evidently still downloadable from Softpedia:

[http://linux.softpedia.com/progDownload/Mythbuntu-Download-27771.html](http://linux.softpedia.com/progDownload/Mythbuntu-Download-27771.html)

Otherwise, 9.04 is close enough that the databse ought to work. I restored a backed-up db from 7.10 to 9.04 without incident when I upgraded a year ago.

---

### Post by axelsvag on 2010-07-28
I will start the long march towards 10.04. The first 9.04 ended up with a initrams error on boot so I looked in my old boxes and found an old 9.04 mythbuntu I will try. I will come back later with a report.

---

### Post by axelsvag on 2010-07-28
Problems when I tried the 8.04 disc everything went well until I tried to make small installation. But....since the new big installation was made fresh for the 10.04 it was installed with ext4 and therefore the 8.04 installer refused to make space for the small 8.04 dist. So maybe I have to do a complete new installation with 8.04 and whole harddrive, my wife does not like me for the moment as I broke her favourite shows for the moment.

---

### Post by axelsvag on 2010-07-28
Next problem with a 8.10 disc I hit the 4Gb aperture error so the 8.10 was useless aswell. Back to the 9.04 disc. Take this story as a warning everyone else. The database is very valuable but soon I will give up and start from the beginning. I will be back

---

### Post by klc5555 on 2010-07-28
A small partition for temp 8.04/9.04 install could have been made with parted/gparted from 10.04 system, or using a PartedMagic disk, which includes an entire minidistro on the CD.

[http://partedmagic.com/](http://partedmagic.com/)

Sorry about the ext4 difficulties. Hadn't thought of that, since ext4 has drawbacks I'd just as soon avoid, all my various machines are on some combination of ext3, reiserfs, and xfs.

---

### Post by axelsvag on 2010-07-28
I took the hard way a complete new installation with 9.04  after gparted had made the disk free from ext4. And then I hope I will be able to insert the old database. I cross my fingers

---

### Post by axelsvag on 2010-07-29
The end of the story that maybe can be of interest for other newbees. I made a completely new installation of 9.04 imported the old 8.04 database. And it worked perfectly. Then I updated to first 9.10 and then to 10.04. Then I saved the database again and saved at least three copies of the database. After that I made a fresh install of the mythbuntu 10.04 and imported the newly created database and everything worked perfectly. So in the end the upgrade from 8.04 to 10.04 took 60 hours and if I would have been it little bit more thoughtful in the beginning it could have been done in 5 hours. The other learning was to save old versions of mythbuntu to be able to revert back if something bad happens so now I have 10 different versions saved for a rainy day.
All in all everything went fine.

---

### Post by newlinux on 2010-07-29
FYI:

You can upgrade directly from 8.04 to 10.04 ubuntu (LTS->LTS version) without going to the intermediate versions via update-manager. Also, I'm guessing something just went wrong with your first schema update when you installed 10.04 and imported your 8.04 (myth .21 most likely) DB. I did a clean install of 10.04 on my master backend (which was previously running 8.04) and then just imported the DB, did the database upgrade, checked it with the local mythfrontend, then upgraded all my other machines.

---

### Post by axelsvag on 2010-07-29
It would probably be the best but I must have done something that made it impossible to go directly from from 8.04 to 10.04.

---

### Post by nickrout on 2010-07-29
my 8.04->10.04 direct update failed and left my machine unbootable.

I then did a fresh 10.04 install and used the backup I had made of the database.

Did you religiously follow the instructions here:[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore) ??

---

### Post by axelsvag on 2010-07-30
No I did not. I followed this from this [HTML]http://www.mythbuntu.org/upgrading[/HTML] which obviously did not work for me.

> You can also backup your database and important files and do a clean install of Mythbuntu.
(excerpted and customized for Ubuntu from [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore))

    *  Execute backup script:

/usr/share/mythtv/mythconverg_backup.pl

Note: if your system doesn't have the necessary scripts, they may be obtained from SVN.

[http://svn.mythtv.org/trac/browser/trunk/mythtv/programs/scripts/database/mythconverg_backup.pl?format=txt](http://svn.mythtv.org/trac/browser/trunk/mythtv/programs/scripts/database/mythconverg_backup.pl?format=txt)
[http://svn.mythtv.org/trac/browser/trunk/mythtv/programs/scripts/database/mythconverg_restore.pl?format=txt](http://svn.mythtv.org/trac/browser/trunk/mythtv/programs/scripts/database/mythconverg_restore.pl?format=txt)

    * Save a copy of the resulting backup (which is usually the most recent file in /var/lib/mythtv/db_backups/) someplace that will survive reinstalls and/or disk failures. 
    * Perform Mythbuntu install or upgrade 
    * Stop the backend: 

sudo stop mythtv-backend

    * Obtain the mythtv password from here: 

grep DBPassword /etc/mythtv/config.xml

    * Delete old database and create a base new one: 

mysql -u mythtv -p -e "DROP DATABASE IF EXISTS mythconverg;"
mysql -u mythtv -p -e "CREATE DATABASE mythconverg;"

    * Copy the previously saved database to /var/lib/mythtv/db_backups/ and then execute the restore command:  
      Note: this restore can take a number of minutes for even average sized databases. 

/usr/share/mythtv/mythconverg_restore.pl --directory /var/lib/mythtv/db_backups --filename FILENAME

    * Start the backend again:

sudo start mythtv-backend

---

### Post by nickrout on 2010-07-30
well that should work as it pretty well summarises the page I pointed to (as it specifically says).

SO what exactly was the error after you followed the instructions? You said you got an error from a frontend ablout database version numbers:

[LIST]
[*]what exactly was the error message?
[*]I assume you had also updated the frontend? You need to be running the same version of mythfrontend as mythbackend.
[/LIST]

---

### Post by klc5555 on 2010-07-30
Since the original database malfunction has been solved, as a practical matter, the exact error messages and precise disposition of the frontend/backend upgrade for diagnostic purposes may be difficult to establish. 

Unless it's being proposed that Axelsvag attempt to "re-break" his correctly functioning machine to recreate the problem (?)

Better to wait and see whether the issue ever pops up again with anyone else. It may well have been a "one off" event.

---

### Post by newlinux on 2010-07-30
> **nickrout said:**
> my 8.04->10.04 direct update failed and left my machine unbootable.

I then did a fresh 10.04 install and used the backup I had made of the database.

Did you religiously follow the instructions here:[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore) ??

8.04-10.04 worked for me on 3 of my backends (after I learned an important lesson for my backend that it failed on). But there are a lot of variables in any supported in place upgrade from any version to another version so I'm sure this doesn't work for everyone. My  point was if you were going to start off with a clean install of an older version and install myth (the cleaner the system the better the chance of the upgrade working) you might be able to save some time starting with 8.04 instead of 9.04 if you are going to 10.04.

---

### Post by axelsvag on 2010-07-30
Yes I should have made a fresh 8.04 install and import the old database and then make the giant leap to 10.04. I feel so stupid now. The error I got said that the database was more than 40 times behind and therefore impossible to upgrade. And maybe I can try again to reproduce the error but right now my wife  is very suspicious if I try to do anything more with her beloved Mythtvbox.

---

### Post by newlinux on 2010-07-30
> **axelsvag said:**
> Yes I should have made a fresh 8.04 install and import the old database and then make the giant leap to 10.04. I feel so stupid now. The error I got said that the database was more than 40 times behind and therefore impossible to upgrade. And maybe I can try again to reproduce the error but right now my wife  is very suspicious if I try to do anything more with her beloved Mythtvbox.

IF it ain't broke... don't break it :) Leave it alone. I don't even install updates after I get the system working as I want it to(except for individual updates I deem I need). Especially since I've got multiple backends and frontends to maintain...

It's still weird to me that installing the old database on a 10.04 install didn't upgrade right, but hey you have it working now so no worries.

---

### Post by nickrout on 2010-07-30
> **klc5555 said:**
> Since the original database malfunction has been solved, as a practical matter, the exact error messages and precise disposition of the frontend/backend upgrade for diagnostic purposes may be difficult to establish. 

Unless it's being proposed that Axelsvag attempt to "re-break" his correctly functioning machine to recreate the problem (?)

Better to wait and see whether the issue ever pops up again with anyone else. It may well have been a "one off" event.

Sorry I didn't read the thread well enough and didn't realise it had been fixed!

---


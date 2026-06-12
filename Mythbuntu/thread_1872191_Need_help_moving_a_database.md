---
title: "Need help moving a database"
date: 2011-10-30
forum: Mythbuntu
---

### Post by donb21 on 2011-10-30
I need help moving the database of a working MythTv box (Mythdora12 - V-0.23-8.fc12 (r25413)) to a new Mythbuntu box (11.10).  I tried the backup/restore method here:

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

, but I ran into a couple of quirks with it; password changed, mythtv-setup exits unexpectedly, some screens take a very long time. 

Does anyone have suggestion on the right way to move a database to Mythbuntu?  Also, is there a way to re-run the database setup that ran during the installation?

---

### Post by nickrout on 2011-10-30
using the wiki page is the best (and really only) way.

If you want to re-run the database setup, use ```
dpkg-reconfigure <packagename>
```

---

### Post by donb21 on 2011-10-30
OK, I'll work with it and post my notes later.  On the reconfigure question, what is name of the package?  I tried:

sudo dpkg-reconfigure mythtv-setup - got errors
"Package `mythtv-setup' is not installed and no info is available."

sudo dpkg-reconfigure mythtv - didn't do anything, just came back to a prompt

---

### Post by newlinux on 2011-10-31
The package you might want to reconfigure is mythtv-database. Last week my primary backend crashed (mobo failure I think, haven't had time to troubleshoot it other than knowing it's not the disk (took that out). I mostly followed the wiki with a backup of my DB and transformed one of my existing secondary backends into a master.

Maybe if we knew about what steps you tried and the errors you are currently getting we could help you more.

---

### Post by donb21 on 2011-10-31
Actually the procedure is working, but it's pretty generic (not MythBuntu-specific at all).  Once I figured-out a couple things the errors mostly went away.  For instance, the re-create database step is:

 "mysql < mc.sql", but the correct syntax is:
[SIZE=2]
[/SIZE] [FONT=Verdana][SIZE=2]"mysql -uroot -p < /usr/share/mythtv/sql/mc.sql"
Enter password:[/SIZE][/FONT][SIZE=2]
[/SIZE] 
...and by the way, when I use that script, the mysql password changes to "mythtv", which should also be changed in the two text files on your home directory.

....details, details.  I think I have it mostly figured out, but if I hit a show-stopper, I'll be back.

---

### Post by GaryP2 on 2011-11-01
Did you simply try a full restore of the MythTV .23 database after you had the Mythbuntu 11.10 (MythTV .24) installed and running? Or did you have to do a partial restore for some reason (not recommended unless required according to the backup/restore wiki).
 
I assume that soon after the restore is applied, MythTV needs some time to convert the database. Would that have been the explanation why it didn&#8217;t look and work correctly right at first? Unless it&#8217;s a huge database, I would assume a moderate-sized database wouldn&#8217;t take that long to convert (from .23 to .24).
 
I&#8217;m interested in knowing how this goes for you in that I&#8217;m preparing to do almost the same thing &#8211; move from a stable Mythbuntu 10.04 (MythTV .23) to a Mythbuntu 11.10 (MythTV .24) system. In my case, I bought a new hard drive and hope to be able to do a clean install of 11.10 on the new drive, then restore the .23 database on top of that finally move over my recording folders and files.

---

### Post by nickrout on 2011-11-01
> **GaryP2 said:**
> 
 
I’m interested in knowing how this goes for you in that I’m preparing to do almost the same thing – move from a stable Mythbuntu 10.04 (MythTV .23) to a Mythbuntu 11.10 (MythTV .24) system. In my case, I bought a new hard drive and hope to be able to do a clean install of 11.10 on the new drive, then restore the .23 database on top of that finally move over my recording folders and files.

Why why why? 0.24.1 is available for *buntu 10.04 via mythbuntu-repos. Use that, unless there is some very glaring need to go to some newer kernel in a later edition of *buntu.

---

### Post by donb21 on 2011-11-01
Yes, I am using the full restore, the partial sounded way too scary.  I don't recall the mis-steps I had on the first attempt, but they must have been pretty good; it really went badly.  I was running myth-setup manually (from a terminal), but now I'm running it from the system menu; seems to be way more stable.  Or, maybe I just forgot to turn off the back-end before starting!

I'm taking a lot of notes; I'll post them when I finish (assuming it all works...I'm sure it will).

And for the size, the backup file is 15 meg, is that considered large?  I've migrated the database over several versions of mythtv, I think the first was on Fedora Core 4.

---

### Post by newlinux on 2011-11-01
> **nickrout said:**
> Why why why? 0.24.1 is available for *buntu 10.04 via mythbuntu-repos. Use that, unless there is some very glaring need to go to some newer kernel in a later edition of *buntu.

I echo this.... Even if you still want to go the 11.10, I'd strongly consider an inplace upgrade to .24.1 in 10.04 first. I'm still running 10.04 (I tend to go LTS to LTS) with .24.1.


> **donb21 said:**
> Yes, I am using the full restore, the partial sounded way too scary.  I don't recall the mis-steps I had on the first attempt, but they must have been pretty good; it really went badly.  I was running myth-setup manually (from a terminal), but now I'm running it from the system menu; seems to be way more stable.  Or, maybe I just forgot to turn off the back-end before starting!

I'm taking a lot of notes; I'll post them when I finish (assuming it all works...I'm sure it will).

And for the size, the backup file is 15 meg, is that considered large?  I've migrated the database over several versions of mythtv, I think the first was on Fedora Core 4.

In my world 15MB is kind of small for a DB.

---

### Post by GaryP2 on 2011-11-02
> **nickrout said:**
> Why why why? 0.24.1 is available for *buntu 10.04 via mythbuntu-repos. Use that, unless there is some very glaring need to go to some newer kernel in a later edition of *buntu.
> **newlinux said:**
> I echo this.... Even if you still want to go the 11.10, I'd strongly consider an inplace upgrade to .24.1 in 10.04 first. I'm still running 10.04 (I tend to go LTS to LTS) with .24.1.
Thanks for the feedback! After further consideration after reading your posts and more about the purpose and schedule behind LTS, I’m going to focus on just what you said and simply upgrade to Myth 24.1 and get 10.04 fully updated! When I installed the environment 14 months ago, I froze the installation from from all patches and updates, including OS and MythTV updates because overall it is working so well. I wanted to avoid surprises with things breaking if an update was released that caused an issue, and only do updates when I had time to focus on them to plan them out and have time to deal with issues. That time for me is now and over the next several weeks.
 
I’m interested in how others manage their updates but don’t want to hijack this thread so I created a new thread with that topic:

[INDENT][http://ubuntuforums.org/showthread.php?t=1874285](http://ubuntuforums.org/showthread.php?t=1874285)
[/INDENT]

---

### Post by donb21 on 2011-11-06
I finished moving the database and it seems to work pretty well.  Here's the procedure in "guide" format (next reply); comments are welcome.

I should note that I had several crashes during the process probably due to a dicey hard disk (brand new Samsung 2T drive; I plan to return it under warranty).

The other unusual behavior were the Mythtv database upgrades.  They seem to be context sensitive, or something.  I had a couple of cases where I exited the frontend and on re-entry, more upgrades happened.  They ran and worked, but it was a surprise.

---

### Post by donb21 on 2011-11-06
Database migration procedure: This is a procedure to migrate an existing MythDora-12 database to a newly installed Mythbuntu-11.10 box.  It's fashioned-after the procedures documented here:

Backup and restore procedure:
[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

Create new database procedure:
[http://www.mythtv.org/docs/mythtv-HOWTO-23.html](http://www.mythtv.org/docs/mythtv-HOWTO-23.html)

Previous procedure for MythDora database migration:
[http://mythdora.com/?q=node/5463](http://mythdora.com/?q=node/5463)

The new box has Mythbuntu installed with a minimal configuration and a virgin database.  It's capture hardware has been installed and setup, but no scheduling or other setups have been done.  Live TV works, but that's about it.  The basic information is:

MythDora – Mythfrontend version: branches/release-0-23-fixes (0.23-8.fc12 (r25413))
MythDora – mythbackend version: branches/release-0-23-fixes [0.23-8.fc12 (r25413)]
MythDora  host name – nick.zoominternet.net

Mythbuntu – Mythfrontend version: fixes/0.24 (v0.24.1.80-g1de0431)
Mythbuntu – mythbackend version: fixes/0.24 [v0.24.1-80-g1de0431]
Mythbuntu – host name – zedo
Mythbuntu – my user account name - don
Mythbuntu – my user account password – mythtv (this was the default on the MythDora installation, reused here)

1.  Create database backup on MythDora box:
From first (main) menu, pick: Mythdora Tools > Database Tools > Optimize Database (let it complete and return to the menu, it takes a minute or so) > Database Backup > Backup DB

Note – We ran “Optimize Database” in order to fix any outstanding table errors before doing the backup.

Note - The generic form of the backup command is:
[root@nick mythtv]# mythconverg_backup.pl --directory /home/mythtv
…and creates a backup file similar to: mythconverg-1254-20111104083937.sql.gz

2.  Determine the hostname of the MythDora box:
[mythtv@nick ~]$ hostname
nick.zoominternet.net

3.  Determine hostname of the MythBuntu box:
don@zedo:/etc$ hostname
zedo

4.  You may care to record the directory names on the MythDora box.  I needed these to move recordings and other things to the new box (not documented in this procedure).  Mine are:
/storage/dorabackup
/storage/games
/storage/lost+found
/storage/misc
/storage/music
/storage/mytharchive
/storage/pictures
/storage/posters
/storage/recordings
/storage/storage1
/storage/temp
/storage/videos

5.  Capture any settings that work on the old box (we needed these for the Hd-Pvr setup).
    a.  Audio selections for HDMI setup
    b.  Video selections for HD-Pvr

6.  Make a copy of the source database backup:
Insert a USB-drive into the source computer (MythDora in our case) and use the file browser to make the copy (Applications > System Tools > File Browser; the USB drive should show up in the “Places” list).

7.  Copy the database onto the Mythbuntu box:
Insert a USB-drive into the Mythbuntu computer.  From the Ubuntu-desktop, use the file browser to make the copy (Applications > System > Thunar File Manager; the USB drive should show up in the left panel as “USB DISK”).  Copy the database backup file to:

/home/don  (replace “don” with your user name)

8.  Open a terminal and stop MythBuntu mythbackend:
don@zedo:~$ sudo stop mythtv-backend
[sudo] password for don: mythtv

9.  There are two users in the mysql database.  The names and passwords are:
User name – root
Password – mythtv
(same password as user account password I entered during the Mythbuntu installation)

User name - mythtv
Password - 98qwfK7d
Note - This is the password the installation created for me.  Yours will not be the same.  If you want to know yours, look in /home/don/.mythtv/config.xml for the install-created password (substitute your account name for “don”).  This name and password are not used for any of the following instructions; I just put them here for information.

10.  Log into mysql:
don@zedo:~$ sudo mysql -uroot –p
Enter password: mythtv

11.  Drop the existing Mythbuntu database:
Caution! This is a big deal; make absolutely sure you’re on the right box and your doing the right database.  There is no recovery from this.  I do everything from a remote terminal with several sessions open at the same time.  It’s really easy to logon to the wrong one!

mysql >drop database mythconverg;
mysql >quit

12.  Create a new, empty mythconverg database:
don@zedo:~$ mysql -uroot -p < /usr/share/mythtv/sql/mc.sql
Enter password: mythtv
don@zedo:~$

Note – If you use “-umythtv” in this command, it will create a database, and then throw an error, resulting in a partially created database.  If that happens, go back and repeat these last two steps (re-drop, re-create using a different user).

13.  The blank database installed by mc.sql (above) creates “mythtv” as the password for the mythtv user (i.e. user/password are mythtv/mythtv); entries in “config.xml” and “mysql.txt” need to be changed to match.  If we don’t change these, mythconverg_restore.pl and myth-setup will not start properly.  Change the mysql password for mythtv:

a.  /home/don/.mythtv/config.xml - Change 98qwfK7d to mythtv
b.  /home/don/.mythtv/@mysql.txt - Change 98qwfK7d to mythtv
c.  Note - Both files are symlinked in the /home/mythtv/.mythtv directory; no need to change them.

Examples:

/home/don/.mythtv/config.xml:  (old password are commented-out in these example…or you could just delete the line)

<DBHostName>localhost</DBHostName>
 <DBUserName>mythtv</DBUserName>
 <!--  <DBPassword>98qwfK7d</DBPassword>  -->
 <DBPassword>mythtv</DBPassword>
 <DBName>mythconverg</DBName>
 <DBPort>0</DBPort>

/home/don/.mythtv/@mysql.txt:  (old password is commented-out)
DBUserName=mythtv
#DBPassword=98qwfK7d
DBPassword=mythtv
DBName=mythconverg
DBType=QMYSQL3

14.  Install the backup database (this can take a minute):
don@zedo:~$ sudo /usr/share/mythtv/mythconverg_restore.pl --directory /home/don --filename mythconverg.sql.gz
don@zedo:~$

15.  Ensure that the new hostname you'll be using isn't already in the database. (replace “zedo” with your host name).  It shouldn’t be the same unless you named the new Mythbuntu box the same as the older box.
$ mysql -uroot -p mythconverg -e "SELECT COUNT(*) FROM settings WHERE hostname LIKE '%zedo%';"
Enter password: mythtv
+----------+
| COUNT(*) |
+----------+
|        0 |
+----------+
[root@nick mythtv]#

16.  Change the hostname:
don@zedo:~$  /usr/share/mythtv/mythconverg_restore.pl --change_hostname --old_hostname="nick.zoominternet.net" --new_hostname="zedo"

Successfully changed hostname
don@zedo:~$

17.  Run mythsetup and allow upgrades (Applications > System > Mythtv Backend Setup)
18.  Delete and re-create the capture hardware, input connection, etc.

Note – “Delete all capture cards” is different than “Delete all capture cards on zedo”.  Use “Delete all capture cards”; it does a more complete delete (finds and deletes bogus settings).

19.  Correct the path names (if different)
    a.  "Default" Storage Group Directories - /var/lib/mythtv/recordings
    b.  "LiveTv" Storage Group Directories - /var/lib/mythtv/livetv/
    c.  "DB Backups" Storage Group Directories - /var/lib/mythtv/db_backups/
    d.  "Videos" Storage Group Directories - /var/lib/mythtv/videos/
    e.  "Trailers" Storage Group Directories - /var/lib/mythtv/trailers/
    f.  "Coverart" Storage Group Directories - /var/lib/mythtv/coverart/
    g.  "Fanart" Storage Group Directories - /var/lib/mythtv/fanart/
    h.  "Screenshots" Storage Group Directories - /var/lib/mythtv/screenshots/
    i.  "Banners" Storage Group Directories - /var/lib/mythtv/banners/
    j.  "Posters" Storage Directories - /var/lib/mythtv/coverart    

20.  Run mythfrontend and allow upgrades.

---

### Post by GaryP2 on 2011-11-07
[SIZE=3][FONT=Calibri]donb21 - Thanks for writing this up! Although I’m not planning on doing quite as extensive an update at this time, I am able to get some good nuggets of info from your experience, such as the fact that I may see multiple database upgrades. I would have thought this would have only happened once also and would have been concerned seeing it happen again.[/FONT][/SIZE]
> **donb21 said:**
> 18. Delete and re-create the capture hardware, input connection, etc.
[SIZE=3][FONT=Calibri]Did you only have to do this because you have unlike capture hardware? In other words, if your old and new system was using the same tuners or capture cards, wouldn’t this be in the database and simply carry over?[/FONT][/SIZE]

---

### Post by newlinux on 2011-11-07
I moved DB from one server to an existing server (That was previously a secondary backend). I had to modify hostnames (change references to the existing secondary backend references before changing the previous replacing the previous backend's name with the current primary backend). Since my tuners, video sources, etc. weren't changing and the tuners wer all on the same machines they were on before changing the master backend, I didn't need to modify those when restoring the DB.

---

### Post by donb21 on 2011-11-24
I disappeared for a while...it's the holidays :).  GaryP2, you're welcome.  I got into the habit of deleting and re-setting-up the capture hardware because of a problem I  had several versions ago.

Deleting the capture hardware is probably not necessary, but since it's simple to do...I just do.  I agree, sometimes it's not so simple; and it kinda violates the "if it works, don't fix it" guideline.  On the other hand, the delete process might clean things up a bit better.  Not that they needed cleaned-up in the first place.....

---

### Post by donb21 on 2013-03-16
I found another password file that needed to be updated.  If using MythWeb, the apache2 web config file needs the same change, so the instructions should include this note:

> [COLOR=#000000]13. The blank database installed by mc.sql (above) creates &#8220;mythtv&#8221; as the password for the mythtv user (i.e. user/password are mythtv/mythtv); entries in &#8220;config.xml&#8221; and &#8220;mysql.txt&#8221; need to be changed to match. If we don&#8217;t change these, mythconverg_restore.pl and myth-setup will not start properly. Change the mysql password for mythtv:[/COLOR]

[COLOR=#000000]a. /home/don/.mythtv/config.xml - Change 98qwfK7d to mythtv[/COLOR]
[COLOR=#000000]b. /home/don/.mythtv/@mysql.txt - Change 98qwfK7d to mythtv[/COLOR]
[COLOR=#000000]c. Note - Both files are symlinked in the /home/mythtv/.mythtv directory; no need to change them.

Note - If using MythWeb, also change "[/COLOR]/etc/apache2/sites-available/mythweb.conf".  Here's an example:

            setenv db_server        "localhost"
            setenv db_name          "mythconverg"
            setenv db_login         "mythtv"
#            setenv db_password      "33LHu8AD"
**            setenv db_password      "mythtv"**


---

### Post by grunge09 on 2013-03-20
Make a backup of database file

mysqldump --opt -u mythtv -p mythconverg > mythconverg.bak

copy mythconverg.bak to flash drive

Restore a database file

path to where ever the mythconverg.bak file is.

mysql -u mythtv -p -v mythconverg < mythconverg.bak

Stop and restart backend, then run front end should b good to go. Providing you have copied all your /var/lib/mythtv folders and data to new drive/server.

---


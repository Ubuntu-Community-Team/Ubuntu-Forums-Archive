---
title: "importing recordings"
date: 2010-01-27
forum: Mythbuntu
---

### Post by linuxhippy on 2010-01-27
I just re-installed mythbuntu 9.10.  My recordings are safely on another partition.  I now made a new directory called /recordings and mounted that partition on /recordings and changed permissions to my user.  When I go to watch my recordings now in mythbuntu my recordings are not there.  I can see them when I browse with thunar.  So, how do import them into mythbuntu?

---

### Post by ian dobson on 2010-01-28
Hi,

I imagine you'll need to use mythcomflag to "tell" mythtv about the recordings. MythTV uses information in a mysql database to know what recordings are on the system.

Regards
Ian Dobson

---

### Post by linuxhippy on 2010-01-28
> **ian dobson said:**
> Hi,

I imagine you'll need to use mythcomflag to "tell" mythtv about the recordings. MythTV uses information in a mysql database to know what recordings are on the system.


How do you use mythcomflag?

---

### Post by ian dobson on 2010-01-28
Hi,

you'll need to go to the terminal then run mythcommflag.

Try mythcommflag --help for what options it supports. I imagine you'll need to use the --video option or 

-c -s -f for channel ID/start time

or -f for Flag recording with specific filename

Regards
Ian Dobson

---

### Post by linuxhippy on 2010-01-28
I got this:

tux@FreeVo:/recordings$ ls
1013_20100125203000.nuv      1013_20100125205900.nuv      1013_20100126205900.nuv
1013_20100125203000.nuv.png  1013_20100125205900.nuv.png  1013_20100126205900.nuv.png

tux@FreeVo:/recordings$ mythcommflag -f 1013_20100125205900.nuv
2010-01-28 20:18:52.215 Using runtime prefix = /usr
2010-01-28 20:18:52.215 Using configuration directory = /home/tux/.mythtv
2010-01-28 20:18:52.216 Empty LocalHostName.
2010-01-28 20:18:52.224 New DB connection, total: 1
2010-01-28 20:18:52.227 Closing DB connection named 'DBManager0'
mythcommflag: ERROR: Unable to find DB info for 1013_20100125205900.nuv
QSqlDatabasePrivate::removeDatabase: connection 'DBManager0' is still in use, all queries will cease to work.

What am I doing wrong?

---

### Post by laffinet on 2010-01-28
Did you backup your database before reinstalling ?

Otherwise I'm afraid you lost all the information for the recordings. Which basically means you are left with a bunch of video files that you can watch if you add them to your videos, but you won't be able to have them show up in recordings with all the information (title etc.).

---

### Post by linuxhippy on 2010-01-28
> **laffinet said:**
> Did you backup your database before reinstalling ?

Otherwise I'm afraid you lost all the information for the recordings. Which basically means you are left with a bunch of video files that you can watch if you add them to your videos, but you won't be able to have them show up in recordings with all the information (title etc.).

no...how do you backup your database?

---

### Post by ian dobson on 2010-01-29
Hi,

Appears to make a backup of the mythtv database to  /var/backups every seven days or so.

Regards
Ian Dobson

---

### Post by linuxhippy on 2010-01-29
> **ian dobson said:**
> Hi,

Appears to make a backup of the mythtv database to  /var/backups every seven days or so.

Regards
Ian Dobson

I saw that somewhere when I set things up and didn't disable it.  So it's automatic.  Is there a manual way of doing this?

---

### Post by ian dobson on 2010-01-29
Hi,

I use this command to backup all my mysql databases to a compressed file.

mysqldump -uroot -ppassword --all-databases --opt | bzip2 > /data/backup/backup-sql.bz2

Regards
Ian Dobson

---

### Post by linuxhippy on 2010-01-29
nice-thanks for that!

---

### Post by nickrout on 2010-01-29
the correct answer is on this wiki page:

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

and read this:

[http://www.gossamer-threads.com/lists/mythtv/users/405443#405443](http://www.gossamer-threads.com/lists/mythtv/users/405443#405443)

---


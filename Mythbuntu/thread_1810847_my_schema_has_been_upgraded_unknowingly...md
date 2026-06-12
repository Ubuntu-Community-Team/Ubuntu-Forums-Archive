---
title: "my schema has been upgraded unknowingly.."
date: 2011-07-23
forum: Mythbuntu
---

### Post by Mad_Professor on 2011-07-23
[QUOTE=mythfrontend]
ERROR: MythTV database has newer TV schema (1264) than expected (1254).
[/QUOTE]

```

pvr@pvr:~$ mythbackend --version
Please attach all output as a file in bug reports.
MythTV Version   : 26863
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 23056
Library API      : 0.23.1.201000710-1
QT Version       : 4.6.2

``````

pvr@pvr:~$ mythfrontend --version
xprop:  unable to open display ''
Please attach all output as a file in bug reports.
MythTV Version   : 26863
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 23056
Library API      : 0.23.1.201000710-1
QT Version       : 4.6.2

```My backend has automatic updates disabled. I have 4 frontends, 1x laptop, 2 desktops and 1 on the backend.

I recently updated my linuxmint on my laptop and for whatever ****** up reason it was downloading mythtv 0.24 when I already compiled and installed 0.23.1.

So I'm wondering if this messed up my backend? Is there anyway to rollback?

---

### Post by Mad_Professor on 2011-07-23
well I totally trashed my database, thank you mythtv team for utter crap.

The backup and restore scripts don't work.

now I gotta reinstall mythtv.

---

### Post by Mad_Professor on 2011-07-24
I managed to recover it and it runs now and I didn't have to wipe it.

What I used originally. 

[http://www.mythpvr.com/mythtv/tips/migrate-recordings.html](http://www.mythpvr.com/mythtv/tips/migrate-recordings.html)

it didn't work, but it was a good template to come up with my own solution.



1.Kill the backend

```
/etc/init.d/mythbackend stop
```2. make a backup of your recordings info 
```

mysqldump -u mythtv -p -t mythconverg record recorded \oldrecorded recordedprogram recordedrating \recordedmarkup recordedseek > recordings.sql
```If you don't know your DB password, /etc/mythtv/mysql.txt will tell ya, or use root for the time being.

then I drop the database and created a new one and then zcat the weekly backup from /var/lib/mythtv/recordings/mythconverg-whatever.sql.gz to mysql

```

zcat /var/lib/mythtv/recordings/mythconverg-whaterver.sql.gz | mysql -u root -p mythconverg

```After that I truncate a few tables using TRUNCATE TABLE via the mysql client. Be sure to USE mythconverg database before executing it.

truncate the following:

record
recorded
oldrecorded
recordedprogram
recordedrating
recordedmarkup
recordedseek

optional:
I had a problem with columns not lining up correctly.
```
[SIZE=2]Error 1136 (21s01) Column Count Doesn't Match Value At Row 1
[/SIZE]
``` I had to compare schema "record" with a virtual install of mythbuntu 11.04 with mythtv 0.24 database using the mysql "describe" command to compare. I removed tsdefault column from record in order to restore my recordings.sql file, but you may not need to. 

If you do, make the restore then re-add tsdefault otherwise it will break the ability to record. You can vi the weekly backup to view the previous settings, and you can use mysql workbench if its too complicated for you to add the columns and move it up 5 or 6 times, which is what I had to do.

Once you truncate the tables, you can cat your recordings.sql back to the mythconverg DB.

```

 cat /var/lib/mythtv/recordings/recordings.sql | mysql -u mythtv -p mythconverg

```After this you will have to start the mythbackend.
  After that enter setup and tweak some stuff. Mostly capture cards or guide data, then save and run mythfilldatabase.

Be sure to test the mythfrontend after you're done:
Check to make sure all your recordings are there including your recent ones.
Do a test recording.
Watch live TV.
Make sure your guide data works.

Test anything else that your worried about.

Hope this helps anyone that is stuck in my situation.

~MP

---


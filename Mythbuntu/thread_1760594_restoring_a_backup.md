---
title: "restoring a backup"
date: 2011-05-17
forum: Mythbuntu
---

### Post by sami8519 on 2011-05-17
Hi guys,

A couple of days ago I made a backup of my database via mythbuntu control center, Now I tried to restore it it gives me the following error(I also oticed everytime I make a backup it is only 1.2KB in size!!)

```

org.freedesktop.DBus.Python.RuntimeError
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/MythbuntuControlCentre/backend.py", line 252, in scriptedchanges
    for item in plugin_dictionary:
RuntimeError: dictionary changed size during iteration
```

I am using mythbuntu 11.04. Any idea guys how to fix this please? 

Thanks.

---

### Post by tgm4883 on 2011-05-17
> **sami8519 said:**
> Hi guys,

A couple of days ago I made a backup of my database via mythbuntu control center, Now I tried to restore it it gives me the following error(I also oticed everytime I make a backup it is only 1.2KB in size!!)

```

org.freedesktop.DBus.Python.RuntimeError
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/MythbuntuControlCentre/backend.py", line 252, in scriptedchanges
    for item in plugin_dictionary:
RuntimeError: dictionary changed size during iteration
```

I am using mythbuntu 11.04. Any idea guys how to fix this please? 

Thanks.

If you backed up the database then that is way too small for a backup. The backup file is just a regular tar.gz file. You should be able to open it up and see what is inside. 

If you didn't back up the database, then that could be the correct size. It is only backing up certain config files and text is pretty compressable.

As for the error message, that should have been fixed in 11.04, but I can't find the commit. I'm looking into that.

---

### Post by jmcvay on 2011-05-17
same problem - 11.04

---

### Post by grygub on 2011-05-18
similar problem. I am also running 11.4 and the backup file was only 6k. 

```
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/MythbuntuControlCentre/backend.py", line 252, in scriptedchanges
    for item in plugin_dictionary:
RuntimeError: dictionary changed size during iteration
```

thanks

---

### Post by tgm4883 on 2011-05-18
What OS did you backup from? 

Did you select the backup DB option?

Can you send me a copy of the backup file ( tgm4883 DOT mythbuntu DOT org )

---

### Post by grygub on 2011-05-18
I backed up the database from a different computer running 11.4. Originally the computer was running 10.10 then had mythtv upgraded to .25 then had the ubuntu upgraded to 11.4. I used mythbuntu control centre and checked the backup database box. Message sent.
thanks for the help
bryan

---

### Post by tgm4883 on 2011-05-18
Thanks, I'm looking into the issue right now. This backup file definitely doesn't have a backup of the database in it.

---

### Post by tgm4883 on 2011-05-18
> **tgm4883 said:**
> Thanks, I'm looking into the issue right now. This backup file definitely doesn't have a backup of the database in it.

Ok, I've hunted down the issue with the restoring. It is currently being worked on as it appears to be an issue with MCC, not mythbuntu-bare.

In the process of hunting that down, I found a bug with the backing up of the database. If you used mythbuntu-bare to do a backup and checked the database backup box it is _**highly likely**_ that the database didn't get backed up.

---

### Post by sami8519 on 2011-05-19
Thanks mate for the help. I have just opened the backup in it has two folders(etc and tmp). Those files are inside the etc:(mythtv/config.xml and mysql.txt, /etc/hostname and /etc/hosts). tmp has an empty folder mythbuntu bare. 

Sorry but what is mythbuntu-bare and how to use it to backup the database? Does the database contain the recordings and livetv? I am only interested in backing up my channels and general settings and I don't know what is the simplest way to do so. Thank you.

Best regards,
Sami

---

### Post by klc5555 on 2011-05-19
Until about mythtv ver. .022 or so, most people tended to back up mythconverg with simple one- or two-line bash scripts based on mysqldump and run as a daily cron job, more or less along the following lines:

 mysqldump -u mythtv -pPASSWORD mythconverg -c | gzip -c > /home/mythtv/mythtv_backup.`date '+%w'`.sql.gz 

With maybe another line added to the script if desired to copy each gzipped backup to a second location. When one needed to restore a database, one would gunzip a copy of the desired backup and from a prompt do a

$mysql -u mythtv -pPASSWORD mythconverg < mythtv_backup.[WHICHEVER].sql  

I was suprised to find not too long ago, considering the amount of obsolete cruft that litters the mythtv wiki site, that all references to such simple older methods are scrubbed from the mythtv wiki in favor of the lengthy perl script that is evidently the only currently sanctioned method. 

I could be wrong, but nevertheless, I don't see why the older method couldn't still be used, and would certainly be simple to debug.

---

### Post by tgm4883 on 2011-05-19
> **sami8519 said:**
> Thanks mate for the help. I have just opened the backup in it has two folders(etc and tmp). Those files are inside the etc:(mythtv/config.xml and mysql.txt, /etc/hostname and /etc/hosts). tmp has an empty folder mythbuntu bare. 

Sorry but what is mythbuntu-bare and how to use it to backup the database? Does the database contain the recordings and livetv? I am only interested in backing up my channels and general settings and I don't know what is the simplest way to do so. Thank you.

Best regards,
Sami

Mythbuntu-bare is the backup and restore utility found in mythbuntu control center. I'll be pushing a fix for this later this afternoon to the mythbuntu repositories. If you have the mythbuntu-repos package you should get the update through normal updates

---

### Post by Amorget on 2011-07-01
I am having this same issue.  I added the mythbuntu repos from the deb package I found on a search and ran the updates, but same problem.

I looked at the .sql file and it's ~3 megs, which seems a little small, however looking at the file there was a lot in it.  I upgraded from 10.10 to 11.04 and did a backup through the Mybtuntu Control Center before I did a clean install.

Any idea what may be going on?

Thanks, Douglas

---

### Post by tgm4883 on 2011-07-01
> **Amorget said:**
> I am having this same issue.  I added the mythbuntu repos from the deb package I found on a search and ran the updates, but same problem.

I looked at the .sql file and it's ~3 megs, which seems a little small, however looking at the file there was a lot in it.  I upgraded from 10.10 to 11.04 and did a backup through the Mybtuntu Control Center before I did a clean install.

Any idea what may be going on?

Thanks, Douglas

If you see the SQL file in there then it should be fine, as -bare uses the mythtv database backup and restore scripts.

As a workaround for restoring.
[LIST=1]
[*]Open a terminal
[*]stop mcc-backend "sudo killall mcc-backend"
[*]start mcc-backend "sudo /usr/share/mythbuntu/mcc-backend"
[*]Open MCC and restore your backup
[/LIST]

---

### Post by Amorget on 2011-07-01
Hi,
It is saying it is successful, however it doesn't appear to be actually doing anything.  None of my settings returned and when I made some changes then restored again, those changes didn't revert.
Any ideas?

---

### Post by tgm4883 on 2011-07-01
> **Amorget said:**
> Hi,
It is saying it is successful, however it doesn't appear to be actually doing anything.  None of my settings returned and when I made some changes then restored again, those changes didn't revert.
Any ideas?

You are going to have to be a bit more specific that than. What settings. What do you mean it didn't do anything.

---

### Post by Amorget on 2011-07-01
> **tgm4883 said:**
> You are going to have to be a bit more specific that than. What settings. What do you mean it didn't do anything.

When I mean it didn't do anything, I mean it didn't set any of my settings (the main one being where my Videos are stored) and it lost all the Meta data for my videos.

So I set my video directory and went and loaded them all.  It rebuilt the database from what I can tell completely.  Looked at the videos and all the meta data was gone.

So I tried restoring again and it left the one change I made, which is where my videos are stored, and didn't change change that setting or update the meta data for my videos.

Is there anything specific I can check to see if the database is actually being updated at all when I run the restore?

---

### Post by tgm4883 on 2011-07-02
> **Amorget said:**
> When I mean it didn't do anything, I mean it didn't set any of my settings (the main one being where my Videos are stored) and it lost all the Meta data for my videos.

So I set my video directory and went and loaded them all.  It rebuilt the database from what I can tell completely.  Looked at the videos and all the meta data was gone.

So I tried restoring again and it left the one change I made, which is where my videos are stored, and didn't change change that setting or update the meta data for my videos.

Is there anything specific I can check to see if the database is actually being updated at all when I run the restore?

Hmm, yea it sounds like it skipped doing the database. Are you restoring it directly on the master backend (ie not over the network.)

---

### Post by Amorget on 2011-07-02
Correct, I am running it on the master backend.

---

### Post by tgm4883 on 2011-07-03
> **Amorget said:**
> Correct, I am running it on the master backend.

Ok, I think I found the issue. Can you do the following

Edit mythrestore.py
```
sudo nano /usr/share/mythbuntu/bare/mythrestore.py 
```

Find
```
if os.path.isfile("/usr/share/doc/mythtv-backend-master"):
```

And change it to
```
if os.path.isdir("/usr/share/doc/mythtv-backend-master"):
```

Save the file then attempt the restore again.

---

### Post by Amorget on 2011-07-08
I am embarrassed that it has taken me so long to reply after your prompt responses, however same thing, doesn't seem to be restoring the database.  I tried removing the Videos directory and clearing out all the video files by doing a rescan, restored it, and the videos directory was still empty.

Thanks,
Douglas

---

### Post by tgm4883 on 2011-07-08
> **Amorget said:**
> I am embarrassed that it has taken me so long to reply after your prompt responses, however same thing, doesn't seem to be restoring the database.  I tried removing the Videos directory and clearing out all the video files by doing a rescan, restored it, and the videos directory was still empty.

Thanks,
Douglas

When you say videos directory, do you mean the actual videos directory or the videos section in the frontend? Because there is not a backup of the actual video files in that backup file.

---

### Post by Amorget on 2011-07-08
I mean the videos section in the front end, all my videos are stored on a separate HDD away from getting lost on accident.

---

### Post by tgm4883 on 2011-07-08
Ok, in an effort to get you back on track, I've included the command that is run to restore the database. Extract the sql file from the backup and then run the following command. Can you also create a bug at [https://bugs.launchpad.net/mythbuntu](https://bugs.launchpad.net/mythbuntu) and upload your backup file so I can take a look.

```
/usr/share/mythtv/mythconverg_restore.pl --drop_database --create_database --directory <directory containing db backup>
```

---

### Post by Amorget on 2011-07-17
Thank you, thank you, thank you!

It restored and everything is there!!!

I will submit a bug report.

Thank you again!

---

### Post by danellisuk on 2012-01-09
Is there any news on the issue where Mythbuntu Control Centre fails to backup the database?

I am using Ubuntu 11.04 with the 0.24.x mythbuntu repo.  Mythbuntu Control Centre is version 0.63-0ubuntu1.

I am selecting:-

[LIST=1]
[*]"Backup & Restore"
[*]"Get Started"
[*]Select "Backup"
[*]Select "Backup now"
[*]Check "Yes, backup the database?"
[/LIST]

The backup operation completes without an error, but the resulting file is small (9.7 KB) and does not seem to include a database dump.

---

### Post by tgm4883 on 2012-01-10
> **danellisuk said:**
> Is there any news on the issue where Mythbuntu Control Centre fails to backup the database?

I am using Ubuntu 11.04 with the 0.24.x mythbuntu repo.  Mythbuntu Control Centre is version 0.63-0ubuntu1.

I am selecting:-

[LIST=1]
[*]"Backup & Restore"
[*]"Get Started"
[*]Select "Backup"
[*]Select "Backup now"
[*]Check "Yes, backup the database?"
[/LIST]

The backup operation completes without an error, but the resulting file is small (9.7 KB) and does not seem to include a database dump.

There is an issue with the backup in 11.04, but there isn't an easy way to backport a fix for that. The fix is in 11.10. I'd recommend backing up the database with [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

---


---
title: "Lost MythTV backend configuration"
date: 2012-03-03
forum: Mythbuntu
---

### Post by markofealing on 2012-03-03
It would appear that I've lost my MythTV backend configuration. Apart from Storage Directories all other settings have been lost, I can not access any of my recordings, although they do exist on a data drive. If I select StartFrontend from Mythwelcome it does nothing.

I've tried reconfiguring my backend, but it will not allow me to enter capture cards, I can complete the parameters, but it will not save them. No errors are displayed.

Whilst I had thought of restoring the SQl database from my backups, some idiot has removed backup & Restore from Mythbuntu Control Centre and trying to do this manually following the Wiki results in mysql asking for a password. I used to be able to see this in Mythbuntu Control Centre in Restore & backup but now its gone I don't know how to find it.

Backup & Restore seems to have been replaced by [https://launchpad.net/ubuntu/oneiric/i386/mythbuntu-bare-client](https://launchpad.net/ubuntu/oneiric/i386/mythbuntu-bare-client) which did not install because of a permisions bug in the installer [http://ubuntuforums.org/archive/index.php/t-1866704.html](http://ubuntuforums.org/archive/index.php/t-1866704.html) (unbelieveable that this was  not tested)! 

So having installed the bare-client, given it the right permissions, pointed it to the location where my backups exist and applied the change, it does not seem to recognise the backups, it just allows me to make new backups which for a bricked system is useless.

I now wished I had never used the Control Centre for backups had I known that this was going to happen in a future release. Change is good if done for the right reasons, in this case the decision to change this feature is retarded.

Short of a reinstall, and a posible restore of the database I see no way out of this mess.

Annoyed with the mythbuntu developers, yes that's a polite way of putting it! MythTV is a great product (I have 3 PCs running it) but crap experiences like this are unacceptable.

Any help will be appreciated, :(

---

### Post by ijumpship on 2012-03-03
Out of curiosity are you testing the mythwelcome on a single machine that carries a primary front-end back end.

I have not much to offer,I share your sentiments when it comes to upgrade,but I too fiddle with development  of software and believe me,I hate when something goes wrong,but its all part of the development.

I spent almost 4 months trying to track down a bug in a project,I even stop answering the phones,as I just did not want to talk to anyone

Try three dose of this,[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore).
When mine got screwed,I just paste this on the Wall,got drunk and I did not know what I did but it got restored

---

### Post by klc5555 on 2012-03-03
> **markofealing said:**
> It would appear that I've lost my MythTV backend configuration. Apart from Storage Directories all other settings have been lost, I can not access any of my recordings, although they do exist on a data drive. If I select StartFrontend from Mythwelcome it does nothing.

I've tried reconfiguring my backend, but it will not allow me to enter capture cards, I can complete the parameters, but it will not save them. No errors are displayed.

Whilst I had thought of restoring the SQl database from my backups, some idiot has removed backup & Restore from Mythbuntu Control Centre and trying to do this manually following the Wiki results in mysql asking for a password. I used to be able to see this in Mythbuntu Control Centre in Restore & backup but now its gone I don't know how to find it.

Backup & Restore seems to have been replaced by [https://launchpad.net/ubuntu/oneiric/i386/mythbuntu-bare-client](https://launchpad.net/ubuntu/oneiric/i386/mythbuntu-bare-client) which did not install because of a permisions bug in the installer [http://ubuntuforums.org/archive/index.php/t-1866704.html](http://ubuntuforums.org/archive/index.php/t-1866704.html) (unbelieveable that this was  not tested)! 

So having installed the bare-client, given it the right permissions, pointed it to the location where my backups exist and applied the change, it does not seem to recognise the backups, it just allows me to make new backups which for a bricked system is useless.

I now wished I had never used the Control Centre for backups had I known that this was going to happen in a future release. Change is good if done for the right reasons, in this case the decision to change this feature is retarded.

Short of a reinstall, and a posible restore of the database I see no way out of this mess.

Annoyed with the mythbuntu developers, yes that's a polite way of putting it! MythTV is a great product (I have 3 PCs running it) but crap experiences like this are unacceptable.

Any help will be appreciated, :(

Your current mysql password is contained in the file mysql.txt, a symlink to which you can access under /home/[your-home-directory]/.mythtv/

If your saved mythconverg backups have the following shape: [some-backup-name].sql.gz the way you restore this manually to a newly installed and nearly empty mythconverg database is as follows:

Copy one of these backups to your home directory. Obviously one from the pre-hosed period.

Unzip it. The command: ```
gunzip [some-backup-name].sql.gz
```    This will leave you with the file: [some-backup-name].sql

From your regular user prompt (not sudo) use the command:

```
mysql -u mythtv -p   mythconverg < [some-backup-name].sql
```

Mysql will ask for the password, which will be what you found in the file mysql.txt When you give it, mysql should chug away for a minute or two, and then return you to a prompt. And the job should be done. If mysql instead returns some error message, then this will need to be addressed.

For future reference, when your database appears to be having problems, there are certain recovery steps you can take before trashing the entire install.

From a prompt: ```
mysqlcheck -A --auto-repair -u mythtv -p 
``` The program should ask for that same mysql password from mysql.txt and then it should check for problems in all your mysql databases (you probably only have the one mythconverg) and fix them.

Sometimes I've found that this does not quite do the job when the recorded and seek tables are particularly seriously crashed. In these cases, I've had good luck adding the option -e for "extended check" to the above command. It takes mysqlcheck as long as 5 minutes or so to execute with the -e option, but it does very well at rooting out the problems and fixing them.

---

### Post by markofealing on 2012-03-04
Thank you KLC5555, that has restored the database.:D

When I first thought I had a DB problem I ran the **optimize_mythdb.pl** script which is supposed to repair and optimise each table in the database.

When I ran your repair command **mysqlcheck -A --auto-repair -u mythtv -p** displayed most of the database tables as being corrupt.

On performing the restore and running it again all tables check out OKay and I can now launch MythTV Frontend.

In the MythTV backend setup all the settings have come back, and whilst Managed Recordings were showing as empty and the EPG listings only had two days of data left in them, running the backend config and stopping and restarting the database as a result seems to have brought back everything up unti the last backup.

I really appreciate your help, and your instructions were clear and concise. If only the Wiki was as well written.

One final thing, whilst my system is making weekly backups of the SQL database, how do I check/ change the schedule for this job or is it automatic? I've looked at crontab and there are no entries which was not what I was expecting. 

I'm asking as the Myth Control Console Bare plug-in (the plug-in which seems to have replaced Backup and restore) is showing nothing in terms of Client Status, Configuration is showing as Unmanaged which could either mean it is not configured or set to run an automated schedule. I've changes the Server configuration tab to the right storage directory.the only info I can find on BARE is [http://www.ubuntuupdates.org/package/mythtv_testing/oneiric/main/base/mythbuntu-bare-console](http://www.ubuntuupdates.org/package/mythtv_testing/oneiric/main/base/mythbuntu-bare-console) which for something so important is a little disappointing.

Once again, thank you for your help.

---

### Post by markofealing on 2012-03-04
Thanks ijumpship, no I'm not testing mythwelcome and this is a combined frontend/ backend server.

The issue has now been resolved thanks to klc5555 excellent instructions.

---

### Post by klc5555 on 2012-03-04
Glad everything is restored and running normally!

I'm afraid I can't be of any help regarding the specifics of mythconverg_backup.pl, as I've steadfastly declined to have anything to do with it. I've never really understood the point of having a 1,000+ line perl script do the job that was traditionally done by a 10-line bash script. Specifically this 10-line bash script: 


```

#! /bin/bash
#
# Created on 3/22/2006 by sdkovacs
# Script: mythbackup
#
# Creates a backup of the mythconverg database in the form
# mythbackup.dayofweek.sql.gz. For example Monday would be 
# mythbackup.Mon.sql.gz.
# This allows for a rotating 7-day backup of the mythconverg database. 
# If ${BACKPATH} exists
# and contains a valid directory, the script will copy the backup to 
# that directory in addition to
# /home/mythtv. This is useful for redundant backups. My ${BACKPATH} is 
# a separate physical drive.
#
#
########################################################
BACKFILE="/home/mythtv/mythbackup.`date +%a`.sql.gz"
BACKPATH="/var/lib/mythtv/newrecordings/databasebackups/"

mysqldump -u mythtv -pmythtv  mythconverg -c | gzip -c > ${BACKFILE}
if [ $? -ne "0" ]
then
        echo "Mythtv database backup failed! Exiting..."
        exit 1
fi

if [[ -d ${BACKPATH} ]]
then
        cp ${BACKFILE} ${BACKPATH} || echo "Could not copy ${BACKFILE} 
to ${BACKPATH}. Please investigate."
fi


```

which I've continued to use since I started fiddling around with Mythtv in 2007. Note the mysql password in it (-p) needs to be changed in Mythbuntu to whatever the password is in your mysql.txt. And there can't be any space between -p and that password. 

The script still works, and I have it set as a daily cron job. Restoring from one of these daily backups just takes a couple of minutes from a prompt as I described in my initial message.

All the best.

---

### Post by nickrout on 2012-03-04
> **klc5555 said:**
> Glad everything is restored and running normally!

I'm afraid I can't be of any help regarding the specifics of mythconverg_backup.pl, as I've steadfastly declined to have anything to do with it. I've never really understood the point of having a 1,000+ line perl script do the job that was traditionally done by a 10-line bash script. Specifically this 10-line bash script: 


```

#! /bin/bash
#
# Created on 3/22/2006 by sdkovacs
# Script: mythbackup
#
# Creates a backup of the mythconverg database in the form
# mythbackup.dayofweek.sql.gz. For example Monday would be 
# mythbackup.Mon.sql.gz.
# This allows for a rotating 7-day backup of the mythconverg database. 
# If ${BACKPATH} exists
# and contains a valid directory, the script will copy the backup to 
# that directory in addition to
# /home/mythtv. This is useful for redundant backups. My ${BACKPATH} is 
# a separate physical drive.
#
#
########################################################
BACKFILE="/home/mythtv/mythbackup.`date +%a`.sql.gz"
BACKPATH="/var/lib/mythtv/newrecordings/databasebackups/"

mysqldump -u mythtv -pmythtv  mythconverg -c | gzip -c > ${BACKFILE}
if [ $? -ne "0" ]
then
        echo "Mythtv database backup failed! Exiting..."
        exit 1
fi

if [[ -d ${BACKPATH} ]]
then
        cp ${BACKFILE} ${BACKPATH} || echo "Could not copy ${BACKFILE} 
to ${BACKPATH}. Please investigate."
fi


```

which I've continued to use since I started fiddling around with Mythtv in 2007. Note the mysql password in it (-p) needs to be changed in Mythbuntu to whatever the password is in your mysql.txt. And there can't be any space between -p and that password. 

The script still works, and I have it set as a daily cron job. Restoring from one of these daily backups just takes a couple of minutes from a prompt as I described in my initial message.

All the best.

Possibly the person who wrote the official script knows the issues backwards forwards and inside out. He wrote it with all those bells and whistles for reasons I don't understand, but I sure as hell know and respect his knowledge of the in workings of mythtv. I think you are a little quick to dismiss the official backup script, so beware of the dragons when not doing it right!

---

### Post by klc5555 on 2012-03-04
> **nickrout said:**
> Possibly the person who wrote the official script knows the issues backwards forwards and inside out. He wrote it with all those bells and whistles for reasons I don't understand, but I sure as hell know and respect his knowledge of the in workings of mythtv. I think you are a little quick to dismiss the official backup script, so beware of the dragons when not doing it right!

I think you and I have landed on opposite sides of this discussion before :)

There's no real "right" or wrong here, only problems and solutions. If a bash script that was designed to backup a mysql database with mysqldump for mythtv 0.17 and has done so reliably for years provides the same essential solution as the later perl script that backs up a mysql database using that very same mysqldump, then there's no compelling reason not to continue to use the simple bash script. I used one of its backups last week to move my mythconverg to a new mythtv installation.

I suspect the perl script was developed to move the backup and restoration process from the OS and its utilities to inside the Mythtv application suite itself, to reduce the need for direct mysql interaction from the user, particularly for restoring mythconverg from backup, and to eliminate most of the user's responsibility to be aware of and set up his own mythconverg backup plan. But there are other solutions, and the only real requirements for any of them are that the user knows how to implement them and that they work.

---

### Post by markofealing on 2012-03-10
Well, as I'm fed-up with menu options changing in MythTV or just not working not helped at all by a total lack of documentation (why go through all the trouble of writing a program without producing the documentation so people can use it?) I think I'll probably stick to running the bash script, at least it is readable and like most users I don't know Perl!

As a footnote, I now think I've discovered why my mythtv database got corrupted. The PC wakes itself up and shuts itself down according to the recording schedule so is probably a fairly unique problem. 

Basically, the CMOS battery on my PC died, the BIOS was configured to ignore all errors and so when MythTV started it discovered the date and time different, on power off the clock on the PC just stopped, then resumed on power on. As the PC was not connected to the Internet at the time, the clock did not update itself on power on. A new battery solved this issue. 

Anyway, that's my theory.

---

### Post by nickrout on 2012-03-10
> **markofealing said:**
> Well, as I'm fed-up with menu options changing in MythTV or just not working not helped at all by a total lack of documentation (why go through all the trouble of writing a program without producing the documentation so people can use it?) I think I'll probably stick to running the bash script, at least it is readable and like most users I don't know Perl!

You don''t need to know perl to run a perl program, but you do need to be able to read the documentation, which is easy enough.

Have you read the user handbook in the wiki? If you find it is incomplete, you can add to it you know. Its a wiki after all.

People who don't contribute seem to moan the loudest.

---

### Post by tgm4883 on 2012-03-11
Can you attach one of the backups that you did in the backup and restore utility (in the mythbuntu-control-centre)? It will have your mythtv password in there and likely your database, so if you would rather pm me or open a private bug on launchpad that is fine. It would help to look at it to figure out why it isn't being recognized. Is it throwing any errors?

---

### Post by markofealing on 2012-03-11
> **nickrout said:**
> You don''t need to know perl to run a perl program, but you do need to be able to read the documentation, which is easy enough.

Have you read the user handbook in the wiki? If you find it is incomplete, you can add to it you know. Its a wiki after all.

People who don't contribute seem to moan the loudest.

The user manual in the mythtv wiki does not mention the Mythbuntu Control Centre, let alone bare. To be able to maintain the wiki, non developers of the software do need decent release notes. The only notable thing about the MythTV/ Mythbuntu release notes is their absence. It looks like the team prefer to hide their light under a bucket!

Without blowing my own trumpet too loud, I probably contribute more than most to mythtv documentation on the Internet, [read my blog]("https://mylinuxramblings.wordpress.com/") and decide for yourself.

In my view, without published release notes, the wiki needs to be maintained by the developers of the software. My role is to take what is essentially a technical document (wiki) and make it readable for the masses. At present because the wiki is not being maintained properly and there is no documentation on how recent enhancements work (no proper release notes are issued with mythbuntu which might help form the basis of end user documentation) it would be dangerous to contribute to the wiki without basic background knowledge. Hence the blog. If this situation changed then I would be delighted in contribution to the wiki.

I've just finished writing a article on how to get bare installed correctly in 11.10. What's preventing me from publishing it is that bare does not work! I've now tested it on two Mythbuntu PCs with the same result.

I strongly believe that if someone has the time to write a program, then they also have the time to put together some technical documentation on how it works, even if it is just basic stuff. 

In this case nothing is documented, not even an indication where the log files are kept. On this basis it was absolutely wrong for the Mythbuntu team to have changed backup and restore in the MCC, which did work (although again undocumented), for something which does not and is also absent of any documentation.

---

### Post by nickrout on 2012-03-11
Ahh your rant is about the lack of mythbuntu documentation, not mythtv itself. I see now.

mythbuntu had quite a good install guide pdf but it got abandoned a while ago (guessing 3-4 ubuntu cycles at least).

But yes the stuff that mythbuntu adds like MCC, bare et al is poorly documented.

I am not sure of the need for bare when the mythtv guys provide such a good and well documented backup/restore utility.

By the way the mythtv (as opposed to mythbuntu) release notes are very thorough. 

yes it can be a pain to go through the mythtv documentation, and the wiki manual, and the mailing list archives, and this forum , abd mythtvtalk, and more to figure out mythtv and then work out where the mythbuntu software fits in to the picture.

Frankly if you want a specific mythtv box, try LinHES.

---

### Post by markofealing on 2012-03-11
> **tgm4883 said:**
> Can you attach one of the backups that you did in the backup and restore utility (in the mythbuntu-control-centre)? It will have your mythtv password in there and likely your database, so if you would rather pm me or open a private bug on launchpad that is fine. It would help to look at it to figure out why it isn't being recognized. Is it throwing any errors?

No problem, I've [uploaded the file to Google docs]("https://docs.google.com/open?id=0B2ltE62QIxqrUk45WWR1RHhTVzZEQi1aUkNDN1YxZw") as it is 11Mb in size, the forum limits uploads to 1mb.

I've also configured a second test Mythbuntu PC, same problems with getting bare working, which I've documented for a blog post (yet to be posted until I can get bare to work) as the fix is slightly different (it seems) for a new install. Bare fails to work on either PC and it might be due to bare not installing properly in the first place.

Also bare will not backup, although mythbuntu still seems to be running it's own backups on a weekly schedule. Not sure how this is still working as it was originally setup through the MCC, but at least it does work. This existing backup does not appear in the bare schedule (see screenshot attached), I assume it should be appearing.

The mythbuntu-bare.conf file looks like the following on my test box. The backup is being stored on a data drive, which is also where the recording are stored.

[General]
serverip = 192.168.1.104
serverport = 52392
managed = True
revision = 0
serverstoragedir = /media/Data/mythtv/db_backup
checksum = 0d4888de6f3be80b9c89dfa76a1bea864daff08d

[Backup]
storagedir = /media/Data/mythtv/db_backup
db = 1
schedule = daily
weekday = *
day = *
hour = 18
minute = 00

---

### Post by markofealing on 2012-03-11
> **nickrout said:**
> Ahh your rant is about the lack of mythbuntu documentation, not mythtv itself. I see now.

mythbuntu had quite a good install guide pdf but it got abandoned a while ago (guessing 3-4 ubuntu cycles at least).

But yes the stuff that mythbuntu adds like MCC, bare et al is poorly documented.


MythTV is generally good, documentation could be more up to date. I did look at Linhes some years back when I was struggling to get mythbuntu working, at the time documentation on getting the UK EPG working was almost non-existent and pulling down the EPG via XMLTV was and still is a nightmare and as the EPG in the UK is so good a rather pointless exercise.

It was because of the pain I had with getting Mythbuntu up and running, I decided to start my linux blog.

Whilst the backup scripts are well documented, at a time of crisis when you just want to restore you backup, reading what is a technical manual for what should be a one-off exercise is not really the right way of doing things. Hence my desire to document and get bare working.

Furthermore, for the purpose of a basic restore, I fail to see why the simple restore process mentioned earlier in this post is not part of the wiki documentation i.e. simple backup and restore. I believe it used to be before it was replaced by the python script documentation.

---

### Post by tgm4883 on 2012-03-11
This is probably a better place to respond than that document.

Unfortunately I wasn't able to document this utility at all. Life happened and I wasn't even able to finish some of the features I had in mind (or the documentation). As I have a bit more time now I hope to get some of it documented.

There really was little changed between the 11.04 and 11.10 versions. The server portion was added, but doesn't need to be installed on each machine, it's a central management program and has zero to do with the actual backup and restore of the files (that is left to the client). That said, because I didn't get to finish portions of it and I don't really like how it works, I'll be hiding the functionality of that in the client for 12.04. The client however should work the same was as it has previously.

The scripts being not executable is an unfortunate bug. As I don't have the time to frequent the forums as much, and I don't see a bug filed at [http://launchpad.net/mythbuntu](http://launchpad.net/mythbuntu) I assumed it was working properly. This should also be resolved in a future build. 

The file that you uploaded to google docs wasn't created using the backup and restore utility (it appears to have been created using the cmd line scripts provided by the mythtv team). That is why it doesn't recognize the backup file.

---

### Post by nickrout on 2012-03-11
> **tgm4883 said:**
> This is probably a better place to respond than that document.

Unfortunately I wasn't able to document this utility at all. Life happened and I wasn't even able to finish some of the features I had in mind (or the documentation). As I have a bit more time now I hope to get some of it documented.

There really was little changed between the 11.04 and 11.10 versions. The server portion was added, but doesn't need to be installed on each machine, it's a central management program and has zero to do with the actual backup and restore of the files (that is left to the client). That said, because I didn't get to finish portions of it and I don't really like how it works, I'll be hiding the functionality of that in the client for 12.04. The client however should work the same was as it has previously.

The scripts being not executable is an unfortunate bug. As I don't have the time to frequent the forums as much, and I don't see a bug filed at [http://launchpad.net/mythbuntu](http://launchpad.net/mythbuntu) I assumed it was working properly. This should also be resolved in a future build. 

The file that you uploaded to google docs wasn't created using the backup and restore utility (it appears to have been created using the cmd line scripts provided by the mythtv team). That is why it doesn't recognize the backup file.

Thomas, perhaps this would be a good opportunity to explain the difference between bare and the mythtv developers' script on the mythtv wiki.

---

### Post by tgm4883 on 2012-03-11
> **nickrout said:**
> Thomas, perhaps this would be a good opportunity to explain the difference between bare and the mythtv developers' script on the mythtv wiki.

Nick, you are probably correct.

The provided mythtv scripts backup the database only.  There are no additional files backed up when using those scripts.

Mythbuntu bare backs up the database as well as some additional files. I'd have to look up the the list of files to be specific, but for instance it will also backup lirc conf files, mythtv conf files, etc. It does not backup media files though. To backup the database file, it does actually use the mythtv backup script. For the rest of the files, it just uses tar and gzip.

---

### Post by nickrout on 2012-03-11
> **tgm4883 said:**
> Nick, you are probably correct.

The provided mythtv scripts backup the database only.  There are no additional files backed up when using those scripts.

Mythbuntu bare backs up the database as well as some additional files. I'd have to look up the the list of files to be specific, but for instance it will also backup lirc conf files, mythtv conf files, etc. It does not backup media files though. To backup the database file, it does actually use the mythtv backup script. For the rest of the files, it just uses tar and gzip.

Thanks, those additions are probably worthwhile for a mythbuntu user, but will not be much use elsewhere as other distros handle lirc configuration differently.

And as for backing up media - you'd need a pretty big backup medium on most myth systems. 


On that topic, have you thought about different default partitioning and file locations for mythbuntu systems?

---

### Post by yonkiman on 2012-03-25
> **ijumpship said:**
> When mine got screwed,I just paste this on the Wall,got drunk and I did not know what I did but it got restored

LOL!  That describes my 4 years of experience with MythTV/linux - I've done a lot by have no idea how I did it.

Except that I got a lot of advice from people who DID know what they were doing (thanks to them).

---


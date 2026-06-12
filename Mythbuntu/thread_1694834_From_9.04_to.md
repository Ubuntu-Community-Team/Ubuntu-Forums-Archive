---
title: "From 9.04 to ?"
date: 2011-02-24
forum: Mythbuntu
---

### Post by mookie60 on 2011-02-24
currently running 9.04 using:
- old HP dc7100, 2.6ghz cpu, 1Gb ram
- Nvidia 8400gs 
- Happaugue 1600 (uses both analog and digital)
- pchdtv 5500 (uses only dig tuner, the analog died)


I have mostly followed the "if it ain't broke, don't fix it" rule -  so I've been reluctant to upgrade from 9.04.  But now that 9.04 is now longer supported, I guess it's time to do something.   10.04 or 10.10 ? 

Because things have worked so well during the past year and a half, I have to admit that I haven't followed the forum very closely.   I checked 1600's myth page (still need to check same for 5500) and didn't see anything that would be a problem with either 10.04 or 10.10.    

I'm leaning towards 10.04, mostly because of the long term support (does that apply to Myth, or just Ubuntu?), but don't want to rule out 10.10 if it hasn't had many quirks/bugs. 

Any known reasons either version would have a problem with the above listed hardware?  I guess the same questions goes for which version of Myth to use.

Thanks for any thoughts on the matter,

---

### Post by AlecJ on 2011-02-25
> **mookie60 said:**
> currently running 9.04 using:
- old HP dc7100, 2.6ghz cpu, 1Gb ram
- Nvidia 8400gs 
- Happaugue 1600 (uses both analog and digital)
- pchdtv 5500 (uses only dig tuner, the analog died)


I have mostly followed the "if it ain't broke, don't fix it" rule -  so I've been reluctant to upgrade from 9.04.  But now that 9.04 is now longer supported, I guess it's time to do something.   10.04 or 10.10 ? 

Because things have worked so well during the past year and a half, I have to admit that I haven't followed the forum very closely.   I checked 1600's myth page (still need to check same for 5500) and didn't see anything that would be a problem with either 10.04 or 10.10.    

I'm leaning towards 10.04, mostly because of the long term support (does that apply to Myth, or just Ubuntu?), but don't want to rule out 10.10 if it hasn't had many quirks/bugs. 

Any known reasons either version would have a problem with the above listed hardware?  I guess the same questions goes for which version of Myth to use.

Thanks for any thoughts on the matter,

10.04 Lts for me, have desktops on 10.10, when they are VERY stable I will upgrade.
follow the instructions on the Mythbuntu website saving your database, and do a clean install, the upgrade online was not fun, I ended up doing a clean install and reloading my database with the channels and recording etc..
I backed up to a USB Key, then if 10.04 did'ent work I could go back without the the pain, but it does and it's well worth it.

---

### Post by LowSky on 2011-02-25
why not wait it out and grab 11.04 in a little over a month

---

### Post by Evil-Ernie on 2011-02-25
I jumped from 9.10 (Karmic) to 10.10 (Maverick) and I love 10.10! Its been steady as a rock and really nice and easy to install.

Looking forward to getting my hands on 11.04 but then if you think your machine is getting long in the tooth a LTS release (10.04) is probably your best bet. 

Personally I always try a live disc before I do a full install just to be on the safe side.

---

### Post by mookie60 on 2011-02-26
A lot of my reservations stem from unsuccessful attempts to backup/restore the database.  The early failures weren't that big a deal as I didn't have much time on the box.  But this time it's almost 2 years worth of data that would be lost.  This is the main reason I'm shying away from the upcoming 11.04.

I made cds of both 10.04 and 10.10, so testing out each in the live CD version sounds like a good idea.   If I'm running from the CD, and want to test the recording capability of the tuner cards, how do I store the recordings?  Does the liveCD let me setup a storage directory on my hard drive?

Does 10.04 or 10.10 include a simple (GUI) way to backup/restore the database?

Thanks for the input.

---

### Post by Archmage on 2011-02-26
> **mookie60 said:**
> I have mostly followed the "if it ain't broke, don't fix it" rule -  so I've been reluctant to upgrade from 9.04.  But now that 9.04 is now longer supported, I guess it's time to do something.

In this case I can only suggest the 10.04 for you. This way you only have to upgrade each 2 years. (or even later)

---

### Post by mookie60 on 2011-02-26
I tried to just run as a liveCD, but it only proved the OS will load.   It seems the only way to test myth this way is as a frontend only.  This appears to require a running backend, which I don't have as this is the same machine as my main FE/BE.  So I could find no way to start myth and test my hardware.

In particular I was concerned with my Hap. 1600 MCE remote.  I'd heard about problems (some remotes) with the newer kernels (2.26.35 and later).  The bug page for this doesn't show it resolved, so with no easy way to check this under a live CD, I guess 10.04 is the safer choice. 

Thanks for the input.

---

### Post by itlarson on 2011-02-27
I've done a clean install and restored the database several times.  Although a couple of times this resulted a descent into "mysql hell". with help from the forums, I have always managed to restore all my recordings.  Here's my quick synopsis on how to do this.  Hopefully people more Knowledgeable than myself fill in where I am unclear, or uncertain.   

The following assumes you have a separate partition for root.  If everything is in the same partition, you will need to move your data and the operating system to separate drives or partitions before you can proceed.

First read the following page:
[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)
It goes into detail on how to use the backup and restore scripts.  

It is helpful to know that there are two passwords you need to be concerned with.  The first is the root mysql password, which is not related to Linux's root password. It is left blank by default, so don't type anything in the place it would go if it was set.  I'm pretty sure this password is left unset in a default mythtv install.

The second password is the password for your database "mythconverge", where all your programs are kept track of.  You can find out the current password for mythconverge by looking in the frontend settings under "general".  You need to write this down before you start.  

To backup the database, download the scripts from the page I gave you above.  Run:
 echo "DBBackupDirectory=<DESIRED BACKUP DIRECTORY>" > ~/.mythtv/backuprc
to set the directory where backups go. You need to substitute a valid directory path for <DESIRED BACKUP DIRECTORY>. Then run:
mythconverg_backup.pl  
or
perl mythconverg_backup.pl  
if you haven't made it executable.
Now copy the database file which was just created onto a flash drive to be safe. 

At this point you should also make sure you know where all your partitions are mounted.  Use df -h  to find this out and write it down if it is complicated.  Also make sure you know the path of all your storage directories.

You can now install the new operating system.  You will have to use the custom partitioning option when you install.  Be carefull to set the mount-points the same as before, and to only format the root partition. 

Once you have a working operating system, you can restore the database.  Here are my personal notes on how to do the database restore.  My understanding of this is not complete, and hopefully other will be able to clarify.  You should substitute the database password you wrote down above for 'mythtv_password' in the fourth command.  You can use perl mythconverg_restore.pl in place of the last command in lieu of making it executable.

1)Drop the current database:
mysql -uroot -p -e 'DROP DATABASE IF EXISTS mythconverg;' 

2)Create the initial database:
mysql -uroot -p < database/mc.sql 

3)Loggin to mysql as root  <root mysql password>  should be blank:
mysql -uroot -p<root_mysql_password> mysql 

4)set myth database password to the old password, replacing <mythtv_password> with the one you wrote down: 
mysql> UPDATE user SET Password=PASSWORD('<mythtv_password>') WHERE user='mythtv';  

5)
mysql> FLUSH PRIVILEGES;

6)exit to bash
mysql> exit  

7)set path to directory containing the backup file:
echo "DBBackupDirectory=<DESIRED BACKUP DIRECTORY>" > ~/.mythtv/backuprc

8 )restore the database:
mythconverg_restore.pl 

Now the data base should be restored, but there's a few things you still need to do.  First check permissions on your storage directories.  If they can't be written to, neither live TV or recording will work.  I think they are supposed to belong to user "mythtv", but my half-assed way of dealing with this has always been to set their permissions to 777.  Now go into the backend settings, and make sure your tuner setup looks ok, and storeage groups are set properly. I think restoring the database restores these settings, but I don't remember.  Now you can start the frontend.  I seem to remember that you get a setup screen when you start the frontend if it doesn't know the right password for the database.  Set the password to the one from the old install, the same one you used in the forth line above.  Now if everything worked, you should be able to watch your recorded shows, and record TV.

---

### Post by itlarson on 2011-02-27
Having gone over the wiki a bit more, I'm wondering the restore procedure could be streamlined as follows:

1)
mythconverg_restore.pl --drop_database --create_database --filename <backup file>

2)set the password in frontend to the one you wrote down.

The directions I gave above must be out of date.  They should still work, but it looks like dropping and recreating the database are now handled by the script.

---

### Post by matt06 on 2011-02-27
> **mookie60 said:**
> I have mostly followed the "if it ain't broke, don't fix it" rule -  so I've been reluctant to upgrade from 9.04.  But now that 9.04 is now longer supported, I guess it's time to do something.

I'm wondering why you want to upgrade at all.  Is it to get a new(er) version of MythTV?  Compelling additional features?

I run a 9.10 system and 0.23.1-fixes with the 1600 in my backend and 8400GS in my frontend.  Actually pretty glad that I didn't take the 10.xx plunge and for a Myth system, I'm not too concerned with updates or being "supported".  That said, I would eventually like to move to 0.24 and beyond, but not wanting to rock the boat since it's been fairly smooth sailing.

---

### Post by tgm4883 on 2011-02-27
> **matt06 said:**
> I'm wondering why you want to upgrade at all.  Is it to get a new(er) version of MythTV?  Compelling additional features?

I run a 9.10 system and 0.23.1-fixes with the 1600 in my backend and 8400GS in my frontend.  Actually pretty glad that I didn't take the 10.xx plunge and for a Myth system, I'm not too concerned with updates or being "supported".  That said, I would eventually like to move to 0.24 and beyond, but not wanting to rock the boat since it's been fairly smooth sailing.

Being "Supported" is mostly about the ability to get updates, most importantly, security updates.

I usually recommend sticking with LTS releases. MythTV versions can be updated using the [mythbuntu-repos]("http://www.mythbuntu.org/repos"). Starting with 10.04, we will build all future MythTV releases for each LTS release until the next LTS release, unless some dependency issue crops up in 10.04 that we would be unable to accommodate.

---

### Post by mookie60 on 2011-02-27
I.T. - thanks so much for the detailed info.  that's going to take some digesting.   if the scripts are now handling a lot of the steps, that will probably be a safer way for me to go.  i always seem to get tripped up in commandline syntax.   at least with a good backup in hand, i know i can take as many whacks at it as necessary. 

Matt - as tgm4883 says, it's mostly about the security updates.  i've also read there's new and improved drivers for the 1600 (though i guess this could be installed without a new o.s.).  i also watch Hulu or Megavideo via Firefox and no longer get the browser & flash updates, so sometimes things don't work.   i don't take this step lightly, but i figure it's time to face the fears and just do it.

---

### Post by mymythtv on 2011-02-28
Hi

I'll go for 10.04 LTS.
Running that myself on a BE/FE, and it's pretty stable. Just upgraded mythtv from 0.23.1 to 0.24 last week.

On the other side - my kernel is still 2.6.31-22-generic as 2.6.32 gave some problems with stuttering/freezing playback on a Nvidia 8400GS.
Tried to upgrade Nvidia driver, but no luck..
Found a thread last summer about other having same problems, but it never got solved ( some said that upgrade kernel to 2.6.35 solved the problems.

When time permits, I'll try to look into it again, but if it's working, don't break it.

Also have a frontend Zotac ID11 running 10.10 with no problems, so both 10.04 and 10.10 af good to go...

---

### Post by mookie60 on 2011-02-28
I installed 10.04 and did all the updates.  When I ran  mythconverg_restore.pl (thankfully itlarson had pointed out the need for the --drop and --create options), it finished say it was successfully restored.   I restarted the backend, then started the frontend and could see all my recordings.

As I'm still messing around with a vmalloc issue (separate post), I rebooted the machine.  After that I can no longer get into myth.  When I attempt to launch the frontend, I get the setup page, the one that starts with selecting the preferred language.  When I get to the page with the database info, my original (from the backup) dbase password is there, as are the correct name and user.  The ip is 'localhost'.   I tried the box's actual ip, didn't help.   Myth just displays "can't login".

Any help is greatly appreciated.

---

### Post by itlarson on 2011-02-28
could this be some kind of permissions thing?  When you reinstall users don't necessarily get the same UID.

---

### Post by mookie60 on 2011-02-28
My username (myth) has a UID of 1000
mythtv is 111

I don't know what "myth's" UID was before.  If it's important that the UID be the same as it was, would that be in the database somewhere?  more importantly, somewhere i can access it?

---

### Post by tgm4883 on 2011-02-28
> **mookie60 said:**
> I installed 10.04 and did all the updates.  When I ran  mythconverg_restore.pl (thankfully itlarson had pointed out the need for the --drop and --create options), it finished say it was successfully restored.   I restarted the backend, then started the frontend and could see all my recordings.

As I'm still messing around with a vmalloc issue (separate post), I rebooted the machine.  After that I can no longer get into myth.  When I attempt to launch the frontend, I get the setup page, the one that starts with selecting the preferred language.  When I get to the page with the database info, my original (from the backup) dbase password is there, as are the correct name and user.  The ip is 'localhost'.   I tried the box's actual ip, didn't help.   Myth just displays "can't login".

Any help is greatly appreciated.

Is the backend service actually started?

```
service mythtv-backend status
```

---

### Post by mookie60 on 2011-02-28
the result of the status query was as follows:

   mythtv-backend start/running, process 6793

thanks

---

### Post by tgm4883 on 2011-02-28
> **mookie60 said:**
> the result of the status query was as follows:

   mythtv-backend start/running, process 6793

thanks

Does restarting mythfrontend resolve the issue?

---

### Post by mookie60 on 2011-02-28
Unfortunately not.   I've stopped/started the backend.   The frontend takes a long time to get going before I get the setup screens.  There is a "no UPnP" error, but I don't know if that's significant.

For the IP, I've tried: localhost, 127.0.0.1, 192.168.1.108 (the machine's current IP), 192.168.104 (the IP for the old database/machine).

... let me switch to the problem machine, and I'll see if I can get some applicable log data

---

### Post by mookie60 on 2011-03-01
backend log:

................................................................................
2011-03-01 00:01:48.380 UPnPautoconf() - No UPnP backends found
2011-03-01 00:01:48.402 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2011-03-01 00:01:48.453 Deleting UPnP client...
2011-03-01 00:01:49.085 Failed to init MythContext, exiting.
2011-03-01 00:01:49.154 mythbackend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2011-03-01 00:01:49.155 Using runtime prefix = /usr
2011-03-01 00:01:49.198 Using configuration directory = /home/mythtv/.mythtv
2011-03-01 00:01:49.213 Empty LocalHostName.
2011-03-01 00:01:49.221 Using localhost value of myth-desktop
2011-03-01 00:01:49.246 New DB connection, total: 1
2011-03-01 00:01:49.257 Unable to connect to database!
2011-03-01 00:01:49.262 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2011-03-01 00:01:51.835 UPnPautoconf() - No UPnP backends found
2011-03-01 00:01:51.859 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2011-03-01 00:01:51.909 Deleting UPnP client...
2011-03-01 00:01:52.542 Failed to init MythContext, exiting.
2011-03-01 00:01:52.608 mythbackend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2011-03-01 00:01:52.609 Using runtime prefix = /usr
2011-03-01 00:01:52.610 Using configuration directory = /home/mythtv/.mythtv
2011-03-01 00:01:52.619 Empty LocalHostName.
2011-03-01 00:01:52.627 Using localhost value of myth-desktop
2011-03-01 00:01:52.647 New DB connection, total: 1
2011-03-01 00:01:52.658 Unable to connect to database!
2011-03-01 00:01:52.660 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)




frontend log:

Starting mythfrontend.real..
2011-02-28 23:58:52.899 mythfrontend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2011-02-28 23:58:52.900 Using runtime prefix = /usr
2011-02-28 23:58:52.900 Using configuration directory = /home/myth/.mythtv
2011-02-28 23:58:53.593 Empty LocalHostName.
2011-02-28 23:58:53.596 Using localhost value of myth-desktop
2011-02-28 23:58:53.606 New DB connection, total: 1
2011-02-28 23:58:53.609 Unable to connect to database!
2011-02-28 23:58:53.609 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2011-02-28 23:58:55.796 UPnPautoconf() - No UPnP backends found
2011-02-28 23:58:55.796 No UPnP backends found
2011-02-28 23:58:55.798 Primary screen: 0.
2011-02-28 23:58:55.798 Using screen 0, 1024x768 at 0,0
2011-02-28 23:58:55.798 Could not find theme:  - Switching to Terra
2011-02-28 23:58:55.799 Using theme base resolution of 1280x720
2011-02-28 23:58:55.808 Desktop video mode: 1024x768 60.006 Hz
2011-02-28 23:58:56.152 get_ip: Name or service not known
2011-02-28 23:58:56.152 LIRC, Error: Failed to parse IP address ''
2011-02-28 23:58:56.152 JoystickMenuThread Error: Joystick disabled - Failed to read /home/myth/.mythtv/joystickmenurc
2011-02-28 23:58:56.167 Using Frameless Window
2011-02-28 23:58:56.167 Using Full Screen Window
2011-02-28 23:58:56.173 Using the Qt painter
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
2011-02-28 23:59:07.717 Writing settings file /home/myth/.mythtv/mysql.txt
2011-02-28 23:59:07.718 Closing DB connection named 'DBManager0'
2011-02-28 23:59:07.722 Closing DB connection named 'DBManager0'
2011-02-28 23:59:07.722 Unable to connect to database!
2011-02-28 23:59:07.722 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

2011-02-28 23:59:07.723 Cannot login to database?
2011-02-28 23:59:07.723 Cannot login to database?
2011-02-28 23:59:08.040 Primary screen: 0.
2011-02-28 23:59:08.040 Using screen 0, 1024x768 at 0,0
2011-02-28 23:59:08.041 Using theme base resolution of 1280x720
2011-02-28 23:59:08.042 get_ip: Name or service not known
2011-02-28 23:59:08.042 LIRC, Error: Failed to parse IP address ''
2011-02-28 23:59:08.042 JoystickMenuThread Error: Joystick disabled - Failed to read /home/myth/.mythtv/joystickmenurc
2011-02-28 23:59:08.058 Using Frameless Window
2011-02-28 23:59:08.058 Using Full Screen Window
2011-02-28 23:59:08.095 Using the Qt painter
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
2011-02-28 23:59:13.242 User cancelled database configuration
2011-02-28 23:59:13.250 Failed to init MythContext, exiting.
2011-02-28 23:59:13.250 Deleting UPnP client...

---

### Post by mookie60 on 2011-03-01
I'll mark this as solved, though it isn't.

I'm just giving up.

---

### Post by itlarson on 2011-03-01
Don't give up!  Try resetting the password like in my first post.

---

### Post by Animal X on 2011-03-01
I started with 9.04 and I had to fix stuff but it was solid, I read about all the troubles people had upgrading instead of doing fresh installs for 9.10 and 10.04. I just went straight to a fresh install 10.10 and everything worked, even gyach.

---

### Post by itlarson on 2011-03-05
You were able to get the database restored?  Could you describe how you did this, since you've done it much more recently than me?

I am hoping that someday that database restore will be built into the install, so all yo you have to do is point the installer at the right backup file, and everything will be taken care of automatically.

---


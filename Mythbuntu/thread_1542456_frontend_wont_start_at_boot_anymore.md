---
title: "frontend wont start at boot anymore"
date: 2010-07-30
forum: Mythbuntu
---

### Post by Sctmon on 2010-07-30
My Mythtv system had been working well but today the frontend stopped starting automatically when the computer boots. It is listed in the startup applications and will start when I click on the menu entry or run it in terminal.
If I log out of my user account and then log back in it will start up automatically, just not when the computer first boots.

I had changed the configuration of the tv and monitor that are connected but have since returned everything to the way they were. I am sure this was the cause of the trouble.

---

### Post by codymyth on 2010-07-30
in The mythtv control center there is a check box you can check that tells it to start up on boot. Perhaps if you uncheck that and apply or restart and then check it again it will work?

---

### Post by Sctmon on 2010-07-31
I had not tried that, just removing and manually re adding the application in the startup applications but a restart in between did not help.
I did notice an unknown application that was still running when I tried to shutdown and checked the system monitor which indicates that the frontend is running at boot but sleeping.
I am just waiting for my wife to finish watching something so I can hunt for the log files and see what is happening.

If I end the process that is sleeping and run the front end again it starts normally.
possibly the frontend is trying to start up before some important service is up and running?

---

### Post by Sctmon on 2010-07-31
It seems that the frontend is starting at boot but about 50% of the time the process terminates and the rest of the time it continues to run but does nothing.

This is the log file for when it runs and terminates at boot.

Starting mythfrontend.real..
2010-07-31 09:58:02.616 mythfrontend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-07-31 09:58:02.616 Using runtime prefix = /usr
2010-07-31 09:58:02.616 Using configuration directory = /home/scott/.mythtv
2010-07-31 09:58:02.617 MediaRenderer::HttpServer Create Error
2010-07-31 09:58:02.618 Empty LocalHostName.
2010-07-31 09:58:02.618 Using localhost value of MythtvFrontend
2010-07-31 09:58:02.619 Testing network connectivity to '192.168.0.6'
2010-07-31 09:58:02.658 New DB connection, total: 1
2010-07-31 09:58:02.659 Connected to database 'mythconverg' at host: 192.168.0.6
2010-07-31 09:58:02.660 Closing DB connection named 'DBManager0'
2010-07-31 09:58:02.728 ScreenSaverX11Private: Gnome screen saver support enabled
2010-07-31 09:58:02.729 DPMS is active.
2010-07-31 09:58:02.730 Primary screen: 0.
2010-07-31 09:58:02.731 Connected to database 'mythconverg' at host: 192.168.0.6
2010-07-31 09:58:02.732 Using screen 0, 1280x1024 at 0,0
2010-07-31 09:58:02.829 Desktop video mode: 1280x1024 75.03 Hz
2010-07-31 09:58:02.866 MythUI Image Cache size set to 20971520 bytes
2010-07-31 09:58:02.928 AudioPulseUtil, Warning: Can not connect to sound server, can not suspend.
            Connection refused
2010-07-31 09:58:02.928 ERROR: ***Pulse Audio is running!!!!***
2010-07-31 09:58:02.928 ERROR: But MythTV was not able to suspend it. EXITING!
2010-07-31 09:58:02.928 Deleting UPnP client...


It seems like it is trying to start up before the network connection is established so I added 'sleep 5' into the start of /usr/bin/mythfrontend and it all works now. 5 seconds seem to be the least I can get away with to allow it to start normally.

What I cannot figure out is why after about 6 months of completely normal operation, it seems to be taking longer for the networking to be established. I have not made any changes other that the regular ubuntu updates.

---

### Post by nickrout on 2010-08-01
These lines seem to be a clue :)

> 2010-07-31 09:58:02.928 AudioPulseUtil, Warning: Can not connect to sound server, can not suspend.
Connection refused
2010-07-31 09:58:02.928 ERROR: ***Pulse Audio is running!!!!***
2010-07-31 09:58:02.928 ERROR: But MythTV was not able to suspend it. EXITING!
2010-07-31 09:58:02.928 Deleting UPnP client...


---

### Post by Sctmon on 2010-08-01
I guess I just figured that was an error caused by the network connection not being up before the frontend tried to start, not a cause of the problem. Especially as a 5 second delay before running the frontend seems to solve it.
I will have a go at removing pulse audio and see what happens.

---

### Post by Sctmon on 2010-08-01
Well, it worked. No pulse audio and no delay needed on startup.

I can't figure out if pulse audio had always been installed or just crept in somewhere.

---

### Post by kyphos on 2010-12-03
@sctmon,
Tonight out of the blue, my myth frontend stopped launching at boot, just as you encountered in July. My log has exactly the same report about Pulse Audio running, mythtv unable to suspend it, EXITING.

What's Pulse Audio?
How did you get rid of it?
Did you ever figure out how it got added in?

Thanks.

---

### Post by thatguruguy on 2010-12-03
kyphos, are you running myth .24?  If so, it doesn't stop pulseaudio, because it doesn't need to.

---

### Post by kyphos on 2010-12-03
Mr. Guru,
Nope. I'm still on 0.23 (I installed from Mythbuntu 10.04 LiveCD three weeks ago). 
  
System has been working fine, until tonight when it froze. I had to reboot, and then the FE failed to launch after booting.

Tx.

---

### Post by Sctmon on 2010-12-04
Pulse audio is part of system and will always have been there. I never figured out why it  could not be suspended so I just removed it.

open a terminal window and type:

   sudo apt-get remove pulseaudio

If you just use the computer as a frontend then it is fine but you may have problems if you use other audio apps on the same computer.

Scott

---

### Post by thatguruguy on 2010-12-04
Or, upgrade to .24, which has much better pulseaudio support.

---

### Post by Sctmon on 2010-12-04
I am sure you know it is not as simple as just upgrading. I have my mythtv system working well at the moment and every upgrade I have tried in the past always resulted in a series of major issues which resulted in either having to do clean installs on all my machines and basically starting from scratch or restoring my old backups.

My last attempt at installing 10.10 on one of my frontends left it unable to communicate with the backend (10.04) because the network protocols had been changed. Backend using version 56 and frontend only understands V 23056

---

### Post by thatguruguy on 2010-12-04
I didn't say anything about upgrading mythbuntu to 10.10, I was referring to upgrading mythtv to .24.

It's a lot easier to upgrade the mythtv package than it is to set up a whole new OS.

And yes, your frontends all need to be running the same version of mythtv as the backend. I run mythtv .24 on ubuntu 10.04 on my two remote frontends, and mythtv .24 on mythbuntu 10.10 on my backend/frontend mythbox.  The package of mythtv has to match between the various computers, not the entire OS.

---

### Post by kyphos on 2010-12-04
> **thatguruguy said:**
> Or, upgrade to .24, which has much better pulseaudio support.

I tried 0.24 a couple of weeks ago. It was a major disaster. I spent several hours troubleshooting and eventually surrendered. I am brand-new to Ubuntu and was way over my head trying to figure out what was wrong.  I ended up doing a clean install of Mythbuntu 10.04 to get to where I am today.  It was working just fine until last night, when out of the blue, the front-end wouldn't start after boot, apparently due to this interaction with pulseaudio.

@scott,
Am I correct in concluding that PulseAudio not required for for mythtv? I only use my myth system as a combined front-end/back-end. Having to manually launch myth front-end from the desktop severely impairs usability, so if I have to get rid of it, I will. 

I found this in user.log. Seems to indicate that pulseaudio is unhappy about something. 

```
Dec  3 19:06:06 myth-box pulseaudio[1805]: module-alsa-card.c: Failed to find a working profile.
Dec  3 19:06:06 myth-box pulseaudio[1805]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Dec  3 19:06:06 myth-box pulseaudio[1928]: pid.c: Daemon already running.
Dec  4 10:28:56 myth-box pulseaudio[1749]: module-alsa-card.c: Failed to find a working profile.
Dec  4 10:28:56 myth-box pulseaudio[1749]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Dec  4 10:28:57 myth-box pulseaudio[1892]: pid.c: Daemon already running.
```

---

### Post by Sctmon on 2010-12-04
> **thatguruguy said:**
> I didn't say anything about upgrading mythbuntu to 10.10, I was referring to upgrading mythtv to .24.

It's a lot easier to upgrade the mythtv package than it is to set up a whole new OS.

And yes, your frontends all need to be running the same version of mythtv as the backend. I run mythtv .24 on ubuntu 10.04 on my two remote frontends, and mythtv .24 on mythbuntu 10.10 on my backend/frontend mythbox.  The package of mythtv has to match between the various computers, not the entire OS.


I am relatively new to all this myself, how do you update the mythtv package? I do seem to be running .23 on all the computers.

Just backing up now in anticipation!

---

### Post by Sctmon on 2010-12-04
> **kyphos said:**
> 
@scott,
Am I correct in concluding that PulseAudio not required for for mythtv? I only use my myth system as a combined front-end/back-end. Having to manually launch myth front-end from the desktop severely impairs usability, so if I have to get rid of it, I will. 




I have certainly not had any problems after removing pulse audio from 2 of my computers, the others are all working happily with is still there and successfully suspending it.

If you are having problems and only use the computer as a mythtv system then it should be fine to remove it.

---

### Post by kyphos on 2010-12-04
> **Sctmon said:**
> I am relatively new to all this myself, how do you update the mythtv package? I do seem to be running .23 on all the computers.

Just backing up now in anticipation!

@scott,
I can answer your question, thanks to guidance I received here a couple weeks ago. First, open up Mythbuntu Control Center and see if there is an option "Repositories". If so, jump down a paragraph.  If not,  you need to download the Mythbuntu-repos repository, found here:
[http://www.mythbuntu.org/files/mythbuntu-repos.deb](http://www.mythbuntu.org/files/mythbuntu-repos.deb)

You do this on your system running myth (not on another PC or Mac).  Once the .deb file downloads (using Firefox), the package manager should automatically open it and install it into the list of repositories that will subsequently be used for updating.

Then you launch the Mythbuntu Control Center.  You should find a new option in the list at the right: "Repositories". You want to check off "Activate MythTV repository" and "Activate Mythbuntu Updates respository".  Next, you select which version of MythTV you want to stay current with: 0.23, 0.23.1, or 0.24.   

Finally, you select **System Updates** from the MCC menu, and click on **Update Manager**.  (or just choose Applications/System/Update Manager.  This will search all of the repositories that have been specified (Ubuntu, Myth, etc), display a list of all the updates available, and give you the opportunity to choose which to download and install.  


Regarding backups, I haven't figured that out yet. It's next on my list to figure out once I can get myth working.  What's the best approach?

Thanks.

---

### Post by Sctmon on 2010-12-05
Am I correct in assuming that if I am currently using .23 I can upgrade to .24 by changing the version number in the repositories part of the MCC?

Regarding backups, I wrote a backup script that creates a database backup if run on the backend and then a complete system backup. I will post it here after I get a chance to add a couple of handy comments and tidy it up a bit.

---

### Post by kyphos on 2010-12-05
@scott,
Yep - change the version number on the MCC/Repositories page, and then run Update Manager.  That's all I did to upgrade from 0.23 to 0.23.1.  Note however that Update Manager will download and install current updates for everything**: Linux kernel, security fixes, patches to Apache, etc. If you're the cautious type, you can unselect updates you don't want so you can focus on making changes in one place at a time.

(** clarification:  if you're running with 10.04, it won't upgrade your system to 10.10, merely give you all the patches and fixes for 10.04).

---

### Post by Sctmon on 2010-12-05
This is the backup script I wrote :

[http://dl.dropbox.com/u/9052836/Backup.sh](http://dl.dropbox.com/u/9052836/Backup.sh)

It was written to run on my system so there may be a bit of tweaking required to get it to work on another.
It basically asks if you want to backup the Mythtv database if you are running it on the backend and then asks if you want to backup the whole system. This is done by using the tar utility to create an archive containing all of the files on the system drive excluding a few that you don't need to backup.

This is where I got it from so no point in explaining it all again, it also explains how to restore your system which my script does not cover.
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

My computer running the backend has an external eSata drive attached which is shared and mounted at media/MyStuff on all my machines. The script is run from that drive and backs up which ever system you run it on onto another folder on that drive. If you run the script on the backend you also have the option of backing up the mythtv database although if you are performing a complete system backup it is not really required but I like to do it all the same.

The folder containing the backup script also has the mythconverg_backup.pl and mythconverg_restore.pl scripts which I downloaded here. There are also instructions on how to setup the backup path for the database
[http://www.mythtv.org/wiki/Database_Backup_and_Restore#Script-based_Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore#Script-based_Database_Backup_and_Restore)
The download links don't seem to work anymore though but I can upload the then if you need them. The ones installed with my system were out of date and the restore script didn't work.

You will need to set up the backend hostname and all the paths you are going to use, all helpfully located at the beginning of the script.

It is my first script so run it with caution and please read it carefully before hand to make sure all your paths are set correctly.
You will need to run the script as root otherwise it won't be able to access some of the files it needs to archive so sudo su first!

---

### Post by kyphos on 2010-12-05
@ scott.
Awesome. Thanks (and thanks for popping it in your dropbox :-)
You just saved me a ton of time googling around.  I've been reticent about upgrading to 0.24 until I backed up what I have 'working' now. It's taken me 3 weeks and I don't want to risk regressing.

Now back to my Sunday assignment:  figuring out why mythfrontend and mythbackend have stopped logging all of a sudden. In fact, they stopped logging yesterday, after I updated Lucid from 2.6.32-25 to -26.  It's tough troubleshooting with no logs...

Cheers.

---

### Post by nickrout on 2010-12-05
You should use the provided backup script for the database. See [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

I HIGHLY recommend you use that script and only that script!

---

### Post by kyphos on 2010-12-07
> **nickrout said:**
> You should use the provided backup script for the database. See [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

I HIGHLY recommend you use that script and only that script!

Nick,
Where do we find that script?   I had already seen the wiki article you cited, but it's a dead end. It says that the script is available from the source respository at _backup_:
[https://github.com/MythTV/mythtv/tree/trunk/mythtv/programs/scripts/database/mythconverg_backup.pl](https://github.com/MythTV/mythtv/tree/trunk/mythtv/programs/scripts/database/mythconverg_backup.pl)

Clicking this link results in   ```
"[SIZE=2]**That page doesn't exist!**[/SIZE]"
```I thought maybe the script was already installed, so I tried executing it with the --help swtich, as described in the wiki.
```
myth@myth-box:~$ mythconverg_restore.pl --help
mythconverg_restore.pl: command not found
```It appears that the script is not already installed as part of Mythbuntu.

As I recall, there's an option for backing up the database in the Mythbuntu Control Center. I checked that off when I first configured my new Mythbuntu 10.04 installation, but I have no idea how to determine if it's actually doing anything. And if it is, where it's saving the backed up database. (the wiki page fails to mention that detail).  I found a backup folder (/var/backups) but it doesn't appear to have any database backups in it. Do you happen to know where the backup is supposed to be saved? And where one can obtain the backup/restore scripts?

Thanks.

---

### Post by nickrout on 2010-12-07
> **kyphos said:**
> Nick,
Where do we find that script?   I had already seen the wiki article you cited, but it's a dead end. It says that the script is available from the source respository at _backup_:
[https://github.com/MythTV/mythtv/tree/trunk/mythtv/programs/scripts/database/mythconverg_backup.pl](https://github.com/MythTV/mythtv/tree/trunk/mythtv/programs/scripts/database/mythconverg_backup.pl)

Clicking this link results in   ```
"[SIZE=2]**That page doesn't exist!**[/SIZE]"
```

I think you are experiencing an artefact from the recent move to git from trac for source code storage. However the locate command will reveal that it IS installed by mythbuntu:

```
nick@media:~$ locate mythconverg_restore.pl
/usr/share/mythtv/mythconverg_restore.pl
nick@media:~$ locate mythconverg_backup.pl
/usr/share/mythtv/mythconverg_backup.pl


```
> 
I thought maybe the script was already installed, so I tried executing it with the --help swtich, as described in the wiki.
```
myth@myth-box:~$ mythconverg_restore.pl --help
mythconverg_restore.pl: command not found
```It appears that the script is not already installed as part of Mythbuntu.

As I recall, there's an option for backing up the database in the Mythbuntu Control Center. I checked that off when I first configured my new Mythbuntu 10.04 installation, but I have no idea how to determine if it's actually doing anything. And if it is, where it's saving the backed up database. (the wiki page fails to mention that detail).  I found a backup folder (/var/backups) but it doesn't appear to have any database backups in it. Do you happen to know where the backup is supposed to be saved? And where one can obtain the backup/restore scripts?

Thanks.

The backup script is run by /etc/cron.weekly/mythtv-database

It stores the database backups in the same place as your recordings.

---

### Post by kyphos on 2010-12-15
> **nickrout said:**
> 

It stores the database backups in the same place as your recordings.

I found them, but not with my recordings.  It stores the database backups in /var/lib/mythtv/db_backups. My recordings are stored somewhere else (thanks to the new Storage Groups feature).  I didn't know the backup job was active - it appears that Mythbuntu set up the scripts and configured the cron job automagically. Nice!

---

### Post by nickrout on 2010-12-15
> **kyphos said:**
> I found them, but not with my recordings.  It stores the database backups in /var/lib/mythtv/db_backups. My recordings are stored somewhere else (thanks to the new Storage Groups feature).  I didn't know the backup job was active - it appears that Mythbuntu set up the scripts and configured the cron job automagically. Nice!

yes, possibly my system has some old setup in the database or config file.

The cron script is nice, but weekly is probably not really enough, you can record a lot and change a lot of recording ruiles in a week!

---

### Post by Sctmon on 2010-12-16
I like the idea of daily database backups and will set up the cron job asap. The little script I posted was just really for my use and more of a learning exercise for me. I have only been using Linux for less than a year so any advice I can offer should probably come with a warning!

The script does however just run the official database backup script.

I usually just run mine before performing any ubuntu system updates, something that saved my bacon a few days ago. I backed up my system and installed a bunch of updates that update manager had been prodding me about and when I rebooted I just got a blank screen, even booting the recovery mode or older kernel images.

eventually I just re formatted the drive, installed 10.04 from the cd, un packed the backup archive over writing it and had the system running again in no time.

---

### Post by nickrout on 2010-12-16
I suggest you simply copy the weekly script into the daily directory:

```
sudo mv /etc/cron.weekly/mythtv-database /etc/cron.daily/
```

As the default only keeps 4 backups, set up a backuprc file to specify it to keep more with the rotate option:

```
nick@media:~$ cat /home/nick/.mythtv/backuprc
rotate=10
```

where nick is the user that runs mythfrontend. (the first user you setup during the install).

Then it will keep 10 daily backups. 10 days should be enough to notice a problem and find a backup that works! My backup files are only about 50M each so 10 of them is about half an hour SD tV storage, which is nothing.

---


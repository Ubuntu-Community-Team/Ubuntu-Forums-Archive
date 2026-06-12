---
title: "Mythbuntu Bare Scheduled Backup Not Including Data Base"
date: 2014-01-20
forum: Mythbuntu
---

### Post by martin41 on 2014-01-20
I have been struggling with this issue for a couple days now. I am running Mythbuntu 12.04 with all updates current as of today 1-20-14.  I want to have a daily backup using Mythbuntu Bare so it will include my data base.  The file it produces is only 2 KB which clearly is incorrect.  I can do a "Backup Up Now" in the MCC and that dumps down a 10 meg file which has the data base.  I make sure every time I test the schedule to check the box to include the data base and that never works.  I can run mythconver_backup.pl and mythbackup.py from the command line and they work fine.  I can't find any errors in any of the logs (I am no expert so if there is a log I should be checking please make a suggestion as I may have missed one).  The only thing I can think of is maybe it is something in my mythbuntu-bare-client.conf which I've posted below.  Any help would be greatly appreciated, thanks.   

[General]
serverip = 127.0.0.1
managed = false
revision = 1

[Backup]
schedule = daily
day = *
weekday = *
storagedir = /var/lib/mythtv/db_backups
minute = 20
hour = 14
db = 1

---

### Post by martin41 on 2014-01-21
I am not sure this matters or contributes but I did notice last night that the config.xml file in my /etc/mythtv location is empty but it is populated in the /home/<user>/.mythtv/ location.  Should I make sure it is populated in both?  I have had no known problems from this being empty for the 6 months I have been running this box.

---

### Post by khPWXxF on 2014-01-21
Your reference to config.xml prompted me to look at my 12.04 system because I’ve had an uncomfortable brush with that file in the past.
 
```
phil@myth:~$ ls -l ~/.mythtv/config.xml
-rw-rw-r-- 1 phil phil 428 Jan 21 18:49 /home/phil/.mythtv/config.xml

phil@myth:~$ ls -l /home/mythtv/.mythtv/config.xml
lrwxrwxrwx 1 root root 22 Aug 24  2012 /home/mythtv/.mythtv/config.xml -> /etc/mythtv/config.xml

phil@myth:~$ ls -l /etc/mythtv/config.xml
-rw-rw---- 1 www-data mythtv 428 Jan 21 18:49 /etc/mythtv/config.xml
```
 
 
From the dates it appears that both ~/.mythtv/config.xml and the file linked by /home/mythtv/.mythtv/config.xml are re-written at each startup.
 
I have found the hard way that my daily mythconverge backups (triggered by autobackup.sh and run under user mythtv) failed for the lack of /home/mythtv/.mythtv.config.xml.

You are quite right to suspect small database backup files.  They should be several MB - for 1TB of recordings mine are up at 28MB.
  
Hope this helps.
 
Phil

---

### Post by martin41 on 2014-01-21
I will take a look into that idea.  Does anyone know if the autobackup.sh is what Mythbuntu Bare uses to run it's backups?  I have tried configuring the mythbuntu-bare-client.conf in nano and it has no affect when I change the time.  I thought it was mythbackup.py which triggers this conf file but I am not sure what triggers mythbackup.py.

---

### Post by khPWXxF on 2014-01-21
I have no knowledge of the 'bare' system so cannot comment on it but I very much doubt that it uses autobackup. They are from different stables.

I can talk about autobackup.sh which is triggered by closedown in a mythwelcome environment.   I wanted to do daily database backups at 'bedtime' when the system would have minimal database traffic - autobackup.sh was the result and I duly published it in the wiki, but I really have no idea how many users other than me that it has.  It also triggers an incremental backup of 'best' recordings.  It's been stable for 12 months now and came up trumps on 26/12/13 when the database crashed and saved me red cheeks.

My resilience approach also has a spinning partition which holds a copy of the 'live' root partition (but with modified fstab) and which can be booted via a bios change.   I should survive a crash of either of my disks with this arrangement and (hopefully) avert discussion of the merits of sky+.

A usb stick with a copy of the half dozen or so files which needed changing when I installed 12.04 along with a log of their permissions, the notes I took at the time and a mythbuntu issue cd are my last resort.  The stick will also be useful when 14.04 hits the streets!

Sorry if this has digressed - I'm not trying to steer you away from the 'bare' system but there are many approaches to backup depends on your equipment and your paranoia level.

Phil

---

### Post by khPWXxF on 2014-01-22
I have now found code for mythbackup.py
[http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/saucy/mythbuntu-bare/saucy/view/head:/client/bare/mythbackup.py](http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/saucy/mythbuntu-bare/saucy/view/head:/client/bare/mythbackup.py)
See line 86:  it does use mythconverg_backup.pl so will need a link in /home/[user invoking mythbackup]/.mythtv for that to find config.xml.

It clearly pre-dates autobackup.sh but I could not find any description or user guide for it.

Phil

---

### Post by martin41 on 2014-01-22
Thank you for some of your insight. I am thinking I may just try to run mythbackup.py as a cron job and see if that will work. Of course now I have to figure out how to kill the Mythbuntu Bare job that keeps creating those 2 KB files.

---

### Post by martin41 on 2014-01-22
Ok so I have found the solution and it was due to the config.xml file located at /etc/mythtv/config.xml being empty so I did the following to symlink it:

cd /etc/mythtv
         sudo rm config.xml
         sudo ln -sf /home/<your-user-name>/.mythtv/config.xml config.xml

I then discovered that the backup was only pulling the symlink config.xml file and not the actual file so I went into mythbackup.py and changed the config.xml file to pull from /home/<your-user-name>/.mythtv/config.xml.

Finally the file that drives the scheduled back up is a cron job located at /etc/cron.d/mythbuntu-bare.

I was able to locate most of this information from /usr/share/mythbuntu/plugins/python/mythbuntu-bare.py which appears to be the file that processes everything from the console.

Now I will see within a week if everything runs as it should by doing the backup at 2AM and rotating out old backups every 5 days.  

Thanks for all the help.

---

### Post by tgm4883 on 2014-01-22
> **martin41 said:**
> Ok so I have found the solution and it was due to the config.xml file located at /etc/mythtv/config.xml being empty so I did the following to symlink it:

cd /etc/mythtv
         sudo rm config.xml
         sudo ln -sf /home/<your-user-name>/.mythtv/config.xml config.xml

I then discovered that the backup was only pulling the symlink config.xml file and not the actual file so I went into mythbackup.py and changed the config.xml file to pull from /home/<your-user-name>/.mythtv/config.xml.

Finally the file that drives the scheduled back up is a cron job located at /etc/cron.d/mythbuntu-bare.

I was able to locate most of this information from /usr/share/mythbuntu/plugins/python/mythbuntu-bare.py which appears to be the file that processes everything from the console.

Now I will see within a week if everything runs as it should by doing the backup at 2AM and rotating out old backups every 5 days.  

Thanks for all the help.

Glad you got that working. I don't check the forums all that much unless I get an email alert on something. It's been awhile since I've touched mythbuntu-bare, but yes that is where most things take place. I believe there is a second directory for helper scripts (IIRC, /usr/share/mythbuntu-bare/). That directory should contain the actual backup and restore scripts (although yes, the database stuff is handled by the provided mythtv database scripts)

---


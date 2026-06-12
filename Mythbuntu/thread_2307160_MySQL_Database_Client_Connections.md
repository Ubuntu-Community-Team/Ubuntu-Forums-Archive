---
title: "MySQL Database Client Connections"
date: 2015-12-22
forum: Mythbuntu
---

### Post by jlp_engineer on 2015-12-22
Hello,

I recently had an issue that I am finding a little disturbing.  I have a older 1U style server that is using an HDHR Prime to grab encrypted channels and running Mythbuntu 14.04 with all updates applied.  Everything was going along just fine, and other than the local RAID array getting a little full (70%), nothing bad has happened.  This weekend, I was downloading and applying updates, and during the process, I received a dialogue box that said something about replacing some config file with an updated one.  I said "no" and continued, but after the reboot, none of my client front-ends could connect to the back-end server.  I would just get the language selection screen with the back-end IP and database login and password on the next screen, over and over again.  However, anything that used the API was working fine (Torc, MythTV for Android).

Okay, well, I then did some searching on the internet, and found some database commands that would reset the mythtv password in the database.  I did this and the command found four instances and changed four.  I was then left at a MySQL> prompt, with no idea on how to gracefully exit, so I hit "Ctrl-C".  That is one of the big issues I have with documentation on how to do these little things, is that most of them omit one or more little commands.  These little omissions aren't such a big deal to the more seasoned linux users, but I find it irritating (climbing down off of my soapbox ](*,)).  I also forgot to use the command "FLUSH PRIVILEGES", before I exited, so I could insert a mistake of my own making #-o.  Things still didn't work, but then I rebooted the server [-o< and I was now able to connect all my clients.  

Question: What happened to the database?  I know frequent backups are a good idea, and I almost restored the backup from the day before.  I am pretty sure that the dialogue box that came up during the update process had something to do with it, or it was a hack? :-k  I have my firewall locked down, with the exception of port 6544, for access by MythTV android and Torc on the iPad.  

I would like to use Rsync to backup my server to a NAS box so things like this or even other more catastrophic failures are less serious, but I am not certain which directories to include.  I would like a nice clean backup including only what I need for MythTV.  For example, if disaster strikes, I would prefer to wipe the server, erasing all drives, and then load Mythbuntu, and then restore from my most recent Rsync session, to pick up right where I left off.  I know with config files scattered throughout the system, this might be a tall order, but I believe this should be doable.

Any suggestions would be appreciated, and any ideas on the database mishap would be informative.

Thank you.

---

### Post by tgm4883 on 2015-12-22
Your database should be fine. What do you have listed for 'bind-address' in /etc/mysql/conf.d/mythtv.cnf ?  It should probably be 'bind-address=0.0.0.0'. It might be commented out, so if it is you should remove the comment and restart mysql.

---

### Post by jlp_engineer on 2016-01-04
Well,

It has happened again.  None of my MythTV Frontends can connect to my Backend server.  I have tried resetting the mythtv passwords in the database following the instructions contained in this [thread]("http://www.gossamer-threads.com/lists/mythtv/users/265008"), for user mythtv, but it found only two and changed none.  I checked the bind address, and it is commented out in the mythtv.cnf file.   Should this be commended out if all my clients are connecting non-locally, from their own IP to the IP of the server???

I am hesitant to restore from a backup, as that looks a little complicated (creating the database, installing tables, etc.).  But I know that the database is good, since my iPad using Torc, tells me all is well, and all my recordings are there, etc.


Please... I need help!   What can I do next?

---

### Post by jlp_engineer on 2016-01-05
I found the problem.  Given the suggestion by tgm4883, I checked the bind address, and it was commented out.  But since I didn't know for certain what it was supposed to be, I didn't mess with it.  Instead I used Mythbuntu Control Center, and checked the MySQL settings.  The "Remote Connections" option was disabled.  I enabled the setting, and that fixed it. I checked the bind address in the MySQL mythtv.cnf file, and the comment hash mark was gone.  

Just another reason to check all the possibilities and make no assumptions.  That is what I like about Mythbuntu and the Ubuntu community...I learn something new every time something strange like this happens. :D

---


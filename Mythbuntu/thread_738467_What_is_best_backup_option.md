---
title: "What is best backup option?"
date: 2008-03-28
forum: Mythbuntu
---

### Post by ahood on 2008-03-28
I am building a mythbuntu system for a friend and considering of running a backup client/utility.

I have a second hard drive where the backups can be stored.

I would like to backup only the new media (music and tv recordings). Videos will not be stored on the machine.

I need a backup utility that will periodically do full and incremental backups, probably during the night, when the system has low activity.

A backup utility with a GUI will be preferred because my friend is not very command line savvy. 

I was thinking of using sbackup, but don't know much about it. Would sbackup be a good choice? What about other backup utilities?

Any input will be greatly appreciated.

Al

---

### Post by fedex1993 on 2008-03-30
i think rsync as a way where you can set it up well i think it is rsync where you can choose what folder to sync daily to a certian location

---

### Post by newlinux on 2008-03-30
I use an rsync script with cron (grsync is a gui version, but it doesn't allow for automatic execution). sBackup is okay and easy to configure, but last I used it it tried to gzip and tar everything it was backing up, which makes it take longer and is more processor intensive. The compression didn't seemto save much space for video files.

---

### Post by tidderd on 2008-04-01
I use BackupPC -
   [http://backuppc.sourceforge.net/](http://backuppc.sourceforge.net/)
It has a browser based GUI which can be taylored to the User level requirements. It is a server/client system but there is no reason why you can't just use it to 'backup' itself.

I have also used it for doing a 'restore'. Perhaps the MOST important aspect of any backup program.

Dave

---


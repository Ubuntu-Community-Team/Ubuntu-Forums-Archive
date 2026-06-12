---
title: "Database Backup - changing the number of backups saved"
date: 2013-11-13
forum: Mythbuntu
---

### Post by Paulgirardin on 2013-11-13
I would like to change the number of backups saved from the default 5.
I have already moved the mythtv-database script to /etc/cron.daily and it is creating a backup each day.
I also created a backuprc file with this command:
 ```
echo "DBBackupDirectory=/home/mythtv" > ~/.mythtv/backuprc
``` 
and added rotate=21 to it. - i.e.

DBBackupDirectory=/var/lib/mythtv/db_backups
rotate=21

It is still only saving 5 backups.I don't really know if   /.mythtv/backuprc  is being used.

---

### Post by khPWXxF on 2013-11-23
A stab in the dark.

Do you know which user the backup is run from?
Would it be mythtv in which case you may need to put that file under /home/mythtv/.mythtv ?

Phil

---

### Post by khPWXxF on 2013-12-10
Paul,
 
Have you resolved your problem?  If not then a few points:
 
1. In version 12.04,  Mythbuntu was already configured to do backups.  Has this been removed in your version, or is that job still being run?
 
2. In your posting the code does not match the comment about the edit.  If this is making your cron job fail then you may still be seeing the results of the original cron job with its backup parameters, or looking in the wrong place.
 
3. I suspect that backuprc also needs to be in the /home/<user running the job>/.mythtv directory. Is that user mythtv?
 
4. you may also need a config.xml file or link in that directory.  Copy it from ~/.mythtv
 
I have chosen to do these backups at closedown with my dedicated FE/BE system.    It’s a personal view that these are best done when the database is idle – see autobackup.sh in the wiki if interested.
 
Regards
Phil

---

### Post by Paulgirardin on 2013-12-11
> **khPWXxF said:**
> 




Paul,
 
Have you resolved your problem?  If not then a few points:
 
1. In version 12.04,  Mythbuntu was already configured to do backups.  Has this been removed in your version, or is that job still being run?

[COLOR=#ff0000]It was doing backups weekly.I was wanting to increase the frequency from weekly to daily.I moved the mythtv-database script from /etc/cron.weekly to /etc/cron.daily.It is now backingup daily.That part is working.I also wanted to increase the number of db backups saved from the default 5 to 21.I followed the directions in the Mythtv.org wiki ( [/COLOR][[COLOR=#ff0000]http://www.mythtv.org/wiki/Database_Backup_and_Restore#Quick_Start[/COLOR]]("http://www.mythtv.org/wiki/Database_Backup_and_Restore#Quick_Start")[COLOR=#ff0000] ) to create a backuprc file in /home/user(myth)/.mythtv and added the line rotate=21 to it. - I am beginning to think that the context of this line is the problem.[/COLOR]
 
2. In your posting the code does not match the comment about the edit.  If this is making your cron job fail then you may still be seeing the results of the original cron job with its backup parameters, or looking in the wrong place.

[COLOR=#ff0000]It is doing backups daily which is my intention.[/COLOR]
 
3. I suspect that backuprc also needs to be in the /home/<user running the job>/.mythtv directory. Is that user mythtv?

[COLOR=#ff0000]It is in   /home/user(myth)/.mythtv    is this the user running cron daily jobs? [/COLOR]


 
4. you may also need a config.xml file or link in that directory.  Copy it from ~/.mythtv
 
I have chosen to do these backups at closedown with my dedicated FE/BE system.    It’s a personal view that these are best done when the database is idle – see autobackup.sh in the wiki if interested.
 
Regards
Phil

Thanks for your reply - see my comments added to your quote.

---


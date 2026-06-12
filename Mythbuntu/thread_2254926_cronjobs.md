---
title: "cronjobs"
date: 2014-12-01
forum: Mythbuntu
---

### Post by deanie44 on 2014-12-01
Hi everyone.  I am trying to create a cronjob to backup mythtv database automatically.  Here is the cronjob:

MAILTO=sister5091@gmail.com
00 01   * * * . /home/mythtv/./mythtv/backuprc && /usr/local/bin/mythconverg_backup.pl 

I followed the directions from this website--[http://www.thesitewizard.com/general/set-cron-job.shtml](http://www.thesitewizard.com/general/set-cron-job.shtml).  The cronjob did not execute.  What am I doing wrong?  Any assistance will be appreciated.  deanie44

---

### Post by newbie-user on 2014-12-01
Try taking out that first period in front of /home

So it should read:

```
MAILTO=sister5091@gmail.com
00 01 * * * /home/mythtv/./mythtv/backuprc && /usr/local/bin/mythconverg_backup.pl
```

---

### Post by deanie44 on 2014-12-04
newbie-user thanks for answering my post.  Sorry it took so long to response. but "life" got in the way.  I tried your suggestion, but it did not work.  I have another question: What folder does the backup land in?  Any more suggestions would be helpful.  deanie44

---

### Post by ian-weisser on 2014-12-04
> **deanie44 said:**
> I tried your suggestion, but it did not work.  I have another question: What folder does the backup land in?  Any more suggestions would be helpful.  deanie44

I don't use myth, but I've fixed a lot of cron jobs.
Are you sure about that first path? '/./' in the path doesn't seem right.

There is no way to tell from the information you have posted where the backup will land.
The backup path must be in one of those scripts the cron job is (apparently not) running.

---

### Post by deanie44 on 2014-12-05
Hi ian-wessler,  Thanks for answering my post.  I just want to schedule a cronjob the backup the mythtv database every week.  The email address is not working.  I read many articles and posts, but I still cannot get the cronjob to execute.  Can you help me?  Thanks deanie44

---

### Post by ian-weisser on 2014-12-05
Lots of people here know a lot about cron jobs.
It's hard to get your first one working, but after that the rest are easy.

Er, those questions in post #4 are still on the table.
It's likely that the cron job _is_ executing, and failing.

What happens if you run that cron job command, exactly as written except for the time, in a terminal window? Does it work?

---

### Post by bilkay on 2014-12-05
What does this produce?

ls -l /home/mythtv/./mythtv/backuprc

Does it exist? Is it executable? Whose cron job is this?

---

### Post by deanie44 on 2014-12-05
Thanks bilkay and ian-wessler.  here is the output from the terminal:

deanie56@deanie56-Inspiron-560:~$ crontab -e
crontab: installing new crontab
deanie56@deanie56-Inspiron-560:~$ ls -l /home/mythtv/./mythtv/backuprc
ls: cannot access /home/mythtv/./mythtv/backuprc: No such file or directory
deanie56@deanie56-Inspiron-560:~$ 36 00 * * * /home/mythtv/./mythtv/backuprc && /usr/local/bin/mythconverg_backup.pl
36: command not found
deanie56@deanie56-Inspiron-560:~$ 36 00 * * * /home/mythtv/./mythtv/backuprc && /usr/local/bin/mythconverg_backup.pl
36: command not found
deanie56@deanie56-Inspiron-560:~$ ls -l/mythtv/backuprc
ls: invalid option -- '/'
Try 'ls --help' for more information.
deanie56@deanie56-Inspiron-560:~$ ls -l /mythtv/backuprc
ls: cannot access /mythtv/backuprc: No such file or directory
deanie56@deanie56-Inspiron-56

How would I write the cronjob.  I changed the permissions to deanie56-- which is me-- on the mythconverg_backup.pl script. Unfortunately, it is still not running.
This is my cronjob.  I am the owner.  Thanks anyway. deanie44

---

### Post by ian-weisser on 2014-12-05
> **deanie44 said:**
> deanie56@deanie56-Inspiron-560:~$ ls -l /home/mythtv/./mythtv/backuprc
ls: cannot access /home/mythtv/./mythtv/backuprc: No such file or directory

That's your first problem.
Where is the first script that you are trying to run (backuprc) actually located?
Is backuprc really a script? Or is that the directory where you want the database backup to go?
Whatever it is, it's clearly not located at /home/mythtv/./mythtv/backuprc. The error message is quite clear about that: "No such file or directory".


FYI: When you try to run cron stuff on the command line, remove the time.
```
NO:  $ 36 00 * * * /home/mythtv/./mythtv/backuprc && /usr/local/bin/mythconverg_backup.pl
YES: $ /home/mythtv/./mythtv/backuprc && /usr/local/bin/mythconverg_backup.pl
```

---

### Post by deanie44 on 2014-12-05
The backuprc file is not a script. It is file that tells where the location of my database backup directory.--DBBackupDirectory=/media/deanie56/mythtvrecordings/databasebackups. Here is the output from the terminal:

deanie56@deanie56-Inspiron-560:~$  /home/mythtv/./mythtv/backuprc && /usr/local/bin/mythconverg_backup.pl
bash: /home/mythtv/./mythtv/backuprc: No such file or directory
deanie56@deanie56-Inspiron-560:~$ /home/deanie56/.mythtv/backuprc && /usr/local/bin/mythconverg_backup/pl
bash: /home/deanie56/.mythtv/backuprc: Permission denied
deanie56@deanie56-Inspiron-560:~$ 

This is strange for when I run mythconverg_backup.pl from the terminal all is fine. Thanks deanie44

---

### Post by newbie-user on 2014-12-06
Okay, hold on here...```
deanie56@deanie56-Inspiron-560:~$ /home/mythtv/./mythtv/backuprc && /usr/local/bin/mythconverg_backup.pl
bash: /home/mythtv/./mythtv/backuprc: No such file or directory
```doesn't work because the file doesn't exist. It looks like the file does exist at /home/deanie56/.mythtv/backuprc since you got a permission denied response on your second try.

Your second try:
```
deanie56@deanie56-Inspiron-560:~$ /home/deanie56/.mythtv/backuprc && /usr/local/bin/mythconverg_backup/pl
bash: /home/deanie56/.mythtv/backuprc: Permission denied
```
doesn't work because backuprc is probably not an executable file. In your last post, you said that backuprc isn't a script, therefore it will probably not be executable by default and doesn't need to be. The computer probably assumes that the command you wrote was meant to run an executable file, and backuprc doesn't have the executable bit enabled, resulting in the permission denied.

Alrighty, so I'm guessing this is how it works. The mythconverg_backup.pl script runs and it references the backuprc file to figure out where to put the backups. Thus, you only need to put the perl script into your cronjob:```
0 1 * * * /usr/local/bin/mythconverg_backup.pl
```
If the mythconverg_backup.pl script does need to read the backuprc file, then you need to make sure that the permissions on the backuprc file are set to at least 644:```
chmod 644 /home/deanie56/.mythtv/backuprc
```.

---

### Post by deanie44 on 2014-12-06
newbie-user. I figured it out.  I used  /usr/local/ bin/ mythconverg_backup.pl and it gave me an output in the backup directory.  The problem I have now is the Mailto variable does not work.  I configured an email account and placed on top of the command in the cronjob.   I read many post and articles, but it will still not execute.  What I am doing wrong?  deanie44

---

### Post by Lester_Burnham on 2014-12-06
Do you have anything configured to send mail?

---

### Post by ian-weisser on 2014-12-06
Did you install a Mail Transfer Agent from the Software Center?
An MTA is -not- your normal e-mail client (your e-mail client won't work for this purpose), and an MTA is not included with the default install of Ubuntu.

---


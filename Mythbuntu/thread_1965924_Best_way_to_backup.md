---
title: "Best way to backup"
date: 2012-04-26
forum: Mythbuntu
---

### Post by Quadari on 2012-04-26
Hi All,

Am planning to upgrade my 10.04/0.24 system in the next week or so.  Before doing so I (obviously) wanted to back everything up.    As it currently stands, I don't have enough room on my backup disk to backup my system with all the video/recording files included.   I don't care that much about the recordings (they could be reproduced), but setting up all the rest of the system to work with the cable provider, the remote, etc. was a giant pain in the tuchus, so I'd rather not lose that.

Is there an easy way to backup my system but ignore the recording files?

Thanks in advance.

Q

---

### Post by GuiGuy on 2012-04-27
> **Quadari said:**
> Hi All,


Is there an easy way to backup my system but ignore the recording files?

Thanks in advance.

Q

I have yet to see a reliable backup system of any sort for ubuntu/ linux. I use cp -a for file backups. Simply omit the /var/mythtv/recordings directory if you don't want to include recording.

There is simple backup in the repository. It is easy to configure and does seem to work. However, in my experience restore did not work so be careful if you use it.

For mysql I use the mythconverg_backup.pl script - it's save me more than once so I recommend it to backup your mythtv mysql database.

I run both of the above these as regular cron jobs and backup to my file server.

Once a month I image the hard disk using Acronis.

I have never been able to get the backup option in the mythtv control center to work. The fanbois tell me that is due to me being too stupid to be using linux.

Cheers.

---

### Post by tgm4883 on 2012-04-27
> **GuiGuy said:**
> <snip>

**I have never been able to get the backup option in the mythtv control center to work. The fanbois tell me that is due to me being too stupid to be using linux.**

Cheers.

Do you have a link to where this was said? I've never told you that (to my knowledge) and I don't know anyone more qualified regarding the backup utility in MCC than me. I do know there were some issues in previous versions that have been worked out in 12.04.

---

### Post by GuiGuy on 2012-04-27
> **tgm4883 said:**
> Do you have a link to where this was said? I've never told you that (to my knowledge) and I don't know anyone more qualified regarding the backup utility in MCC than me. I do know there were some issues in previous versions that have been worked out in 12.04.

Sorry, I forgot the smilie. My quip certainly wasn't a reflection on you or the Contorl Center;

> I have never been able to get the backup option in the mythtv control center to work. The fanbois tell me that is due to me being too stupid to be using linux. ;) 

My point being that when the hard problems arise in linux, the sequence is:

[LIST=1]
[*]User seeks to solve an obscure problem
[*]Most responses will be "Works for me" with no further explanation
[*]User mutters something
[/LIST]

So my comment is simply a generalisation about the linux community based on my experience; when it comes to hard to solve problems the user is usually on their own. Most will never find a solution other than by accident, because they lack the skills and knowledge. By implication, they slink away feeling almost **stupid**. 

In respect to "works fo me" responses, I once replied, "Thanks for that. There is nothing quite as revealing as a bit of gratuitous insight devoid of any practical help". You can imagine the payback I got.

As an aside, I upgraded to 12.04 LTS this morning. I get the same lock up on the control center backup  function as before when I attempt to enable it. 

Cheers

---

### Post by tgm4883 on 2012-04-28
> **GuiGuy said:**
> Sorry, I forgot the smilie. My quip certainly wasn't a reflection on you or the Contorl Center;



My point being that when the hard problems arise in linux, the sequence is:

[LIST=1]
[*]User seeks to solve an obscure problem
[*]Most responses will be "Works for me" with no further explanation
[*]User mutters something
[/LIST]

So my comment is simply a generalisation about the linux community based on my experience; when it comes to hard to solve problems the user is usually on their own. Most will never find a solution other than by accident, because they lack the skills and knowledge. By implication, they slink away feeling almost **stupid**. 

In respect to "works fo me" responses, I once replied, "Thanks for that. There is nothing quite as revealing as a bit of gratuitous insight devoid of any practical help". You can imagine the payback I got.

As an aside, I upgraded to 12.04 LTS this morning. I get the same lock up on the control center backup  function as before when I attempt to enable it. 

Cheers

Did you try running the control centre from the command line and seeing any output it had?

---

### Post by neutron68 on 2012-09-01
> **GuiGuy said:**
> I have yet to see a reliable backup system of any sort for ubuntu/ linux. I use cp -a for file backups. Simply omit the /var/mythtv/recordings directory if you don't want to include recording.
I'd like to do this - copy all BUT the recordings directory off to an external USB hard drive.  Is there single command line or a script that will do this?
> **GuiGuy said:**
> There is simple backup in the repository. It is easy to configure and does seem to work. However, in my experience restore did not work so be careful if you use it.Ugh!  If you can't restore, the backup isn't much good, is it?
> **GuiGuy said:**
> For mysql I use the mythconverg_backup.pl script - it's save me more than once so I recommend it to backup your mythtv mysql database.

I run both of the above these as regular cron jobs and backup to my file server.

Once a month I image the hard disk using Acronis.
I've got Acronis 10 and have been using the live CD to successfully clone Linux hard drives since about 2007.  Is there a way to use Acronis to just copy the boot and data partitions of Mythbuntu off to my external USB hard drive, and exclude the recordings partition?

Eric

---

### Post by Ubu_Fester on 2012-09-24
Eric's last comment:

> I've got Acronis 10 and have been using the live CD to successfully  clone Linux hard drives since about 2007.  Is there a way to use Acronis  to just copy the boot and data partitions of Mythbuntu off to my  external USB hard drive, and exclude the recordings partition?
I would also like to know a good and reliable solution to backup my OS and mythtv configuration.  A CD/DVD that contains my current system state as of X date, etc.

Thanks in advance

---

### Post by funicorn on 2012-09-24
I think tar is always the best choice.
```

#!/bin/bash
mkdir -p $HOME/backup
fullfile=$HOME/backup/system_backup.tar.gz
ARGS="--exclude=$HOME/backup --exclude=/dev/* --exclude=/lost+found --exclude=/media/* --exclude=/mnt/* --exclude=/proc/* --exclude=/sys/* --exclude=/tmp/* --exclude=/run/* --exclude=/var/tmp/* --exclude /var/crash/* --exclude /var/cache/*"

sudo tar  -cvpzf $fullfile $ARGS / 

```feel free to add anything you want to neglect into 'args', just keep in mind the difference between '--exclude /some/path' and '--exclude /some/path/*'.

And if you do not have a separate /home partition, you'd better copy the backup file to somewhere else. To restore the system, try some way to enter shell, mout the whole root file system, and run
```

sudo tar -pzvxf system_backup.tar.gz -C /path/to/root

```

---

### Post by nickrout on 2012-09-24
All of your mythtv setup information is in the database.

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

---

### Post by Ubu_Fester on 2012-09-24
Thanks all, a few more questions:

I'll investigate the TAR option.  
Thanks nickrout, I have that mythtv document printed.  I am not looking for just the mythtv setup  -- I am looking for something more holistic.  

Like an image of my 12.04 system, as pristine and working perfect "right now", plus:
Include (or maybe exclude) my mythtv configuration.  Or, is the mythtv mysql database 99% of what I need? 

Should I think of this as two backup needs, or one?  And is the approach different for backing up a 12.04 system and backing up my mythtv setup

(basic current system:  12.04, mythbuntu, .025 + repos)

---

### Post by nickrout on 2012-09-24
> **Ubu_Fester said:**
> Thanks all, a few more questions:

I'll investigate the TAR option.  
Thanks nickrout, I have that mythtv document printed.  I am not looking for just the mythtv setup  -- I am looking for something more holistic.  

Like an image of my 12.04 system, as pristine and working perfect "right now", plus:
Include (or maybe exclude) my mythtv configuration.  Or, is the mythtv mysql database 99% of what I need? 

Should I think of this as two backup needs, or one?  And is the approach different for backing up a 12.04 system and backing up my mythtv setup

(basic current system:  12.04, mythbuntu, .025 + repos)Frankly if I had a system that was trashed I would reinstall from scratch, update to 0.25-fixes via the repo, update the rest of the system using the standard repos and restore my database. This assumes that your recordings/videos etc are not in your root partition.

---

### Post by Ubu_Fester on 2012-09-24
Thanks.

---


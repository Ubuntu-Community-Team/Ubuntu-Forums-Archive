---
title: "mythrename script cron job not running"
date: 2009-02-25
forum: Mythbuntu
---

### Post by davidstoll on 2009-02-25
I have a daily cron job to run mythrename.py but it doesn't seem to be running.  If I run the script manually, it runs just fine.

How can I find out what's going on?

Here is what my script looks like...

#!/bin/bash
/usr/share/doc/mythtv-backend/contrib/mythrename.pl --verbose --format "%T - %S %g%A %m-%d-%y %c"

---

### Post by albandy on 2009-02-25
This script has execution perms and it's in /etc/cron.daily ?

---

### Post by newlinux on 2009-02-25
how do you have the cron set up? as a daily cron in cron.daily or as a user cron? if a user cron, show us your crontab...

one way to troubleshoot it is to make add a bit of logging to the script to see if it is running at all, or somehow just failing when it runs.

---

### Post by davidstoll on 2009-02-25
> **albandy said:**
> This script has execution perms and it's in /etc/cron.daily ?

Yes, but if that's bad, I didn't know.  I'm still figuring this linux thing out.

---

### Post by davidstoll on 2009-02-25
> **newlinux said:**
> how do you have the cron set up? as a daily cron in cron.daily or as a user cron? if a user cron, show us your crontab...

one way to troubleshoot it is to make add a bit of logging to the script to see if it is running at all, or somehow just failing when it runs.

It's in /cron.daily/, not crontab.  Should I change it?  I just like to use the folders.

I'll look at trying to add some logging of some sort.

---

### Post by newlinux on 2009-02-25
> **davidstoll said:**
> It's in /cron.daily/, not crontab.  Should I change it?  I just like to use the folders.

I'll look at trying to add some logging of some sort.

It's fine to have it on cron.daily - I was just curious what user permissions it was running with. Is the mythrename.pl perl script executable in addition to your cron script?


For logging, maybe just start off by echoing something  to a file before you run the mythrename.pl script and echo something else after. Also, maybe run mythrename.pl with the --verbose option and log that to the file as well...

---

### Post by davidstoll on 2009-02-26
> **newlinux said:**
> It's fine to have it on cron.daily - I was just curious what user permissions it was running with. Is the mythrename.pl perl script executable in addition to your cron script?


For logging, maybe just start off by echoing something  to a file before you run the mythrename.pl script and echo something else after. Also, maybe run mythrename.pl with the --verbose option and log that to the file as well...

Wow, I got nothing in my log!  I know the log entry works because if I run the command by hand, it logs.
I also checked to see if it had executable perms.  It's 755.
There is another script in the same folder that I created and it runs just fine.

-stumped

---

### Post by davidstoll on 2009-03-06
My crontab runs my cron.daily as root.  For some reason mythrename.py doesn't like to be run as root inside a cron job.  So I made a crontab entry that runs just that script as my normal login and it works just fine.

Kind of strange because if I run the script as root manually, it works fine.  Just doesn't like to run as root be inside a cron job.

Weird

Here is my script I had in my cron.hourly folder (with executable perms) to run mythrename.py...called "prettynames":
```

#!/bin/bash
/usr/share/doc/mythtv-backend/contrib/mythrename.pl --verbose --format "%T - %S %g%A %m-%d-%y %c"
```

The line in my crontab to run that script (along with everything else in cron.hourly) was:
```

17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
```

Everything else ran fine, just not my "prettynames" script, so I put this in my crontab file:
```

33 *    * * *   myusername   /etc/cron.hourly/prettynames
```

Where myusername is my normal login name...and it works.
If I change myusername to root, it doesn't work anymore.

---

### Post by neutron68 on 2009-10-05
I'm trying to do the same thing on a friend's Mythbuntu 8.04 machine.  
***It's very odd because the following setup works perfectly in my Mythbuntu 9.04 machine.***

I'm running the /etc/cron.hourly/prettynames script as the mythtv user.  The /etc/crontab line looks like this:
```
# m h dom mon dow user	command
5,35 *    * * *   mythtv   /etc/cron.hourly/prettynames
```

The script /etc/cron.hourly/prettynames looks like this:
```
#!/bin/bash
/usr/share/doc/mythtv-backend/contrib/mythrename.pl --link /var/lib/mythtv/pretty --verbose --format "%T %- %Y-%m-%d, %g-%i %A %- %S"
```

From the /var/log/syslog, it looks like the script is running at 5 and 35 minutes past each hour as desired, but no entries appear in the /var/lib/mythtv/pretty directory.  See log entrys:
> Oct  4 22:35:01 mythbuntu-desktop /USR/SBIN/CRON[1469]: (mythtv) CMD (  /etc/cron.hourly/prettynames)
Oct  4 23:05:01 mythbuntu-desktop /USR/SBIN/CRON[1657]: (mythtv) CMD (  /etc/cron.hourly/prettynames)

I've got both the /etc/cron.hourly/prettynames and the mythrename.pl scripts set as executable (755).

The /var/lib/mythtv/pretty folder was created as root and is therefore owned by root.

I'd like to stress that this same setup works perfectly on my Mythbuntu 9.04 machine.

What could be wrong on the 8.04 machine?  I'm running in circles.

INSIGHT APPRECIATED!
Eric

---

### Post by SiHa on 2009-10-05
You say the pretty directory is owned by root, but what are it's permissions?

---

### Post by neutron68 on 2009-10-05
I looked again.  It looks like I changed ownership on the folder so it would match the others in the directory.  I tried to match permissions, but I see they are not all the same.
```
user@mythbuntu-desktop:/var/lib/mythtv$ ls -l
total 36
drwxrwsr-x 2 mythtv mythtv     6 2008-10-16 00:36 music
drwxrwxr-x 2 mythtv mythtv     6 2008-10-16 00:36 pictures
drwxrwxr-x 2 mythtv mythtv  8192 2009-10-04 23:11 pretty
drwxrwsr-x 2 mythtv mythtv 16384 2009-10-05 01:34 recordings
drwxrwxr-x 2 mythtv mythtv  4096 2009-10-03 19:21 videos
```

I'm not sure how you change a wxr to a wsr.

---

### Post by SiHa on 2009-10-05
No, me neither. The only time I've played with the 'sticky bit' (which I think the 's' represents, is when setting up a Samaba share on the backend so I could view my media folders from a Windows machine.

---

### Post by neutron68 on 2009-10-05
So, do those permissions and folder ownerships look like the problem with the script not being able to create the symlinks in that /var/lib/mythtv/pretty directory?

I should mention that the reason the pretty directory has a size to it, is that I called the mythrename script from a command line (logged in as a regular user) and the script worked fine - putting lots of symlinks into the folder.

Eric

---

### Post by neutron68 on 2009-10-06
I tried something similar to the person who started this tread, and it worked for me too.

In the crontab file, I changed the user that invokes the prettynames script from the mythtv user to my friend's user name.  It worked.
```
# m h dom mon dow user	command
5,35 *    * * *   user   /etc/cron.hourly/prettynames
```
Within 30 minutes, updated symlinks appeared in the pretty folder.

I'm still stumped why the users mythtv and root would cause problems with the prettynames script??

Eric

---

### Post by dakota34 on 2010-01-16
Slight variation to the solutions above. I was having a similar problem getting the mythconverg_backup.pl script to run daily. I realize there is a weekly DB backup script in cron.weekly but I wanted it to run daily and I wanted to use the mythconverg_backup.pl script since it [appear]("http://www.mythtv.org/wiki/Database_Backup_and_Restore")s to be the most elegant DB restoral path. 

Including it in cron.daily didn't get it to run. Was going to follow suggestion above to specify the user (ie not root user) in the /etc/crontab file but [this page]("https://help.ubuntu.com/community/CronHowto") suggests that may be overwritten on updates, so I did as suggested on that page and entered the job with 'crontab -e' so that my local user crontab looked like this: 

```
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h  dom mon dow   command
20 04   * * *   /etc/cron.daily/mythconverg-backup-mytry

```

... where the /etc/cron.daily/mythconverg-backup-mytry file was : 

```
#!/bin/sh
/usr/local/bin/mythconverg_backup.pl

```



I don't know if the PATH and SHELL entries are needed, I added them to be safe...and I suspect I could have simply referenced the actual perl script directly or copied it into the daily directory, but anyway, after setting the time in the crontab to run a few minutes into the future to test I was overjoyed to find a brand new backup in the right location a few minutes later. So thanks for the solutions in this threal:D

Just found out the 'gnome-schedule' app provides a gui for crontab as well, if that is your thing...

---


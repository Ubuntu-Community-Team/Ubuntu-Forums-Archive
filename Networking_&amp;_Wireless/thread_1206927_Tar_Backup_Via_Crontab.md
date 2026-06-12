---
title: "Tar Backup Via Crontab"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by terazen on 2009-07-07
I've got stupidly simple backup script that has worked forever and suddenly it stopped working correctly.  It works when I run it manually using sudo, but when it runs via crontab it creates empty files for 2 of the 3 directories.  The dhcp backup is fine, but the others are empty.  Any ideas why this is?

All files in the /etc/bind directory (except rndc.key) are:
-rw-r--r--  1 root bind 

All the files in the freeradius directory are:
-rw-r-----  1 root freerad

ls -la /etc | egrep "dhcp|bind|freeradius"
drwxr-sr-x  2 root bind      4096 2009-02-10 14:41 bind
drwxr-xr-x  6 root root      4096 2009-05-14 16:30 dhcp3
drwxr-sr-x  7 root freerad   4096 2009-04-02 11:00 freeradius



```
#!/bin/bash
#
#
# define date yymmdd
DATE=`date +%y%m%d`
#
rm /tmp/name0_dhcpd_*.tgz
rm /tmp/name0_bind_*.tgz
rm /tmp/name0_freeradius_*.tgz
#Create
tar cvpzf /tmp/name0_dhcpd_$DATE.tgz /etc/dhcp3
tar cvpzf /tmp/name0_bind_$DATE.tgz /etc/bind
tar cvpzf /tmp/name0_freeradius_$DATE.tgz /etc/freeradius
#Copy to backup
scp -B -q /tmp/name0_dhcpd_$DATE.tgz root@san:backups/name0/name0_dhcpd_$DATE.tgz
scp -B -q /tmp/name0_bind_$DATE.tgz root@san:backups/name0/name0_bind_$DATE.tgz
scp -B -q /tmp/name0_freeradius_$DATE.tgz root@san:backups/name0/name0_freeradius_$DATE.tgz

```

---

### Post by terazen on 2009-07-07
Actually I just noticed that 2 of my 4 servers are doing this.  On the other server with problems dhcp and bind files are fine, but the freeradius one is empty.  The file permissions for the bind directories are the same...?

---

### Post by terazen on 2009-07-07
Anyone?  I tried using /bin/tar in the script and running `/bin/bash /bin/dailybackup` in the crontab instead of `bin/dailybackup` and still no luck.

---

### Post by jonobr on 2009-07-07
Hello

Using occums razor in this case, its obvious that the cleaning lady is unplugging the machines at night when she is hoovering around the machines.

Seriously though, given what you mention,
1- you try it on all machines and it fails on 2 of the 4.
2- It used to work but does not now 
3- The scripts are as you mention pretty simple and dont have any complexity
4- You run the script without cron and it works.

All this points to something in cron, and something in execution of the cron job which is different in two of the 4 servers.

The only thing I can come to is that cron could have changed in some update recently applied which is causing your script not to run correctly.

I did think maybe your files had grown and that the compression and tarring was taking so long that the copy was taking place before the compression and archiving had completed, but again, given your manual execution works, Im discounting that possibility.

Have you checked the syslog files for any messages on cron?
cat /var/log/syslog

If nothing else, Im giving you a free bump


Cheers

PS- tell the cleaning lady she aint off the hook yet

---

### Post by terazen on 2009-07-08
As retarded as this may sound, installing postfix in satellite mode and then installing mailx fixed the problem.

I checked my mail on the server and the email I got was just output from tar saying that yes, it tar'd the files up:
...
/etc/freeradius/sql/mssql/
/etc/freeradius/sql/mssql/dialup.conf
/etc/freeradius/sql/mssql/schema.sql
/etc/freeradius/otp.conf
/etc/freeradius/acct_users
/etc/freeradius/clients.conf.original
/etc/freeradius/dictionary
...

On the other server I added the below line to /etc/crontab right above the path to tell cron to not bother trying to send an email:
```
MAILTO=""
```

Everything works on the 2nd server now.  I'm going to change the 1st server's crontab and uninstall postfix & mailx.

---

### Post by jonobr on 2009-07-08
I would never have guessed that.........

Thanks for responding with the fix though

Cheers

---


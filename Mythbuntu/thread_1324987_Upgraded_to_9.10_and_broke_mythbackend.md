---
title: "Upgraded to 9.10 and broke mythbackend"
date: 2009-11-13
forum: Mythbuntu
---

### Post by carrucha on 2009-11-13
I upgraded to version 9.10 from 9.04 last night and when it was done mythtv wouldn't start.  It gets stuck on the setup portion where you select the language and database settings.  When trying to do that it just says "No UPnP backends found".  Using the stored db info it also fails to connect over port 3306.  It does work to connect manually with the same info.

I noticed that mythbackend keeps exiting and restarting every couple of seconds.  Here's part of my backend log:

................................................................................
2009-11-13 00:13:20.129 UPnPautoconf() - No UPnP backends found
2009-11-13 00:13:20.130 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2009-11-13 00:13:20.143 Deleting UPnP client...
2009-11-13 00:13:20.592 Failed to init MythContext, exiting.
2009-11-13 00:13:20.780 mythbackend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2009-11-13 00:13:20.781 Using runtime prefix = /usr
2009-11-13 00:13:20.782 Using configuration directory = /home/mythtv/.mythtv
2009-11-13 00:13:20.783 Empty LocalHostName.
2009-11-13 00:13:20.784 Using localhost value of dvr01
................................................................................
2009-11-13 00:13:23.308 UPnPautoconf() - No UPnP backends found
2009-11-13 00:13:23.309 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2009-11-13 00:13:23.312 Deleting UPnP client...
2009-11-13 00:13:23.694 Failed to init MythContext, exiting.
2009-11-13 00:13:23.874 mythbackend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2009-11-13 00:13:23.876 Using runtime prefix = /usr
2009-11-13 00:13:23.876 Using configuration directory = /home/mythtv/.mythtv
2009-11-13 00:13:23.878 Empty LocalHostName.
2009-11-13 00:13:23.879 Using localhost value of dvr01
................................................................................
2009-11-13 00:13:26.404 UPnPautoconf() - No UPnP backends found
...

Not sure where to go from here.

Thanks,
Damon

---

### Post by carrucha on 2009-11-13
Still haven't figured this out.  It seems like there are two sets of configs?

/home/mythtv/.mythtv/mysql.txt -> /etc/mythtv/mysql.txt
/home/mythtv/.mythtv/config.xml -> /etc/mythtv/config.xml

/home/myuser/.mythtv/mysql.txt -> /etc/mythtv/mysql.txt
/home/myuser/.mythtv/config.xml

It seems like the backend and frontend are using different users, but I could be wrong. 

backend trying to use mythtv?
"Using configuration directory = /home/mythtv/.mythtv"

frontend trying to use myuser?
"writing settings file /home/myuser/.mythtv/mysql.txt"

I tried adding the myuser user to the database with the same privileges and password, but that didn't help.  I also tried running it with the root user, but nothing changed.

Any ideas?

---

### Post by ian dobson on 2009-11-14
Hi,

Maybe try starting mythsetup, that should update the database if anything is missing/wrong.

Regards
Ian Dobson

---

### Post by ianhaycox on 2009-11-14
Is the backend on a different machine from the frontend ?

If yes, edit /etc/mysql/my.cnf and comment out

bind-address		= 127.0.0.1

stop mythbackend, restart mysql, start backend.

Also the 'Empty LocalHostName' entry in the log looks suspicious.

From bash, does, 

$ hostname

give you a sensible answer ? Is there a localhost entry in /etc/hosts for your machine ?

---

### Post by carrucha on 2009-11-14
One machine for backend and frontend.

echo $HOSTNAME returns 'dvr01'

How do I go about running mythsetup?  I don't see that anywhere.  Or is it myth-setup?  Either way, I couldn't find that.

in /etc/hosts each has an entry
localhost or DVR01 for 127.0.0.1
that error message said the host was unknown, so use DVR01

So that should work I would think.

Have the tables changed in the database?  Is there something to fix there?

Thanks

---

### Post by carrucha on 2009-11-15
Well, looking to go down to 9.04 the hard way.  Copying recordings to a ext drive, backing up db, reinstalling and reimporting.

Is there a better way (or does anyone have any other ideas how to salvage what I've got?)

---

### Post by carrucha on 2009-11-18
Couldn't make it work, reinstalled 9.04.

---

### Post by Dougie187 on 2009-11-18
Did you try a 9.10 fresh install? Or just your upgrade? Upgrades tend to have issues that the fresh install doesn't.

---


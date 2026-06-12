---
title: "No connection to the database, user access denied etc..."
date: 2008-07-05
forum: Mythbuntu
---

### Post by ZippyP on 2008-07-05
Hello

Everyone has probably seen this a million times.
I had a somewhat working MythTV system, but I had problems with the tuner cards and the video.  I decided to start from scratch.
This is a fresh install via Ubuntu and I am having problems with the database.  I have tried quite a few posted methods to access the database and all I get is access denied.  In the backend setup I have this setup as follows and tried,
[color=red]Hostname:[/color] localhost, tried 127.0.0.1 and even took a shot at my local IP 192.168.1.204
[color=red]Ping:[/color] checked or unchecked
[color=red]Port:[/color]3306 or nothing
[color=red]Database name:[/color]mythconverg
[color=red]User:[/color]mythtv
[color=red]Pass:[/color] yada yada yada (just the given password which is the same that is in the mysql.txt)
All I get from the backend is.
[color=red]**"Cannot login to database"[/color]**
I have tried various attempts via the terminal and I get the same or [color=red]**access denied.[/color]** It looks like a user grant issue but I cannot get into MySQL via any terminal, remote access via MySQLAdministrator to give the user granted privileges.   I installed MySQL Navigator and no access either.  I had Myth running before but all I had to change was the Host name to 127.0.0.1 and that fixed the situation.
Before I forget, looking in the directory there seems to be three MySQL servers, mysql, mysql-ndb and mysql-ndb-mgm.  Is this normal?
I would like to put this box back together and stop tweaking so I can start to enjoy Myth.
Any help with this would be greatly appreciated.

---

### Post by OffAxis on 2008-07-07
> This is a fresh install via Ubuntu
Is this a fresh install of mythtv or mythbuntu?
[www.mythbuntu.org](www.mythbuntu.org)

If you're okay with doing a fresh install with mythbuntu, then go for it; much easier than configuring mythtv as a standalone program. You can download the liveCD or install it's package.

Otherwise, here's how you can reset your root password:
[http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html)

---

### Post by ZippyP on 2008-07-07
Hi OffAxis

Thanks for the response.  I ended up uninstalling MythTV and reinstalling it.  The long way around but it fixed the problem.  I installed Myth via the Synaptic Package Manager.  I had the problem once before but that was with Mythbuntu and that was easy to fix just changing the host name.  This one was a bear for someone new at this.  I really don't like uninstalling and reinstalling stuff, but I was anxious to get this going.  Again thanks for your help and the link to the password fix for MySQL.  I have that bookmarked on another computer just in case. :)

Take care, 

Z

---


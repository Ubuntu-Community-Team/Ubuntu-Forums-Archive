---
title: "Where does Mythbuntu store its settings file?"
date: 2009-01-22
forum: Mythbuntu
---

### Post by 4ebees on 2009-01-22
Hi all,

Given that I'll be fiddling with my setup for a while, can someone please direct me to where in the file structure Mythbuntu stores the settings file (eg. like xorg.conf being in /etc/X11)

This will help me to easily restore whatever I break :))

Many thanks.

---

### Post by newlinux on 2009-01-22
If you are referring to mythtv settings, most are stored in the mysql database.

---

### Post by 4ebees on 2009-01-22
> **newlinux said:**
> If you are referring to mythtv settings, most are stored in the mysql database.

Thanks newlinux.

Where exactly can I access them? I'd like to back'm up when I try to bork my box.

---

### Post by newlinux on 2009-01-23
I think mythbuntu-control-centre allows you to schedule regular backups. I use a cron job and backup my database daily and keep 7 days worth of backups. It's similar to what is done on this page:

[http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance)

I use phpmyadmin to access the database directly, but if all you need is backups, you can do it with help from the link above.

---

### Post by roundhay on 2009-01-24
I am running Mythbuntu and seem to be having problems with the channel scanning function of myth and want to access the myth database using phpmyadmin so I can mannually change some of the channels settings to see if I can fix the probelm.

I have installed phpmyadmin but I can't see the myth database so I have not been able to access it.

Do you know how I can access the database using phpmyadmin?

---

### Post by 4ebees on 2009-01-24
> **newlinux said:**
> I think mythbuntu-control-centre allows you to schedule regular backups. I use a cron job and backup my database daily and keep 7 days worth of backups. It's similar to what is done on this page:

[http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance)

I use phpmyadmin to access the database directly, but if all you need is backups, you can do it with help from the link above.

Hi again,

I think we're talking about different things. I'm more seeking where the setup details are stored. For instance, if I set particular parameters for video storage, is there a file which holds that information. If I then backup the file, I can re-insert it if I bork something.

It's possible this may not be possible - or simple :)

---

### Post by newlinux on 2009-01-24
> **4ebees said:**
> Hi again,

I think we're talking about different things. I'm more seeking where the setup details are stored. For instance, if I set particular parameters for video storage, is there a file which holds that information. If I then backup the file, I can re-insert it if I bork something.

It's possible this may not be possible - or simple :)

We are talking about the same thing. Those settings are in the database. So you either need to backup the database, or the particular tables in the database that have the setting you want to save. If you bork something you would then either restore the table or the whole database. Almost all of myth's frontend and backend settings are stored in the mysql database. It's as simple as the instructions in the link I posted earlier. It's just a couple of commands to backup and restore.

---

### Post by newlinux on 2009-01-24
> **roundhay said:**
> I am running Mythbuntu and seem to be having problems with the channel scanning function of myth and want to access the myth database using phpmyadmin so I can mannually change some of the channels settings to see if I can fix the probelm.

I have installed phpmyadmin but I can't see the myth database so I have not been able to access it.

Do you know how I can access the database using phpmyadmin?

did you install phpmyadmin on the master backend? What happens when you try to see the DB? Do you get a choice of looking at the mythconverg database? It should just be one of the dbs you can select when you go to the phpmyadmin web page

---

### Post by 4ebees on 2009-01-24
hokely dokely,

It appeared to me that we were not discussing the same issue, so I'm glad it was my misunderstanding.

Many thanks for that, I'll get on to it :)

---

### Post by roundhay on 2009-01-24
> **newlinux said:**
> did you install phpmyadmin on the master backend? What happens when you try to see the DB? Do you get a choice of looking at the mythconverg database? It should just be one of the dbs you can select when you go to the phpmyadmin web page

Yes i have installed phpmyadmin on the same PC as the backend. The PC is working as both backend & frontend

When i go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) I can't see any reference to mythconverg?

when I search for mythconverg it appears to be in /var/lib/mysql/mythconverg

I have tried to open this folder using the database > import > browse function in phpmyadmin but it would open / load?
:confused:
I have also tried opening the mysql.txt file using databse > import > browse. The file is in /home/use/.mythtv but I got the following error message in phpmyadmin

Error

SQL query:

DBHostName = localhostDBUserName = mythtvDBPassword = C1RFOKlEDBName = mythconvergDBType = QMYSQL3

MySQL said: Documentation
#1064 - You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'DBHostName=localhost

DBUserName=mythtv
DBPassword=C1RFOKlE
DBName=mythconverg
' at line 1

Solved this -- needed to log into phpmyadmin as root

---


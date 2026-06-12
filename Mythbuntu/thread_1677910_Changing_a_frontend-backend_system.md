---
title: "Changing a frontend-backend system"
date: 2011-01-29
forum: Mythbuntu
---

### Post by boondocks on 2011-01-29
I have this Mythbuntu (10.04) system working as a standalone frontend-backend.

Now I want setup a second host that is just a frontend Mythbuntu 10.04 system.

What changes need to be done to the standalone frontend-backend system so that it can be also be a backend to other hosts?

---

### Post by BicyclerBoy on 2011-01-30
I had to do the same thing over 1 year ago.

It can be easy or real hard way depending on the host name in the database.
This page is your rescue..
[http://www.mythtv.org/wiki/Database_Backup_and_Restore#Change_the_hostname_of_a_MythTV_frontend_or_backend](http://www.mythtv.org/wiki/Database_Backup_and_Restore#Change_the_hostname_of_a_MythTV_frontend_or_backend)

This webpage links to the latest backup rstore scripts.

IIRC The default combined frontend-backend solution names the computer localhost. This makes it the hard way.

You must change:
-  sort out a static IP/hosts file for the sql database server.
-  the hostname in the mysql control files.
-  hostname in the mythtv-setup (backend)
-  hostname of all the recordings in the database.

The existing hardware config for the backend belongs to current host name. The last step should fix that.
The frontend config belongs to the frontend host name so you may need to reconfigure that.

You need static IP (& hosts file or DNS) so other frontends can find the master backend database server.
You can use your router to allocate a fixed IP to the master backend by MAC address.

Please make a database backup first.
Please do not try unless you are able to perform backup & restore (scripts)..

---

### Post by tgm4883 on 2011-01-30
> **BicyclerBoy said:**
> I had to do the same thing over 1 year ago.

It can be easy or real hard way depending on the host name in the database.
This page is your rescue..
[http://www.mythtv.org/wiki/Database_Backup_and_Restore#Change_the_hostname_of_a_MythTV_frontend_or_backend](http://www.mythtv.org/wiki/Database_Backup_and_Restore#Change_the_hostname_of_a_MythTV_frontend_or_backend)

This webpage links to the latest backup rstore scripts.

IIRC The default combined frontend-backend solution names the computer localhost. This makes it the hard way.

You must change:
-  sort out a static IP/hosts file for the sql database server.
-  the hostname in the mysql control files.
-  hostname in the mythtv-setup (backend)
-  hostname of all the recordings in the database.

The existing hardware config for the backend belongs to current host name. The last step should fix that.
The frontend config belongs to the frontend host name so you may need to reconfigure that.

You need static IP (& hosts file or DNS) so other frontends can find the master backend database server.
You can use your router to allocate a fixed IP to the master backend by MAC address.

Please make a database backup first.
Please do not try unless you are able to perform backup & restore (scripts)..

Um, thats not what the OP wants to do at all. He wants to add another node into his mythtv network which at the moment consists of a single machine. He said nothing about moving his master backend to another machine.

@OP Depending on how you have things configured right now, it may be pretty easy. When you set up your backend ip addresses, did you use your private network IP or did you use localhost (127.0.0.1)? 

For the backend, open up mythbuntu-control-centre and enable the mythtv service. 

When you install the new frontend machine, you will need your mythtv credentials to connect the frontend and backend. You should be able to look at /etc/mythtv/mysql.txt and get the username and password.

---

### Post by boondocks on 2011-01-30
> **tgm4883 said:**
> Um, thats not what the OP wants to do at all. He wants to add another node into his mythtv network which at the moment consists of a single machine. He said nothing about moving his master backend to another machine.
...

Exactly.

> **tgm4883 said:**
> ...
For the backend, open up mythbuntu-control-centre and enable the mythtv service. 
...
What section is the mythtv service under?

Under System Roles, currently I have:
Backend Role (O) Primary Backend
Frontend Role (O) Desktop Frontend
Desktop (nothing is checked)

---

### Post by nickrout on 2011-01-30
> **boondocks said:**
> Exactly.


What section is the mythtv service under?

Under System Roles, currently I have:
Backend Role (O) Primary Backend
Frontend Role (O) Desktop Frontend
Desktop (nothing is checked)

from memory it is the mysql service you want to check, under the mysql tab.

---

### Post by boondocks on 2011-01-30
> **nickrout said:**
> from memory it is the mysql service you want to check, under the mysql tab.

In Mythbuntu Control Centre, under MySQL Configuration:
[LIST]
[*]I should "Enable" the MySQL service on ethernet interfaces.
[*]What about - Enable daily MySQL DB Optimize/Repair cron job?
[*]What about - Enable MySQL performance Tweaks?
[/LIST]

---

### Post by nickrout on 2011-01-30
> **boondocks said:**
> In Mythbuntu Control Centre, under MySQL Configuration:
[LIST]
[*]I should "Enable" the MySQL service on ethernet interfaces.
[*]What about - Enable daily MySQL DB Optimize/Repair cron job?
[*]What about - Enable MySQL performance Tweaks?
[/LIST]

Yes enable them, although I am not sure what the last one actually does.

---

### Post by BicyclerBoy on 2011-01-30
@OP
Honestly very sorry to put you wrong..
Mythbuntu must have a better setup.
The default Ubuntu MythTV combined front-backend ends up with 127.0.0.1 localhost IP & hostname.
This is a mess when you decide to use over LAN with multiple front-backends..

I never said anything about moving the master backend but in essence this happens if you change the hostname..

---

### Post by boondocks on 2011-01-31
> **BicyclerBoy said:**
> @OP
Honestly very sorry to put you wrong..
Mythbuntu must have a better setup.
The default Ubuntu MythTV combined front-backend ends up with 127.0.0.1 localhost IP & hostname.
This is a mess when you decide to use over LAN with multiple front-backends..

I never said anything about moving the master backend but in essence this happens if you change the hostname..
Its alright.
I am moving in the right direction.

---

### Post by boondocks on 2011-01-31
> **nickrout said:**
> Yes enable them, although I am not sure what the last one actually does.

What actually happens when you - "Enable" the MySQL service on ethernet interfaces?
Does it make any changes to the "bind-address = 127.0.0.1" in "/etc/mysql/my.cnf" ?
What else happens?

---

### Post by nickrout on 2011-01-31
I believe that's what it does.

---

### Post by boondocks on 2011-01-31
I have NOT hit the "Enable" yet.

But I did comment out the "bind-address = 127.0.0.1" line in "/etc/mysql/my.cnf" file.


As mentioned by tgm4883 earlier, the backend had the localhost (127.0.0.1). That was the setup by default in Mythbuntu.
I changed this to 192.168.1.8 which is the eth0 for the backend.

Then I rebooted the system.

The standalone frontend-backend system worked fine after the reboot.

So I took the MySQL info from the backend's config screen and entered that into the new frontend system.
Rebooted the new frontend and it works too!

---


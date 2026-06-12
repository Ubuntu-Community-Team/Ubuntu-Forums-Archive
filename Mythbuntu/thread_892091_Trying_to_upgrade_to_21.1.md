---
title: "Trying to upgrade to 21.1"
date: 2008-08-16
forum: Mythbuntu
---

### Post by zdude on 2008-08-16
I am running 20.2 and I would like to upgrade to 21.1 - I know that the SQL database is different and herein lies my problem. I am running my server on 6.06 and it won't upgrade to 8.04 due to various reasons so I thought I would do a clean install, which is a good idea. BUT, I have A LOT of videos and I don't want to lose the data or my setup configuration - I have a lot of time setting this thing up. I want to install the 8.04 buntu with myth and then reload the database but I need to know what the database differences are and if there are sql scripts to update the tables. My work flow is install myth then reload the old database schema and data THEN update the database to the new schema. Does this make sense? Is it doable? I am very knowledgeable with sql (mostly sqlserver) but sql is sql and I think I can do this but are there existing scripts or any gotchas if I've got to write my own scripts, i.e., missing data that must be filled in in the new schema?
Thanks for any insight or help.

---

### Post by superm1 on 2008-08-16
> **zdude said:**
> I am running 20.2 and I would like to upgrade to 21.1 - I know that the SQL database is different and herein lies my problem. I am running my server on 6.06 and it won't upgrade to 8.04 due to various reasons so I thought I would do a clean install, which is a good idea.

I'd be interested in hearing what's wrong with the upgrade

> 
 BUT, I have A LOT of videos and I don't want to lose the data or my setup configuration - I have a lot of time setting this thing up. I want to install the 8.04 buntu with myth and then reload the database but I need to know what the database differences are and if there are sql scripts to update the tables. 

Personally, I say go invest in a cheap hard drive - 20 or 30 gigs will suffice.  Do your install to the new hard drive, copy the database in etc.  This way until you have everything perfect, you haven't wrecked your old install.



> 
My work flow is install myth then reload the old database schema and data THEN update the database to the new schema.Does this make sense? Is it doable? I am very knowledgeable with sql (mostly sqlserver) but sql is sql and I think I can do this but are there existing scripts or any gotchas if I've got to write my own scripts, i.e., missing data that must be filled in in the new schema?
Thanks for any insight or help.
Backup your old db, do your 8.04 install.  Drop the db on the 8.04 install, and then load your backup in.  The first time mythbackend starts, it will update the schema and all.

---

### Post by zdude on 2008-08-16
> **superm1 said:**
> I'd be interested in hearing what's wrong with the upgrade

Personally, I say go invest in a cheap hard drive - 20 or 30 gigs will suffice.  Do your install to the new hard drive, copy the database in etc.  This way until you have everything perfect, you haven't wrecked your old install.

Backup your old db, do your 8.04 install.  Drop the db on the 8.04 install, and then load your backup in.  The first time mythbackend starts, it will update the schema and all.

My Ubuntu 6.06 server, that has myth on it (it is a myth backend only) also is a mail server, ftp, web access, media server, etc. It does a lot of work and it was originally upgraded from 4.10 - soooo, it has a lot of screwy dependencies such that, when upgrading to 8.04.1 it goes into and endless loop trying to fix one dependency and then it breaks another, etc.   I finally gave up! The server runs 24/7 and there are no broken dependencies but it has a lot of deprecated crap on it. 
I was doing exactly what you described, building the OS on another machine and making sure all is working then I will transfer the new OS build to the old server. It has about 6 TB of disk space so it is a beast.:) I am also testing a new mail system so I am kind of upgrading and updating everything!
I did not realize that the backend updated itself on start-up. Cool! Thanks for the info! I'll try it tomorrow :)

---


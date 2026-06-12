---
title: "MythTV sql table 'channel' schema needed"
date: 2007-10-02
forum: Multimedia &amp; Video
---

### Post by risby on 2007-10-02
I have received no help after three weeks on MythTVtalk forum with this problem so I wonder if any of you guys could help.

I got MythTV working well but I thought I'd just clear out the mismash of nearly duplicate channels left over from a variety of attempts to get MythTV's guide working and re-fill by running mythfilldatabase. 
 
so i connected to the database and entered "drop channel;" 
 
now I can't find the table definition to recreate it. 
 
I read in "Practical MythTV" that /usr/share/mythtv/sql/mc.sql sets up the schema but it doesn't seem to. It just contains: 
 
CREATE DATABASE if not exists mythconverg; 
GRANT ALL ON mythconverg.* TO mythtv@localhost IDENTIFIED BY "mythtv"; 
FLUSH PRIVILEGES; 
GRANT CREATE TEMPORARY TABLES ON mythconverg.* TO mythtv@localhost IDENTIFIED BY "mythtv"; 
FLUSH PRIVILEGES; 
ALTER DATABASE mythconverg DEFAULT CHARACTER SET latin1; 
 
Does anyone know where I could find the table definitions? 
 
I'm running MythTV version 0.20.20060828-3 on ubuntu 7.04

 Or, alternatively, could someone run 
 
sudo mysql mythconverg 
mysql> SHOW CREATE TABLE channel; 
 
and then post the resulting output which will allow me to re-create the channel table. 
 
Thx

---


---
title: "Cannot get Mythlink.pl to run - Cannot connecto to database"
date: 2012-02-10
forum: Mythbuntu
---

### Post by Whitebeam on 2012-02-10
I have pretty much a vanilla install of the latest version of Mythbuntu - based on Ubuntu 11.10 running the latest version of 0.24 (.2?) updated fresh from the Mythbuntu repos.

Every aspect of the system seems to be working well (recording, remote frontend, Mythweb).

Except:

I have added miniDLNA to serve recorded DVB-T (Freeview) video to my Sony Bravia TV. The link to the telly works well, but I'd like the TV to see human-readable file names rather than the channel/date/time groups that are the default file names. Natural reaction is to get the Mythlink,pl script working, but every time I try I get:

DBI connect ('database=mythconverg:host=localhost;port=3306','mythtv',...) failed: Access denied for user 'mythtv'@'localhost' (using password: YES) at /usr/share/perl5/MythTV.pm line 359
Cannot connect to data base:

This happens if I run it as user or using sudo.

What have I missed please?

Peter

---

### Post by Whitebeam on 2012-02-11
Wow! 109 views and not a single suggestion!

An update on what I've tried:

[INDENT]Edit /etc/mysql/my.conf to change bind-address from 127.0.0.1 to 192.168.2.30

Edit /etc/mythtv/mysql,txt to change DBHostName to 192.168.2.30

Edit /etc/hosts to associate 192.168.2.30 to the name of my computer

In mysql> 
grant all on mythconverg.* to 'mythtv'@'%' identified by 'passwd';Done the overnight update from mythbuntu repos that included updates to mythtv.pl and .py
[/INDENT]
Still _exactly_ the same error (including the reference to local host). Where does this script get its details of DBHostName, DBUserName and DBPassword from?

Peter

---

### Post by Whitebeam on 2012-02-12
Got it working in the end. I _think_ the stage that got it working was to edit config.xml in /etc/mythtv and replace localhost with the actual IP address of my backend and then to copy this amended file to the .mythtv folders in the home directories of both my own user the mythtv user. After doing this it all just worked.

I note that of the files in my home .mythtv, mysql.txt is a link to the master copy in /etc/mythtv, but config.xml is a real file rather than a symlink - this looks like a minor bug in the installation to my newbie eyes.

Peter

---

### Post by kurt2000 on 2012-04-25
Hi

I can confirm that confix.xml is empty on ubuntu 12.04, and doing a copy of the skeleton file from /usr/share/doc/mythtv-backend/contrib/config_files/config.xml to /etc/mythtv and setting the password worked

Wkr and thank you for the hint

---

### Post by andylinux on 2012-05-23
This same bug affected me when I upgraded from 0.24 to 0.25 mythtv.  Except my issue was when I was trying to use the direct download link in MythWeb, I would get an Apache Internal Server Error page.

Just like the previous user mentioned, my /etc/mythtv/config.xml file was blank.

I copied my /home/user/.mythtv/config.xml file to /etc/mythtv/config.xml and that fixed the issue.

---


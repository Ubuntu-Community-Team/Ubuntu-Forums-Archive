---
title: "Failure to Connect to Database"
date: 2008-07-15
forum: Mythbuntu
---

### Post by nicom on 2008-07-15
I have a version of 7.10 running off a USB harddrive. Recently I tied to enable other front-end machines to access it so I ran
```
sudo dpkg-reconfigure mythtv-database
```I left everything the same accept for allowing other front ends. Since then I have unable to run the front end or mythtv-setup. Each time it goes into database configuration. If I try to run dpkg-reconfigure mythtv-database all the settings appear correct but when I finish I get the warning```
Failed to connect to database: Access denied for user 'root'@'localhost' (using 
password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's possible the mysql-server wasn't running. After install is
 completed, you will need to make sure mysql-server is running
 and that you supplied the correct information. Try:
sudo dpkg-reconfigure mythtv-database
```

Password for root is blank as recommended. 

I have obviously done something wrong. Can I correct it or do I need to reinstall.

---

### Post by nicom on 2008-07-17
Anyone??

---

### Post by nicom on 2008-07-18
Silence.

Looks like it's a re-install.

---

### Post by superm1 on 2008-07-18
> **nicom said:**
> I have a version of 7.10 running off a USB harddrive. Recently I tied to enable other front-end machines to access it so I ran
```
sudo dpkg-reconfigure mythtv-database
```I left everything the same accept for allowing other front ends. Since then I have unable to run the front end or mythtv-setup. Each time it goes into database configuration. If I try to run dpkg-reconfigure mythtv-database all the settings appear correct but when I finish I get the warning```
Failed to connect to database: Access denied for user 'root'@'localhost' (using 
password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's possible the mysql-server wasn't running. After install is
 completed, you will need to make sure mysql-server is running
 and that you supplied the correct information. Try:
sudo dpkg-reconfigure mythtv-database
```Password for root is blank as recommended. 

I have obviously done something wrong. Can I correct it or do I need to reinstall.
If at some point you put a password for root, it has a hard time resetting itself to blank.

Try setting a root password and then using that in the reconfigure

---

### Post by nicom on 2008-07-18
Thanks for the suggestion but no joy.

---

### Post by nicom on 2008-07-19
Well I gave up and reinstalled Mythbuntu onto the USB hard disk and got it working again. Since the purpose of my investigation is to try and get a remote front end working I then ran "sudo dpkg-reconfigure mythtv-database" but I just accepted all the default entries, ie no change. It returned to the command line succesfully when complete. However now each time I try to start the local front end it goes into the database configuration which finishes correctly when all pages are complete but still the front end does not start. It seems running "sudo dpkg-reconfigure mythtv-database" has broken it again for me. 

Has anyone else had this problem?

---

### Post by canukguy1974 on 2008-07-27
I am having the same problem.


[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)

---

### Post by nicom on 2008-07-29
Thanks for that link. It was the ```
sudo dpkg-reconfigure mythtv-common
```step I was missing. Now it reconnects.

---


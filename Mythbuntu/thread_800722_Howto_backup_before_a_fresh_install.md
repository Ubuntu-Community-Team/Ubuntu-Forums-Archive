---
title: "Howto backup before a fresh install"
date: 2008-05-20
forum: Mythbuntu
---

### Post by axelsvag on 2008-05-20
I have tried to read all fantastic information on this forum and on all other stuff I can find around to understand the backup procedures before a fresh install. But all these tutorials always lack some small bit of information. Maybe anyone here can give me and probably others this information. 

When I look at this info found at [http://www.mythtv.org/wiki/index.php/User_Manual:Periodic_Maintenance]("http://www.mythtv.org/wiki/index.php/User_Manual:Periodic_Maintenance")

```
$ mysqldump -u mythtv -pmythtv mythconverg -c > mythtv_backup.sql

``` and ```
$ mysql -u root
  mysql>create database mythconverg;
  mysql>exit
$ mysql -u mythtv -pmythtv mythconverg < mythtv_backup.sql

``` I get three questions 
1. Do I have to be logged on as root or is it enough to use the sudo? 
2. Where is the file stored?
3. If I use an external usb harddrive to store the database how should I do then 

After the database is backuped I have to backup the actual recordings, videos, music and pictures. Is it enough to just make a copy of the folders in var/lib/mythtv folders? And after the fresh install is made, is it enough to just put the folders back? Does the backend find the files with correct database info?

Am I on the right track or have I misunderstood something here?

---

### Post by novellahub on 2008-05-20
1.  I have done this recently and used sudo.  You can also become root for your terminal session by using "sudo su" before typing the commands as normal.
2.  The files are stored in whatever directory you are currently in. You can use "pwd" to see what directory you are currently in.
3.  Simple.  Just mount your external hard drive.  Change directories to it (It should be in the /media directory).  Then run the backup commands.

You should be able to just move your recordings, videos, pictures, etc in the new folders after the database has been restored.  I would not think you need more than just the recording related database items since there are tools in mythtv to add back your videos and photos under the "setup" section of the Mythtv frontend.

---

### Post by novellahub on 2008-05-20
Here are the specific commands I used going from my old install to new: 

```
mysqldump -c -u mythtv -p -t mythconverg record recorded \ 
oldrecorded recordedprogram recordedrating \
recordedmarkup recordedseek > recordings.sql
```

(remove the \ in the lines if doing this command on one line in the terminal)

Restoring on new machine/setup:

```
mysql -f -u mythtv -p mythconverg < recordings.sql
```

Then copy all the backed up recordings / pictures / videos to the appropriate directories under /var/lib/mythtv/

You can find the mythtv database password under the frontend in Setup/General.

---

### Post by axelsvag on 2008-05-20
Thank you all very much I will go for it tomorrow. This forum is great, and so is mythbuntu.

---


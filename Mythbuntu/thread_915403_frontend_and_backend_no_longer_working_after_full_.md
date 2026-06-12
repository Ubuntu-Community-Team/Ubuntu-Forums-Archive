---
title: "frontend and backend no longer working after full disk"
date: 2008-09-09
forum: Mythbuntu
---

### Post by ~~MAINFRAIME²~~ on 2008-09-09
Mythtv filled up my var/lib with recordings until the disk was full and now I can't start the frontend or backend also mythtv-setup does not work.

"/etc/mythtv/mysql.txt" does not contain the db name, user and password and I do not know them so I can't type them in, where can I find these?

---

### Post by laga on 2008-09-11
You can try running ```
 sudo dpkg-reconfigure mythtv-database
``` followed by ```
sudo dpkg-reconfigure mythtv-common
```.

Also make sure to run optimize_mythdb.pl later.

---

### Post by SniperKIng on 2008-09-11
Hi

I had this problem a while ago for me it was simple finding the recordings folder and deleting some to free up space.

Can you not do this?

---

### Post by Shurran on 2008-09-11
I also suffered this problem when I was first setting up the system. Back then I only had 1 80GB HD for testing and left LiveTV going which filled it up. To get it to work, I had to do both of the things previously mentioned. (started with deleting the LiveTV video file)

---

### Post by ~~MAINFRAIME²~~ on 2008-09-13
```

sudo dpkg-reconfigure mythtv-database
sudo dpkg-reconfigure mythtv-common

```
Just curious because I already fixed it but wouldn't this reset my settings?



After "/var/lib" was filled and I restarted the system I got the blue page where I can setup the db settings but this was not correctly display due to new ATI drivers so I just clicked through which probably had reset the settings.
BTW If I run mythfrontend.real -geometry 801x601 there is no display corruption (seems only to happen with the current display resolution) also the backendsetup is only displayed correctly if started through the mythcontrolcentre.

Anyway I fixed it by removing the records from "/var/lib" then setting a new mysql password for mythtv
[http://ph.ubuntuforums.com/showthread.php?p=5700116](http://ph.ubuntuforums.com/showthread.php?p=5700116)
and then updated "/etc/mythtv/mysql.txt" with db name, user and password like this
```

DBUserName=mythtv
DBPassword=xxxxxx
DBName=mythconverg
DBType=QMYSQL3

```
then after a restart I had to fix a broken mysql table with "myisamchk" like this [http://blog.emeidi.com/2007/09/mysql-table-is-marked-as-crashed-and.html](http://blog.emeidi.com/2007/09/mysql-table-is-marked-as-crashed-and.html) (check "/var/log/mythtv")
also I had to reconfigure my emulators and now everything seems to work again :)

And also I have configured the Default storage group to another partition, I had this already for the LiveTV group and thought it would also record there, totally forgot the Default one.

---


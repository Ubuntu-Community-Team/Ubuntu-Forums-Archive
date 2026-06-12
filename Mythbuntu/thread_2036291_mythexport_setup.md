---
title: "mythexport setup"
date: 2012-08-01
forum: Mythbuntu
---

### Post by bfarra on 2012-08-01
I am unable to setup mythexport. When I go to [http://localhost/mythexport](http://localhost/mythexport), I am able to see my normal mythweb header with navigation tabs and background, but it says

**An unknown module was specified**

 Any idea on how to proceed? I am running mythtv 0.25


[B]
[/B]

---

### Post by DanBender on 2012-08-05
Are you running mythbuntu? If so, have you enabled mythexport in the MCC?

---

### Post by bfarra on 2012-08-05
> **DanBender said:**
> Are you running mythbuntu? If so, have you enabled mythexport in the MCC?

Yes and yes. In digging through the logs, it seems to be an issue with connecting to the mysql db? Lots of 'mythtv user denied on localhost password = yes' type errors. I seem to have all the same passwords for the mysql db in the various config.xml files. 

I have a virtual host setup in apache which directs traffic from my free no-ip domain to /var/www/mythweb, so if I try to browse to localhost/mythweb or lan-ip/mythweb I get the same error msg as for mythexport. Could that be a problem? Banging me head against a wall here...

---

### Post by dangerous_d on 2012-08-08
MythWeb needs to know your database credentials.  Normally mythbuntu configures this for you automatically in mythweb.conf (or similar).  

```
setenv db_server        "localhost"
setenv db_name          "mythconverg"
setenv db_login         "mythtv" 
setenv db_password      "mythtv"
```Did you read the install guide?

[https://github.com/MythTV/mythweb/blob/cc3c3aeceff85c44803129c5eaa70b766f98d10a/INSTALL](https://github.com/MythTV/mythweb/blob/cc3c3aeceff85c44803129c5eaa70b766f98d10a/INSTALL)

---

### Post by bfarra on 2012-08-08
> **dangerous_d said:**
> MythWeb needs to know your database credentials.  Normally mythbuntu configures this for you automatically in mythweb.conf (or similar).  

```
setenv db_server        "localhost"
setenv db_name          "mythconverg"
setenv db_login         "mythtv" 
setenv db_password      "mythtv"
```Did you read the install guide?

[https://github.com/MythTV/mythweb/blob/cc3c3aeceff85c44803129c5eaa70b766f98d10a/INSTALL](https://github.com/MythTV/mythweb/blob/cc3c3aeceff85c44803129c5eaa70b766f98d10a/INSTALL)

I have mythweb running with no problems; it's mythexport I am having trouble with.

---

### Post by dangerous_d on 2012-08-09
Check /home/mythtv/.mythtv and ~/.mythtv for "mysql.txt" and "config.xml".  There might also be files in /etc/mythtv and /usr/share/mythtv.  The mythexport-daemon is likely run as user mythtv.


```
sabolish@mythBox:~$ ls -ltr .mythtv
lrwxrwxrwx   1 sabolish sabolish     21 Nov 18  2011 mysql.txt -> /etc/mythtv/mysql.txt
lrwxrwxrwx   1 sabolish sabolish     15 Jan 28  2012 lircrc -> ../.lirc/mythtv
lrwxrwxrwx   1 sabolish sabolish     22 Aug  9 05:44 config.xml -> /etc/mythtv/config.xml

sabolish@mythBox:~$ ls -ltr /home/mythtv/.mythtv
lrwxrwxrwx 1 root   root      21 Nov 18  2011 mysql.txt -> /etc/mythtv/mysql.txt
lrwxrwxrwx 1 root   root      22 Aug  1 08:50 config.xml -> /etc/mythtv/config.xml

```


After fixing the problem with the mythtv account's DB files all I had to do was link /var/www/mythexport to my real mythexport location and create mythexport.cfg.  Oh, and make sure everything is writable by the mythtv group. 

Good luck.

---

### Post by bfarra on 2012-08-11
> **dangerous_d said:**
> Check /home/mythtv/.mythtv and ~/.mythtv for "mysql.txt" and "config.xml".  There might also be files in /etc/mythtv and /usr/share/mythtv.  The mythexport-daemon is likely run as user mythtv.


```
sabolish@mythBox:~$ ls -ltr .mythtv
lrwxrwxrwx   1 sabolish sabolish     21 Nov 18  2011 mysql.txt -> /etc/mythtv/mysql.txt
lrwxrwxrwx   1 sabolish sabolish     15 Jan 28  2012 lircrc -> ../.lirc/mythtv
lrwxrwxrwx   1 sabolish sabolish     22 Aug  9 05:44 config.xml -> /etc/mythtv/config.xml

sabolish@mythBox:~$ ls -ltr /home/mythtv/.mythtv
lrwxrwxrwx 1 root   root      21 Nov 18  2011 mysql.txt -> /etc/mythtv/mysql.txt
lrwxrwxrwx 1 root   root      22 Aug  1 08:50 config.xml -> /etc/mythtv/config.xml

```


After fixing the problem with the mythtv account's DB files all I had to do was link /var/www/mythexport to my real mythexport location and create mythexport.cfg.  Oh, and make sure everything is writable by the mythtv group. 

Good luck.

OK. I have verified that all the mysql.txt and config.xml files all contain the same info and are all writeable by the mythtv group. /var/www/mythexport links to /usr/share/mythtv/mythexport and mythexport.cfg exists in /etc/mythtv/mythexport and is owned by www-data - could that be a problem?

---


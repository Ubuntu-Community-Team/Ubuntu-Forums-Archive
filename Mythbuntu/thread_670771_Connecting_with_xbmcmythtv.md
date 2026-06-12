---
title: "Connecting with xbmcmythtv"
date: 2008-01-17
forum: Mythbuntu
---

### Post by lingenfr on 2008-01-17
After getting a bit sudo happy with my last backend installation, I rebuilt with mythbuntu. I have my kubuntu-based frontends connecting fine. I can't get my xbox xbmcmythtv-based frontends connected again. I know that I need to enable old passwords and have tried what worked before, but no joy. I have tried:

$ mysql -u root -p 
 
mysql> UPDATE mysql.user SET password=OLD_PASSWORD('mythtv') WHERE user='mythtv' AND host='mythtv@192.168.1.%'; 
mysql> flush privileges; 
mysql> quit 

and

$ mysql -u root -p 
 
mysql> GRANT ALL PRIVILEGES ON mythconverg.* TO 'mythtv'@'192.168.1.102' identified by 'mythtv'; 
Query OK, 0 rows affected (0.00 sec) 
 
mysql> flush privileges; 
Query OK, 0 rows affected (0.08 sec) 

but when I get to the following, I get an error

mysql> SET PASSWORD FOR 'mythtv'@'192.168.1.102' = OLD_PASSWORD('mythtv'); 
ERROR 1133 (42000): Can't find any matching row in the user table 
 

Does anyone see what I am doing wrong? How can I diagnose the problem? I have looked in /var/log/mythbackend.log and don't see anything.

---

### Post by lingenfr on 2008-01-17
Thanks to information in this thread, post #5

[http://ubuntuforums.org/showthread.php?t=357927&highlight=MYTHTV](http://ubuntuforums.org/showthread.php?t=357927&highlight=MYTHTV)

I used phpmyadmin to go into the mysql database in the user table and I deleted all of the bad entries from my mistaken attempts. Then I started over and the last set password command worked.

---


---
title: "Backend setup/not running problems"
date: 2008-04-08
forum: Mythbuntu
---

### Post by sparrafizzle on 2008-04-08
i have tried to install myth TV and couldn't get that to work then found mythbuntu and tried installing front end and backend on my computer so i can use my hauappage nova t DVB T 909. install it all on top of my Ubuntu install, go to run the frontend and it comes up with a setup Language>then host name user name password database and database type, tried dpkg configure on the password other little tips no luck.

can anyone help?

---

### Post by volkswagner on 2008-04-08
Can you access mysql with root or mythtv?

```
mysql -u root -p
```
```

mysql -u mythtv -p
```

If not you need to tell mysql the new password if you changed it in mythtv from the default.

---

### Post by sparrafizzle on 2008-04-08
tried those and the outcome was 

> adam@adam-desktop:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 5226
Server version: 5.0.45-Debian_1ubuntu3.3-log Debian etch distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> exit
Bye
adam@adam-desktop:~$ mysql -u mythtv -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES)
adam@adam-desktop:~$ mysql -u mythtv -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES)
adam@adam-desktop:~$ 

how do i set the password then?

---

### Post by volkswagner on 2008-04-08
Check here.

[http://ubuntuforums.org/showthread.php?t=746640]("http://ubuntuforums.org/showthread.php?t=746640")

---


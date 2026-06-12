---
title: "I can't for the life of me access the mythtv backend!!"
date: 2007-12-12
forum: Mythbuntu
---

### Post by Mysticle31 on 2007-12-12
I have been trying and trying th access the mythTV backend.

From moment one I followed these directions.

[https://help.ubuntu.com/community/MythTV_Gutsy](https://help.ubuntu.com/community/MythTV_Gutsy)

MythTV front end started, but whenever I tried to configure or watch TV it would say that it can't connect to the backend.

I've tried running 

 sudo dpkg-reconfigure mythtv-database

Which gives me:
Failed to connect to database: Can't connect to MySQL server on '192.168.1.3' (111) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
steve@Desktop:~$ sudo mysql -u root mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

I've tried running 

dpkg-reconfigure mysql-server-5.0

And reset my password to a specific password and then ran the command to reconfigure the mythtv database again.  Same result!

I've tried running

sudo mysql -u root mysql
and get:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)


Wny in the world would I "Try sudo dpkg-reconfigure mythtv-database" to reconfigure the database when that was the command I ran to reconfigure the database when the database can't be accessed!!  I've ran sudo dpkg-reconfigure mythtv-databace MANY times.  Reconfiguring the databace is EXACTLY what I'm TRYING to do!! Or rather, get access to the stupid thing! 

 :mad::mad::mad::mad:

---

### Post by volkswagner on 2007-12-13
Did you set up a root password for mysql?  If you did run the following command.

```
sudo mysql -u root mysql -p
```

You should get a prompt asking for your password.

You can also try 

```
sudo mysql -u mythtv mysql -p
```

Again you should be prompted to enter password, which you should have set up during the install.

You need access to mysql to acess mythtv backend to start there.

Provide info on your setup.  Is the backend and frontend on the same machine?

If it is on the same machine you should use 127.0.0.1 for database location and backend location.  For other frontend machines use the actual ip address of the master machine.

---

### Post by tombott on 2007-12-13
I have had the same problem, and tried so many things but never got it to work, so I d/l mythbuntu instead and am going to try a fresh install.
So not sure if changing the mysql root password would have fixed it now.

---

### Post by linuxgrrl on 2007-12-13
hi everyone,
I had the exact same problem on a clean install of Gutsy.  It turned out that although the mythtv package claimed it was "configuring" mysql, it never actually CREATED the mythconverg database within mysql.  So whether the password was right or wrong, there was nothing for it to log into.  Argh.

The solution was that I had to create a mysql database by hand.  It sounds like a lenghty process but took less than 10 minutes: 

1. installed a utility called "webmin" (download the ".deb" version from here, [http://www.webmin.com/download.html](http://www.webmin.com/download.html), then installed it with the command "dpkg -i webmin_1.380_all.deb"

2.  point your browser to [https://localhost:10000](https://localhost:10000), log into webmin, then under one of the main headings -- I think "servers" but I forget exactly-- there is a screen to configure mysql.

3. use the screen create a new database called "mythconverg".  You can retain all the default settings.

Now, you may still have to go through the "dpkg-reconfigure" process to make sure your mysql password matches and everything, but in my case the above three steps were all I had to do.  You can use a command like "mysql -uroot -p" to test that the root password works, for example.
 
I hope this helps someone.  What an annoying "gotcha" this was.

---

### Post by uopjohnson on 2007-12-13
You can create a new db without webmin which you may never use again just do:
```
mysql -u root -p
enter password:
mysql> create database mythconverg;
mysql> GRANT ALL on mythconverg.* to' mythtv'@'%' IDENTIFIED BY 'password';
mysql> exit 
```
Change 'password' to something you like and then edit /etc/mythtv/mysql.txt to use the password you selected and run mythtv-setup from MCC to have myth fill the database correctly.

---

### Post by linuxgrrl on 2007-12-13
> **uopjohnson said:**
> You can create a new db without webmin which you may never use again.

yeah, your way is prob'ly more direct but I just always find the mysql command line to be so clumsy and hard for an average user (like me) to understand.  Webmin is also a dirt- easy way to administer lvm and samba so i end up using it a lot.  :)

---

### Post by Mysticle31 on 2007-12-13
I actually solved my problem by just having mythTV log in as root with the root password.  I'm actually running the mythtv back end and a front end on the same machine, and another front end on another machiene.  The MySQL server is localhost for the main machine (with the backend and frontend)

Is there a security issue with that?

How do I create the user MythTV if there is?

---

### Post by Mysticle31 on 2007-12-13
Oh, it was right in front of me..
.
This will create the mySQL user mythtv, and a password?

> You can create a new db without webmin which you may never use again just do:


mysql -u root -p
enter password:
mysql> create database mythconverg;
mysql> GRANT ALL on mythconverg.* to' mythtv'@'%' IDENTIFIED BY 'password';
mysql> exit




How do I enter code like that?  I was using the quote feature to stand it apart in other posts.

---

### Post by uopjohnson on 2007-12-14
With the code feature. # on the tool bar or CODE in [ ]  brackets

---

### Post by Mysticle31 on 2007-12-17
I just did this again on a new install of ubuntu.

Again, I find that I can't log in with mysqul user mythtv and the generated password.

I can't change the password with 
```
[CODE]sudo mysql -u mythtv mysql -p
```[/CODE]

becouse of access denied.

I have gotten MythTV to log in using the root account though.

---

### Post by uopjohnson on 2007-12-17
[QUOTE=Mysticle31;3969443]
```
[CODE]sudo mysql -u mythtv mysql -p
```[/CODE]
Isn't going to get you anywhere what you are saying here is using the root account on your system run the mysql command (sudo mysql) then you are saying to mysql log in as the user mythtv (-u mythtv) and connect to the database mysql using a password (-p)
Try:
```
mysql -u mythtv -p mythconverg
```
you can get the password for this from /etc/mythtv/mysql.txt.

---

### Post by sharris203 on 2008-04-22
> **linuxgrrl said:**
> hi everyone,
I had the exact same problem on a clean install of Gutsy.  It turned out that although the mythtv package claimed it was "configuring" mysql, it never actually CREATED the mythconverg database within mysql.  So whether the password was right or wrong, there was nothing for it to log into.  Argh.

The solution was that I had to create a mysql database by hand.  It sounds like a lenghty process but took less than 10 minutes: 

1. installed a utility called "webmin" (download the ".deb" version from here, [http://www.webmin.com/download.html](http://www.webmin.com/download.html), then installed it with the command "dpkg -i webmin_1.380_all.deb"

2.  point your browser to [https://localhost:10000](https://localhost:10000), log into webmin, then under one of the main headings -- I think "servers" but I forget exactly-- there is a screen to configure mysql.

3. use the screen create a new database called "mythconverg".  You can retain all the default settings.

Now, you may still have to go through the "dpkg-reconfigure" process to make sure your mysql password matches and everything, but in my case the above three steps were all I had to do.  You can use a command like "mysql -uroot -p" to test that the root password works, for example.
 
I hope this helps someone.  What an annoying "gotcha" this was.

This doesn't help me, as I can't login to the mysql database server to begin with. I used username: root; password: [blank];  Access denied for user root@localhost. I did the sudo dpkg-reconfigure mythtv-database
Results:

 * Starting MySQL database server mysqld                                 [ OK ] 
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database

edit: after i ran sudo dpkg-reconfigure mythtv-database again, ans SET a "root" password; it all worked like normal. I don't understand why a blank password didn't work though.

---


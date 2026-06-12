---
title: "MythTV MySQL problems"
date: 2006-08-09
forum: Multimedia &amp; Video
---

### Post by phenolholic on 2006-08-09
Hello,
I'm following Hyams HOWTO of installing MythTV. In the part that mentions opening up 'localhost' from browser and changing password, and after trying to go into the 'phpmyadmin' directory, I get:

Cannot load mysql extension. Please check your PHP configuration. - Documentation

I ignored this, and kept on with the installation. After loading mythtv-setup, I get a Database Configuration menu, which says 'Myth could not connect to your database. Please verify the correct information' 
asking me for my login, password, host name, database, and database type. On the /home/mythtv/.mythtv/mysql.txt file, this is the information on there:

DBHostName=localhost
DBUserName=admin
DBPassword=
DBName=mythconverg
DBType=QMYSQL3

I tried going into mythtv-setup and putting in admin and leaving the passwd field blank on that database configuration menu, but no luck.

I also tried:
mysql -u root

and got the mysql> prompt and entered:
SET PASSWORD FOR admin = PASSWORD('mythtv');

and got this response:
ERROR 1133 (42000): Can't find any matching row in the user table

I've verified the services are running and indeed Apache2 and MySQL both are running. Any help would be appreciated. Thanks in advance

---

### Post by Titus A Duxass on 2006-08-09
You need to go back and change the passwd.

Open up your browser, enter localhost in the address bar and that should give you another window, click on the phpadmin directory and you are nearly there.

If that fails, check you php installation and reboot.

---

### Post by capriccio on 2006-08-09
Have you tried adding the user to the DB manually?  ie -

grant all on mythconverg.* to admin@localhost identified by 'mythtv';

---

### Post by phenolholic on 2006-08-09
Titus: it won't let me get to the passwd setup. like i said, when i click on the phpmyadmin directory, it says:
Cannot load mysql extension. Please check your PHP configuration. - Documentation

capricio: how do i add it manually?

---

### Post by Titus A Duxass on 2006-08-10
Try removing PHP and MySql through Synaptic and then reinstalling both through aptitude.

Use Synaptic first so you can see what is installed.

---

### Post by phenolholic on 2006-08-14
Ok I can log into phpmyadmin. I created a mythtv user account and logged into it, and when running mythtv-setup, I get the Database Configuration menu, and I entered my phpmyadmin login/password (along with hostname, database, database type, etc) , and it quits and displays the following error. I also verified that the login/password is indeed correct by logging in via localhost on firefox. The error is:

2006-08-14 06:59:44.324 Unable to connect to database!
2006-08-14 06:59:44.324 Driver error was [1/1049]:
QMYSQL3: Unable to connect
Database error was:
Unknown database 'mythconverg'

2006-08-14 06:59:44.324 Failed to init MythContext, exiting.



Anyone know what I'm doing wrong? Thanks in advance

---

### Post by Titus A Duxass on 2006-08-14
Why did you create a myth account?
All you have to do is change the password from nothing to something and remember it.

During the myth installation you will be asked for the passwd to that account.

---


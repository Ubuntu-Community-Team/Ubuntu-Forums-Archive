---
title: "mythtv mysql problem"
date: 2008-05-19
forum: Multimedia Software
---

### Post by bogoliubov on 2008-05-19
I've managed to screw up my database config for mythtv. I thought that one could change the database password through the, but it turned out I only changed the password that mythfrontend/backend gives when connecting to the database.
So I managed to change the password for the database. But I can't connect to the database anyway. Don't know why.

Also, I fiddled with the "grants" for the mythtv database, but I may have set them wrong. I'd like to set them so that only mythtv with password can have access. How do I do this?

For me, the easiest way may be to reinstall mythtv and mysql. But there are tons of packages related to this, and perhaps there are other stuff on the computer that needs mysql. So how do I do this the easiest way?

---

### Post by Monicker on 2008-05-19
What version of mythtv is this?  Do you have the file /home/username/.mythtv/mysql.txt?  If so, the password in that file must match what you set directly in mysql.

The mythtvuser should have all privileges on the mythconverg database.

```
mysql> show grants for 'mythtv'@'localhost';
+---------------------------------------------------------------------------------------------------------------+
| Grants for mythtv@localhost                                                                                   |
+---------------------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'mythtv'@'localhost' IDENTIFIED BY PASSWORD '*XXXXXXXXXX' |
| GRANT ALL PRIVILEGES ON `mythconverg`.* TO 'mythtv'@'localhost'                                               |
+---------------------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)

mysql> show grants for 'mythtv'@'%';
+-------------------------------------------------------------------------------------------------------+
| Grants for mythtv@%                                                                                   |
+-------------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'mythtv'@'%' IDENTIFIED BY PASSWORD '*XXXXXXXXXX' |
| GRANT ALL PRIVILEGES ON `mythconverg`.* TO 'mythtv'@'%'                                               |
+-------------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)
```


I use 'mythtv'@'%' so that I can connect from multiple frontends, such as my laptop.  Its not necessary if you are using one machine for both the frontend and backend.

---

### Post by bogoliubov on 2008-05-19
Hmm, for some reason I can't log in to mysql:

mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I could yesterday, so I must be doing something wrong.

---

### Post by Monicker on 2008-05-19
Verify the mysql server is actually running.

```
sudo netstat -anltp|grep mysql
```


Also try restarting it

```
sudo /etc/init.d/mysql restart
```

---

### Post by bogoliubov on 2008-05-20
Ok, that worked, and it seems I have the same grants as you do. Just a question here; the password isn't written in cleartext, right?

But still, I've set the password in mythtv to match that of mythtv database, but it doesn't work.

Here's some output from the mythtv terminal:

2008-05-20 08:16:54.575 New DB connection, total: 1
2008-05-20 08:16:59.629 Unable to connect to database!
2008-05-20 08:16:59.629 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'192.168.0.3' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-05-20 08:17:04.713 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
................................................................................
2008-05-20 08:17:07.169 UPnPautoconf() - No UPnP backends found
2008-05-20 08:17:07.170 No UPnP backends found
2008-05-20 08:17:07.188 Primary screen 0.
2008-05-20 08:17:07.188 Using screen 0, 1280x1024 at 0,0
2008-05-20 08:17:07.199 Switching to square mode (blue)
2008-05-20 08:17:07.248 Using the Qt painter
mythtv: could not connect to socket
mythtv: Filen eller katalogen finns inte
2008-05-20 08:17:07.249 lirc_init failed for mythtv, see preceding messages
2008-05-20 08:17:07.250 JoystickMenuClient Error: Joystick disabled - Failed to read /home/christian/.mythtv/joystickmenurc

---

### Post by Monicker on 2008-05-20
The password in the database itself is not cleartext; its a hash of the password.  The password in the file /home/username/.mythtv/mysql.txt is in cleartext.

Also, mysql can be picky about the hostnames and ip address for accepting connections.  What is the bind-address in /etc/mysql/my.cnf?  What do you have for DBHostName in ~/.mythtv/mysql.txt?

  You never said if this machine is a ocmbined frontend and backend, or if you are trying to connect from a different machine than the backend.

---

### Post by bogoliubov on 2008-05-20
I found that 
bind-address            = 127.0.0.1

and

DBHostName=192.168.0.3

where I should say that 192.168.0.3 is the adress of the computer in my LAN.

About frontend/backend: the computer has both frontend/backend, but I'd like to be able to use other machines (within the LAN) to be frontends and connect to this backend.

At the moment I'm trying to do the backend setup. Then I'll do the frontend setup on this machine, then on another machine.

---

### Post by Monicker on 2008-05-20
You need to either comment out the bind-address line, so that mysql listens on any ip address assigned to that machine, or change it to 192.168.0.3.

After the change do
```

sudo /etc/init.d/mysql restart
```

---

### Post by bogoliubov on 2008-05-21
Thanks for the tip. But I still get the same problem:


From the mythtv terminal when I start mythtv backend setup:

QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'192.168.0.3' (using password: YES)

QSqlQuery::exec: database not open

---

### Post by Monicker on 2008-05-21
And did you specify a proper hostname for the mythtv account?  Remember, if you are not connecting from localhost you will need to add mythtv as 'mythtv'@'%' (mentioned previously in regards to multiple frontends), or as 'mythtv'@'192.168.0.3'.

---

### Post by bogoliubov on 2008-05-21
> **Monicker said:**
> And did you specify a proper hostname for the mythtv account? 

I'm not sure what and how you mean. Which file do I set this in, or when during the mythtv backend setup?

I am trying to set up the backend on the machine where I have both backend and frontend.

Thanks for helping out!

---

### Post by bogoliubov on 2008-05-21
I think I solved it. You've probably said this, but I had to have "localhost" in the backend-database config, since this is what I use in the mysql config. "192.168.0.3" didn't work, even though this is where the computer is.

---

### Post by bogoliubov on 2008-05-21
But I want to be able to connect from other machines! So I guess I have to change localhost to 192.168.0.3 for the mysql mythtv database; but how?

---

### Post by bogoliubov on 2008-05-21
Ok, so I changed the bind-adress line in /etc/mysql/my.cnf, then ran 
sudo /etc/init.d/mysql restart
and then
sudo dpkg-reconfigure mythtv-database

But, after this, I can't connect for some reason:Failed to connect to database: Access denied for user 'root'@'192.168.0.3' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database

Then I tried to sudo dpkg-reconfigure mythtv-database again, but now with "localhost", and this works! So, it seems what I write on the bind-adress line in /etc/mysql/my.cnf doesn't make any difference!?

---

### Post by bogoliubov on 2008-05-21
Now I got fed up and tried to reinstall mythtv and mysql packages. I tried "complete removal" in synaptic, but that didn't remove the config files. So I tried "purge" with aptitude, but that didn't work either.

This is really strange. Do I need to reinstall Ubuntu to change "localhost" to "192.168.0.3" ? There must be another way, but I can't find it....

---

### Post by Monicker on 2008-05-21
You don't have to change localhost in the backend.  You just need to add a mythtv account with a host of 192.168.0.3 or '%' (connect from anywhere), in order for other frontends to connect to mysql on that machine; the backend is still on the same machine as the mysql database.  That is why I my output showed 2 mythtv accounts previously.

---

### Post by bogoliubov on 2008-05-22
> **Monicker said:**
> You don't have to change localhost in the backend.  You just need to add a mythtv account with a host of 192.168.0.3 or '%' (connect from anywhere), in order for other frontends to connect to mysql on that machine; the backend is still on the same machine as the mysql database.  That is why I my output showed 2 mythtv accounts previously.

Ok, I think I understand. But how do I create this account?

---

### Post by Monicker on 2008-05-22
```
mysql -u root -p

grant all privileges on mythconverg.* to 'mythtv'@'%' identified by 'password';
flush privileges;
```

The password would be the same as what you are already using for the mythtv account.  The newly created account will be able to connect from any ip address.

---

### Post by bogoliubov on 2008-05-22
> **Monicker said:**
> ```
mysql -u root -p

grant all privileges on mythconverg.* to 'mythtv'@'%' identified by 'password';
flush privileges;
```

The password would be the same as what you are already using for the mythtv account.  The newly created account will be able to connect from any ip address.

But I already had this setup. I don't really understand all this. Do you mean two accounts in mysql, or two  accounts in Ubuntu? I guess you mean the first, but I just want to check.

So if I already have this setup in mysql, how should I go about connecting the other frontend?

Btw, should I still have commented out "bind-adress" in mysql config?

---

### Post by Monicker on 2008-05-22
This is all pretty straightforward.

You may want to step through the following documentation: [https://help.ubuntu.com/community/MythTV]("https://help.ubuntu.com/community/MythTV")

---

### Post by bogoliubov on 2008-05-22
Hehe, this is the guide I started out from. 
But I found the problem; I had selected "ping" in the frontend setup on the frontend-only machine. Now I can connect!

But, for some reason, I can "see" my music, but not play the songs! 
The error message is
DecoderMAD: Failed to open input. Error 5.

The same goes for videos; I can browse and find the video I want to see, but watching it doesn't work for some reason.
The message here is:
Failed to open [path to file]

How should the file permissions on the media I want to play be set?

Great thanks for bearing with me!

---

### Post by Monicker on 2008-05-22
Hrmm. Where are these files located?  As long as the mythtv user can read the files they should be accessible.

Could you post an "ls -lh" of the directories containing these files?

---

### Post by bogoliubov on 2008-05-23
> **Monicker said:**
> Hrmm. Where are these files located?  As long as the mythtv user can read the files they should be accessible.

Could you post an "ls -lh" of the directories containing these files?

These files are located on the backend. My music is under /media/storrackare/musik/ and all files have these settings:
drwxr-xr-x 10 christian multimedia 4,0K 2007-03-24 15:39 Pain Of Salvation

I don't need any NFS mounts or anything to access the files from the frontend on the other computer? This would partly spoil the point of using mythtv...

---

### Post by Monicker on 2008-05-23
I don' think it requires a mount, but I am not positive about that.  I only use mythtv to watch telivison shows that were recorded with a capture card on the backend.

This thread might help:  [http://readlist.com/lists/mythtv.org/mythtv-users/11/56451.html]("http://readlist.com/lists/mythtv.org/mythtv-users/11/56451.html")

---


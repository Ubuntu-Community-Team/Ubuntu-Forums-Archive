---
title: "Can't get mythtv frontend-only system to connect"
date: 2006-12-20
forum: Multimedia &amp; Video
---

### Post by josesanders on 2006-12-20
I have a functioning MythTV frontend/backend system, and I am trying to set up another computer as a remote frontend-only system.  I can't seem to get the frontend to connect to the backend through my local network.  I also can't connect using ssh, even though I installed openssh-server.  I can, however, access the system remotely from my Windows machine using Samba.  I'm very new to linux networking, so there may be something very obvious that I have overlooked.  I would appreciate any suggestions.

---

### Post by halfhalo on 2006-12-20
I am assuming that the existing Frontend and Backend are onthe same system.  That would mean that the mysql database is only accepting connections from the locolhost (the computer the msql server is on).  i may be wrong but the only thing you need to do is to enter "sudo /etc/mysql/my.cnf" and change the line that reads "bind-address		= 127.0.0.1" to "#bind-address		= 127.0.0.1".:)

---

### Post by josesanders on 2006-12-20
Thanks for the suggestion, but I've already tried that.  Still doesn't work.

---

### Post by halfhalo on 2006-12-20
When you open it from the terminal, what is the error message it gives you.

---

### Post by josesanders on 2006-12-20
I run the command:
$ mythfrontend

Here is a section of the error messges (the rest appears very similar):

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-12-20 19:52:30.688 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-12-20 19:52:30.744 Database not open while trying to save setting: Language
2006-12-20 19:52:30.764 Unable to connect to database!
2006-12-20 19:52:30.764 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.5' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-12-20 19:52:30.820 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-12-20 19:52:35.667 User canceled database configuration
2006-12-20 19:52:35.696 Failed to init MythContext, exiting.


The only thing that I have installed on the remote system is mythfrontend.  Is there some mysql stuff that I also need?

---

### Post by halfhalo on 2006-12-20
There is nothing you need on the frontend machine, but have you restarted the mysql server?

---

### Post by NT4usB on 2006-12-20
Have you granted permission to the frontend IP and/or machine name in mysql on the master backend?
You have to add that box as a user in mysql and grant premissions.
If you installed the frontend as mythtv you'll have to use another name as your master already uses mythtv.
Once you have the frontend installed as mythtv, you can launch mythtv as any user by moving some textfile around. Not in front of my box atm and crs has set in so I don't remember the details... google it.

---

### Post by josesanders on 2006-12-20
I have restarted mysql, but I have not added a new user for the remote system.  How do I do that?

---

### Post by halfhalo on 2006-12-20
The way i did it was install phpmyadmin along with a webserver, and use that to set your user to be allowed acess from anywhere

---

### Post by josesanders on 2006-12-20
Is there a howto somewhere for that?  I have no idea what those things are.

---

### Post by NT4usB on 2006-12-21
google around.
there's tons of info out there...
[http://www.gossamer-threads.com/lists/mythtv/users/151473?search_string=slave%2Fmaster%20interaction;#151473](http://www.gossamer-threads.com/lists/mythtv/users/151473?search_string=slave%2Fmaster%20interaction;#151473)
[http://wilsonet.com/mythtv/tips.php](http://wilsonet.com/mythtv/tips.php)

---

### Post by majoridiot on 2006-12-21
> **josesanders said:**
> The only thing that I have installed on the remote system is mythfrontend.  Is there some mysql stuff that I also need?

did you copy /home/mythtv/.mythv/mysql.txt from your backend to /home/<frontend_user>/.mythv/ 
on the frontend?  that should open the database for you- it's got all the logon info.

<frontend_user> is the home folder for whatever user will be running the frontend.  you will most likely
have to create the .mythtv (hidden folder) on the frontend before you copy the file there.

---

### Post by josesanders on 2006-12-28
I've done everything, and I still can't get it to work.  Are there any router settings, or networking settings on the backend that may be preventing remote computers on the local network from accessing it?  I'm using a Netgear router.  I also can't access the computer through ssh, although it appears to be listening on port 22.

EDIT:
I just tried ssh to connect the opposite way from the backend to the frontend machine, and it worked.  I think there must be something blocking incoming connections on the backend.  I don't have a firewall installed.

---

### Post by NT4usB on 2006-12-29
> **josesanders said:**
> I've done everything, and I still can't get it to work...

Well, you haven't done *everything* or it would work.
Can you connect to mysql?
If you type in a terminal:
```
mysql -h <masterbackendhostname> -u <the uername you added to mysql for the frontend> -p mythconverg
```
where <masterbackendhostname> is the hostname that you gave your master backend MythTV server, obviously. 
If you connect successfully, you should see a MySQL prompt. Type ```
quit;
``` to exit
If it doesn't connect, you need to stop here and fix this problem on your MythTV master backend. Typically, you will need to add the frontend user from your <frontendhostname> as a permitted user on the backend sql server. You might also need to edit /etc/mysql/my.cnf on your backend server to bind to the server's IP, rather than the loopback address, and in that same file, make sure that skip-networks is not enabled.

[Google]("http://www.google.com/search?hl=en&lr=&q=mythtv+connect+mysql+on+backend+from+frontend&btnG=Search") is your friend

---

### Post by josesanders on 2006-12-30
I figured out the problem.  I'm embarrased to say, I had the wrong IP address.  I forgot that I changed network cards, so the router was assigning a new IP, instead of the one that I thought it was, even though the old one is still in the list.  I can't believe that it took me three weeks to figure that out.

---


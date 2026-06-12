---
title: "Mythfrontend will not connect to database"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by Protoss on 2007-03-17
Alright so I am trying to get my desktop machine to be able to run mythfrontend and connect to my backend/frontend box in my room. I added a user to mysql, aqmyth, and can connect to it via "mysql -h myth -u aqmyth -p mythconverg" successfully, but mythfrontend will not connect.  I get flooded with > QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-03-17 15:32:59.870 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-03-17 15:32:59.922 Database not open while trying to load setting: GuiVidModeHeight
2007-03-17 15:32:59.923 Unable to connect to database!
2007-03-17 15:32:59.923 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
 Even though both /etc/mythtv/mysql.txt and ~/.mythtv/mysql.txt contain > DBHostName=myth
DBUserName=aqmyth
DBPassword=myth
DBName=mythconverg
DBType=QMYSQL3

What am I doing wrong here?

---

### Post by NT4usB on 2007-03-18
oops... misread your post.
no ideas... sorry.

---

### Post by GrammatonCleric on 2007-03-18
Try changing where your Mysql socket points to...

edit you /etc/mysql/my.cf and change....

```

socket = /var/run/mysqld/mysqld.sock

```to...

```

socket=/var/lib/mysql/mysql.sock 

```

---

### Post by Protoss on 2007-03-18
Um, there are about 10+ entries of that in my.cnf...should I change every entry?

---

### Post by majoridiot on 2007-03-19
check this on your backend machine:

```
# sudo nano /etc/mysql/my.cnf
```

look for :

```
bind-address= 127.0.0.1
```

and comment it out by hashing it:

```
#bind-address= 127.0.0.1
```

restart mysql server:

```
# sudo /etc/init.d/mysql restart
```

and try to connect from the frontend.

---

### Post by FryerFox on 2007-04-30
I found your post while looking into my own problem, and that seems to be the problem: The new MySQL turns off network access by default.

Thanks

> **majoridiot said:**
> check this on your backend machine:

```
# sudo nano /etc/mysql/my.cnf
```

look for :

```
bind-address= 127.0.0.1
```

and comment it out by hashing it:

```
#bind-address= 127.0.0.1
```

restart mysql server:

```
# sudo /etc/init.d/mysql restart
```

and try to connect from the frontend.

---

### Post by armware on 2007-04-30
ok, i did all that and my frontend still tells me it can't connect to the backend.

watching the output, it seems mythtv is using the proper ip to connect to the backend (192.168.0.3), yet it still attempts to connect to the local host (127.0.0.1). see:

```

2007-04-30 20:41:23.577 Using runtime prefix = /usr
2007-04-30 20:41:23.584 DPMS is active.
2007-04-30 20:41:23.596 New DB connection, total: 1
2007-04-30 20:41:23.658 Connected to database 'mythconverg' at host: 192.168.0.3
2007-04-30 20:41:23.660 Total desktop dim: 1440x900, with 1 screen[s].
2007-04-30 20:41:23.663 Using screen 0, 1440x900 at 0,0
2007-04-30 20:41:23.732 Total desktop dim: 1440x900, with 1 screen[s].
2007-04-30 20:41:23.734 Using screen 0, 1440x900 at 0,0
2007-04-30 20:41:23.739 Switching to square mode (G.A.N.T.)
2007-04-30 20:41:23.781 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-04-30 20:41:24.105 Joystick disabled.
2007-04-30 20:41:24.247 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/welcome-ui.xml
2007-04-30 20:41:24.371 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-04-30 20:41:24.371 Connection timed out.
                        You probably should modify the Master Server
                        settings in the setup program and set the
                        proper IP address.

```

where is it being told the backend server is the localhost!?

i've checked both the mysql.txt files, and neither say 127.0.0.1.

so..... i'm kinda lost. i'll keep poking around and post what i come up with here, but i'd LOVE someone to point me in a direction. please?

---

### Post by NT4usB on 2007-04-30
did you search for all instances of mysql.txt?
sometimes there's more than one on the system, depending on how you did your install...

ed: page through mythtv-setup and you'll see where the ip address for the master is set.

---

### Post by armware on 2007-05-04
you were right - thanks. 
i needed to edit
/etc/mythtv/mysql.txt

and
/home/arm/.mythtv/mysql.txt

the mythtv setup only changed the first file, but when it was using the second (possibly both, which is why it was pulling the recordings and the guide data, but still kicking out errors.

---

### Post by kansei on 2008-02-13
> **armware said:**
> you were right - thanks. 
i needed to edit
/etc/mythtv/mysql.txt

and
/home/arm/.mythtv/mysql.txt

the mythtv setup only changed the first file, but when it was using the second (possibly both, which is why it was pulling the recordings and the guide data, but still kicking out errors.

I know this is an old thread but the other mysql.txt files are just symlinked to the first, at least in a default install.

---

### Post by Protoss on 2008-02-13
Must be a recent update, as I remember specifically looking at 2 different mysql.txt files.

---

### Post by kansei on 2008-02-14
> **Protoss said:**
> Must be a recent update, as I remember specifically looking at 2 different mysql.txt files.

I know I've seen it before on Ubuntu, where one file has it right and another has it wrong. I think it was ~6-9 months ago though

---


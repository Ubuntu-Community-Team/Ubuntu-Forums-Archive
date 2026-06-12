---
title: "Mythbuntu 10.10 clean install: backend does not start"
date: 2010-10-22
forum: Mythbuntu
---

### Post by ub40d on 2010-10-22
This week I restarted from scratch and installed a clean Mythbuntu 10.10 onto a fresh hard disk (not an upgrade of a previous installation).

EXECUTIVE SUMMARY:

Everything works fine except for one thing: it seems that the backend does not start automatically. What could be the cause, on a clean install, and how can I fix that?

DETAILS:

As soon as the frontend starts, it gives me a dialog box with:

"Could not connect to the master backend server -- is it running? Is the IP address set for it in the setup program correct? OK"

The manual fix is to launch the backend, ie:

move to another workspace for clarity

applications / system / mythtv backend setup

(mythbackend must be closed before continuing. Is it ok to close any currently running mythbackend processes? YES)

please enter password

and after that it all works fine until the next reboot.

Suggestions welcome on how to make the backend autostart
Thanks

---

### Post by LowSky on 2010-10-22
the backend seems to running if your getting the message for it to  be closed.

your issue sounds more like an IP address issue.

Make sure both ther frontned and the backend have the machines address correctly list. If is giving a problem, in the frontend settings enter localhost instead of the number address.

Hope this helps

---

### Post by superm1 on 2010-10-22
LowSky is right, this is generally an IP address issue.

If that doesn't help out, start investigating /var/log/mythtv/mythbackend.log for additional errors.

Also check and see if it's really running (ps aux | grep mythbackend).

---

### Post by ub40d on 2010-10-23
Thanks to both for your suggestions.

You are right: the backend is actually running.

Reboot.

I get the error dialog box as before  (could not connect etc).

ps aux | grep mythbackend
finds a running mythbackend process.

The ip address in the frontend is localhost (not changed from default). The one in the backend is 127.0.0.1 (also not changed from default install). Changing it to localhost makes no difference.

I still have that dialog box (could not connect) from the frontend. If I OK it, I get a new one after a few seconds.

If I look at the /var/log/mythtv/mythbackend.log then the only related/suspicious things are (my comments in brackets):

Empty LocalHostName
(whereas in the setup screen it says localhost)
Using localhost value of k-tv
(which is correct: that's the computer name)
New DB connection, total 1
Connected to database mythconverg at host localhost
Closing DB connection named dbmanager0
(not sure why...)
Connected to database mythconverg at host localhost
Current mythtv schema version dbschemaver 1254
Mythbackend: starting up as the master server
new db connection, total 2
Connected to database mythconverg at host localhost
new db connection, total 3
Connected to database mythconverg at host localhost
new db scheduler connection
Connected to database mythconverg at host localhost
mediaserver:: loopback address specified - localhost. disabling upnp
(not sure why so many connections, but most of them seem to stay open)


Mythbackend is still running.

If I restart it with the method I described in the previous message (applications / system / mythtv backend setup), of course without changing any ip address, it then all works.


Is there anything specific I should be looking for in mythbackend.log?

If instead I look in the frontend logs, I get plenty of

Connection to master server timed out.
Either the server is down or the master server settings in mythtv-settings does [sic] not contain the proper ip address.


The exact settings for the backend (all from the default install, except for 127.0.0.1 -> localhost) are:

local backend
ip address: localhost
port 6543
status port 6544
security pin (required) 0000

master backend
ip address: localhost
port 6543

Both of the 6543 port settings say "unless you've got good reason to, don't change this".

In the frontend I have:

database server settings
hostname: localhost
ping test server? yes
port: [blank]
database name: mythconverg
user: mythtv
password: blablah

The port setting says "The port number the database is running on. Leave blank if using the default port (3306)." I assume it's correct for the database server and the master backend server to be on different ports.

Anything else I should check?
Thank you again

---

### Post by uncle hammy on 2010-10-23
I will admit to being a little bit confused.  Is this one machine backend / frontend, or two machines and the second frontend can't connect to the first frontend?

If it is one machine, it sounds to me that the mythtv user does not have permissions to the database from "localhost".  Write down the password from ~/.mythtv/mysql.txt and use it when asked executing the following.
```

sudo dpkg-reconfigure mythtv-common

sudo dpkg-reconfigure mythtv-database

```
That should clear up a permission issue.  If not, you can go old school....
```

mysql -uMYUSER -pMYPASS
GRANT ALL ON mythconverg.* to 'mythtv'@'localhost' IDENTIFIED BY 'MY PASS FROM MYSQL.TXT';
FLUSH PRIVILEGES;
EXIT

NOTE: If you will be using additional frontends, execute the following before "flush privileges'
GRANT ALL ON mythconverg.* to 'mythtv'@'%' IDENTIFIED BY 'MY PASS FROM MYSQL.TXT';

```

If it's case 2 (2 machines), then on the second frontend, you should not have "localhost" as the ip address, you'll need the actual ip address of the remote backend (i.e. 192.168.1.100).

Good luck.

---

### Post by ub40d on 2010-10-23
Thank you.

It is just one machine for now, but configured with the expectation that another frontend machine will be connecting to it later.

I did this

sudo dpkg-reconfigure mythtv-common
sudo dpkg-reconfigure mythtv-database

(saying that yes, other computers will run mythtv and connect to this as their master server) and on reboot I still have the same problem as before.

I redid it again, saying NO to the above question and... on reboot I still have the same problem, regardless.

As for the "old school" method, talking to the database works:

mysql --user=mythtv --password=blablah mythconverg

but the command you gave says 

error 1044 (42000): access denied for user 'mythtv'@'localhost' to database 'mythconverg'

despite the fact that, in ~mythtv/.mythtv/mysql.txt I have exactly the same stuff, namely

DBHostName=localhost
DBUserName=mythtv
DBName=mythconverg
DBType=QMYSQL3
DBPassword=blablah

(the pwd is not really blablah but it's the same as used above of course)

I am confused.

Once again this all came out of a vanilla installation from a freshly burnt 10.10 cd onto an empty hard disk... I am surprised I'm the only one with this problem among the many who got the new release, and I'd like to understand what's different in my setup!

---

### Post by uncle hammy on 2010-10-23
> **ub40d said:**
> As for the "old school" method, talking to the database works:

mysql --user=mythtv --password=blablah mythconverg

but the command you gave says 

error 1044 (42000): access denied for user 'mythtv'@'localhost' to database 'mythconverg'
Notice in my original post, I didn't specify to log into mysql with mythtv, I specified your user (though I probably should have used root).  However, your attempt to do so, and the error you got does seem to indicate that mythtv does not have mysql permissions from localhost.

Do this...

```

mysql -uroot -pMY COMPUTER PASSWORD THAT I SET DURING INSTALL
GRANT ALL ON mythconverg.* to 'mythtv'@'localhost' IDENTIFIED BY 'MY PASS FROM MYSQL.TXT';
FLUSH PRIVILEGES;
EXIT

```

Note: using ROOT as the user to log into mysql, not mythtv

---

### Post by ub40d on 2010-10-23
> **uncle hammy said:**
> Notice in my original post, I didn't specify to log into mysql with mythtv, I specified your user (though I probably should have used root). 


Sorry, I misunderstood what you meant then.

> 
 However, your attempt to do so, and the error you got does seem to indicate that mythtv does not have mysql permissions from localhost.

Do this...

```

mysql -uroot -pMY COMPUTER PASSWORD THAT I SET DURING INSTALL
GRANT ALL ON mythconverg.* to 'mythtv'@'localhost' IDENTIFIED BY 'MY PASS FROM MYSQL.TXT';
FLUSH PRIVILEGES;
EXIT

```

Note: using ROOT as the user to log into mysql, not mythtv

OK, what you say makes sense. I executed the commands above without error. Unfortunately, on reboot, I still have the same problem (Could not connect to the master backend server etc etc).

Sigh...

---

### Post by uncle hammy on 2010-10-23
Try changing the IP address in your frontend to 127.0.0.1 or the actual address (i.e. 192.168.1.100).

---

### Post by ub40d on 2010-10-23
When changing to the actual address (192.168...) it says it can't connect to the database. (Weird!) It says so after a while even on the setup screen itself, without the need for rebooting.

When changing to 127.0.0.1 it doesn't complain there and then, but on reboot I get the usual "Could not connect to the master backend server". 

Other note, probably much more relevant: while redoing all these experiments I noticed that, if I press ESC to dismiss that dialog box, it comes up again after some 5-10 seconds. And again. And again. However, after a good while (like 5-10 mins after mythfrontend comes up) it goes away by itself without coming back.

Now, the crucial point is that, while the dialog box keeps popping up like whack-a-mole, the mythbackend process isn't running! (as reported by ps) 
But later mythbackend starts and then the dialog box no longer appears.

This is slightly different from what I observed and reported this morning, where as soon as I got the dialog box I'd check with ps and I'd find a running mythbackend. Not sure what caused this change.

It seems as if, on this installation, mythbackend takes a *lot* longer to start than mythfrontend. If that's really the problem, how can I figure out what's slowing down its startup?

---

### Post by uncle hammy on 2010-10-23
Well, at least we know you don't have a mysql permissions issue.  As to what's causing your backend to take so long to start, I don't know.  Issues with your tuners maybe?  

I am not familiar with what goes on in starting the backend to make much of a guess.

---

### Post by jMon54 on 2010-10-29
I wish I could aid in a solution here but I just want to add my voice in that I am having this same exact issue after many troubleshooting steps including multiple fresh installs.  For me this is a killer in that I use Mythwelcome to turn my box on as needed.  My next try is to lengthen the time before recording is set to begin in the hopes if I give it enough time the issue will be resolved.

But I wonder isn't there some kind of script that could be auto-executed after boot to restart the front and backends?

Note: I am now on 10.10

---

### Post by rjg_munga on 2011-02-05
I have the same issue as 'ub40d'. I'm running ubuntu 10.10 from a fresh install, using the auto login and using mythwelcome to start mythfrontend. 
I have try the suggestions from this thread and from this bug report
[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/470672](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/470672)
all without success. I have had to add a 30 sec sleep in the /usr/bin/mythfrontend script to avoid the connection issue, I'm hoping this is only a temporary fix/hack.
The weird thing is that if I shutdown mysql, mythbackend and mythfrontend then start them all up manually they is no connection issue.

I've run out of ideas to try so if anyone has any suggestions I'd love to hear them.

---


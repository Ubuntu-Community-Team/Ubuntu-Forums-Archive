---
title: "myth back-end doesn't start at boot, but restarts later fine"
date: 2009-03-06
forum: Mythbuntu
---

### Post by ubnewbie2 on 2009-03-06
I was trying to enable networking for the mysql database behind mythtv (by commenting out the bind statement in my,cnf), and didn't quite get it working, so I decided to return everything to where it was at first.So I removed the comment from the bind statement in my.cnf.  I ran the backend setup (from the xfce menu) and changed it back to 127.0.0.1.

I started the front-end and it all seemed to work, so I rebooted the machine to make sure all would come up working.  Well, it didn't.  The front-end reported it couldn't contact the backend, so I exited it. I then ran the back-end setup from the xfce menu, and it seemed OK (set to 127.0.0.1), so I exited that again.  Now when I restarted the front-end, it works.

So, I rebooted again, and checked the mythtv logs.  Sure enough, the backend is failing to start on reboot, but it starts fine after running the setup (not changing anything) from the xfce menu.

How do I fix this?  Here's the log from a failed start

```

2009-03-07 10:26:51.232 Using runtime prefix = /usr
2009-03-07 10:26:51.289 Empty LocalHostName.
2009-03-07 10:26:51.335 Using localhost value of mythtv-server
2009-03-07 10:26:51.526 New DB connection, total: 1
2009-03-07 10:26:51.636 Unable to connect to database!
2009-03-07 10:26:51.712 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-03-07 10:26:52.029 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
................................................................................
2009-03-07 10:26:54.372 UPnPautoconf() - No UPnP backends found
2009-03-07 10:26:54.373 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [localhost]  
[console is not interactive, using default 'localhost']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [OIaGrT99]  
[console is not interactive, using default 'xxxxxxx']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2009-03-07 10:26:54.380 Could not open settings file /home/mythtv/.mythtv/mysql.txt for writing
2009-03-07 10:26:54.380 Deleting UPnP client...
2009-03-07 10:26:54.680 Failed to init MythContext, exiting.
```

---

### Post by ubnewbie2 on 2009-03-07
Further developments...

I have found why the mysql database didn't work so well when I enabled networking.  I needed to set mysql to not cache and to not resolve hostnames - because my small home network has no dns.  The ultra-slow performance is gone (that's why I tried to roll back to no networking yesterday)

However, the main problem remains - the mythtv backend does still fails to start on boot, and needs a restart later (upon which it works fine).

Any ideas?

---

### Post by scary_jeff on 2009-03-07
I had a similar problem which was basically caused by the network manager being too slow or too late starting to really work with static IPs and mysql. My problem was solved by removing network manager completely, and setting a static IP in a config file I found out about on the web somewhere.

The alternative would have been to reorder the starting of different services (i.e. move network manager to start before mysqld and mythbackend), which was also suggested on the web; this didn't work for me.

This might not be needed at all. Look in /var/log/mythbackend.log and "cat /var/log/syslog | grep mysql", and see if there are any error messages that might help identify the cause of the problem.

---

### Post by ubnewbie2 on 2009-03-08
> **scary_jeff said:**
> I had a similar problem which was basically caused by the network manager being too slow or too late starting to really work with static IPs and mysql. My problem was solved by removing network manager completely, and setting a static IP in a config file I found out about on the web somewhere.

The alternative would have been to reorder the starting of different services (i.e. move network manager to start before mysqld and mythbackend), which was also suggested on the web; this didn't work for me.

This might not be needed at all. Look in /var/log/mythbackend.log and "cat /var/log/syslog | grep mysql", and see if there are any error messages that might help identify the cause of the problem.

mythbackend.log is what I quoted in my first message.  To me it just looks like mysql hasn't started yet when mythtvbackend tries to log in to it. There's no mention of mysql in syslog.

I might try juggling the order services start - although I'll need to find out how it works in ubuntu.  Maybe I can just insert a delay in the mythbackend startup script?

---

### Post by scary_jeff on 2009-03-08
I guess you could edit the mythbackend startup script, but it's very odd to have nothing at all about mysql in syslog. You say that mythbackend starts up properly if you run the setup; can you connect a frontend? If so, then to me there must be something about mysql in syslog...

---

### Post by ubnewbie2 on 2009-03-08
> **scary_jeff said:**
> I guess you could edit the mythbackend startup script, but it's very odd to have nothing at all about mysql in syslog. You say that mythbackend starts up properly if you run the setup; can you connect a frontend? If so, then to me there must be something about mysql in syslog...

Mythbackend starts, even if you just do a restart from the command line.  Running Setup from the menu, which I wanted to do to check the config, also stops and restarts the backend, so that gets it going as well.

Yes, the frontend connects fine (once I get the backend up).

I issued the command you gave, i.e.

cat /var/log/syslog | grep mysql

and nothing was reported.  I supposed I should try that after a reboot, because maybe the log rotated or something, and lost the mysql references.

---

### Post by scary_jeff on 2009-03-09
OWhat happens if you sudo mysqld after restarting? Does it say mysql is already running? I'm at a bit of a loss now as to what to suggest...

---

### Post by 4dognight on 2009-03-09
> **ubnewbie2 said:**
> 
2009-03-07 10:26:54.380 Could not open settings file /home/mythtv/.mythtv/mysql.txt for writing


Check your permissions on that file.
Another possibilty is permissions on the database are wrong.
Try connecting manually to the database server as mythtv user.

---

### Post by ubnewbie2 on 2009-03-09
> **4dognight said:**
> Check your permissions on that file.
Another possibilty is permissions on the database are wrong.
Try connecting manually to the database server as mythtv user.

```


$ ls -al /home/mythtv/.mythtv/mysql.txt
lrwxrwxrwx 1 mythtv root 21 2008-10-05 11:15 /home/mythtv/.mythtv/mysql.txt -> /etc/mythtv/mysql.txt
$ ls -al /etc/mythtv/mysql.txt
-rw-r--r-- 1 root root 78 2009-03-07 10:25 /etc/mythtv/mysql.txt

```

I am not sure how permissions can be the issue however, as it starts up fine later, just not during boot time.

Same thing for database login, it works fine normally.

---

### Post by ubnewbie2 on 2009-03-09
> **scary_jeff said:**
> OWhat happens if you sudo mysqld after restarting? Does it say mysql is already running? I'm at a bit of a loss now as to what to suggest...

when I use the restart script

i.e.   sudo /etc/init.d/mythtv-backend restart

it says no running backend was found when it tried to stop it, then it starts normally


```
$ sudo /etc/init.d/mythtv-backend restart
 * Restarting MythTV server: mythbackend                                        
No /usr/bin/mythbackend found running; none killed.
                                                                         [ OK ]

```


when I try sudo mysqld it complains it can't get a lock on some files - check if another mysql process is already running, so it is running, but I don't think this proves whether it was running when nythbackend first tried to start

---

### Post by 4dognight on 2009-03-09
try this to test your connection to the database.

mysql -h 127.0.0.1 --user mythtv --password mythconverg

enter your password you entered for user mythtv

to exit just type 'exit;'

this will test your connection to the database is working.

---

### Post by ubnewbie2 on 2009-03-09
> **4dognight said:**
> try this to test your connection to the database.

mysql -h 127.0.0.1 --user mythtv --password mythconverg

enter your password you entered for user mythtv

to exit just type 'exit;'

this will test your connection to the database is working.

Why do you think it's not working?  I keep saying that the backend starts and everything works (records programs, plays recordings on frontend etc) as long as I restart the backend after it boots.  The mysql database is up and working.  I can log into it with mysql-admin.

---

### Post by 4dognight on 2009-03-10
you are getting a permission error. This is from your log

2009-03-07 10:26:54.380 Could not open settings file /home/mythtv/.mythtv/mysql.txt for writing

And you showed it being owned by user root with 644 permissions. So you should change it to 666. 

You posted the frontend log. Can we see your backend log that fails on boot?

when you manually start the backend. can you check who is running the backend, by using the ps command.

---

### Post by ubnewbie2 on 2009-03-10
> **4dognight said:**
> you are getting a permission error. This is from your log

2009-03-07 10:26:54.380 Could not open settings file /home/mythtv/.mythtv/mysql.txt for writing
.


Yes, but that was from a failed start.  Did you notice that that error was in a section at the end - after it had failed to find the database, and after it had entered some sort of auto reconfigure mode?  That doesn't happen when it starts normally.

> **4dognight said:**
> 
And you showed it being owned by user root with 644 permissions. So you should change it to 666. .

I would have thought those permissions were as set by the designers of mythbuntu and hence unlikely to be wrong.  Maybe it's only a problem because of the auto-reconfigure it attempts?

> **4dognight said:**
> 
You posted the frontend log. Can we see your backend log that fails on boot?.

I posted the main log file that I found in /var/log/mythtv.  I was not aware that there was a separate backend only log.  I will look for it tonight.


> **4dognight said:**
> 
when you manually start the backend. can you check who is running the backend, by using the ps command.

I will check this as well and report back.

---

### Post by nickrout on 2009-03-10
my guess:

[LIST]
[*]there is a delay in starting mysqld for some reason; therefore
[*]mythbackend cannot connect to mysqld and fails to start on boot; and
[*]later the mysqld startup has completed and mythbackend starts OK.
[/LIST]

If I am right you need to find out why mysqld is not starting properly. Try looking in different logs, like /var/log/daemon.log.

You can try:

grep -r mysql /var/log/*.log 

if necessary piping it through less if it goes on for pages, or piping it through some more grep statements to search more finely (eg by  date to get just the ones from today).

Often if reverse dns is not working properly there are long timeouts on startting services, as the program sits waiting for a reverse lookup that never comes, and this can take a while to time out. 

Similarly if networking is not up properly some things will not work at all. This can be a pain on systems with network manager that may not get a network address until after someone logs in to X (even if that is an auto login, it comes way after other services should have started).

---

### Post by ubnewbie2 on 2009-03-11
> **nickrout said:**
> my guess:

[LIST]
[*]there is a delay in starting mysqld for some reason; therefore
[*]mythbackend cannot connect to mysqld and fails to start on boot; and
[*]later the mysqld startup has completed and mythbackend starts OK.
[/LIST]

If I am right you need to find out why mysqld is not starting properly. Try looking in different logs, like /var/log/daemon.log.

You can try:

grep -r mysql /var/log/*.log 

if necessary piping it through less if it goes on for pages, or piping it through some more grep statements to search more finely (eg by  date to get just the ones from today).

Often if reverse dns is not working properly there are long timeouts on startting services, as the program sits waiting for a reverse lookup that never comes, and this can take a while to time out. 

Similarly if networking is not up properly some things will not work at all. This can be a pain on systems with network manager that may not get a network address until after someone logs in to X (even if that is an auto login, it comes way after other services should have started).


Reversedns lookups could well be the problem.  I am on a small private network with no dns server.  I had to turn off hostname lookup and caching in mysql to get normal performance out of it after startup.  So maybe there's another setting I have to tweak (or, as per one of my earlier ideas, just delay mythbackend's startup)

---

### Post by ubnewbie2 on 2009-03-11
> I posted the main log file that I found in /var/log/mythtv.  I was not aware that there was a separate backend only log.  I will look for it tonight.

I was wrong.  The log file I posted was indeed the mythbackend log.



> 
I will check this as well and report back.

```
$ ps -ef|grep 'mythbackend'
mythtv    6368     1  0 Mar10 ?        00:11:45 /usr/bin/mythbackend --daemon --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid

```


Seems to be running as mythtv as I believe it should

---

### Post by ubnewbie2 on 2009-03-11
> **nickrout said:**
> my guess:

[LIST]
[*]there is a delay in starting mysqld for some reason; therefore
[*]mythbackend cannot connect to mysqld and fails to start on boot; and
[*]later the mysqld startup has completed and mythbackend starts OK.
[/LIST]


Well I fixed it.  You were very nearly correct.  What really was happening is that mysql was being started at S50  whereas mythbackend was being started before that at S20 in /etc/rc2.d !!!

Something must have altered that.  Maybe an update of mysql?

Anyway, I changed mythtv backend to start at S99, and it all came up fine after a reboot.

Thanks for the help.

---

### Post by nickrout on 2009-03-11
on my hardy system both mysql and mythtv-backend start at 20

weird.

---

### Post by ubnewbie2 on 2009-03-11
> **nickrout said:**
> on my hardy system both mysql and mythtv-backend start at 20

weird.

Definitely weird.  This all started because I was enabling network access to the mysql database. The only thing I can think of, is that I used mysql-admin (the gui) to enable networking on mysql.  Mythbuntu, by default, not using the network. Maybe, mysql-admin has some smarts and moved mysql startup to later in the boot process.

---


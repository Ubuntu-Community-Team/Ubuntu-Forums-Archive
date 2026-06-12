---
title: "[SOLVED] mythconverg, backend, errors"
date: 2009-01-03
forum: Mythbuntu
---

### Post by iitywygms on 2009-01-03
So I screwed up and downloaded a huge file to my desktop and used up all the space in my home folder.  This caused errors, big errors.  My guide data went away and so did my tv recordings.  SO, I delete the huge file, restart mythtv.  The frontend would not start.  I got a no upnp error message.
So after some messing around I finally got everything working. BUT, I had to configure the mythbackend setup using root and my root password. (backend setup)
So now mythbackend is setup using root user with root password.  Is this okay?  I would like to use the mythtv user and password but have no idea what he mythtv password is.
I see many error messages about permissions deleting files.  Here is a snipit.

kevin@mythtv:~$ mythbackend
2009-01-02 23:35:44.989 Using runtime prefix = /usr
2009-01-02 23:35:44.991 Empty LocalHostName.
2009-01-02 23:35:44.991 Using localhost value of mythtv
2009-01-02 23:35:45.010 New DB connection, total: 1
2009-01-02 23:35:45.014 Unable to connect to database!
2009-01-02 23:35:45.014 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-01-02 23:35:45.065 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QServerSocket: failed to bind or listen to the socket
2009-01-02 23:35:45.117 MCP::InitUPnP() - HttpServer Create Error
2009-01-02 23:35:45.117 Deleting UPnP client...
2009-01-02 23:35:45.117 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [yes]  
Database host name: [localhost]      
Should I test connectivity to this host using the ping command? [yes]  
Database non-default port: [0]  
Database name: [mythconverg]  
Database user name: [mythtv]  root
Database password: [4fd639a1]  DELETEDBYMEFORTHISFORUM
Unique identifier for this machine (if empty, the local host name will be used):  
Would you like to use Wake-On-LAN to retry database connections? [no]  
2009-01-02 23:36:24.269 Writing settings file /home/kevin/.mythtv/mysql.txt
2009-01-02 23:36:24.269 Closing DB connection named 'DBManager0'
2009-01-02 23:36:24.270 Connected to database 'mythconverg' at host: localhost
2009-01-02 23:36:24.271 Closing DB connection named 'DBManager0'
2009-01-02 23:36:24.271 Connected to database 'mythconverg' at host: localhost
2009-01-02 23:36:24.273 New DB connection, total: 2
2009-01-02 23:36:24.273 Connected to database 'mythconverg' at host: localhost
2009-01-02 23:36:24.303 Current Schema Version: 1214
Starting up as the master server.
2009-01-02 23:36:24.351 New DB connection, total: 3
2009-01-02 23:36:24.352 Connected to database 'mythconverg' at host: localhost
2009-01-02 23:36:24.366 HDHRChan(ffffffff/0): device found at address 192.168.2.5
2009-01-02 23:36:24.451 HDHRChan(ffffffff/1): device found at address 192.168.2.5
2009-01-02 23:36:24.752 New DB scheduler connection
2009-01-02 23:36:24.752 Connected to database 'mythconverg' at host: localhost
2009-01-02 23:36:24.840 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-02 23:36:24.840 Main::Registering HttpStatus Extension
2009-01-02 23:36:24.841 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-02 23:36:24.841 Enabled verbose msgs:  important general
2009-01-02 23:36:24.872 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-02 23:36:27.820 Reschedule requested for id -1.
2009-01-02 23:36:30.858 Scheduled 177 items in 3.0 = 2.05 match + 0.96 place
2009-01-02 23:36:30.865 Seem to be woken up by USER
2009-01-02 23:36:44.768 Expiring 36 MBytes for 1021 @ Fri Jan 2 21:00:00 2009 => College Football Postgame
2009-01-02 23:36:47.808 Error deleting '/D2/LiveTV/1021_20090102210000.mpg' could not open 
			eno: Permission denied (13)
2009-01-02 23:36:47.808 Delete Error '/D2/LiveTV/1021_20090102210000.mpg'
			eno: Permission denied (13)


Edit 
This is defiantly a problem because I can no longer delete shows, they just re-appear after I delete them.
Thanks

---

### Post by iitywygms on 2009-01-03
Never mind, this issue is fixed.

---

### Post by aalh on 2009-03-20
so it is SOLVED
HOW?

if there is no solution in the thread, why leave the problem?

just wasted time reading this thinking i would find help

describing a problem them simply saying "I fixed it." is at least as bad as asking for help by saying "It's broke." and giving no other info

I wasted more time reading through a pointless thread

my adding this commentary is certainly not worse

---

### Post by joeinbend on 2009-04-03
I second that -- PLEASE post the solution!! This is a useless thread without the solution!!!

---

### Post by iitywygms on 2009-04-05
Hey sorry about that.  To be honest I am not sure exactly what fixed it as I did many things until if finally worked again.
Mainly I just deleted files as sudo until there was enough free space.  
After that, the frontend started working again.  As far as some recorded shows not deleting, I ran mythfrontend with sudo and then deleted the shows that would not previously stay deleted.
I would have posted a solution sooner had I had one solution that worked.

---


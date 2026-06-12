---
title: "MythTV problems (MySQL problem?)"
date: 2008-11-25
forum: Multimedia Software
---

### Post by tommy.sean on 2008-11-25
Hi there.
I'm having  an issue setting up MythTV on Ubuntu. It has something to do with the MySQL.
I was running 8.04 but just tried upgrading to 8.1 to see if that would help. It didn't. After doing some reading I found a website that said during MythTV setup “it will ask you for a password for the MySQL root user. It is strongly recommended that you leave this blank. Specifying a password here has been known to cause database access problems later on.” I think thats what happened. 


I am getting the following message:

New DB connection, total: 1
Unable to connect to database!
Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QsqkQuery::exec: database not open
QsqkQuery::exec: database not open
DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QsqlError? Strange...
QserverScoket: failed to bind or listen to the socket
Deleting UPnP client...
No UPnP backends found


Then it asks me several questions (“Would you like to configure database now?” and the other few setup questions) and then returns me to exact same error message. 

Total noob here, and a little uncomfortable with the command line. So if you can offer any advice, please be specific. (To be honest, I don't even know what MySQL is. :-/ 

Thanks
Tommy

P.S. My video capture card works fine, can use it with TVtime.

---


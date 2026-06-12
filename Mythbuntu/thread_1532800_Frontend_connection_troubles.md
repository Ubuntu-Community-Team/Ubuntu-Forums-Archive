---
title: "Frontend connection troubles"
date: 2010-07-17
forum: Mythbuntu
---

### Post by jimmyoo0 on 2010-07-17
I am having a bit of trouble connecting a frontend to a frontend/backend this is what i get;

```

styles@styles-desktop:~$ sudo mythfrontend -v most
[sudo] password for styles: 
2010-07-17 16:10:56.526 mythfrontend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-07-17 16:10:56.527 (old)Settings::ReadSettings(settings.txt) - No such file
2010-07-17 16:10:56.527 Using runtime prefix = /usr
2010-07-17 16:10:56.527 Using configuration directory = /home/styles/.mythtv
2010-07-17 16:10:56.527 UPnp - Constructor
2010-07-17 16:10:56.527 MediaRenderer::Begin
2010-07-17 16:10:56.527 ThreadPool:AddWorkerThread - HTTP_WorkerThread
2010-07-17 16:10:56.528 HttpServer() - SharePath = /usr/share/mythtv/
2010-07-17 16:10:56.528 UPnp::Initialize - Begin
2010-07-17 16:10:56.528 UPnp::Initialize - Starting TaskQueue
2010-07-17 16:10:56.528 UPnp::Initialize - Creating SSDP Thread at port 6547
2010-07-17 16:10:56.529 UPnp::Initialize - End
2010-07-17 16:10:56.529 MediaRenderer::Creating UPnp Description
2010-07-17 16:10:56.529 MediaRenderer::Registering MythFEXML Service.
2010-07-17 16:10:56.529 MediaRenderer::Registering CMGR Service.
2010-07-17 16:10:56.529 UPnp::Start - Starting SSDP Thread (Multicast)
2010-07-17 16:10:56.529 UPnp::Start - Enabling Notifications
2010-07-17 16:10:56.529 SSDP::EnableNotifications() - creating new task
2010-07-17 16:10:56.529 SSDP::EnableNotifications() - sending NTS_byebye
2010-07-17 16:10:56.529 LookupUDN(urn:schemas-upnp-org:device:MediaRenderer:1) sName=UPnP/UDN/MediaRenderer, sUDN=4e896da3-b413-47ea-8fde-b411fbead870
2010-07-17 16:10:57.535 SSDP::EnableNotifications() - sending NTS_alive
2010-07-17 16:10:57.536 SSDP::EnableNotifications() - Task added to UPnP queue
2010-07-17 16:10:57.536 UPnp::Start - Returning
2010-07-17 16:10:57.536 MediaRenderer::End
2010-07-17 16:10:57.536 (old)Settings::ReadSettings(settings.txt) - No such file
2010-07-17 16:10:57.537 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - No such file
2010-07-17 16:10:57.537 (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file
2010-07-17 16:10:57.537 (old)Settings::ReadSettings(/home/styles/.mythtv/mysql.txt) - 'DBHostName' = '10.1.1.10'.
2010-07-17 16:10:57.537 (old)Settings::ReadSettings(/home/styles/.mythtv/mysql.txt) - 'DBHostPing' = 'no'.
2010-07-17 16:10:57.537 (old)Settings::ReadSettings(/home/styles/.mythtv/mysql.txt) - 'DBPort' = '6543'.
2010-07-17 16:10:57.537 (old)Settings::ReadSettings(/home/styles/.mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2010-07-17 16:10:57.537 (old)Settings::ReadSettings(/home/styles/.mythtv/mysql.txt) - 'DBPassword' = 'cs5I9yfQ'.
2010-07-17 16:10:57.538 (old)Settings::ReadSettings(/home/styles/.mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2010-07-17 16:10:57.538 (old)Settings::ReadSettings(/home/styles/.mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2010-07-17 16:10:57.538 (old)Settings::ReadSettings(./mysql.txt) - No such file
2010-07-17 16:10:57.538 Empty LocalHostName.
2010-07-17 16:10:57.538 Using localhost value of styles-desktop
2010-07-17 16:10:57.539 MCP::DefaultUPnP() - No default UPnP backend
2010-07-17 16:10:57.539 MythSocket(ffffffffb6504c28:17): new socket
2010-07-17 16:10:57.539 MythSocket(ffffffffb6504c28:17): attempting connect() to (10.1.1.10:6543)
2010-07-17 16:10:57.540 MythSocket(ffffffffb6504c28:17): state change Idle -> Connected
2010-07-17 16:10:57.540 MythSocket(ffffffffb6504c28:17): state change Connected -> Idle
2010-07-17 16:10:57.546 New DB connection, total: 1

```then it just sits there and does nothing further.

i have had a bit of a google and i have commented out "bind host 127.0.0.1" in the database settings

I have also altered the privileges table for the mythtv database to allow the frontend  to access the backend as per [http://www.mythtv.org/wiki/Frontend](http://www.mythtv.org/wiki/Frontend)

```
    mysql -u root -p mysql
    mysql> grant all on mythconverg.* to 'mythtv'@'%' identified by 'passwd';
    mysql> flush privileges;
    mysql> exit;

```one weird thing was when i looked at the database table of connected users there was the mythtv user form "10.1.1.10" (the backend) but the user form "10.1.1.6" the connecting front end was a "%" under the name, is this part of the problem?

Thanks in advance

---

### Post by jimmyoo0 on 2010-07-17
After leaving it for over 30 min in that state it has now progressed and has added this to ht end of it and is now sitting doing nothing again

```

2010-07-17 16:40:28.383 ===============================================================================
2010-07-17 16:40:28.383  URI (type) - Found: 14 Entries - 14 have been Allocated. 
2010-07-17 16:40:28.383            USN (unique id)         | Expires     | Location
2010-07-17 16:40:28.383 -------------------------------------------------------------------------------
2010-07-17 16:40:28.383 upnp:rootdevice
2010-07-17 16:40:28.383  *         uuid:40e11113-ee44-4ac5-ba1b-dfcb48f03fd9::upnp:rootdevice     | 3594     | http://10.1.1.10:6544/getDeviceDesc 
2010-07-17 16:40:28.383  *         uuid:4e896da3-b413-47ea-8fde-b411fbead870::upnp:rootdevice     | 1829     | http://10.1.1.4:6547/getDeviceDesc 
2010-07-17 16:40:28.383  *         uuid:775b6680-bfde-11d3-99cf-00173f8c1099::upnp:rootdevice     | 88     | http://192.168.2.2:49152/description.xml 
2010-07-17 16:40:28.383  
2010-07-17 16:40:28.383 urn:microsoft.com:service:X_MS_MediaReceiverRegistrar:1
2010-07-17 16:40:28.383  *         uuid:40e11113-ee44-4ac5-ba1b-dfcb48f03fd9::urn:microsoft.com:service:X_MS_MediaReceiverRegistrar:1     | 3595     | http://10.1.1.10:6544/getDeviceDesc 
2010-07-17 16:40:28.383  
2010-07-17 16:40:28.383 urn:schemas-mythtv-org:device:MasterMediaServer:1
2010-07-17 16:40:28.383  *         uuid:d7c6fa05-66e9-49d5-b4f8-ded4a2a3b837::urn:schemas-mythtv-org:device:MasterMediaServer:1     | 3595     | http://10.1.1.10:6544/getDeviceDesc 
2010-07-17 16:40:28.384  
2010-07-17 16:40:28.384 urn:schemas-mythtv-org:service:MythTv:1
2010-07-17 16:40:28.384  *         uuid:4e896da3-b413-47ea-8fde-b411fbead870::urn:schemas-mythtv-org:service:MythTv:1     | 1830     | http://10.1.1.4:6547/getDeviceDesc 
2010-07-17 16:40:28.384  *         uuid:d7c6fa05-66e9-49d5-b4f8-ded4a2a3b837::urn:schemas-mythtv-org:service:MythTv:1     | 3595     | http://10.1.1.10:6544/getDeviceDesc 
2010-07-17 16:40:28.384  
2010-07-17 16:40:28.384 urn:schemas-upnp-org:device:MediaRenderer:1
2010-07-17 16:40:28.384  *         uuid:4e896da3-b413-47ea-8fde-b411fbead870::urn:schemas-upnp-org:device:MediaRenderer:1     | 1830     | http://10.1.1.4:6547/getDeviceDesc 
2010-07-17 16:40:28.384  
2010-07-17 16:40:28.384 urn:schemas-upnp-org:device:MediaServer:1
2010-07-17 16:40:28.384  *         uuid:40e11113-ee44-4ac5-ba1b-dfcb48f03fd9::urn:schemas-upnp-org:device:MediaServer:1     | 3594     | http://10.1.1.10:6544/getDeviceDesc 
2010-07-17 16:40:28.384  
2010-07-17 16:40:28.384 urn:schemas-upnp-org:service:ConnectionManager:1
2010-07-17 16:40:28.384  *         uuid:40e11113-ee44-4ac5-ba1b-dfcb48f03fd9::urn:schemas-upnp-org:service:ConnectionManager:1     | 3595     | http://10.1.1.10:6544/getDeviceDesc 
2010-07-17 16:40:28.387  *         uuid:4e896da3-b413-47ea-8fde-b411fbead870::urn:schemas-upnp-org:service:ConnectionManager:1     | 1830     | http://10.1.1.4:6547/getDeviceDesc 
2010-07-17 16:40:28.387  
2010-07-17 16:40:28.387 urn:schemas-upnp-org:service:ContentDirectory:1
2010-07-17 16:40:28.387  *         uuid:40e11113-ee44-4ac5-ba1b-dfcb48f03fd9::urn:schemas-upnp-org:service:ContentDirectory:1     | 3595     | http://10.1.1.10:6544/getDeviceDesc 
2010-07-17 16:40:28.387  
2010-07-17 16:40:28.387 urn:schemas-wifialliance-org:device:WFADevice:1
2010-07-17 16:40:28.387  *         uuid:775b6680-bfde-11d3-99cf-00173f8c1099::urn:schemas-wifialliance-org:device:WFADevice:1     | 89 | http://192.168.2.2:49152/description.xml 
2010-07-17 16:40:28.387  
2010-07-17 16:40:28.387 urn:schemas-wifialliance-org:service:WFAWLANConfig:1
2010-07-17 16:40:28.387  *         uuid:775b6680-bfde-11d3-99cf-00173f8c1099::urn:schemas-wifialliance-org:service:WFAWLANConfig:1     | 89 | http://192.168.2.2:49152/description.xml 
2010-07-17 16:40:28.387  
2010-07-17 16:40:28.387 uuid:40e11113-ee44-4ac5-ba1b-dfcb48f03fd9
2010-07-17 16:40:28.388  *         uuid:40e11113-ee44-4ac5-ba1b-dfcb48f03fd9     | 3594     | http://10.1.1.10:6544/getDeviceDesc 
2010-07-17 16:40:28.388  
2010-07-17 16:40:28.388 uuid:4e896da3-b413-47ea-8fde-b411fbead870
2010-07-17 16:40:28.388  *         uuid:4e896da3-b413-47ea-8fde-b411fbead870     | 1829     | http://10.1.1.4:6547/getDeviceDesc 
2010-07-17 16:40:28.388  
2010-07-17 16:40:28.388 uuid:775b6680-bfde-11d3-99cf-00173f8c1099
2010-07-17 16:40:28.388  *         uuid:775b6680-bfde-11d3-99cf-00173f8c1099     | 88     | http://192.168.2.2:49152/description.xml 
2010-07-17 16:40:28.388  
2010-07-17 16:40:28.388 uuid:d7c6fa05-66e9-49d5-b4f8-ded4a2a3b837
2010-07-17 16:40:28.388  *         uuid:d7c6fa05-66e9-49d5-b4f8-ded4a2a3b837     | 3595     | http://10.1.1.10:6544/getDeviceDesc 
2010-07-17 16:40:28.388  
2010-07-17 16:40:28.388 -------------------------------------------------------------------------------
2010-07-17 16:40:28.388  Found: 18 Entries - 18 have been Allocated. 
2010-07-17 16:40:28.388 ===============================================================================

```

---

### Post by ian dobson on 2010-07-17
Hi,

It looks as if the frontend is trying to do a upnp media scan and has found several devices:-

[http://10.1.1.10:6544/getDeviceDesc](http://10.1.1.10:6544/getDeviceDesc)
[http://10.1.1.4:6547/getDeviceDesc](http://10.1.1.4:6547/getDeviceDesc) 
[http://192.168.2.2:49152/description.xml](http://192.168.2.2:49152/description.xml)

Sorry but I've never seen this before and google hasn't got anything.

The only thing I found was [http://ubuntuforums.org/showthread.php?t=815329](http://ubuntuforums.org/showthread.php?t=815329)

Regards
Ian Dobson

---

### Post by jimmyoo0 on 2010-07-17
[http://10.1.1.10:6544/getDeviceDesc](http://10.1.1.10:6544/getDeviceDesc) this is the backend
[http://10.1.1.4:6547/getDeviceDesc](http://10.1.1.4:6547/getDeviceDesc)  this is the frontend
[http://192.168.2.2:49152/description.xml](http://192.168.2.2:49152/description.xml) this looks as though it may be a router although it should be 10.1.1.2 but some times it plays up

there is no other computers on the network

I have removed the router and replaced it with a dumb switch, its probably not causing a problem but better to eliminate it and not have to worry.

It looks like removing the router hasn't changed anything, no surprise realy.

---

### Post by lnoland on 2010-07-18
> **jimmyoo0 said:**
> I am having a bit of trouble connecting a frontend to a frontend/backend this is what i get;

```

styles@styles-desktop:~$ sudo mythfrontend -v most
[sudo] password for styles: 
2010-07-17 16:10:56.526 mythfrontend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-07-17 16:10:56.527 (old)Settings::ReadSettings(settings.txt) - No such file
2010-07-17 16:10:56.527 Using runtime prefix = /usr
2010-07-17 16:10:56.527 Using configuration directory = /home/styles/.mythtv
2010-07-17 16:10:56.527 UPnp - Constructor
2010-07-17 16:10:56.527 MediaRenderer::Begin
2010-07-17 16:10:56.527 ThreadPool:AddWorkerThread - HTTP_WorkerThread
2010-07-17 16:10:56.528 HttpServer() - SharePath = /usr/share/mythtv/
2010-07-17 16:10:56.528 UPnp::Initialize - Begin
2010-07-17 16:10:56.528 UPnp::Initialize - Starting TaskQueue
2010-07-17 16:10:56.528 UPnp::Initialize - Creating SSDP Thread at port 6547
2010-07-17 16:10:56.529 UPnp::Initialize - End
2010-07-17 16:10:56.529 MediaRenderer::Creating UPnp Description
2010-07-17 16:10:56.529 MediaRenderer::Registering MythFEXML Service.
2010-07-17 16:10:56.529 MediaRenderer::Registering CMGR Service.
2010-07-17 16:10:56.529 UPnp::Start - Starting SSDP Thread (Multicast)
2010-07-17 16:10:56.529 UPnp::Start - Enabling Notifications
2010-07-17 16:10:56.529 SSDP::EnableNotifications() - creating new task
2010-07-17 16:10:56.529 SSDP::EnableNotifications() - sending NTS_byebye
2010-07-17 16:10:56.529 LookupUDN(urn:schemas-upnp-org:device:MediaRenderer:1) sName=UPnP/UDN/MediaRenderer, sUDN=4e896da3-b413-47ea-8fde-b411fbead870
2010-07-17 16:10:57.535 SSDP::EnableNotifications() - sending NTS_alive
2010-07-17 16:10:57.536 SSDP::EnableNotifications() - Task added to UPnP queue
2010-07-17 16:10:57.536 UPnp::Start - Returning
2010-07-17 16:10:57.536 MediaRenderer::End
2010-07-17 16:10:57.536 (old)Settings::ReadSettings(settings.txt) - No such file
2010-07-17 16:10:57.537 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - No such file
2010-07-17 16:10:57.537 (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file
2010-07-17 16:10:57.537 (old)Settings::ReadSettings(/home/styles/.mythtv/mysql.txt) - 'DBHostName' = '10.1.1.10'.
2010-07-17 16:10:57.537 (old)Settings::ReadSettings(/home/styles/.mythtv/mysql.txt) - 'DBHostPing' = 'no'.
2010-07-17 16:10:57.537 (old)Settings::ReadSettings(/home/styles/.mythtv/mysql.txt) - 'DBPort' = '6543'.
2010-07-17 16:10:57.537 (old)Settings::ReadSettings(/home/styles/.mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2010-07-17 16:10:57.537 (old)Settings::ReadSettings(/home/styles/.mythtv/mysql.txt) - 'DBPassword' = 'cs5I9yfQ'.
2010-07-17 16:10:57.538 (old)Settings::ReadSettings(/home/styles/.mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2010-07-17 16:10:57.538 (old)Settings::ReadSettings(/home/styles/.mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2010-07-17 16:10:57.538 (old)Settings::ReadSettings(./mysql.txt) - No such file
2010-07-17 16:10:57.538 Empty LocalHostName.
2010-07-17 16:10:57.538 Using localhost value of styles-desktop
2010-07-17 16:10:57.539 MCP::DefaultUPnP() - No default UPnP backend
2010-07-17 16:10:57.539 MythSocket(ffffffffb6504c28:17): new socket
2010-07-17 16:10:57.539 MythSocket(ffffffffb6504c28:17): attempting connect() to (10.1.1.10:6543)
2010-07-17 16:10:57.540 MythSocket(ffffffffb6504c28:17): state change Idle -> Connected
2010-07-17 16:10:57.540 MythSocket(ffffffffb6504c28:17): state change Connected -> Idle
2010-07-17 16:10:57.546 New DB connection, total: 1

```then it just sits there and does nothing further.

i have had a bit of a google and i have commented out "bind host 127.0.0.1" in the database settings

I have also altered the privileges table for the mythtv database to allow the frontend  to access the backend as per [http://www.mythtv.org/wiki/Frontend](http://www.mythtv.org/wiki/Frontend)

```
    mysql -u root -p mysql
    mysql> grant all on mythconverg.* to 'mythtv'@'%' identified by 'passwd';
    mysql> flush privileges;
    mysql> exit;

```one weird thing was when i looked at the database table of connected users there was the mythtv user form "10.1.1.10" (the backend) but the user form "10.1.1.6" the connecting front end was a "%" under the name, is this part of the problem?

Thanks in advance

First, I presume that when you entered that "grant all" you used the actual database password and not literally 'passwd'.

Check your file */etc/mysql/conf.d/mythtv.cnf* on your backend system.  If it has any of the following three lines, uncommented:

```
skip-networking
bind-address localhost
bind-address 127.0.0.1

```
Replace it with:

```
bind-address 0.0.0.0

```
Basically, the three lines I cited each attempt to prevent MySql connections from over the network, in the first case overtly, and in the other two by explicitly allowing only local connections through the loopback connector.  The replacement code says to allow connections from any interface.

You might see some places on the net where they recommend that change for the file */etc/mysql/my.cnf*.  That is fine for generic MySql but in mythtv */etc/mysql/conf.d/mythtv.cnf* trumps that file.

Hope that helps.

- Les

---

### Post by jimmyoo0 on 2010-07-19
I have now tried all that and it is still not working.

I can log in to the database on the backend from my frontend machine as suggested on this page [http://www.mythtvtalk.com/forum/installation-issues/12548-setting-up-frontend-connect-remote-backend.html](http://www.mythtvtalk.com/forum/installation-issues/12548-setting-up-frontend-connect-remote-backend.html)

using this i do get the full list of tables in the database, its not super quick about 30 seconds or so
```

mysql -u mythtv -p -h 10.1.1.10 mythconverg
mysql> show tables;
(You should get a list of mythtv tables)
mysql> quit

```any more ideas?

---

### Post by lnoland on 2010-07-19
> **jimmyoo0 said:**
> I have now tried all that and it is still not working.

I can log in to the database on the backend from my frontend machine as suggested on this page [http://www.mythtvtalk.com/forum/installation-issues/12548-setting-up-frontend-connect-remote-backend.html](http://www.mythtvtalk.com/forum/installation-issues/12548-setting-up-frontend-connect-remote-backend.html)

using this i do get the full list of tables in the database, its not super quick about 30 seconds or so
```

mysql -u mythtv -p -h 10.1.1.10 mythconverg
mysql> show tables;
(You should get a list of mythtv tables)
mysql> quit

```any more ideas?

Sorry, I can't really think of anything else to try at the moment (other than desperation moves like "try rebooting everything").  I am curious about your comment that it took "30 seconds or so" to get that list of tables -- on my system it occurs pretty much instantaneously -- but I can't imagine how that would be relevant to the connection issue (unless whatever is causing the slowness is causing timeouts to occur somewhere).

One thing you might do: you have been posting the logs from your frontend -- you might try posting current logs for both your frontend and your backend -- perhaps there is a problem on the backend which is rejecting the connection.  Unless you are using the upnp functionality, you might try using the --noupnp option to eliminate all of those messages from the log to make it easier to read.  (I have my system set up to always use --noupnp because of some bug I read about but I don't remember what the bug was so I don't know if it is still relevant).

The only other thing I can think of at the moment is to verify that you have the same version of mythtv for both front end and back end -- I remember reading that mixing versions is not guaranteed to work.

If I think of anything else I will let you know.

 - Les

---

### Post by jimmyoo0 on 2010-07-20
Good thinking i didnt realy pay much attention to my backend log as i thought it was a database issue, in my log there is this one line then i try to run the connect the frontend;

2010-07-20 20:24:09.295 MainServer, Warning: Unknown socket closing MythSocket(0xffffffffadf1bcc8)

i then found this and it seems to be exactly the same problem, no resolution though.

[http://www.mailinglistarchive.com/html/mythtv-users@mythtv.org/2009-09/msg02084.html](http://www.mailinglistarchive.com/html/mythtv-users@mythtv.org/2009-09/msg02084.html)

thanks for your help so far

---

### Post by lnoland on 2010-07-20
> **jimmyoo0 said:**
> Good thinking i didnt realy pay much attention to my backend log as i thought it was a database issue, in my log there is this one line then i try to run the connect the frontend;

2010-07-20 20:24:09.295 MainServer, Warning: Unknown socket closing MythSocket(0xffffffffadf1bcc8)

i then found this and it seems to be exactly the same problem, no resolution though.

[http://www.mailinglistarchive.com/html/mythtv-users@mythtv.org/2009-09/msg02084.html](http://www.mailinglistarchive.com/html/mythtv-users@mythtv.org/2009-09/msg02084.html)

thanks for your help so far

It seems to me that I had a similar issue early on but I don't remember what I did to fix it.  There were so many issues getting MythTV set up and it seemed like each time I searched for a fix, there were a dozen things to try before finally resolving an issue -- it's hard to keep track of what worked and what didn't.  I remember at one point I had somehow defined both of my backends as slaves (or was it both were defined as masters?) and I seem to recall that confused my front end quite a bit.  I know you only have one backend, but perhaps you should check if it is defined as the master backend?

Another thing I thought about, though it doesn't seem like it would cause the "unknown socket" issue, is that I don't recall seeing anything in the MythTV documentation regarding accounts and groups on different computers.  I'm not a Unix expert so I am not sure how Unix treats the situation but I noticed when I set up my front end system that the user, "mythtv", and the group, "mythtv" on my frontend system were defined with a different uid/gid than on my backend system.  I wasn't sure that this was a problem, but since one can identify users and groups by either name or number, it seemed like it would be a good idea to have them be the same on each system, so I modified them to be the same (and then had to change permissions on all files owned by them to match the new uid/gid).  Since I have never seen any mention in the MythTV literature that such a thing was necessary, it is probably irrelevant, but I thought I would mention it, just in case.

Good luck.

- Les

---

### Post by axelsvag on 2010-07-23
I also have trouble getting my frontend find my backend. I tried this " [http://www.hackourlives.com/setting-up-multiple-remote-frontend-for-an-existing-mythtv-backend/comment-page-1/#comment-1598](http://www.hackourlives.com/setting-up-multiple-remote-frontend-for-an-existing-mythtv-backend/comment-page-1/#comment-1598) " as it looked promising but I get stucked at the " sudo service mysqld restart " which seems to be different from my old 8.04 setup. Maybe some have any idea what this command was called a few years ago?

---

### Post by ian dobson on 2010-07-23
Hi,

I imagine the command is sudo /etc/init.d/mythtv-backend restart

just do a ls /etc/init.d/ to see what services are available.

Regards
Ian Dobson

---

### Post by jimmyoo0 on 2010-07-23
[COLOR=Black]Hi axelsvag[/COLOR], thanks for the link, i have gone through all those steps previously and am still getting

```
MainServer, Warning: Unknown socket closing MythSocket(0xffffffffadf1bcc:cool:)
```

---

### Post by axelsvag on 2010-07-25
I used the hard method with a reboot instead of a restart of mysql daemon.

---

### Post by braddock on 2010-08-02
I too am having this problem.  mythfrontend works when running on the same server as the mythbackend, but when I try mythfrontend from my laptop it hangs at "New DB connection, total: 1" (on frontend), and "MainServer, Warning: Unknown socket closing MythSocket(0x18531b0)" in the mythbackend.log.

Both hosts are from-scratch 10.04 installs with all updates installed.

I've only ever had two successful mythtv installations in 8 years of trying... was working for me under 9.04 for six blissful months. :/

---

### Post by braddock on 2010-08-02
I got it working.  

Some combination of apt-get removing mythtv-frontend on my laptop, wiping all of /etc/mythtv and ~/.mythtv, attempting to set the mysql password (buggy gui?) on the frontend, and then wiping all of ~/.mythtv AGAIN and restarting the frontend made it work.

---

### Post by braddock on 2010-08-06
Just a followup in case my last post left an optimistic impression...

1) MythTV worked for exactly one day and then audio stopped working.  I don't know if it is some bad interaction with pulse or something else, but it has me stumped after sinking an hour into the problem.

2) Furthermore, it turns out that MythTV Analog channel scanning is broken - and has been known to be broken in the latest builds for a couple years.  In addition, attempts to add channels manually failed for me.

3) An attempt at using a SchedulesDirect account failed.  I get AUTH errors when mythfilldatabase runs, despite double and triple checking and reentering my account name and password.

MythTV provides fantastic functionality.  I just wish it worked.

---

### Post by jimmyoo0 on 2010-09-10
So i have had some more tome to try and get this working,

To re-cap; combined BE/FE working and able to connect ok, FE on another machine can not connect.

I made sure FE had the same settings as in Mythbackend-setup on the BE/FE machine, this did not work.
So then i thought what settings has the FE on the BE/FE machine got if it can connect, the only difference is it was connecting on port 3306, not the port 6543 (default) listed in Mythbackend-setup.
So i changed my FE settings on my other machine to port 3306 and it worked, it was very slow and had lots of "readStringList: Error, timed out after 7000 ms." errors but it worked.

So my question is how can my BE settings in Mythbackend-setup say port 6543 but nothing can connect to that port but connects to 3306? what is going wrong?

---

### Post by peterthevicar on 2010-10-08
> **jimmyoo0 said:**
> 
So i changed my FE settings on my other machine to port 3306 and it worked, it was very slow and had lots of "readStringList: Error, timed out after 7000 ms." errors but it worked.

So my question is how can my BE settings in Mythbackend-setup say port 6543 but nothing can connect to that port but connects to 3306? what is going wrong?

THANK YOU!! I've been chasing this for hours with no luck. Of course (in retrospect!) the DBPort is for MySQL so has to be 3306. Like you I put in 6543 as that was the only port mentioned in the MythTV stuff. In fact just leaving out the DBPort line in mysql.txt works since 3306 is the default. They probably should put a better title for the entry in the setup menus.

Thank you again, Peter

---


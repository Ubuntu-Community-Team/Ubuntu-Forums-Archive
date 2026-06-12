---
title: "Mythbuntu 9.10 frontend wont display mythfrontend"
date: 2009-12-13
forum: Mythbuntu
---

### Post by Beatbreaker on 2009-12-13
I've battled on this for a day now and i'm finding it hard to continue without any further ideas or instruction. everything i've tried gives me the impression that mythtv is working correctly, but it just won't display.

quick rundown on my setup. My backend runs Arch Linux, the frontend runs Mythbuntu 9.10. It used to run Mythbuntu 9.04 perfectly but now i'm having real issues.


so i've updated to 0.22 on the backend and the frontend. The backend presents mythfrontend as it should.

the problem is when i've installed mythbuntu 9.10 i just can't get it to display mythfrontend. it seems like it's connecting fine, I can connect to the database from both front/backend using this command:
```
mysql -h <backend IP> -u mythtv mythconverg -p
```

But if i run mythfrontend -v all in the termianl it will just stop at the end of the output and i have to CTRL-Z out because mythtv won't start


```
michael@myth-frontend:~$ ps -ef | grep myth
michael   1412  1383  0 17:55 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/share/mythbuntu/session.sh
michael   1415     1  0 17:55 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/share/mythbuntu/session.sh
michael   1727  1708  0 18:12 pts/0    00:00:00 grep --color=auto myth
michael@myth-frontend:~$ mythfrontend -v most
2009-12-13 18:12:36.437 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2009-12-13 18:12:36.453 (old)Settings::ReadSettings(settings.txt) - No such file
2009-12-13 18:12:36.453 Using runtime prefix = /usr
2009-12-13 18:12:36.453 Using configuration directory = /home/michael/.mythtv
2009-12-13 18:12:36.453 UPnp - Constructor
2009-12-13 18:12:36.453 MediaRenderer::Begin
2009-12-13 18:12:36.454 ThreadPool:AddWorkerThread - HTTP_WorkerThread
2009-12-13 18:12:36.454 HttpServer() - SharePath = /usr/share/mythtv/
2009-12-13 18:12:36.454 UPnp::Initialize - Begin
2009-12-13 18:12:36.454 UPnp::Initialize - Starting TaskQueue
2009-12-13 18:12:36.455 UPnp::Initialize - Creating SSDP Thread at port 6547
2009-12-13 18:12:36.455 UPnp::Initialize - End
2009-12-13 18:12:36.455 MediaRenderer::Creating UPnp Description
2009-12-13 18:12:36.455 MediaRenderer::Registering MythFEXML Service.
2009-12-13 18:12:36.455 MediaRenderer::Registering CMGR Service.
2009-12-13 18:12:36.455 UPnp::Start - Starting SSDP Thread (Multicast)
2009-12-13 18:12:36.455 UPnp::Start - Enabling Notifications
2009-12-13 18:12:36.455 SSDP::EnableNotifications() - creating new task
2009-12-13 18:12:36.456 SSDP::EnableNotifications() - sending NTS_byebye
2009-12-13 18:12:36.456 LookupUDN(urn:schemas-upnp-org:device:MediaRenderer:1) sName=UPnP/UDN/MediaRenderer, sUDN=861e82ef-9dae-46ee-82dd-7c56483c396f
2009-12-13 18:12:37.307 SSDP::EnableNotifications() - sending NTS_alive
2009-12-13 18:12:37.307 SSDP::EnableNotifications() - Task added to UPnP queue
2009-12-13 18:12:37.307 UPnp::Start - Returning
2009-12-13 18:12:37.307 MediaRenderer::End
2009-12-13 18:12:37.307 (old)Settings::ReadSettings(settings.txt) - No such file
2009-12-13 18:12:37.307 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBHostName' = '192.168.1.200'.
2009-12-13 18:12:37.308 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBPort' = '6543'.
2009-12-13 18:12:37.308 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2009-12-13 18:12:37.308 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBPassword' = 'mythtv'.
2009-12-13 18:12:37.308 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2009-12-13 18:12:37.308 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2009-12-13 18:12:37.308 (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file
2009-12-13 18:12:37.308 (old)Settings::ReadSettings(/home/michael/.mythtv/mysql.txt) - 'DBHostName' = '192.168.1.200'.
2009-12-13 18:12:37.308 (old)Settings::ReadSettings(/home/michael/.mythtv/mysql.txt) - 'DBPort' = '6543'.
2009-12-13 18:12:37.308 (old)Settings::ReadSettings(/home/michael/.mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2009-12-13 18:12:37.308 (old)Settings::ReadSettings(/home/michael/.mythtv/mysql.txt) - 'DBPassword' = 'mythtv'.
2009-12-13 18:12:37.308 (old)Settings::ReadSettings(/home/michael/.mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2009-12-13 18:12:37.308 (old)Settings::ReadSettings(/home/michael/.mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2009-12-13 18:12:37.309 (old)Settings::ReadSettings(./mysql.txt) - No such file
2009-12-13 18:12:37.309 Empty LocalHostName.
2009-12-13 18:12:37.309 Using localhost value of myth-frontend
2009-12-13 18:12:37.309 MCP::DefaultUPnP() - No default UPnP backend
2009-12-13 18:12:37.309 Testing network connectivity to '192.168.1.200'
2009-12-13 18:12:37.316 MythSocket(9a774a0:20): new socket
2009-12-13 18:12:37.316 MythSocket(9a774a0:20): attempting connect() to (192.168.1.200:6543)
2009-12-13 18:12:37.316 MythSocket(9a774a0:20): state change Idle -> Connected
2009-12-13 18:12:37.316 MythSocket(9a774a0:20): state change Connected -> Idle
2009-12-13 18:12:37.326 New DB connection, total: 1
```

after it does all that then it'll just stop  i think i'm going crazy! need help please :(

---


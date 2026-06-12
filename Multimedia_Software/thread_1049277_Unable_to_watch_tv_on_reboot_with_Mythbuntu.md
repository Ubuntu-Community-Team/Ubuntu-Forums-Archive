---
title: "Unable to watch tv on reboot with Mythbuntu"
date: 2009-01-24
forum: Multimedia Software
---

### Post by sschneidertx on 2009-01-24
I have a new HTPC system using Mythbuntu 8.10 64-bit.  My system is a AMD X2 2.6 GHz with NVIDIA 8300 and HDHR connected directly to PC on wired ethernet port eth0.  I have wireless connectivity to internet on ath0.  My install was made with a single user "scott" who I have verified is a member of the mythtv group.

When I reboot the HTPC the "Watch TV" option does nothing.  When I quite Mythfrontend and look at the Mythbackend log file it shows that it was unable to connect to the HDHR (Device not found).  From my research it appears that this error is due to the HDHR not getting an address prior to the Mythbackend starting.  I am still using NetworkManager.

My bigger issue is that when I try to manually start the Mythbackend using "sudo /etc/init.d/mythtv-backend start" and I review the " /var/log/mythtv/mythbackend.log" it has the follwoing information with the error at the end.  It connects to the HDHR but the "Watch TV" option does not work.  I have tried to change the ownership of the recording directory to "scott" from "mythtv" to no avail (drwxrwsr-x 2 scott mythtv 4096 2009-01-24 10:45 /var/lib/mythtv/recordings/).  Any suggestions?

> 2009-01-24 11:16:06.109 Using runtime prefix = /usr
2009-01-24 11:16:06.119 Empty LocalHostName.
2009-01-24 11:16:06.129 Using localhost value of scott-desktop
2009-01-24 11:16:06.136 New DB connection, total: 1
2009-01-24 11:16:06.174 Connected to database 'mythconverg' at host: localhost
2009-01-24 11:16:06.175 Closing DB connection named 'DBManager0'
2009-01-24 11:16:06.176 Connected to database 'mythconverg' at host: localhost
2009-01-24 11:16:06.178 New DB connection, total: 2
2009-01-24 11:16:06.179 Connected to database 'mythconverg' at host: localhost
2009-01-24 11:16:06.181 Current Schema Version: 1214
Starting up as the master server.
2009-01-24 11:16:06.195 HDHRChan(ffffffff/0): device found at address 10.0.0.1
2009-01-24 11:16:06.197 New DB connection, total: 3
2009-01-24 11:16:06.198 Connected to database 'mythconverg' at host: localhost
2009-01-24 11:16:06.312 HDHRChan(ffffffff/1): device found at address 10.0.0.1
2009-01-24 11:16:06.320 New DB scheduler connection
2009-01-24 11:16:06.334 Connected to database 'mythconverg' at host: localhost
QServerSocket: failed to bind or listen to the socket
2009-01-24 11:16:06.341 MediaServer::HttpServer Create Error
2009-01-24 11:16:06.342 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-24 11:16:06.343 Enabled verbose msgs:  important general
2009-01-24 11:16:06.345 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QServerSocket: failed to bind or listen to the socket
2009-01-24 11:16:06.354 Failed to bind port 6543. Exiting.


---


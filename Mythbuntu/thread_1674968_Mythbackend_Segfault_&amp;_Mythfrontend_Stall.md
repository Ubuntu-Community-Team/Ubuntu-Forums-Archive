---
title: "Mythbackend Segfault &amp; Mythfrontend Stall"
date: 2011-01-24
forum: Mythbuntu
---

### Post by ashton88 on 2011-01-24
I am having trouble getting my mythfrontend to connect to my mythbackend.

Computer1 has myth frontend and backend installed.  I can watch TV on this system and it seems to work fine.  However, when I attempt to run mythbackend I get a segmentation fault (full log below).

Computer2 only has myth frontend installed.  I cannot get the frontend to run on this system (full log below).

Any help is appreciated!

Computer1@system:/usr/share/mythtv$ mythbackend -v all
```
2011-01-24 18:03:08.110 mythbackend version: fixes/0.24 [v0.24-113-g90fe13c] www.mythtv.org
2011-01-24 18:03:08.111 Using runtime prefix = /usr
2011-01-24 18:03:08.111 Using configuration directory = /home/user/.mythtv
2011-01-24 18:03:08.111 (old)Settings::ReadSettings(settings.txt) - No such file
2011-01-24 18:03:08.112 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - No such file
2011-01-24 18:03:08.112 (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file
2011-01-24 18:03:08.113 (old)Settings::ReadSettings(/home/user/.mythtv/mysql.txt) - 'DBHostName' = 'localhost'.
2011-01-24 18:03:08.113 (old)Settings::ReadSettings(/home/user/.mythtv/mysql.txt) - 'DBPort' = '3306'.
2011-01-24 18:03:08.113 (old)Settings::ReadSettings(/home/user/.mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2011-01-24 18:03:08.113 (old)Settings::ReadSettings(/home/user/.mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2011-01-24 18:03:08.113 (old)Settings::ReadSettings(/home/user/.mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2011-01-24 18:03:08.113 (old)Settings::ReadSettings(/home/user/.mythtv/mysql.txt) - 'DBPassword' = 'mythtv'.
2011-01-24 18:03:08.113 (old)Settings::ReadSettings(./mysql.txt) - No such file
2011-01-24 18:03:08.114 Empty LocalHostName.
2011-01-24 18:03:08.114 Using localhost value of Computer1
2011-01-24 18:03:08.114 Clearing Settings Cache.
2011-01-24 18:03:08.115 MCP::DefaultUPnP() - No default UPnP backend
2011-01-24 18:03:08.116 MythSocket(9686298:0): new socket
2011-01-24 18:03:08.120 MythSocket(9686298:0): attempting connect() to (127.0.0.1:3306)
2011-01-24 18:03:08.121 MythSocket(9686298:0): state change Idle -> Connected
2011-01-24 18:03:08.121 MythSocket(9686298:0): DownRef: -1
2011-01-24 18:03:08.121 MythSocket(9686298:0): state change Connected -> Idle
2011-01-24 18:03:08.122 MSocketDevice::close: Closed socket 0
2011-01-24 18:03:08.122 MythSocket(9686298:-1): delete socket
2011-01-24 18:03:08.122 Clearing Settings Cache.
2011-01-24 18:03:08.134 New DB connection, total: 1
2011-01-24 18:03:08.140 Connected to database 'mythconverg' at host: 127.0.0.1
2011-01-24 18:03:08.153 Closing DB connection named 'DBManager0'
2011-01-24 18:03:08.153 Clearing Settings Cache.
2011-01-24 18:03:08.155 Connected to database 'mythconverg' at host: 127.0.0.1
2011-01-24 18:03:08.157 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'language' AND hostname = 'computer1' <<<< Returns 1 row(s)
2011-01-24 18:03:08.158 MSqlQuery::next(DBManager0) Result: "data = EN_US"
2011-01-24 18:03:08.160 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'country' AND hostname = 'computer1' <<<< Returns 1 row(s)
2011-01-24 18:03:08.160 MSqlQuery::next(DBManager0) Result: "data = CA"
2011-01-24 18:03:08.160 Current locale EN_CA
2011-01-24 18:03:08.161 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
2011-01-24 18:03:08.163 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'freqtable' AND hostname = 'computer1' <<<< Returns 0 row(s)
2011-01-24 18:03:08.165 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'freqtable' AND hostname IS NULL <<<< Returns 1 row(s)
2011-01-24 18:03:08.165 MSqlQuery::next(DBManager0) Result: "data = us-cable"
2011-01-24 18:03:08.166 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'iso639language0' AND hostname = 'Computer1' <<<< Returns 0 row(s)
2011-01-24 18:03:08.168 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'iso639language0' AND hostname IS NULL <<<< Returns 1 row(s)
2011-01-24 18:03:08.168 MSqlQuery::next(DBManager0) Result: "data = eng"
2011-01-24 18:03:08.169 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'iso639language1' AND hostname = 'Computer1' <<<< Returns 0 row(s)
2011-01-24 18:03:08.170 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'iso639language1' AND hostname IS NULL <<<< Returns 1 row(s)
2011-01-24 18:03:08.170 MSqlQuery::next(DBManager0) Result: "data = eng"
2011-01-24 18:03:08.171 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'tvformat' AND hostname = 'Computer1' <<<< Returns 0 row(s)
2011-01-24 18:03:08.172 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'tvformat' AND hostname IS NULL <<<< Returns 1 row(s)
2011-01-24 18:03:08.172 MSqlQuery::next(DBManager0) Result: "data = NTSC"
2011-01-24 18:03:08.173 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'vbiformat' AND hostname = 'Computer1' <<<< Returns 0 row(s)
2011-01-24 18:03:08.174 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'vbiformat' AND hostname IS NULL <<<< Returns 1 row(s)
2011-01-24 18:03:08.174 MSqlQuery::next(DBManager0) Result: "data = None"
2011-01-24 18:03:08.176 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'country' AND hostname = 'Computer1' <<<< Returns 1 row(s)
2011-01-24 18:03:08.176 MSqlQuery::next(DBManager0) Result: "data = CA"
2011-01-24 18:03:08.177 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'dateformat' AND hostname = 'Computer1' <<<< Returns 1 row(s)
2011-01-24 18:03:08.177 MSqlQuery::next(DBManager0) Result: "data = ddd MMM d"
2011-01-24 18:03:08.178 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'language' AND hostname = 'Computer1' <<<< Returns 1 row(s)
2011-01-24 18:03:08.178 MSqlQuery::next(DBManager0) Result: "data = EN_US"
2011-01-24 18:03:08.180 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mytharchivedateformat' AND hostname = 'Computer1' <<<< Returns 1 row(s)
2011-01-24 18:03:08.180 MSqlQuery::next(DBManager0) Result: "data = %a  %b  %d"
2011-01-24 18:03:08.181 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mytharchivetimeformat' AND hostname = 'Computer1' <<<< Returns 1 row(s)
2011-01-24 18:03:08.181 MSqlQuery::next(DBManager0) Result: "data = %I:%M %p"
2011-01-24 18:03:08.182 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mytharchivevideoformat' AND hostname = 'Computer1' <<<< Returns 1 row(s)
2011-01-24 18:03:08.182 MSqlQuery::next(DBManager0) Result: "data = PAL"
2011-01-24 18:03:08.183 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mythwelcomedateformat' AND hostname = 'Computer1' <<<< Returns 1 row(s)
2011-01-24 18:03:08.184 MSqlQuery::next(DBManager0) Result: "data = dddd\\nMMM dd yyyy"
2011-01-24 18:03:08.184 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'shortdateformat' AND hostname = 'Computer1' <<<< Returns 1 row(s)
2011-01-24 18:03:08.184 MSqlQuery::next(DBManager0) Result: "data = M/d"
2011-01-24 18:03:08.186 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'timeformat' AND hostname = 'Computer1' <<<< Returns 1 row(s)
2011-01-24 18:03:08.186 MSqlQuery::next(DBManager0) Result: "data = h:mm AP"
2011-01-24 18:03:08.187 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'zoneminderdateformat' AND hostname = 'Computer1' <<<< Returns 1 row(s)
2011-01-24 18:03:08.188 MSqlQuery::next(DBManager0) Result: "data = ddd MMM d yyyy"
2011-01-24 18:03:08.189 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'zonemindertimeformat' AND hostname = 'Computer1' <<<< Returns 1 row(s)
2011-01-24 18:03:08.189 MSqlQuery::next(DBManager0) Result: "data = hh:mm AP"
2011-01-24 18:03:08.190 Enabling Settings Cache.
2011-01-24 18:03:08.190 Clearing Settings Cache.
2011-01-24 18:03:08.190 Disabling Settings Cache.
2011-01-24 18:03:08.190 Clearing Settings Cache.
2011-01-24 18:03:08.191 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'dbschemaautoupgrade' AND hostname = 'Computer1' <<<< Returns 0 row(s)
2011-01-24 18:03:08.192 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'dbschemaautoupgrade' AND hostname IS NULL <<<< Returns 0 row(s)
2011-01-24 18:03:08.194 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'dbschemaver' AND hostname = 'Computer1' <<<< Returns 0 row(s)
2011-01-24 18:03:08.195 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'dbschemaver' AND hostname IS NULL <<<< Returns 1 row(s)
2011-01-24 18:03:08.195 MSqlQuery::next(DBManager0) Result: "data = 1264"
2011-01-24 18:03:08.195 Current MythTV Schema Version (DBSchemaVer): 1264
2011-01-24 18:03:08.196 Enabling Settings Cache.
2011-01-24 18:03:08.196 Clearing Settings Cache.
2011-01-24 18:03:08.197 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'backendserverip' AND hostname = 'Computer1' <<<< Returns 2 row(s)
2011-01-24 18:03:08.197 MSqlQuery::next(DBManager0) Result: "data = 127.0.0.1"
2011-01-24 18:03:08.199 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'masterserverip' AND hostname = 'Computer1' <<<< Returns 0 row(s)
2011-01-24 18:03:08.203 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'masterserverip' AND hostname IS NULL <<<< Returns 1 row(s)
2011-01-24 18:03:08.203 MSqlQuery::next(DBManager0) Result: "data = 127.0.0.1"
2011-01-24 18:03:08.204 UPnp - Constructor
2011-01-24 18:03:08.204 MediaServer::Begin
2011-01-24 18:03:08.205 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'backendstatusport' AND hostname = 'Computer1' <<<< Returns 2 row(s)
2011-01-24 18:03:08.205 MSqlQuery::next(DBManager0) Result: "data = 6544"
2011-01-24 18:03:08.212 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'threadpool/http/initial' AND hostname = 'Computer1' <<<< Returns 0 row(s)
2011-01-24 18:03:08.213 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'threadpool/http/initial' AND hostname IS NULL <<<< Returns 0 row(s)
2011-01-24 18:03:08.215 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'threadpool/http/max' AND hostname = 'Computer1' <<<< Returns 0 row(s)
2011-01-24 18:03:08.216 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'threadpool/http/max' AND hostname IS NULL <<<< Returns 0 row(s)
2011-01-24 18:03:08.217 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'threadpool/http/timeout' AND hostname = 'Computer1' <<<< Returns 0 row(s)
2011-01-24 18:03:08.218 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'threadpool/http/timeout' AND hostname IS NULL <<<< Returns 0 row(s)
2011-01-24 18:03:08.218 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-01-24 18:03:08.218 ThreadPool:AddWorkerThread - HTTP_WorkerThread
2011-01-24 18:03:08.220 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'http/keepalivetimeoutsecs' AND hostname = 'Computer1' <<<< Returns 0 row(s)
2011-01-24 18:03:08.220 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'http/keepalivetimeoutsecs' AND hostname IS NULL <<<< Returns 0 row(s)
2011-01-24 18:03:08.221 ThreadPool:HTTP: thread pool size 1
2011-01-24 18:03:08.221 HttpServer() - SharePath = /usr/share/mythtv/
2011-01-24 18:03:08.222 MediaServer::HttpServer Create Error
2011-01-24 18:03:08.222 ThreadPool:HTTP: thread pool size 0
2011-01-24 18:03:08.222 WorkerThread:Run - Exiting: HTTP_WorkerThread
Segmentation fault
```

Computer2@system:~$ mythfrontend -v all
```
2011-01-24 19:00:45.663 mythfrontend version: branches/release-0-23-fixes [26437] www.mythtv.org
2011-01-24 19:00:45.664 (old)Settings::ReadSettings(settings.txt) - No such file
2011-01-24 19:00:45.664 Using runtime prefix = /usr
2011-01-24 19:00:45.664 Using configuration directory = /home/user/.mythtv
2011-01-24 19:00:45.665 UPnp - Constructor
2011-01-24 19:00:45.671 MediaRenderer::Begin
2011-01-24 19:00:45.672 ThreadPool:AddWorkerThread - HTTP_WorkerThread
2011-01-24 19:00:45.676 HttpServer() - SharePath = /usr/share/mythtv/
2011-01-24 19:00:45.682 MediaRenderer::HttpServer Create Error
2011-01-24 19:00:45.683 WorkerThread:Run - Exiting: HTTP_WorkerThread
2011-01-24 19:00:45.686 (old)Settings::ReadSettings(settings.txt) - No such file
2011-01-24 19:00:45.687 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - No such file
2011-01-24 19:00:45.687 (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file
2011-01-24 19:00:45.688 (old)Settings::ReadSettings(/home/user/.mythtv/mysql.txt) - 'DBHostName' = '192.168.9.98'.
2011-01-24 19:00:45.688 (old)Settings::ReadSettings(/home/user/.mythtv/mysql.txt) - 'DBPort' = '6543'.
2011-01-24 19:00:45.688 (old)Settings::ReadSettings(/home/user/.mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2011-01-24 19:00:45.688 (old)Settings::ReadSettings(/home/user/.mythtv/mysql.txt) - 'DBPassword' = 'mythtv'.
2011-01-24 19:00:45.688 (old)Settings::ReadSettings(/home/user/.mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2011-01-24 19:00:45.688 (old)Settings::ReadSettings(/home/user/.mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2011-01-24 19:00:45.689 (old)Settings::ReadSettings(./mysql.txt) - No such file
2011-01-24 19:00:45.689 Empty LocalHostName.
2011-01-24 19:00:45.689 Using localhost value of Computer2
2011-01-24 19:00:45.689 Clearing Settings Cache.
2011-01-24 19:00:45.690 MCP::DefaultUPnP() - No default UPnP backend
2011-01-24 19:00:45.698 Testing network connectivity to '192.168.9.98'
2011-01-24 19:00:45.727 MythSocket(98bc730:19): new socket
2011-01-24 19:00:45.727 MythSocket(98bc730:19): attempting connect() to (192.168.9.98:6543)
2011-01-24 19:00:45.728 MythSocket(98bc730:19): state change Idle -> Connected
2011-01-24 19:00:45.728 MythSocket(98bc730:19): state change Connected -> Idle
2011-01-24 19:00:45.728 MSocketDevice::close: Closed socket 19
2011-01-24 19:00:45.728 Clearing Settings Cache.
2011-01-24 19:00:45.760 New DB connection, total: 1
```

After this the myth GUI does not load. It just waits indefinitely in the terminal window.

---

### Post by newlinux on 2011-01-24
For your first problem, if you are able to watch tv mythtv-backend is probably already running - that could be what you are seeing.

The backend should be started using service with root priveleges e.g.
```

sudo service mythtv-backend start

```

It also appears the frontend on the second machine is .23 and the backend is .24 - This will lead to a protocol mismatch and will not work. You need to upgrade the frontend on your second machine.

you should also make sure your mysql.txt files and config.xml on the second mackend machine point to the master backend's IP address.

---

### Post by ashton88 on 2011-02-04
You were absolutely right.

I had installed the mythbunutu "fixes" package onto one of the 2 machines and in the process upgraded it to .24.  I hadn't done that on the second machine.

Thank you for your help!

---


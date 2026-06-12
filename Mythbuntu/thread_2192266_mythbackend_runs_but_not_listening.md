---
title: "mythbackend runs but not listening?"
date: 2013-12-06
forum: Mythbuntu
---

### Post by andrewc6l on 2013-12-06
I've got a strange one. After some updates, I'm in a state where it looks like mythbackend runs, but it isn't listening on 6543. Because of this, I get a black screen when my frontend starts up. (I'm running both my frontend and backend on the same server, but have the IP address specified - though I've tried it with 127.0.0.1 as well with no more success.)

Here's the end bit of the log from the backend:
```
2013-12-06 20:54:14.599467 I  Connected to database 'mythconverg' at host: localhost
2013-12-06 20:54:14.607375 N  Setting QT default locale to en_US
2013-12-06 20:54:14.607534 I  Current locale en_US
2013-12-06 20:54:14.616386 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2013-12-06 20:54:14.655727 I  Enabling Settings Cache.
2013-12-06 20:54:14.655748 I  Clearing Settings Cache.
2013-12-06 20:54:14.655924 E  setHttpProxy() - failed to find a network proxy
2013-12-06 20:54:14.660470 I  Disabling Settings Cache.
2013-12-06 20:54:14.660489 I  Clearing Settings Cache.
2013-12-06 20:54:14.663164 I  Current MythTV Schema Version (DBSchemaVer): 1317
2013-12-06 20:54:14.663199 I  Enabling Settings Cache.
2013-12-06 20:54:14.663214 I  Clearing Settings Cache.
2013-12-06 20:54:14.664898 I  Loading en_us translation for module mythfrontend
2013-12-06 20:54:14.666632 N  MythBackend: Starting up as the master server.
```
Note the error setHttpProxy() - I'm not sure if that has anything to do with anything. I don't have http_proxy or HTTP_PROXY set, as far as I can tell. This happened when I ran the backend from the command line.

When I ran the backend using Upstart, I got something without the proxy error:
```
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-115-gf785255] www.mythtv.org
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: I CoreContext mythcorecontext.cpp:249 (Init) Assumed character encoding: en_US.UTF-8
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: I Logger logging.cpp:315 (run) Added logging to the console
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtv
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: N CoreContext mythcorecontext.cpp:1272 (InitLocale) Setting QT default locale to en_US
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: I CoreContext mythcorecontext.cpp:1305 (SaveLocaleDefaults) Current locale en_US
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Dec  6 21:21:01 mythtv mythbackend: mythbackend[5757]: N CoreContext main_helpers.cpp:582 (run_backend) MythBackend: Starting up as the master server.

```

The front end shows:
```
2013-12-06 20:55:20.602513 I  MythCoreContext: Connecting to backend server: 192.168.1.17:6543 (try 1 of 1)
2013-12-06 20:55:20.602570 I  MythSocket(9f0b090:-1): MythSocket(-1, 0x0) ctor
2013-12-06 20:55:20.611739 I  MythSocket(9f0b090:-1): IP is local, using loopback address instead
2013-12-06 20:55:20.611793 I  MythSocket(9f0b090:-1): attempting connect() to (127.0.0.1:6543)
2013-12-06 20:55:20.612239 E  MythSocket(9f0b090:-1): Failed to connect to (127.0.0.1:6543) Connection refused
```

Doing a netstat
```
sudo netstat -nlp | grep 6543
```
shows that indeed, nobody is listening to that port (or 6544).

I'm running version 2:0.27.0+fixes.20131205.f785255-0ubuntu0mythbuntu2 as my backend on a 12.04 server (Linux mythtv 3.2.0-57-generic #87-Ubuntu SMP Tue Nov 12 21:38:12 UTC 2013 i686 i686 i386 GNU/Linux).

Any idea what might be going on? According to mythtv-setup, my ports are 6543 and 6544.

---

### Post by aelfric55 on 2013-12-10
At first blush, it looks as though you haven't tcp/ip-enabled the MySQL server to accept remote (tcp/ip) connections. Mysql is expecting  the local frontend client to talk to it locally via mysql.sock.  But your frontend is set up for tcp/ip, trying to connect via 192.168.1.17 (or 127.0.0.1) And Mysql isn't listening there.
Probably the best fix is to set up the backend on (static IP!) 192.167.1.17;  then enable "remote connections" (i.e. tcp/ip) for your MySQL server. Either from the control center, or by commenting out (#) the line in the my.cnf file under /etc referencing "skip-networking", adding a "bind" line for your static 192.168.1.17 address, and restarting mysqld

---

### Post by andrewc6l on 2013-12-11
Thank you! That was the problem. Apparently nowadays there's no longer a "skip-networking" in /etc/mysql/my.cnf - so I just added my host's IP address after the bind-address for localhost:

```

# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 127.0.0.1
# ... and I added the following:
bind-address            = 192.168.1.17

```

Once I did that, things started working. Perhaps it was that update which broke it to begin with. At any rate, I'm back recording. Thanks again!

---


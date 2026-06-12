---
title: "Mythbackend crashes on clean mythbuntu 14.04 install"
date: 2015-12-25
forum: Mythbuntu
---

### Post by varneyb on 2015-12-25
Recently had a drive crash in my MythTV server - been running mythbuntu 14.04 for some time. So I got a new drive and did a clean install (frontend and backend on the same machine), and now mythbackend is constantly crashing. It will crash whenever I try to schedule a recording via mythweb, and nothing will record. If I try to schedule recordings it appears to simply ignore the request (nothing is recorded), but doesn't crash immediately. It will also crash at times for no apparant reason.

I grabbed the mythTV Backend log and it's here:  [http://pastebin.com/ChEJfUnE](http://pastebin.com/ChEJfUnE)

Any help is greatly appreciated - this has worked for years on this hardware/network setup and I'm not sure why it has suddenly stopped...

Bruce

---

### Post by varneyb on 2015-12-25
OK, I just ran mythbackend from a terminal window and it crashed after two minutes:

```
2015-12-25 22:25:46.024707 C  mythbackend version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org2015-12-25 22:25:46.024738 C  Qt version: compile: 4.8.6, runtime: 4.8.6
2015-12-25 22:25:46.024741 N  Enabled verbose msgs:  general
2015-12-25 22:25:46.024755 N  Setting Log Level to LOG_INFO
2015-12-25 22:25:46.036135 I  Added logging to the console
2015-12-25 22:25:46.062954 I  Setup Interrupt handler
2015-12-25 22:25:46.062972 I  Setup Terminated handler
2015-12-25 22:25:46.062982 I  Setup Segmentation fault handler
2015-12-25 22:25:46.062992 I  Setup Aborted handler
2015-12-25 22:25:46.062999 I  Setup Bus error handler
2015-12-25 22:25:46.063008 I  Setup Floating point exception handler
2015-12-25 22:25:46.063016 I  Setup Illegal instruction handler
2015-12-25 22:25:46.063029 I  Setup Real-time signal 0 handler
2015-12-25 22:25:46.063092 N  Using runtime prefix = /usr
2015-12-25 22:25:46.063105 N  Using configuration directory = /home/mythtv/.mythtv
2015-12-25 22:25:46.063188 I  Assumed character encoding: en_US.UTF-8
2015-12-25 22:25:46.117720 N  Empty LocalHostName.
2015-12-25 22:25:46.117734 I  Using localhost value of VarneyTV
2015-12-25 22:25:46.165313 I  New Client:  (#1)
2015-12-25 22:25:46.313764 N  Setting QT default locale to EN_US
2015-12-25 22:25:46.313846 I  Current locale EN_US
2015-12-25 22:25:46.318199 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2015-12-25 22:25:46.356215 I  Current MythTV Schema Version (DBSchemaVer): 1317
2015-12-25 22:25:46.384953 I  Loading en_us translation for module mythfrontend
2015-12-25 22:25:46.387433 E  MythSocket(1a5a530:-1): Failed to connect to (127.0.0.1:6543) Connection refused
2015-12-25 22:25:46.395130 N  MythBackend: Running as a slave backend.
2015-12-25 22:25:46.471016 I  Registering HouseKeeperTask 'JobQueueRecover'.
2015-12-25 22:25:46.471033 I  Registering HouseKeeperTask 'HardwareProfiler'.
2015-12-25 22:25:46.471999 I  Starting HouseKeeper.
2015-12-25 22:25:46.542531 I  Listening on TCP 127.0.0.1:6544
2015-12-25 22:25:46.542575 I  Listening on TCP 192.1.1.50:6544
2015-12-25 22:25:46.542645 I  Listening on TCP [::1]:6544
2015-12-25 22:25:46.542715 I  Listening on TCP [fe80::201:2eff:fe38:45be%eth0]:6544
2015-12-25 22:26:12.134749 E  Bonjour: Error: -65537
2015-12-25 22:26:12.134762 E  Bonjour: Failed to register service.
2015-12-25 22:26:12.134774 I  Main::Registering HttpStatus Extension
2015-12-25 22:26:12.136318 I  Listening on TCP 127.0.0.1:6543
2015-12-25 22:26:12.136367 I  Listening on TCP 192.1.1.50:6543
2015-12-25 22:26:12.136454 I  Listening on TCP [::1]:6543
2015-12-25 22:26:12.136516 I  Listening on TCP [fe80::201:2eff:fe38:45be%eth0]:6543
2015-12-25 22:26:13.136895 N  Connecting to master server: 127.0.0.1:6543
2015-12-25 22:26:13.137593 N  Connected successfully
2015-12-25 22:26:43.182054 E  MythSocket(1a8dad0:34): ReadStringList: Error, timed out after 30000 ms.
2015-12-25 22:26:43.201464 W  MainServer: Unknown socket closing MythSocket(0x1a8dad0)
2015-12-25 22:26:43.201553 E  MythSocket(1a8dad0:-1): No response.
2015-12-25 22:26:43.201562 E  MainServer: Failed to open master server socket, timeout
2015-12-25 22:26:43.234076 I  adding: VarneyTV as a slave backend server
2015-12-25 22:26:43.234681 E  MythSocket(1a8c5b0:-1): WriteStringList: Error, called with unconnected socket.
2015-12-25 22:26:44.201950 N  Connecting to master server: 127.0.0.1:6543
2015-12-25 22:26:44.202337 N  Connected successfully
2015-12-25 22:27:14.234263 E  MythSocket(1a8dad0:35): ReadStringList: Error, timed out after 30000 ms.
2015-12-25 22:27:14.234375 W  MainServer: Unknown socket closing MythSocket(0x1a8dad0)
2015-12-25 22:27:14.234421 E  MythSocket(1a8dad0:-1): No response.
2015-12-25 22:27:14.234428 E  MainServer: Failed to open master server socket, timeout
2015-12-25 22:27:14.235390 I  adding: VarneyTV as a slave backend server
2015-12-25 22:27:14.235514 E  MythSocket(1a8c5b0:-1): WriteStringList: Error, called with unconnected socket.
2015-12-25 22:27:15.234583 N  Connecting to master server: 127.0.0.1:6543
2015-12-25 22:27:15.235047 N  Connected successfully
2015-12-25 22:27:45.269386 E  MythSocket(1a8c5b0:35): ReadStringList: Error, timed out after 30000 ms.
2015-12-25 22:27:45.269589 E  MythSocket(1a8c5b0:-1): No response.
2015-12-25 22:27:45.269765 E  MainServer: Failed to open master server socket, timeout
Handling Segmentation fault
Segmentation fault (core dumped)



```

Not sure if that helps diagnose it...

---

### Post by blm-ubunet on 2015-12-26
The backend seems to think it is a slave backend..
The first attempt to start (in your log) it appears networking is not up.
As you're using local link (127.0.0.1) that might not matter.

Also mythtv-setup needs to be run as user "mythtv" not "bruce".

Can you connect to the mysql server ?:
```
echo help | mysql -umythtv -p
```

You might have to check the contents of /etc/mysql/my.conf & your ~/.mythtv/config.xml for credentials.
New installs of mysql can make up crazy passwords..

---


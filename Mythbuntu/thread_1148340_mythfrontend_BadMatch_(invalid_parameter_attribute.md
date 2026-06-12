---
title: "mythfrontend BadMatch (invalid parameter attributes) 8"
date: 2009-05-04
forum: Mythbuntu
---

### Post by map7 on 2009-05-04
When I start my frontend on one computer I get this error:

```

2009-05-04 21:42:50.028 Using runtime prefix = /usr/local, libdir = /usr/local/lib
2009-05-04 21:42:50.595 XScreenSaver support enabled
2009-05-04 21:42:50.596 DPMS is active.
2009-05-04 21:42:50.597 Empty LocalHostName.
2009-05-04 21:42:50.597 Using localhost value of d110-laptop
2009-05-04 21:42:50.597 Testing network connectivity to 10.1.1.4
2009-05-04 21:42:50.620 New DB connection, total: 1
2009-05-04 21:43:00.714 Connected to database 'mythconverg' at host: 10.1.1.4
2009-05-04 21:43:00.724 Closing DB connection named 'DBManager0'
2009-05-04 21:43:00.725 Total desktop dim: 1280x800, with 1 screen[s].
2009-05-04 21:43:10.764 Connected to database 'mythconverg' at host: 10.1.1.4
2009-05-04 21:43:10.780 Using screen 0, 1280x800 at 0,0
2009-05-04 21:43:10.931 New DB connection, total: 2
2009-05-04 21:43:20.950 Connected to database 'mythconverg' at host: 10.1.1.4
2009-05-04 21:43:21.005 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-05-04 21:43:21.006 Enabled verbose msgs:  important general
2009-05-04 21:43:23.067 Total desktop dim: 1280x800, with 1 screen[s].
2009-05-04 21:43:23.077 Using screen 0, 1280x800 at 0,0
2009-05-04 21:43:23.083 Switching to square mode (Titivillus)
2009-05-04 21:43:23.181 Using the Qt painter
2009-05-04 21:43:23.182 JoystickMenuClient Error: Joystick disabled - Failed to read /home/d110/.mythtv/joystickmenurc
mythtv: No such file or directory
2009-05-04 21:43:23.182 lirc_init failed for mythtv, see preceding messages
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x420000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x420000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x420000e

```

My other remote frontend works fine.  It's only just started happening.  I've upgraded this computer with the issue from Ubuntu 810 to Ubuntu 904.

---

### Post by superm1 on 2009-05-04
ATI graphics? If so, known issue (see mythbuntu jaunty release notes):

[http://www.launchpad.net/bugs/341898](http://www.launchpad.net/bugs/341898)

---

### Post by broozm on 2009-05-23
> **superm1 said:**
> ATI graphics? If so, known issue (see mythbuntu jaunty release notes):

[http://www.launchpad.net/bugs/341898](http://www.launchpad.net/bugs/341898)

Thanks - good post, that tip fixes my Front end too, but my BackEnd is still throwing an error similar to the one above:
```
sudo XLIB_SKIP_ARGB_VISUALS="1" mythfrontend

``` 


When I run the Backend setup, I get a few lines of presumably good normal stuff, then continuously shows this error (until I kill that window):

```
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a01db7
```


I have pasted my entire set of logs here to give context...

PS (I have two monitors plugged in and working - an analog and a DVI)
TIA

```
==> /var/log/mythtv/mtd.log <==
mtd started at Mon May 25 10:20:52 2009
mtd is running on a host called bm-desktop
10:20:52: Waiting for connections/jobs
10:20:52: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-05-24 13:32:21.403 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-05-24 13:32:22.097 ERROR: Unable to create schemalock table: No error type from QSqlError?  Strange...
2009-05-24 13:32:22.124 Connected to database 'mythconverg' at host: localhost
2009-05-24 13:32:22.181 Current Schema Version: 1214
Starting up as the master server.
2009-05-24 13:32:22.246 New DB connection, total: 2
2009-05-24 13:32:22.252 Connected to database 'mythconverg' at host: localhost
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-05-24 13:32:22.321 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-05-24 13:32:22.324 Main::Registering HttpStatus Extension
2009-05-24 13:32:22.327 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-05-24 13:32:22.329 Enabled verbose msgs:  important general
2009-05-24 13:32:22.354 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 13:33:42.265 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 13:44:52.479 Using runtime prefix = /usr
2009-05-24 13:44:52.533 Empty LocalHostName.
2009-05-24 13:44:52.535 Using localhost value of bm-desktop
2009-05-24 13:44:52.545 New DB connection, total: 1
2009-05-24 13:44:52.552 Connected to database 'mythconverg' at host: localhost
2009-05-24 13:44:52.555 Closing DB connection named 'DBManager0'
2009-05-24 13:44:52.556 Connected to database 'mythconverg' at host: localhost
2009-05-24 13:44:52.561 New DB connection, total: 2
2009-05-24 13:44:52.564 Connected to database 'mythconverg' at host: localhost
2009-05-24 13:44:52.570 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-05-24 13:44:52.676 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-05-24 13:44:52.685 Main::Registering HttpStatus Extension
2009-05-24 13:44:52.686 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-05-24 13:44:52.687 Enabled verbose msgs:  important general
2009-05-24 13:44:52.693 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 13:46:12.606 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 13:47:29.368 Using runtime prefix = /usr
2009-05-24 13:47:29.414 Empty LocalHostName.
2009-05-24 13:47:29.415 Using localhost value of bm-desktop
2009-05-24 13:47:29.424 New DB connection, total: 1
2009-05-24 13:47:29.433 Connected to database 'mythconverg' at host: localhost
2009-05-24 13:47:29.435 Closing DB connection named 'DBManager0'
2009-05-24 13:47:29.437 Connected to database 'mythconverg' at host: localhost
2009-05-24 13:47:29.441 New DB connection, total: 2
2009-05-24 13:47:29.444 Connected to database 'mythconverg' at host: localhost
2009-05-24 13:47:29.450 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-05-24 13:47:29.539 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-05-24 13:47:29.545 Main::Registering HttpStatus Extension
2009-05-24 13:47:29.547 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-05-24 13:47:29.551 Enabled verbose msgs:  important general
2009-05-24 13:47:29.558 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 13:47:57.987 Using runtime prefix = /usr
2009-05-24 13:47:58.025 Empty LocalHostName.
2009-05-24 13:47:58.026 Using localhost value of bm-desktop
2009-05-24 13:47:58.036 New DB connection, total: 1
2009-05-24 13:47:58.044 Connected to database 'mythconverg' at host: localhost
2009-05-24 13:47:58.046 Closing DB connection named 'DBManager0'
2009-05-24 13:47:58.048 Connected to database 'mythconverg' at host: localhost
2009-05-24 13:47:58.054 New DB connection, total: 2
2009-05-24 13:47:58.056 Connected to database 'mythconverg' at host: localhost
2009-05-24 13:47:58.062 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-05-24 13:47:58.152 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-05-24 13:47:58.154 Main::Registering HttpStatus Extension
2009-05-24 13:47:58.155 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-05-24 13:47:58.161 Enabled verbose msgs:  important general
2009-05-24 13:47:58.166 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 13:48:01.754 MainServer::HandleAnnounce Monitor
2009-05-24 13:48:01.764 adding: bm-desktop as a client (events: 0)
2009-05-24 13:48:01.771 MainServer::HandleAnnounce Monitor
2009-05-24 13:48:01.772 adding: bm-desktop as a client (events: 1)
2009-05-24 13:48:49.255 Using runtime prefix = /usr
2009-05-24 13:48:49.290 Empty LocalHostName.
2009-05-24 13:48:49.291 Using localhost value of bm-desktop
2009-05-24 13:48:49.308 New DB connection, total: 1
2009-05-24 13:48:49.323 Connected to database 'mythconverg' at host: localhost
2009-05-24 13:48:49.326 Closing DB connection named 'DBManager0'
2009-05-24 13:48:49.327 Connected to database 'mythconverg' at host: localhost
2009-05-24 13:48:49.333 New DB connection, total: 2
2009-05-24 13:48:49.336 Connected to database 'mythconverg' at host: localhost
2009-05-24 13:48:49.341 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-05-24 13:48:49.418 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-05-24 13:48:49.428 Main::Registering HttpStatus Extension
2009-05-24 13:48:49.429 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-05-24 13:48:49.431 Enabled verbose msgs:  important general
2009-05-24 13:48:49.439 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-24 13:50:09.370 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

==> /var/log/mythtv/mythfrontend.log <==
  Minor opcode:  0
  Resource id:  0x3a0000c
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000c
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  149
  Minor opcode:  4
  Resource id:  0x28
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a01db4
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a001ca
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a01db4
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a01db4
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a01db4
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a01db4
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a01db4
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a01db4
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a01db4
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a01db4
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a01db4
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a01db4
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a01db7
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a01db7
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  7
  Resource id:  0x2804458
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x2800009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x2800009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x2800009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x2800009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x2800009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x2800009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x2800009
ICE default IO error handler doing an exit(), pid = 6340, errno = 11
ICE default IO error handler doing an exit(), pid = 3777, errno = 11

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
May 24 13:32:20 bm-desktop dhclient: DHCPOFFER of 192.168.1.11 from 192.168.1.1
May 24 13:32:20 bm-desktop dhclient: DHCPREQUEST of 192.168.1.11 on eth0 to 255.255.255.255 port 67
May 24 13:32:20 bm-desktop dhclient: DHCPACK of 192.168.1.11 from 192.168.1.1
May 24 13:32:20 bm-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
May 24 13:32:20 bm-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
May 24 13:32:20 bm-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
May 24 13:32:20 bm-desktop NetworkManager: <info>    address 192.168.1.11 
May 24 13:32:20 bm-desktop NetworkManager: <info>    prefix 24 (255.255.255.0) 
May 24 13:32:20 bm-desktop NetworkManager: <info>    gateway 192.168.1.1 
May 24 13:32:20 bm-desktop NetworkManager: <info>    hostname 'bm-desktop' 
May 24 13:32:20 bm-desktop NetworkManager: <info>    nameserver '192.168.1.1' 
May 24 13:32:20 bm-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May 24 13:32:20 bm-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
May 24 13:32:20 bm-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
May 24 13:32:20 bm-desktop avahi-daemon[2968]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.11.
May 24 13:32:20 bm-desktop avahi-daemon[2968]: New relevant interface eth0.IPv4 for mDNS.
May 24 13:32:20 bm-desktop avahi-daemon[2968]: Registering new address record for 192.168.1.11 on eth0.IPv4.
May 24 13:32:20 bm-desktop dhclient: bound to 192.168.1.11 -- renewal in 1407 seconds.
May 24 13:32:20 bm-desktop avahi-daemon[2968]: Withdrawing address record for fe80::20d:61ff:fe3a:2b8b on eth0.
May 24 13:32:20 bm-desktop avahi-daemon[2968]: Host name conflict, retrying with <bm-desktop-2>
May 24 13:32:20 bm-desktop avahi-daemon[2968]: Registering new address record for fe80::20d:61ff:fe3a:2b8b on eth0.*.
May 24 13:32:20 bm-desktop avahi-daemon[2968]: Registering new address record for 192.168.1.11 on eth0.IPv4.
May 24 13:32:20 bm-desktop avahi-daemon[2968]: Registering HINFO record with values 'I686'/'LINUX'.
May 24 13:32:21 bm-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 
May 24 13:32:21 bm-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
May 24 13:32:21 bm-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
May 24 13:32:21 bm-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
May 24 13:32:21 bm-desktop mysqld_safe[3250]: Number of processes running now: 1
May 24 13:32:21 bm-desktop mysqld_safe[3265]: mysqld process hanging, pid 2457 - killed
May 24 13:32:21 bm-desktop mysqld_safe[3270]: restarted
May 24 13:32:21 bm-desktop mysqld[3279]: InnoDB: The log sequence number in ibdata files does not match
May 24 13:32:21 bm-desktop mysqld[3279]: InnoDB: the log sequence number in the ib_logfiles!
May 24 13:32:21 bm-desktop mysqld[3279]: 090524 13:32:21  InnoDB: Database was not shut down normally!
May 24 13:32:21 bm-desktop mysqld[3279]: InnoDB: Starting crash recovery.
May 24 13:32:21 bm-desktop mysqld[3279]: InnoDB: Reading tablespace information from the .ibd files...
May 24 13:32:21 bm-desktop mysqld[3279]: InnoDB: Restoring possible half-written data pages from the doublewrite
May 24 13:32:21 bm-desktop mysqld[3279]: InnoDB: buffer...
May 24 13:32:21 bm-desktop avahi-daemon[2968]: Server startup complete. Host name is bm-desktop-2.local. Local service cookie is 342837176.
May 24 13:32:22 bm-desktop mysqld[3279]: 090524 13:32:22  InnoDB: Started; log sequence number 0 53911
May 24 13:32:22 bm-desktop mysqld[3279]: 090524 13:32:22 [Note] /usr/sbin/mysqld: ready for connections.
May 24 13:32:22 bm-desktop mysqld[3279]: Version: '5.0.75-0ubuntu10'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
May 24 13:32:27 bm-desktop kernel: [   39.152011] eth0: no IPv6 routers present
May 24 13:32:32 bm-desktop ntpd[2600]: ntpd exiting on signal 15
May 24 13:32:33 bm-desktop ntpdate[3366]: adjust time server 91.189.94.4 offset 0.058169 sec
May 24 13:32:33 bm-desktop ntpd[3395]: ntpd 4.2.4p4@1.1520-o Wed May 13 21:05:42 UTC 2009 (1)
May 24 13:32:33 bm-desktop ntpd[3396]: precision = 1.000 usec
May 24 13:32:33 bm-desktop ntpd[3396]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
May 24 13:32:33 bm-desktop ntpd[3396]: Listening on interface #1 wildcard, ::#123 Disabled
May 24 13:32:33 bm-desktop ntpd[3396]: Listening on interface #2 lo, ::1#123 Enabled
May 24 13:32:33 bm-desktop ntpd[3396]: Listening on interface #3 eth0, fe80::20d:61ff:fe3a:2b8b#123 Enabled
May 24 13:32:33 bm-desktop ntpd[3396]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
May 24 13:32:33 bm-desktop ntpd[3396]: Listening on interface #5 eth0, 192.168.1.11#123 Enabled
May 24 13:32:33 bm-desktop ntpd[3396]: kernel time sync status 0040
May 24 13:32:33 bm-desktop ntpd[3396]: frequency initialized -37.439 PPM from /var/lib/ntp/ntp.drift
May 24 13:32:46 bm-desktop gdm[2913]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
May 24 13:32:46 bm-desktop gdm[2913]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed 
May 24 13:32:46 bm-desktop console-kit-daemon[2662]: WARNING: Couldn't read /proc/2655/environ: Failed to open file '/proc/2655/environ': No such file or directory 
May 24 13:32:46 bm-desktop gdm[3413]: WARNING: session_child_run: gnome-session not found for a failsafe GNOME session, trying xterm 
May 24 13:32:46 bm-desktop gdm[3439]: Gtk-WARNING: Ignoring the separator setting 
May 24 13:32:50 bm-desktop gdm[3547]: Gtk-WARNING: Ignoring the separator setting 
May 24 13:35:55 bm-desktop kernel: [  246.544122] [drm] Num pipes: 1
May 24 13:35:55 bm-desktop kernel: [  246.629696] mtrr: MTRR 3 not used
May 24 13:35:56 bm-desktop acpid: client 2917[0:0] has disconnected 
May 24 13:35:56 bm-desktop acpid: client connected from 3646[0:0] 
May 24 13:35:56 bm-desktop kernel: [  248.090919] agpgart-via 0000:00:00.0: AGP 3.5 bridge
May 24 13:35:56 bm-desktop kernel: [  248.090944] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
May 24 13:35:56 bm-desktop kernel: [  248.091005] pci 0000:01:00.0: putting AGP V3 device into 8x mode
May 24 13:35:57 bm-desktop kernel: [  248.298501] [drm] Setting GART location based on new memory map
May 24 13:35:57 bm-desktop kernel: [  248.298512] [drm] Loading R300 Microcode
May 24 13:35:57 bm-desktop kernel: [  248.298549] [drm] Num pipes: 1
May 24 13:35:57 bm-desktop kernel: [  248.298557] [drm] writeback test succeeded in 1 usecs
May 24 13:36:12 bm-desktop lircd-0.8.4a[2375]: accepted new client on /dev/lircd
May 24 13:36:12 bm-desktop lircd-0.8.4a[2375]: initializing '/dev/lirc0'
May 24 13:36:12 bm-desktop lircd-0.8.4a[2375]: unable to open '/dev/lirc0'
May 24 13:36:12 bm-desktop lircd-0.8.4a[2375]: Failed to initialize hardware
May 24 13:36:38 bm-desktop lircd-0.8.4a[2375]: accepted new client on /dev/lircd
May 24 13:36:52 bm-desktop ntpd[3396]: synchronized to 91.189.94.4, stratum 2
May 24 13:36:52 bm-desktop ntpd[3396]: kernel time sync status change 0001
May 24 13:39:01 bm-desktop /USR/SBIN/CRON[3965]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 24 13:40:01 bm-desktop /USR/SBIN/CRON[4166]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May 24 13:44:49 bm-desktop lircd-0.8.4a[2375]: removed client
May 24 13:45:20 bm-desktop lircd-0.8.4a[2375]: accepted new client on /dev/lircd
May 24 13:47:18 bm-desktop lircd-0.8.4a[2375]: accepted new client on /dev/lircd
May 24 13:47:26 bm-desktop lircd-0.8.4a[2375]: removed client
May 24 13:47:45 bm-desktop lircd-0.8.4a[2375]: accepted new client on /dev/lircd
May 24 13:47:54 bm-desktop lircd-0.8.4a[2375]: removed client
May 24 13:48:02 bm-desktop lircd-0.8.4a[2375]: removed client
May 24 13:48:45 bm-desktop lircd-0.8.4a[2375]: accepted new client on /dev/lircd
May 24 13:48:46 bm-desktop lircd-0.8.4a[2375]: removed client
May 24 13:50:01 bm-desktop /USR/SBIN/CRON[4750]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May 24 13:54:06 bm-desktop ntpd[3396]: time reset -0.271764 s
May 24 13:55:46 bm-desktop dhclient: DHCPREQUEST of 192.168.1.11 on eth0 to 192.168.1.1 port 67
May 24 13:55:47 bm-desktop dhclient: DHCPACK of 192.168.1.11 from 192.168.1.1
May 24 13:55:47 bm-desktop NetworkManager: <info>  DHCP: device eth0 state changed bound -> renew 
May 24 13:55:47 bm-desktop NetworkManager: <info>    address 192.168.1.11 
May 24 13:55:47 bm-desktop NetworkManager: <info>    prefix 24 (255.255.255.0) 
May 24 13:55:47 bm-desktop NetworkManager: <info>    gateway 192.168.1.1 
May 24 13:55:47 bm-desktop NetworkManager: <info>    hostname 'bm-desktop' 
May 24 13:55:47 bm-desktop NetworkManager: <info>    nameserver '192.168.1.1' 
May 24 13:55:47 bm-desktop dhclient: bound to 192.168.1.11 -- renewal in 1702 seconds.

==> /var/log/Xorg.0.log <==
(II) RADEON(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: IBM  Model: 18bb  Serial#: 16843009
(II) RADEON(0): Year: 2003  Week: 19
(II) RADEON(0): EDID Version: 1.2
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 28  vert.: 21
(II) RADEON(0): Gamma: 2.77
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.312 greenY: 0.597
(II) RADEON(0): blueX: 0.150 blueY: 0.063   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 56.2 MHz   Image Size:  260 x 195 mm
(II) RADEON(0): h_active: 800  h_sync: 832  h_sync_end 896 h_blank_end 1048 h_border: 0
(II) RADEON(0): v_active: 600  v_sync: 601  v_sync_end 604 v_blanking: 631 v_border: 0
(II) RADEON(0): Monitor name: IBM 6331 E54
(II) RADEON(0): Ranges: V min: 50 V max: 120 Hz, H min: 30 H max: 69 kHz, PixClock max 110 MHz
(II) RADEON(0): Serial No: 23-DCFM5
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00244dbb1801010101
(II) RADEON(0): 	130d0102681c15b1ea0f99a0574f9826
(II) RADEON(0): 	10484ca4420031594559615981800101
(II) RADEON(0): 	010101010101f91520f830581f202040
(II) RADEON(0): 	130004c31000001e000000fc0049424d
(II) RADEON(0): 	2036333331204535340a000000fd0032
(II) RADEON(0): 	781e450b000a202020202020000000ff
(II) RADEON(0): 	0032332d4443464d350a20202020000f
(II) RADEON(0): EDID vendor "IBM", prod id 6331
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: f008  Serial#: 809715029
(II) RADEON(0): Year: 2008  Week: 29
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #4: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Serial No: G489H87G0CEU
(II) RADEON(0): Monitor name: DELL 1908WFP
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac08f055454330
(II) RADEON(0): 	1d12010380291a78eeee95a3544c9926
(II) RADEON(0): 	0f5054bfef809500714f8180950f8100
(II) RADEON(0): 	0101010101019a29a0d0518422305098
(II) RADEON(0): 	360098ff1000001c000000fd00384b1e
(II) RADEON(0): 	530e000a202020202020000000ff0047
(II) RADEON(0): 	34383948383747304345550a000000fc
(II) RADEON(0): 	0044454c4c20313930385746500a00f8
(II) RADEON(0): EDID vendor "DEL", prod id 61448
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0

==> /home/bm/.xsession-errors <==
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1a00009

==> lsb_release -a <==
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  1.7G  8.8G  16% /
tmpfs                 375M     0  375M   0% /lib/init/rw
varrun                375M  328K  375M   1% /var/run
varlock               375M     0  375M   0% /var/lock
udev                  375M  152K  375M   1% /dev
tmpfs                 375M     0  375M   0% /dev/shm
lrm                   375M  2.4M  373M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda6             175G  125M  174G   1% /var/lib

==> uname -a <==
Linux bm-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0d.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:0d.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)

==> lsusb <==
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04b3:310b IBM Corp. Red Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 2040:8400 Hauppauge 

==> lshw <==
computer
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 767MiB
     *-cpu
          product: AMD Athlon(tm) XP 2600+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.10.0
          size: 1950MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: VT8377 [KT400/KT600 AGP] Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 80
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: RV350 AP [Radeon 9600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=32 mingnt=8
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV350 AP [Radeon 9600] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=32 mingnt=8
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: d
             bus info: pci@0000:00:0d.0
             version: 62
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: d.2
             bus info: pci@0000:00:0d.2
             version: 65
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-storage
             description: RAID bus controller
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: storage bus_master cap_list
             configuration: driver=sata_via latency=32
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_via latency=32
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 13
             bus info: pci@0000:00:13.0
             logical name: eth0
             version: 10
             serial: [REMOVED]
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=[REMOVED] latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```



I seem to have some success using the newer version of the fw for my Hauppage Nova-TD-500 (HD dual Tuner) model 289 84109LF Rev D1F4: 

```
bm@bm-desktop:~$ dmesg | grep -i dvb
[    6.990873] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[    6.990880] usb 1-1: firmware: requesting dvb-usb-dib0700-1.20.fw
[    7.236031] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[    7.992036] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[    7.992233] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    7.992788] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[    8.220872] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[    8.399945] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    8.400450] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[    8.546252] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[    8.724080] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[    8.724253] usbcore: registered new interface driver dvb_usb_dib0700
bm@bm-desktop:~$ 
```

---


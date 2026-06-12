---
title: "New motherboard in B/E now no live TV.... (broken database?)"
date: 2011-03-22
forum: Mythbuntu
---

### Post by bance on 2011-03-22
Hi all,

Was having a few problems here and there with my old set up and decided to upgrade the back-end, this was only to be a hardware upgrade:- relegate one mobo/cpu to SBE and introduce slightly better mobo/cpu as MBE.

 Anyway foolishly I didn't have static IP's set up and for a short time the machines were running with different IP's than were originally set.

Now I can't get live TV......  I've been through set-up several times checked and re-set IP's in the relevant files:-

[LIST]
[*] /mythtv/.mythtv/mysql.txt
[*]/home/user/.mtyhtv/msql.txt
[*]/etc/mythtv/config.xml
[*]and so on
[/LIST]
I deleted all tuners/sources added them back and re-set in-put connections and rescanned, but no joy!

Recordings are working, and can be watched, and everything else seems to be OK.

I don't think I've made a configuration error, maybe the DB is confused?

I'm not that clever with mysql but am willing to try if any one has any ideas!

My set up:-

MBE

intel E5400 dual core CPU
2 Gb RAM
Haupage hvr4000 dvbS/S2 dvbT dual tuner (can't get the dvbT working am working on it)
Compro dvbS-350
40 gb HDD with /, home,DB etc
2X1.5 tb HDD's for storage
IP 192.168.10.2

SBE

intel celeron dual core cpu
1Gb RAM
Peak K-World dual dvbT tuner
Avermedia Super007 dvbT tuner
6.4 gb HDD with /, home, etc
20 gb HDD for storage
IP 192.168.10.3

4 various FE machines


Frontend log :-

```
<snip>
2011-03-22 21:15:45.351 Connected to database 'mythconverg' at host: 192.168.10.2
2011-03-22 21:15:54.254 ProgramInfo(): Updated pathname '':'' -> '10211_20110322170000.mpg'
2011-03-22 21:16:01.691 TV: Attempting to change from None to WatchingLiveTV
2011-03-22 21:16:01.692 MythContext: Connecting to backend server: 192.168.10.3:0 (try 1 of 1)
2011-03-22 21:16:01.692 Connection to master server timed out.
            Either the server is down or the master server settings
            in mythtv-settings does not contain the proper IP address

2011-03-22 21:16:01.692 RemoteEncoder::Setup(): Failed to connect to backend
2011-03-22 21:16:01.692 Spawning LiveTV Recorder -- begin
2011-03-22 21:16:01.692 MythContext: Connecting to backend server: 192.168.10.3:0 (try 1 of 1)
2011-03-22 21:16:01.693 Connection to master server timed out.
            Either the server is down or the master server settings
            in mythtv-settings does not contain the proper IP address

2011-03-22 21:16:01.693 RemoteEncoder::Setup(): Failed to connect to backend
2011-03-22 21:16:01.693 RemoteEncoder::SendReceiveStringList(): Failed to reconnect with backend.
2011-03-22 21:16:01.693 Spawning LiveTV Recorder -- end
2011-03-22 21:16:01.700 GetEntryAt(-1) failed.
2011-03-22 21:16:01.712 EntryToProgram(0@Thu Jan 1 01:00:00 1970) failed to get pginfo
2011-03-22 21:16:01.712 TV Error: HandleStateChange(): LiveTV not successfully started
2011-03-22 21:16:01.712 We have a RingBuffer
2011-03-22 21:16:01.766 TV Error: LiveTV not successfully started
2011-03-22 21:16:01.801 ScreenSaverX11Private: DPMS Deactivated 1
2011-03-22 21:16:01.805 ScreenSaverX11Private: DPMS Reactivated 1
2011-03-22 21:16:19.906 AudioPulseUtil: Resume Success
2011-03-22 21:16:19.906 Deleting UPnP client...
```MBE log:-

```
2011-03-22 21:13:30.520 adding: stephen-desktop as a client (events: 1)
2011-03-22 21:14:25.479 mythbackend version: branches/release-0-23-fixes [26863] www.mythtv.org
2011-03-22 21:14:25.480 Using runtime prefix = /usr
2011-03-22 21:14:25.504 Using configuration directory = /home/mythtv/.mythtv
2011-03-22 21:14:25.515 Empty LocalHostName.
2011-03-22 21:14:25.526 Using localhost value of myth-backend
2011-03-22 21:14:25.538 Testing network connectivity to '192.168.10.2'
2011-03-22 21:14:25.580 New DB connection, total: 1
2011-03-22 21:14:25.603 Connected to database 'mythconverg' at host: 192.168.10.2
2011-03-22 21:14:25.615 Closing DB connection named 'DBManager0'
2011-03-22 21:14:25.627 Connected to database 'mythconverg' at host: 192.168.10.2
2011-03-22 21:14:25.641 Current MythTV Schema Version (DBSchemaVer): 1254
2011-03-22 21:14:25.650 MythBackend: Starting up as the master server.
2011-03-22 21:14:25.665 New DB connection, total: 2
2011-03-22 21:14:25.674 Connected to database 'mythconverg' at host: 192.168.10.2
2011-03-22 21:14:25.683 mythbackend: MythBackend started as master server
2011-03-22 21:14:25.868 New DB connection, total: 3
2011-03-22 21:14:25.948 Connected to database 'mythconverg' at host: 192.168.10.2
2011-03-22 21:14:25.971 New DB connection, total: 4
2011-03-22 21:14:25.982 Connected to database 'mythconverg' at host: 192.168.10.2
2011-03-22 21:14:27.268 DVBChan(2:/dev/dvb/adapter1/frontend0) Warning: Your frequency setting (10714000) is out of range. (min/max:950000/2150000)
2011-03-22 21:14:28.878 DVBChan(6:/dev/dvb/adapter0/frontend0) Warning: Your frequency setting (10758500) is out of range. (min/max:950000/2150000)
2011-03-22 21:14:28.945 New DB scheduler connection
2011-03-22 21:14:28.956 Connected to database 'mythconverg' at host: 192.168.10.2
2011-03-22 21:14:29.020 Enabling Upnpmedia rebuild thread.
2011-03-22 21:14:30.248 Main::Registering HttpStatus Extension
2011-03-22 21:14:30.254 Enabled verbose msgs:  important general
2011-03-22 21:14:30.268 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-03-22 21:14:30.805 adding: slave-backend as a slave backend server
2011-03-22 21:14:30.811 adding 3/More4/"Come Dine with Me" as recording
2011-03-22 21:14:33.974 Reschedule requested for id -1.
2011-03-22 21:14:34.477 Scheduled 20 items in 0.5 = 0.03 match + 0.46 place
2011-03-22 21:14:34.497 scheduler: Scheduled items: Scheduled 20 items in 0.5 = 0.03 match + 0.46 place
2011-03-22 21:14:34.509 Seem to be woken up by USER
2011-03-22 21:14:36.835 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-03-22 21:14:38.988 mythbackend: Running housekeeping thread
2011-03-22 21:14:39.047 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2011-03-22 21:14:39.058 UPnpMedia: BuildMediaMap Done. Found 3 objects
2011-03-22 21:14:44.648 Slave backend: slave-backend no longer connected
2011-03-22 21:14:44.690 setting 3/More4/"Come Dine with Me" as aborted
2011-03-22 21:14:44.716 Reschedule requested for id 0.
2011-03-22 21:14:45.189 Scheduled 19 items in 0.5 = 0.01 match + 0.45 place
2011-03-22 21:14:45.207 scheduler: Scheduled items: Scheduled 19 items in 0.5 = 0.01 match + 0.45 place
2011-03-22 21:15:25.053 MainServer::ANN Monitor
2011-03-22 21:15:25.071 adding: tzcheck as a client (events: 0)
2011-03-22 21:15:28.116 Program #1025 not found in PAT!
Program Association Table
 PSIP tableID(0x0) length(69) extension(0x968)
      version(25) current(1) section(0) last_section(0)
         tsid: 2408
 programCount: 15
  program number     0 has PID 0x  10   data  0x 0 0x 0 0xe0 0x10
  program number  4826 has PID 0x 137   data  0x12 0xda 0xe1 0x37
  program number  4827 has PID 0x 102   data  0x12 0xdb 0xe1 0x 2
  program number  4828 has PID 0x 105   data  0x12 0xdc 0xe1 0x 5
  program number  4829 has PID 0x 112   data  0x12 0xdd 0xe1 0x12
  program number  4830 has PID 0x 114   data  0x12 0xde 0xe1 0x14
  program number  4926 has PID 0x 115   data  0x13 0x3e 0xe1 0x15
  program number  5554 has PID 0x 10c   data  0x15 0xb2 0xe1 0x c
  program number  4655 has PID 0x 103   data  0x12 0x2f 0xe1 0x 3
  program number  4653 has PID 0x 104   data  0x12 0x2d 0xe1 0x 4
  program number  5003 has PID 0x 10a   data  0x13 0x8b 0xe1 0x a
  program number  6030 has PID 0x 109   data  0x17 0x8e 0xe1 0x 9
  program number  3894 has PID 0x 106   data  0x f 0x36 0xe1 0x 6
  program number  3895 has PID 0x 107   data  0x f 0x37 0xe1 0x 7
  program number  8072 has PID 0x 113   data  0x1f 0x88 0xe1 0x13

2011-03-22 21:15:28.714 ProcessPAT: Program not found in PAT. 
            Rescan your transports.
2011-03-22 21:15:28.723 Desired program #1025 not found in PAT.
            Can Not create single program PAT.
2011-03-22 21:15:36.293 MainServer::ANN Monitor
2011-03-22 21:15:36.314 adding: stephen-desktop as a client (events: 0)
2011-03-22 21:15:36.327 MainServer::ANN Monitor
2011-03-22 21:15:36.336 adding: stephen-desktop as a client (events: 1)
2011-03-22 21:15:40.265 adding: slave-backend as a slave backend server
2011-03-22 21:15:40.277 Reschedule requested for id 0.
2011-03-22 21:15:40.712 Scheduled 19 items in 0.4 = 0.01 match + 0.41 place
2011-03-22 21:15:40.734 scheduler: Scheduled items: Scheduled 19 items in 0.4 = 0.01 match + 0.41 place
2011-03-22 21:15:46.291 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-03-22 21:15:48.991 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-03-22 21:15:49.017 Expiring 78 MBytes for 11261 @ Sat Feb 26 18:45:00 2011 => Inspector Morse "Second Time Around"
2011-03-22 21:15:49.024 autoexpire: Expiring Program: Expiring 78 MBytes for 11261 @ Sat Feb 26 18:45:00 2011 => Inspector Morse "Second Time Around"
2011-03-22 21:15:49.034 Expiring 762 MBytes for 2004 @ Sat Dec 18 18:05:00 2010 => Come Dine with Me
2011-03-22 21:15:49.035 ProgramInfo(): Updated pathname '':'' -> '11261_20110226185959.mpg'
2011-03-22 21:15:49.046 autoexpire: Expiring Program: Expiring 762 MBytes for 2004 @ Sat Dec 18 18:05:00 2010 => Come Dine with Me
2011-03-22 21:15:49.140 ProgramInfo(): Updated pathname '':'' -> '2004_20101218180500.mpg'
2011-03-22 21:15:49.147 ProgramInfo(2004_20101218180500.mpg), Error: GetPlaybackURL: '2004_20101218180500.mpg' should be local, but it can not be found.
2011-03-22 21:15:49.156 ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/myth-backend/2004_20101218180500.mpg. File doesn't exist.  Database metadata will not be removed.
2011-03-22 21:15:49.170 mythbackend: Delete Recording: File GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/myth-backend/2004_20101218180500.mpg does not exist for chanid 2004 at Sat Dec 18 18:05:00 2010 when trying to delete recording.
2011-03-22 21:17:01.762 MainServer::ANN Monitor
```SBE log:-

```
2011-03-22 20:21:30.495 ProgramInfo(2010_20110322165700.mpg), Error: GetPlaybackURL: '2010_20110322165700.mpg' should be local, but it can not be found.
2011-03-22 20:21:30.534 ProgramInfo(2014_20110322185000.mpg), Error: GetPlaybackURL: '2014_20110322185000.mpg' should be local, but it can not be found.
2011-03-22 20:21:31.466 ProgramInfo(2014_20110322185000.mpg), Error: GetPlaybackURL: '2014_20110322185000.mpg' should be local, but it can not be found.
2011-03-22 20:21:31.493 ProgramInfo(2010_20110322165700.mpg), Error: GetPlaybackURL: '2010_20110322165700.mpg' should be local, but it can not be found.
2011-03-22 20:21:31.932 ProgramInfo(2014_20110322185000.mpg), Error: GetPlaybackURL: '2014_20110322185000.mpg' should be local, but it can not be found.
2011-03-22 20:21:31.959 ProgramInfo(2010_20110322165700.mpg), Error: GetPlaybackURL: '2010_20110322165700.mpg' should be local, but it can not be found.
2011-03-22 20:21:40.252 ProgramInfo(2014_20110322185000.mpg), Error: GetPlaybackURL: '2014_20110322185000.mpg' should be local, but it can not be found.
2011-03-22 20:21:48.794 ProgramInfo(2010_20110322165700.mpg), Error: GetPlaybackURL: '2010_20110322165700.mpg' should be local, but it can not be found.
2011-03-22 20:21:54.828 ProgramInfo(2014_20110322185000.mpg), Error: GetPlaybackURL: '2014_20110322185000.mpg' should be local, but it can not be found.
2011-03-22 21:14:17.858 Connecting to master server: 192.168.10.2:6543
2011-03-22 21:14:17.885 Connection to master server timed out.
2011-03-22 21:14:18.896 Connecting to master server: 192.168.10.2:6543
2011-03-22 21:14:18.907 Connection to master server timed out.
2011-03-22 21:14:19.918 Connecting to master server: 192.168.10.2:6543
2011-03-22 21:14:19.940 Connection to master server timed out.
2011-03-22 21:14:20.951 Connecting to master server: 192.168.10.2:6543
2011-03-22 21:14:20.962 Connection to master server timed out.
2011-03-22 21:14:21.973 Connecting to master server: 192.168.10.2:6543
2011-03-22 21:14:21.985 Connection to master server timed out.
2011-03-22 21:14:22.996 Connecting to master server: 192.168.10.2:6543
2011-03-22 21:14:23.030 Connection to master server timed out.
2011-03-22 21:14:24.062 Connecting to master server: 192.168.10.2:6543
2011-03-22 21:14:24.080 Connection to master server timed out.
2011-03-22 21:14:25.120 Connecting to master server: 192.168.10.2:6543
2011-03-22 21:14:25.152 Connection to master server timed out.
2011-03-22 21:14:26.162 Connecting to master server: 192.168.10.2:6543
2011-03-22 21:14:26.174 Connection to master server timed out.
2011-03-22 21:14:27.184 Connecting to master server: 192.168.10.2:6543
2011-03-22 21:14:27.196 Connection to master server timed out.
2011-03-22 21:14:28.207 Connecting to master server: 192.168.10.2:6543
2011-03-22 21:14:28.218 Connection to master server timed out.
2011-03-22 21:14:29.229 Connecting to master server: 192.168.10.2:6543
2011-03-22 21:14:29.298 Connection to master server timed out.
2011-03-22 21:14:30.307 Connecting to master server: 192.168.10.2:6543
2011-03-22 21:14:30.329 Connection to master server timed out.
2011-03-22 21:14:31.340 Connecting to master server: 192.168.10.2:6543
2011-03-22 21:14:31.351 Connection to master server timed out.
2011-03-22 21:14:32.362 Connecting to master server: 192.168.10.2:6543
2011-03-22 21:14:32.373 Connection to master server timed out.
2011-03-22 21:14:33.384 Connecting to master server: 192.168.10.2:6543
2011-03-22 21:14:33.396 Connection to master server timed out.
2011-03-22 21:14:34.407 Connecting to master server: 192.168.10.2:6543
2011-03-22 21:14:34.418 Connected successfully
2011-03-22 21:15:18.265 mythbackend version: branches/release-0-23-fixes [26863] www.mythtv.org
2011-03-22 21:15:18.268 Using runtime prefix = /usr
2011-03-22 21:15:18.294 Using configuration directory = /home/mythtv/.mythtv
2011-03-22 21:15:18.306 Empty LocalHostName.
2011-03-22 21:15:18.316 Using localhost value of slave-backend
2011-03-22 21:15:18.374 New DB connection, total: 1
2011-03-22 21:15:23.487 Connected to database 'mythconverg' at host: 192.168.10.2
2011-03-22 21:15:23.505 Closing DB connection named 'DBManager0'
2011-03-22 21:15:28.618 Connected to database 'mythconverg' at host: 192.168.10.2
2011-03-22 21:15:28.671 Using protocol version 23056
2011-03-22 21:15:28.725 Backend is running in Europe/London time zone.
2011-03-22 21:15:28.755 Current MythTV Schema Version (DBSchemaVer): 1254
2011-03-22 21:15:28.774 MythBackend: Running as a slave backend.
2011-03-22 21:15:28.806 New DB connection, total: 2
2011-03-22 21:15:33.915 Connected to database 'mythconverg' at host: 192.168.10.2
2011-03-22 21:15:33.943 mythbackend: MythBackend started as a slave backend
2011-03-22 21:15:34.632 New DB connection, total: 3
2011-03-22 21:15:39.926 Connected to database 'mythconverg' at host: 192.168.10.2
2011-03-22 21:15:42.857 Main::Registering HttpStatus Extension
2011-03-22 21:15:42.859 Enabled verbose msgs:  important general
2011-03-22 21:15:43.887 Connecting to master server: 192.168.10.2:6543
2011-03-22 21:15:43.893 Connected successfully
2011-03-22 21:15:52.212 mythbackend: Running housekeeping thread
2011-03-22 21:15:52.746 ProgramInfo(11261_20110226185959.mpg), Error: GetPlaybackURL: '11261_20110226185959.mpg' should be local, but it can not be found.
2011-03-22 21:15:52.748 ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/slave-backend/11261_20110226185959.mpg. File doesn't exist.  Database metadata will not be removed.
2011-03-22 21:15:52.771 mythbackend: Delete Recording: File GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/slave-backend/11261_20110226185959.mpg does not exist for chanid 11261 at Sat Feb 26 18:59:59 2011 when trying to delete recording.
2011-03-22 21:20:54.253 mythbackend: Running housekeeping thread
2011-03-22 21:28:15.395 New DB connection, total: 4
2011-03-22 21:28:20.523 Connected to database 'mythconverg' at host: 192.168.10.2
```
The SBE actually holds the tuner ( the last one set up) for live TV.... I hope that's not all it is!

TIA Steve.

---


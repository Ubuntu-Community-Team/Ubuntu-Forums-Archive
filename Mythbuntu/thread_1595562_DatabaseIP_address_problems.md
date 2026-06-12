---
title: "Database/IP address problems"
date: 2010-10-13
forum: Mythbuntu
---

### Post by bance on 2010-10-13
I like to fiddle with my set-up:oops:

Anyway, I had a couple of blank recordings, and I thought there may have been an issue with one of my tuner cards. (Kworld plusTV dual DVB-T PCI). So I deleted all capture cards/video sources, and added them back, re-scanned etc. As far as I recall I didn't change anything else.

Now when I try to watch live TV, I get the "error mythtv is using all input devices but there are no active recordings" message. I understand from other posts that this is caused by incorrect setting of IP address for the B/E. I've been through set-up several times, using actual IP address/local-host/host-name. I've checked the conf file in /home/stephen/.mythtv and all seem to match.

I thought I'd see if I could watch a recorded show, but at the watch recordings screen, nothing came up in the box that contains the recordings, and beneath was "%TITLE%DESCRIPTION% or so.

Maybe it's a database error? I used PHPMyadmin to repair tables. 
Not sure if it did anything, because nothing changed.

Any help would be greatly appreciated!

I am using Mythbuntu 10.04 0.23 fixes

Here are some logs:- Backend


```
stephen@master-backend:~$ tail -250 /var/log/mythtv/mythbackend.log

2010-10-12 15:57:20.847 ProcessPAT: Program not found in PAT. 
	
Rescan your transports.

2010-10-12 15:57:20.856 Desired program #4615 not found in PAT.
Can Not create single program PAT.

2010-10-12 15:58:08.558 Reschedule requested for id -1.

2010-10-12 15:58:08.929 Scheduled 36 items in 0.3 = 0.03 match + 0.29 place

2010-10-12 16:01:08.785 Reschedule requested for id -1.

2010-10-12 16:01:09.131 Scheduled 36 items in 0.3 = 0.03 match + 0.27 place

2010-10-12 16:01:36.827 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:

2010-10-12 16:01:36.871 UPnpMedia: BuildMediaMap Done. Found 3 objects

2010-10-12 16:02:31.900 ERROR: Master backend tried to connect back to itself!

2010-10-12 16:02:41.824 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

2010-10-12 16:04:52.398 Reschedule requested for id -1.

2010-10-12 16:04:52.730 Scheduled 37 items in 0.3 = 0.03 match + 0.25 place

2010-10-12 16:07:41.365 Reschedule requested for id -1.

2010-10-12 16:07:43.686 Scheduled 37 items in 1.9 = 0.12 match + 1.81 place

2010-10-12 16:07:43.955 ERROR: Master backend tried to connect back to itself!

2010-10-12 16:07:44.462 Program #1016 not found in PAT!

Program Association Table
 
PSIP tableID(0x0) length(65) extension(0x965)
      
version(28) current(1) section(0) last_section(0)
         
tsid: 2405
 programCount: 14
  program number     
0 has PID 0x  10   data  0x 0 0x 0 0xe0 0x10
  
program number 50400 has PID 0x 101   
data  0xc4 0xe0 0xe1 0x 1
program number 50405 has PID 0x 102   
data  0xc4 0xe5 0xe1 0x 2
  
program number 50410 has PID 0x 103   
data  0xc4 0xea 0xe1 0x 3
  
program number 50411 has PID 0x 106   
data  0xc4 0xeb 0xe1 0x 6
  
program number 50415 has PID 0x 10d   
data  0xc4 0xef 0xe1 0x d
  
program number 50425 has PID 0x 104   
data  0xc4 0xf9 0xe1 0x 4
  
program number 50445 has PID 0x 108   
data  0xc5 0x d 0xe1 0x 8
  
program number 50446 has PID 0x 109   
data  0xc5 0x e 0xe1 0x 9
  
program number 50460 has PID 0x 100   
data  0xc5 0x1c 0xe1 0x 0
  
program number 50465 has PID 0x 105   
data  0xc5 0x21 0xe1 0x 5
  
program number 50470 has PID 0x 107   
data  0xc5 0x26 0xe1 0x 7
  
program number 50475 has PID 0x 10f   
data  0xc5 0x2b 0xe1 0x f
program number 50480 has PID 0x 10e   
data  0xc5 0x30 0xe1 0x e


2010-10-12 16:07:45.026 ProcessPAT: Program not found in PAT. 
			
Rescan your transports.

2010-10-12 16:07:45.038 Desired program #1016 not found in PAT.
			
Can Not create single program PAT.

2010-10-12 16:09:20.046 mythbackend version: branches/release-0-23-fixes [s25362] www.mythtv.org
2010-10-12 16:09:20.054 Using runtime prefix = /usr

2010-10-12 16:09:20.066 Using configuration directory = /home/mythtv/.mythtv

2010-10-12 16:09:20.078 Empty LocalHostName.

2010-10-12 16:09:20.088 Using localhost value of master-backend

2010-10-12 16:09:20.141 New DB connection, total: 1

2010-10-12 16:09:20.166 Connected to database 'mythconverg' at host: master-backend

2010-10-12 16:09:20.177 Closing DB connection named 'DBManager0'

2010-10-12 16:09:20.191 Connected to database 'mythconverg' at host: master-backend

2010-10-12 16:09:20.235 Current MythTV Schema Version (DBSchemaVer): 1254

2010-10-12 16:09:20.267 MythBackend: Starting up as the master server.

2010-10-12 16:09:20.312 New DB connection, total: 
2
2010-10-12 16:09:20.323 Connected to database 'mythconverg' at host: master-backend

2010-10-12 16:09:20.335 MythBackend, Error: No valid capture cards are defined in the database.
			
Perhaps you should re-read the installation instructions?

2010-10-12 16:09:20.367 New DB connection, total: 3

2010-10-12 16:09:20.381 Connected to database 'mythconverg' at host: master-backend
2010-10-12 16:09:20.470 Enabling Upnpmedia rebuild thread.

2010-10-12 16:09:21.688 Main::Registering HttpStatus Extension

2010-10-12 16:09:21.697 Enabled verbose msgs:  important general

2010-10-12 16:09:21.715 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

2010-10-12 16:09:30.493 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:

2010-10-12 16:09:30.517 UPnpMedia: BuildMediaMap Done. Found 3 objects

2010-10-12 16:10:40.366 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

2010-10-12 16:45:24.193 mythbackend version: branches/release-0-23-fixes [s25362] www.mythtv.org

2010-10-12 16:45:24.195 Using runtime prefix = /usr

2010-10-12 16:45:24.210 Using configuration directory = /home/mythtv/.mythtv

2010-10-12 16:45:24.220 Empty LocalHostName.

2010-10-12 16:45:24.230 Using localhost value of master-backend

2010-10-12 16:45:24.279 New DB connection, total: 1

2010-10-12 16:45:24.378 Connected to database 'mythconverg' at host: master-backend

2010-10-12 16:45:24.397 Closing DB connection named 'DBManager0'

2010-10-12 16:45:24.410 Connected to database 'mythconverg' at host: master-backend

2010-10-12 16:45:24.443 Current MythTV Schema Version (DBSchemaVer): 1254

2010-10-12 16:45:24.465 MythBackend: Starting up as the master server.

2010-10-12 16:45:24.508 New DB connection, total: 2

2010-10-12 16:45:24.520 Connected to database 'mythconverg' at host: master-backend
2010-10-12 16:45:24.779 New DB connection, total: 3

2010-10-12 16:45:24.787 Connected to database 'mythconverg' at host: master-backend

2010-10-12 16:45:24.798 New DB connection, total: 4

2010-10-12 16:45:24.809 Connected to database 'mythconverg' at host: master-backend

2010-10-12 16:45:26.051 DVBChan(2:/dev/dvb/adapter2/frontend0) Warning: Your frequency setting (10773250) is out of range. (min/max:950000/2150000)

2010-10-12 16:45:41.229 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:45:46.329 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:45:51.437 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:45:56.541 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:46:01.645 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:46:06.769 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:46:11.865 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:46:16.969 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:46:22.085 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:46:27.189 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:46:32.297 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:46:37.413 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:46:42.517 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:46:47.621 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:46:52.749 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:46:57.853 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:47:02.969 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:47:08.089 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
		
eno: Device or resource busy (16)

2010-10-12 16:47:13.189 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:47:18.293 DVBChan(3:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:47:18.326 DVBChan(3:/dev/dvb/adapter2/frontend1) 
Error: Failed to open DVB frontend device due to fatal error or too many 

2010-10-12 16:47:33.481 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:47:38.613 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:47:43.729 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:47:48.857 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:47:53.973 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:47:59.125 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:48:04.225 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:48:09.329 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:48:14.433 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:48:19.541 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:48:24.645 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:48:29.761 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:48:34.865 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:48:39.969 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:48:45.073 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:48:50.181 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:48:55.285 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:49:00.389 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:49:05.493 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:49:10.597 DVBChan(4:/dev/dvb/adapter2/frontend1) Warning: Opening DVB frontend device failed.
			
eno: Device or resource busy (16)

2010-10-12 16:49:10.615 DVBChan(4:/dev/dvb/adapter2/frontend1) 
Error: Failed to open DVB frontend device due to fatal error or too many attempts.

2010-10-12 16:49:11.335 New DB scheduler connection

2010-10-12 16:49:11.349 Connected to database 'mythconverg' at host: master-backend

2010-10-12 16:49:11.443 Enabling Upnpmedia rebuild thread.

2010-10-12 16:49:12.783 Main::Registering HttpStatus Extension

2010-10-12 16:49:12.790 Enabled verbose msgs:  important general

2010-10-12 16:49:12.808 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

2010-10-12 16:49:14.445 Reschedule requested for id -1.

2010-10-12 16:49:14.652 Scheduled 0 items in 0.2 = 0.02 match + 0.14 

2010-10-12 16:49:14.676 Seem to be woken up by user

2010-10-12 16:49:21.461 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:

2010-10-12 16:49:21.488 UPnpMedia: BuildMediaMap Done. Found 3 objects

2010-10-12 16:50:31.377 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

2010-10-12 16:52:27.722 Reschedule requested for id -1.

2010-10-12 16:52:28.404 Scheduled 1 items in 0.4 = 0.08 match + 0.27 place

2010-10-12 16:52:30.676 ERROR: Master backend tried to connect back to itself!

2010-10-12 16:52:30.688 ERROR: Master backend tried to connect back to itself!

2010-10-12 16:52:31.283 Program #1014 not found in PAT!
Program Association Table
 
PSIP tableID(0x0) length(57) extension(0x909)
      
version(4) current(1) section(0) last_section(0)
         
tsid: 2313
 programCount: 12
  
program number 53200 has PID 0x 101   data  0xcf 0xd0 0xe1 0x 1
  
program number 53205 has PID 0x 108   data  0xcf 0xd5 0xe1 0x 8
  
program number 53230 has PID 0x 10a   data  0xcf 0xee 0xe1 0x a
  
program number 53255 has PID 0x 110   data  0xd0 0x 7 0xe1 0x10
  
program number 53260 has PID 0x 10d   data  0xd0 0x c 0xe1 0x d
  
program number 53270 has PID 0x 107   data  0xd0 0x16 0xe1 0x 7
  
program number 53275 has PID 0x 116   data  0xd0 0x1b 0xe1 0x16
  
program number 53280 has PID 0x 10b   data  0xd0 0x20 0xe1 0x b
  
program number 53285 has PID 0x 10c   data  0xd0 0x25 0xe1 0x c
  
program number 53290 has PID 0x 109   data  0xd0 0x2a 0xe1 0x 9
  
program number 53295 has PID 0x 103   data  0xd0 0x2f 0xe1 0x 3
  
program number 53297 has PID 0x 10f   data  0xd0 0x31 0xe1 0x f


2010-10-12 16:52:31.813 ProcessPAT: Program not found in PAT. 
			
Rescan your transports.

2010-10-12 16:52:31.864 Desired program #1014 not found in PAT.
			
Can Not create single program PAT.

2010-10-12 16:57:45.213 ERROR: Master backend tried to connect back to itself!

2010-10-12 16:57:45.230 ERROR: Master backend tried to connect back to itself!

2010-10-12 16:58:20.309 Reschedule requested for id -1.

2010-10-12 16:58:26.421 Scheduled 27 items in 6.0 = 4.23 match + 1.82 place

2010-10-12 17:02:54.729 Reschedule requested for id -1.

2010-10-12 17:02:57.305 Scheduled 27 items in 1.9 = 0.11 match + 1.79 place

2010-10-12 17:02:57.536 ERROR: Master backend tried to connect back to itself!

2010-10-12 17:02:57.539 ERROR: Master backend tried to connect back to itself!

2010-10-12 17:05:31.586 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

2010-10-12 17:06:18.225 Reschedule requested for id -1.

2010-10-12 17:06:18.572 Scheduled 27 items in 0.3 = 0.04 match + 0.26 place

2010-10-12 17:08:09.033 ERROR: Master backend tried to connect back to itself!

2010-10-12 17:08:09.049 ERROR: Master backend tried to connect back to itself!

2010-10-12 17:08:09.454 Program #5044 not found in PAT!

Program Association Table
 PSIP tableID(0x0) length(77) extension(0x961)
      
version(1) current(1) section(0) last_section(0)
         
tsid: 2401
 programCount: 17
  
program number     0 has PID 0x  10   data  0x 0 0x 0 0xe0 0x10
  
program number  4327 has PID 0x 102   data  0x10 0xe7 0xe1 0x 2
  
program number  4826 has PID 0x 103   data  0x12 0xda 0xe1 0x 3
  
program number  4827 has PID 0x 104   data  0x12 0xdb 0xe1 0x 4
  
program number  4828 has PID 0x 105   data  0x12 0xdc 0xe1 0x 5
  
program number  4829 has PID 0x 106   data  0x12 0xdd 0xe1 0x 6
  
program number  4830 has PID 0x 107   data  0x12 0xde 0xe1 0x 7
  
program number  4889 has PID 0x  56   data  0x13 0x19 0xe0 0x56
  
program number  4890 has PID 0x  56   data  0x13 0x1a 0xe0 0x56
  
program number  4926 has PID 0x 108   data  0x13 0x3e 0xe1 0x 8
  
program number  4927 has PID 0x 109   data  0x13 0x3f 0xe1 0x 9
  
program number  4928 has PID 0x 10a   data  0x13 0x40 0xe1 0x a
  
program number  4929 has PID 0x 10b   data  0x13 0x41 0xe1 0x b
  
program number  5554 has PID 0x 10c   data  0x15 0xb2 0xe1 0x c
  
program number  5555 has PID 0x 10f   data  0x15 0xb3 0xe1 0x f
  
program number  8012 has PID 0x 111   data  0x1f 0x4c 0xe1 0x11
  
program number  8088 has PID 0x 110   data  0x1f 0x98 0xe1 0x10


2010-10-12 17:08:09.909 ProcessPAT: Program not found in PAT. 
			
Rescan your transports.

2010-10-12 17:08:09.914 Desired program #5044 not found in PAT.
			
Can Not create single program PAT.

2010-10-12 17:11:20.556 Reschedule requested for id -1.

2010-10-12 17:11:20.878 Scheduled 27 items in 0.3 = 0.03 match + 0.25 place

2010-10-12 17:13:20.533 ERROR: Master backend tried to connect back to itself!


```



Frontend log:-


```
[CODE]stephen@master-backend:~$ tail -50 /var/log/mythtv/mythfrontend.log
			
or has deadlocked in due to bugs or hardware failure.

2010-10-12 16:45:47.272 MythContext: Connecting to backend server: 192.168.10.2:3306 (try 1 of 1)

2010-10-12 16:45:47.274 MythSocket(9e92aa0:37): Protocol error: 'r' is not a valid size prefix. 110 bytes pending.

2010-10-12 16:45:47.274 Protocol version check failure.
			
The response to MYTH_PROTO_VERSION was empty.
			
This happens when the backend is too busy to respond,
			
or has deadlocked in due to bugs or hardware failure.

2010-10-12 16:45:49.367 MythContext: Connecting to backend server: 192.168.10.2:3306 (try 1 of 1)

2010-10-12 16:45:49.369 MythSocket(9a746e0:33): Protocol error: 'r' is not a valid size prefix. 110 bytes pending.

2010-10-12 16:45:49.369 Protocol version check failure.
			
The response to MYTH_PROTO_VERSION was empty.
			
This happens when the backend is too busy to respond,
			
or has deadlocked in due to bugs or hardware failure.

2010-10-12 16:45:52.274 MythContext: Connecting to backend server: 192.168.10.2:3306 (try 1 of 1)

2010-10-12 16:45:52.276 MythSocket(9a695c0:33): Protocol error: 'r' is not a valid size prefix. 110 bytes pending.

2010-10-12 16:45:52.276 Protocol version check failure.
			
The response to MYTH_PROTO_VERSION was empty.
			
This happens when the backend is too busy to respond,
			
or has deadlocked in due to bugs or hardware failure.

2010-10-12 16:45:52.620 New DB connection, total: 2

2010-10-12 16:45:52.622 Connected to database 'mythconverg' at host: master-backend

2010-10-12 16:45:52.627 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/recordings-ui.xml

2010-10-12 16:45:52.691 MythContext: Connecting to backend server: 192.168.10.2:3306 (try 1 of 1)

2010-10-12 16:45:52.692 MythSocket(9e92500:40): Protocol error: 'r' is not a valid size prefix. 110 bytes pending.

2010-10-12 16:45:52.693 Protocol version check failure.
			
The response to MYTH_PROTO_VERSION was empty.
			
This happens when the backend is too busy to respond,
			
or has deadlocked in due to bugs or hardware failure.

2010-10-12 16:45:52.723 PlaybackBox Error: SortedList is Empty

2010-10-12 16:45:52.724 MythContext: Connecting to backend server: 192.168.10.2:3306 (try 1 of 1)

2010-10-12 16:45:52.725 MythSocket(a0c5428:40): Protocol error: 'r' is not a valid size prefix. 110 bytes pending.

2010-10-12 16:45:52.725 Protocol version check failure.
			
The response to MYTH_PROTO_VERSION was empty.
			
This happens when the backend is too busy to respond,
			
or has deadlocked in due to bugs or hardware failure.

2010-10-12 16:45:52.820 PlaybackBox Error: SortedList is Empty

2010-10-12 16:45:57.277 MythContext: Connecting to backend server: 192.168.10.2:3306 (try 1 of 1)

2010-10-12 16:45:57.278 MythSocket(a0bf2b0:38): Protocol error: 'r' is not a valid size prefix. 110 bytes pending.

2010-10-12 16:45:57.278 Protocol version check failure.
			
The response to MYTH_PROTO_VERSION was empty.
			
This happens when the backend is too busy to respond,
			
or has deadlocked in due to bugs or hardware failure.
2010-10-12 16:45:59.185 MythContext: Connecting to backend server: 192.168.10.2:3306 (try 1 of 1)

2010-10-12 16:45:59.186 MythSocket(9aa3330:33): Protocol error: 'r' is not a valid size prefix. 110 bytes pending.

2010-10-12 16:45:59.186 Protocol version check failure.
			
The response to MYTH_PROTO_VERSION was empty.
			
This happens when the backend is too busy to respond,
			
or has deadlocked in due to bugs or hardware failure.

2010-10-12 16:46:00.935 AudioPulseUtil: Resume Success

2010-10-12 16:46:00.936 Deleting UPnP client...




```[/CODE]

---

### Post by laffinet on 2010-10-13
I had this problem a while ago.

Deleting all my tuners, rebooting, re-adding them fixed the issue. Not very convenient but it worked.

---

### Post by bance on 2010-10-14
Thanks, I'll try that, any idea about the second part?

Never mind did a fresh install.........

---


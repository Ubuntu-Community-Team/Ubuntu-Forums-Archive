---
title: "cannot open dvb card in mythtv"
date: 2010-01-01
forum: Multimedia Software
---

### Post by Afkpuz on 2010-01-01
I'm running ubuntu 9.10 wit mythtv.  My dvb card is a haupauge pvr 1250.  When I run the backend, this is the output.  ```
alex@mythtv-center:~$ sudo killall mythbackend
[sudo] password for alex: 
alex@mythtv-center:~$ mythbackend
2010-01-01 16:16:39.329 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-01-01 16:16:39.329 Using runtime prefix = /usr
2010-01-01 16:16:39.330 Using configuration directory = /home/alex/.mythtv
2010-01-01 16:16:39.330 Empty LocalHostName.
2010-01-01 16:16:39.330 Using localhost value of mythtv-center
2010-01-01 16:16:39.345 New DB connection, total: 1
2010-01-01 16:16:39.349 Connected to database 'mythconverg' at host: localhost
2010-01-01 16:16:39.349 Closing DB connection named 'DBManager0'
2010-01-01 16:16:39.350 Connected to database 'mythconverg' at host: localhost
2010-01-01 16:16:39.354 Current MythTV Schema Version (DBSchemaVer): 1244
2010-01-01 16:16:39.356 MythBackend: Starting up as the master server.
2010-01-01 16:16:39.365 New DB connection, total: 2
2010-01-01 16:16:39.365 Connected to database 'mythconverg' at host: localhost
2010-01-01 16:16:39.370 New DB connection, total: 3
2010-01-01 16:16:39.371 Connected to database 'mythconverg' at host: localhost
2010-01-01 16:16:39.459 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:39.509 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:39.559 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:39.610 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:39.660 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:39.710 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:39.760 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:39.811 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:39.861 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:39.911 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:39.961 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:40.012 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:40.062 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:40.112 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:40.162 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:40.213 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:40.263 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:40.313 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:40.363 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:40.413 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-01-01 16:16:40.414 DVBChan(3:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2010-01-01 16:16:40.415 New DB scheduler connection
2010-01-01 16:16:40.415 Connected to database 'mythconverg' at host: localhost
2010-01-01 16:16:40.431 MediaServer::HttpServer Create Error
2010-01-01 16:16:40.446 Enabled verbose msgs:  important general
2010-01-01 16:16:40.448 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-01-01 16:16:43.422 Reschedule requested for id -1.
2010-01-01 16:16:43.546 Scheduled 0 items in 0.1 = 0.00 match + 0.12 place
2010-01-01 16:16:43.549 Seem to be woken up by USER
2010-01-01 16:18:00.424 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

```


Looks like the problem lies with the dvb card, yet this card is known to work.  I've used it in previous versions.  Any ideas?

---

### Post by yoghurt on 2010-01-26
Hi,
I have the same problem, but with a different card (Leadtek Winfast Dongle gold). My card is working fine in Kaffeine though...

---

### Post by schitthoch2 on 2010-06-02
Same Problem with TT-2300-C here ...

---

### Post by jaripetteri on 2010-06-24
I had similar problem and just find out that my user was somehow drop out for video group. I re-added user to video group and logout/login and was able to use DVB cards again.

---

### Post by schitthoch2 on 2010-06-27
my DVB card was registered three-fold in the DB. Used the same udev adapter but a different DB adapter number each. After deleting 2 adapters i had no problems anymore.

---

### Post by morkunas on 2010-08-05
This error just occurred for me.  Is there a definitive  solution?

Andrew

---


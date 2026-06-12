---
title: "Myth 0.22 in repos."
date: 2009-11-08
forum: Multimedia Software
---

### Post by dchurch24 on 2009-11-08
Hi all,

I currently have 4 myth frontends running on my network and one backend server (with 3 dvb-t cards).

I went to install another frontend through Synaptic and it's installed 0.22. Not a problem, I was wanting to have a look at the new UI in any case.

However, it wants me to upgrade the backend database schema - indeed the frontend install attempted to do this and failed with:

```

2009-11-08 12:30:51.110 MythTV database schema is old. Waiting to see if DB is being upgraded.
2009-11-08 12:30:52.118 Current MythTV Schema Version (DBSchemaVer): 1214
2009-11-08 12:30:53.126 Current MythTV Schema Version (DBSchemaVer): 1214
2009-11-08 12:30:54.133 Current MythTV Schema Version (DBSchemaVer): 1214
2009-11-08 12:30:55.141 Current MythTV Schema Version (DBSchemaVer): 1214
2009-11-08 12:30:56.149 Current MythTV Schema Version (DBSchemaVer): 1214
2009-11-08 12:30:56.150 Timed out waiting.
2009-11-08 12:30:56.150 Not allowed to upgrade the database. Skipping backup.
2009-11-08 12:31:04.152 Couldn't upgrade database to new schema, exiting.

```

Is there a way I can run 0.22 frontend without upgrading the DB - I don't want to upset the other 4 frontend installs on the network.


EDIT: I figured I'd take the plunge and upgrade the server - I noticed that 0.22 is not in the hardy repos. 

Do I have to upgrade to 9.10 to install the 0.22 MythBackend? If so, is it safe to do a 'sudo apt-get upgrade' or is it still recommended to install 9.10 from scratch?

To install 0.22 on my other clients will they need the OS to be upgraded as well? Again, if so, does anyone know it the ADU devices are supported in 9.10, as I have configured one of my frontends to be able to turn the lights on and off when playing movies etc... and it does it through an ADU device for which there was support in 8.04, but not in 8.10 - and therefore, that machine is running 8.04.

EDIT2: Scratch the ADU question - I just ran 9.10 on a live disc on the machine with the ADU unit in it, and it seems that support in the kernel has been reinstated, so am currently installing 9.10 on the main mythfrontend, and when it's finished with the disc, I will upgrade the server to 9.10 and mythbackend 0.22 as well and see how that goes.

Wish me luck, my misses is already annoyed that there is no TV that works anywhere in the house already!

---

### Post by dchurch24 on 2009-11-08
Arrrrghhh - I've just gone through and updated my MythBackend.

Now every time I try to run it I get:

```

2009-11-08 16:35:45.911 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-11-08 16:35:45.912 Using runtime prefix = /usr
2009-11-08 16:35:45.912 Using configuration directory = /home/dave/.mythtv
2009-11-08 16:35:45.920 Empty LocalHostName.
2009-11-08 16:35:45.920 Using localhost value of mythserver
2009-11-08 16:35:45.927 New DB connection, total: 1
2009-11-08 16:35:45.932 Connected to database 'mythconverg' at host: localhost
2009-11-08 16:35:45.932 Closing DB connection named 'DBManager0'
2009-11-08 16:35:45.932 Connected to database 'mythconverg' at host: localhost
2009-11-08 16:35:45.936 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-08 16:35:45.937 MythBackend: Starting up as the master server.
2009-11-08 16:35:45.940 New DB connection, total: 2
2009-11-08 16:35:45.941 Connected to database 'mythconverg' at host: localhost
2009-11-08 16:35:45.944 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2009-11-08 16:35:45.945 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2009-11-08 16:35:45.995 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)


```

I don't understand how my dvb card can be busy.

---


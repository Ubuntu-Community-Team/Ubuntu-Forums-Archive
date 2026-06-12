---
title: "help needed with newbie mythbuntu setup errors"
date: 2008-08-04
forum: Mythbuntu
---

### Post by riknos on 2008-08-04
Still not got started with Mythtv but do not throw in the towel easily. Have gone through all the backend screens many times to try to set up DVB-S TV channels but so far no success. There is definitely a problem with the db as starting channel somehow has "Please add" as a channel!

Would appreciate any pointers from anyone who can decipher the following ouput.

Also I am not sure if users/permissions/profiles have been setup correctly automatically by the mythbuntu install. Would like to know what I need to check. 

Thanks.  

```

 * Restarting MythTV server: mythbackend                                 [ OK ] 
richard@main-pc:~$ /usr/bin/mythbackend
2008-08-04 12:52:34.210 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-04 12:52:34.210 Empty LocalHostName.
2008-08-04 12:52:34.210 Using localhost value of main-pc
QSettings::sync: filename is null/empty
2008-08-04 12:52:34.217 New DB connection, total: 1
2008-08-04 12:52:34.221 Connected to database 'mythconverg' at host: localhost
2008-08-04 12:52:34.222 Closing DB connection named 'DBManager0'
2008-08-04 12:52:34.222 Connected to database 'mythconverg' at host: localhost
QSettings::sync: filename is null/empty
2008-08-04 12:52:34.225 New DB connection, total: 2
2008-08-04 12:52:34.225 Connected to database 'mythconverg' at host: localhost
2008-08-04 12:52:34.226 Current Schema Version: 1214
Starting up as the master server.
2008-08-04 12:52:34.250 DiSEqCDevTree, Warning: No device tree for cardid 282
QSettings::sync: filename is null/empty
2008-08-04 12:52:34.996 New DB connection, total: 3
2008-08-04 12:52:34.996 Connected to database 'mythconverg' at host: localhost
2008-08-04 12:52:34.998 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2008-08-04 12:52:34.998 DVBChan(282:0) Error: SetChannelByString(Please add): Unable to find channel in database.
2008-08-04 12:52:34.998 ChannelBase(282) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
QSettings::sync: filename is null/empty
2008-08-04 12:52:35.005 New DB scheduler connection
2008-08-04 12:52:35.005 Connected to database 'mythconverg' at host: localhost
QServerSocket: failed to bind or listen to the socket
2008-08-04 12:52:35.011 MediaServer::HttpServer Create Error
2008-08-04 12:52:35.012 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-08-04 12:52:35.012 Enabled verbose msgs:  important general
2008-08-04 12:52:35.013 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QServerSocket: failed to bind or listen to the socket
2008-08-04 12:52:35.013 Failed to bind port 6543. Exiting.


```

---

### Post by wyliecoyoteuk on 2008-08-04
Have you done a successful channel scan? -until you do "please add" is the default entry in the input section.

---

### Post by superm1 on 2008-08-04
> **riknos said:**
> Still not got started with Mythtv but do not throw in the towel easily. Have gone through all the backend screens many times to try to set up DVB-S TV channels but so far no success. There is definitely a problem with the db as starting channel somehow has "Please add" as a channel!

Would appreciate any pointers from anyone who can decipher the following ouput.

Also I am not sure if users/permissions/profiles have been setup correctly automatically by the mythbuntu install. Would like to know what I need to check. 

Thanks.  

```

 * Restarting MythTV server: mythbackend                                 [ OK ] 
richard@main-pc:~$ /usr/bin/mythbackend
2008-08-04 12:52:34.210 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-04 12:52:34.210 Empty LocalHostName.
2008-08-04 12:52:34.210 Using localhost value of main-pc
QSettings::sync: filename is null/empty
2008-08-04 12:52:34.217 New DB connection, total: 1
2008-08-04 12:52:34.221 Connected to database 'mythconverg' at host: localhost
2008-08-04 12:52:34.222 Closing DB connection named 'DBManager0'
2008-08-04 12:52:34.222 Connected to database 'mythconverg' at host: localhost
QSettings::sync: filename is null/empty
2008-08-04 12:52:34.225 New DB connection, total: 2
2008-08-04 12:52:34.225 Connected to database 'mythconverg' at host: localhost
2008-08-04 12:52:34.226 Current Schema Version: 1214
Starting up as the master server.
2008-08-04 12:52:34.250 DiSEqCDevTree, Warning: No device tree for cardid 282
QSettings::sync: filename is null/empty
2008-08-04 12:52:34.996 New DB connection, total: 3
2008-08-04 12:52:34.996 Connected to database 'mythconverg' at host: localhost
2008-08-04 12:52:34.998 GetChannelData() failed because it could not
            find channel number 'Please add' in DB for source '1'.
2008-08-04 12:52:34.998 DVBChan(282:0) Error: SetChannelByString(Please add): Unable to find channel in database.
2008-08-04 12:52:34.998 ChannelBase(282) Error: Setting start channel 'Please add' failed, 
            and we failed to find any suitible channels on any input.
QSettings::sync: filename is null/empty
2008-08-04 12:52:35.005 New DB scheduler connection
2008-08-04 12:52:35.005 Connected to database 'mythconverg' at host: localhost
QServerSocket: failed to bind or listen to the socket
2008-08-04 12:52:35.011 MediaServer::HttpServer Create Error
2008-08-04 12:52:35.012 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-08-04 12:52:35.012 Enabled verbose msgs:  important general
2008-08-04 12:52:35.013 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QServerSocket: failed to bind or listen to the socket
2008-08-04 12:52:35.013 Failed to bind port 6543. Exiting.


```
Don't start mythbackend your self as your own user.  Use the init script only.

---

### Post by riknos on 2008-08-04
Part success! Have managed to scan in lots of channels. Then run mythfilldatabase from gui but when I go to Frontend and select TV nothing appears...

---

### Post by riknos on 2008-08-04
Tks superm1. Starting mythbackend as suggested now but see reply to wyliecoyoteuk.

---

### Post by superm1 on 2008-08-04
> **riknos said:**
> Part success! Have managed to scan in lots of channels. Then run mythfilldatabase from gui but when I go to Frontend and select TV nothing appears...
You need to make sure you  "associate" that channel line up to an input;.

---

### Post by wyliecoyoteuk on 2008-08-10
Hi, you need to set things up in this order

capture card (driver)
video source (program guide source)
Input (link card to video source)

The fact that you have scanned channels means you have probably got that far.

If you are not getting tv, it could mean that :
a) you are not a member of the mythtv group
b)the mythtv user does not have rw permissions on  /var/lib/mythtv , or  /usr/share/mythtv

---

### Post by avocade on 2008-08-10
My "channel scanner" button is simply grayed out, so I can't even use it! What is going on? It finds my DVB-T card (avertv dvb-t 771) in the setup alright, as well as the swedb XMLTV sources. 

Please help! I used to use Knoppmyth, but Mythbuntu seems much nicer. Only this channel scanning problem left.

---


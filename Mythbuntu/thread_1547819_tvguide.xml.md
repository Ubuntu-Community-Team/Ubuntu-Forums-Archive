---
title: "tvguide.xml"
date: 2010-08-07
forum: Mythbuntu
---

### Post by tpg_sr on 2010-08-07
Have 10.04 installed and seems to be working well (but not perfectly).  The front end is a Silicon Dust HomeRun dual channel unit.  I know very little about Linux or Unbutu ... am more of a Windows person ... but trying to learn (I'm old so learning 'ain't so easy' !!)

Anyway, mythfilldatabase doesn't seem to work ... it opens a window and shows it's trying, but no joy.  So I opened a terminal window and input command to manually update the database to see if that would work.  The command is:
mythfilldatabase --update --file 1 tvguide.xml

And the result was:
2010-08-07 05:22:21.540 Bypassing grabbers, reading directly from file
2010-08-07 05:22:21.542 Using runtime prefix = /usr
2010-08-07 05:22:21.542 Using configuration directory = /home/htpc/.mythtv
2010-08-07 05:22:21.544 Empty LocalHostName.
2010-08-07 05:22:21.544 Using localhost value of htpc-desktop
2010-08-07 05:22:21.564 New DB connection, total: 1
2010-08-07 05:22:21.574 Connected to database 'mythconverg' at host: localhost
2010-08-07 05:22:21.574 Closing DB connection named 'DBManager0'
2010-08-07 05:22:21.577 Connected to database 'mythconverg' at host: localhost
2010-08-07 05:22:21.583 Current MythTV Schema Version (DBSchemaVer): 1254
2010-08-07 05:22:21.594 mythfilldatabase: Listings Download Started
2010-08-07 05:22:21.628 Error unable to open 'tvguide.xml' for reading.
2010-08-07 05:22:21.630 DataDirect: Deleting temporary files
QSqlDatabasePrivate::removeDatabase: connection 'DBManager0' is still in use, all queries will cease to work.
htpc@htpc-desktop:~$ mythfilldatabase --update --file 1 tvguide.xml
2010-08-07 06:04:35.935 Bypassing grabbers, reading directly from file
2010-08-07 06:04:35.936 Using runtime prefix = /usr
2010-08-07 06:04:35.936 Using configuration directory = /home/htpc/.mythtv
2010-08-07 06:04:35.938 Empty LocalHostName.
2010-08-07 06:04:35.938 Using localhost value of htpc-desktop
2010-08-07 06:04:35.960 New DB connection, total: 1
2010-08-07 06:04:35.979 Connected to database 'mythconverg' at host: localhost
2010-08-07 06:04:35.979 Closing DB connection named 'DBManager0'
2010-08-07 06:04:35.981 Connected to database 'mythconverg' at host: localhost
2010-08-07 06:04:35.992 Current MythTV Schema Version (DBSchemaVer): 1254
2010-08-07 06:04:36.010 mythfilldatabase: Listings Download Started
2010-08-07 06:04:36.014 Error unable to open 'tvguide.xml' for reading.
2010-08-07 06:04:36.016 DataDirect: Deleting temporary files
QSqlDatabasePrivate::removeDatabase: connection 'DBManager0' is still in use, all queries will cease to work.


Anyone have any insight into what is happening?

thanks folks

tpg

---

### Post by ian dobson on 2010-08-07
Hi,

Does the file  tvguide.xml exist in the directory that you started mythfilldatabase in?

Where are you getting your EPG data?

Regards
Ian Dobson

---

### Post by LowSky on 2010-08-07
What did you set up under video sources on the MythTV backend?

if you in the US as your ID says, then you will need to set up an account with schedules direct, its the only way to get TV info data in the US.
[www.schedulesdirect.org/](www.schedulesdirect.org/)

and then add it to your Video sources in the backend, then link to the input connections. then mythfill will work

---

### Post by tpg_sr on 2010-08-07
OK ... I setup a schedulesdirect.org account, and got Myth reading it ... shouldn't show names be showing up?  or do I have to wait 24 hours to let it populate?

---

### Post by LowSky on 2010-08-07
24 hours?

did you do a channel scan? on the back end to see what channels you can pick up?

---

### Post by tpg_sr on 2010-08-07
I did it BEFORE getting the schedules direct connection working, but since it knows what channels are in my area (and I can watch them live, so I know it's working), I figured that once I setup schedules direct, I'd see show names ... but there are none.  I re-ran the scan just now, and still no show info showing.

---


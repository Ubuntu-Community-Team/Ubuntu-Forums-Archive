---
title: "DVBChan(4:0) Error: Opening DVB frontend device failed."
date: 2008-09-07
forum: Mythbuntu
---

### Post by Andrew U.K. on 2008-09-07
Hi,
I'm trying to set up the acpi wake up with the
 
/help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake#MythShutdownCheck

web page but I keep on running into problems with this bit
 
[COLOR="DimGray"]]Another Test

Before proceeding, go into the frontend and schedule a recording an hour or so from now and note the time it starts.

Now we can test to see if the scripts and their interfaces with MythTV are set up correctly. First, set /proc/acpi alarm to a known value (again, if your date/time format is not yyyy-MM-dd hh:mm:ss, adjust as needed):

    *

      $ sudo sh -c 'echo "2007-12-12 12:12:12" > /proc/acpi/alarm'[/COLOR]

When I complete the test once I get the shutting down warning, if I do the test again (usually after the final test doesn't work) I now get this error come up instead of the shutting down warning.

[COLOR="DimGray"]andrew@andrew-Telly:~$ sudo mythbackend &
[1] 17156
andrew@andrew-Telly:~$ 2008-09-07 07:20:31.635 Using runtime prefix = /usr, libdir = /usr/lib
2008-09-07 07:20:31.636 Empty LocalHostName.
2008-09-07 07:20:31.636 Using localhost value of andrew-Telly
2008-09-07 07:20:31.654 New DB connection, total: 1
2008-09-07 07:20:31.661 Connected to database 'mythconverg' at host: localhost
2008-09-07 07:20:31.663 Closing DB connection named 'DBManager0'
2008-09-07 07:20:31.664 Connected to database 'mythconverg' at host: localhost
2008-09-07 07:20:31.666 New DB connection, total: 2
2008-09-07 07:20:31.667 Connected to database 'mythconverg' at host: localhost
2008-09-07 07:20:31.669 Current Schema Version: 1214
Starting up as the master server.
2008-09-07 07:20:31.681 DVBChan(4:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-09-07 07:20:31.682 DVBChan(5:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
QServerSocket: failed to bind or listen to the socket
2008-09-07 07:20:31.689 MediaServer::HttpServer Create Error
2008-09-07 07:20:31.689 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-09-07 07:20:31.690 Enabled verbose msgs:  important general
2008-09-07 07:20:31.691 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QServerSocket: failed to bind or listen to the socket
2008-09-07 07:20:31.693 Failed to bind port 6543. Exiting.
andrew@andrew-Telly:~$ [/COLOR]



Please anybody help, is it a problem between frontend and backend?

Cheers 
Andrew

---

### Post by ian dobson on 2008-09-07
Hi,

The "Device or resource busy" means that something as already opened the devices. The same does for not being able to "bind to an interface" as something has already opened it.

I've see this error when I try and start the backend for the second time. Maybe you should try killing off Mythbackend before restarting it.

Regards
Ian Dobson

---

### Post by Andrew U.K. on 2008-09-08
Thanks

---

### Post by ian dobson on 2008-09-08
So,is the problem solved?
If so it would be nice if you would explain what you did to fix the problem, so that maybe someone else with the same problem could find the solution here.

Regards
Ian Dobson

---

### Post by Andrew U.K. on 2008-09-09
Yes of course.

I had a poke around the back, and I think the TV card had become unseated. I opened her up and pushed it in and everything is O.K. now.

Thanks

Andrew

---


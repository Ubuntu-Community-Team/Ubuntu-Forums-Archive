---
title: "tzcheck as a client (?)"
date: 2009-12-21
forum: Mythbuntu
---

### Post by rusty0101 on 2009-12-21
Ok, I had a reasonably working combination master/slave mythbackend combination with a front end running on the master backend. 

The slave back end has the better capture for whatever reason. We'll call the master Mike, and the slave Steve. Not the devices real names, but that doesn't matter.

Up until today, if Steve was shut down, or rebooted or something, I could see when it came on line by doing a search for it's name in the /var/log/mythtv/mythbackend.log file on Mike. The results would look something like:

2009-12-21 20:46:54.807 adding: steve as a client (events: 0)

For whatever reason though, now I see a lot of log entries like:

2009-12-21 21:06:39.423 adding: tzcheck as a client (events: 0)

And by a lot I mean 2192 entries between timestamps 2009-12-21 19:52:24.899 and 2009-12-21 21:08:15.230 (Not planning on pasting the list)

When I look at the /var/log/mythtv/mythbackend.log on steve, I see entries like:
2009-12-21 20:45:55.853 Using runtime prefix = /usr
2009-12-21 20:45:55.894 Using configuration directory = /home/mythtv/.mythtv
2009-12-21 20:45:55.936 Empty LocalHostName.
2009-12-21 20:45:55.978 Using localhost value of steve
2009-12-21 20:45:56.020 Testing network connectivity to 'mike'
2009-12-21 20:45:56.070 New DB connection, total: 1
2009-12-21 20:45:56.114 Connected to database 'mythconverg' at host: mike
2009-12-21 20:45:56.154 Closing DB connection named 'DBManager0'
2009-12-21 20:45:56.198 Connected to database 'mythconverg' at host: mike
2009-12-21 20:45:56.243 Using protocol version 50
2009-12-21 20:45:56.389 Backend is running in America/Chicago time zone.
2009-12-21 20:45:56.433 Current MythTV Schema Version (DBSchemaVer): 1244
2009-12-21 20:45:56.475 MythBackend: Running as a slave backend.
2009-12-21 20:45:56.518 New DB connection, total: 2
2009-12-21 20:45:56.556 Connected to database 'mythconverg' at host: mike
2009-12-21 20:45:56.604 New DB connection, total: 3
2009-12-21 20:45:56.648 Connected to database 'mythconverg' at host: mike
2009-12-21 20:45:57.397 mythbackend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)

that simply repeats. If I stop the backend on steve using the 'sudo stop mythv-backend' or 'sudo /etc/init.d/mythtv-backend stop' commands, the tzcheck entries stop incrementing. 


If I look at the backend status page on my master backend mythweb interface, it tells me that the tuners for steve are '(currently not connected)' and recordings that were stored only on this box are currently unavailable. (I can copy them across to the master to watch them, but until the master and slave are communicating again, I'm going to see garbage for new recordings, see comments regarding tuners above.

I've attempted to reboot both systems several times, singly and simultaneously, no change. I've done an apt-get dist-upgrade on both systems to make sure that they are running the same collection of packages for mythtv.

The command 'mythtv-status' on steve returns "Sorry, failed to fetch http://localhost:6544/xml."

From what I'm able to tell, 'steve' went into suspend because of a stray 'suspend' key press on the keyboard. When attempting to bring it out of suspend it wouldn't recognize key presses on the keyboard and ultimately had to be power cycled. It was not showing up as connected before that power cycle.

There is a database error on the master, however it existed before the problem started. for over a week I've been getting an 'Incorrect key file for table 'tvchain'; try to repair it' message, which all attempts to repair have resulted in nothing other than an explanation that the file is corrupt and _no_ apparent attempt to actually _fix_ or _repair_ the problem. A bit annoying but so far as I've been able to tell not otherwise presenting any issue that seem to impact the functionality of the platform. 

I don't expect it will help, but I can make the log files available on a server some place. Nothing I'm seeing in the log files seems to be particularly useful. Front ends all seem to be able to connect without trouble, other than that they can't see the content stored on Steve.

I've spent more time re-building these two computers in the past 2 months than I spent watching live or recorded TV under Jaunty. It's getting really old, entirely too fast.

---

### Post by rusty0101 on 2009-12-22
I would hesitate to call this a 'solution' but for the moment it's 'solved.'

In my network at home, not between the master back end and slave is a switch that is sensitive to heat. If the room gets over 80 degrees or so, the switch stops talking to it's upstream switch.

One of the devices plugged into this switch is an HDHomRunner dual tuner that is one of my ota digital sources. (Reception on shorter co-ax than the tuner on steve is not as good as the hvr-1600 provides.)

After spending entirely too much time filtering out error messages in my master backend log, stopping and starting the master back end, with and without the slave back end attempting to connect, I noticed a bunch of "HDHRSH(1010F378-1) Error: Unable to connect to device" messages (and similar) in the log. A quick search showed that this was for hdhomerun access, and I checked the switch, and found that it had lost it's uplink. Nothing on that switch besides the hdhomerun is critical at the moment, so I bypassed it (upstream switch does auto mdi|x switching) and restarted the master back end.

I was still getting the multiple 'added: tzcheck..' events when I restarted the slave backend service, but reloading the slave backend box resulted in a functioning system.

Even though the switch the hdhomerun box was connected to was not functioning upstream through the reboots on the master backend, the master backend still showed the tuners in it's list of available tuners in the web server. 

I suppose that it's time to come up with a new switch that doesn't have the same heat sensitivity.

Entirely too many useless errors in the backend logs.

Filter string I used to get down to just the stuff I was looking for was:

$] tail -F mythbackend.log | grep -vi "channel\|band\|pnum\|^$"

---


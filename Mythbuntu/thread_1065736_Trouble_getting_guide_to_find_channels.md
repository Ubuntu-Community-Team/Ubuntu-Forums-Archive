---
title: "Trouble getting guide to find channels"
date: 2009-02-10
forum: Mythbuntu
---

### Post by scs217 on 2009-02-10
Hi, I've read the stickies and searched around for several hours for a solution to this...

From the mythbuntu website I added to a Ubuntu installation. My tuner is a Pinnacle Systems PCTV HD Card (800i).

The problem I am having is in getting a guide to work. I'm not willing to pay for guide service, so I am trying to get the directv guide to work. I'll post output for both tv_grab_na_dtv --configure and for what occurs during the backend setup.

My first try was setting up the tuner card for analog, selecting North America directv as my guide, and the terminal shows the following:
```

2009-02-10 07:23:17.174 Running tv_find_grabbers.
2009-02-10 07:24:23.897 Please wait while MythTV retrieves the list of available channels
Which is your time zone?
Time Zone:
0: Eastern
1: Central
2: Mountain
3: Pacific
4: Alaska
5: Hawaii
Select one: [0,1,2,3,4,5 (default=0)] 0
Enter your zip code to include local channels.
Zip Code: [] #####
Select the channels that you want to receive data for.
```

The terminal then stops updating information. I then go into input connections and try to fetch channels from listing source (other posts have recommended this course of action). The terminal gives the following output:

```
2009-02-10 07:27:50.626 DiSEqCDevTree, Warning: No device tree for cardid 3
2009-02-10 07:27:50.628 New DB connection, total: 3
2009-02-10 07:27:50.640 Connected to database 'mythconverg' at host: localhost
2009-02-10 07:27:50.645 New DB connection, total: 4
2009-02-10 07:27:50.645 Connected to database 'mythconverg' at host: localhost
2009-02-10 07:27:50.647 New DB connection, total: 5
2009-02-10 07:27:50.648 Connected to database 'mythconverg' at host: localhost
2009-02-10 07:28:48.817 Using runtime prefix = /usr
2009-02-10 07:28:48.818 Empty LocalHostName.
2009-02-10 07:28:48.818 Using localhost value of stevens
2009-02-10 07:28:48.831 New DB connection, total: 1
2009-02-10 07:28:48.840 Connected to database 'mythconverg' at host: localhost
2009-02-10 07:28:48.841 Closing DB connection named 'DBManager0'
2009-02-10 07:28:48.842 Connected to database 'mythconverg' at host: localhost
2009-02-10 07:28:48.847 Running for sourceid 1 ONLY because --sourceid was given on command-line
2009-02-10 07:28:48.849 New DB connection, total: 2
2009-02-10 07:28:48.850 Connected to database 'mythconverg' at host: localhost
2009-02-10 07:28:48.851 Updating source #1 (coax) with grabber tv_grab_na_dtv
2009-02-10 07:28:48.852 No channels are configured to use grabber.
2009-02-10 07:28:49.656 Grabber has capabilities: baseline manualconfig tkconfig apiconfig 
2009-02-10 07:28:49.656 
2009-02-10 07:28:49.656 Checking day @ offset 0, date: Tue Feb 10 2009
2009-02-10 07:28:49.656 Data Refresh needed because of user request
2009-02-10 07:28:49.656 Refreshing data for Tue Feb 10 2009
2009-02-10 07:28:49.658 New DB connection, total: 3
2009-02-10 07:28:49.659 Connected to database 'mythconverg' at host: localhost
2009-02-10 07:28:49.660 XMLTV config file is: /home/shane/.mythtv/coax.xmltv
2009-02-10 07:29:17.505 New DB connection, total: 4
2009-02-10 07:29:17.506 Connected to database 'mythconverg' at host: localhost
2009-02-10 07:29:17.509 Updating icons for sourceid: 1
2009-02-10 07:29:17.510 No programs found in data.
2009-02-10 07:29:17.511 Grabber is no longer returning program data, finishing
2009-02-10 07:29:17.512 Data fetching complete.
2009-02-10 07:29:17.512 Adjusting program database end times.
2009-02-10 07:29:17.513     0 replacements made
2009-02-10 07:29:17.513 Marking generic episodes.
2009-02-10 07:29:17.513     Found 0
2009-02-10 07:29:17.513 Marking repeats.
2009-02-10 07:29:17.515     Found 0
2009-02-10 07:29:17.515 Unmarking new episode rebroadcast repeats.
2009-02-10 07:29:17.515     Found 0
2009-02-10 07:29:17.516 Marking episode first showings.
2009-02-10 07:29:17.516     Found 0
2009-02-10 07:29:17.516 Marking episode last showings.
2009-02-10 07:29:17.517     Found 0
2009-02-10 07:29:17.518 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2009-02-10 07:29:17.524 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-10 07:29:17.524 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2009-02-10 07:29:17.524 Error rescheduling id -1 in ScheduledRecording::signalChange
2009-02-10 07:29:17.525 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-10 07:29:17.525 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2009-02-10 07:29:17.526 mythfilldatabase run complete.
2009-02-10 07:29:17.526 DataDirect: Deleting temporary files
```



I then move onto scanning channels and the scanner finds everything that it should. I then exit the setup program and run mythfilldatabase:

```

2009-02-10 07:37:49.215 Using runtime prefix = /usr
2009-02-10 07:37:49.216 Empty LocalHostName.
2009-02-10 07:37:49.216 Using localhost value of stevens
2009-02-10 07:37:49.229 New DB connection, total: 1
2009-02-10 07:37:49.238 Connected to database 'mythconverg' at host: localhost
2009-02-10 07:37:49.239 Closing DB connection named 'DBManager0'
2009-02-10 07:37:49.240 Connected to database 'mythconverg' at host: localhost
2009-02-10 07:37:49.243 New DB connection, total: 2
2009-02-10 07:37:49.244 Connected to database 'mythconverg' at host: localhost
2009-02-10 07:37:49.245 Updating source #1 (coax) with grabber tv_grab_na_dtv
2009-02-10 07:37:49.246 No channels are configured to use grabber.
2009-02-10 07:37:50.059 Grabber has capabilities: baseline manualconfig tkconfig apiconfig 
2009-02-10 07:37:50.060 
2009-02-10 07:37:50.060 Checking day @ offset 0, date: Tue Feb 10 2009
2009-02-10 07:37:50.062 Data refresh needed because no data exists for day @ offset 0 from 8PM - midnight.
2009-02-10 07:37:50.062 Refreshing data for Tue Feb 10 2009
2009-02-10 07:37:50.063 New DB connection, total: 3
2009-02-10 07:37:50.064 Connected to database 'mythconverg' at host: localhost
2009-02-10 07:37:50.066 XMLTV config file is: /home/shane/.mythtv/coax.xmltv
2009-02-10 07:38:17.969 New DB connection, total: 4
2009-02-10 07:38:17.970 Connected to database 'mythconverg' at host: localhost
2009-02-10 07:38:17.972 Updating icons for sourceid: 1
2009-02-10 07:38:17.974 No programs found in data.
2009-02-10 07:38:17.974 Grabber is no longer returning program data, finishing
2009-02-10 07:38:17.975 Data fetching complete.
2009-02-10 07:38:17.975 Adjusting program database end times.
2009-02-10 07:38:17.976     0 replacements made
2009-02-10 07:38:17.976 Marking generic episodes.
2009-02-10 07:38:17.977     Found 0
2009-02-10 07:38:17.977 Marking repeats.
2009-02-10 07:38:17.979     Found 0
2009-02-10 07:38:17.979 Unmarking new episode rebroadcast repeats.
2009-02-10 07:38:17.979     Found 0
2009-02-10 07:38:17.980 Marking episode first showings.
2009-02-10 07:38:17.981     Found 1
2009-02-10 07:38:17.981 Marking episode last showings.
2009-02-10 07:38:17.983     Found 1
2009-02-10 07:38:17.985 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2009-02-10 07:38:17.991 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-10 07:38:17.993 Using protocol version 40
2009-02-10 07:38:18.043 Received a remote 'Clear Cache' request
2009-02-10 07:38:18.045 mythfilldatabase run complete.
2009-02-10 07:38:18.045 DataDirect: Deleting temporary files
Segmentation fault
```



I'll now post the output of mythfilldatabase --manual:




```
###
### Running in manual channel configuration mode.
### This will ask you questions about every channel.
###
2009-02-10 07:39:22.535 Using runtime prefix = /usr
2009-02-10 07:39:22.536 Empty LocalHostName.
2009-02-10 07:39:22.536 Using localhost value of stevens
2009-02-10 07:39:22.549 New DB connection, total: 1
2009-02-10 07:39:22.559 Connected to database 'mythconverg' at host: localhost
2009-02-10 07:39:22.560 Closing DB connection named 'DBManager0'
2009-02-10 07:39:22.560 Connected to database 'mythconverg' at host: localhost
2009-02-10 07:39:22.565 New DB connection, total: 2
2009-02-10 07:39:22.582 Connected to database 'mythconverg' at host: localhost
2009-02-10 07:39:22.584 Updating source #1 (coax) with grabber tv_grab_na_dtv
2009-02-10 07:39:22.584 No channels are configured to use grabber.
2009-02-10 07:39:23.400 Grabber has capabilities: baseline manualconfig tkconfig apiconfig 
2009-02-10 07:39:23.400 
2009-02-10 07:39:23.400 Checking day @ offset 0, date: Tue Feb 10 2009
2009-02-10 07:39:23.402 Data refresh needed because no data exists for day @ offset 0 from 8PM - midnight.
2009-02-10 07:39:23.403 Refreshing data for Tue Feb 10 2009
2009-02-10 07:39:23.404 New DB connection, total: 3
2009-02-10 07:39:23.404 Connected to database 'mythconverg' at host: localhost
2009-02-10 07:39:23.405 XMLTV config file is: /home/shane/.mythtv/coax.xmltv
2009-02-10 07:39:44.774 New DB connection, total: 4
2009-02-10 07:39:44.775 Connected to database 'mythconverg' at host: localhost
2009-02-10 07:39:44.777 Updating icons for sourceid: 1
2009-02-10 07:39:44.778 No programs found in data.
2009-02-10 07:39:44.778 Grabber is no longer returning program data, finishing
2009-02-10 07:39:44.779 Data fetching complete.
2009-02-10 07:39:44.780 Adjusting program database end times.
2009-02-10 07:39:44.781     0 replacements made
2009-02-10 07:39:44.781 Marking generic episodes.
2009-02-10 07:39:44.782     Found 0
2009-02-10 07:39:44.782 Marking repeats.
2009-02-10 07:39:44.784     Found 0
2009-02-10 07:39:44.784 Unmarking new episode rebroadcast repeats.
2009-02-10 07:39:44.784     Found 0
2009-02-10 07:39:44.784 Marking episode first showings.
2009-02-10 07:39:44.793     Found 1
2009-02-10 07:39:44.793 Marking episode last showings.
2009-02-10 07:39:44.794     Found 1
2009-02-10 07:39:44.796 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2009-02-10 07:39:44.801 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-10 07:39:44.808 Using protocol version 40
2009-02-10 07:39:44.823 mythfilldatabase run complete.
2009-02-10 07:39:44.823 DataDirect: Deleting temporary files
```



And finally the result of a few operations with the tv grabber program:


```
s@stevens:~$ tv_grab_na_dtv --list-channels
<?xml version="1.0" encoding="ISO-8859-1"?>
<!DOCTYPE tv SYSTEM "xmltv.dtd">
<tv source-info-url="http://www.directv.com/" source-info-name="DirecTV" generator-info-name="XMLTV" generator-info-url="http://www.xmltv.org/">
</tv>
```

```
s@stevens:~$ tv_grab_na_dtv --configure
Which is your time zone?
Time Zone:
0: Eastern
1: Central
2: Mountain
3: Pacific
4: Alaska
5: Hawaii
Select one: [0,1,2,3,4,5 (default=0)] 0
Enter your zip code to include local channels.
Zip Code: [] #####
Select the channels that you want to receive data for.

```

and the program returns to prompt there, it never asks for channels.


So it seems that the tv_grab program isn't communicating with what mythtv is finding for my channels. I don't know what else to try, so any input is very much appreciated.

---

### Post by scs217 on 2009-02-10
I forgot to add, Ubuntu version is 8.10.

---


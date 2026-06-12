---
title: "ERROR: MythTV is using all inputs, but there are no active recordings?"
date: 2010-09-08
forum: Mythbuntu
---

### Post by gonkyouka on 2010-09-08
After setting the backend and frontend, when running MythTV Frontend, I have the following error:

[[IMG]http://img694.imageshack.us/img694/4966/screenshot23ji.th.png[/IMG]](http://img694.imageshack.us/i/screenshot23ji.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

Heres what my sql.txt
```
# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
DBHostPing=no

DBHostName=localhost
DBUserName=mythtv
DBName=mythconverg

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv (or futz with the DB) every time.
# TWO HOSTS MUST NOT USE THE SAME VALUE
#
LocalHostName=MYCOOLMYTHTVHOST

# If you want your frontend to be able to wake your MySQL server
# using WakeOnLan, have a look at the following settings:
#
#
# The time the frontend waits (in seconds) between reconnect tries.
# This should be the rough time your MySQL server needs for startup
#
#WOLsqlReconnectWaitTime=0
#
#
# This is the number of retries to wake the MySQL server
# until the frontend gives up
#
#WOLsqlConnectRetry=5
#
#
# This is the command executed to wake your MySQL server.
#
#WOLsqlCommand=echo 'WOLsqlServerCommand not set'

DBPassword=7rYxM8gm
```

Im using Ubuntu Lucid.

Can anyone instruct or lighten me up about which part is wrong?

Thanks!

---

### Post by DemonBob on 2010-09-08
What IP address do you have set on both mythbackend and mythfrontend?

If it is set to localhost or 127.0.0.1, set it to the actual IP address of the machine in both the backend setup and frontend preferances. 

Thier should be two spots in the backend setup, make sure you put the machines ip in both. Frontend should only have one spot to put an ip address.

---

### Post by JMcFly on 2010-09-08
Start mythfrontend and mythbackend from terminal windows, alt-tab and look for errors after the 'no tuners' message pops up.

---

### Post by newlinux on 2010-09-08
yep, check your backend logs and system status. probably something wrong with initializing your tuners. what tuners do you have.

---

### Post by LowSky on 2010-09-08
it isn't a tuner issue, its a either a driver issue (less likely) or a network address issue (more likely)

---

### Post by agamotto on 2010-09-09
Could it be that the kernel modules for his tuners aren't loading at the correct time, causing the system to time/error out with the ivtv subsection?  I seem to recall having problems with that and my Hauppauge 150 card during the 8.x series...

---

### Post by LowSky on 2010-09-10
> **agamotto said:**
> Could it be that the kernel modules for his tuners aren't loading at the correct time, causing the system to time/error out with the ivtv subsection?  I seem to recall having problems with that and my Hauppauge 150 card during the 8.x series...

very possible, and the easiest solution is to restart the backend when the system boots.

A bit more time consuming would be to change the startup times of the backend and mysql

---

### Post by lee3521 on 2010-09-10
I had the exact same problem using a PVR-150.  Found that with Mythbuntu 10.04 The backend was starting before the PVR-150 tuner card drivers were loaded and initialized. (Some kind of udev configuration setting I believe)  I enabled auto-builds, did an update, and that has corrected the problem.

Lee C.

---

### Post by RadicalGeek on 2010-09-26
I've reset the IP address to match the IP address of my local machine.  I still get the same issue though.  Lee that procedure you talk about.  How does one go about that?

---

### Post by LowSky on 2010-09-26
upgrade to 23.1 and the issue does seem to correct itself

```
sudo add-apt-repository ppa:mythbuntu/0.23.1

sudo apt-get update && sudo apt-get upgrade
```

---

### Post by gonkyouka on 2011-02-03
> **LowSky said:**
> upgrade to 23.1 and the issue does seem to correct itself

```
sudo add-apt-repository ppa:mythbuntu/0.23.1

sudo apt-get update && sudo apt-get upgrade
```

I still have the same error after upgrading. 

This is my backend setup
[[IMG]http://img593.imageshack.us/img593/9629/selection031.th.png[/IMG]](http://img593.imageshack.us/i/selection031.png/)

---

### Post by newlinux on 2011-02-03
> **newlinux said:**
> yep, check your backend logs and system status. probably something wrong with initializing your tuners. what tuners do you have.

> **LowSky said:**
> it isn't a tuner issue, its a either a driver issue (less likely) or a network address issue (more likely)

Seems like a semantics issue. I guess we have a different definition of tuner issue - to me a driver not loading stopping a tuner from working or network initialization not happening in the right sequence (i.e. hdhomerun)  are still tuner issues (because they stop the tuner from working). I'm looking at it from the mythtv context.

> **gonkyouka said:**
> I still have the same error after upgrading. 

This is my backend setup
[[IMG]http://img593.imageshack.us/img593/9629/selection031.th.png[/IMG]](http://img593.imageshack.us/i/selection031.png/)

Logs please :). Tuner model  please :). Does mythtv report your tuners as working (system status)?

And how did you set up your tuner in the backend?

---

### Post by gonkyouka on 2011-02-04
> **newlinux said:**
> 
Logs please :). Tuner model  please :). Does mythtv report your tuners as working (system status)?

And how did you set up your tuner in the backend?

both mythbackend.log and mythfrontend.log are too large to paste. but here are both logs compressed: [logs]("http://www.mediafire.com/?ufyyt3yr8bol355")

My Tuner: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01) It works fine in Windows.

Tuner Backend Setup:

Card Type: Analog V4L capture card
Video device: /dev/video1
Probed info: UNKNOWN/GENERIC [saa7134]
VBI device: /dev/vbi0
Audio device: ALSA:default
Audio sampling rate limit: (None)
Default input: default

---

### Post by newlinux on 2011-02-04
Video source/Input configuration? There's more tuner configuration than that. What type of tuner is it? You have it configured as a V4L analog card. What brand and model (chipset doesn't tell me that). 

As for your logs that's certainly where we should start - the relevant portions are:
> 
2011-02-04 03:36:35.483 Unable to connect to database!
2011-02-04 03:36:35.547 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2011-02-04 03:36:38.148 UPnPautoconf() - No UPnP backends found
2011-02-04 03:36:38.188 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2011-02-04 03:36:38.487 Deleting UPnP client...
2011-02-04 03:36:39.153 Failed to init MythContext, exiting.
2011-02-04 03:36:39.815 mythbackend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2011-02-04 03:36:39.850 Using runtime prefix = /usr
2011-02-04 03:36:39.900 Using configuration directory = /home/mythtv/.mythtv
2011-02-04 03:36:39.945 Empty LocalHostName.
2011-02-04 03:36:40.000 Using localhost value of gonkyouka
2011-02-04 03:36:40.062 New DB connection, total: 1
2011-02-04 03:36:40.122 Unable to connect to database!
2011-02-04 03:36:40.176 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

2011-02-04 03:37:04.642 mythbackend version: branches/release-0-23-fixes [26863] [www.mythtv.org](www.mythtv.org)
2011-02-04 03:37:04.714 Using runtime prefix = /usr
2011-02-04 03:37:04.764 Using configuration directory = /home/mythtv/.mythtv
2011-02-04 03:37:04.811 Empty LocalHostName.
2011-02-04 03:37:04.843 Using localhost value of gonkyouka
2011-02-04 03:37:04.910 New DB connection, total: 1
2011-02-04 03:37:04.971 Connected to database 'mythconverg' at host: localhost
2011-02-04 03:37:05.024 Closing DB connection named 'DBManager0'
2011-02-04 03:37:05.091 Connected to database 'mythconverg' at host: localhost
2011-02-04 03:37:05.144 MythSocket(95fb778:8): Protocol error: '?' is not a valid size prefix. 90 bytes pending.
2011-02-04 03:37:05.216 Protocol version check failure.
			The response to MYTH_PROTO_VERSION was empty.
			This happens when the backend is too busy to respond,
			or has deadlocked in due to bugs or hardware failure.
2011-02-04 03:37:05.283 Master backend is incompatible with this backend.
Cannot become a slave.

 I think you need to re-run mythtv-setup (and frontend setup after backend is right) to make sure you are using the right mysql password from your mysql.txt and config.xml files, and make sure your tuner is fully configured. Then verify your backend is running and move on to the frontend. Also make sure mysql is running. Do you only have on backend?

---


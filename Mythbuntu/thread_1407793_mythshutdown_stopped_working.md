---
title: "mythshutdown stopped working"
date: 2010-02-15
forum: Mythbuntu
---

### Post by myth01 on 2010-02-15
Hi all

I had ACPI wakeup/mythshutdown working perfectly and now all of a sudden, it wakes up on schedule but will never shut down.  The backend log used to report this:

```
2010-02-07 11:24:49.544 Running the command to shutdown this computer :-
						mythshutdown --shutdown
2010-02-07 11:35:06.139 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
```

for a successful (I assume) shutdown/wakeup cycle, but now I get this:

```
2010-02-13 04:27:29.562 Running the command to shutdown this computer :-
						mythshutdown --shutdown
sh: /sbin/grub-set-default: not found
reboot: Need to be root
```

and the idle timeout seems to start again.  This just keeps repeating itself over and over again and never shuts down.  I don't recall changing anything that should cause this to stop working.

Any help appreciated, I'm getting fed up waking up in the morning to find the PC has been on all night doing nothing...

mythbackend --version:
MythTV Version   : 22594
MythTV Branch    : branches/release-0-22-fixes
Network Protocol : 50
Library API      : 0.22.20091023-1
QT Version       : 4.5.2

---

### Post by Neon Dusk on 2010-02-15
In mythwelcome settings (mythwelcome --setup or F11 in mythwelcome) the 'nvram-wakeup Restart command' should be blank for ACPI Wakeup.

---

### Post by myth01 on 2010-02-17
Cheers Neon Dusk, I checked mythwelcome and the nvram-wakeup field was filled in.  Which is odd because it wasn't before and it worked perfectly.  I definitely didn't put it in there.  Nevermind.

It did the trick; the PC actually turned off while I was trying to reply to you.  Which then made me realise that the pre-shutdown check script must not be working as it is supposed to check if a user is logged in (which I was) and prevent shutdown (which it didn't).  I've disabled the check now because I didn't really need it anyway.

---

### Post by myth01 on 2010-02-18
OK, so it seems that that first part of the problem has been fixed, but it now appears like the countdown never even starts.  These are 2 consecutive backend log entries from last night:

```
2010-02-17 23:46:03.346 Preview: Grabbed preview '/home/matt/recordedtv/7319_20100217232500.mpg' 720x576@180s
2010-02-17 23:51:01.658 Program #5040 not found in PAT!
```

I have the idle timeout for EIT scan set to 5 minutes, and the mythshutdown timeout set for 2 minutes, but the backend was idle for 5 minutes (23:46 - 23:51) allowing the EIT scan to start.  Surely the shutdown countdown should have started in those 5 minutes and shut the computer down before the EIT scan got a chance to start?

And then this afternoon:

```
2010-02-18 18:07:04.798 Reschedule requested for id -1.
2010-02-18 18:07:05.296 Scheduled 69 items in 0.5 = 0.02 match + 0.47 place
2010-02-18 18:10:32.470 Reschedule requested for id -1.
2010-02-18 18:10:32.960 Scheduled 69 items in 0.5 = 0.02 match + 0.46 place
2010-02-18 18:12:45.233 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-18 18:15:59.101 Reschedule requested for id -1.
2010-02-18 18:15:59.612 Scheduled 69 items in 0.5 = 0.02 match + 0.49 place
```

There a multiple occasions of more than 2 minutes of idleness, but no shutdown occurs.  What triggers the constant "Reschedule requested for id..."?  It is repeated over and over again, and I'm guessing it is what is keeping the backend awake...

---

### Post by Neon Dusk on 2010-02-18
Is mythtv still updating the epg?

I've disabled Active EIT scan on my system. In the UK both Freeview & Freesat broadcast the full epg on all muxes/transponders - so if you make regular recordings the epg will be updated from the passive scan.

---

### Post by myth01 on 2010-02-18
> **Neon Dusk said:**
> so if you make regular recordings the epg will be updated from the passive scan.

Didn't know that.  (Actually didn't know there was a passive scan, still trying to learn as much as I can, but it seems the more you learn, the more you realise you don't know)

I'll give disabling the active scan a try.  Earlier I upped the idle timeout before EIT to 10 minutes, and it seemed to work (it switched the PC off while I was typing a reply on this forum-again), but I'm kind of expecting to find the PC still on tomorrow morning.

Is the 'new' EIT data what prompts the 'Reschedule requested...'?

---

### Post by myth01 on 2010-02-19
Argh!  OK, I disabled Active EIT on both cards so now the reschedule requests have quietened down, but now this:

```
2010-02-19 14:37:43.554 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-19 14:52:43.593 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-19 15:07:43.639 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
```

all consecutive entries in the backend log, whole 15 minute periods where the shutdown should have occurred.  Why does the backend sit apparently idle for 15 minutes?  Or is it that the autoexpire is actually still running during that 15 minutes preventing the shutdown?

---

### Post by Neon Dusk on 2010-02-19
The autexpire messages every 15 mins when the backend is on is normal and shouldn't stop the shutdown.

Do you get any 'I'm idle now... shutdown will occur in xx seconds.' messages in the backend log?

If you're using a pre shutdown check script it could that this is preventing shutdown.

When the system is idle what does 
```

mythshutdown --check
echo $?
mythshutdown --status
echo $?

```

return?

---

### Post by myth01 on 2010-02-19
This was the last time the 'I'm idle' message showed up:

```
2010-02-19 00:46:35.847 I'm idle now... shutdown will occur in 120 seconds.
2010-02-19 00:46:41.397 UPnpMedia: BuildMediaMap VIDEO scan starting in :/home/matt/DVD:
2010-02-19 00:46:41.843 UPnpMedia: BuildMediaMap Done. Found 539 objects
2010-02-19 00:47:51.296 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-19 00:48:23.991 MainServer::ANN Monitor
2010-02-19 00:48:24.001 adding: server as a client (events: 0)
2010-02-19 00:48:24.021 MainServer::ANN Monitor
2010-02-19 00:48:24.023 adding: server as a client (events: 1)
2010-02-19 00:48:34.918 Running the command to set the next scheduled wakeup time :-
						mythshutdown --setwakeup 2010-02-19T09:50:00
2010-02-19 00:48:35.020 Running the command to shutdown this computer :-
						mythshutdown --shutdown
2010-02-19 09:51:06.118 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
```

and the PC was successfully shut down.  It is then woken up again at 09:51, to record one program and it has been on ever since (now 22:37).  This is some of the log from during the day:

```
2010-02-19 10:21:58.449 Reschedule requested for id -1.
2010-02-19 10:21:58.985 Scheduled 73 items in 0.5 = 0.02 match + 0.51 place
2010-02-19 10:22:42.914 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-19 10:37:42.955 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-19 10:52:42.991 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-19 11:07:43.025 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-19 11:17:02.053 MainServer::ANN Monitor
2010-02-19 11:17:02.055 adding: server as a client (events: 0)
2010-02-19 11:22:43.060 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-19 11:37:43.096 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-19 11:51:40.534 UPnpMedia: BuildMediaMap VIDEO scan starting in :/home/matt/DVD:
2010-02-19 11:51:40.787 UPnpMedia: BuildMediaMap Done. Found 539 objects
2010-02-19 11:52:43.131 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-19 12:07:43.168 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-19 12:17:02.139 MainServer::ANN Monitor
2010-02-19 12:17:02.141 adding: server as a client (events: 0)
2010-02-19 12:22:43.206 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-19 12:37:43.246 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-19 12:52:43.280 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-19 13:07:43.319 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-19 13:17:02.245 MainServer::ANN Monitor
2010-02-19 13:17:02.247 adding: server as a client (events: 0)
2010-02-19 13:22:43.356 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-19 13:37:43.391 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
```

I disabled the pre-shutdown check the other day as it was supposed to check if a user was logged in and prevent shutdown but it didn't seem to work, I decided I didn't really need it anyway.

> When the system is idle what does 
Code:
mythshutdown --check
echo $?
mythshutdown --status
echo $?
return?

The backend is currently recording 3 shows so I assume it affects the answers but --check returned 1, and --status returned 8.

---

### Post by Neon Dusk on 2010-02-20
> 
When the system is idle what does
Code:
mythshutdown --check
echo $?
mythshutdown --status
echo $?
return? 


Need to try them again when the backend is idle and should be shutting down.

How is your system set-up?
Is it one combined backend / frontend, mutiple frontends ...?
When it starts up is it set for mythwelcome to start?

If you're not seeing any 'I'm idle now ..' messages it suggests a frontend is still connected to the backend.

---

### Post by myth01 on 2010-02-20
It's a combined FE/BE, (I also have a wireless FE but that is always off before the server is due to shutdown).

--check and --status both returned 0 when the backend log reported that the countdown was in progress.

Now that I can see the state the PC is in after a scheduled wakeup (Neon Dusk solved [my other thread]("http://ubuntuforums.org/showthread.php?t=1409518") about the screen not being displayed), I can see that mythwelcome doesn't appear to be started (or at least visible).  The frontend is started on every boot which I guess is what is keeping the backend awake...?  This might make sense, as the PC mostly shuts down ok at night, when I have exited the frontend, but never during the day when it has been unattended and apparently started the frontend.

Although probably unconnected, what is strange is that it seems that Rhythmbox is started on every boot as well, even though it is not in Startup Applications or ~/.config/autostart

---

### Post by Neon Dusk on 2010-02-21
It does sound like that mythwelcome isn't detecting if a startup is scheduled or manual. It should only automatically start the frontend on a manual startup. If a frontend is connected it will block the shutdown.

How is mythwelcome started? Have you set 'MYTHWELCOME=true' in /etc/mythtv/session-settings ?

Can you post you settings for the following :-
mythtv-setup Shutdown/Wakeup options
```

Block shutdown before client connected:
Idle shutdown timeout (secs):
Max. wait for recording (min):         
Startup before rec. (secs):        
Wakeup time format:           
Command to set Wakeup Time:
Server halt command:           
Pre Shutdown check-command:

```

mythwelcome settings
```

Command to set wakeup time:
Wakeup time format:
nvram-wakeup Restart command:
Command to shutdown:

```

---

### Post by myth01 on 2010-02-21
The backend log seems to show it knows who started the PC, it says 'Auto startup assumed' when it has been scheduled, and 'Seems to be woken by user' when it was manual.

I have uncommented the MYTHWELCOME=true line in the session-settings file (a bit annoyed that this wasn't mentioned anywhere in the myth wiki).

It almost seems like mythwelcome is being completely by-passed.  There is nothing (as in absolutely nothing) in the mythwelcome log, and the frontend log hasn't been written to since the 6th Feb.  System monitor doesn't show mythwelcome as a running process until I start it manually from a terminal.

mythbackend settings:
```
Block shutdown before client connected: (unchecked)
Idle shutdown timeout (secs): 60
Max. wait for recording (min):  15       
Startup before rec. (secs): 180     
Wakeup time format: yyyy-MM-ddThh:mm:ss
Command to set Wakeup Time: mythshutdown --setwakeup $time
Server halt command: mythshutdown --shutdown
Pre Shutdown check-command: (blank)
```

mythwelcome settings:
```
Command to set wakeup time: sudo sh -c "/usr/bin/setwakeup.sh $time"
Wakeup time format: time_t
nvram-wakeup Restart command: (blank)
Command to shutdown: sudo shutdown -h now
```

On a side note; any idea why rhythmbox keeps being started at boot?

---

### Post by Neon Dusk on 2010-02-21
Have you restarted the system since uncommenting the MYTHWELCOME line? Hopefully once you restart mythwelcome will start first and then launch the frontend (if it's a manual start).

Your other settings look fine. I'll update the wiki.

> 
On a side note; any idea why rhythmbox keeps being started at boot?

There's an option to save the session for future logins when you go to appliactions -> logout this could be causing it to start every boot

Edit: Once mythwelcome is starting up correctly the mythwelcome and frontend logs will go to /var/log/mythtv/mythwelcome.log

---

### Post by myth01 on 2010-02-21
Sorry Neon, I meant to say that I *had already* uncommmented MYTHWELCOME=true line, after the restart the same thing happened, no mythwelcome, automatic frontend start.  I am assume that if it is working the following would happen:

Automatic start (scheduled wakeup):
Mythwelcome screen displayed, with option to start frontend.

Manual start up:
Mythwelcome screen displayed, frontend displayed automatically.

Or does **only** the frontend appear when it is a manual start, and mythwelcome is run as a background process?

Thanks for all of your help and attention so far Neon Dusk!

---

### Post by Neon Dusk on 2010-02-21
What should happen is 

Automatic start (scheduled wakeup):
Mythwelcome screen displayed, with option to start frontend.

Manual start up:
Mythwelcome screen displayed brielfy then the frontend will start automatically.

In both cases a mythwelcome process will be running.

How have you configured MythTV to automatically start? Did you use Mythbuntu Control Centre or did you do it manually?

If you did it manually the command needs to be 'mythfrontend --service' - if it's just 'mythfrontend' it will ignore the settings in /etc/mythtv/session-settings.

Can you try running 'mythfrontend --service' and see if mythwelcome is starting? 

Just to explain this a bit further. In mythbuntu the actual mythfrontend program has been renamed mythfrontend.real. mythfrontend is a wrapper script which when called with --service will use the session-settings or if called with no parameters will just run mythfrontend.real.

---

### Post by myth01 on 2010-02-21
> How have you configured MythTV to automatically start? Did you use Mythbuntu Control Centre or did you do it manually?

Hmm, now that you mention it, I had manually added 'mythfrontend' to startup applications but then removed it when I started having problems.  Yet the frontend was still always automatically started on every boot.  If mythwelcome wasn't launching it then what was?

Maybe this is connected to the problem with rhythmbox always starting?  I always close rhythmbox straight away (from the notification area), and the frontend before closing down so they should not be counted as applications to 'remember on log out', and I don't even use that feature so it shouldn't happen at all...

I have installed mythbuntu-control-centre and ticked the 'Automatically start frontend' option under 'Startup behaviour'.  That seemed to place a file in ~/.config/autostart that launches mythfrontend --service so hopefully that should work, but I won't have a chance to test an automatic shutdown/wake up cycle for a few hours I don't think.

I closed mythwelcome and the frontend and ran:
```
mythfrontend --service
```
from a terminal which successfully launched mythwelcome followed by the frontend, and  wrote to the mythwelcome log.

---

### Post by Neon Dusk on 2010-02-21
For your rhytmbox problem you could look at this [thread=1376786]thread[/thread].

In mythbuntu 'Removeable Drives and Media' & 'Sessions and Startup' are in Applications -> Settings

---

### Post by myth01 on 2010-02-21
Cheers for all your help Neon, just had a successful startup with mythwelcome working the way it should.  The real test will be tomorrow when I come home from work...

Cheers for the heads up with the rhythmbox thread, it worked a treat, also got rid of the lurking mythfrontend startup.  I don't know why that thread didn't show up when I Googled though...

I noticed you've updated the wiki already, I didn't mean to sound like an a*!e about that.  I'd like to try and help out with mythtv but not sure if I've got much to offer at the moment!

Cheers again.  Faith in ubuntu forums: restored.

---

### Post by Neon Dusk on 2010-02-21
Good to hear that it's working - hopefully all will be good tomorrow as well.

Re: wiki. No problem. There seemed to be little or conflicting info about setting up mythwelcome/mythshutdown so I added that section to the wiki a few weeks back - feedback is welcome.

---

### Post by d1ckwyn on 2010-09-08
Sorry to resurrect an old thread but this is exactly the problem I'm having. When the computer wakes up for a recording, mythfrontend starts and hence the computer won't shutdown since mythfrontend is running!

My system is Mythbuntu 10.04, my scripts are working fine, shutdown.sh and setwakeup.sh. I've tested both and no problem at all, they send the machine to sleep after mythwelcome counts down the 180 seconds and the system wakes ontime for the next scheduled recording. The problem is that when it wakes up for a sceduled recording, mythfrontend starts, hence it won't close down.
I made sure that when I reboot the computer mythfrontend does NOT start. After that I uncommented the Mythwelcome=true line in /etc/mythtv/session-settings and now the Mythwelcome screen starts and shortly after that Mythfrontend starts. Because I started the machine manually, this is the correct behavior I think.
When the machine starts because of a scheduled recording I expect the mythwelcome screen ONLY but the mythfrontend starts aswell. This is my problem, the machine won't shut down anymore because mythfrontend is running.
All help will be highly appreciated and thanks in advance.

---

### Post by Neon Dusk on 2010-09-08
If mythwelcome is always starting mythfrontend (even after a scheduled wakeup) then it indicates that you're not saving the wakeup time in the database using mythshutdown --setwakeup $time (with the time format set to yyyy-MM-ddThh:mm:ss)

Please post your mythbackend Shutdown/Wakeup Options (mythtv-setup) & MythShutdown/MythWelcome Settings (mythwelcome --setup or F11 in mythwelcome) or see the Mythwelcome section in the [ACPI Wakeup Wiki](http://www.mythtv.org/wiki/ACPI_Wakeup)

---

### Post by d1ckwyn on 2010-09-09
Just to make sure, I did a complete new install of MythBuntu 10.04 LTS and followed the ACPI Wiki exactly. I disabled Mythfrontend from the Control Centre and start now with: Mythfrontend --service
If I don't schedule a recording the system will close down after 120 sec which is the value I have set.
If I do on the other hand schedule a recording the system starts counting down from 120 sec but stops at 10 sec and stays there.
It will start recording and close down after the recording is finished. Nothing is easy is it, I hope Neon you have some kind of a solution for this cause I have no idea and don't want to go back to Windows MCE.
Mythshutdown Checks both return zeros!
Thanks in advance

---

### Post by Neon Dusk on 2010-09-09
> **d1ckwyn said:**
> Just to make sure, I did a complete new install of MythBuntu 10.04 LTS and followed the ACPI Wiki exactly. I disabled Mythfrontend from the Control Centre and start now with: Mythfrontend --service
If I don't schedule a recording the system will close down after 120 sec which is the value I have set.
If I do on the other hand schedule a recording the system starts counting down from 120 sec but stops at 10 sec and stays there.
It will start recording and close down after the recording is finished. Nothing is easy is it, I hope Neon you have some kind of a solution for this cause I have no idea and don't want to go back to Windows MCE.
Mythshutdown Checks both return zeros!
Thanks in advance

I'm away from my PC at the moment but when you say that you disabled Mythfrontend from the Control Centre do you mean that you disabled the automatic Mythfrontend startup?

When your PC starts up for a scheduled recording what does 
```

mythshutdown --startup
echo $?

```
return? Should be 0 for a scheduled startup and 1 for a manual startup

You can also try 
```

mythshutdown --startup --verbose all

```

Towards the end of the out put you should see some lines like 
```

2010-09-09 19:13:39.616 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'MythshutdownWakeupTime' AND hostname IS NULL; <<<< Returns 1 row(s)
2010-09-09 19:13:39.616 MSqlQuery::next(DBManager0)  Result: "data = 2010-09-09T21:54:40"

```

---

### Post by d1ckwyn on 2010-09-10
Yes Neon, I disabled the tickbox in MCC and now use mythfrontend --service to start until my problems are over.
I attach some output from the backend log, hopefully it will help
So, the problem is that the countdown stops at 10 seconds and nothing else happens. The screen just sits there showing 10 seconds.
Thank you for taking the time to help me Neon.

```


2010-09-10 15:42:14.747 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-09-10 15:42:14.780 Using runtime prefix = /usr
2010-09-10 15:42:14.790 Using configuration directory = /home/mythtv/.mythtv
2010-09-10 15:42:14.799 Empty LocalHostName.
2010-09-10 15:42:14.806 Using localhost value of dickmyth
2010-09-10 15:42:14.835 New DB connection, total: 1
2010-09-10 15:42:14.840 Unable to connect to database!
2010-09-10 15:42:14.848 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

2010-09-10 15:42:36.982 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-09-10 15:42:37.117 Using runtime prefix = /usr
2010-09-10 15:42:37.195 Using configuration directory = /home/mythtv/.mythtv
2010-09-10 15:42:37.321 Empty LocalHostName.
2010-09-10 15:42:37.337 Using localhost value of dickmyth
2010-09-10 15:42:37.386 New DB connection, total: 1
2010-09-10 15:42:37.396 Unable to connect to database!
2010-09-10 15:42:37.403 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

2010-09-10 15:42:37.441 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-09-10 15:42:37.446 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
SSDP::PerformSearch - did not write entire buffer.
..2010-09-10 15:42:37.641 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
.......................................................................
2010-09-10 15:42:39.623 UPnPautoconf() - No UPnP backends found
2010-09-10 15:42:39.633 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-09-10 15:42:39.691 Deleting UPnP client...
2010-09-10 15:42:39.700 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-09-10 15:42:40.467 Failed to init MythContext, exiting.
2010-09-10 15:42:40.860 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-09-10 15:42:40.874 Using runtime prefix = /usr
2010-09-10 15:42:40.881 Using configuration directory = /home/mythtv/.mythtv
2010-09-10 15:42:40.891 Empty LocalHostName.
2010-09-10 15:42:40.898 Using localhost value of dickmyth
2010-09-10 15:42:40.933 New DB connection, total: 1
2010-09-10 15:42:40.960 Connected to database 'mythconverg' at host: localhost
2010-09-10 15:42:40.973 Closing DB connection named 'DBManager0'
2010-09-10 15:42:40.983 Connected to database 'mythconverg' at host: localhost
2010-09-10 15:42:41.026 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-10 15:42:41.054 MythBackend: Starting up as the master server.
2010-09-10 15:42:41.099 New DB connection, total: 2
2010-09-10 15:42:41.107 Connected to database 'mythconverg' at host: localhost
2010-09-10 15:42:41.156 New DB connection, total: 3
2010-09-10 15:42:41.165 Connected to database 'mythconverg' at host: localhost
2010-09-10 15:42:41.308 New DB scheduler connection
2010-09-10 15:42:41.315 Connected to database 'mythconverg' at host: localhost
2010-09-10 15:42:41.364 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-09-10 15:42:41.372 Main::Registering HttpStatus Extension
2010-09-10 15:42:41.380 Enabled verbose msgs:  important general
2010-09-10 15:42:41.406 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-09-10 15:42:44.338 Reschedule requested for id -1.
2010-09-10 15:42:44.832 Scheduled 0 items in 0.5 = 0.23 match + 0.25 place
2010-09-10 15:42:44.852 AUTO-Startup assumed
2010-09-10 15:42:45.889 I'm idle now... shutdown will occur in 120 seconds.
2010-09-10 15:44:01.337 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-09-10 15:44:44.953 Running the command to shutdown this computer :-
						sudo mythshutdown --shutdown
2010-09-10 15:45:45.299 Waited more than 60 seconds for shutdown to complete - resetting idle time
2010-09-10 15:45:47.345 I'm idle now... shutdown will occur in 120 seconds.
2010-09-10 15:47:46.629 Running the command to shutdown this computer :-
						sudo mythshutdown --shutdown
2010-09-10 15:48:46.877 Waited more than 60 seconds for shutdown to complete - resetting idle time
2010-09-10 15:48:48.905 I'm idle now... shutdown will occur in 120 seconds.
2010-09-10 15:50:47.947 Running the command to shutdown this computer :-
						sudo mythshutdown --shutdown


```

---

### Post by Neon Dusk on 2010-09-10
Can you try setting the server halt command in the Mythbackend options page to
```

mythshutdown --shutdown --verbose all

```

And then look at the backend log files when it failes to shut down.

---

### Post by d1ckwyn on 2010-09-10
Hi Neon
Hereby the requested output. Something wrong with the HDHomerun Tuner??
I use an ASRock ION 330 with a HD Homerun dual Tuner (only one tuner used as far as I know)


```


2010-09-10 21:22:32.195 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-09-10 21:22:32.225 Using runtime prefix = /usr
2010-09-10 21:22:32.235 Using configuration directory = /home/mythtv/.mythtv
2010-09-10 21:22:32.245 Empty LocalHostName.
2010-09-10 21:22:32.252 Using localhost value of dickmyth
2010-09-10 21:22:32.281 New DB connection, total: 1
2010-09-10 21:22:32.286 Unable to connect to database!
2010-09-10 21:22:32.293 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

................................................................................
2010-09-10 21:22:34.879 UPnPautoconf() - No UPnP backends found
2010-09-10 21:22:34.889 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-09-10 21:22:35.039 Deleting UPnP client...
2010-09-10 21:22:58.225 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-09-10 21:22:58.324 Using runtime prefix = /usr
2010-09-10 21:22:58.356 Using configuration directory = /home/mythtv/.mythtv
2010-09-10 21:22:58.470 Empty LocalHostName.
2010-09-10 21:22:58.498 Using localhost value of dickmyth
2010-09-10 21:22:58.582 New DB connection, total: 1
2010-09-10 21:22:58.606 Unable to connect to database!
2010-09-10 21:22:58.655 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

2010-09-10 21:22:58.672 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-09-10 21:22:58.681 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
SSDP::PerformSearch - did not write entire buffer.
.....2010-09-10 21:22:58.873 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
...........................................................................
2010-09-10 21:23:00.777 UPnPautoconf() - No UPnP backends found
2010-09-10 21:23:00.802 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-09-10 21:23:00.861 Deleting UPnP client...
2010-09-10 21:23:01.787 Failed to init MythContext, exiting.
2010-09-10 21:23:02.770 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-09-10 21:23:02.784 Using runtime prefix = /usr
2010-09-10 21:23:02.792 Using configuration directory = /home/mythtv/.mythtv
2010-09-10 21:23:02.801 Empty LocalHostName.
2010-09-10 21:23:02.807 Using localhost value of dickmyth
2010-09-10 21:23:02.852 New DB connection, total: 1
2010-09-10 21:23:02.878 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:23:02.892 Closing DB connection named 'DBManager0'
2010-09-10 21:23:02.901 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:23:02.932 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-10 21:23:02.947 MythBackend: Starting up as the master server.
2010-09-10 21:23:02.989 New DB connection, total: 2
2010-09-10 21:23:03.000 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:23:03.044 New DB connection, total: 3
2010-09-10 21:23:03.070 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:23:03.298 New DB scheduler connection
2010-09-10 21:23:03.308 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:23:03.380 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-09-10 21:23:03.390 Main::Registering HttpStatus Extension
2010-09-10 21:23:03.407 Enabled verbose msgs:  important general
2010-09-10 21:23:03.439 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-09-10 21:23:06.360 Reschedule requested for id -1.
2010-09-10 21:23:06.692 Scheduled 0 items in 0.3 = 0.12 match + 0.20 place
2010-09-10 21:23:06.721 AUTO-Startup assumed
2010-09-10 21:23:07.732 I'm idle now... shutdown will occur in 180 seconds.
2010-09-10 21:23:30.982 MainServer::ANN Monitor
2010-09-10 21:23:30.995 adding: dickmyth as a client (events: 0)
2010-09-10 21:23:31.005 MainServer::ANN Monitor
2010-09-10 21:23:31.012 adding: dickmyth as a client (events: 1)
QSqlQuery::exec: database not open
2010-09-10 21:23:59.588 No error type from QSqlError?  Strange...
2010-09-10 21:23:59.651 Database not open while trying to load setting: eventcmdclientdisconnected
QSqlQuery::exec: database not open
2010-09-10 21:23:59.717 No error type from QSqlError?  Strange...
2010-09-10 21:23:59.781 Database not open while trying to load setting: eventcmdclientdisconnected
2010-09-10 21:24:01.685 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-09-10 21:24:01.687 Using runtime prefix = /usr
2010-09-10 21:24:01.707 Using configuration directory = /home/mythtv/.mythtv
2010-09-10 21:24:01.717 Empty LocalHostName.
2010-09-10 21:24:01.724 Using localhost value of dickmyth
2010-09-10 21:24:01.752 New DB connection, total: 1
2010-09-10 21:24:01.758 Unable to connect to database!
2010-09-10 21:24:01.765 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

...............................................................................
2010-09-10 21:24:04.331 UPnPautoconf() - No UPnP backends found
2010-09-10 21:24:04.338 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-09-10 21:24:04.463 Deleting UPnP client...
2010-09-10 21:24:31.504 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-09-10 21:24:31.645 Using runtime prefix = /usr
2010-09-10 21:24:31.666 Using configuration directory = /home/mythtv/.mythtv
2010-09-10 21:24:31.724 Empty LocalHostName.
2010-09-10 21:24:31.749 Using localhost value of dickmyth
2010-09-10 21:24:31.839 New DB connection, total: 1
2010-09-10 21:24:31.876 Unable to connect to database!
2010-09-10 21:24:31.907 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

2010-09-10 21:24:31.928 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-09-10 21:24:31.949 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
SSDP::PerformSearch - did not write entire buffer.
....2010-09-10 21:24:32.127 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
...........................................................................
2010-09-10 21:24:34.046 UPnPautoconf() - No UPnP backends found
2010-09-10 21:24:34.054 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-09-10 21:24:34.104 Deleting UPnP client...
2010-09-10 21:24:34.112 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-09-10 21:24:34.979 Failed to init MythContext, exiting.
2010-09-10 21:24:35.363 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-09-10 21:24:35.365 Using runtime prefix = /usr
2010-09-10 21:24:35.377 Using configuration directory = /home/mythtv/.mythtv
2010-09-10 21:24:35.396 Empty LocalHostName.
2010-09-10 21:24:35.402 Using localhost value of dickmyth
2010-09-10 21:24:35.438 New DB connection, total: 1
2010-09-10 21:24:35.463 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:24:35.652 Closing DB connection named 'DBManager0'
2010-09-10 21:24:35.662 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:24:35.703 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-10 21:24:35.732 MythBackend: Starting up as the master server.
2010-09-10 21:24:35.767 New DB connection, total: 2
2010-09-10 21:24:35.778 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:24:35.803 New DB connection, total: 3
2010-09-10 21:24:35.811 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:24:35.974 New DB scheduler connection
2010-09-10 21:24:35.982 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:24:36.069 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-09-10 21:24:36.081 Main::Registering HttpStatus Extension
2010-09-10 21:24:36.090 Enabled verbose msgs:  important general
2010-09-10 21:24:36.118 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-09-10 21:24:39.004 Reschedule requested for id -1.
2010-09-10 21:24:39.528 Scheduled 0 items in 0.5 = 0.23 match + 0.28 place
2010-09-10 21:24:39.547 Seem to be woken up by USER
2010-09-10 21:24:40.562 I'm idle now... shutdown will occur in 180 seconds.
2010-09-10 21:24:50.774 MainServer::ANN Monitor
2010-09-10 21:24:50.783 adding: dickmyth as a client (events: 0)
2010-09-10 21:24:50.793 MainServer::ANN Monitor
2010-09-10 21:24:50.799 adding: dickmyth as a client (events: 1)
2010-09-10 21:24:56.614 MainServer::ANN Playback
2010-09-10 21:24:56.627 adding: dickmyth as a client (events: 0)
2010-09-10 21:24:56.638 MainServer::ANN Monitor
2010-09-10 21:24:56.644 adding: dickmyth as a client (events: 1)
2010-09-10 21:25:54.455 Reschedule requested for id 22.
2010-09-10 21:25:54.590 Scheduled 1 items in 0.1 = 0.03 match + 0.10 place
2010-09-10 21:25:56.029 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-09-10 21:26:04.601 I'm idle now... shutdown will occur in 180 seconds.
2010-09-10 21:29:03.965 Running the command to set the next scheduled wakeup time :-
						sudo mythshutdown --setwakeup 2010-09-10T21:39:00
2010-09-10 21:29:04.256 Running the command to shutdown this computer :-
						sudo mythshutdown --shutdown --verbose all
2010-09-10 21:29:04.440 (old)Settings::ReadSettings(settings.txt) - No such file
2010-09-10 21:29:04.448 Using runtime prefix = /usr
2010-09-10 21:29:04.456 Using configuration directory = /home/mythtv/.mythtv
2010-09-10 21:29:04.465 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - No such file
2010-09-10 21:29:04.473 (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file
2010-09-10 21:29:04.482 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBHostName' = 'localhost'.
2010-09-10 21:29:04.490 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2010-09-10 21:29:04.498 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBPassword' = '18M4ZYHA'.
2010-09-10 21:29:04.506 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2010-09-10 21:29:04.515 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2010-09-10 21:29:04.523 (old)Settings::ReadSettings(./mysql.txt) - No such file
2010-09-10 21:29:04.531 Empty LocalHostName.
2010-09-10 21:29:04.540 Using localhost value of dickmyth
2010-09-10 21:29:04.548 Clearing Settings Cache.
2010-09-10 21:29:04.558 MCP::DefaultUPnP() - No default UPnP backend
2010-09-10 21:29:04.565 Clearing Settings Cache.
2010-09-10 21:29:04.589 New DB connection, total: 1
2010-09-10 21:29:04.605 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:29:04.615 Closing DB connection named 'DBManager0'
2010-09-10 21:29:04.623 Clearing Settings Cache.
2010-09-10 21:29:04.631 Enabling Settings Cache.
2010-09-10 21:29:04.639 Clearing Settings Cache.
2010-09-10 21:29:04.648 Mythshutdown: --shutdown
2010-09-10 21:29:04.657 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:29:04.667 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'DailyWakeupStartPeriod1' AND hostname IS NULL; <<<< Returns 1 row(s)
2010-09-10 21:29:04.673 MSqlQuery::next(DBManager0) Result: "data = 00:00"
2010-09-10 21:29:04.683 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'DailyWakeupEndPeriod1' AND hostname IS NULL; <<<< Returns 1 row(s)
2010-09-10 21:29:04.689 MSqlQuery::next(DBManager0) Result: "data = 00:00"
2010-09-10 21:29:04.699 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'DailyWakeupStartPeriod2' AND hostname IS NULL; <<<< Returns 1 row(s)
2010-09-10 21:29:04.750 MSqlQuery::next(DBManager0) Result: "data = 00:00"
2010-09-10 21:29:04.761 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'DailyWakeupEndPeriod2' AND hostname IS NULL; <<<< Returns 1 row(s)
2010-09-10 21:29:04.768 MSqlQuery::next(DBManager0) Result: "data = 00:00"
2010-09-10 21:29:04.777 no daily wakeup times are set
2010-09-10 21:29:04.786 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'MythShutdownNextScheduled' AND hostname IS NULL; <<<< Returns 1 row(s)
2010-09-10 21:29:04.793 MSqlQuery::next(DBManager0) Result: "data = 2010-09-10T21:39:00"
2010-09-10 21:29:04.802 recording scheduled at: 2010-09-10T21:39:00
2010-09-10 21:29:04.810 will wake up at next scheduled program
2010-09-10 21:29:04.820 MSqlQuery::exec(DBManager0) DELETE FROM settings WHERE value = 'MythShutdownWakeupTime';
2010-09-10 21:29:04.828 MSqlQuery::exec(DBManager0) INSERT INTO settings ( value, data ) VALUES ( 'MythShutdownWakeupTime', '2010-09-10T21:39:00' );
2010-09-10 21:29:04.837 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mythshutdownnvramrestartcmd' AND hostname = 'dickmyth' <<<< Returns 1 row(s)
2010-09-10 21:29:04.843 MSqlQuery::next(DBManager0) Result: "data = "
2010-09-10 21:29:04.852 The next wakeup time is less than 15 mins away, not shutting down
2010-09-10 21:30:03.890 Waited more than 60 seconds for shutdown to complete - resetting idle time
2010-09-10 21:30:05.900 I'm idle now... shutdown will occur in 180 seconds.
2010-09-10 21:33:04.967 Running the command to set the next scheduled wakeup time :-
						sudo mythshutdown --setwakeup 2010-09-10T21:39:00
2010-09-10 21:33:05.179 Running the command to shutdown this computer :-
						sudo mythshutdown --shutdown --verbose all
2010-09-10 21:33:05.347 (old)Settings::ReadSettings(settings.txt) - No such file
2010-09-10 21:33:05.354 Using runtime prefix = /usr
2010-09-10 21:33:05.362 Using configuration directory = /home/mythtv/.mythtv
2010-09-10 21:33:05.371 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - No such file
2010-09-10 21:33:05.379 (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file
2010-09-10 21:33:05.388 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBHostName' = 'localhost'.
2010-09-10 21:33:05.396 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2010-09-10 21:33:05.404 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBPassword' = '18M4ZYHA'.
2010-09-10 21:33:05.412 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2010-09-10 21:33:05.421 (old)Settings::ReadSettings(/home/mythtv/.mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2010-09-10 21:33:05.429 (old)Settings::ReadSettings(./mysql.txt) - No such file
2010-09-10 21:33:05.437 Empty LocalHostName.
2010-09-10 21:33:05.446 Using localhost value of dickmyth
2010-09-10 21:33:05.454 Clearing Settings Cache.
2010-09-10 21:33:05.465 MCP::DefaultUPnP() - No default UPnP backend
2010-09-10 21:33:05.471 Clearing Settings Cache.
2010-09-10 21:33:05.500 New DB connection, total: 1
2010-09-10 21:33:05.511 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:33:05.521 Closing DB connection named 'DBManager0'
2010-09-10 21:33:05.529 Clearing Settings Cache.
2010-09-10 21:33:05.537 Enabling Settings Cache.
2010-09-10 21:33:05.545 Clearing Settings Cache.
2010-09-10 21:33:05.554 Mythshutdown: --shutdown
2010-09-10 21:33:05.563 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:33:05.573 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'DailyWakeupStartPeriod1' AND hostname IS NULL; <<<< Returns 1 row(s)
2010-09-10 21:33:05.579 MSqlQuery::next(DBManager0) Result: "data = 00:00"
2010-09-10 21:33:05.589 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'DailyWakeupEndPeriod1' AND hostname IS NULL; <<<< Returns 1 row(s)
2010-09-10 21:33:05.595 MSqlQuery::next(DBManager0) Result: "data = 00:00"
2010-09-10 21:33:05.605 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'DailyWakeupStartPeriod2' AND hostname IS NULL; <<<< Returns 1 row(s)
2010-09-10 21:33:05.653 MSqlQuery::next(DBManager0) Result: "data = 00:00"
2010-09-10 21:33:05.664 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'DailyWakeupEndPeriod2' AND hostname IS NULL; <<<< Returns 1 row(s)
2010-09-10 21:33:05.670 MSqlQuery::next(DBManager0) Result: "data = 00:00"
2010-09-10 21:33:05.679 no daily wakeup times are set
2010-09-10 21:33:05.688 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'MythShutdownNextScheduled' AND hostname IS NULL; <<<< Returns 1 row(s)
2010-09-10 21:33:05.695 MSqlQuery::next(DBManager0) Result: "data = 2010-09-10T21:39:00"
2010-09-10 21:33:05.704 recording scheduled at: 2010-09-10T21:39:00
2010-09-10 21:33:05.712 will wake up at next scheduled program
2010-09-10 21:33:05.721 MSqlQuery::exec(DBManager0) DELETE FROM settings WHERE value = 'MythShutdownWakeupTime';
2010-09-10 21:33:05.730 MSqlQuery::exec(DBManager0) INSERT INTO settings ( value, data ) VALUES ( 'MythShutdownWakeupTime', '2010-09-10T21:39:00' );
2010-09-10 21:33:05.738 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mythshutdownnvramrestartcmd' AND hostname = 'dickmyth' <<<< Returns 1 row(s)
2010-09-10 21:33:05.745 MSqlQuery::next(DBManager0) Result: "data = "
2010-09-10 21:33:05.754 The next wakeup time is less than 15 mins away, not shutting down
2010-09-10 21:34:05.793 Waited more than 60 seconds for shutdown to complete - resetting idle time
2010-09-10 21:35:32.579 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-09-10 21:35:32.581 Using runtime prefix = /usr
2010-09-10 21:35:32.591 Using configuration directory = /home/mythtv/.mythtv
2010-09-10 21:35:32.601 Empty LocalHostName.
2010-09-10 21:35:32.608 Using localhost value of dickmyth
2010-09-10 21:35:32.636 New DB connection, total: 1
2010-09-10 21:35:32.642 Unable to connect to database!
2010-09-10 21:35:32.649 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

................................................................................
2010-09-10 21:35:35.222 UPnPautoconf() - No UPnP backends found
2010-09-10 21:35:35.271 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-09-10 21:35:35.354 Deleting UPnP client...
2010-09-10 21:35:55.364 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-09-10 21:35:55.485 Using runtime prefix = /usr
2010-09-10 21:35:55.499 Using configuration directory = /home/mythtv/.mythtv
2010-09-10 21:35:55.557 Empty LocalHostName.
2010-09-10 21:35:55.583 Using localhost value of dickmyth
2010-09-10 21:35:55.638 New DB connection, total: 1
2010-09-10 21:35:55.650 Unable to connect to database!
2010-09-10 21:35:55.657 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

2010-09-10 21:35:55.669 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-09-10 21:35:55.675 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
SSDP::PerformSearch - did not write entire buffer.
..2010-09-10 21:35:55.869 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
.............................................................................
2010-09-10 21:35:57.846 UPnPautoconf() - No UPnP backends found
2010-09-10 21:35:57.854 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-09-10 21:35:57.904 Deleting UPnP client...
2010-09-10 21:35:57.929 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-09-10 21:35:58.697 Failed to init MythContext, exiting.
2010-09-10 21:35:59.110 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-09-10 21:35:59.113 Using runtime prefix = /usr
2010-09-10 21:35:59.144 Using configuration directory = /home/mythtv/.mythtv
2010-09-10 21:35:59.166 Empty LocalHostName.
2010-09-10 21:35:59.173 Using localhost value of dickmyth
2010-09-10 21:35:59.208 New DB connection, total: 1
2010-09-10 21:35:59.237 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:35:59.248 Closing DB connection named 'DBManager0'
2010-09-10 21:35:59.258 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:35:59.302 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-10 21:35:59.337 MythBackend: Starting up as the master server.
2010-09-10 21:35:59.368 New DB connection, total: 2
2010-09-10 21:35:59.382 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:35:59.411 HDHRSH(192.168.1.40-0) Error: Unable to connect to device
2010-09-10 21:35:59.417 New DB connection, total: 3
2010-09-10 21:35:59.424 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:35:59.467 HDHRSH(192.168.1.40-0) Error: Get request failed
			eno: Network is unreachable (101)
2010-09-10 21:35:59.473 HDHRSH(192.168.1.40-0) Error: Set request failed
			eno: Network is unreachable (101)
2010-09-10 21:35:59.481 HDHRSH(192.168.1.40-0) Error: Get request failed
			eno: Network is unreachable (101)
2010-09-10 21:35:59.489 HDHRSH(192.168.1.40-0) Error: Set request failed
			eno: Network is unreachable (101)
2010-09-10 21:35:59.504 HDHRSH(192.168.1.40-0) Error: Get request failed
			eno: Network is unreachable (101)
2010-09-10 21:35:59.514 HDHRSH(192.168.1.40-0) Error: Set request failed
			eno: Network is unreachable (101)
2010-09-10 21:35:59.592 HDHRSH(192.168.1.40-0) Error: Get request failed
			eno: Network is unreachable (101)
2010-09-10 21:35:59.597 HDHRSH(192.168.1.40-0) Error: Set request failed
			eno: Network is unreachable (101)
2010-09-10 21:35:59.606 HDHRSH(192.168.1.40-0) Error: Get request failed
			eno: Network is unreachable (101)
2010-09-10 21:35:59.614 HDHRSH(192.168.1.40-0) Error: Set request failed
			eno: Network is unreachable (101)
2010-09-10 21:35:59.629 HDHRSH(192.168.1.40-0) Error: Get request failed
			eno: Network is unreachable (101)
2010-09-10 21:35:59.639 HDHRSH(192.168.1.40-0) Error: Set request failed
			eno: Network is unreachable (101)
2010-09-10 21:35:59.654 New DB scheduler connection
2010-09-10 21:35:59.665 Connected to database 'mythconverg' at host: localhost
2010-09-10 21:35:59.716 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-09-10 21:35:59.722 Main::Registering HttpStatus Extension
2010-09-10 21:35:59.730 Enabled verbose msgs:  important general
2010-09-10 21:35:59.764 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-09-10 21:36:02.688 Reschedule requested for id -1.
2010-09-10 21:36:03.326 Scheduled 1 items in 0.6 = 0.41 match + 0.22 place
2010-09-10 21:36:03.347 AUTO-Startup assumed
2010-09-10 21:37:19.694 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min










```

---

### Post by Neon Dusk on 2010-09-10
I'm not sure about the HD Homerun errors but from :-

2010-09-10 21:29:04.802 recording scheduled at: 2010-09-10T21:39:00
2010-09-10 21:29:04.852 The next wakeup time is less than 15 mins away, not shutting down

It's not shutting down as the next scheduled recording is less than 15 minutes away. I belive that this 15 minute check is hard coded into Mythshutdown.

---

### Post by d1ckwyn on 2010-09-12
Hi Neon

```

I belive that this 15 minute check is hard coded into Mythshutdown.

```

That was my problem, I was running tests within that time. Now all is well and thanks for your help.

---


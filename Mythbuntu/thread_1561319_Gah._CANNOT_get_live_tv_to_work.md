---
title: "Gah. CANNOT get live tv to work"
date: 2010-08-26
forum: Mythbuntu
---

### Post by eljeffe on 2010-08-26
I've been messing with this for ages.

[INDENT][LIST]
[*]My tv card works ( and has worked in mythtv recently ( total reinstall since then, though ) ) in other apps.

[*]I have linked, via ln -s /data/mythtv in the /var/lib dir. 

[*]Everything in mythtv directory and down is owned by mythtv:mythtv.

[*]Everything in mythtv directory and down has been sudo chmod -R 775

[*]Specifically ls -l yields "drwxrwsr-x  2 mythtv mythtv  4096 2010-08-25 23:09 [COLOR="Blue"]livetv[/COLOR]" 

[*]I'm sure there are many other rights issues I've verified as well.
[/LIST][/INDENT]

Still I get the dreaded (by me by now) entry in the backend log:

[B]TFW, Error: Opening file '/var/lib/mythtv/livetv/1009_20100825234257.nuv'.
			eno: Permission denied (13)[/B]

Here is the entire log.

```
................................................................................
2010-08-25 23:42:46.944 UPnPautoconf() - No UPnP backends found
2010-08-25 23:42:46.955 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-08-25 23:42:47.067 Deleting UPnP client...
2010-08-25 23:42:47.824 Failed to init MythContext.
2010-08-25 23:42:47.867 mythbackend version: trunk [25797] www.mythtv.org
2010-08-25 23:42:47.867 Using runtime prefix = /usr
2010-08-25 23:42:47.872 Using configuration directory = /home/mythtv/.mythtv
2010-08-25 23:42:47.881 Empty LocalHostName.
2010-08-25 23:42:47.889 Using localhost value of myth
2010-08-25 23:42:47.901 New DB connection, total: 1
2010-08-25 23:42:47.907 Connected to database 'mythconverg' at host: localhost
2010-08-25 23:42:47.981 Closing DB connection named 'DBManager0'
2010-08-25 23:42:47.989 Current locale en_US
2010-08-25 23:42:47.997 No locale defaults file for en_US, skipping
2010-08-25 23:42:48.014 Connected to database 'mythconverg' at host: localhost
2010-08-25 23:42:48.032 Current MythTV Schema Version (DBSchemaVer): 1263
2010-08-25 23:42:48.844 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-08-25 23:42:48.862 MythBackend: Starting up as the master server.
2010-08-25 23:42:48.895 New DB connection, total: 2
2010-08-25 23:42:48.904 Connected to database 'mythconverg' at host: localhost
2010-08-25 23:42:48.912 mythbackend: MythBackend started as master server
2010-08-25 23:42:48.939 New DB connection, total: 3
2010-08-25 23:42:48.962 Connected to database 'mythconverg' at host: localhost
2010-08-25 23:42:49.004 New DB scheduler connection
2010-08-25 23:42:49.021 Connected to database 'mythconverg' at host: localhost
2010-08-25 23:42:49.046 Main::Registering HttpStatus Extension
2010-08-25 23:42:49.062 Enabled verbose msgs:  important general
2010-08-25 23:42:49.070 AutoExpire: ERROR: Filesystem Info cache is empty, unable to calculate necessary parameters.
2010-08-25 23:42:49.107 mythbackend: Autoexpire CalcParams: ERROR: Filesystem Info cache is empty, unable to calculate necessary parameters.
2010-08-25 23:42:50.291 MainServer::ANN Monitor
2010-08-25 23:42:50.320 adding: myth as a client (events: 0)
2010-08-25 23:42:52.048 Reschedule requested for id -1.
2010-08-25 23:42:52.149 Scheduled 0 items in 0.1 = 0.02 match + 0.09 place
2010-08-25 23:42:52.163 scheduler: Scheduled items: Scheduled 0 items in 0.1 = 0.02 match + 0.09 place
2010-08-25 23:42:52.172 Seem to be woken up by USER
2010-08-25 23:42:52.306 MainServer::ANN Monitor
2010-08-25 23:42:52.320 adding: myth as a client (events: 0)
2010-08-25 23:42:52.329 MainServer::ANN Monitor
2010-08-25 23:42:52.337 adding: myth as a client (events: 1)
2010-08-25 23:42:57.008 MainServer::ANN Playback
2010-08-25 23:42:57.020 adding: myth as a client (events: 0)
2010-08-25 23:42:57.029 TVRec(1): Changing from None to WatchingLiveTV
2010-08-25 23:42:57.038 TVRec(1): HW Tuner: 1->1
2010-08-25 23:42:57.063 LoadFromScheduler(): Error, called from backend.
2010-08-25 23:42:57.064 AutoExpire: ERROR: Filesystem Info cache is empty, unable to calculate necessary parameters.
2010-08-25 23:42:57.093 TFW, Error: Opening file '/var/lib/mythtv/livetv/1009_20100825234257.nuv'.
			eno: Permission denied (13)
2010-08-25 23:42:57.112 TVRec(1) Error: RingBuffer '/var/lib/mythtv/livetv/1009_20100825234257.nuv' not open...
2010-08-25 23:42:57.120 TVRec(1) Error: CreateLiveTVRingBuffer(9) failed
2010-08-25 23:42:57.128 TVRec(1) Error: Failed to create RingBuffer 1
2010-08-25 23:42:57.137 TVRec(1): Changing from WatchingLiveTV to None
2010-08-25 23:42:59.032 mythbackend: Last message repeated 1 times: Autoexpire CalcParams: ERROR: Filesystem Info cache is empty, unable to calculate necessary parameters.
2010-08-25 23:42:59.038 mythbackend: Running housekeeping thread
2010-08-25 23:44:09.032 AutoExpire: ERROR: Filesystem Info cache is empty, unable to calculate necessary parameters.
2010-08-25 23:44:09.046 mythbackend: Autoexpire CalcParams: ERROR: Filesystem Info cache is empty, unable to calculate necessary parameters.
2010-08-25 23:44:09.055 AutoExpire: ERROR: Filesystem Info cache is empty, unable to determine what Recordings to expire
2010-08-25 23:44:09.062 mythbackend: Autoexpire Recording: ERROR: Filesystem Info cache is empty, unable to determine what Recordings to expire
```

I'm kind of at a loss. Any ideas?

---

### Post by ian dobson on 2010-08-27
Hi,

Could you try incrasing your tuning delays. LiveTV tries to tune to a channel and read the created file directly from the HD and if the file isn't already there it can produce strange/inaccurate error messages.

Regards
Ian Dobson

---

### Post by eljeffe on 2010-08-28
Thanks for your suggestion. I'm unsure how to do this. Can you give me a pointer?

---

### Post by ian dobson on 2010-08-29
Hi,

Start mythtv-setup, go to the tuner page and there should be an option for tuner delay, just increase it (note the value is in ms so 1000 is 1second).

Regards
Ian Dobson

---

### Post by eljeffe on 2010-08-29
My card uses the v4l driver, so it's not as easy as that. I could probably tweak the v4l driver, but I found another solution.

I have no problem with a large ring buffer on my mythtv partition. I AM able to have the recordings go to my /data partion the way I described, so sudden recording growth is no longer an issue. 

Thanks for giving me encouragement that there was an answer; I looked at it with fresher eyes and found an answer.

---

### Post by boy007 on 2011-11-27
I had same kind problem's and found this from
error log,...Filesystem Info cache is empty, unable to calculate necessary parameters.

I got everything working after changed user right's starting from
media's root directory, media/xxx and not sub media/xxx/xxxx !

chown -R mythtv:mythtv media/xxx
chmod -R 777 media/xxx

joni

---


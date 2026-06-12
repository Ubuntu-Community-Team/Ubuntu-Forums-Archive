---
title: "Mythbackend multiple instances"
date: 2014-11-19
forum: Mythbuntu
---

### Post by rbeer on 2014-11-19
I seem to have issues with multiple mythbackend processes which is messing up my system. If I look at processes running:

```

ps aux | grep backend
rmbeer    2197 86.2  1.4 422032 56900 ?        Sl   15:09  21:19 /usr/bin/myth**backend**
rmbeer    3351  0.0  0.0   4396   796 pts/0    S+   15:34   0:00 grep --color=auto [B]backend
[/B]
```

I see that mythbackend started at 15:09 and has been running 21 minutes. But if I check the mytbackend logs it shows nothing until 15:10 when it attempts to start but then closes as a process is already running. The mythbackend process that's running doesn't seem to generate any more logs.

I can start mythfrontend on one of my remote PCs (but it can be very slow at loading recordings) but I can't access mythbackend status from mythweb.

```

Nov 19 14:56:46 mythtv mythbackend: mythbackend[2845]: C CoreContext main_helpers.cpp:681 (run_backend) Backend exiting, MainServer initialization error.Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: C thread_unknown mythcommandlineparser.cpp:2596 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27.4-17-g4572a55] www$
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: C thread_unknown mythcommandlineparser.cpp:2598 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: N thread_unknown mythcommandlineparser.cpp:2600 (ConfigureLogging) Enabled verbose msgs:  general
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: N thread_unknown logging.cpp:907 (logStart) Setting Log Level to LOG_INFO
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I Logger logging.cpp:308 (run) Added logging to the console
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I CoreContext mythcorecontext.cpp:257 (Init) Assumed character encoding: en_GB.UTF-8
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtv
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network connectivity to '192.168.0.17'
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I LogForward loggingserver.cpp:1373 (forwardMessage) New Client:  (#1)
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: N CoreContext mythcorecontext.cpp:1634 (InitLocale) Setting QT default locale to EN_US
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I CoreContext mythcorecontext.cpp:1667 (SaveLocaleDefaults) Current locale EN_US
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Nov 19 15:10:09 mythtv mythbackend: mythbackend[2864]: N CoreContext main_helpers.cpp:582 (run_backend) MythBackend: Starting up as the master server.
Nov 19 15:10:10 mythtv mythbackend: mythbackend[2864]: W CoreContext recorders/dvbchannel.cpp:229 (Open) DVBChan[10](/dev/dvb/adapter1/frontend0): Opening DVB frontend device fail$
Nov 19 15:10:12  mythbackend: last message repeated 19 times
Nov 19 15:10:12 mythtv mythbackend: mythbackend[2864]: E CoreContext recorders/dvbchannel.cpp:234 (Open) DVBChan[10](/dev/dvb/adapter1/frontend0): Failed to open DVB frontend devi$
Nov 19 15:10:12 mythtv mythbackend: mythbackend[2864]: E CoreContext recorders/dvbchannel.cpp:234 (Open) DVBChan[10](/dev/dvb/adapter1/frontend0): Failed to open DVB frontend devi$
Nov 19 15:10:12 mythtv mythbackend: mythbackend[2864]: E CoreContext recorders/channelbase.cpp:1232 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device /dev/$
Nov 19 15:10:12 mythtv mythbackend: mythbackend[2864]: E CoreContext main_helpers.cpp:199 (setupTVs) Problem with capture cardsCard 10failed init
Nov 19 15:10:12 mythtv mythbackend: mythbackend[2864]: W CoreContext recorders/dvbchannel.cpp:229 (Open) DVBChan[11](/dev/dvb/adapter1/frontend0): Opening DVB frontend device fail$
Nov 19 15:10:12  mythbackend: last message repeated 19 times
Nov 19 15:10:12 mythtv mythbackend: mythbackend[2864]: E CoreContext recorders/dvbchannel.cpp:234 (Open) DVBChan[11](/dev/dvb/adapter1/frontend0): Failed to open DVB frontend devi$
Nov 19 15:10:12 mythtv mythbackend: mythbackend[2864]: E CoreContext recorders/channelbase.cpp:1232 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device /dev/$
Nov 19 15:10:12 mythtv mythbackend: mythbackend[2864]: E CoreContext main_helpers.cpp:199 (setupTVs) Problem with capture cardsCard 11failed init
Nov 19 15:10:12 mythtv mythbackend: mythbackend[2864]: W CoreContext scheduler.cpp:213 (VerifyCards) Scheduler: Listings source 'EIT' is defined, but is not attached to a card inp$
Nov 19 15:10:13 mythtv mythbackend: mythbackend[2864]: I CoreContext programinfo.cpp:2136 (CheckProgramIDAuthorities) Found 2 distinct programid authorities
Nov 19 15:10:13 mythtv mythbackend: mythbackend[2864]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'LogClean'.
Nov 19 15:10:13 mythtv mythbackend: mythbackend[2864]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'DBCleanup'.
Nov 19 15:10:13 mythtv mythbackend: mythbackend[2864]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'ThemeUpdateNotifications'.
Nov 19 15:10:13 mythtv mythbackend: mythbackend[2864]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'RecordedArtworkUpdate'.
Nov 19 15:10:13 mythtv mythbackend: mythbackend[2864]: I Scheduler mythdbcon.cpp:436 (getStaticCon) New static DB connectionSchedCon
Nov 19 15:10:13 mythtv mythbackend: mythbackend[2864]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'MythFillDB'.
Nov 19 15:10:13 mythtv mythbackend: mythbackend[2864]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'JobQueueRecover'.
Nov 19 15:10:13 mythtv mythbackend: mythbackend[2864]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'HardwareProfiler'.
Nov 19 15:10:13 mythtv mythbackend: mythbackend[2864]: I CoreContext housekeeper.cpp:655 (Start) Starting HouseKeeper.
Nov 19 15:10:13 mythtv mythbackend: mythbackend[2864]: E CoreContext serverpool.cpp:416 (listen) Failed listening on TCP 127.0.0.1:6544 - Error 8: The bound address is already in $
Nov 19 15:10:13 mythtv mythbackend: mythbackend[2864]: E CoreContext mediaserver.cpp:86 (Init) MediaServer::HttpServer Create Error
Nov 19 15:10:13 mythtv mythbackend: mythbackend[2864]: E CoreContext serverpool.cpp:416 (listen) Failed listening on TCP 127.0.0.1:6543 - Error 8: The bound address is already in $
Nov 19 15:10:13 mythtv mythbackend: mythbackend[2864]: E CoreContext mediaserver.cpp:86 (Init) MediaServer::HttpServer Create Error
Nov 19 15:10:13 mythtv mythbackend: mythbackend[2864]: E CoreContext serverpool.cpp:416 (listen) Failed listening on TCP 127.0.0.1:6543 - Error 8: The bound address is already in $
Nov 19 15:10:13 mythtv mythbackend: mythbackend[2864]: C CoreContext main_helpers.cpp:681 (run_backend) Backend exiting, MainServer initialization error.
```

---

### Post by dannyboy79 on 2014-11-19
you have multiple problems going on, first of all your capture device isn't properly setup, you can see this error
```
Opening DVB frontend device fail
```
and
```
Failed listening on TCP 127.0.0.1:6544 - Error 8: The bound address is already in
```
get your backend working correctly before trying any remote frontends. this process you see here
```
rmbeer    3351  0.0  0.0   4396   796 pts/0    S+   15:34   0:00 grep --color=auto backend
```
is not the backend, that's merely the ps aux | grep backend command itself. so if i were you i would stop the mythtv backend and run the mythtv-setup again and get your backend configured correctly first.

---

### Post by rbeer on 2014-11-20
The first 2 issues you point out in the mythbackend log (opening DVB device failed and bound address in use) are the result of the system starting mythbackend while it is already running. If I killall mythbackend and start it again it loads fine without any of these errors.
 
And if you look at the PS output again you&#8217;ll notice 2 lines. The grep line (you pointed out) but also /usr/bin/mythbackend which has been running since boot.
 
The strange thing seems to be why mythbackend seems to start on boot but nothing appears in the logs. Some time after this mythbackend will attempt to start again and this time appears in the logs but will obviously fail as it is already running.
 
Left on it&#8217;s own mythbackend is successfully recording programmes and doing other jobs like updating listings but with nothing appearing on the logs but is creating problems with sluggish frontends and no status in mythweb.
 
My current workaround is to hope it just works (which it does on some boots) or manually kill the backend and start it again as a user where everything will work fine.

---

### Post by dannyboy79 on 2014-11-20
are you running mythbuntu? it sounds like your upstart scripts are messed up and or your mythtv backend configuration. it should be attempting to start if it's already running. also, you should not have to "manually" kill it, you should be using 
```
sudo service mythbackend stop 
```
or whatever the init script is named

---

### Post by rbeer on 2014-11-20
I'm running 12.04 LTS with the mythbuntu repositories. It had been running without issue for at least 6 months, probably longer, so I'm reluctant to change a configuration without knowing the cause in case I just cause more problems. I did replace the upstart script with a new one last week when I started seeing this problem but was still getting the same problem. 

The only pattern I'm possibly seeing is that when it does an ACPI startup I don't seem to have any issues (for example this evening it's been on for several hours after starting itself for a few recordings). But when I turn on one of my frontends that does WoL it frequently has the issue I've been describing. I don't see why this should make a difference though.

---

### Post by rbeer on 2014-11-21
p.s. why does mythtv-setup say the default stop command for the backend is 'killall mythbackend' if I should be using a different method?

---

### Post by rbeer on 2014-11-21
```

sudo service mythbackend stop
mythbackend: unrecognized service

```

---

### Post by tgm4883 on 2014-11-21
you're looking for mythtv-backend

---

### Post by rbeer on 2014-11-23
Thanks tgm4883 but that didn't work either. Something fairly major was obviously wrong with my system. In addition to this it was refusing to shutdown every time as it was indefinitely 'waiting for process to end' so had to cut power, lots of messages about 'system program problem detected' but nothing in logs and a few other annoyances.

I've marked as Solved but my solution was a back-up of the database and a fresh install of ubuntu/mythtv on an SSD (a job I'd been meaning to get around to) and imported back in. 

Now everything is back and working (after the obligatory 12 hours messing around getting everything else back as I like it).

---

### Post by dannyboy79 on 2014-11-24
seems like your init scripts got messed up somehow, i'm sure we could've figured it out after many many hours of troubleshooting but in the end that's why it's always great to have an automated backup system of your mythtv database. ;)

---


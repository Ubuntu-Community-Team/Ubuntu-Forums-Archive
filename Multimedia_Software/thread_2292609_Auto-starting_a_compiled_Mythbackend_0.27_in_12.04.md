---
title: "Auto-starting a compiled Mythbackend 0.27 in 12.04"
date: 2015-08-29
forum: Multimedia Software
---

### Post by SagaciousKJB on 2015-08-29
So I had to compile my own version of MythTV in order to use a patch that fixed the electronic programming guide.  However when I installed it, I never figured out how to get it to auto-start, I wrote a little init script but it just wouldn't work.  I was just starting it through Xfce's auto-start menu but I want it to launch without me having to login to the computer.

The init script wasn't written properly with all the LSB information but it works to start and stop the service when I run it manually.  Mythbackend just doesn't want to seem to run at the time of startup with the way I'm invoking it in the script.

Script...

```
#!/bin/bash

case "$1" in
	start)
	/usr/local/bin/mythbackend -d --loglevel err --logpath /var/log/mythtv/
	;;
	stop)
	kill -KILL $(pgrep -d " " mythbackend)
	;;
esac
```

Here is a log file of when it is ran ( owned by root ) versus when it auto-starts from my Xfce login ( and runs properly )

```
kenny@AMD:~$ ls -lah /var/log/mythtv/mythbackend.*
-rw-r--r-- 1 root   root   790 Aug 29 11:39 /var/log/mythtv/mythbackend.20150829183905.1903.log
-rw-rw-r-- 1 kenny  kenny 9.0K Aug 29 11:45 /var/log/mythtv/mythbackend.20150829184027.3745.log
-rw-r--r-- 1 root   root   790 Aug 29 11:47 /var/log/mythtv/mythbackend.20150829184726.1886.log
-rw-rw-r-- 1 kenny  kenny  11K Aug 29 12:02 /var/log/mythtv/mythbackend.20150829185043.3746.log

```

```
kenny@AMD:~$ cat /var/log/mythtv/mythbackend.20150829184726.1886.log
2015-08-29 11:47:26.919704 C [1886/1886] thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) - mythbackend version: fixes/0.27 [v0.27.4-38-ga2563e1-dirty] www.mythtv.org
2015-08-29 11:47:26.919760 C [1886/1886] thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) - Qt version: compile: 4.8.1, runtime: 4.8.1
2015-08-29 11:47:26.919770 N [1886/1886] thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) - Enabled verbose msgs:  general
2015-08-29 11:47:26.932892 C [1886/1886] CoreContext main.cpp:129 (main) - Failed to init MythContext.
2015-08-29 11:47:26.933860 E [1886/1886] CoreContext mmulticastsocketdevice.cpp:62 (MMulticastSocketDevice) - MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP 
			eno: No such device (19)
```
The Xfce auto-started process has a lot more log information as I invoked it with --loglevel info, as opposed to --loglevel err in the init script
```
kenny@AMD:~$ cat /var/log/mythtv/mythbackend.20150829185043.3746.log
2015-08-29 11:50:43.410611 C [3746/3746] thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) - mythbackend version: fixes/0.27 [v0.27.4-38-ga2563e1-dirty] www.mythtv.org
2015-08-29 11:50:43.410648 C [3746/3746] thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) - Qt version: compile: 4.8.1, runtime: 4.8.1
2015-08-29 11:50:43.410652 N [3746/3746] thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) - Enabled verbose msgs:  general
2015-08-29 11:50:43.410806 N [3746/3746] thread_unknown logging.cpp:907 (logStart) - Setting Log Level to LOG_INFO
2015-08-29 11:50:43.427956 I [3746/3758] Logger logging.cpp:308 (run) - Added logging to the console
2015-08-29 11:50:43.428154 I [3746/3746] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Interrupt handler
2015-08-29 11:50:43.428166 I [3746/3746] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Terminated handler
2015-08-29 11:50:43.428174 I [3746/3746] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Segmentation fault handler
2015-08-29 11:50:43.428182 I [3746/3746] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Aborted handler
2015-08-29 11:50:43.428189 I [3746/3746] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Bus error handler
2015-08-29 11:50:43.428196 I [3746/3746] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Floating point exception handler
2015-08-29 11:50:43.428205 I [3746/3746] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Illegal instruction handler
2015-08-29 11:50:43.428214 I [3746/3746] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Real-time signal 0 handler
2015-08-29 11:50:43.428294 N [3746/3746] thread_unknown mythdirs.cpp:55 (InitializeMythDirs) - Using runtime prefix = /usr/local
2015-08-29 11:50:43.428312 N [3746/3746] thread_unknown mythdirs.cpp:68 (InitializeMythDirs) - Using configuration directory = /home/kenny/.mythtv
2015-08-29 11:50:43.428409 I [3746/3746] CoreContext mythcorecontext.cpp:257 (Init) - Assumed character encoding: en_US.UTF-8
2015-08-29 11:50:43.428904 N [3746/3746] CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) - Empty LocalHostName.
2015-08-29 11:50:43.428918 I [3746/3746] CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) - Using localhost value of AMD
2015-08-29 11:50:43.529841 I [3746/3748] LogForward loggingserver.cpp:1373 (forwardMessage) - New Client:  (#1)
2015-08-29 11:50:43.601037 I [3746/3748] LogForward loggingserver.cpp:142 (FileLogger) - Added logging to /var/log/mythtv/mythbackend.20150829185043.3746.log
2015-08-29 11:50:43.801872 N [3746/3746] CoreContext mythcorecontext.cpp:1634 (InitLocale) - Setting QT default locale to en_US
2015-08-29 11:50:43.802021 I [3746/3746] CoreContext mythcorecontext.cpp:1667 (SaveLocaleDefaults) - Current locale en_US
2015-08-29 11:50:43.802093 N [3746/3746] CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) - Reading locale defaults from /usr/local/share/mythtv//locales/en_us.xml
2015-08-29 11:50:44.308013 I [3746/3746] CoreContext schemawizard.cpp:118 (Compare) - Current MythTV Schema Version (DBSchemaVer): 1317
2015-08-29 11:50:44.308721 I [3746/3746] CoreContext mythtranslation.cpp:65 (load) - Loading en_us translation for module mythfrontend
2015-08-29 11:50:44.311208 N [3746/3746] CoreContext main_helpers.cpp:582 (run_backend) - MythBackend: Starting up as the master server.
2015-08-29 11:50:45.726617 I [3746/3893] TVRecEvent tv_rec.cpp:1269 (run) - TVRec[2]: Adjusted Scan start Sat Aug 29 18:52:30 2015
2015-08-29 11:50:45.731771 I [3746/3896] TVRecEvent tv_rec.cpp:1274 (run) - TVRec[3]: EIT scan DISABLED Mon Aug 29 18:50:45 2016
2015-08-29 11:50:45.736134 I [3746/3897] TVRecEvent tv_rec.cpp:1274 (run) - TVRec[4]: EIT scan DISABLED Mon Aug 29 18:50:45 2016
2015-08-29 11:50:45.774489 I [3746/3746] CoreContext programinfo.cpp:2136 (CheckProgramIDAuthorities) - Found 0 distinct programid authorities
2015-08-29 11:50:45.775097 I [3746/3899] Scheduler mythdbcon.cpp:436 (getStaticCon) - New static DB connectionSchedCon
2015-08-29 11:50:45.775148 I [3746/3746] CoreContext housekeeper.cpp:582 (RegisterTask) - Registering HouseKeeperTask 'LogClean'.
2015-08-29 11:50:45.775195 I [3746/3746] CoreContext housekeeper.cpp:582 (RegisterTask) - Registering HouseKeeperTask 'DBCleanup'.
2015-08-29 11:50:45.775228 I [3746/3746] CoreContext housekeeper.cpp:582 (RegisterTask) - Registering HouseKeeperTask 'ThemeUpdateNotifications'.
2015-08-29 11:50:45.775266 I [3746/3746] CoreContext housekeeper.cpp:582 (RegisterTask) - Registering HouseKeeperTask 'RecordedArtworkUpdate'.
2015-08-29 11:50:45.777589 I [3746/3746] CoreContext housekeeper.cpp:582 (RegisterTask) - Registering HouseKeeperTask 'MythFillDB'.
2015-08-29 11:50:45.777636 I [3746/3746] CoreContext housekeeper.cpp:582 (RegisterTask) - Registering HouseKeeperTask 'JobQueueRecover'.
2015-08-29 11:50:45.777657 I [3746/3746] CoreContext housekeeper.cpp:582 (RegisterTask) - Registering HouseKeeperTask 'HardwareProfiler'.
2015-08-29 11:50:45.819963 I [3746/3746] CoreContext housekeeper.cpp:655 (Start) - Starting HouseKeeper.
2015-08-29 11:50:45.824430 I [3746/3746] CoreContext serverpool.cpp:404 (listen) - Listening on TCP 127.0.0.1:6544
2015-08-29 11:50:45.824555 I [3746/3746] CoreContext serverpool.cpp:404 (listen) - Listening on TCP [::1]:6544
2015-08-29 11:50:45.824672 I [3746/3746] CoreContext serverpool.cpp:404 (listen) - Listening on TCP [fe80::201:29ff:fea6:24b0%eth0]:6544
2015-08-29 11:50:45.828033 N [3746/3746] CoreContext mediaserver.cpp:168 (Init) - MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2015-08-29 11:50:45.828048 I [3746/3746] CoreContext main_helpers.cpp:668 (run_backend) - Main::Registering HttpStatus Extension
2015-08-29 11:50:45.830119 I [3746/3746] CoreContext serverpool.cpp:404 (listen) - Listening on TCP 127.0.0.1:6543
2015-08-29 11:50:45.830231 I [3746/3746] CoreContext serverpool.cpp:404 (listen) - Listening on TCP [::1]:6543
2015-08-29 11:50:45.830337 I [3746/3746] CoreContext serverpool.cpp:404 (listen) - Listening on TCP [fe80::201:29ff:fea6:24b0%eth0]:6543
2015-08-29 11:50:46.141032 N [3746/3746] CoreContext autoexpire.cpp:264 (CalcParams) - AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2015-08-29 11:50:49.429624 I [3746/3899] Scheduler scheduler.cpp:2140 (HandleReschedule) - Reschedule requested for MATCH 0 0 0 - SchedulerInit
2015-08-29 11:50:50.404336 I [3746/3899] Scheduler scheduler.cpp:2253 (HandleReschedule) - Scheduled 0 items in 0.9 = 0.79 match + 0.14 check + 0.01 place
2015-08-29 11:50:50.405563 I [3746/3899] Scheduler scheduler.cpp:2320 (HandleRunSchedulerStartup) - Scheduler: Seem to be woken up by USER
2015-08-29 11:52:05.142197 N [3746/3900] Expire autoexpire.cpp:264 (CalcParams) - AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2015-08-29 11:52:30.737572 I [3746/3893] TVRecEvent tv_rec.cpp:1423 (run) - TVRec[2]: StartActiveScan eitTransportTimeout is 300 
2015-08-29 11:52:32.388718 E [3746/3893] TVRecEvent recorders/dvbchannel.cpp:1026 (GetSignalStrength) - DVBChan[2](/dev/dvb/adapter0/frontend0): Getting Frontend signal strength failed.
			eno: Invalid argument (22)
2015-08-29 11:52:32.388745 W [3746/3893] TVRecEvent recorders/dvbsignalmonitor.cpp:91 (DVBSignalMonitor) - DVBSigMon[2](/dev/dvb/adapter0/frontend0): Cannot measure Signal Strength
			eno: Invalid argument (22)
2015-08-29 11:52:32.389883 E [3746/3893] TVRecEvent recorders/dvbchannel.cpp:1055 (GetSNR) - DVBChan[2](/dev/dvb/adapter0/frontend0): Getting Frontend signal/noise ratio failed.
			eno: Invalid argument (22)
2015-08-29 11:52:32.389900 W [3746/3893] TVRecEvent recorders/dvbsignalmonitor.cpp:93 (DVBSignalMonitor) - DVBSigMon[2](/dev/dvb/adapter0/frontend0): Cannot measure S/N
			eno: Invalid argument (22)
2015-08-29 11:57:44.464420 I [3746/3899] Scheduler scheduler.cpp:2140 (HandleReschedule) - Reschedule requested for MATCH 0 1 3 2015-08-30T05:30:00Z EITScanner
2015-08-29 11:57:44.498705 I [3746/3899] Scheduler scheduler.cpp:2253 (HandleReschedule) - Scheduled 0 items in 0.0 = 0.01 match + 0.00 check + 0.00 place
2015-08-29 11:57:45.464848 E [3746/3893] TVRecEvent recorders/dvbchannel.cpp:1026 (GetSignalStrength) - DVBChan[2](/dev/dvb/adapter0/frontend0): Getting Frontend signal strength failed.
			eno: Invalid argument (22)
2015-08-29 11:57:45.464878 W [3746/3893] TVRecEvent recorders/dvbsignalmonitor.cpp:91 (DVBSignalMonitor) - DVBSigMon[2](/dev/dvb/adapter0/frontend0): Cannot measure Signal Strength
			eno: Invalid argument (22)
2015-08-29 11:57:45.466006 E [3746/3893] TVRecEvent recorders/dvbchannel.cpp:1055 (GetSNR) - DVBChan[2](/dev/dvb/adapter0/frontend0): Getting Frontend signal/noise ratio failed.
			eno: Invalid argument (22)
2015-08-29 11:57:45.466024 W [3746/3893] TVRecEvent recorders/dvbsignalmonitor.cpp:93 (DVBSignalMonitor) - DVBSigMon[2](/dev/dvb/adapter0/frontend0): Cannot measure S/N
			eno: Invalid argument (22)
2015-08-29 11:57:46.756726 E [3746/4030] SignalMonitor recorders/dvbchannel.cpp:1026 (GetSignalStrength) - DVBChan[2](/dev/dvb/adapter0/frontend0): Getting Frontend signal strength failed.
			eno: Invalid argument (22)
2015-08-29 12:02:57.502724 I [3746/3899] Scheduler scheduler.cpp:2140 (HandleReschedule) - Reschedule requested for MATCH 0 1 2 2015-08-30T23:00:00Z EITScanner
2015-08-29 12:02:57.540053 I [3746/3899] Scheduler scheduler.cpp:2253 (HandleReschedule) - Scheduled 0 items in 0.0 = 0.01 match + 0.00 check + 0.00 place
2015-08-29 12:02:58.464712 E [3746/3893] TVRecEvent recorders/dvbchannel.cpp:1026 (GetSignalStrength) - DVBChan[2](/dev/dvb/adapter0/frontend0): Getting Frontend signal strength failed.
			eno: Invalid argument (22)
2015-08-29 12:02:58.464729 W [3746/3893] TVRecEvent recorders/dvbsignalmonitor.cpp:91 (DVBSignalMonitor) - DVBSigMon[2](/dev/dvb/adapter0/frontend0): Cannot measure Signal Strength
			eno: Invalid argument (22)
2015-08-29 12:02:58.465860 E [3746/3893] TVRecEvent recorders/dvbchannel.cpp:1055 (GetSNR) - DVBChan[2](/dev/dvb/adapter0/frontend0): Getting Frontend signal/noise ratio failed.
			eno: Invalid argument (22)
2015-08-29 12:02:58.465869 W [3746/3893] TVRecEvent recorders/dvbsignalmonitor.cpp:93 (DVBSignalMonitor) - DVBSigMon[2](/dev/dvb/adapter0/frontend0): Cannot measure S/N
			eno: Invalid argument (22)
```

So I really don't know what I'm doing wrong pretty much lost in the dark here, the usual packages in the repository setup the auto-starting perfectly but since I need to use a patch on a custom compiled version I'm having a little trouble figuring out how to do it.  The patch I need is pretty important because otherwise it mismatches the description and title for a program--pretty annoying.  It's because I'm using ATSC and picking up the over-the-air programming info.  Otherwise I would just use the version in the respos.

---

### Post by blm-ubunet on 2015-08-29
Why not just modify the upstart job script ?
The default ubuntu mythtv init process uses upstart (AFAIK).
The mythtv wiki has example working upstart scripts (& systemd).
[https://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](https://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)

The tricky mythbuntu setup wraps the real executable with a auto-respawning script so the actual backend program is renamed "mythbackend.real". IMO this is unnecessary.

The normal configuration is to run mythbackend as user "mythtv" (with its own /home/mythtv/.mythtv/config.xml).

You do realize you can use the mythbuntu ppa (for mythtv) on your ubuntu flavour without using mythbuntu xfce?

---


---
title: "mythfilldatabase xmltv error code 13"
date: 2012-11-09
forum: Mythbuntu
---

### Post by tez1982 on 2012-11-09
Basically I've never managed to get mythfilldatabase and xmltv to work properly.

If I execute mythfilldatabase manually it runs fine, however every time I let it run automatically I get error code 13 and no EPG data (very common I know).

I've symlinked /home/media/.mythtv/usb.xmltv and /home/mythtv/.mythtv/usb.xmltv - again this didn't help. The first file is the one mythfilldatabase is using.

I tried setting a cron job to run mythfilldatabase manually but this fails with error code 13 as well.

After a lot of googling I'm getting a bit stuck - have I missed anything obvious?

System:
Mythbuntu 12.04
Mythtv 0.26
Nanostick 290e

---

### Post by nickrout on 2012-11-09
> **tez1982 said:**
> Basically I've never managed to get mythfilldatabase and xmltv to work properly.

If I execute mythfilldatabase manually it runs fine, however every time I let it run automatically I get error code 13 and no EPG data (very common I know).

I've symlinked /home/media/.mythtv/usb.xmltv and /home/mythtv/.mythtv/usb.xmltv - again this didn't help. The first file is the one mythfilldatabase is using.

I tried setting a cron job to run mythfilldatabase manually but this fails with error code 13 as well.

After a lot of googling I'm getting a bit stuck - have I missed anything obvious?

System:
Mythbuntu 12.04
Mythtv 0.26
Nanostick 290e

Yes you have missed posting a full log of a session that works and one that doesn't.

---

### Post by tez1982 on 2012-11-12
Successful manual run

```
2012-11-12 17:52:03.685459 C  mythfilldatabase version: fixes/0.26 [v0.26.0-29-gbcd34da] www.mythtv.org
2012-11-12 17:52:03.685481 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2012-11-12 17:52:03.685484 N  Enabled verbose msgs:  general
2012-11-12 17:52:03.685497 N  Setting Log Level to LOG_INFO
2012-11-12 17:52:03.685835 I  Added logging to the console
2012-11-12 17:52:03.686218 I  Setup Interrupt handler
2012-11-12 17:52:03.686229 I  Setup Terminated handler
2012-11-12 17:52:03.686237 I  Setup Segmentation fault handler
2012-11-12 17:52:03.686243 I  Setup Aborted handler
2012-11-12 17:52:03.686250 I  Setup Bus error handler
2012-11-12 17:52:03.686256 I  Setup Floating point exception handler
2012-11-12 17:52:03.686263 I  Setup Illegal instruction handler
2012-11-12 17:52:03.686276 I  Setup Real-time signal 0 handler
2012-11-12 17:52:03.686308 N  Using runtime prefix = /usr
2012-11-12 17:52:03.686322 N  Using configuration directory = /home/media/.mythtv
2012-11-12 17:52:03.686382 I  Assumed character encoding: en_GB.UTF-8
2012-11-12 17:52:03.686966 N  Empty LocalHostName.
2012-11-12 17:52:03.686973 I  Using localhost value of mediacentre
2012-11-12 17:52:03.687007 I  Testing network connectivity to '192.168.1.102'
2012-11-12 17:52:03.687465 I  Starting process manager
2012-11-12 17:52:03.688332 I  Starting IO manager (read)
2012-11-12 17:52:03.688353 I  Starting process signal handler
2012-11-12 17:52:03.688472 I  Starting IO manager (write)
2012-11-12 17:52:03.818860 N  Setting QT default locale to en_GB
2012-11-12 17:52:03.819001 I  Current locale en_GB
2012-11-12 17:52:03.819082 N  Reading locale defaults from /usr/share/mythtv//locales/en_gb.xml
2012-11-12 17:52:03.833115 I  Loading en_gb translation for module mythfrontend
2012-11-12 17:52:03.836733 I  Current MythTV Schema Version (DBSchemaVer): 1307
2012-11-12 17:52:03.906334 I  Updating source #1 (usb) with grabber tv_grab_uk_rt
2012-11-12 17:52:03.907056 I  Found 46 channels for source 1 which use grabber
2012-11-12 17:52:03.915511 I  Added logging to mythlogserver at TCP:35327
2012-11-12 17:52:04.389941 I  Grabber has capabilities: baseline manualconfig cache preferredmethod tkconfig apiconfig lineups
2012-11-12 17:52:04.890704 I  Grabber prefers method: allatonce
2012-11-12 17:52:04.891866 I  XMLTV config file is: /home/media/.mythtv/usb.xmltv
2012-11-12 17:53:31.977317 I  IconData: Updating icons for sourceid: 1
2012-11-12 17:54:35.327351 I  Updated programs: 3716 Unchanged programs: 13335
2012-11-12 17:54:35.452018 N  Data fetching complete.
2012-11-12 17:54:35.452056 I  Adjusting program database end times.
2012-11-12 17:54:35.698338 I      0 replacements made
2012-11-12 17:54:35.698352 I  Marking generic episodes.
2012-11-12 17:54:35.785285 I      Found 307
2012-11-12 17:54:35.785347 I  Extending non-unique programids with multiple parts.
2012-11-12 17:54:35.813483 I      Found 0
2012-11-12 17:54:35.813539 I  Marking repeats.
2012-11-12 17:54:35.869271 I      Found 0
2012-11-12 17:54:35.869278 I  Unmarking new episode rebroadcast repeats.
2012-11-12 17:54:35.921739 I      Found 0
2012-11-12 17:54:36.198785 I  Marking episode first showings.
2012-11-12 17:54:36.929086 I      Found 10687
2012-11-12 17:54:36.929102 I  Marking episode last showings.
2012-11-12 17:54:37.711924 I      Found 9729
2012-11-12 17:54:37.715790 I
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2012-11-12 17:54:37.721112 I  MythCoreContext: Connecting to backend server: 192.168.1.102:6543 (try 1 of 1)
2012-11-12 17:54:37.722206 I  Using protocol version 75
2012-11-12 17:54:37.724574 I  Received remote 'Clear Cache' request
2012-11-12 17:54:37.724745 N  mythfilldatabase run complete.

```

Unsuccessful Automatic run

```
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythfilldatabase version: fixes/0.26 [v0.2$
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I Logger logging.cpp:306 (run) Added logging to the console
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythfilldatabase version: fixes/0.26 [v0.2$
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I Logger logging.cpp:306 (run) Added logging to the console
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of mediacentre
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext mythcontext.cpp:682 (TestDBconnection) Testing network connectivity to '192.168.1.102'
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to en_GB
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale en_GB
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locale$
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext mythtranslation.cpp:65 (load) Loading en_gb translation for module mythfrontend
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1307
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext filldata.cpp:594 (Run) Updating source #1 (usb) with grabber tv_grab_uk_rt
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext filldata.cpp:608 (Run) Found 46 channels for source 1 which use grabber
Nov 12 17:29:40 mediacentre mythlogserver: mythfilldatabase[2604]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Nov 12 17:29:41 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext filldata.cpp:666 (Run) Grabber has capabilities: baseline manualconfig cache preferredmethod tk$
Nov 12 17:29:41 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext filldata.cpp:689 (Run) Grabber prefers method: allatonce
Nov 12 17:29:41 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext filldata.cpp:396 (GrabData) XMLTV config file is: /home/mythtv/.mythtv/usb.xmltv
Nov 12 17:29:42 mediacentre mythlogserver: mythfilldatabase[2604]: E CoreContext filldata.cpp:465 (GrabData) FillData: XMLTV grabber returned error code 13
Nov 12 17:29:42 mediacentre mythlogserver: mythfilldatabase[2604]: E CoreContext xmltvparser.cpp:605 (parseFile) Error in 1:1: unexpected end of file
Nov 12 17:29:42 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext icondata.cpp:164 (UpdateSourceIcons) IconData: Updating icons for sourceid: 1
Nov 12 17:29:42 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext filldata.cpp:338 (GrabDataFromFile) No programs found in data.
Nov 12 17:29:42 mediacentre mythlogserver: mythfilldatabase[2604]: E CoreContext main.cpp:497 (main) Failed to fetch some program info
Nov 12 17:29:42 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext main.cpp:538 (main) Adjusting program database end times.
Nov 12 17:29:42 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext main.cpp:544 (main)     0 replacements made
Nov 12 17:29:42 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext main.cpp:549 (main) Marking generic episodes.
Nov 12 17:29:42 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext main.cpp:561 (main)     Found 0
Nov 12 17:29:42 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext main.cpp:567 (main) Extending non-unique programids with multiple parts.
Nov 12 17:29:42 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext main.cpp:618 (main)     Found 0
Nov 12 17:29:42 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext main.cpp:567 (main) Extending non-unique programids with multiple parts.
Nov 12 17:29:42 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext main.cpp:618 (main)     Found 0
Nov 12 17:29:42 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext main.cpp:623 (main) Marking repeats.
Nov 12 17:29:42 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext main.cpp:637 (main)     Found 0
Nov 12 17:29:42 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext main.cpp:639 (main) Unmarking new episode rebroadcast repeats.
Nov 12 17:29:42 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext main.cpp:649 (main)     Found 0
Nov 12 17:29:43 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext main.cpp:661 (main) Marking episode first showings.
Nov 12 17:29:43 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext main.cpp:691 (main)     Found 9623
Nov 12 17:29:43 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext main.cpp:693 (main) Marking episode last showings.
Nov 12 17:29:44 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext main.cpp:723 (main)     Found 8769
Nov 12 17:29:44 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext main.cpp:751 (main) #012===============================================================#012| At$
Nov 12 17:29:44 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext mythcorecontext.cpp:375 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 1$
Nov 12 17:29:44 mediacentre mythlogserver: mythfilldatabase[2604]: I CoreContext mythcorecontext.cpp:1191 (CheckProtoVersion) Using protocol version 75
Nov 12 17:29:44 mediacentre mythlogserver: mythfilldatabase[2604]: N CoreContext main.cpp:761 (main) mythfilldatabase run complete.

```

---

### Post by nickrout on 2012-11-12
I think this is a xmltv problem as the grabber is not getting any data. Try looking at the code of your grabber and see what is causing it to generate error 13.

---


---
title: "Tuners are often not detected"
date: 2014-10-25
forum: Mythbuntu
---

### Post by mikitz on 2014-10-25
This is the latest mythbuntu 14.04
The tuners are often not detected. Sometimes a reboot fixes this, but restarting mythtv-backend doesn't seem to fix this! After starting and stopping mythtv-backend waiting a while and restarting it, the tuners are still not detected correctly.

Here is a copy-paste of the mythtvbackend.log of what I think is the relevant section, you can see I stop and then start the mythtv-backend service.

Any hints or things to try are greatly appreciated.

```

Oct 25 16:14:24 mythtv mythbackend: mythbackend[2586]: N CoreContext main_helpers.cpp:706 (run_backend) MythBackend exiting
Oct 25 16:14:24 mythtv mythbackend: mythbackend[2586]: I CoreContext mythcontext.cpp:1194 (~MythContext) Waiting for threads to exit.
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27.4-5-gc4de5c5] www.mythtv.org
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.6, runtime: 4.8.6
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: N thread_unknown logging.cpp:907 (logStart) Setting Log Level to LOG_INFO
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I Logger logging.cpp:308 (run) Added logging to the console
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext mythcorecontext.cpp:257 (Init) Assumed character encoding: en_CA.UTF-8
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtv
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: N CoreContext mythcorecontext.cpp:1634 (InitLocale) Setting QT default locale to EN_US
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext mythcorecontext.cpp:1667 (SaveLocaleDefaults) Current locale EN_US
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: N CoreContext main_helpers.cpp:582 (run_backend) MythBackend: Starting up as the master server.
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: W CoreContext recorders/dvbchannel.cpp:229 (Open) DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.#012#011#011#011eno: No such file or directory (2)
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: E CoreContext recorders/dvbchannel.cpp:234 (Open) DVBChan[1](/dev/dvb/adapter0/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: E CoreContext recorders/channelbase.cpp:1232 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: E CoreContext main_helpers.cpp:199 (setupTVs) Problem with capture cardsCard 1failed init
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: W CoreContext recorders/dvbchannel.cpp:229 (Open) DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.#012#011#011#011eno: No such file or directory (2)
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: E CoreContext recorders/dvbchannel.cpp:234 (Open) DVBChan[2](/dev/dvb/adapter0/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: E CoreContext recorders/channelbase.cpp:1232 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: E CoreContext main_helpers.cpp:199 (setupTVs) Problem with capture cardsCard 2failed init
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: W CoreContext recorders/dvbchannel.cpp:229 (Open) DVBChan[3](/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.#012#011#011#011eno: No such file or directory (2)
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: E CoreContext recorders/dvbchannel.cpp:234 (Open) DVBChan[3](/dev/dvb/adapter1/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: E CoreContext recorders/channelbase.cpp:1232 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter1/frontend0
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: E CoreContext main_helpers.cpp:199 (setupTVs) Problem with capture cardsCard 3failed init
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: W CoreContext recorders/dvbchannel.cpp:229 (Open) DVBChan[4](/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.#012#011#011#011eno: No such file or directory (2)
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: E CoreContext recorders/dvbchannel.cpp:234 (Open) DVBChan[4](/dev/dvb/adapter1/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: E CoreContext recorders/channelbase.cpp:1232 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter1/frontend0
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: E CoreContext main_helpers.cpp:199 (setupTVs) Problem with capture cardsCard 4failed init
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: W CoreContext main_helpers.cpp:214 (setupTVs) MythBackend: No valid capture cards are defined in the database.
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext programinfo.cpp:2136 (CheckProgramIDAuthorities) Found 1 distinct programid authorities
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I Scheduler mythdbcon.cpp:436 (getStaticCon) New static DB connectionSchedCon
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'LogClean'.
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'DBCleanup'.
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'ThemeUpdateNotifications'.
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'RecordedArtworkUpdate'.
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'MythFillDB'.
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'JobQueueRecover'.
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'HardwareProfiler'.
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext housekeeper.cpp:655 (Start) Starting HouseKeeper.
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP 127.0.0.1:6544
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP [::1]:6544
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP [fe80::76d4:35ff:fe5d:51f5%eth1]:6544
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: N CoreContext mediaserver.cpp:168 (Init) MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext main_helpers.cpp:668 (run_backend) Main::Registering HttpStatus Extension
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP 127.0.0.1:6543
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP [::1]:6543
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP [fe80::76d4:35ff:fe5d:51f5%eth1]:6543
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I LogForward loggingserver.cpp:1373 (forwardMessage) New Client:  (#1)
Oct 25 16:14:37 mythtv mythbackend: mythbackend[2635]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Oct 25 16:14:40 mythtv mythbackend: mythbackend[2635]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - SchedulerInit
Oct 25 16:14:40 mythtv mythbackend: mythbackend[2635]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 25 items in 0.0 = 0.01 match + 0.00 check + 0.02 place
Oct 25 16:14:40 mythtv mythbackend: mythbackend[2635]: I Scheduler scheduler.cpp:2319 (HandleRunSchedulerStartup) Scheduler: Seem to be woken up by USER
Oct 25 16:14:45 mythtv mythbackend: mythbackend[2635]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Playback
Oct 25 16:14:45 mythtv mythbackend: mythbackend[2635]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: mythtv as a client (events: 0)
Oct 25 16:14:45 mythtv mythbackend: mythbackend[2635]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Monitor
Oct 25 16:14:45 mythtv mythbackend: mythbackend[2635]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: mythtv as a client (events: 1)
mikitzel@mythtv:/var/log/mythtv$ 


```

---

### Post by Gillingham on 2014-10-26
Hi Mikitz

Can you give more details about your set-up please?  Especially what card or cards you are using and what you get if you run ```
ls /dev/dvb/
```.

David

---

### Post by mikitz on 2014-10-28
Sure. Sorry for the late reply.
Two tuners, they are both Hauppauge 1250's. On reboot there is a 50/50 chance they get detected. Either both or none get detected.

```

~$ ls /dev/dvb/
adapter0  adapter1

```

---

### Post by mikitz on 2014-10-28
More info via lspci

```

01:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
....
03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)

```

---

### Post by dannyboy79 on 2014-10-29
i would suggest trying them in different pci slots. the driver has been in the linux kernel since 2.6.27 so that's not the issue, i'm betting it's a hardware issue. how many PCI slots does your motherboard have? do they both use the same IRQ?

---

### Post by mikitz on 2014-10-29
Ok I only have remote access at the moment, the machine is at my parents'... I'll try switching slots in the next couple days. They are just keeping it on all the time for now which.

One card is in the single PCI-e slot, the other is in a regular PCI slot.

If it helps, it is a Gigabyte F2A78M-D3H motherboard with one PCI-express slot and 2 regular PCI slots.

---

### Post by mikitz on 2014-11-01
Solved! The machine is set for [ACPI wakeup]("https://www.mythtv.org/wiki/ACPI_Wakeup") however the nvram wake-up startup command was not empty as recommended in the link. This caused the system to continuously reboot and upon reboot the tuners were often not detected. Clearing the nvram wake-up startup command (accessed from mythwelcome --setup) fixed the reboot problem and the tuners are always detected now. Thanks for all the replies and help. They got me on the right track anyhow.

---

### Post by gedakc on 2014-11-27
Thank you Mikitz for posting your solution to the problem.

Was there a log or some other evidence that you looked at to confirm the continuous reboot problem/theory?

I recently encountered a similar problem with some Mythbuntu 14.04.1 PVRs infrequently failing to recognize two Hauppauge HVR-2250 cards.  I also have ACPI wakeup configured; however, in my case the failure to detect tuners occurred very infrequently (once or twice a month).  Recently I [Migrated from Mythbuntu 12.04.2 with MythTV 0.25 to Mythbuntu 14.04.1 with MythTV 0.27+fixes]("http://gedakc.users.sourceforge.net/display-doc.php?name=pvr-mythbuntu1204-to-1404").

I ran **mythwelcome --setup** and discovered that I had a space character in the **nvram-wakeup Restart command** entry.  I have deleted this space character to see if it fixes the problem.  I too support family members with two similar PVRs.

Since the failure to detect tuners occurred very infrequently, it will take a few months of solid PVR operation before I will feel confident that the problem is solved.

Thanks again for sharing your experience and how you resolved the problem.  :-)

Sincerely,
Curtis Gedak
(Maintainer of GParted)

---

### Post by Ubu_Fester on 2014-12-04
Sorry, I have no answers to this problem but did want to report that this happened to me last week.  

I have a Haup 1600 and 2250 (dual) tuners running on mythbuntu 12.04.2 (24/7).  Last Saturday, I made some edits to the backend setup and exited (no reboot).  Sunday I didn't get any of the football games recorded -- but 1-2 other shows did record.  My theory is that the 2250 tuner went dark and the 1600 continued to work -- which is why most (but not all) recordings failed over a 24 hour period (Sat-Sun).

I rebooted and then all was fine again.  This is the first time that this has happened.

---


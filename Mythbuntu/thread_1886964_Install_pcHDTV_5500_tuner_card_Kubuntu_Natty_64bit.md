---
title: "Install pcHDTV 5500 tuner card Kubuntu Natty 64bit"
date: 2011-11-25
forum: Mythbuntu
---

### Post by Shabakthanai on 2011-11-25
KDE 4.7.2
Kubuntu 11.04
Mythbuntu

Configuring 'Mythbuntu Control Center' does not reveal a TV or program configuration.

Configuring 'Myth TV Viewer' does not reveal a TV or program configuration.

It is as though the drivers for the TV card were not installed or I have missing needed packages.

I cannot find any applications in the applications menu other than the two above described which appear to relate to TV or multimedia applications.

I believe I have read everything posted about the subject, but am unable to understand what I am doing wrong.

Does anyone have suggestions?  Thanks!

---

### Post by klc5555 on 2011-11-26
The drivers for the 5500 should have been installed with the DVB kernel modules at the main OS install. Output from dmesg at a prompt should give you information as to whether the OS found the card and loaded its driver at boot. The 5500 comes as close to working out-of-the-box as anything does in Linux, and should require only a minimum of Mythtv-specific configuration when you set up the Mythtv backend. 

You need to have at least the following 3 packages installed: mythtv-common, mythtv-backend, mythtv-frontend (plus their dependencies) to get a minimal Mythtv setup running. Extra themes, plugins, and other gewgaws can all be added later. So check your package manager to make sure at least these three packages are installed.

When you have (at least) these three packages installed, you should be able to run 'sudo mythtv-setup' from a prompt and begin configuring the mythtv backend. The relevant guides for this include mythtv's own manual [http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index)   and Mythbuntu's somewhat outdated manual [http://mythbuntu.org/wiki/installation-guide](http://mythbuntu.org/wiki/installation-guide)

---

### Post by Shabakthanai on 2011-11-26
> **klc5555 said:**
> The drivers for the 5500 should have been installed with the DVB kernel modules at the main OS install. Output from dmesg at a prompt should give you information as to whether the OS found the card and loaded its driver at boot. The 5500 comes as close to working out-of-the-box as anything does in Linux, and should require only a minimum of Mythtv-specific configuration when you set up the Mythtv backend. 

>Drivers appear to be properly installed.  Dmesg showed them, so apparently the OS has found and loaded the drivers.

You need to have at least the following 3 packages installed: mythtv-common, mythtv-backend, mythtv-frontend (plus their dependencies) to get a minimal Mythtv setup running. Extra themes, plugins, and other gewgaws can all be added later. So check your package manager to make sure at least these three packages are installed.

>All three packages are installed.

When you have (at least) these three packages installed, you should be able to run 'sudo mythtv-setup' from a prompt and begin configuring the mythtv backend. The relevant guides for this include mythtv's own manual [http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index)   and Mythbuntu's somewhat outdated manual [http://mythbuntu.org/wiki/installation-guide](http://mythbuntu.org/wiki/installation-guide)

>I followed your links and believe I configured the application properly.  I have run mythfilldatabase.  Much information scrolls down, but before I can read any error messages, if any, the window leaves the screen.

>Then, Applications>multimedia>MythTV Viewer appears (I have been here many times always ending in failure), I select Language English (United States), then 'save'; the next window says   No   I click on 'OK', then
                                             UPnP
                                              OK
the following error message appears:

MythTV could not connect tpo the database.  Please verify your database settings below.  Required fields are marked with an asterisk (*).

The only thing having an '*' is the entry for 'Hostname'.  I enter 192.168.0.111 and leave everything else as predefined.  It is all that is required by the application.  I click 'Next' and the following appears:

'Use custom identifier for frontend preferences' and 'Enable database server wakeup'.  I do not have any idea what 'my-unique-identifier-gos-here'is, so I do not check that box.  Under 'Enable database server wakeup', I check this one, set 'Reconnect time:  to 10 and leave Retry attempts: @ 5.  I set wake command to 'sudo /etc/init.d/mysql restart.  It is an example they provided, but I am not sure it is correct.  Then I select 'Finish'.  The next window says   Cannot.  I am then returned to 
                                           OK
the second page of Database Configuration 1/2 with all default entries as before.  It is a loop I am unable to cure.  Does this help your diagnosis of my problem?  

Applications I installed relative to upnp are as follows:  libnet-upnp-perl, upnp-inspector, libhupnp0, midiatomb, libupnp3, mediatomb-daemon, mediatomb-common, linux-igd, gupnp-tools, libupnp4, python-coherence, cagibi, and libgupnp-1.0-3.

When I attempt to open Midia Tomb UI, it is disabled.  It says to check your configuration, however does not provide a preferences or configuration tab to make any changes.  I am not experienced enough to continue without specific help.  Thanks if you are willing to continue having patience with me and continue to help.

---

### Post by klc5555 on 2011-11-26
With only one mythbackend and one mythfrontend and those on a single machine, the IP address for the backend and frontend should should probably both be left at 127.0.0.1 or localhost. The user will be mythtv, the password the machine-supplied one of random characters (not 'mythtv') found in /home/mythtv/.mythtv/mysql.txt (or /home/[your_user]/.mythtv/mysql.txt

You need to confirm that you have completed the backend setup (general setup, tuner cards, videosources, input connections, and the channel scan in input connections) and that mythbackend has, after completing this configuration, and exiting the setup, been started and is in fact running. Though mythbackend can be started by the user with 'sudo mythbackend -d' or similar, if your setup is completed correctly, mythbackend will normally be started in its appropriate place by a startup script after the machine is rebooted. 

Only when the mythbackend daemon is running will mythfrontend, which is where you're getting your connection error loop from, be able to connect. If mythbackend is not running, this will need to be fixed before mythfrontend can connect to it. The mythbackend log under /var/log/mythtv/ can be checked for errors.

As far as your other UPnP applications, I don't run them so I can't comment on why they specifically do what they do.

---

### Post by Shabakthanai on 2011-11-26
> **klc5555 said:**
> With only one mythbackend and one mythfrontend and those on a single machine, the IP address for the backend and frontend should should probably both be left at 127.0.0.1 or localhost. The user will be mythtv, the password the machine-supplied one of random characters (not 'mythtv') found in /home/mythtv/.mythtv/mysql.txt (or /home/[your_user]/.mythtv/mysql.txt

>I have been working this problem for quite a while.  I tried Hostname 'localhost' with Password: (blank).  I also tried same with 127.0.0.1 and failed that way.  In both cases it said a password was required, however there was nothing in either file you mentioned above, so I did not know what to enter there.

You need to confirm that you have completed the backend setup (general setup, tuner cards, videosources, input connections, and the channel scan in input connections) and that mythbackend has, after completing this configuration,

>How do I confirm?

 and exiting the setup, been started and is in fact running. Though mythbackend can be started by the user with 'sudo mythbackend -d' or similar, if your setup is completed correctly, mythbackend will normally be started in its appropriate place by a startup script after the machine is rebooted.

>I 'sudo mythbackend -d' and got the following:

steven@Yeshuah:~$ sudo mythbackend -d
[sudo] password for steven: 
2011-11-26 20:40:04.388 mythbackend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-11-26 20:40:04.389 Using runtime prefix = /usr
2011-11-26 20:40:04.389 Using configuration directory = /home/steven/.mythtv
steven@Yeshuah:~$ 2011-11-26 20:40:04.400 Empty LocalHostName.
2011-11-26 20:40:04.400 Using localhost value of Yeshuah
2011-11-26 20:40:04.415 New DB connection, total: 1
2011-11-26 20:40:04.417 Connected to database 'mythconverg' at host: localhost
2011-11-26 20:40:04.421 Closing DB connection named 'DBManager0'
2011-11-26 20:40:04.421 Connected to database 'mythconverg' at host: localhost
2011-11-26 20:40:04.422 Current locale EN_US
2011-11-26 20:40:04.423 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-11-26 20:40:04.429 Current MythTV Schema Version (DBSchemaVer): 1264
2011-11-26 20:40:04.431 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-11-26 20:40:04.991 MythSocket(7fe93c010c20:17): Unable to lookup: 192,168.0.111
2011-11-26 20:40:04.992 MythBackend: Running as a slave backend.
2011-11-26 20:40:04.993 mythbackend: MythBackend started as a slave backend
2011-11-26 20:40:04.994 New DB connection, total: 2
2011-11-26 20:40:04.994 Connected to database 'mythconverg' at host: localhost
2011-11-26 20:40:04.995 TVRec(7) Error: Problem finding starting channel, setting to default of '3'.
2011-11-26 20:40:04.998 ChannelBase(7) Error: InitializeInputs(): 
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?
2011-11-26 20:40:04.999 mythbackend: Problem with capture cards: Card 7 failed init
2011-11-26 20:40:05.000 TVRec(8) Error: Problem finding starting channel, setting to default of '3'.
2011-11-26 20:40:05.000 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.050 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.100 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.150 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.201 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.251 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.301 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.351 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.401 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.451 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.502 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.552 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.602 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.652 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.702 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.753 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.803 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.853 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.903 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.953 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2011-11-26 20:40:05.953 DVBChan(8:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2011-11-26 20:40:05.954 mythbackend: Problem with capture cards: Card 8 failed init
2011-11-26 20:40:05.954 MythBackend, Warning: No valid capture cards are defined in the database.
2011-11-26 20:40:05.955 mythbackend: No capture cards are defined: This backend will not be used for recording.

Is the tuner the capture card?  I just purchased it. It is mentioned here:

trim.....
sb-audio
[   15.536496] tda9887 1-0043: creating new instance
[   15.536500] tda9887 1-0043: tda988[5/6/7] found
[   15.539484] tuner 1-0061: chip found @ 0xc2 (cx88[0])
[   15.540645] cx2388x alsa driver version 0.0.8 loaded
[   15.598407] tuner-simple 1-0061: creating new instance
[   15.598410] tuner-simple 1-0061: type set to 64 (LG TDVS-H06xF)
[   15.640038] Registered IR keymap rc-rc5-hauppauge-new
[   15.640146] input: cx88 IR (pcHDTV HD5500 HDTV) as /devices/pci0000:00/0000:00:08.0/0000:01:09.0/rc/rc0/input5
[   15.640219] rc0: cx88 IR (pcHDTV HD5500 HDTV) as /devices/pci0000:00/0000:00:08.0/0000:01:09.0/rc/rc0
[   15.640299] rc rc0: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 0
[   15.640306] cx88[0]/0: found at 0000:01:09.0, rev: 5, irq: 17, latency: 32, mmio: 0xf8000000
[   15.640380] cx88[0]/0: registered device video1 [v4l2]
[   15.640411] cx88[0]/0: registered device vbi0
[   15.641899] cx88[0]/2: cx2388x 8802 Driver Manager
[   15.641916] cx88-mpeg driver manager 0000:01:09.2: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   15.641924] cx88[0]/2: found at 0000:01:09.2, rev: 5, irq: 17, latency: 32, mmio: 0xfa000000
[   15.643582] cx88_audio 0000:01:09.1: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   15.643616] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   15.698030] cx88/2: cx2388x dvb driver version 0.0.8 loaded
[   15.698034] cx88/2: registering cx8802 driver, type: dvb access: shared
[   15.698038] cx88[0]/2: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47]
[   15.698041] cx88[0]/2: cx2388x based DVB/ATSC card
[   15.698043] cx8802_alloc_frontends() allocating 1 frontend(s)
[   16.001655] tuner-simple 1-0061: attaching existing instance
[   16.001659] tuner-simple 1-0061: type set to 64 (LG TDVS-H06xF)
[   16.001732] tda9887 1-0043: attaching existing instance
[   16.001737] DVB: registering new adapter (cx88[0])
[   16.001740] DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...

Only when the mythbackend daemon is running will mythfrontend, which is where you're getting your connection error loop from, be able to connect. If mythbackend is not running, this will need to be fixed before mythfrontend can connect to it. The mythbackend log under /var/log/mythtv/ can be checked for errors.

>My friend, I think I found the problem, but my mind is unable to handle what I found.  I am sure I made a mistake in the configuration, but I don't have the foggiest idea how to get back where I can make the change or the wording I need to enter.  I will print the entire document, but the crux of the problem is as follows:

[B]2011-11-12 22:26:19.272 MythBackend, Warning: No valid capture cards are defined in the database.  and....

2011-11-12 22:26:19.451 Scheduler, Error: No capture cards are defined in the database.  Perhaps you should re-read the installation instructions?
[/B]
I am not embarrassed, because all of this is way over my head for understanding.  Without you, where would I be?

As far as your other UPnP applications, I don't run them so I can't comment on why they specifically do what they do.

>I installed the UPnP just because I thought it was needed for this installation.  I don't understand much of what I am trying to accomplish, but learning............

I will return to the installation instructions and see if I can figure out where I missed entering pcHDTV HD-5500, which is the only name I know for my Tuner (Prividing that is my capture card).

Thanks for your continued patience.  **I am willing to include the entire Backend log if necessary, but it was so long, I did not know if it would be received by the forum.**  I believe I got the important part, and it only seemed to repeat itself on multiple re-trys.

Info gathered after my above entry:

I went over the entire manual,item by item and could not find anywhere where I would enter the name of my capture card.  Where should I look?  Additionally the following information appeared with error message while attempting to run 'Running mythfilldatabase:

QMYSQL:  Unable to connect
Database error was:
Access denied for user 'mythtv '@' localhost'  (using password: (YES)

&#8230;..................................................................................................................................................................
2011-11-26  21:40:14.352 UpnPautoconf() - No UpnP backends found
2011-11-26  21:40:14.352 No UpnP backends found

No UpnP backends found

Would you like to configure the database connection now?  [no]  []

Notice the Access denied for user 'mythtv '@' localhost'  (using password: (YES).  If that is the problem, how do I remedy it?  Thanks again.

---

### Post by klc5555 on 2011-11-27
There's nothing wrong with your capture card. As you yourself have noticed, you haven't completed your mythbackend setup. 

In the mythbackend setup screen, There are 6 main menus: General, Capture Cards, Video Sources, Input Connections, Channel Editor, and Storage Groups.

You seem to have gotten through the General setup menu more-or-less successfully, but you still need to define your Capture Card (you actually have two: the DVB side of the 5500 and, if you care to use it, the analog half of the 5500).

When you open the Capture Card menu, and Add Card, mythtv-setup will try to detect various card types on various device nodes. Click through the Card Types menu until it finds your 5500 presumably at DVB0 (a 'DVB DTV Capture Card type (v3.0) or some such). Under 'subtype' it will have found pchdtv5500 as a likely candidate. In the menu Recording Options you change simultaneous recording from '2' to '1' and Finish. Your DVB capture card is now defined.

In Video Sources, you need to set up a Video Source for your DVB tuner. You can set up a grabber now, but that is not essential.

In Input Connections, you will bind the Video Source you just created to the DVB input of the Capture Card you just set up. Going to the menu for this DVB input in Input Connections, you will do a scan for available channels. If you are on cable, this scan will likely be a Full Scan, and QAM256. If your scan is getting signal strength, and channel locks, you are in business. When the scan is over, your Video Source should be populated with these new channels that Mythtv knows about and that it can tune to when the information is saved, mythbackend is started, and mythfrontend connects to it.

This is the gist of what the instruction manuals are trying to tell you.

---

### Post by Shabakthanai on 2011-11-27
> **klc5555 said:**
> There's nothing wrong with your capture card. As you yourself have noticed, you haven't completed your mythbackend setup. 

In the mythbackend setup screen, There are 6 main menus: General, Capture Cards, Video Sources, Input Connections, Channel Editor, and Storage Groups.

You seem to have gotten through the General setup menu more-or-less successfully, but you still need to define your Capture Card (you actually have two: the DVB side of the 5500 and, if you care to use it, the analog half of the 5500).

When you open the Capture Card menu, and Add Card, mythtv-setup will try to detect various card types on various device nodes. Click through the Card Types menu until it finds your 5500 presumably at DVB0 (a 'DVB DTV Capture Card type (v3.0) or some such). Under 'subtype' it will have found pchdtv5500 as a likely candidate. In the menu Recording Options you change simultaneous recording from '2' to '1' and Finish. Your DVB capture card is now defined.

In Video Sources, you need to set up a Video Source for your DVB tuner. You can set up a grabber now, but that is not essential.

In Input Connections, you will bind the Video Source you just created to the DVB input of the Capture Card you just set up. Going to the menu for this DVB input in Input Connections, you will do a scan for available channels. If you are on cable, this scan will likely be a Full Scan, and QAM256. If your scan is getting signal strength, and channel locks, you are in business. When the scan is over, your Video Source should be populated with these new channels that Mythtv knows about and that it can tune to when the information is saved, mythbackend is started, and mythfrontend connects to it.

This is the gist of what the instruction manuals are trying to tell you.

This is embarrassing; I am old and forget things. Twice I have gotten the mythbackend setup screen to appear. I have configured each entry to my best ability, the second time better than the first. Nevertheless, I cannot remember how I got the screen to open, either time.
There is an option in the Kmenu under:
Kmenu>Applications>System>mythtv-setup(Mythtv Backend Setup)
It appears to be the appropriate link to the menu for configuring mythtv backend, however, when I currently click on it, a window opens with'Mythbackend must be closed before continuing - It is OK to close any currently running bythbackend processes?' I select 'Yes' and enter my password. Mythsetup terminal opens briefly, then the screen with the Country flags and Languages. I select English (United States) and 'Save'. The next window says No UPnP and I check 'OK' (it is the only option). This is a brown background screen titled Database Configuration 1/2.
The top includes an error message as follows:
MythTV could not connect to the database. Please verify your database settings below. Required fields are marked with an asterisk (*). Hostname: is the only field with an '*', so I have tried these options in that field:
127.0.0.1, 192.168.0.111, and localhost. Each provide the following results:
I select next and Database Configuration 2/2 appears. There are two items to choose from, 'Use custom identifier for frontend preferences' and 'Enable database server wakeup'.
When I select 'Use customidentifier for frontend preferences' selection 'Custom identifier: appears with 'my-unique-identifier-goes-here' to describe what I am to put in the space.
I do not know what that means or what to put in the space, so currently I leave it blank. (On a previous occasion, I may have put something in there, perhaps 'Yeshuah', then select 'Finish' and 'Cannot' appears with an 'OK' button.
When I click on 'OK', I am returned to the Database Configuration 1/2 screen. This time on 2/2, I check 'Enable database server wakeup'.
For Reconnect time: I enter 10 and Retry attempts: 5. Next I select 'Wake command: it is pre-filled with the following:
'echo 'WOLsqlServerCommand not set'. Below in the instruction window is the following:
The command executed on this frontend to wake up the database server (eg. sudo /etc/init.d/mysql restart).'
I do not understand what this is about, so I enter 'sudo /etc/init.d/mysql restart' for the wake command, and select 'Finish'. The window that opens says 'Cannot' so I click 'OK', and I am returned to page 1/2.
I guess I expect the 'Backend Configuration' window to open to begin configuring the backend, but am caught in an endless loup.
I hate to expose how really stupid I am, and suppose you may lose patience with me and not want to finish, but we are so close. I believe if I could somehow find the configuration page again, I could make the final adjustment and have a TV. I amaze myself how I am able to do as well as I do in operating a computer. Couldn't happen without kind people like you.
Occassionally, when I run mythfilldatabase,it automatically opens the Country and Language page of 'start mythtv-backend'. Sometimes it opens with trim...
QMYSQL: unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES) followed by:
...............................................
2011-11-27 11:06:32.034 UPnPautoconf() - No UPnP backends found
2011-11-27 11:06:32.034 No UPnP backends found
No UPnP backends found
Would you like to configure database connections now: [no]
At this point, I usually type in yes and attempt configuration. Becuase this appears almost like a command line entry of the same stuff in the GUI, I am not sure what choices I make on the individual entries, because none of those options have worked in the past attempts, except on the rare occasion I may have entered the right combination of choices and that was when I got the configuration window for the backend. I don't know.
If you are willing to put me back on the configuration screen, I will make that last change and stop troubling you. I am confident you have a more important use of your time. Still, this is really important to me. I would like to watch football games live and perhaps a movie once in a while. Thanks again, most valued and patient one.
You seem to have gotten through the General setup menu more-or-less successfully, but you still need to define your Capture Card (you actually have two: the DVB side of the 5500 and, if you care to use it, the analog half of the 5500).
When you open the Capture Card menu, and Add Card, mythtv-setup will try to detect various card types on various device nodes. Click through the Card Types menu until it finds your 5500 presumably at DVB0 (a 'DVB DTV Capture Card type (v3.0) or some such). Under 'subtype' it will have found pchdtv5500 as a likely candidate. In the menu Recording Options you change simultaneous recording from '2' to '1' and Finish. Your DVB capture card is now defined.
In Video Sources, you need to set up a Video Source for your DVB tuner. You can set up a grabber now, but that is not essential.
In Input Connections, you will bind the Video Source you just created to the DVB input of the Capture Card you just set up. Going to the menu for this DVB input in Input Connections, you will do a scan for available channels. If you are on cable, this scan will likely be a Full Scan, and QAM256. If your scan is getting signal strength, and channel locks, you are in business. When the scan is over, your Video Source should be populated with these new channels that Mythtv knows about and that it can tune to when the information is saved, mythbackend is started, and mythfrontend connects to it.
This is the gist of what the instruction manuals are trying to tell you.[/QUOTE]

---

### Post by Shabakthanai on 2011-11-27
> **Shabakthanai said:**
> This is embarrassing; I am old and forget things. Twice I have gotten the mythbackend setup screen to appear. I have configured each entry to my best ability, the second time better than the first. Nevertheless, I cannot remember how I got the screen to open, either time.
There is an option in the Kmenu under:
Kmenu>Applications>System>mythtv-setup(Mythtv Backend Setup)
It appears to be the appropriate link to the menu for configuring mythtv backend, however, when I currently click on it, a window opens with'Mythbackend must be closed before continuing - It is OK to close any currently running bythbackend processes?' I select 'Yes' and enter my password. Mythsetup terminal opens briefly, then the screen with the Country flags and Languages. I select English (United States) and 'Save'. The next window says No UPnP and I check 'OK' (it is the only option). This is a brown background screen titled Database Configuration 1/2.
The top includes an error message as follows:
MythTV could not connect to the database. Please verify your database settings below. Required fields are marked with an asterisk (*). Hostname: is the only field with an '*', so I have tried these options in that field:
127.0.0.1, 192.168.0.111, and localhost. Each provide the following results:
I select next and Database Configuration 2/2 appears. There are two items to choose from, 'Use custom identifier for frontend preferences' and 'Enable database server wakeup'.
When I select 'Use customidentifier for frontend preferences' selection 'Custom identifier: appears with 'my-unique-identifier-goes-here' to describe what I am to put in the space.
I do not know what that means or what to put in the space, so currently I leave it blank. (On a previous occasion, I may have put something in there, perhaps 'Yeshuah', then select 'Finish' and 'Cannot' appears with an 'OK' button.
When I click on 'OK', I am returned to the Database Configuration 1/2 screen. This time on 2/2, I check 'Enable database server wakeup'.
For Reconnect time: I enter 10 and Retry attempts: 5. Next I select 'Wake command: it is pre-filled with the following:
'echo 'WOLsqlServerCommand not set'. Below in the instruction window is the following:
The command executed on this frontend to wake up the database server (eg. sudo /etc/init.d/mysql restart).'
I do not understand what this is about, so I enter 'sudo /etc/init.d/mysql restart' for the wake command, and select 'Finish'. The window that opens says 'Cannot' so I click 'OK', and I am returned to page 1/2.
I guess I expect the 'Backend Configuration' window to open to begin configuring the backend, but am caught in an endless loup.
I hate to expose how really stupid I am, and suppose you may lose patience with me and not want to finish, but we are so close. I believe if I could somehow find the configuration page again, I could make the final adjustment and have a TV. I amaze myself how I am able to do as well as I do in operating a computer. Couldn't happen without kind people like you.
Occassionally, when I run mythfilldatabase,it automatically opens the Country and Language page of 'start mythtv-backend'. Sometimes it opens with trim...
QMYSQL: unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES) followed by:
...............................................
2011-11-27 11:06:32.034 UPnPautoconf() - No UPnP backends found
2011-11-27 11:06:32.034 No UPnP backends found
No UPnP backends found
Would you like to configure database connections now: [no]
At this point, I usually type in yes and attempt configuration. Becuase this appears almost like a command line entry of the same stuff in the GUI, I am not sure what choices I make on the individual entries, because none of those options have worked in the past attempts, except on the rare occasion I may have entered the right combination of choices and that was when I got the configuration window for the backend. I don't know.
If you are willing to put me back on the configuration screen, I will make that last change and stop troubling you. I am confident you have a more important use of your time. Still, this is really important to me. I would like to watch football games live and perhaps a movie once in a while. Thanks again, most valued and patient one.
You seem to have gotten through the General setup menu more-or-less successfully, but you still need to define your Capture Card (you actually have two: the DVB side of the 5500 and, if you care to use it, the analog half of the 5500).
When you open the Capture Card menu, and Add Card, mythtv-setup will try to detect various card types on various device nodes. Click through the Card Types menu until it finds your 5500 presumably at DVB0 (a 'DVB DTV Capture Card type (v3.0) or some such). Under 'subtype' it will have found pchdtv5500 as a likely candidate. In the menu Recording Options you change simultaneous recording from '2' to '1' and Finish. Your DVB capture card is now defined.
In Video Sources, you need to set up a Video Source for your DVB tuner. You can set up a grabber now, but that is not essential.
In Input Connections, you will bind the Video Source you just created to the DVB input of the Capture Card you just set up. Going to the menu for this DVB input in Input Connections, you will do a scan for available channels. If you are on cable, this scan will likely be a Full Scan, and QAM256. If your scan is getting signal strength, and channel locks, you are in business. When the scan is over, your Video Source should be populated with these new channels that Mythtv knows about and that it can tune to when the information is saved, mythbackend is started, and mythfrontend connects to it.
This is the gist of what the instruction manuals are trying to tell you.[/QUOTE]

**[COLOR="DarkRed"]Wish I could edit this post.  It was a bit embarrassing.  Anyway I found how to get to the configuration page and will attempt it now.  I wrote this to perhaps edit out the lengthy and embarrassing comment.  If you read this first, you may avoid the long read.  I will still post success once accomplished.  You have been and continue to be just GREAT.  Thanks![/COLOR]**

---

### Post by Shabakthanai on 2011-11-27
> **Shabakthanai said:**
> 

**[COLOR="DarkRed"]Wish I could edit this post.  It was a bit embarrassing.  Anyway I found how to get to the configuration page and will attempt it now.  I wrote this to perhaps edit out the lengthy and embarrassing comment.  If you read this first, you may avoid the long read.  I will still post success once accomplished.  You have been and continue to be just GREAT.  Thanks![/COLOR]**[/QUOTE]

[COLOR="Green"]I wasn't permitted to edit out the previous response, sorry.  I wanted to save you the unnecessary long read.

I was able to find my way back to correct the configuration error.  I also added the analog tuner you mentioned.  When I attempted to login, I was unable to 'unlock' the login settings.  I waited a couple of minutes to make sure there was no delay in effect.  Login in sudo required an additional password.  I tried 0000. mythtv, 6343, and my two current passwords for things like this.  All logins were unsuccessful.  

I believe talk is taking place with the database and things are pretty-much workable, but the new problem has me baffled.  Do you have any recommendations for this new problem?
[/COLOR]

---

### Post by Shabakthanai on 2011-11-27
> **Shabakthanai said:**
> **[COLOR="DarkRed"]Wish I could edit this post.  It was a bit embarrassing.  Anyway I found how to get to the configuration page and will attempt it now.  I wrote this to perhaps edit out the lengthy and embarrassing comment.  If you read this first, you may avoid the long read.  I will still post success once accomplished.  You have been and continue to be just GREAT.  Thanks![/COLOR]**

[COLOR="Green"]I wasn't permitted to edit out the previous response, sorry.  I wanted to save you the unnecessary long read.

I was able to find my way back to correct the configuration error.  I also added the analog tuner you mentioned.  When I attempted to login, I was unable to 'unlock' the login settings.  I waited a couple of minutes to make sure there was no delay in effect.  Login in sudo required an additional password.  I tried 0000. mythtv, 6343, and my two current passwords for things like this.  All logins were unsuccessful.  
I believe talk is taking place with the database and things are pretty-much workable, but the new problem has me baffled.  Do you have any recommendations for this new problem?
[/COLOR][/QUOTE]

[B][COLOR="DarkOrange"]I selected 'Startup Behavior in 'Mythbuntu Control Center.  'Automatically start MythTV frontend is checked.  I selected 'Autopmagic Login Configuration'.  What opens is a Login Screen.  It needs changes made, however the only active items are  'Unlock' and  'X Close'.  Selecting 'Unlock' nothing seems to happen.

There are 13 signals locked, but I can't figure a way to see any of them.  It seems that being locked out of Login may be the thing that is halting the progress.[/COLOR][/B]

---

### Post by klc5555 on 2011-11-27
> **Shabakthanai said:**
> [COLOR="Green"]I wasn't permitted to edit out the previous response, sorry.  I wanted to save you the unnecessary long read.

I was able to find my way back to correct the configuration error.  I also added the analog tuner you mentioned.  When I attempted to login, I was unable to 'unlock' the login settings.  I waited a couple of minutes to make sure there was no delay in effect.  Login in sudo required an additional password.  I tried 0000. mythtv, 6343, and my two current passwords for things like this.  All logins were unsuccessful.  
I believe talk is taking place with the database and things are pretty-much workable, but the new problem has me baffled.  Do you have any recommendations for this new problem?
[/COLOR]

[B][COLOR="DarkOrange"]I selected 'Startup Behavior in 'Mythbuntu Control Center.  'Automatically start MythTV frontend is checked.  I selected 'Autopmagic Login Configuration'.  What opens is a Login Screen.  It needs changes made, however the only active items are  'Unlock' and  'X Close'.  Selecting 'Unlock' nothing seems to happen.

There are 13 signals locked, but I can't figure a way to see any of them.  It seems that being locked out of Login may be the thing that is halting the progress.[/COLOR][/B][/QUOTE]

It isn't immediately clear at this stage what you're trying to login to or what you're locked out of.

Mythbackend is a daemon which is running automatically as root. It controls the scheduled starting up of and tuning of the tuner card(s) to specific channels for specific periods of time. If you've managed to complete the backend setup, has mythbackend actually been started? Once started, it will just run without further direct intervention except through mythfrontend.

Mythfrontend is essentially a just fancy viewing application and an interface to the database and scheduler. It runs as your regular user, not root or sudo. If your backend is running, you can see whether mythfrontend can connect by opening a prompt and typing "mythfrontend". If it connects, you get the standard menu with Watch TV, Media Library, Manage recordings, Information Center, and Utilities/Setup. If mythfrontend can't connect, you get the configuration screen asking for details of where the mythconverg database is. i.e. 127.0.0.1 (or localhost) user: mythtv, password: [the 5 or 6 characters in your mysql.txt file]

So if the backend is running, the only thing you should be logging into is your regular user account.

---

### Post by Shabakthanai on 2011-11-28
> **klc5555 said:**
> [B][COLOR="DarkOrange"]I selected 'Startup Behavior in 'Mythbuntu Control Center.  'Automatically start MythTV frontend is checked.  I selected 'Autopmagic Login Configuration'.  What opens is a Login Screen.  It needs changes made, however the only active items are  'Unlock' and  'X Close'.  Selecting 'Unlock' nothing seems to happen.

There are 13 signals locked, but I can't figure a way to see any of them.  It seems that being locked out of Login may be the thing that is halting the progress.[/COLOR][/B]

It isn't immediately clear at this stage what you're trying to login to or what you're locked out of.

[B][COLOR="SeaGreen"]When first I installed MythTV, an application appeared in Kmenu>Applications>System>(with the title 'Login Screen'.  In the lineup, it preceded 'Mythbuntu Control Center and mythtv-setup'.  I did not pay it much attention, because it could have been there prior to installing MythTV.  Nonetheless, after trying everything I could think of and utilizing all the help provided by you, I tried it.  A 'Login Screen Settings' appeared with everything contained therein grayed out.  Only the 'Unlock' and 'Close' buttons were available.  When attempting to 'Unlock' the screen, nothing happened.

The screen contains the following selections:

When the computer starts up:

'check-box' for Show a list of users
'radio button' for Show the screen for choosing who will log in (pre-ticked)
'radio button' for Log in as (steven vollom (steven) automatically
'check box' for Allow 30 seconds for anyone else to log in first
Select (Ubuntu) as default session
                                          [Unlock]        [XClose]

Since I am a Kubuntu user, the pre-entered reference made a mental connection for Mythbuntu.  Even the configuration screens are in the brown - Ubuntu style.

Other than that, I don't see the purpose for the application.  And since I seem to be locked out of the mythbackend, I thought it a possibility as a solution to my problem - if I was able to unlock it, that is, and change it's configuration to suit my preferences.[/COLOR][/B]


Mythbackend is a daemon which is running automatically as root. It controls the scheduled starting up of and tuning of the tuner card(s) to specific channels for specific periods of time. If you've managed to complete the backend setup, has mythbackend actually been started? Once started, it will just run without further direct intervention except through mythfrontend.

**[COLOR="SeaGreen"][COLOR="SeaGreen"]Frankly, I don't think the backend has ever been started.  I believe that is the problem.[/COLOR][/COLOR]**

Mythfrontend is essentially a just fancy viewing application and an interface to the database and scheduler. It runs as your regular user, not root or sudo. If your backend is running, you can see whether mythfrontend can connect by opening a prompt and typing "mythfrontend".

**[COLOR="SeaGreen"]When I type in mythfrontend, it takes me to the same configuration page as with the backend.  the *Localhost is always preset as 'localhost'.  It is only when I enter sudo mythfrontend that I get the fancy screen, with the standard menu, you are talking about.[/COLOR]** 

If it connects, you get the standard menu with Watch TV, Media Library, Manage recordings, Information Center, and Utilities/Setup. If mythfrontend can't connect, you get the configuration screen asking for details of where the mythconverg database is. i.e. 127.0.0.1 (or localhost) user: mythtv, password: [the 5 or 6 characters in your mysql.txt file]

**[COLOR="SeaGreen"]When I open the mysql.text file, located at /etc/mythtv/mysql.txt, the document does not contain anything at all.[/COLOR]**

So if the backend is running, the only thing you should be logging into is your regular user account.[/QUOTE]

[B][COLOR="SeaGreen"]From the command line, here is the several attempts at providing information for you which might diagnose what I am missing.  I am not experienced enough to know other sources of data that might help.

If I open mythfrontend using sudo, the screen opens the directory of choices you mentioned, Media Library, Manage Recordings, Informatiin, Optical Disks, and Watch TV.  It is the first time I have seen this screen.  In the center of the screen, it says Could not connect to the master backend server.  Is it running?  Is the IP address set for it in mythtv-setup correct? And  the OK button.

Here is what I get opening mythfrontend not in sudo:

No UPnP and the OK selection.  I select OK and it opens with the error message:

MythTv could not connect to the database.  Please verify your database settings below.  The required field is marked with an asterisk (*).  Under '*Hostname:  It is always preset as 'localhost'.  From previous instruction, I type in 127.0.0.1, check 'Ping test server? Leaving 'Port:' empty.  On 2/2 both choices' check-boxes are not ticked and I leave it that way and click 'Finish'.  The screen that appears says 'Cannot &#8211; OK'.  It then returns to the first screen of configuration.  

The entry for '*Hostname:' has returned to 'localhost'.  This time I type in my IP address.  I copied this from my panel and it says the following:


Type:
*Wired Ethernet
Connection*State:
*Connected
IP*Address:
*192.168.0.111
Connection*Speed:
*100 MBit/s
System*Name:
*eth1
MAC*Address:
*xx:xx:xx:xx  (I am showing x's because I suspect security to my system would be compromised by putting this on the Internet)
Driver:
*r8169

The warning is same, 'MythTV could not connet to the database.  Please verify your database settings below.  Required fields are marked with an asterisk (*).

This time under '*Hostname' I enter 192.168.0.111, check 'Ping test server' leaving 'Port' empty and select 'Next'.  On page 2/2 I again leave both choices unchecked and select 'Finish'.  The final screen says 'Cannot  - OK'.  After selecting 'OK', the screen returns to the same screen as before; a reoccurring loop.

Using a konsole, I enter the command 'mythfrontend'.  Here is the information the konsole reveals:

 steven@Yeshuah:~$ mythfrontend
2011-11-28 15:59:17.693 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-11-28 15:59:17.693 Using runtime prefix = /usr
2011-11-28 15:59:17.693 Using configuration directory = /home/steven/.mythtv
2011-11-28 15:59:17.694 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-11-28 15:59:18.298 Unable to read configuration file mysql.txt
2011-11-28 15:59:18.298 Empty LocalHostName.
2011-11-28 15:59:18.298 Using localhost value of Yeshuah
2011-11-28 15:59:18.314 New DB connection, total: 1
2011-11-28 15:59:18.316 Unable to connect to database!
2011-11-28 15:59:18.316 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES) **[COLOR="DarkRed"]???Is this potentially the problem???[/COLOR]**

................................................................................
2011-11-28 15:59:20.445 UPnPautoconf() - No UPnP backends found
2011-11-28 15:59:20.445 No UPnP backends found
2011-11-28 15:59:20.447 Could not find theme:  - Switching to Terra
2011-11-28 15:59:20.459 Desktop video mode: 3600x1080 60.000 Hz
2011-11-28 15:59:20.468 get_ip: No address associated with hostname
2011-11-28 15:59:20.468 LIRC, Error: Failed to parse IP address ''
2011-11-28 15:59:20.468 JoystickMenuThread: Joystick disabled - Failed to read /home/steven/.mythtv/joystickmenurc
2011-11-28 15:59:20.480 Using Frameless Window
2011-11-28 15:59:20.481 Using Full Screen Window
2011-11-28 15:59:20.484 Using the Qt painter
2011-11-28 15:59:20.896 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-11-28 15:59:20.897 System Locale (en_US), Country (US), Language (en_US)
2011-11-28 16:01:13.108 Loading en_us translation for module mythfrontend
2011-11-28 16:04:56.393 User cancelled database configuration
2011-11-28 16:04:56.409 Failed to init MythContext, exiting.
2011-11-28 16:04:56.409 Deleting UPnP client...
steven@Yeshuah:~$ 

Then a GUI appears with Flags and language, same as for the backend setup.  After selecting 'English &#8211; United States', the next screen says, 'No UPnP &#8211; OK'.  Selecting 'OK' the next screen is identical to the myth backend screen setup with the same warning and presets.  It begins the same loup as when configuring mythbackend.

Now I open 'sudo mythfrontend' and the graphic opening screen for MythTV.  Choices starting with 'Media Library' and ending with 'Watch TV'.  In the center of the screen is the error message:

Could not connect to the master backend server.  Is it running?  Is the IP address set for it in mythtv-setup correct? And the 'OK' button. Clicking on the OK button only reopens the error message again.

Next I exit MythTV.  I don't know what else to do.  The konsole data for this effort is as follows:

steven@Yeshuah:~$ sudo mythfrontend
[sudo] password for steven:                                                           
2011-11-28 16:09:07.671 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-11-28 16:09:07.671 Using runtime prefix = /usr
2011-11-28 16:09:07.671 Using configuration directory = /home/steven/.mythtv
2011-11-28 16:09:07.672 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-11-28 16:09:08.276 Empty LocalHostName.
2011-11-28 16:09:08.276 Using localhost value of Yeshuah
2011-11-28 16:09:08.293 New DB connection, total: 1
2011-11-28 16:09:08.295 Connected to database 'mythconverg' at host: localhost
2011-11-28 16:09:08.309 Closing DB connection named 'DBManager0'
2011-11-28 16:09:08.309 Connected to database 'mythconverg' at host: localhost
2011-11-28 16:09:08.311 Current locale EN_US
2011-11-28 16:09:08.311 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-11-28 16:09:08.519 DPMS is disabled.
2011-11-28 16:09:08.535 Desktop video mode: 3600x1080 60.000 Hz
2011-11-28 16:09:08.545 Enabled verbose msgs:  important general
2011-11-28 16:09:08.547 Loading en_us translation for module mythfrontend
2011-11-28 16:09:08.553 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
                        eno: No such file or directory (2)
2011-11-28 16:09:08.553 JoystickMenuThread: Joystick disabled - Failed to read /home/steven/.mythtv/joystickmenurc
2011-11-28 16:09:08.575 Using Frameless Window
2011-11-28 16:09:08.575 Using Full Screen Window
2011-11-28 16:09:08.732 Using the Qt painter
2011-11-28 16:09:08.863 Current MythTV Schema Version (DBSchemaVer): 1264
2011-11-28 16:09:08.949 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-11-28 16:09:08.949 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-11-28 16:09:08.950 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-11-28 16:09:08.950 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-11-28 16:09:09.120 Registering Internal as a media playback plugin.
2011-11-28 16:09:09.134 Loading en_us translation for module mytharchive
2011-11-28 16:09:09.137 Registering WebBrowser as a media playback plugin.
2011-11-28 16:09:09.138 Loading en_us translation for module mythbrowser
2011-11-28 16:09:09.153 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-28 16:09:09.153 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-28 16:09:09.154 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-28 16:09:09.155 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-28 16:09:09.155 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-28 16:09:09.155 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-28 16:09:09.156 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-28 16:09:09.156 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-28 16:09:09.156 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-28 16:09:09.157 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-11-28 16:09:09.157 Loading en_us translation for module mythgallery
2011-11-28 16:09:09.163 Loading en_us translation for module mythgame
2011-11-28 16:09:09.178 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-11-28 16:09:09.199 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-11-28 16:09:09.203 Loading en_us translation for module mythmusic
2011-11-28 16:09:09.205 Loading en_us translation for module mythnetvision
2011-11-28 16:09:09.208 Loading en_us translation for module mythnews
2011-11-28 16:09:09.213 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-11-28 16:09:09.222 Loading en_us translation for module mythvideo
2011-11-28 16:09:09.226 Loading en_us translation for module mythweather
2011-11-28 16:09:09.416 Found mainmenu.xml for theme 'Mythbuntu'
2011-11-28 16:09:09.433 MythCoreContext: Connecting to backend server: 192,168.0.111:6543 (try 1 of 1)
2011-11-28 16:09:09.434 MythSocket(16d4090:36): Unable to lookup: 192,168.0.111
2011-11-28 16:09:09.434 Connection to master server timed out.
                        Either the server is down or the master server settings
                        in mythtv-settings does not contain the proper IP address

2011-11-28 16:09:14.657 MythCoreContext: Connecting to backend server: 192,168.0.111:6543 (try 1 of 1)
2011-11-28 16:09:14.657 MythSocket(1668f10:33): Unable to lookup: 192,168.0.111
2011-11-28 16:09:14.657 Connection to master server timed out.
                        Either the server is down or the master server settings
                        in mythtv-settings does not contain the proper IP address

Trim......   Several pages of failed repeat attempts....

2011-11-28 16:12:49.676 MythCoreContext: Connecting to backend server: 192,168.0.111:6543 (try 1 of 1)
2011-11-28 16:12:49.676 MythSocket(7f0130078620:26): Unable to lookup: 192,168.0.111
2011-11-28 16:12:49.676 Connection to master server timed out.
                        Either the server is down or the master server settings
                        in mythtv-settings does not contain the proper IP address

Something that is nagging my current memory is 'group settings'.  I don't recall the specifics, but in other searches it seemed to cure their problem with MythTV.  Is there a possibility something like that could be causing the problem?  If so, I do not know how to find or change and correct that.

Thanks for your patience.[/COLOR][/B]

**[COLOR="DarkRed"]Actually, I believe the backend is running; I just think that front and backends are not talking to eachother.  That is why I made mention of 'group settings' and or 'passwords'.  I sited in the Red color, above where my connection was rejected using the password 'YES'; I don't even know where that password was entered. I don't remember ever using 'YES' as a password for anything.[/COLOR]**

---

### Post by klc5555 on 2011-11-29
> 2011-11-28 16:12:49.676 MythCoreContext: Connecting to backend server: 192,168.0.111:6543 (try 1 of 1)
2011-11-28 16:12:49.676 MythSocket(7f0130078620:26): Unable to lookup: 192,168.0.111
2011-11-28 16:12:49.676 Connection to master server timed out.
Either the server is down or the master server settings
in mythtv-settings does not contain the proper IP address

Problem #1: "192,168.0.111" is not valid --it has a comma between the first two binary groups. This would be the invalid IP error running sudo. If sudo mythfrontend can connect and can access the backend, then there is a config.xml and mysql.txt containing correct data somewhere --maybe under /root/.mythtv/ or under /home/mythtv/.mythtv/ Find them and copy them to the corresponding position in your user directory.

When trying to connect as a regular user:

 > This time under '*Hostname' I enter 192.168.0.111, check 'Ping test server' leaving 'Port' empty and select 'Next'. On page 2/2 I again leave both choices unchecked and select 'Finish'. The final screen says 'Cannot - OK'. After selecting 'OK', the screen returns to the same screen as before; a reoccurring loop

You don't mention whether you have set the password on the mythfrontend configuration screen to the database's password. If you have found a correct mysql.txt and/or config.xml on your system and copied them to the correct place in your user directory, this problem with your user account should disappear.

I assume that when you set up your backend with mythtv-setup you also set the PIN number in the first page of the General setup to 0000 (as specified in [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend) ) which may facilitate your two frontends (the one you're trying to run as sudo and the one you're trying to run as your user) in finding and authenticating to the backend.

As far as the peculiarities pertaining to Kbuntu's KDE login and KDE desktop configuration go, these should have no particular bearing on Mythtv whatever. As long as the required libraries are present, Mythtv operates more-or-less the same out of KDE, Gnome, XCFE, fvwm, fluxbox, blackbox, twm, a bare-naked xterm, or X with no window manager at all.

As far as users/groups go, during the original installation of the .deb packages, a mythtv group should have been created. Eventually your main user will need to be added to this mythtv group to avoid odd permission errors. The Ubuntu version of myth control center should offer to do this the first time you run it as your regular user. Otherwise, at some point you can do it by hand.

---

### Post by Shabakthanai on 2011-11-30
> **klc5555 said:**
> Problem #1: "192,168.0.111" is not valid --it has a comma between the first two binary groups. This would be the invalid IP error running sudo. If sudo mythfrontend can connect and can access the backend, then there is a config.xml and mysql.txt containing correct data somewhere --maybe under /root/.mythtv/ or under /home/mythtv/.mythtv/ Find them and copy them to the corresponding position in your user directory.

When trying to connect as a regular user:

 

You don't mention whether you have set the password on the mythfrontend configuration screen to the database's password. If you have found a correct mysql.txt and/or config.xml on your system and copied them to the correct place in your user directory, this problem with your user account should disappear.

I assume that when you set up your backend with mythtv-setup you also set the PIN number in the first page of the General setup to 0000 (as specified in [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend) ) which may facilitate your two frontends (the one you're trying to run as sudo and the one you're trying to run as your user) in finding and authenticating to the backend.

As far as the peculiarities pertaining to Kbuntu's KDE login and KDE desktop configuration go, these should have no particular bearing on Mythtv whatever. As long as the required libraries are present, Mythtv operates more-or-less the same out of KDE, Gnome, XCFE, fvwm, fluxbox, blackbox, twm, a bare-naked xterm, or X with no window manager at all.

As far as users/groups go, during the original installation of the .deb packages, a mythtv group should have been created. Eventually your main user will need to be added to this mythtv group to avoid odd permission errors. The Ubuntu version of myth control center should offer to do this the first time you run it as your regular user. Otherwise, at some point you can do it by hand.

[B]It is Wednesday the 30th 2011 about 1:30PM.  Not much interest has been shown in the past couple of days, but I have an update that might help the more skilled to help me fix  my problem.

I am getting a signal and TV when I open the Mythfrontend using 'Sudo'.  I don't know if that can happen without communication between the mythfronted and the mythbackend, nevertheless, it is working as a television.  I am able to view TV on one screen while working on another.  The picture is quite beautiful, however the two channels that I receive which provide Movies, there is a think line of noise at the top of the screen.  It appears like a bunch of various size dashes rapidly moving and distracting a person from the program.  It looks like if I could move the screen up about 1/8th of an inch it would disappear, but I am unable to find an adjustment for that so far.

Thanks to everyone who tried or is continuing to try to help me.  

I would rather open the TV not in sudo, because I am inclined to work and view at the same time.  Kind of like having another person in the room.

Does anyone know how to change user and group settings with mythtv?  In many of the postings, that has cured problems for many users, just by entering a usergroup.  Additionally I need to know how to add a name to a user group or user.  I will research that procedure while waiting for additional help.  Again Thanks for the help![/B]

---

### Post by klc5555 on 2011-11-30
> **Shabakthanai said:**
> [B]
Does anyone know how to change user and group settings with mythtv?  In many of the postings, that has cured problems for many users, just by entering a usergroup.  Additionally I need to know how to add a name to a user group or user.  I will research that procedure while waiting for additional help.  Again Thanks for the help![/B]

Documented in many places for Kubuntu, for example here: [http://linux.about.com/od/kubuntu_doc/a/kubudg15t01.htm](http://linux.about.com/od/kubuntu_doc/a/kubudg15t01.htm)

---

### Post by Shabakthanai on 2011-11-30
> **klc5555 said:**
> Documented in many places for Kubuntu, for example here: [http://linux.about.com/od/kubuntu_doc/a/kubudg15t01.htm](http://linux.about.com/od/kubuntu_doc/a/kubudg15t01.htm)

I believe I found the way to corrects any group problem, however I still have to open mythfrontend in sudo to get a TV workiing.

---

### Post by klc5555 on 2011-12-01
> **Shabakthanai said:**
> I believe I found the way to corrects any group problem, however I still have to open mythfrontend in sudo to get a TV workiing.

How is the regular user failing? 

If there's a failure to connect to the backend that's perpetually giving you a mythfrontend config screen, check in the /.mythtv  directory in your main user's home directory and see whether your mysql.txt and config.xml exist and have actual information in them --in particular the correct mysql password. If these files are blank or don't exist in your user's home directory somewhere under ../.mythtv/, replace them with valid ones, which may exist under /root/.mythtv/ or under /home/mythtv/.mythtv/   Or provide the complete and correct information in the frontend config screen, particularly the machine-generated mysql password, when you run mythfrontend as your regular user.

If the regular user is connecting to the backend so that the regular mythtv menu is showing, but you simply can't run livetv as regular user, this will need to be diagnosed separately, but is usually a storage directory permissions problem.

Looking at the frontend log may provide a clue.

---

### Post by Shabakthanai on 2011-12-01
> **klc5555 said:**
> How is the regular user failing? 

If there's a failure to connect to the backend that's perpetually giving you a mythfrontend config screen, check in the /.mythtv  directory in your main user's home directory and see whether your mysql.txt and config.xml exist and have actual information in them --in particular the correct mysql password. If these files are blank or don't exist in your user's home directory somewhere under ../.mythtv/, replace them with valid ones, which may exist under /root/.mythtv/ or under /home/mythtv/.mythtv/   Or provide the complete and correct information in the frontend config screen, particularly the machine-generated mysql password, when you run mythfrontend as your regular user.

If the regular user is connecting to the backend so that the regular mythtv menu is showing, but you simply can't run livetv as regular user, this will need to be diagnosed separately, but is usually a storage directory permissions problem.

Looking at the frontend log may provide a clue.

[B][COLOR="SeaGreen"]I now have TV, properly opening.  It opens by default when I boot the computer.  It opens by clicking the Frontend icon in the Kmenu Applications list. I can not thank you all enough.

There are just two things that need attention and my mythtv should be working as intended.

First, There is a movie channel.  In this area of the US, it is identified as channel 45.2, the 'THIS' Channel.  It is perhaps my favorite channel.

The first row of pixels at the top of the screen appear as a row of various sized dashes that keep moving, like TV noise.  It is very distracting and would be nice if there is an adjustment that would either cover or remove the row.  All other received channels fill the screen without noise.

Secondly, when I first sought the signals that would lock, there were a few that do not pruduce an acceptable picture, or open at all.  I would like to remove the inactive channels from the menu.  

When changing channels, and when I come to the offending channels, I have to shutdown mythtv and reopen it to select the next channel opportunity, then remember and pass over those channels to be able to continue to change channels without re-booting wintv.  (Hard problem to describe.)

In any event, how do I find that configuration page so I can edit out the unwanted saved channels?  I can't figure out where or what the option is called that identifies the page.  Thanks if you can help?  I googled the subject and looked for it in the manual, but apparently I am using the wrong search terms.[/COLOR][/B]

---

### Post by klc5555 on 2011-12-01
1) Channels can be deleted from individual Video Sources from the Channel Editor in the backend setup. Highlight the offending channel and (depending on mythtv version) the 'delete' key or 'd' key will delete it. The offending channels may reappear the next time you scan your card input for new or moved channels, so you might want to make a note of where they appear for the next time they need to be nuked.

2) If encrypted channels have turned up on your list of channels, your channel scan in Input Connections has a checkbox option to exclude encrypted channels from the scan. Many (but not all) of the channels that are hanging up your Mythtv are likely encrypted channels that were not excluded in the scan parameters.

3) There is actually no such thing as 'Live TV' in Mythtv --it's all recorded to the designated storage directory (or directories). Stuff which came in as 'Live TV' expires and is deleted by the system the next day. You are therefore properly set up to timer record TV for later viewing. Just be aware that TV (Live TV or recording) consumes space: 1 Gigabyte/hr. for Standard Digital; 2.2 Gigs/hr. for analog; and 6 Gigs/hr. for HD recording. So be sure you are set up with enough space available on whatever physical drive /var/lib/mythtv/recordings is on. (Or wherever else you may have set your storage directory)

4) You can manually schedule recordings now --sort of like the way VCRs work. But to more flexibly schedule recordings according to TV listings, you will want to set up a grabber for each of your Video Sources. The Schedules Direct grabber is the standard in the US, and its subscription I think is about the most worthwhile $25 annually I spend for anything. 

5) The moving pixels you see on the 'THIS' channel are the sound track. The scan will need to be adjusted a bit to eliminate this (by spilling the track past the viewable edge of the screen). This mythtv wiki page will introduce you to the problem: [http://www.mythtv.org/wiki/Overscan](http://www.mythtv.org/wiki/Overscan)

There have also been threads on this topic which have popped up on this forum from time to time that can be searched.

It looks like you're up and running now with Mythtv! Good luck! :)

---

### Post by Shabakthanai on 2011-12-01
Dear klc5555,

You have been so thorough, kind and patient.  You are one of the many who make Linux so terrific.  

It is the best TV I have ever known.  It has been most of 10 years since I had a good working TV.  I did not realize how much I missed it.

Now when I am old and retired, and have only a couple of friends anymore, the absence of voices in my environment has become rather painful.  Now I have a channel or two that fill that void.  And the quality of the picture is absolutely unbelievable.  HD is truly high definition. And the colors are so vivid.  Even older programming is much higher quality than I remember from before.  I suspect my problem was a real challenge. My memory is a bit lacking anymore.  It is hard to get back to configuration locations anymore.  I will get my sound adjustments taken care of as soon as I finish.

By the way, my tuner is a pcHDTV 5500 tuner card.  I needed the savings and bought it used.  I was a bit careless and didn't notice that it was made for low profile cases.  I wrote the manufacturer and they sent me a bracket to make my card suitable for regular cases.  They did not charge me anything for the bracket, and were aware that I did not even purchase the card from them, new.

None of the difficulties I have had setting things up have anything to do with the tuner card.  I believe that the character shown by the manufacturer, as well as, the fact that used the card works perfectly should be known by potential users and hope this comment in not out of the order.  I highly recommend their product, which seems to function perfectly right out of the box.  For those who are reading this, it is my personal opinion, however I believe, an accurate one.

---

### Post by Shabakthanai on 2011-12-01
> **Shabakthanai said:**
> Dear klc5555,

You have been so thorough, kind and patient.  You are one of the many who make Linux so terrific.  

It is the best TV I have ever known.  It has been most of 10 years since I had a good working TV.  I did not realize how much I missed it.

Now when I am old and retired, and have only a couple of friends anymore, the absence of voices in my environment has become rather painful.  Now I have a channel or two that fill that void.  And the quality of the picture is absolutely unbelievable.  HD is truly high definition. And the colors are so vivid.  Even older programming is much higher quality than I remember from before.  I suspect my problem was a real challenge. My memory is a bit lacking anymore.  It is hard to get back to configuration locations anymore.  I will get my sound adjustments taken care of as soon as I finish.

By the way, my tuner is a pcHDTV 5500 tuner card.  I needed the savings and bought it used.  I was a bit careless and didn't notice that it was made for low profile cases.  I wrote the manufacturer and they sent me a bracket to make my card suitable for regular cases.  They did not charge me anything for the bracket, and were aware that I did not even purchase the card from them, new.

None of the difficulties I have had setting things up have anything to do with the tuner card.  I believe that the character shown by the manufacturer, as well as, the fact that used the card works perfectly should be known by potential users and hope this comment in not out of the order.  I highly recommend their product, which seems to function perfectly right out of the box.  For those who are reading this, it is my personal opinion, however I believe, an accurate one.

[B][COLOR="DarkRed"]I read the 'overscan' wiki, however, my primare monitor is larger with greater dimentions.  The monitor is a 16:9 with 1920 x 1080.  With the recommended resize of 5% to approximately 1824 x1026 I was apprehensive of attempting the available adjustment in nVidia Settings.  Their maximum size was 1680 x 1050.

In the past, when I have attempted making video setting changes, I have crashed my system, so my concern is probably not unwarranted.  Should I leave the settings on Auto or change to the largest available settings to try to get the noise removed from the top of the screen. 

In nNvidia Settings, under Position:  Absolute, the adjacent box says +1680+0.  I toyed with the idea of changing the +0 to +1, but remembered my luck when changing video settings while not absolutly knowing what to expect from the change.  If you are still following this and have a recommendation, I would appreciate the additional advice.  I would rather try something new using your experience than my own.  And, I am not positive I understand the instruction in the wiki completely.  Thanks, if you do. [/COLOR][/B]

---

### Post by Shabakthanai on 2011-12-03
> **Shabakthanai said:**
> [B][COLOR="DarkRed"]I read the 'overscan' wiki, however, my primare monitor is larger with greater dimentions.  The monitor is a 16:9 with 1920 x 1080.  With the recommended resize of 5% to approximately 1824 x1026 I was apprehensive of attempting the available adjustment in nVidia Settings.  Their maximum size was 1680 x 1050. 

In the past, when I have attempted making video setting changes, I have crashed my system, so my concern is probably not unwarranted.  Should I leave the settings on Auto or change to the largest available settings to try to get the noise removed from the top of the screen. 

In nNvidia Settings, under Position:  Absolute, the adjacent box says +1680+0.  I toyed with the idea of changing the +0 to +1, but remembered my luck when changing video settings while not absolutly knowing what to expect from the change.  If you are still following this and have a recommendation, I would appreciate the additional advice.  I would rather try something new using your experience than my own.  And, I am not positive I understand the instruction in the wiki completely.  Thanks, if you do. [/COLOR][/B]

The screen size is 27 1/2 inches.

---


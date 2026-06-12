---
title: "Tuner detection Mythbuntu 8.04 Linux NOOB"
date: 2008-05-24
forum: Mythbuntu
---

### Post by jasrxtx on 2008-05-24
Hello all,  new linux user and just installed Mythbuntu 8.04.  I have a pcHDTV HD3000 card in system.  At the screen to configure "capture" card, the card is listed as "probed" so it is detected, but in the choice box I don't see a choice for the card specifically.  If I chose either V4L or DVB, the card is still listed as probed, but is apparently not "connected" or "bound" to the system (see log file below). I have read the installation instructions and don't see what I might be missing - this should be a supported card.
 OK so maybe I need the drivers from PCHDTV to load into the "kernel" (new research topic for me).

Now I have two files from PCHDTV - firmware.tar.gz and dvb-atsc-tools-1.0.7.tgz.  Now where do I put them in the filesystem? I suppose this had to be done with Mythdora closed? Then uncompress them, then how to get operating system to compile into kernel?  Or is this not necessary?  

Below is the backend log.  PS no internet connection yet, trying to get it running first.

Thanks for any help or references.

Jasper

2008-05-24 06:52:35.780 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-24 06:52:35.886 Empty LocalHostName.
2008-05-24 06:52:35.978 Using localhost value of jasper-desktop
2008-05-24 06:52:36.092 New DB connection, total: 1
2008-05-24 06:52:36.117 Connected to database 'mythconverg' at host: localhost
2008-05-24 06:52:36.119 Closing DB connection named 'DBManager0'
2008-05-24 06:52:36.121 Connected to database 'mythconverg' at host: localhost
2008-05-24 06:52:36.135 New DB connection, total: 2
2008-05-24 06:52:36.184 Connected to database 'mythconverg' at host: localhost
2008-05-24 06:52:36.353 Current Schema Version: 1214
Starting up as the master server.
2008-05-24 06:52:36.440 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2008-05-24 06:52:36.538 ChannelBase(1) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-05-24 06:52:36.794 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-05-24 06:52:36.920 Main::Registering HttpStatus Extension
2008-05-24 06:52:37.029 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-05-24 06:52:37.081 Enabled verbose msgs:  important general
2008-05-24 06:52:37.278 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-24 06:53:56.757 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-24 06:54:42.577 MainServer::HandleAnnounce Monitor
2008-05-24 06:54:42.581 adding: jasper-desktop as a client (events: 0)
2008-05-24 06:54:42.582 MainServer::HandleAnnounce Monitor
2008-05-24 06:54:42.583 adding: jasper-desktop as a client (events: 1)
2008-05-24 06:55:09.197 Reloading backend settings
2008-05-24 06:55:34.985 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
2008-05-24 06:55:37.440 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
2008-05-24 06:56:54.601 Reloading backend settings
2008-05-24 07:13:30.444 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-24 07:13:30.531 Empty LocalHostName.
2008-05-24 07:13:30.532 Using localhost value of jasper-desktop
2008-05-24 07:13:30.606 New DB connection, total: 1
2008-05-24 07:13:30.676 Connected to database 'mythconverg' at host: localhost
2008-05-24 07:13:30.702 Closing DB connection named 'DBManager0'
2008-05-24 07:13:30.717 Connected to database 'mythconverg' at host: localhost
2008-05-24 07:13:30.749 New DB connection, total: 2
2008-05-24 07:13:30.769 Connected to database 'mythconverg' at host: localhost
2008-05-24 07:13:30.779 Current Schema Version: 1214
Starting up as the master server.
2008-05-24 07:13:30.819 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2008-05-24 07:13:30.831 Channel(0)::Open(): Can't open video device, error "No such file or directory"
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-05-24 07:13:30.915 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-05-24 07:13:30.944 Main::Registering HttpStatus Extension
2008-05-24 07:13:30.945 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-05-24 07:13:30.946 Enabled verbose msgs:  important general
2008-05-24 07:13:30.950 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-24 07:14:50.887 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

---

### Post by tgm4883 on 2008-05-24
Did you go through all the steps in mythtv-setup?  I'll refer you to the installation manual to check that out.

You will need the card setup, a channel data source, and then an input on the card connected to the channel data source (step 4 i believe)

Installation manual can be found at [http://www.mythbuntu.org/installation_manual](http://www.mythbuntu.org/installation_manual)

---

### Post by neutron68 on 2008-05-24
Hi, I'm also having trouble with the HD-5500 card in Mythbuntu 8.04.  I've got about 2 years of Mythtv experience and I am very familiar with the correct setup process.

I was able to use the HD-5500 card as an HDTV receiver card in Mythbuntu 7.04, so I conclude that 8.04 is broken for the HD-5500 cards.  

In the Mythtv Setup, it is not detected as a DVB card, as it should be.  It is only detected as a V4L analog card.

Is there a patch being worked on to fix this false detection problem in 8.04?

Thanks!
Eric

---

### Post by WCCOAM on 2008-05-24
Same tuner card detection issues here as well -- you are not alone.  

Mythbuntu v7.10 correctly detects my PC5500 HD card, but there does not appear to be any correct detection in v8.04; it keeps getting detected as a V4L analog card, and the pull down gives me no digital tuner card options.   

I was forced to blow out 8.04 and revert to Mythbuntu 7.10. I hope this can get corrected in future releases.

---

### Post by tgm4883 on 2008-05-24
I can verify that the HD5500 does in fact work in 8.04.  I stress that you must do some more troubleshooting before jumping on the driver regression bandwagon.

---

### Post by jasrxtx on 2008-05-24
Well, Thanks TGM4883 and group for the help,

I went through the install steps again carefully.  I selected for the cap card the "DVB/DTV Capture Card (V3.x)".  The pick box never said "pcHDTV HD3000" but it seemed to be happy with the card (The manual and the wiki it referred to said that it would). 
On the first attempt to scan, the screen with the black box and "Scanning" at top came up, but nothing more happened.  After about 15 min I backed out to main menu and tried again.  This time success! 
So tomorrow I hook up the DVI output to my big screen TV and figure out the aspect ratio settings!

Thakns again, problem solved (RTFM - carefully!)

Jasper

---

### Post by neutron68 on 2008-05-25
I maintain that there is a problem with the 8.04 install.  We have simply found a bug and have reported it.  If you want, I can redo the install and take photos of the screens so you can see the problem for yourselves.  

Note that Mythbuntu 7.10 and Knoppmyth R5F27 work fine with the same HD-5500 card in the same PCI slot on the same computer.  By process of elimination, version 8.04 is the problem.  Beyond that, I don't know if this is a driver problem or what, exactly.
The pc is built with an Asus A8N-VM CSM motherboard, 1GB of DDR RAM,  an AMD 4000+ single core processor, a single Western Digital IDE hard drive, Pioneer DRV-110 DVD writer.

After posting the problem yesterday, I found a workaround:  During the initial install of Mythbuntu with the HD-5500 as an V4L analog card, I added my local analog channels using Schedules Direct as the channel source, let the install finish and rebooted.  
After reboot, the Mythtv menu screens come up and I hit ESC to exit out of the Mythtv frontend.  I then ran the Mythtv Backend Setup.  When I got into the Capture Card setup screen I found that the HD-5500 card was now being correctly detected as a DVB card.  I then went back through the card configuration process and channel scan process.  Now with the HD-5500 being correctly configured as a DVB card, it was seeing the over the air DTV channels and they were added to the channel lineup.  I then went into the Channel Editor screen and deleted the analog channels because I want to use the HD-5500 card for DTV and HDTV channels only.  After that, I restarted the Mythtv Frontend software and was able to watch an HDTV channel using the Watch TV menu selection.

Let me know if screen photos of the problem are useful.
Eric

---


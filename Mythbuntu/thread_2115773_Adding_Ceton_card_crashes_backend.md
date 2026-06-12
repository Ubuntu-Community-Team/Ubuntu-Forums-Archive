---
title: "Adding Ceton card crashes backend"
date: 2013-02-13
forum: Mythbuntu
---

### Post by Massfeller on 2013-02-13
Evening all,

Just installed a fresh build of 12.04.1 64bit got my infinitv drivers loaded fine, tested tuner using "cat /dev/ceton/ctn91xx_mpeg0_0 | mplayer -cache 8192 -" and can successfully tune any channel i'm authorized for. Problem is when I try to add my capture card to the backend using the standard defaults CETON : 192.168.200.1-0.0 it makes the backend fail to start, here's the output from the terminal when trying to start the backend manually using "sudo mythbackend"

```
2013-02-13 20:05:29.200250 C  mythbackend version: fixes/0.25 [v0.25.2-15-g46cab93] www.mythtv.org
2013-02-13 20:05:29.200267 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2013-02-13 20:05:29.200272 N  Enabled verbose msgs:  general
2013-02-13 20:05:29.200288 N  Setting Log Level to LOG_INFO
2013-02-13 20:05:29.200325 I  Added logging to the console
2013-02-13 20:05:29.200332 I  Added database logging to table logging
2013-02-13 20:05:29.200392 N  Setting up SIGHUP handler
2013-02-13 20:05:29.200445 N  Using runtime prefix = /usr
2013-02-13 20:05:29.200529 N  Using configuration directory = /home/ryan/.mythtv
2013-02-13 20:05:29.200758 I  Assumed character encoding: en_US.UTF-8
2013-02-13 20:05:29.201118 N  Empty LocalHostName.
2013-02-13 20:05:29.201124 I  Using localhost value of TV-Server
2013-02-13 20:05:29.211167 N  Setting QT default locale to EN_US
2013-02-13 20:05:29.211226 I  Current locale EN_US
2013-02-13 20:05:29.211261 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2013-02-13 20:05:29.214840 I  Current MythTV Schema Version (DBSchemaVer): 1299
2013-02-13 20:05:29.215042 I  Loading en_us translation for module mythfrontend
2013-02-13 20:05:29.215334 N  MythBackend: Starting up as the master server.
2013-02-13 20:05:29.216666 E  TVRec(1): Problem finding starting channel, setting to default of '3'.
2013-02-13 20:05:29.477730 E  InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2013-02-13 20:05:29.947496 E  ChannelBase: CreateChannel() Error: Failed to open device 192.168.200.1-0.0
2013-02-13 20:05:29.947533 E  Problem with capture cardsCard 1failed init
2013-02-13 20:05:29.947564 W  MythBackend: No valid capture cards are defined in the database.
2013-02-13 20:05:29.948398 E  Scheduler: No channel sources defined in the database
```

Am I missing something really obvious? I've been searching the forums, google, and cant find anything that matches my issue. Since I'm new to this distro can someone help with some basic troubleshooting things to try?

Thanks in advance -Ryan

---

### Post by Akriss on 2013-02-14
> 2013-02-13 20:05:29.216666 E  TVRec(1): Problem finding starting channel, setting to default of '3'.
2013-02-13 20:05:29.477730 E  InitializeInputs(): Could not get inputs for the capturecard. Perhaps you have forgotten to bind video sources to your card's inputs?

Have you setup your T.V. listings? (IE: Schedules Direct or a listing scrapper of your choice) 

The error above indicates that the backend was not fully configured perhaps?

Hope that helps.

Kris.

---

### Post by Massfeller on 2013-02-16
Thanks for the response I have created a Schedules Direct account and got it added, the EPG data has been downloaded successfully now. I had to upgrade to .26 to make it work all is well now and I'm loving it so far. Thanks!

---


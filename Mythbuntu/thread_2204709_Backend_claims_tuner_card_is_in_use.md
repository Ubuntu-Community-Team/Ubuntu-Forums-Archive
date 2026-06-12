---
title: "Backend claims tuner card is in use"
date: 2014-02-09
forum: Mythbuntu
---

### Post by hexaguin on 2014-02-09
I'm running the latest Mythbuntu on an HP Pavilion m7750n. When I have my tuner set up in the backend, it gives me the following output:

```
2014-02-09 21:29:52.645579 C  mythbackend version: fixes/0.25 [v0.25.2-15-g46cab93] www.mythtv.org2014-02-09 21:29:52.645606 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2014-02-09 21:29:52.645611 N  Enabled verbose msgs:  general
2014-02-09 21:29:52.645638 N  Setting Log Level to LOG_INFO
2014-02-09 21:29:52.645703 I  Added logging to the console
2014-02-09 21:29:52.645711 I  Added database logging to table logging
2014-02-09 21:29:52.645831 N  Setting up SIGHUP handler
2014-02-09 21:29:52.645893 N  Using runtime prefix = /usr
2014-02-09 21:29:52.645912 N  Using configuration directory = /home/user/.mythtv
2014-02-09 21:29:52.646234 I  Assumed character encoding: en_CA.UTF-8
2014-02-09 21:29:52.646761 N  Empty LocalHostName.
2014-02-09 21:29:52.646773 I  Using localhost value of Family-Myth-HP
2014-02-09 21:29:52.662190 N  Setting QT default locale to EN_US
2014-02-09 21:29:52.662279 I  Current locale EN_US
2014-02-09 21:29:52.662330 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2014-02-09 21:29:52.667985 I  Current MythTV Schema Version (DBSchemaVer): 1299
2014-02-09 21:29:52.668280 I  Loading en_us translation for module mythfrontend
2014-02-09 21:29:52.668740 N  MythBackend: Starting up as the master server.
2014-02-09 21:29:52.671242 E  TVRec(1): Problem finding starting channel, setting to default of '3'.
2014-02-09 21:29:52.868868 E  InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2014-02-09 21:29:52.868917 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
2014-02-09 21:29:52.868975 E  Problem with capture cardsCard 1failed init
2014-02-09 21:29:52.870427 E  TVRec(2): Problem finding starting channel, setting to default of '3'.
2014-02-09 21:29:52.870683 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:52.920793 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:52.970989 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:53.021172 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:53.071404 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:53.121586 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:53.171772 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:53.221925 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:53.272077 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:53.322230 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:53.372374 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:53.422527 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:53.472706 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:53.522868 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:53.573015 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:53.623168 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:53.673342 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:53.723503 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:53.773645 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:53.823795 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2014-02-09 21:29:53.823818 E  DVBChan(2:/dev/dvb/adapter0/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
2014-02-09 21:29:53.823836 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
2014-02-09 21:29:53.823887 E  Problem with capture cardsCard 2failed init
2014-02-09 21:29:53.823915 W  MythBackend: No valid capture cards are defined in the database.
2014-02-09 21:29:53.825503 E  Scheduler: No channel sources defined in the database
```

How can I get the tuner working?

---

### Post by aelfric55 on 2014-02-10
> **hexaguin said:**
> I'm running the latest Mythbuntu on an HP Pavilion m7750n. When I have my tuner set up in the backend, it gives me the following output:

```
 ... [snip]2014-02-09 21:29:52.668740 N  MythBackend: Starting up as the master server.
2014-02-09 21:29:52.671242 E  TVRec(1): Problem finding starting channel, setting to default of '3'.
2014-02-09 21:29:52.868868 E  InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2014-02-09 21:29:52.868917 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
2014-02-09 21:29:52.868975 E  Problem with capture cardsCard 1failed init
...
2014-02-09 21:29:53.823915 W  MythBackend: No valid capture cards are defined in the database.
2014-02-09 21:29:53.825503 E  Scheduler: No channel sources defined in the database
```

How can I get the tuner working?

The place to start would be to take the error message at face value. It looks as though the backend setup may not have been properly completed. In particular it looks as though no Video Source has been set up and therefore no Videosource has been bound to the card in Input Connections. If any part of the backend setup is not completed, the backend won't start. The mythtv manual section on setting up capture cards in the backend is found here: [http://www.mythtv.org/wiki/User_Manual:MythTV_structure](http://www.mythtv.org/wiki/User_Manual:MythTV_structure)

---

### Post by tuat2 on 2014-02-11
I've had this problem with tuner cards taking a long time to initialize. If the tuner card is not yet available on backend startup, the backend will not do another approach to find it. You can test if your problem is similar by restarting the backend. If that works, you may want to add a sleep task to the mythbackend startup process to delay the start a little (maybe 5 - 10 seconds) to give the tuner card enough time to initialize. Don't know if that's the best solution, but it worked for me.
Another source of information may be "dmesg" or "dmesg | grep -i dvb".

If the error persists, you may have an issue with the card itself, driver, firmeare, or whatnot... Did the card ever work?

---


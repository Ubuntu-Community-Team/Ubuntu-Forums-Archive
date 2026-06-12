---
title: "Multiple problems...."
date: 2010-10-26
forum: Mythbuntu
---

### Post by bance on 2010-10-26
Hi all,

I had a fully working system, for a few brief weeks, but I borked it somehow.

Luckily, I haven't moved in yet, so I did a fresh install. 10.04 with 23-1 fixes on the B/E and 2 F/E 10.10 with 23-1 fixes. (F/E's are remote.)

First issue is with one of the tuners, I have two ( Hauppage Win-TV HVR 4000 DVB-S/S2/T & KWORLD DVB-T PC 160-2T. Both dual tuners.), the DVB-T tuner on the Hauppage, Shows an error in status page. This tuner was working in the earlier installation and I haven't got a clue whats gone wrong this time.

Second thing is that when I reboot the back-end, (or cold boot) , I constantly have to change the B/E IP address, usually cycling through Local-host, Host-name & actual IP address, until one of them allows a D/B connection. When I first set up myth-tv I only used actual IP addresses! Also the appearance changes randomely, sometimes myth-centre, sometimes terra, sometimes mythbuntu....

Here's some output :-

dmesg
```

[   30.612849] dvb-usb: KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T) successfully initialized and connected.
[   30.624171] usbcore: registered new interface driver dvb_usb_af9015
[   37.303703] tda18271: performing RF tracking filter calibration
[   41.068011] eth0: no IPv6 routers present
[   43.118743] tda18271: RF tracking filter calibration complete
[   43.378197] DVB: adapter 2 frontend 0 frequency 10773250 out of range (174000000..862000000)
[   43.653289] DVB: adapter 2 frontend 0 frequency 10773250 out of range (174000000..862000000)
[   44.232379] tda18271: performing RF tracking filter calibration
[   48.406868] tda18271: RF tracking filter calibration complete
[   49.026315] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[   49.026327] cx8800 0000:00:08.0: firmware: requesting dvb-fe-cx24116.fw
[   49.072221] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[   56.765197] cx24116_load_firmware: FW version 1.26.90.0
[   56.765218] cx24116_firmware_ondemand: Firmware upload complete
[  105.307652] DVB: adapter 2 frontend 0 frequency 11426330 out of range (174000000..862000000)
```Backend log
```

2010-10-26 12:41:48.478 TVRec(1): Changing from WatchingLiveTV to None
2010-10-26 12:42:02.714 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-10-26 12:42:02.749 UPnpMedia: BuildMediaMap Done. Found 3 objects
2010-10-26 12:42:38.266 Reschedule requested for id -1.
2010-10-26 12:42:38.599 Scheduled 28 items in 0.3 = 0.03 match + 0.29 place
2010-10-26 12:42:49.246 ERROR: Master backend tried to connect back to itself!
2010-10-26 12:42:49.274 ERROR: Master backend tried to connect back to itself!
2010-10-26 12:42:49.291 DVBChan(1:/dev/dvb/adapter2/frontend0) Warning: Your frequency setting (12559670) is out of range. (min/max:174000000/862000000)
2010-10-26 12:42:49.295 DVBChan(1:/dev/dvb/adapter2/frontend0) Warning: Unsupported bandwidth parameter.
2010-10-26 12:42:49.306 DVBChan(1:/dev/dvb/adapter2/frontend0) Error: Tune(): Setting Frontend tuning parameters failed.
            eno: Invalid argument (22)
2010-10-26 12:42:49.347 DVBChan(1:/dev/dvb/adapter2/frontend0) Error: SetChannelByString(54053): Tuning to frequency.
2010-10-26 12:42:49.373 TVRec(1) Error: Failed to set channel to 54053. Reverting to kState_None
2010-10-26 12:46:40.762 Reschedule requested for id -1.
2010-10-26 12:46:41.048 Scheduled 28 items in 0.3 = 0.04 match + 0.24 place
2010-10-26 12:51:05.245 Reschedule requested for id -1.
2010-10-26 12:51:05.520 Scheduled 28 items in 0.3 = 0.03 match + 0.23 place
```Frontend log
```

2010-10-26 12:23:35.943 Current MythTV Schema Version (DBSchemaVer): 1254
2010-10-26 12:23:37.253 Registering Internal as a media playback plugin.
2010-10-26 12:23:37.350 Cannot load language en_gb for module mytharchive
2010-10-26 12:23:37.453 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-26 12:23:37.454 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-26 12:23:37.458 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-26 12:23:37.461 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-26 12:23:37.462 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-26 12:23:37.462 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-26 12:23:37.464 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-10-26 12:23:37.465 Cannot load language en_gb for module mythgallery
2010-10-26 12:23:37.473 Cannot load language en_gb for module mythmovies
2010-10-26 12:23:37.528 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-10-26 12:23:37.690 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-10-26 12:23:37.718 Cannot load language en_gb for module mythmusic
2010-10-26 12:23:37.745 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-10-26 12:23:37.859 Cannot load language en_gb for module mythvideo
2010-10-26 12:23:37.884 Cannot load language en_gb for module mythweather
2010-10-26 12:23:37.893 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-10-26 12:23:37.909 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-10-26 12:23:37.914 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-10-26 12:23:38.349 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-10-26 12:23:38.362 Found mainmenu.xml for theme 'MythCenter'
2010-10-26 12:23:38.902 MythContext: Connecting to backend server: 192.168.10.2:6543 (try 1 of 1)
2010-10-26 12:23:38.904 Using protocol version 23056
2010-10-26 12:23:43.001 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//info_menu.xml
2010-10-26 12:23:45.185 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/status-ui.xml
2010-10-26 12:23:45.185 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default/status-ui.xml
2010-10-26 12:23:45.322 New DB connection, total: 2
2010-10-26 12:23:45.424 Connected to database 'mythconverg' at host: 192.168.10.2
2010-10-26 12:24:25.527 Deleting UPnP client..
```.

The real problem is obviously the tuner, the other stuff is just an annoyance I'd like to get rid of.

I've learned a lot from this forum, I'd like to say thanks again for all help in the past, and of course thanks in advance.

---

### Post by ian dobson on 2010-10-26
Hi,

Something wrong with your configuration:-
ERROR: Master backend tried to connect back to itself!

The log file from the backend shows that the backend it trying to attach to the master backend. Check your computer name/ipaddress defined for the masterbackend/the box your running the backend on.

Have a look at [http://www.gossamer-threads.com/lists/mythtv/users/410783](http://www.gossamer-threads.com/lists/mythtv/users/410783)

Regards
Ian Dobson

---

### Post by bance on 2010-10-26
Thanks Ian,

So it seems it might not be something I've done thats causing this, Phew!

I was very careful during set up...... I'll follow up on those threads.

Once again thanks for your help.

Steve

---


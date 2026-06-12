---
title: "Can't get a video feed"
date: 2008-05-20
forum: Mythbuntu
---

### Post by leftler on 2008-05-20
When ever I click watch tv the screen goes black for a half second then comes back to the main page. When I do a scan for channels it can see them easyly. I have a Diamond 550 (its just a pvr-550 rebranded i think) any suggestions?


```
This is from mythfrontend.log
Starting mythfrontend.real..
2008-05-20 09:06:09.596 New DB connection, total: 2
2008-05-20 09:06:09.597 Connected to database 'mythconverg' at host: localhost
2008-05-20 09:06:09.600 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-05-20 09:06:09.600 Enabled verbose msgs:  important general
2008-05-20 09:06:09.745 Unable to parse themeinfo.xml for glass-wide
2008-05-20 09:06:09.745 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-20 09:06:10.038 Unable to parse themeinfo.xml for glass-wide
2008-05-20 09:06:10.038 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-20 09:06:10.486 Primary screen 0.
2008-05-20 09:06:10.486 Using screen 0, 1024x768 at 0,0
2008-05-20 09:06:10.489 Switching to square mode (Mythbuntu-8.04)
2008-05-20 09:06:10.508 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-05-20 09:06:10.508 lirc_init failed for mythtv, see preceding messages
2008-05-20 09:06:10.509 JoystickMenuClient Error: Joystick disabled - Failed to read /home/scott/.mythtv/joystickmenurc
2008-05-20 09:06:12.081 Specified base font 'medium' does not exist for font clock
2008-05-20 09:06:12.082 Specified base font 'medium' does not exist for font small
2008-05-20 09:06:12.082 Specified base font 'medium' does not exist for font medium
2008-05-20 09:06:12.082 Specified base font 'medium' does not exist for font large
2008-05-20 09:06:12.084 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-05-20 09:06:12.213 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-05-20 09:06:12.269 Registering Internal as a media playback plugin.
2008-05-20 09:06:12.330 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-05-20 09:06:12.390 Failed to run 'cdrecord --scanbus'
2008-05-20 09:06:12.394 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-05-20 09:06:12.398 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-05-20 09:06:12.442 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
myth2008-05-20 09:06:16.065 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-05-20 09:06:16.066 Using protocol version 40
2008-05-20 09:06:21.070 Deleting UPnP client...
```

```
This is backend.log
2008-05-20 09:06:16.066 MainServer::HandleAnnounce Monitor
2008-05-20 09:06:16.082 adding: media1 as a client (events: 0)
2008-05-20 09:06:16.083 MainServer::HandleAnnounce Monitor
2008-05-20 09:06:16.084 adding: media1 as a client (events: 1)

```

I didn't see anything that really helped in the logs, do you need me to post anything else?

---

### Post by leftler on 2008-05-20
never mind i think i got it.

---


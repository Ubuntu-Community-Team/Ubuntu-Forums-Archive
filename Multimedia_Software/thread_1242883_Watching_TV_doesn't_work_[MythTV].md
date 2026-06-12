---
title: "Watching TV doesn't work [MythTV]"
date: 2009-08-17
forum: Multimedia Software
---

### Post by DemonDomen on 2009-08-17
I've been trying to configure MythTV for IPTV. I can watch it from VLC. 
I press on the "Watch TV" button and the screen goes black for 1/4 of a second and returns back to the main screen.

The channels are in a m3u file and look like this:
```

#EXTINF:0,56 - Sky News
udp://@239.255.4.61:5002

```
I've already done this:

[LIST=1]
[*]Added a "Network record" capture card
[*]Added a video source with no grabber
[*]Scaned the channels from m3u
[/LIST]


The response to the button press is at 22:33:31.495.
Log from frontend:
```
Starting mythfrontend.real..
2009-08-17 22:33:14.321 New DB connection, total: 2
2009-08-17 22:33:14.322 Connected to database 'mythconverg' at host: localhost
2009-08-17 22:33:14.326 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-08-17 22:33:14.326 Enabled verbose msgs:  important general
2009-08-17 22:33:16.069 No theme dir: /home/domen/.mythtv/themes/ProjectGrayhem
2009-08-17 22:33:16.072 Primary screen 0.
2009-08-17 22:33:16.076 Using screen 0, 1600x1200 at 0,0
2009-08-17 22:33:16.077 No theme dir: /home/domen/.mythtv/themes/ProjectGrayhem
2009-08-17 22:33:16.077 Switching to square mode (ProjectGrayhem)
2009-08-17 22:33:16.170 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-08-17 22:33:16.171 lirc_init failed for mythtv, see preceding messages
2009-08-17 22:33:16.172 JoystickMenuClient Error: Joystick disabled - Failed to read /home/domen/.mythtv/joystickmenurc
2009-08-17 22:33:21.195 Specified base font 'medium' does not exist for font clock
2009-08-17 22:33:21.198 Specified base font 'medium' does not exist for font small
2009-08-17 22:33:21.199 Specified base font 'medium' does not exist for font medium
2009-08-17 22:33:21.199 Specified base font 'medium' does not exist for font large
2009-08-17 22:33:21.201 Loading from: /usr/share/mythtv/themes/ProjectGrayhem/base.xml
2009-08-17 22:33:21.574 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-08-17 22:33:21.634 Registering Internal as a media playback plugin.
2009-08-17 22:33:21.866 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-08-17 22:33:22.087 MythMusic adding CD-Writer: 2,0,0 -- DVD_RW ND-3550A 
2009-08-17 22:33:22.218 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-08-17 22:33:22.346 No theme dir: /home/domen/.mythtv/themes/ProjectGrayhem
2009-08-17 22:33:31.495 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-17 22:33:31.498 Using protocol version 40
2009-08-17 22:33:34.750 Deleting UPnP client...
```

Log from backend:
```
2009-08-17 22:33:31.499 MainServer::HandleAnnounce Monitor
2009-08-17 22:33:31.504 adding: domen-desktop as a client (events: 0)
2009-08-17 22:33:31.506 MainServer::HandleAnnounce Monitor
2009-08-17 22:33:31.507 adding: domen-desktop as a client (events: 1)
```

---


---
title: "Problem getting tuner to work"
date: 2008-11-17
forum: Mythbuntu
---

### Post by Tzizimime on 2008-11-17
I recently set up a computer to use as a PVR, and I've been unable to watch live TV or record shows from an OTA antenna. All I get is a screen filled with static and the station information for whatever station I set it on.

I'm using a Hauppauge HVR-1600 (having followed the instructions at [http://www.mythtv.org/wiki/index.php/Hauppauge_hvr-1600](http://www.mythtv.org/wiki/index.php/Hauppauge_hvr-1600) to set it up with MythTV) and have a Radeon HD3650 graphics card.

I'm running Mythbuntu 8.10, kernel 2.6.27-7-generic. I'm using the AMD supplied drivers for the graphics card.

I get the following error information when I try to run it
```

2008-11-16 19:46:05.930 Using runtime prefix = /usr
QServerSocket: failed to bind or listen to the socket
2008-11-16 19:46:05.931 MediaRenderer::HttpServer Create Error
2008-11-16 19:46:05.940 XScreenSaver support enabled
2008-11-16 19:46:05.940 DPMS is active.
2008-11-16 19:46:05.941 Empty LocalHostName.
2008-11-16 19:46:05.941 Using localhost value of Compbox
2008-11-16 19:46:05.946 New DB connection, total: 1
2008-11-16 19:46:05.949 Connected to database 'mythconverg' at host: localhost
2008-11-16 19:46:05.950 Closing DB connection named 'DBManager0'
2008-11-16 19:46:05.951 Primary screen 0.
2008-11-16 19:46:05.951 Connected to database 'mythconverg' at host: localhost
2008-11-16 19:46:05.952 Using screen 0, 1360x768 at 0,0
2008-11-16 19:46:05.957 New DB connection, total: 2
2008-11-16 19:46:05.958 Connected to database 'mythconverg' at host: localhost
2008-11-16 19:46:05.959 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-11-16 19:46:05.959 Enabled verbose msgs:  important general
2008-11-16 19:46:06.337 No theme dir: /home/paracelsus/.mythtv/themes/Mythbuntu-8.04
2008-11-16 19:46:06.338 Primary screen 0.
2008-11-16 19:46:06.338 Using screen 0, 1360x768 at 0,0
2008-11-16 19:46:06.338 No theme dir: /home/paracelsus/.mythtv/themes/Mythbuntu-8.04
[COLOR="Red"]2008-11-16 19:46:06.339 Switching to square mode (Mythbuntu-8.04)
X Error: BadRequest (invalid request code or no such operation) 1
  Major opcode:  143
  Minor opcode:  19
  Resource id:  0x2800001
X Error: BadRequest (invalid request code or no such operation) 1
  Major opcode:  143
  Minor opcode:  19
  Resource id:  0x2800001
X Error: BadRequest (invalid request code or no such operation) 1
  Major opcode:  143
  Minor opcode:  14
  Resource id:  0x2800001
X Error: BadRequest (invalid request code or no such operation) 1
  Major opcode:  143
  Minor opcode:  19
  Resource id:  0x2800001
X Error: BadRequest (invalid request code or no such operation) 1
  Major opcode:  143
  Minor opcode:  19
  Resource id:  0x2800001
X Error: BadRequest (invalid request code or no such operation) 1
  Major opcode:  143
  Minor opcode:  14
  Resource id:  0x2800001
X Error: BadRequest (invalid request code or no such operation) 1
  Major opcode:  143
  Minor opcode:  19
  Resource id:  0x2800001
X Error: BadRequest (invalid request code or no such operation) 1
  Major opcode:  143
  Minor opcode:  19
  Resource id:  0x2800001
X Error: BadRequest (invalid request code or no such operation) 1
  Major opcode:  143
  Minor opcode:  14
  Resource id:  0x2800001
2008-11-16 19:46:06.344 Using the Qt painter
2008-11-16 19:46:06.344 JoystickMenuClient Error: Joystick disabled - Failed to read /home/paracelsus/.mythtv/joystickmenurc
2008-11-16 19:46:06.345 lirc init success using configuration file: /home/paracelsus/.mythtv/lircrc
X Error: BadRequest (invalid request code or no such operation) 1
  Major opcode:  143
  Minor opcode:  19
  Resource id:  0x28
X Error: BadRequest (invalid request code or no such operation) 1
  Major opcode:  143
  Minor opcode:  19
  Resource id:  0x28
X Error: BadRequest (invalid request code or no such operation) 1
  Major opcode:  143
  Minor opcode:  14
  Resource id:  0x28[/COLOR]
2008-11-16 19:46:06.935 Specified base font 'medium' does not exist for font clock
2008-11-16 19:46:06.935 Specified base font 'medium' does not exist for font small
2008-11-16 19:46:06.935 Specified base font 'medium' does not exist for font medium
2008-11-16 19:46:06.935 Specified base font 'medium' does not exist for font large
2008-11-16 19:46:06.936 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-11-16 19:46:07.002 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-16 19:46:07.023 Registering Internal as a media playback plugin.
2008-11-16 19:46:07.101 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-16 19:46:07.125 Failed to run 'cdrecord --scanbus'
2008-11-16 19:46:07.128 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-11-16 19:46:07.130 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-11-16 19:46:07.152 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to bind for SIP connection 192.168.1.69
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-11-16 19:46:07.209 No theme dir: /home/paracelsus/.mythtv/themes/Mythbuntu-8.04
2008-11-16 19:46:45.542 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-11-16 19:46:45.542 Using protocol version 40
^[[B2008-11-16 19:46:52.150 Deleting UPnP client...
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server "0&#65533;E"
      after 37454 requests (37453 known processed) with 0 events remaining.

```

When I try to run Xine itself I also get an error code
```

This is xine (X11 gui) - a free video player v0.99.6cvs.
(c) 2000-2007 The xine Team.
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  1725
  Current serial number in output stream:  1725

```

I've tried uninstalling and reinstalling xine with no success,

---

### Post by ian dobson on 2008-11-17
Hi,

Looks like a graphic card driver problem. Try using the opensource or closed source drivers. You can select/configure the driver in the mythbuntu control center.

Exactly which graphic card do you have?

Regards
Ian Dobson

---

### Post by Tzizimime on 2008-11-17
I'm using a Sapphire Radeon HD 3650 graphics card. After using the control center to get the proprietary driver for the card, I've found that Xine works fine, so that seemed to help.

However, now whenever I am in any MythTV screen the display becomes fragmented, lines of broken image cut by dead space. Moving to the TV view I see static cut by this dead space.

---


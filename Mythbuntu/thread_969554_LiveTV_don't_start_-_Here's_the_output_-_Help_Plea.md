---
title: "LiveTV don't start - Here's the output - Help Please"
date: 2008-11-03
forum: Mythbuntu
---

### Post by impossibilechecisiaquesto on 2008-11-03
Hi, when i strat Live TV the screen became black for 5/6 seconds and then return to the menu.

Here's the output of mythfrontend

```

master@master-desktop:~$ mythfrontend
2008-11-03 20:19:46.383 Using runtime prefix = /usr
2008-11-03 20:19:46.578 XScreenSaver support enabled
2008-11-03 20:19:46.579 DPMS is active.
2008-11-03 20:19:46.580 Empty LocalHostName.
2008-11-03 20:19:46.581 Using localhost value of master-desktop
2008-11-03 20:19:46.623 New DB connection, total: 1
2008-11-03 20:19:46.634 Connected to database 'mythconverg' at host: localhost
2008-11-03 20:19:46.643 Closing DB connection named 'DBManager0'
2008-11-03 20:19:46.666 Primary screen 0.
2008-11-03 20:19:46.671 Connected to database 'mythconverg' at host: localhost
2008-11-03 20:19:46.675 Using screen 0, 1024x768 at 0,0
2008-11-03 20:19:46.724 New DB connection, total: 2
2008-11-03 20:19:46.725 Connected to database 'mythconverg' at host: localhost
2008-11-03 20:19:46.732 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-11-03 20:19:46.738 Enabled verbose msgs:  important general
2008-11-03 20:19:47.128 Unable to parse themeinfo.xml for glass-wide
2008-11-03 20:19:47.128 The theme (glass-wide) is missing a themeinfo.xml file
2008-11-03 20:19:47.677 Unable to parse themeinfo.xml for glass-wide
2008-11-03 20:19:47.677 The theme (glass-wide) is missing a themeinfo.xml file
2008-11-03 20:19:48.479 No theme dir: /home/master/.mythtv/themes/Mythbuntu-8.04
2008-11-03 20:19:48.482 Primary screen 0.
2008-11-03 20:19:48.483 Using screen 0, 1024x768 at 0,0
2008-11-03 20:19:48.487 No theme dir: /home/master/.mythtv/themes/Mythbuntu-8.04
2008-11-03 20:19:48.489 Switching to square mode (Mythbuntu-8.04)
AllocateDmaBuffer fail
X Error: BadAlloc (insufficient resources for operation) 11
  Major opcode:  161
  Minor opcode:  3
  Resource id:  0x3000001
X Error: GLXBadContext 180
  Major opcode:  161
  Minor opcode:  6
  Resource id:  0x3000008
2008-11-03 20:19:48.646 Using the Qt painter
2008-11-03 20:19:48.653 lirc init success using configuration file: /home/master/.mythtv/lircrc
2008-11-03 20:19:48.666 JoystickMenuClient Error: Joystick disabled - Failed to read /home/master/.mythtv/joystickmenurc
X Error: GLXBadContext 180
  Major opcode:  161
  Minor opcode:  5
  Resource id:  0x3000008
QGLContext::makeCurrent(): Failed.
X Error: GLXBadContext 180
  Major opcode:  161
  Minor opcode:  5
  Resource id:  0x3000008
QGLContext::makeCurrent(): Failed.
2008-11-03 20:19:54.787 Specified base font 'medium' does not exist for font clock
2008-11-03 20:19:54.787 Specified base font 'medium' does not exist for font small
2008-11-03 20:19:54.787 Specified base font 'medium' does not exist for font medium
2008-11-03 20:19:54.788 Specified base font 'medium' does not exist for font large
2008-11-03 20:19:54.791 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-11-03 20:19:55.063 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-03 20:19:55.266 Registering Internal as a media playback plugin.
2008-11-03 20:19:55.452 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-03 20:19:55.747 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.2:5060 NAT address 192.168.1.2
SIP: Cannot register; proxy, username or password not set
2008-11-03 20:19:56.160 No theme dir: /home/master/.mythtv/themes/Mythbuntu-8.04
2008-11-03 20:20:02.119 Connecting to backend server: 192.168.1.2:6543 (try 1 of 5)
2008-11-03 20:20:02.122 Using protocol version 40
2008-11-03 20:20:02.160 TV: Attempting to change from None to WatchingLiveTV
2008-11-03 20:20:02.162 Using protocol version 40
2008-11-03 20:20:09.194 MythSocket(8337ed8:22): readStringList: Error, timeout (quick).
2008-11-03 20:20:09.194 RemoteEncoder::SendReceiveStringList(): No response.
2008-11-03 20:20:09.196 GetEntryAt(-1) failed.
2008-11-03 20:20:09.198 EntryToProgram(0@gio gen 1 01:00:00 1970) failed to get pginfo
2008-11-03 20:20:09.198 TV Error: LiveTV not successfully started
2008-11-03 20:20:09.199 TV Error: LiveTV not successfully started
2008-11-03 20:20:09.203 TV: Deleting TV Chain in destructor
2008-11-03 20:20:09.226 DPMS Deactivated 
2008-11-03 20:20:09.228 DPMS Reactivated.

```

Need anything else?

---

### Post by raptorjr on 2008-11-03
I had a similar problem. It always happend after a restart. But if i killed the autostarted mythbackend and opened a terminal and started mythbackend manually everything worked.

---

### Post by impossibilechecisiaquesto on 2008-11-04
mmm.. thanks i try and let we know

---

### Post by impossibilechecisiaquesto on 2008-11-05
Don't work at all.

Any others have any soggestion?? Where the problem could came from? PVR-150, databese don't work?

---

### Post by impossibilechecisiaquesto on 2008-11-05
I have an Update, the Pvr-150 is working, i tryed

cat /dev/video0 > /tmp/test.mpeg and opening that file is ok.

Now i think the problem is inside mythtv?? A Bug or what??

Can someone help me?

---

### Post by impossibilechecisiaquesto on 2008-11-05
Here's the output of the backend 
```
master@master-desktop:~$ mythbackend 
2008-11-05 15:00:51.499 Using runtime prefix = /usr
2008-11-05 15:00:51.501 Empty LocalHostName.
2008-11-05 15:00:51.501 Using localhost value of master-desktop
2008-11-05 15:00:51.553 New DB connection, total: 1
2008-11-05 15:00:51.581 Connected to database 'mythconverg' at host: localhost
2008-11-05 15:00:51.587 Closing DB connection named 'DBManager0'
2008-11-05 15:00:51.588 Connected to database 'mythconverg' at host: localhost
2008-11-05 15:00:51.592 New DB connection, total: 2
2008-11-05 15:00:51.593 Connected to database 'mythconverg' at host: localhost
2008-11-05 15:00:51.597 Current Schema Version: 1214
Starting up as the master server.
2008-11-05 15:00:51.642 New DB connection, total: 3
2008-11-05 15:00:51.644 Connected to database 'mythconverg' at host: localhost
2008-11-05 15:00:55.468 ret_pid(0) child(9372) status(0x0)
2008-11-05 15:00:56.468 ret_pid(0) child(9372) status(0x0)
2008-11-05 15:00:57.469 ret_pid(0) child(9372) status(0x0)
2008-11-05 15:00:58.469 ret_pid(9372) child(9372) status(0x0)
2008-11-05 15:00:58.469 External Tuning program exited with no error
2008-11-05 15:00:58.501 New DB scheduler connection
2008-11-05 15:00:58.502 Connected to database 'mythconverg' at host: localhost
TV is defined, but isn't attached to a cardinput.
2008-11-05 15:00:59.829 Main::Registering HttpStatus Extension
2008-11-05 15:00:59.829 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-11-05 15:00:59.829 Enabled verbose msgs:  important general
2008-11-05 15:00:59.833 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-05 15:01:01.511 Reschedule requested for id -1.
2008-11-05 15:01:01.715 Scheduled 0 items in 0.2 = 0.01 match + 0.18 place
2008-11-05 15:01:01.775 Seem to be woken up by USER
2008-11-05 15:01:08.983 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/MULTIMEDIA/VIDEO/:
2008-11-05 15:01:12.059 UPnpMedia: BuildMediaMap Done. Found 1222 objects
2008-11-05 15:02:16.522 MainServer::HandleAnnounce Monitor
2008-11-05 15:02:16.522 adding: master-desktop as a client (events: 0)
2008-11-05 15:02:16.524 MainServer::HandleAnnounce Monitor
2008-11-05 15:02:16.524 adding: master-desktop as a client (events: 1)
2008-11-05 15:02:16.571 MainServer::HandleAnnounce Playback
2008-11-05 15:02:16.572 adding: master-desktop as a client (events: 0)
2008-11-05 15:02:16.605 TVRec(1): Changing from None to WatchingLiveTV
2008-11-05 15:02:16.638 TVRec(1): HW Tuner: 1->1
2008-11-05 15:02:20.749 ret_pid(0) child(9433) status(0x0)
2008-11-05 15:02:21.749 ret_pid(0) child(9433) status(0x0)
2008-11-05 15:02:22.750 ret_pid(0) child(9433) status(0x0)
2008-11-05 15:02:23.750 ret_pid(9433) child(9433) status(0x0)
2008-11-05 15:02:23.750 External Tuning program exited with no error
2008-11-05 15:02:25.373 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
			is not supported by ivtv driver, using 48000 Hz instead.
2008-11-05 15:02:25.399 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-11-05 15:02:25.531 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-11-05 15:02:25.641 TVRec(1): Changing from WatchingLiveTV to None
2008-11-05 15:02:26.489 Finished recording Come tu mi vuoi: channel 1101
2008-11-05 15:02:26.498 MythSocket(831d450:-1): writeStringList: Error, socket went unconnected.
2008-11-05 15:04:25.540 Expiring 0 MBytes for 1101 @ mer nov 5 14:30:00 2008 => Come tu mi vuoi



```

Hope it could help.

---

### Post by mrand on 2008-11-05
Two things:

Have you tried a different theme?
```

2008-11-03 20:19:47.677 Unable to parse themeinfo.xml for glass-wide
2008-11-03 20:19:47.677 The theme (glass-wide) is missing a themeinfo.xml file 
```

Will it successfully perform a scheduled recording?
It might be that your channel change script is taking too long.  Try not using one (temporarily), or launch it to the background, or reduce delays (if you can).

[INDENT]   Marc[/INDENT]

---

### Post by mjezell on 2008-11-05
Had the same problem with clean install of mythbuntu 8.10 alternate amd64. After changing all myth dir (/var/lib/mythtv/recordings, music, videos, pictures) to have read/write privliges for all users live tv started working. Hope this helps.

---


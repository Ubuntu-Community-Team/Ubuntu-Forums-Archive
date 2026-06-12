---
title: "Mythfrontend watching Live TV causes MythBackend to go defunct"
date: 2008-03-20
forum: Mythbuntu
---

### Post by s73v3r on 2008-03-20
So I'm firing up MythFrontend to watch some tv, but whenever I go to select Live TV, the screen goes black for a minute or so, then goes back to the menu. The log for MythFrontend looks like this:

```

2008-03-20 16:43:36.196 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-20 16:43:36.729 XScreenSaver support enabled
2008-03-20 16:43:36.730 DPMS is active.
2008-03-20 16:43:36.749 Empty LocalHostName.
2008-03-20 16:43:36.749 Using localhost value of professor
2008-03-20 16:43:36.800 New DB connection, total: 1
2008-03-20 16:43:36.844 Connected to database 'mythconverg' at host: localhost
2008-03-20 16:43:36.847 Closing DB connection named 'DBManager0'
2008-03-20 16:43:36.848 Total desktop dim: 1280x1024, with 1 screen[s].
2008-03-20 16:43:36.849 Connected to database 'mythconverg' at host: localhost
2008-03-20 16:43:36.866 Using screen 0, 1280x1024 at 0,0
2008-03-20 16:43:36.883 New DB connection, total: 2
2008-03-20 16:43:36.884 Connected to database 'mythconverg' at host: localhost
2008-03-20 16:43:36.888 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-03-20 16:43:36.892 Enabled verbose msgs:  important general
2008-03-20 16:43:37.545 Total desktop dim: 1280x1024, with 1 screen[s].
2008-03-20 16:43:37.546 Using screen 0, 1280x1024 at 0,0
2008-03-20 16:43:37.548 Switching to square mode (G.A.N.T)
2008-03-20 16:43:37.582 Using the Qt painter
2008-03-20 16:43:37.598 JoystickMenuClient Error: Joystick disabled - Failed to read /home/professor/.mythtv/joystickmenurc
2008-03-20 16:43:37.637 lirc init success using configuration file: /home/professor/.mythtv/lircrc
2008-03-20 16:43:39.182 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2008-03-20 16:43:39.412 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-03-20 16:43:39.495 Registering Internal as a media playback plugin.
2008-03-20 16:43:47.056 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/status-ui.xml
2008-03-20 16:43:48.808 Connecting to backend server: 192.168.2.5:6543 (try 1 of 5)
2008-03-20 16:43:48.810 Using protocol version 40
2008-03-20 16:43:57.118 TV: Attempting to change from None to WatchingLiveTV
2008-03-20 16:43:57.119 Using protocol version 40
2008-03-20 16:43:59.198 DPMS Deactivated
2008-03-20 16:44:39.130 TV Error: StartRecorder() -- timed out waiting for recorder to start
2008-03-20 16:44:39.130 TV Error: LiveTV not successfully started
2008-03-20 16:44:39.191 TV: Deleting TV Chain in destructor
2008-03-20 16:44:39.195 DPMS Reactivated.
2008-03-20 16:45:27.606 MythSocket(82ad760:21): readStringList: Error, timeout.
2008-03-20 16:45:27.606 Connection to backend server lost
2008-03-20 16:45:27.612 Connecting to backend server: 192.168.2.5:6543 (try 1 of 5)
2008-03-20 16:45:34.618 MythSocket(82ad760:21): readStringList: Error, timeout (quick).
2008-03-20 16:45:34.618 Unexpected response to MYTH_PROTO_VERSION:
2008-03-20 16:45:34.618 Reconnection to backend server failed
2008-03-20 16:46:17.825 Deleting UPnP client...

```

As you can see, there's a timeout waiting for the backend to start recording. Here is the companion log from the backend, although it doesn't show the backend starting up.
```

2008-03-20 16:11:32.392 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-03-20 16:12:06.514 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-03-20 16:12:06.520 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-03-20 16:26:32.431 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-03-20 16:41:32.483 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-03-20 16:42:06.523 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-03-20 16:42:06.526 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-03-20 16:43:48.811 MainServer::HandleAnnounce Monitor
2008-03-20 16:43:48.815 adding: professor as a client (events: 0)
2008-03-20 16:43:48.817 MainServer::HandleAnnounce Monitor
2008-03-20 16:43:48.817 adding: professor as a client (events: 1)
2008-03-20 16:43:57.120 MainServer::HandleAnnounce Playback
2008-03-20 16:43:57.123 adding: professor as a client (events: 0)
2008-03-20 16:43:57.146 TVRec(1): Changing from None to WatchingLiveTV
2008-03-20 16:43:57.225 TVRec(1): HW Tuner: 1->1
2008-03-20 16:43:59.032 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
strange error flushing buffer ...

```

I've been told that the "strange error flushing buffer" is mostly a LAME MP3 error, but I'm not sure.

Usually after attempting this, the backend process will go defunct, and the only way I've been able to fix it is to restart the computer.

I tried recording a program, to see if maybe there's just a problem with the Live TV output. Attempting to watch the recording in MythFrontend resulted in that program hanging, with the log saying it couldn't find the file. I myself also could not locate the file.  

I have a Leadtek WinFast 2000XP tuner card that has been identified as a bttv card, and I believe I have that set up properly. I know the card works, because I can get TV just fine through TvTime. Its MythTV that's giving me the problems.

Any help trying to get this to work would be greatly appreciated.

---

### Post by volkswagner on 2008-03-20
Before selecting live TV.  Check and see what the status of your tuner is.
Information Center >System information >Tuner Status.

Is the frontend on the same machine as the backend?

What are you settings for playback?

---

### Post by s73v3r on 2008-03-20
The status says that the tuner is not recording. The frontend is both on the same machine, and on others on the network, however I've been concentrating on the one on the same machine for testing purposes. 

The playback settings are set to use MPEG-4 instead of RTjpeg (or whatever its called). They also have audio on MP3 with a sampling rate of 48000.

---

### Post by volkswagner on 2008-03-21
Wondering if other frontends show the tuner as available.

```
2008-03-20 16:43:36.749 Empty LocalHostName.
```

I was getting this error until I set all lan connected machines to use static ip in network manager.

---

### Post by majoridiot on 2008-03-21
> **s73v3r said:**
> The playback settings are set to use MPEG-4 instead of RTjpeg (or whatever its called). They also have audio on MP3 with a sampling rate of 48000.

have you tried rtjpeg to see if that works any better?

---

### Post by s73v3r on 2008-03-21
When trying to use MythFrontend on my laptop, it does show that same message in the log. However, a couple lines down, it does say Connected to database 'mythconverg' at the machine I have it on. However, it also was a lot slower to respond. Here's the end of the log, up until I quit the program.
```
Zoidberg:MacOS stevo$ ./MythFrontend 
Qt: QApplication: Warning argv[0] == './MythFrontend' is relative.
In order to dispatch events correctly Mac OS X may require applications to be run with the *full* path to the executable.
2008-03-21 10:17:31.801 Using runtime prefix = /Volumes/MythFrontend/MythFrontend.app/Contents/Resources, libdir = /Volumes/MythFrontend/MythFrontend.app/Contents/Resources/lib
2008-03-21 10:17:32.396 Empty LocalHostName.
2008-03-21 10:17:32.397 Using localhost value of Zoidberg.local
2008-03-21 10:17:32.397 Testing network connectivity to 192.168.2.5
2008-03-21 10:17:32.411 New DB connection, total: 1
2008-03-21 10:17:32.420 Connected to database 'mythconverg' at host: 192.168.2.5
2008-03-21 10:17:32.425 Closing DB connection named 'DBManager0'
2008-03-21 10:17:32.425 Total desktop dim: 1280x800, with 1 screen[s].
2008-03-21 10:17:32.431 Connected to database 'mythconverg' at host: 192.168.2.5
2008-03-21 10:17:32.436 Using screen 0, 1280x800 at 0,0
2008-03-21 10:17:32.464 New DB connection, total: 2
2008-03-21 10:17:32.471 Connected to database 'mythconverg' at host: 192.168.2.5
2008-03-21 10:17:32.480 MythFrontend version: 0.21.20080304-1 www.mythtv.org
2008-03-21 10:17:32.480 Enabled verbose msgs:  important general
2008-03-21 10:17:33.213 Total desktop dim: 1280x800, with 1 screen[s].
2008-03-21 10:17:33.216 Using screen 0, 1280x800 at 0,0
2008-03-21 10:17:33.219 Switching to square mode (G.A.N.T)
2008-03-21 10:17:33.248 Using the Qt painter
2008-03-21 10:17:34.154 Loading from: /Volumes/MythFrontend/MythFrontend.app/Contents/Resources/share/mythtv/themes/G.A.N.T/base.xml
2008-03-21 10:17:34.232 Loading from: /Volumes/MythFrontend/MythFrontend.app/Contents/Resources/share/mythtv/themes/default/base.xml
2008-03-21 10:17:34.493 Registering Internal as a media playback plugin.
2008-03-21 10:17:34.703 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-03-21 10:17:34.815 Failed to run 'cdrecord --scanbus'
2008-03-21 10:17:34.818 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-03-21 10:17:34.820 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-03-21 10:17:34.945 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-03-21 10:18:15.161 Connecting to backend server: 192.168.2.5:6543 (try 1 of 5)
2008-03-21 10:18:22.171 MythSocket(14871de0:13): readStringList: Error, timeout (quick).
2008-03-21 10:18:22.171 Unexpected response to MYTH_PROTO_VERSION: 
2008-03-21 10:18:22.171 Connecting to backend server: 192.168.2.5:6543 (try 1 of 5)
2008-03-21 10:18:29.173 MythSocket(14871de0:13): readStringList: Error, timeout (quick).
2008-03-21 10:18:29.174 Unexpected response to MYTH_PROTO_VERSION: 
^[[A^[[B2008-03-21 10:18:37.506 Connecting to backend server: 192.168.2.5:6543 (try 1 of 5)
2008-03-21 10:18:44.510 MythSocket(148621b0:13): readStringList: Error, timeout (quick).
2008-03-21 10:18:44.510 Unexpected response to MYTH_PROTO_VERSION: 
2008-03-21 10:20:16.595 Deleting UPnP client...

```

---

### Post by s73v3r on 2008-03-21
> **majoridiot said:**
> have you tried rtjpeg to see if that works any better?

It was originally on RTJpeg. I was still having this same problem, and then I switched to MPEG-4.

---

### Post by majoridiot on 2008-03-21
i missed this bit in your logs...

> **s73v3r said:**
> 2008-03-21 10:18:15.161 Connecting to backend server: 192.168.2.5:6543 (try 1 of 5)
2008-03-21 10:18:22.171 MythSocket(14871de0:13): readStringList: Error, timeout (quick).
2008-03-21 10:18:22.171 Unexpected response to MYTH_PROTO_VERSION: 
2008-03-21 10:18:22.171 Connecting to backend server: 192.168.2.5:6543 (try 1 of 5)
2008-03-21 10:18:29.173 MythSocket(14871de0:13): readStringList: Error, timeout (quick).
2008-03-21 10:18:29.174 Unexpected response to MYTH_PROTO_VERSION: 
^[[A^[[B2008-03-21 10:18:37.506 Connecting to backend server: 192.168.2.5:6543 (try 1 of 5)
2008-03-21 10:18:44.510 MythSocket(148621b0:13): readStringList: Error, timeout (quick).
2008-03-21 10:18:44.510 Unexpected response to MYTH_PROTO_VERSION: 
2008-03-21 10:20:16.595 Deleting UPnP client...


this error generally occurs when you have two different versions of mythtv trying to talk to each other.
are your frontend and backend running the same version of myth?

this will also happen if you changed the address of the backend server in mythtv-setup "General" from
127.0.0.1 and did not change the address of the database field to match.

---

### Post by laga on 2008-03-21
> **majoridiot said:**
> i missed this bit in your logs...



this error generally occurs when you have two different versions of mythtv trying to talk to each other.
are your frontend and backend running the same version of myth?

I think I've also seen this error when the backends are not configured correctly.. make sure you put the correct IP addresses in those two boxes in mythtv-setup.

---

### Post by s73v3r on 2008-03-21
The frontend running on my laptop says its the 0.21 release, while the backend and frontend on the desktop are the latest version in the repositories. I'm not sure what that version is, but it could easily be 0.20.

However, shouldn't the two that are on the same machine be the same version? So why would that be foobarring?

---

### Post by majoridiot on 2008-03-21
> **s73v3r said:**
> The frontend running on my laptop says its the 0.21 release, while the backend and frontend on the desktop are the latest version in the repositories. I'm not sure what that version is, but it could easily be 0.20.

However, shouldn't the two that are on the same machine be the same version? So why would that be foobarring?

i hit post too quickly before finishing the thought... you might have missed the edit:

this will also happen if you changed the address of the backend server in mythtv-setup "General" from
127.0.0.1 and did not change the address of the database field to match.

.21 uses a different protocol than .20, so you will need to upgrade the backend or re-install .20 on the
laptop.

---

### Post by s73v3r on 2008-03-21
Where can I check the address the database field is using? Mythtv-setup has the Local Backend and then Master Backend (there being only one backend in this setup) as the IP address of the machine.

---

### Post by majoridiot on 2008-03-21
> **s73v3r said:**
> Where can I check the address the database field is using? Mythtv-setup has the Local Backend and then Master Backend (there being only one backend in this setup) as the IP address of the machine.

run mythtv-setup... under 1. General, first page

the first field "ip address for mythtv" should be the address of that machine on your local network.

the fifth field, "master server ip address" should match.

if you are not certain of the ip-

```
$ ifconfig
```

---

### Post by s73v3r on 2008-03-21
Then yes, they both are the same, and are a valid IP on my home network.

---

### Post by sketchysunday on 2008-03-23
I'm getting the same problem. Just went to watch tv as usual, the screen turns black for a second then goes back to the menu. Frontend and Backend on same machine. PVR-500. Was set to 192.168.0.2 but I changed both to 127.0.0.1...same problem. Deleted tuners in myth-setup. Truncated capturecard and cardinput. Added tuners in myth-setup...same problem. Everything else seems fine, don't know what went wrong to not make it work all of a sudden.

---

### Post by majoridiot on 2008-03-23
> **sketchysunday said:**
> I'm getting the same problem. Just went to watch tv as usual, the screen turns black for a second then goes back to the menu. Frontend and Backend on same machine. PVR-500. Was set to 192.168.0.2 but I changed both to 127.0.0.1...same problem. Deleted tuners in myth-setup. Truncated capturecard and cardinput. Added tuners in myth-setup...same problem. Everything else seems fine, don't know what went wrong to not make it work all of a sudden.

what do you see in /var/log/mythtv/mythbackend.log and frontend.log?  any errors you see there worth sharing?

---

### Post by sketchysunday on 2008-03-23
SOLVED! thank you....mythbackend.log did say tables *inuseprogram* and *tvchain* were crashed and should be repaired. I used phpmyadmin to repair them and now TV works fine.

---

### Post by majoridiot on 2008-03-23
> **sketchysunday said:**
> SOLVED! thank you....mythbackend.log did say tables *inuseprogram* and *tvchain* were crashed and should be repaired. I used phpmyadmin to repair them and now TV works fine.

excellent!  the logs do help from time to time ;)

---

### Post by s73v3r on 2008-03-30
Sorry that I haven't posted in a while, but I got busy with work and stuff and haven't had time to work on my problem, which is still persisting.

After reading the current replies, it looks like the database could be a culprit, but after repairing/optimizing the tables a dozen times with no results, I don't think so. I've also read on other forums that the proprietary nVidia drivers can do bad things, so I disabled them, to no avail.

When I try to switch to Live TV, the last thing I see in the mythbackend.log is the line "strange error flushing buffer." Any idea what this means?

Could someone please help?

---

### Post by s73v3r on 2008-03-30
I thought I'd try to get some more info on the problem, so I ran both the backend and frontend with higher levels of debug info (-v all,nodatabase) and captured it, hoping it might help. Attached should be the log files.

---

### Post by Fjodor on 2008-04-02
Just wanted to chime in and say that I too have this problem. Only thing that seems amiss in the logs is the "strange error flushing buffer"-thing, which mythtv docs say is harmless :-(

/Fjodor

---


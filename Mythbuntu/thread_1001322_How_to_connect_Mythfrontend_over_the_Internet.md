---
title: "How to connect Mythfrontend over the Internet?"
date: 2008-12-03
forum: Mythbuntu
---

### Post by kwilliam on 2008-12-03
So, I'm trying to connect to my MythTV box over the Internet. It worked great on my LAN at home (even wirelessly, which surprised me), but now I'd like to access it from college. I can access MythWeb, but when I start the frontend on my laptop, it seems to be using the wrong IP address. In the frontend General settings, I've changed the Database Server Settings Hostname to jupitermythtv.dyndns.tv. It seems to connect to the MySQL database alright initially, but when it tries to connect to the backend server it appears to be using the old local network IP, 192.168.1.5. Is there some other place where I need to change the IP address?? Also, I'm aware that the way I'm doing this (port forwarding MySQL and friends) isn't very secure. I'm vaguely aware of a thing called VPN which seems like it might be a better solution, as it would make my laptop appear to be on the local LAN and I could still use 192.168.1.5 as the address for the MythTV box, but I don't know how to set up a VPN.

```
[william@Swordfish:~] mythfrontend
2008-12-03 20:52:55.945 Using runtime prefix = /usr
2008-12-03 20:52:56.507 DPMS is active.            
2008-12-03 20:52:56.508 Using localhost value of Swordfish
2008-12-03 20:52:56.532 New DB connection, total: 1       
2008-12-03 20:52:56.804 Connected to database 'mythconverg' at host: mythtv.dyndns.com                                                                        
2008-12-03 20:52:56.850 Closing DB connection named 'DBManager0'                  
2008-12-03 20:52:56.852 Primary screen 0.                                         
2008-12-03 20:52:57.024 Connected to database 'mythconverg' at host: mythtv.dyndns.com                                                                       
2008-12-03 20:52:57.072 Using screen 0, 1680x1050 at 0,0                          
2008-12-03 20:52:57.609 New DB connection, total: 2                               
2008-12-03 20:52:57.778 Connected to database 'mythconverg' at host: mythtv.dyndns.com                                                                        
2008-12-03 20:52:58.024 mythfrontend version: 0.21.20080304-1 www.mythtv.org      
2008-12-03 20:52:58.024 Enabled verbose msgs:  important general                  
2008-12-03 20:53:01.629 Unable to parse themeinfo.xml for glass-wide              
2008-12-03 20:53:01.629 The theme (glass-wide) is missing a themeinfo.xml file    
2008-12-03 20:53:05.082 Unable to parse themeinfo.xml for glass-wide              
2008-12-03 20:53:05.082 The theme (glass-wide) is missing a themeinfo.xml file    
2008-12-03 20:53:11.418 No theme dir: /home/william/.mythtv/themes/blootube-wide  
2008-12-03 20:53:11.473 Primary screen 0.                                         
2008-12-03 20:53:11.511 Using screen 0, 1680x1050 at 0,0                          
2008-12-03 20:53:11.554 No theme dir: /home/william/.mythtv/themes/blootube-wide  
2008-12-03 20:53:11.555 Switching to wide mode (blootube-wide)                    
2008-12-03 20:53:12.400 Using the Qt painter                                      
mythtv: could not connect to socket                                               
mythtv: No such file or directory                                                 
2008-12-03 20:53:12.401 lirc_init failed for mythtv, see preceding messages       
2008-12-03 20:53:12.401 JoystickMenuClient Error: Joystick disabled - Failed to read /home/william/.mythtv/joystickmenurc                                           
2008-12-03 20:53:40.908 Specified base font 'medium' does not exist for font clock
2008-12-03 20:53:40.909 Specified base font 'medium' does not exist for font small
2008-12-03 20:53:40.909 Specified base font 'medium' does not exist for font medium                                                                                 
2008-12-03 20:53:40.909 Specified base font 'medium' does not exist for font large
2008-12-03 20:53:41.030 Loading from: /usr/share/mythtv/themes/blootube-wide/base.xml                                                                               
2008-12-03 20:53:41.141 Loading from: /usr/share/mythtv/themes/default/base.xml   
2008-12-03 20:53:48.878 Registering Internal as a media playback plugin.          
2008-12-03 20:53:53.203 MonitorRegisterExtensions(0x100, gif,jpg,png)             
2008-12-03 20:53:53.870 MythMusic adding CD-Writer: 1,0,0 -- DVD+-RW TS-L632D     
2008-12-03 20:53:56.691 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)         
SIP listening on IP Address 10.86.1.210:5060 NAT address 10.86.1.210              
SIP: Cannot register; proxy, username or password not set                         
2008-12-03 20:54:04.788 No theme dir: /home/william/.mythtv/themes/blootube-wide  
2008-12-03 20:54:54.945 Writing settings file /home/william/.mythtv/mysql.txt     
2008-12-03 20:54:54.946 Closing DB connection named 'DBManager0'                  
2008-12-03 20:54:54.946 Closing DB connection named 'DBManager1'                  
2008-12-03 20:54:55.132 Connected to database 'mythconverg' at host: mythtv.dyndns.com                                                                        
2008-12-03 20:54:55.580 Connecting to backend server: 192.168.1.5:6543 (try 1 of 5)                                                                                 
2008-12-03 20:58:04.577 Connection timed out.
                        You probably should modify the Master Server
                        settings in the setup program and set the
                        proper IP address.
2008-12-03 21:04:29.170 Connecting to backend server: 192.168.1.5:6543 (try 1 of 5)


```

---

### Post by tgm4883 on 2008-12-03
Not that this helps you achieve your goal, but I doubt the internet connection at your home is fast enough for that.

---

### Post by funkydan2 on 2008-12-04
+1 for tgm4883's suggestion that your home internet connection won't be fast enough for you to watch full quality TV over the internet.

One way to get access to your recorded TV over the net would be to setup MythWeb and the 'Video Playback' section in its settings which gives you (low bandwidth/quality) access to flash video (think youtube) version of the stuff that's recorded on your backend.  Much kinder on your internet connection.

---

### Post by Archmage on 2008-12-04
If I read it right, you need to set up the right IP at the Masterbackend = Your internet-IP-Adress.

This way it should work over the internet, but it wont work anymore over the local network.

As suggested, I would give Mythweb a try.

---

### Post by anonymousdog on 2008-12-04
...and for more MythWeb options for remote playback, try my current packaging of mythstreamtv MythWeb plugin, [http://ubuntuforums.org/showthread.php?t=922937](http://ubuntuforums.org/showthread.php?t=922937)

---

### Post by kwilliam on 2008-12-05
On the bright side, I got OpenVPN working the [HOWTO]("http://openvpn.net/index.php/documentation/howto.html") and changing the master ip and backend ip to 10.8.0.1. The frontend connects, and I can sort-of get LiveTV - but it comes in half-second bursts, with several seconds in between bursts. You guys are probably right - my Internet probably isn't fast enough to stream Live TV. I'm surprised that pre-recorded shows don't work at all though, as I would think they'd be easier to stream.

For the record/posterity:

```
$ mythfrontend
2008-12-04 23:55:40.052 Using runtime prefix = /usr
2008-12-04 23:55:41.231 DPMS is active.
2008-12-04 23:55:41.241 Using localhost value of laptop
2008-12-04 23:55:41.292 New DB connection, total: 1
2008-12-04 23:55:41.527 Connected to database 'mythconverg' at host: 10.8.0.1
2008-12-04 23:55:41.567 Closing DB connection named 'DBManager0'
2008-12-04 23:55:41.589 Primary screen 0.
2008-12-04 23:55:41.749 Connected to database 'mythconverg' at host: 10.8.0.1
2008-12-04 23:55:41.788 Using screen 0, 1680x1050 at 0,0
2008-12-04 23:55:42.543 New DB connection, total: 2
2008-12-04 23:55:42.718 Connected to database 'mythconverg' at host: 10.8.0.1
2008-12-04 23:55:42.971 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-12-04 23:55:42.972 Enabled verbose msgs:  important general
2008-12-04 23:55:49.391 Unable to parse themeinfo.xml for glass-wide
2008-12-04 23:55:49.392 The theme (glass-wide) is missing a themeinfo.xml file
2008-12-04 23:55:54.319 Unable to parse themeinfo.xml for glass-wide
2008-12-04 23:55:54.319 The theme (glass-wide) is missing a themeinfo.xml file
2008-12-04 23:56:06.583 No theme dir: /home/william/.mythtv/themes/G.A.N.T
2008-12-04 23:56:06.623 Primary screen 0.
2008-12-04 23:56:06.661 Using screen 0, 1680x1050 at 0,0
2008-12-04 23:56:06.703 No theme dir: /home/william/.mythtv/themes/G.A.N.T
2008-12-04 23:56:06.705 Switching to square mode (G.A.N.T)
2008-12-04 23:56:07.839 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-12-04 23:56:07.839 lirc_init failed for mythtv, see preceding messages
2008-12-04 23:56:07.839 JoystickMenuClient Error: Joystick disabled - Failed to read /home/william/.mythtv/joystickmenurc
QSocketDevice::writeBlock: Invalid socket
QSocketDevice::writeBlock: Invalid socket
2008-12-04 23:56:14.506 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2008-12-04 23:56:14.710 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-12-04 23:56:25.671 Registering Internal as a media playback plugin.
2008-12-04 23:56:33.585 MonitorRegisterExtensions(0x100, gif,jpg,png)
QSocketDevice::writeBlock: Invalid socket
QSocketDevice::writeBlock: Invalid socket
QSocketDevice::writeBlock: Invalid socket
QSocketDevice::writeBlock: Invalid socket
2008-12-04 23:56:34.798 MythMusic adding CD-Writer: 1,0,0 -- DVD+-RW TS-L632D
2008-12-04 23:56:39.254 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 10.86.1.210:5060 NAT address 10.86.1.210
SIP: Cannot register; proxy, username or password not set
2008-12-04 23:56:51.962 No theme dir: /home/william/.mythtv/themes/G.A.N.T
2008-12-04 23:57:07.060 XMLParse::LoadTheme using /usr/share/mythtv/themes/G.A.N.T/ui.xml
2008-12-04 23:57:08.173 Connecting to backend server: 10.8.0.1:6543 (try 1 of 5)
2008-12-04 23:58:41.256 Using protocol version 40
QSocketDevice::writeBlock: Invalid socket
QSocketDevice::writeBlock: Invalid socket
2008-12-04 23:59:02.432 AFD: Opened codec 0x85d2bc0, id(MPEG2VIDEO) type(Video)
2008-12-04 23:59:02.432 AFD: codec MP2 has 2 channels
2008-12-04 23:59:02.432 AFD: Opened codec 0x85d32c0, id(MP2) type(Audio)
```

Watching recorded shows doesn't work. It goes to a black screen, waits a while, then comes back to the recording list.
```

2008-12-05 00:00:07.160 TV: Attempting to change from None to WatchingPreRecorded
2008-12-05 00:00:07.341 New DB connection, total: 3
2008-12-05 00:00:07.711 Connected to database 'mythconverg' at host: 10.8.0.1
2008-12-05 00:00:28.189 AFD: Opened codec 0x8346450, id(MPEG2VIDEO) type(Video)
2008-12-05 00:00:28.189 AFD: codec MP2 has 2 channels
2008-12-05 00:00:28.189 AFD: Opened codec 0x8315b40, id(MP2) type(Audio)
2008-12-05 00:00:30.050 DPMS Deactivated
2008-12-05 00:00:48.004 AFD: Opened codec 0x82b0400, id(MPEG2VIDEO) type(Video)
2008-12-05 00:00:48.004 AFD: codec MP2 has 2 channels
2008-12-05 00:00:48.004 AFD: Opened codec 0x839b9d0, id(MP2) type(Audio)
2008-12-05 00:00:49.521 Opening audio device 'default'. ch 2(2) sr 48000
2008-12-05 00:00:49.521 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-12-05 00:00:49.711 AudioOutput Warning: Mixer attach error -2: No such file or directory
                        Check Mixer Name in Setup: '/dev/mixer'
2008-12-05 00:00:50.051 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-12-05 00:00:50.129 TV: Changing from None to WatchingPreRecorded
2008-12-05 00:00:50.456 TV: Attempting to change from WatchingPreRecorded to None
2008-12-05 00:00:51.456 RingBuf(myth://10.8.0.1:6543/3053_20081127020825.mpg): Waited too long for ringbuffer pause..
2008-12-05 00:00:55.212 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-12-05 00:00:55.471 OSD Theme Dimensions W: 640 H: 480
2008-12-05 00:00:58.239 Realtime priority would require SUID as root.
2008-12-05 00:00:58.305 Video timing method: USleep with busy wait
2008-12-05 00:00:58.457 TV: Changing from WatchingPreRecorded to None
2008-12-05 00:00:58.960 DPMS Reactivated.
```

Curiously, LiveTV fairs better:
```
2008-12-05 00:01:18.203 AFD: Opened codec 0x898e9d0, id(MPEG2VIDEO) type(Video)
2008-12-05 00:01:18.203 AFD: codec MP2 has 2 channels
2008-12-05 00:01:18.203 AFD: Opened codec 0x85d81d0, id(MP2) type(Audio)
2008-12-05 00:01:28.480 TV: Attempting to change from None to WatchingLiveTV
2008-12-05 00:01:28.561 Using protocol version 40
2008-12-05 00:01:31.476 DPMS Deactivated
2008-12-05 00:01:41.506 RingBuf(myth://10.8.0.1:6543/3013_20081205000128.mpg): Waited 1.0 seconds for data to become available...
2008-12-05 00:01:41.506 Checking to see if there's a new livetv program to switch to..
2008-12-05 00:01:42.611 AFD: Opened codec 0x83551d0, id(MPEG2VIDEO) type(Video)
2008-12-05 00:01:42.611 AFD: codec MP2 has 2 channels
2008-12-05 00:01:42.611 AFD: Opened codec 0x8667bc0, id(MP2) type(Audio)
2008-12-05 00:01:43.470 Opening audio device 'default'. ch 2(2) sr 48000
2008-12-05 00:01:43.470 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-12-05 00:01:43.475 AudioOutput Warning: Mixer attach error -2: No such file or directory
                        Check Mixer Name in Setup: '/dev/mixer'
2008-12-05 00:01:48.204 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-12-05 00:01:48.691 OSD Theme Dimensions W: 640 H: 480
2008-12-05 00:01:49.002 TV: Changing from None to WatchingLiveTV
2008-12-05 00:01:49.003 Realtime priority would require SUID as root.
2008-12-05 00:01:49.101 Video timing method: USleep with busy wait
2008-12-05 00:01:49.600 NVP: prebuffering pause
2008-12-05 00:01:51.087 NVP: prebuffering pause
2008-12-05 00:01:52.417 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:01:53.755 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:01:55.086 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:01:56.417 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:01:57.643 NVP: prebuffering pause
2008-12-05 00:01:58.974 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:00.305 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:01.635 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:02.966 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:04.357 NVP: prebuffering pause
2008-12-05 00:02:05.688 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:07.019 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:08.350 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:08.629 RingBuf(myth://10.8.0.1:6543/3013_20081205000128.mpg): Waited 1.0 seconds for data to become available...
2008-12-05 00:02:08.629 Checking to see if there's a new livetv program to switch to..
2008-12-05 00:02:09.680 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:11.011 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:11.615 NVP: prebuffering pause
2008-12-05 00:02:12.946 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:14.277 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:15.608 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:16.939 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:18.270 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:18.656 NVP: prebuffering pause
2008-12-05 00:02:19.987 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:21.317 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:22.648 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:23.979 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:25.054 NVP: prebuffering pause
2008-12-05 00:02:26.388 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:27.719 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:29.049 NVP: Prebuffer wait timed out 10 times.
2008-12-05 00:02:30.381 NVP: Prebuffer wait timed out 10 times.
```
And the prebuffer waits continue ad infinitum.

Is it possible to increase this "NVP: Prebuffer" so it doesn't time out? (For that matter, what is NVP?)

But perhaps the Flash plugin for Mythweb is a better chance. Does this Flash player let you skip commercials? I would let MythTV simply re-encode the shows without commercials, but sometimes it's commercial detection is a little off.

---

### Post by anonymousdog on 2008-12-05
No, neither the flash streamer nor mythstreamtv have commercial skip features: that'd require a lot more integration with myth protocol and mysql functions for both streaming services.

Unless you've very stable 5Mbps or better upload at home and the same download wherever your remote machine is, you'll never get a remote frontend to work over the internet.  Even if you did, the utility of that is severely limited by the number of remote locations with 5Mbps+ bandwidth.

---

### Post by vhalros on 2009-03-17
Woops, posted to the wrong thread. I can't seem to delete this post, only replace the body...

---


---
title: "MythBuntu 9.10 Beta"
date: 2009-10-12
forum: Mythbuntu
---

### Post by scovel on 2009-10-12
I'm running the Mythbuntu 9.10 Beta.  Got more than a few updates in the last few days.  Here is what is currently running for my frontend:

```
scovel@mythbuntu:~$ mythfrontend.real --version
Please include all output in bug reports.
MythTV Version   : 22359
MythTV Branch    : trunk
Network Protocol : 50
Library API      : 0.22.20091008-1
QT Version       : 4.5.2
Options compiled in:
 linux profile using_oss using_alsa using_pulse using_jack using_backend using_dvb using_firewire using_frontend using_glx_proc_addr_arb using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_libfftw3 using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg

```backend:

```
scovel@gordon:~$ /usr/bin/mythbackend --version
Please include all output in bug reports.
MythTV Version   : 22359
MythTV Branch    : trunk
Network Protocol : 50
Library API      : 0.22.20091008-1
QT Version       : 4.5.2
Options compiled in:
 linux profile using_oss using_alsa using_pulse using_jack using_backend using_dvb using_firewire using_frontend using_glx_proc_addr_arb using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_libfftw3 using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg
```Trying to watch a recording.  First the list of recorded shows fails to load the first time.  Second attempt I get a list.  Trying to pick a show I get the following from the frontend log:

```
2009-10-12 20:31:03.062 Loading window theme from /usr/share/mythtv/themes/MythCenter/recordings-ui.xml
2009-10-12 20:31:03.062 Loading window theme from /usr/share/mythtv/themes/default/recordings-ui.xml
2009-10-12 20:31:03.174 MythContext: Connecting to backend server: 10.10.20.20:6543 (try 1 of 1)
2009-10-12 20:31:10.182 MythSocket(a4e9f50:26): readStringList: Error, timed out after 7000 ms.
2009-10-12 20:31:10.182 Protocol version check failure. The response to MYTH_PROTO_VERSION was empty.
2009-10-12 20:31:10.182 SortedList is Empty
2009-10-12 20:31:13.502 Loading window theme from /usr/share/mythtv/themes/MythCenter/recordings-ui.xml
2009-10-12 20:31:13.502 Loading window theme from /usr/share/mythtv/themes/default/recordings-ui.xml
2009-10-12 20:31:13.587 MythContext: Connecting to backend server: 10.10.20.20:6543 (try 1 of 1)
2009-10-12 20:31:20.590 MythSocket(a0826f8:26): readStringList: Error, timed out after 7000 ms.
2009-10-12 20:31:20.590 Protocol version check failure. The response to MYTH_PROTO_VERSION was empty.
2009-10-12 20:31:20.590 SortedList is Empty
2009-10-12 20:31:23.260 Loading window theme from /usr/share/mythtv/themes/MythCenter/recordings-ui.xml
2009-10-12 20:31:23.260 Loading window theme from /usr/share/mythtv/themes/default/recordings-ui.xml
2009-10-12 20:31:23.345 MythContext: Connecting to backend server: 10.10.20.20:6543 (try 1 of 1)
2009-10-12 20:31:28.640 Using protocol version 50
2009-10-12 20:31:33.316 TV: Attempting to change from None to Watching WatchingPreRecorded
2009-10-12 20:31:40.334 MythSocket(a0dd228:40): readStringList: Error, timed out after 7000 ms.
2009-10-12 20:31:40.335 RemoteFile::openSocket(control socket), Error: Failed to open socket, timeout
2009-10-12 20:31:47.338 MythSocket(a3e4fe8:40): readStringList: Error, timed out after 7000 ms.
2009-10-12 20:31:47.338 RemoteFile::openSocket(file data socket), Error: Failed to open socket, timeout
2009-10-12 20:31:47.338 RingBuffer::RingBuffer(): Failed to open remote file (myth://10.10.20.20:6543/1052_20091009235800.mpg)
2009-10-12 20:31:49.999 TV: Attempting to change from None to Watching WatchingPreRecorded
2009-10-12 20:31:57.016 MythSocket(a5b5668:40): readStringList: Error, timed out after 7000 ms.
2009-10-12 20:31:57.017 RemoteFile::openSocket(control socket), Error: Failed to open socket, timeout
2009-10-12 20:32:00.279 RingBuffer::RingBuffer(): Failed to open remote file (myth://10.10.20.20:6543/1052_20091009235800.mpg)
2009-10-12 20:32:06.356 TV: Attempting to change from None to Watching WatchingPreRecorded
2009-10-12 20:32:13.372 MythSocket(a3c5660:40): readStringList: Error, timed out after 7000 ms.
2009-10-12 20:32:13.372 RemoteFile::openSocket(control socket), Error: Failed to open socket, timeout
2009-10-12 20:32:20.379 MythSocket(a3c5660:40): readStringList: Error, timed out after 7000 ms.
2009-10-12 20:32:20.379 RemoteFile::openSocket(file data socket), Error: Failed to open socket, timeout
2009-10-12 20:32:20.379 RingBuffer::RingBuffer(): Failed to open remote file (myth://10.10.20.20:6543/1052_20091009235800.mpg)

```Rarely I will finally get to a show and can watch it.  Mostly I get "Please Wait...." then it goes back to the menu.

I'm willing to help debug to get this going.  Is this the version that is going to be in 9.10 Final?

Sean

---

### Post by scovel on 2009-10-13
Turns out there were 2 issues:

1.  At some point the backend forgot that it was a backend server!  It was trying to make the frontend the master, and the backend a slave.  
```
apt-cache policy mythtv-backend-master
``` should return something for Insalled:  If it says its not installed
```
apt-get install  mythtv-backend-master
``` takes care of this part of the problem.

2.  There were a bunch of mysql.txt files sprinkled all over the backend machine.  ```
find / -name mysql.txt
``` gets you the list.  Delete all of them except the one in  /etc/mythtv/.  Make sure the one in  /etc/mythtv/mysql.txt is setup properly.

restart the backend after.

Many Thanks to mrand on the mythbuntu IRC channel!

---


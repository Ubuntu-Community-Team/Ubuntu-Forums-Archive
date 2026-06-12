---
title: "mythtv error when running on edgy"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by lime4x4 on 2006-10-29
I got mythtv to install but when i run it i get this error in the terminal window

john@john-edgy:~$ mythtv
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2006-10-29 20:23:32.876 Using runtime prefix = /usr
2006-10-29 20:23:32.888 Gnome-Screensaver support enabled
2006-10-29 20:23:32.888 DPMS is active.
2006-10-29 20:23:32.889 Unable to read configuration file mysql.txt
2006-10-29 20:23:32.889 Trying to create a basic mysql.txt file
2006-10-29 20:23:32.889 Could not open settings file /home/john/.mythtv/mysql.txt for writing
2006-10-29 20:23:32.890 Failed to init MythContext, exiting.
john@john-edgy:~$

---

### Post by jaymode on 2006-10-29
try this

```

$locate mysql.txt

```

Then copy that file to to the location in the error message.

---

### Post by lime4x4 on 2006-10-29
well it appears it doesn't exsist

john@john-edgy:~$ locate mysql.txt
john@john-edgy:~$ sudo locate mysql.txt
john@john-edgy:~$

---

### Post by superm1 on 2006-10-30
John,

If you are trying to configure mythtv, you have to configure the backend prior to the frontend.

Run mythtv-setup by
```

sudo mythtv-setup
```

Once the backend is configured, copy /etc/mythtv/mysql.txt to ~/.mythtv/mysql.txt and make sure the permissions allow the user you are launching myth as to read them.  The mythfrontend is then launched by

```
mythfrontend
```

See the help page for more information about this procedure. [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by jbird1785 on 2006-11-03
I am having the same problem. I copied mysql.txt to my /.mythtv directory and gave permissions so everyone can access it. That got rid of the part of the error complaining about mysql.txt, but the Bad Device errors are still there:

jay@jay-desktop:~$ mythfrontend
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2006-11-03 00:39:29.623 Using runtime prefix = /usr
2006-11-03 00:39:29.632 Gnome-Screensaver support enabled
2006-11-03 00:39:29.633 DPMS is active.
2006-11-03 00:39:29.657 New DB connection, total: 1
2006-11-03 00:39:29.662 Connected to database 'mythconverg' at host: localhost
2006-11-03 00:39:29.663 Total desktop dim: 960x720, with 1 screen[s].
2006-11-03 00:39:29.666 Running in a window
2006-11-03 00:39:29.671 Using screen 0, 960x689 at 0,6
2006-11-03 00:39:29.758 Current Schema Version: 1160
2006-11-03 00:39:29.758 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2006-11-03 00:39:29.759 Enabled verbose msgs:  important general
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
2006-11-03 00:39:30.112 Total desktop dim: 960x720, with 1 screen[s].
2006-11-03 00:39:30.113 Running in a window
2006-11-03 00:39:30.113 Using screen 0, 960x689 at 0,6
2006-11-03 00:39:30.114 Switching to square mode (Retro)
2006-11-03 00:39:30.332 Using the OpenGL painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2006-11-03 00:39:30.581 Joystick disabled.
2006-11-03 00:39:30.686 Loading from: /usr/share/mythtv/themes/default/base.xml
2006-11-03 00:39:31.012 Registering Internal as a media playback plugin.
2006-11-03 00:39:31.043 Registering MythDVD DVD Media Handler as a media handler ext()
2006-11-03 00:39:31.044 Registering MythDVD VCD Media Handler as a media handler ext()
2006-11-03 00:39:31.066 Registering MythGallery Media Handler 1/2 as a media handler ext()
2006-11-03 00:39:31.066 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
2006-11-03 00:39:31.136 Using ARB NPOT texture extension
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
2006-11-03 00:39:35.688 Registering MythMusic Media Handler 1/2 as a media handler ext()
2006-11-03 00:39:35.688 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 



I'm using the pcHDTV HD5500 card with the drivers downloaded from their site.

---

### Post by superm1 on 2006-11-03
What graphics device are you using?  

I've typically seen these bad device errors cropping up with the open source drivers for some graphics cards or when the binary driver isn't properly installed.

---

### Post by jbird1785 on 2006-11-05
I'm using a radeon X600 Pro. I actually got rid of the errors by deleting 3 wacom device entries in xorg.conf. They isn't working seem to be in there for tablet touchscreen and input support, but I'm not sure. 

Now, mythtv runs fine, but I just get a blank screen for tv. I think its an issue with my setup of the capture card. I'll keep working on it.

---

### Post by superm1 on 2006-11-05
Well glad you solved that issue at least.

If your not getting any picture from live tv, try stopping mythtvbackend and getting video directly from your capture card.

```
sudo /etc/init.d/mythtv-backend stop
```

if you are using a ivtv or anything covered by v4l2, 

```
cat /dev/video0 > ~/test.mpg
```

Try playing this file in a media player like mplayer, xine, totem, or vlc.

As long as it works, then you have somethig configured wrong in mythtv-setup.

---

### Post by jbird1785 on 2006-11-05
Okay, I tried what you said and it creates the file, but it crashes both mplayer and xine when I try to view it. 

A little more info for you. Using tvtime, I can tune to channels 1-99 no problem. Also, I believe the hd5500 is suppose to use the dvb driver interface for digital and the v4l interface for analog tuning. I made a thread on pchdtv's forum to see if anyone knows specifics there. Thanks for the help, I'm lost.

---

### Post by superm1 on 2006-11-06
a hd5500 should be using the dvb interface yes.  Mplayer & VLC both have native support for dvb, but will need to know the exact frequency to tune.  

If you are using a hd5500, you probably need to scan for channels available using mythtv-setup before you were able to tune them.

---

### Post by jbird1785 on 2006-11-06
I can get the exact frequencies from the dtvscan tool pchdtv has, but I can't check if mplayer or VLC can show the stream until I get home.

In mythtv-setup, it did scan for the channels and it did find them. Unfortunately Comcast strips all the meta info on the channels, so it doesn't link the numbers up with the info from labs.zap2it.com.

Once in the frontend, I can "tune" to the detected channels, in that I can change channels, but they are all blank. The frontend doesn't give any errors in the terminal. Where should I check to see if the backend is generating any errors during this process?

Also, I would think that even if it was having trouble with the dvb stuff, the analog tuner would work, but I don't see it even picking up on the analog channels. I set the Analog Options on the card in mythtv-setup, but maybe I missed something.

In [this]("http://parker1.co.uk/mythtv_ubuntu.php") link from another post on this forum, it shows some more dvb testing tools. I'll also try them out.

---

### Post by jbird1785 on 2006-11-06
Okay, gave it another go. None of the tools I've found to test the incoming dvb stream seem to work. I was wrong on the frontend not giving any errors. Here is its output:

```
jay@jay-desktop:~$ mythfrontend
'2006-11-06 18:01:45.441 Using runtime prefix = /usr
2006-11-06 18:01:45.468 Gnome-Screensaver support enabled
2006-11-06 18:01:45.469 DPMS is active.
2006-11-06 18:01:45.519 New DB connection, total: 1
2006-11-06 18:01:45.524 Connected to database 'mythconverg' at host: localhost
2006-11-06 18:01:45.525 Total desktop dim: 960x720, with 1 screen[s].
2006-11-06 18:01:45.528 Running in a window
2006-11-06 18:01:45.528 Using screen 0, 960x689 at 0,6
2006-11-06 18:01:45.648 Current Schema Version: 1160
2006-11-06 18:01:45.648 mythfrontend version: 0.20.20060828-3 www.mythtv.org
2006-11-06 18:01:45.648 Enabled verbose msgs:  important general
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
2006-11-06 18:01:46.467 Total desktop dim: 960x720, with 1 screen[s].
2006-11-06 18:01:46.468 Running in a window
2006-11-06 18:01:46.468 Using screen 0, 960x689 at 0,6
2006-11-06 18:01:46.468 Switching to square mode (Retro)
2006-11-06 18:01:46.729 Using the OpenGL painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2006-11-06 18:01:47.031 Joystick disabled.
2006-11-06 18:01:47.173 Loading from: /usr/share/mythtv/themes/default/base.xml
2006-11-06 18:01:47.534 Registering Internal as a media playback plugin.
2006-11-06 18:01:47.615 Registering MythDVD DVD Media Handler as a media handler ext()
2006-11-06 18:01:47.616 Registering MythDVD VCD Media Handler as a media handler ext()
2006-11-06 18:01:47.653 Registering MythGallery Media Handler 1/2 as a media handler ext()
2006-11-06 18:01:47.653 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
2006-11-06 18:01:47.901 Using ARB NPOT texture extension
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
2006-11-06 18:01:52.625 Registering MythMusic Media Handler 1/2 as a media handler ext()
2006-11-06 18:01:52.625 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2006-11-06 18:01:57.297 New DB connection, total: 2
2006-11-06 18:01:57.298 Connected to database 'mythconverg' at host: localhost
2006-11-06 18:01:57.346 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2006-11-06 18:01:57.367 Using protocol version 31
2006-11-06 18:01:57.399 TV: Attempting to change from None to WatchingLiveTV
2006-11-06 18:01:57.399 Using protocol version 31
2006-11-06 18:01:57.917 DPMS Deactivated 
2006-11-06 18:01:57.942 NVP: Disabling Audio, params(-1,2,44100)
2006-11-06 18:01:57.953 VideoOutputXv: XvMCTex: Init failed
2006-11-06 18:01:57.955 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon Video Overlay'
2006-11-06 18:01:58.375 Using realtime priority.
2006-11-06 18:01:58.375 TV: Changing from None to WatchingLiveTV
2006-11-06 18:01:58.391 Video timing method: USleep with busy wait
2006-11-06 18:02:02.995 RingBuf(/var/lib/mythtv//2001_20061106180158.mpg): Taking too long to be allowed to read..
2006-11-06 18:02:04.199 NVP: Prebuffer wait timed out 10 times.
2006-11-06 18:02:04.255 RingBuf(/var/lib/mythtv//2001_20061106180158.mpg): Waited 1.0 seconds for data to become available...
2006-11-06 18:02:04.255 Checking to see if there's a new livetv program to switch to..
2006-11-06 18:02:05.831 RingBuf(/var/lib/mythtv//2001_20061106180158.mpg): Waited 1.0 seconds for data to become available...
2006-11-06 18:02:05.831 Checking to see if there's a new livetv program to switch to..
2006-11-06 18:02:05.907 VideoOutputXv: XvMCTex: Init failed
2006-11-06 18:02:05.908 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon Video Overlay'
2006-11-06 18:02:06.132 AFD: Opened codec 0x8e32fa0, id(MPEG2VIDEO) type(Video)
2006-11-06 18:02:06.133 AFD: Opened codec 0x8d78f90, id(AC3) type(Audio)
2006-11-06 18:02:06.134 AFD: Opened codec 0x8d810f0, id(AC3) type(Audio)
2006-11-06 18:02:06.219 NVP: Disabling Audio, params(0,0,0)
2006-11-06 18:02:06.463 NVP: Prebuffer wait timed out 10 times.
2006-11-06 18:02:07.231 RingBuf(/var/lib/mythtv//2001_20061106180158.mpg): Taking too long to be allowed to read..
2006-11-06 18:02:08.396 NVP: prebuffering pause
2006-11-06 18:02:08.451 RingBuf(/var/lib/mythtv//2001_20061106180158.mpg): Waited 1.0 seconds for data to become available...
2006-11-06 18:02:08.451 Checking to see if there's a new livetv program to switch to..
2006-11-06 18:02:10.655 RingBuf(/var/lib/mythtv//2001_20061106180158.mpg): Waited 1.0 seconds for data to become available...
2006-11-06 18:02:10.655 Checking to see if there's a new livetv program to switch to..
2006-11-06 18:02:10.748 NVP: prebuffering pause
2006-11-06 18:02:13.443 RingBuf(/var/lib/mythtv//2001_20061106180158.mpg): Waited 1.0 seconds for data to become available...
2006-11-06 18:02:13.443 Checking to see if there's a new livetv program to switch to..
2006-11-06 18:02:13.530 NVP: prebuffering pause
2006-11-06 18:02:14.471 RingBuf(/var/lib/mythtv//2001_20061106180158.mpg): Waited 2.0 seconds for data to become available...
2006-11-06 18:02:14.471 Checking to see if there's a new livetv program to switch to..
2006-11-06 18:02:15.171 NVP: Prebuffer wait timed out 10 times.
2006-11-06 18:02:16.523 RingBuf(/var/lib/mythtv//2001_20061106180158.mpg): Waited 4.0 seconds for data to become available...
2006-11-06 18:02:16.523 Checking to see if there's a new livetv program to switch to..
2006-11-06 18:02:16.811 NVP: Prebuffer wait timed out 10 times.
2006-11-06 18:02:18.451 NVP: Prebuffer wait timed out 10 times.
2006-11-06 18:02:20.091 NVP: Prebuffer wait timed out 10 times.
2006-11-06 18:02:20.623 RingBuf(/var/lib/mythtv//2001_20061106180158.mpg): Waited 8.0 seconds for data to become available...
2006-11-06 18:02:20.623 Checking to see if there's a new livetv program to switch to..
2006-11-06 18:02:21.731 NVP: Prebuffer wait timed out 10 times.
2006-11-06 18:02:32.211 RingBuf(/var/lib/mythtv//2001_20061106180158.mpg): Taking too long to be allowed to read..
2006-11-06 18:02:32.323 NVP: prebuffering pause
2006-11-06 18:02:33.215 RingBuf(/var/lib/mythtv//2001_20061106180158.mpg): Taking too long to be allowed to read..
2006-11-06 18:02:42.472 RingBuf(/var/lib/mythtv//2001_20061106180158.mpg): Taking too long to be allowed to read..
2006-11-06 18:02:42.612 NVP: prebuffering pause
2006-11-06 18:02:43.476 RingBuf(/var/lib/mythtv//2001_20061106180158.mpg): Taking too long to be allowed to read..
2006-11-06 18:02:53.272 RingBuf(/var/lib/mythtv//2001_20061106180158.mpg): Taking too long to be allowed to read..
2006-11-06 18:02:53.388 NVP: prebuffering pause

```

---

### Post by superm1 on 2006-11-06
Well in the meanwhile - I'd suggest a pvr-150 or something to that nature.  Are you sure that its not just because of encrypted streams from comcast possibly?

---


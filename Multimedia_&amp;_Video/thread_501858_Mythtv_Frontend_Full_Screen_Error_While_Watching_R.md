---
title: "Mythtv Frontend Full Screen Error While Watching Recordings"
date: 2007-07-15
forum: Multimedia &amp; Video
---

### Post by bla2000 on 2007-07-15
I've installed a mythtv frontend on a regular desktop and set it to connect to a backend on another computer.  In the frontend I can watch tv in full screen and view the previews of the recording but when I try to view a recording it tries to load but then kicks me back to the listings of the recorded programs.  I am using both Feisty on the backend and frontend and have followed the instructions found at [https://help.ubuntu.com/community/MythTV#head-5c90afbe1e30cc1b14ba2badb41a8b170f37b24e]("https://help.ubuntu.com/community/MythTV#head-5c90afbe1e30cc1b14ba2badb41a8b170f37b24e").

I have no problems watching dvds in full screen using either totem, xine or mplayer.  How can I fix my problem of not being able to watch recordings in full screen?  I have looked at [https://help.ubuntu.com/community/MythTV/Install/Troubleshooting]("https://help.ubuntu.com/community/MythTV/Install/Troubleshooting") and did not find a solution.  Thanks.

---

### Post by newlinux on 2007-07-15
can you run mythfrontend from a terminal and look at the output when you try to view a recording? That will probably give you an idea of what is happening.

---

### Post by bla2000 on 2007-07-15
Here is the output:

```
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-07-15 20:48:42.153 Using runtime prefix = /usr
2007-07-15 20:48:42.165 Gnome-Screensaver support enabled
2007-07-15 20:48:42.166 DPMS is active.
2007-07-15 20:48:42.187 New DB connection, total: 1
2007-07-15 20:48:42.220 Connected to database 'mythconverg' at host: 192.168.1.4
2007-07-15 20:48:42.222 Total desktop dim: 1280x1024, with 1 screen[s].
2007-07-15 20:48:42.247 Using screen 0, 1280x1024 at 0,0
2007-07-15 20:48:42.259 Current Schema Version: 1160
2007-07-15 20:48:42.260 mythfrontend version: 0.20.20060828-3 www.mythtv.org
2007-07-15 20:48:42.260 Enabled verbose msgs:  important general
2007-07-15 20:48:42.753 Total desktop dim: 1280x1024, with 1 screen[s].
2007-07-15 20:48:42.755 Using screen 0, 1280x1024 at 0,0
2007-07-15 20:48:42.756 Switching to square mode (MythCenter)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
2007-07-15 20:48:42.772 Using the Qt painter
Xlib:  extension "GLX" missing on display ":0.0".
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-07-15 20:48:43.200 Joystick disabled.
2007-07-15 20:48:43.257 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-07-15 20:48:43.816 Registering Internal as a media playback plugin.
2007-07-15 20:48:48.974 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2007-07-15 20:48:49.248 Connecting to backend server: 192.168.1.4:6543 (try 1 of 5)
2007-07-15 20:48:49.250 Using protocol version 31
0: start_time: 0.036 duration: 262.892
1: start_time: 0.026 duration: 262.861
stream: start_time: 0.289 duration: 2921.129 bitrate=5190 kb/s
2007-07-15 20:48:50.591 AFD: Opened codec 0xb2bff00, id(MPEG2VIDEO) type(Video)
2007-07-15 20:48:50.621 AFD: Opened codec 0xb2c0250, id(MP2) type(Audio)
0: start_time: 0.036 duration: 263.072
1: start_time: 0.026 duration: 263.043
stream: start_time: 0.289 duration: 2923.131 bitrate=5190 kb/s
2007-07-15 20:48:52.681 AFD: Opened codec 0xb2b7120, id(MPEG2VIDEO) type(Video)
2007-07-15 20:48:52.681 AFD: Opened codec 0xb2b7470, id(MP2) type(Audio)
0: start_time: 0.036 duration: 323.603
1: start_time: 0.026 duration: 323.562
stream: start_time: 0.289 duration: 3595.703 bitrate=5189 kb/s
2007-07-15 20:48:54.001 AFD: Opened codec 0xb2e3c40, id(MPEG2VIDEO) type(Video)
2007-07-15 20:48:54.002 AFD: Opened codec 0xb2b7120, id(MP2) type(Audio)
2007-07-15 20:48:55.295 New DB connection, total: 2
2007-07-15 20:48:55.296 Connected to database 'mythconverg' at host: 192.168.1.4
2007-07-15 20:48:55.348 TV: Attempting to change from None to WatchingPreRecorded
2007-07-15 20:48:55.365 RemoteFile::openSocket(control socket): 
                        Could not connect to server "" @ port -1
2007-07-15 20:48:55.365 RemoteFile::openSocket(file data socket): 
                        Could not connect to server "" @ port -1
2007-07-15 20:48:55.366 RingBuffer::RingBuffer(): Failed to open remote file (myth://:/1009_20070712200000.mpg)
0: start_time: 0.036 duration: 323.603
1: start_time: 0.026 duration: 323.562
stream: start_time: 0.289 duration: 3595.703 bitrate=5189 kb/s
2007-07-15 20:48:55.818 AFD: Opened codec 0xb2b7120, id(MPEG2VIDEO) type(Video)
2007-07-15 20:48:55.819 AFD: Opened codec 0xb2bfb80, id(MP2) type(Audio)
0: start_time: 0.036 duration: 323.603
1: start_time: 0.026 duration: 323.562
stream: start_time: 0.289 duration: 3595.703 bitrate=5189 kb/s
2007-07-15 20:48:56.191 AFD: Opened codec 0xb2b7120, id(MPEG2VIDEO) type(Video)
2007-07-15 20:48:56.192 AFD: Opened codec 0xb1f5c90, id(MP2) type(Audio)
2007-07-15 20:48:57.144 TV: Attempting to change from None to WatchingPreRecorded
2007-07-15 20:48:57.168 RemoteFile::openSocket(control socket): 
                        Could not connect to server "" @ port -1
2007-07-15 20:48:57.169 RemoteFile::openSocket(file data socket): 
                        Could not connect to server "" @ port -1
2007-07-15 20:48:57.169 RingBuffer::RingBuffer(): Failed to open remote file (myth://:/1009_20070710210000.mpg)
0: start_time: 0.036 duration: 323.606
1: start_time: 0.026 duration: 323.587
stream: start_time: 0.289 duration: 3595.736 bitrate=5189 kb/s
2007-07-15 20:48:57.199 AFD: Opened codec 0x81f9540, id(MPEG2VIDEO) type(Video)
2007-07-15 20:48:57.199 AFD: Opened codec 0xb2b7120, id(MP2) type(Audio)
0: start_time: 0.036 duration: 323.606
1: start_time: 0.026 duration: 323.587
stream: start_time: 0.289 duration: 3595.736 bitrate=5189 kb/s
2007-07-15 20:48:58.094 AFD: Opened codec 0xb22b8a0, id(MPEG2VIDEO) type(Video)
2007-07-15 20:48:58.095 AFD: Opened codec 0xb22b4f0, id(MP2) type(Audio)
Segmentation fault (core dumped)

```

---

### Post by bla2000 on 2007-07-16
My problems appears to be similar to [http://www.gossamer-threads.com/lists/engine?do=post_view_flat;post=228581;page=1;sb=post_latest_reply;so=ASC;mh=25;list=mythtv]("http://www.gossamer-threads.com/lists/engine?do=post_view_flat;post=228581;page=1;sb=post_latest_reply;so=ASC;mh=25;list=mythtv") but I don't understand the solutions.  Could someone please clarify?  Those recording were captured on myth 0.19 on Edgy.

---

### Post by bla2000 on 2007-07-16
My files are owned by the groups powerdev and slocate

```
-rwxrwxrwx  1 mythtv  powerdev 2322857984 2005-10-27 22:00 1005_20051027210000_2
0051027220000.nuv
-rw-rw-rw-  1 mythtv  powerdev      35913 2007-03-15 21:20 1005_20051027210000_2
0051027220000.nuv.png
-rw-r--r--  1 mythtv  slocate  2333194240 2006-12-04 21:00 1003_20061204200000.m
pg
-rw-rw-rw-  1 mythtv  slocate       38998 2007-07-14 03:17 1003_20061204200000.m
pg.png
-rwxrwxrwx  1 mythtv  powerdev 2322857984 2005-10-27 22:00 1005_20051027210000_2 0051027220000.nuv
-rw-rw-rw-  1 mythtv  powerdev      35913 2007-03-15 21:20 1005_20051027210000_2
0051027220000.nuv.png
```

---

### Post by bla2000 on 2007-07-16
It's fixed. I re-installed the mythtv frontend:

```
sudo apt-get remove --purge mythtv-frontend
sudo apt-get install mythtv-frontend
sudo apt-get install mythtv-themes
```

---

### Post by bla2000 on 2007-07-17
I spoke too soon.  The new recording work but the old don't.  It look like the new ones have group membership set to mythtv.

```
-rw-r--r--  1 mythtv  mythtv    299276288 2007-07-16 21:07 1011_20070716210000.m
pg
-rw-rw-rw-  1 mythtv  mythtv        30584 2007-07-16 21:00 1007_20070716200000.m
pg.png
```

I'll try changing the group membership.

---

### Post by bla2000 on 2007-07-17
In my recordings directory I changed all the *.mpg *.png and *.nuv to group membership mythtv but that didn't fix anything.  Same problem as before, recording from 0.19 don't open on a remote frontend in 0.20.  On my other computer which has both the backend and frontend all the recordings work.

---


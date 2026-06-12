---
title: "DVD playback"
date: 2009-01-14
forum: Multimedia Software
---

### Post by chaandana on 2009-01-14
Hi,

I have Ubuntu 8.10 installed on an Intel box.
I have Totem Movie Player 2.22.1 using Gstreamer 0.10.18 & GNOME installed.
The reason for Gstreamer : I'm using Internet Video streaming.
(and its working well)

But, when it comes to DVD playback, Totem just crashes. I mean It started up and in a second it goes off the screen. I cannot see any error message on any of the /var/log files.

Taking advice from few forum entries, I installed, Ogle and VLC.
But the result is same: starts up and goes off in a flash.

Can someone help me to fix this.
Thanks in advance.
Chaandana

---

### Post by CarpKing on 2009-01-15
Did you install libdvdcss or whatever?  This should have been a step required to get DVD playback.  

If you think you followed all the steps, open a terminal and type:
```
vlc
```

VLC should start.  Use it to play the disk.  When it crashes, post the output from the terminal here.  This will hopefully allow us to see what's wrong.

---

### Post by chaandana on 2009-01-15
Thanks for the reply.
Yes I have libdvdcss2 installed.

This is the output of the vlc.
I get the VLC window. Then I chose the 'open disc' option....
----
chaandana@ubuntu:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: PI30EUS1
libdvdnav: DVD Serial Number: 373b2ef2
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/chaandana/.dvdnav/PI30EUS1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000153
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000022e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000002e1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00030afb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00030ca9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00030e60
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00030f13
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00031636
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000316e9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00032685
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00032738
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0010cf25
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00112efa
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0014bb25
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0014bbd8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0015554f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00155602
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x00180c80
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x00180d33
libdvdread: Elapsed time 0
libdvdread: Found 9 VTS's
libdvdread: Elapsed time 0
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
[00000294] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  86
  Current serial number in output stream:  87
chaandana@ubuntu:~$

---


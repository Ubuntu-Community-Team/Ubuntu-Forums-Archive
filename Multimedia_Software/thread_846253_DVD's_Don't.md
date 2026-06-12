---
title: "DVD's Don't"
date: 2008-07-01
forum: Multimedia Software
---

### Post by kf4tqj on 2008-07-01
Well, I'm at it again. I keep failing to get DVD's to play using directions on this page: [http://ubuntuforums.org/showthread.p...ght=dvd+codecs](http://ubuntuforums.org/showthread.p...ght=dvd+codecs)
I know I must be missing something but I can't find it. Trying to open a DVD with VLC, Totem they both run and hide. They start to open then just disappear. Gxine will open and play the audio, but just shows a blank green screen.
When I open VLC in treminal I get this:
kf4tqj@kf4tqj-laptop:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: STARGATE_ATLANTIS_S1_D2
libdvdnav: DVD Serial Number: 33313215
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/kf4tqj/.dvdnav/STARGATE_ATLANTIS_S1_D2.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000161
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000244
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001fd62
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0010140f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001014ca
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001ea5ff
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001ea6ba
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x002cbdb9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002cbe74
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003ac209
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003ac44b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003ac600
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003ac6bb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003ac842
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003ac8fd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003ad45c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003ad517
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003afe71
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003aff2c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003b0181
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003b023c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x003b0bf8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003b0cb3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x003da59d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003da658
libdvdread: Elapsed time 0
libdvdread: Found 12 VTS's
libdvdread: Elapsed time 2
[00000338] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
X Error of failed request: BadAlloc (insufficient resources for operation)
Major opcode of failed request: 140 (XVideo)
Minor opcode of failed request: 19 ()
Serial number of failed request: 84
Current serial number in output stream: 85
pure virtual method called
terminate called without an active exception
Aborted

Can someone tell me what I'm missing? Machine is an IBM Thinkpad 600x. 500mhz 256 ram. Played DVD's with ver. 6.04.
Thanks,
Woody / KF4TQJ

---

### Post by iperich on 2008-07-01
I have exactly the same problem, with Gutsy I never had a problem watching DVDs and with Hardy is completely impossible...

I think it's a bug, I have all libraries (libdvdnav, dvdcss, etc), all well-configured, but nothing works.

Somebody knows what is happening here?

---

### Post by iperich on 2008-07-01
Ok, it's a bug.

I have searched and found [this page]("http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/64d6f40aa43102fd") where they say there is a xine bug working with compositing on, so i tried to play the dvd with no compiz effects and voila!! it worked...

can you try the same? I had exactly the same error.

---

### Post by iperich on 2008-07-02
I've also found that if you use Kaffeine, go to "Settings-xine engine parameters" and set the video driver to "xshm" you can play the DVD with compositing.

---


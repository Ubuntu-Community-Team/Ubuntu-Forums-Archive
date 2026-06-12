---
title: "Tuners aren't working correctly"
date: 2010-05-17
forum: Mythbuntu
---

### Post by Meph1st0 on 2010-05-17
I'm having trouble with my tuners.  I have two; both of them are PC HDTV 5500s.  Tuner 1 is only getting between 8 and 10 percent signal strenth no matter which channel I tune to.  Tuner 2 gets upwards of 70 to 90 percent on most channels.  However, on tuner 2 I get no audio.  Tuner 1 there is audio if it can get a lock on a channel which is rare.

If i perform a channel scan in mythbackend=setup then both channels are able to find the same channels.  They're both only connected to an antenna on my roof, connected to a splitter.  I've swapped the cables going into each tuner and still no change.  I've also swapped which port on the slitter each card is connected to, so I'm certain my video splitter is fine.

I have no idea what to do at this point.  They're both the exact same make and model of tuner card and they're both receiving the same signal off the same antenna.  I don't understand why I can't get audio on tuner 2.

I'm not even sure which logs to post.  This started happening when I upgraded to 9.10 32 bit.  I did a full reinstall.  In fact I screwed up the full reinstall because I lost my database backup in the processes as well as all of my recordings.  That was just plain stupidity on my part though, I don't think it's related to the problems I'm having with my tuners.

Anyone have any ideas?

---

### Post by Meph1st0 on 2010-05-17
```
==> /var/log/mythtv/jamu.log <==
Unknown (0000)

-----Scheduled & Recorded Statistics-------
Number of Scheduled & Recorded ......(   10)
Number of Fanart graphics found .....(    8)
Number of Poster graphics found .....(    9)
Number of Banner graphics found .....(    6)
Number of Fanart graphics downloaded (    0)
Number of Poster graphics downloaded (    0)
Number of Banner graphics downloaded (    0)
Number of Miro TV Shows ............ (    0)
Number of Miro Movie Trailers ...... (    0)

-------------Scheduled & Recorded----------
House
The Usual Suspects (1995)
My Name Is Earl
Chuck
How I Met Your Mother
Community
The Office
Fringe
Medium
Unknown (0000)

-----Scheduled & Recorded Statistics-------
Number of Scheduled & Recorded ......(   10)
Number of Fanart graphics found .....(    8)
Number of Poster graphics found .....(    9)
Number of Banner graphics found .....(    6)
Number of Fanart graphics downloaded (    0)
Number of Poster graphics downloaded (    0)
Number of Banner graphics downloaded (    0)
Number of Miro TV Shows ............ (    0)
Number of Miro Movie Trailers ...... (    0)

-------------Scheduled & Recorded----------
House
The Usual Suspects (1995)
My Name Is Earl
Chuck
How I Met Your Mother
Community
The Office
Fringe
Medium
Unknown (0000)

-----Scheduled & Recorded Statistics-------
Number of Scheduled & Recorded ......(   11)
Number of Fanart graphics found .....(    8)
Number of Poster graphics found .....(    9)
Number of Banner graphics found .....(    6)
Number of Fanart graphics downloaded (    0)
Number of Poster graphics downloaded (    0)
Number of Banner graphics downloaded (    0)
Number of Miro TV Shows ............ (    0)
Number of Miro Movie Trailers ...... (    0)

-------------Scheduled & Recorded----------
My Name Is Earl
Chuck
How I Met Your Mother
Community
The Office
Fringe
House
Medium
Unknown (0000)
Street Court
The Usual Suspects (1995)

-----Scheduled & Recorded Statistics-------
Number of Scheduled & Recorded ......(   16)
Number of Fanart graphics found .....(    8)
Number of Poster graphics found .....(    9)
Number of Banner graphics found .....(    6)
Number of Fanart graphics downloaded (    0)
Number of Poster graphics downloaded (    0)
Number of Banner graphics downloaded (    0)
Number of Miro TV Shows ............ (    0)
Number of Miro Movie Trailers ...... (    0)

-------------Scheduled & Recorded----------
My Name Is Earl
Chuck
How I Met Your Mother
Community
The Office
Fringe
House
Medium
Unknown (0000)
Super Why!
Street Court
The Usual Suspects (1995)
FOX 5 Weather 24/7
News Three at Noon
MLL Lacrosse
Gina D's Kids Club

==> /var/log/mythtv/mtd.log <==
mtd started at Mon May 17 11:36:43 2010
mtd is running on a host called browndvr
11:36:43: Waiting for connections/jobs
11:36:43: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
2010-05-17 12:14:25.270 Connected to database 'mythconverg' at host: localhost
2010-05-17 12:14:25.483 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(3) desired(4)
2010-05-17 12:14:25.850 Finished recording FOX 5 Weather 24/7: channel 1052
2010-05-17 12:14:25.854 scheduler: Finished recording: FOX 5 Weather 24/7: channel 1052
2010-05-17 12:14:25.869 Finished recording FOX 5 Weather 24/7: channel 1052
2010-05-17 12:14:25.898 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2010-05-17 12:14:27.727 AFD: Opened codec 0xa02d240, id(MPEG2VIDEO) type(Video)
2010-05-17 12:14:27.732 AFD: codec AC3 has 2 channels
2010-05-17 12:14:27.733 AFD: Opened codec 0xa02d5f0, id(AC3) type(Audio)
2010-05-17 12:14:27.762 RecBase(2:/dev/dvb/adapter1/frontend0): GetKeyframePositions(16,9223372036854775807,#1) out of 3
2010-05-17 12:14:27.773 Preview: Grabbed preview '/var/lib/mythtv/livetv/1033_20100517121420.mpg' 352x480@79s
2010-05-17 12:14:27.883 RecBase(2:/dev/dvb/adapter1/frontend0): GetKeyframePositions(16,9223372036854775807,#2) out of 4
2010-05-17 12:14:31.549 TVRec(2): HW Tuner: 2->2
2010-05-17 12:14:31.915 Finished recording FOX 5 Weather 24/7: channel 1052
2010-05-17 12:14:31.989 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-05-17 12:14:32.035 Using runtime prefix = /usr
2010-05-17 12:14:32.036 Using configuration directory = /home/mythtv/.mythtv
2010-05-17 12:14:32.037 Empty LocalHostName.
2010-05-17 12:14:32.038 Using localhost value of browndvr
2010-05-17 12:14:32.044 New DB connection, total: 1
2010-05-17 12:14:32.048 Connected to database 'mythconverg' at host: localhost
2010-05-17 12:14:32.053 Closing DB connection named 'DBManager0'
2010-05-17 12:14:32.052 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2010-05-17 12:14:32.054 Connected to database 'mythconverg' at host: localhost
2010-05-17 12:14:32.070 Current MythTV Schema Version (DBSchemaVer): 1244
2010-05-17 12:14:32.073 New DB connection, total: 2
2010-05-17 12:14:32.075 Connected to database 'mythconverg' at host: localhost
2010-05-17 12:14:32.217 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(4) desired(7)
2010-05-17 12:14:32.220 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(5) desired(7)
2010-05-17 12:14:32.221 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(3) desired(7)
2010-05-17 12:14:32.272 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(6) desired(7)
2010-05-17 12:14:32.274 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(8) desired(7)
2010-05-17 12:14:32.644 Finished recording Super Why! "The Little Red Hen": channel 1007
2010-05-17 12:14:32.648 scheduler: Last message repeated 2 times: Finished recording: FOX 5 Weather 24/7: channel 1052
2010-05-17 12:14:32.652 scheduler: Finished recording: Super Why! "The Little Red Hen": channel 1007
2010-05-17 12:14:32.670 Finished recording Super Why! "The Little Red Hen": channel 1007
2010-05-17 12:14:32.683 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2010-05-17 12:14:34.523 AFD: Opened codec 0x9579050, id(MPEG2VIDEO) type(Video)
2010-05-17 12:14:34.526 AFD: codec AC3 has 2 channels
2010-05-17 12:14:34.527 AFD: Opened codec 0x95754c0, id(AC3) type(Audio)
2010-05-17 12:14:34.582 Preview: Grabbed preview '/var/lib/mythtv/livetv/1052_20100517121425.mpg' 704x480@79s
2010-05-17 12:14:46.236 TVRec(2): Changing from Watching WatchingLiveTV to None
2010-05-17 12:14:46.256 Unknown type, recording width was 0
2010-05-17 12:14:46.737 Finished recording Super Why! "The Little Red Hen": channel 1007
2010-05-17 12:14:46.790 MainServer::ANN Playback
2010-05-17 12:14:46.792 adding: browndvr as a client (events: 0)
2010-05-17 12:14:46.794 TVRec(1): Changing from None to Watching WatchingLiveTV
2010-05-17 12:14:46.798 TVRec(1): HW Tuner: 1->1
2010-05-17 12:14:46.843 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2010-05-17 12:14:46.909 TVRec(1): Changing from Watching WatchingLiveTV to None
2010-05-17 12:14:47.338 Finished recording News Three at Noon: channel 1031
2010-05-17 12:14:47.342 scheduler: Last message repeated 2 times: Finished recording: Super Why! "The Little Red Hen": channel 1007
2010-05-17 12:14:47.346 scheduler: Finished recording: News Three at Noon: channel 1031
2010-05-17 12:16:03.779 Expiring 0 MBytes for 1051 @ Mon May 17 12:00:00 2010 => Paid Programming
2010-05-17 12:16:03.781 autoexpire: Expiring Program: Expiring 0 MBytes for 1051 @ Mon May 17 12:00:00 2010 => Paid Programming
2010-05-17 12:16:03.783 Expiring 0 MBytes for 1006 @ Mon May 17 12:13:32 2010 => Unknown
2010-05-17 12:16:03.785 autoexpire: Expiring Program: Expiring 0 MBytes for 1006 @ Mon May 17 12:13:32 2010 => Unknown
2010-05-17 12:16:03.804 Expiring 0 MBytes for 1007 @ Mon May 17 12:00:00 2010 => Super Why! "The Little Red Hen"
2010-05-17 12:16:03.807 autoexpire: Expiring Program: Expiring 0 MBytes for 1007 @ Mon May 17 12:00:00 2010 => Super Why! "The Little Red Hen"
2010-05-17 12:16:03.809 Expiring 0 MBytes for 1081 @ Mon May 17 12:00:00 2010 => 8 News Now at Noon
2010-05-17 12:16:03.813 autoexpire: Expiring Program: Expiring 0 MBytes for 1081 @ Mon May 17 12:00:00 2010 => 8 News Now at Noon
2010-05-17 12:16:03.816 Expiring 0 MBytes for 1101 @ Mon May 17 12:00:00 2010 => Super Why! "The Little Red Hen"
2010-05-17 12:16:03.819 autoexpire: Expiring Program: Expiring 0 MBytes for 1101 @ Mon May 17 12:00:00 2010 => Super Why! "The Little Red Hen"
2010-05-17 12:16:03.824 Expiring 0 MBytes for 1103 @ Mon May 17 12:00:00 2010 => Cocinando con Fernando Canales "Canutillos de jamón y Tallarines de gambas"
2010-05-17 12:16:03.828 autoexpire: Expiring Program: Expiring 0 MBytes for 1103 @ Mon May 17 12:00:00 2010 => Cocinando con Fernando Canales "Canutillos de jamÃ³n y Tallarines de gambas"
2010-05-17 12:16:03.830 Expiring 0 MBytes for 1132 @ Mon May 17 12:13:52 2010 => Unknown
2010-05-17 12:16:03.834 autoexpire: Expiring Program: Expiring 0 MBytes for 1132 @ Mon May 17 12:13:52 2010 => Unknown
2010-05-17 12:16:03.840 Expiring 0 MBytes for 1152 @ Mon May 17 12:00:00 2010 => Heridas de Amor
2010-05-17 12:16:03.845 autoexpire: Expiring Program: Expiring 0 MBytes for 1152 @ Mon May 17 12:00:00 2010 => Heridas de Amor
2010-05-17 12:16:03.848 Expiring 0 MBytes for 1151 @ Mon May 17 12:00:00 2010 => Pecadora
2010-05-17 12:16:03.851 autoexpire: Expiring Program: Expiring 0 MBytes for 1151 @ Mon May 17 12:00:00 2010 => Pecadora
2010-05-17 12:16:03.853 Expiring 0 MBytes for 1211 @ Mon May 17 12:00:00 2010 => Judge Mathis
2010-05-17 12:16:03.857 autoexpire: Expiring Program: Expiring 0 MBytes for 1211 @ Mon May 17 12:00:00 2010 => Judge Mathis
2010-05-17 12:16:03.861 Expiring 0 MBytes for 1251 @ Mon May 17 12:14:01 2010 => Unknown
2010-05-17 12:16:03.865 autoexpire: Expiring Program: Expiring 0 MBytes for 1251 @ Mon May 17 12:14:01 2010 => Unknown
2010-05-17 12:16:03.869 Expiring 0 MBytes for 1331 @ Mon May 17 12:00:00 2010 => The Steve Wilkos Show "Devil Dad"
2010-05-17 12:16:03.873 autoexpire: Expiring Program: Expiring 0 MBytes for 1331 @ Mon May 17 12:00:00 2010 => The Steve Wilkos Show "Devil Dad"
2010-05-17 12:16:03.880 Expiring 0 MBytes for 1391 @ Mon May 17 12:00:00 2010 => La Favorita
2010-05-17 12:16:03.883 autoexpire: Expiring Program: Expiring 0 MBytes for 1391 @ Mon May 17 12:00:00 2010 => La Favorita
2010-05-17 12:16:03.886 Expiring 0 MBytes for 1031 @ Mon May 17 12:00:00 2010 => News Three at Noon
2010-05-17 12:16:03.888 autoexpire: Expiring Program: Expiring 0 MBytes for 1031 @ Mon May 17 12:00:00 2010 => News Three at Noon
2010-05-17 12:16:03.890 Expiring 7 MBytes for 1031 @ Mon May 17 12:00:00 2010 => News Three at Noon
2010-05-17 12:16:03.894 autoexpire: Expiring Program: Expiring 7 MBytes for 1031 @ Mon May 17 12:00:00 2010 => News Three at Noon
2010-05-17 12:16:03.902 Expiring 1 MBytes for 1032 @ Mon May 17 12:00:00 2010 => Gina D's Kids Club
2010-05-17 12:16:03.905 autoexpire: Expiring Program: Expiring 1 MBytes for 1032 @ Mon May 17 12:00:00 2010 => Gina D's Kids Club
2010-05-17 12:16:03.907 Expiring 1 MBytes for 1033 @ Mon May 17 11:00:00 2010 => MLL Lacrosse "Long Island Lizards at Washington Bayhawks"
2010-05-17 12:16:03.911 autoexpire: Expiring Program: Expiring 1 MBytes for 1033 @ Mon May 17 11:00:00 2010 => MLL Lacrosse "Long Island Lizards at Washington Bayhawks"
2010-05-17 12:16:03.917 Expiring 0 MBytes for 1052 @ Mon May 17 06:00:00 2010 => FOX 5 Weather 24/7
2010-05-17 12:16:03.920 autoexpire: Expiring Program: Expiring 0 MBytes for 1052 @ Mon May 17 06:00:00 2010 => FOX 5 Weather 24/7
2010-05-17 12:16:03.922 Expiring 1 MBytes for 1052 @ Mon May 17 06:00:00 2010 => FOX 5 Weather 24/7
2010-05-17 12:16:03.925 autoexpire: Expiring Program: Expiring 1 MBytes for 1052 @ Mon May 17 06:00:00 2010 => FOX 5 Weather 24/7
2010-05-17 12:16:03.927 Expiring 0 MBytes for 1007 @ Mon May 17 12:00:00 2010 => Super Why! "The Little Red Hen"
2010-05-17 12:16:03.930 autoexpire: Expiring Program: Expiring 0 MBytes for 1007 @ Mon May 17 12:00:00 2010 => Super Why! "The Little Red Hen"
2010-05-17 12:16:03.932 Expiring 2 MBytes for 1007 @ Mon May 17 12:00:00 2010 => Super Why! "The Little Red Hen"
2010-05-17 12:16:03.935 autoexpire: Expiring Program: Expiring 2 MBytes for 1007 @ Mon May 17 12:00:00 2010 => Super Why! "The Little Red Hen"
2010-05-17 12:16:03.937 Expiring 0 MBytes for 1031 @ Mon May 17 12:00:00 2010 => News Three at Noon
2010-05-17 12:16:03.942 autoexpire: Expiring Program: Expiring 0 MBytes for 1031 @ Mon May 17 12:00:00 2010 => News Three at Noon
2010-05-17 12:17:02.044 MainServer::ANN Monitor
2010-05-17 12:17:02.048 adding: browndvr as a client (events: 0)
2010-05-17 12:18:03.950 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

==> /var/log/mythtv/mythfrontend.log <==
2010-05-17 12:13:08.907 OSD Theme Dimensions W: 1280 H: 720
2010-05-17 12:13:09.171 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end ok
2010-05-17 12:13:09.172 Realtime priority would require SUID as root.
2010-05-17 12:13:09.172 TV: Changing from None to Watching WatchingLiveTV
2010-05-17 12:13:09.172 TV: State is LiveTV & mctx == ctx
2010-05-17 12:13:09.174 TV: UpdateOSDInput done
2010-05-17 12:13:09.174 TV: UpdateLCD done
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 720 x 576
YadifDeint: Using existing thread.
2010-05-17 12:13:09.176 Video timing method: USleep with busy wait
2010-05-17 12:13:09.177 TV: ITVRestart done
2010-05-17 12:13:09.219 ScreenSaverX11Private: DPMS Deactivated 1
2010-05-17 12:13:12.320 MythContext: Connecting to backend server: 192.168.1.11:6543 (try 1 of 1)
2010-05-17 12:13:12.321 Using protocol version 50
2010-05-17 12:13:12.387 NVP(c): Disabling Audio, params(-1,2,44100)
2010-05-17 12:13:12.397 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-05-17 12:13:12.428 OSD Theme Dimensions W: 1280 H: 720
2010-05-17 12:13:12.693 Realtime priority would require SUID as root.
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 720 x 576
YadifDeint: Using existing thread.
2010-05-17 12:13:12.698 Video timing method: USleep with busy wait
2010-05-17 12:13:12.701 LiveTVChain(live-browndvr-2010-05-17T12:13:08): SwitchTo() not switching to current
2010-05-17 12:13:14.620 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-05-17 12:13:14.926 AFD: Opened codec 0xa21ebbc0, id(MPEG2VIDEO) type(Video)
2010-05-17 12:13:14.926 AFD: codec AC3 has 6 channels
2010-05-17 12:13:14.928 AFD: Opened codec 0xa21204a0, id(AC3) type(Audio)
2010-05-17 12:13:15.342 Opening audio device 'default'. ch 2(2) sr 48000
2010-05-17 12:13:15.342 Opening ALSA audio device 'default'.
2010-05-17 12:13:15.408 mixer unable to find control Master 1
2010-05-17 12:13:15.409 NVP(c): Enabling Audio
2010-05-17 12:14:10.965 WriteAudio: buffer underrun
2010-05-17 12:14:11.821 AFD: Opened codec 0xa15ec3f0, id(MPEG2VIDEO) type(Video)
2010-05-17 12:14:11.821 AFD: codec AC3 has 6 channels
2010-05-17 12:14:11.821 AFD: Opened codec 0xa15ef8a0, id(AC3) type(Audio)
CC length( 7) seq_num(0) 0x4 0x0 
CC length(19) seq_num(3) 0xca 0x51 0x98 0x3b 0xe3 0x0 0x63 0x1f 0x10 0x90 0x5 0x3 0x91 0x3f 0x0 0x3f 0x92 0x3 
2010-05-17 12:14:16.217 msg: On known multiplex...
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 352 x 480
YadifDeint: Using existing thread.
2010-05-17 12:14:17.388 AFD: Opened codec 0xa085f10, id(MPEG2VIDEO) type(Video)
2010-05-17 12:14:17.388 AFD: codec AC3 has 2 channels
2010-05-17 12:14:17.389 AFD: Opened codec 0xb074860, id(AC3) type(Audio)
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 352 x 480
YadifDeint: Using existing thread.
2010-05-17 12:14:17.589 WriteAudio: buffer underrun
2010-05-17 12:14:20.473 msg: On known multiplex...
2010-05-17 12:14:21.626 AFD: Opened codec 0x10e35e10, id(MPEG2VIDEO) type(Video)
2010-05-17 12:14:21.627 AFD: codec AC3 has 2 channels
2010-05-17 12:14:21.627 AFD: Opened codec 0xc831ab0, id(AC3) type(Audio)
2010-05-17 12:14:22.113 WriteAudio: buffer underrun
2010-05-17 12:14:26.369 WriteAudio: buffer underrun
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 704 x 480
YadifDeint: Using existing thread.
2010-05-17 12:14:27.698 NVP(c): Prebuffer wait timed out 10 times.
2010-05-17 12:14:27.700 AFD: Opened codec 0xea5f060, id(MPEG2VIDEO) type(Video)
2010-05-17 12:14:27.701 AFD: codec AC3 has 2 channels
2010-05-17 12:14:27.701 AFD: Opened codec 0xc831ab0, id(AC3) type(Audio)
2010-05-17 12:14:32.772 WriteAudio: buffer underrun
2010-05-17 12:14:34.101 NVP(c): Prebuffer wait timed out 10 times.
2010-05-17 12:14:35.432 NVP(c): Prebuffer wait timed out 20 times.
2010-05-17 12:14:36.763 NVP(c): Prebuffer wait timed out 30 times.
2010-05-17 12:14:38.094 NVP(c): Prebuffer wait timed out 40 times.
2010-05-17 12:14:39.424 NVP(c): Prebuffer wait timed out 50 times.
2010-05-17 12:14:40.755 NVP(c): Prebuffer wait timed out 60 times.
2010-05-17 12:14:42.086 NVP(c): Prebuffer wait timed out 70 times.
2010-05-17 12:14:43.417 NVP(c): Prebuffer wait timed out 80 times.
2010-05-17 12:14:44.748 NVP(c): Prebuffer wait timed out 90 times.
2010-05-17 12:14:46.078 NVP(c): Prebuffer wait timed out 100 times.
2010-05-17 12:14:46.078 NVP(c), Error: Timed out waiting for prebuffering too long. Exiting..
2010-05-17 12:14:46.180 TV: Attempting to change from Watching WatchingLiveTV to None
2010-05-17 12:14:46.180 NVP(c): Disabling Audio, params(-1,-1,-1)
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 704 x 480
YadifDeint: Using existing thread.
2010-05-17 12:14:46.192 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-05-17 12:14:46.351 Couldn't open decoder for: /var/lib/mythtv/livetv/1007_20100517121432.mpg
2010-05-17 12:14:46.352 NVP(c), Error: Error opening jump program file
2010-05-17 12:14:46.352 NVP(c), Error: JumpToProgram failed.
2010-05-17 12:14:46.352 NVP(c), Error: Unknown recorder error, exiting decoder
2010-05-17 12:14:46.740 TV: Changing from Watching WatchingLiveTV to None
2010-05-17 12:14:46.761 ScreenSaverX11Private: DPMS Reactivated 1
2010-05-17 12:14:46.761 TV: Attempting to change from None to None
2010-05-17 12:14:46.788 TV: Attempting to change from None to Watching WatchingLiveTV
2010-05-17 12:14:46.789 MythContext: Connecting to backend server: 192.168.1.11:6543 (try 1 of 1)
2010-05-17 12:14:46.790 Using protocol version 50
2010-05-17 12:14:46.793 Spawning LiveTV Recorder -- begin
2010-05-17 12:14:46.838 Spawning LiveTV Recorder -- end
2010-05-17 12:14:46.852 We have a playbackURL(/var/lib/mythtv/livetv/1031_20100517121446.mpg) & cardtype(DUMMY)
2010-05-17 12:14:46.856 We have a RingBuffer
2010-05-17 12:14:46.906 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- begin
2010-05-17 12:14:46.906 playCtx, Error: Attempting to setup a player, but it already exists.
2010-05-17 12:14:46.906 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end error
2010-05-17 12:14:46.906 TV Error: LiveTV not successfully started
2010-05-17 12:14:46.927 ScreenSaverX11Private: DPMS Deactivated 1
2010-05-17 12:14:46.927 ScreenSaverX11Private: DPMS Reactivated 1

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
May 17 11:39:26 browndvr kernel: [  184.317976] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:27 browndvr kernel: [  184.817987] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:27 browndvr kernel: [  185.317978] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:28 browndvr kernel: [  185.817984] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:28 browndvr kernel: [  186.317961] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:29 browndvr kernel: [  186.817987] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:29 browndvr kernel: [  187.317976] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:30 browndvr kernel: [  187.817961] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:30 browndvr kernel: [  188.317977] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:31 browndvr kernel: [  188.817985] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:31 browndvr kernel: [  189.317981] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:32 browndvr kernel: [  189.817984] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:32 browndvr kernel: [  190.317969] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:33 browndvr kernel: [  190.817986] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:33 browndvr kernel: [  191.317978] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:34 browndvr kernel: [  191.817984] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:34 browndvr kernel: [  192.317968] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:35 browndvr kernel: [  192.817985] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:35 browndvr kernel: [  193.317981] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:36 browndvr kernel: [  193.817977] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:36 browndvr kernel: [  194.317978] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:37 browndvr kernel: [  194.817977] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:37 browndvr kernel: [  195.317980] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:38 browndvr kernel: [  195.817986] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:38 browndvr kernel: [  196.317975] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:39 browndvr kernel: [  196.817965] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:39 browndvr kernel: [  197.317978] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:40 browndvr kernel: [  197.817978] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:40 browndvr kernel: [  198.317967] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:41 browndvr kernel: [  198.817981] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:41 browndvr kernel: [  199.317976] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:42 browndvr kernel: [  199.817980] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:42 browndvr kernel: [  200.317969] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:43 browndvr kernel: [  200.817979] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:43 browndvr kernel: [  201.317979] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:44 browndvr kernel: [  201.817976] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:44 browndvr kernel: [  202.317977] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:45 browndvr kernel: [  202.817986] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:45 browndvr kernel: [  203.317978] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:46 browndvr kernel: [  203.817985] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:46 browndvr kernel: [  204.317965] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:47 browndvr kernel: [  204.817986] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:47 browndvr kernel: [  205.317980] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:48 browndvr kernel: [  205.817981] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:48 browndvr kernel: [  206.317974] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:49 browndvr kernel: [  206.817982] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:49 browndvr kernel: [  207.317968] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:50 browndvr kernel: [  207.817979] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:50 browndvr kernel: [  208.317977] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:51 browndvr kernel: [  208.817978] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:51 browndvr kernel: [  209.317969] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:39:52 browndvr kernel: [  209.818467] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:40:37 browndvr init: mythtv-backend main process (898) terminated with status 255
May 17 11:40:38 browndvr lircd-0.8.6[1270]: accepted new client on /var/run/lirc/lircd
May 17 11:40:53 browndvr lircd-0.8.6[1270]: removed client
May 17 11:40:53 browndvr kernel: [  270.961349] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:40:57 browndvr ntpd[1534]: synchronized to 91.189.94.4, stratum 2
May 17 11:40:57 browndvr ntpd[1534]: time reset +0.222619 s
May 17 11:40:57 browndvr ntpd[1534]: kernel time sync status change 2001
May 17 11:41:47 browndvr init: mythtv-backend main process (2336) terminated with status 255
May 17 11:41:47 browndvr lircd-0.8.6[1270]: accepted new client on /var/run/lirc/lircd
May 17 11:45:15 browndvr kernel: [  532.928789] DVB: adapter 1 frontend 0 frequency 863000000 out of range (54000000..858000000)
May 17 11:45:15 browndvr kernel: [  532.943751] DVB: adapter 1 frontend 0 frequency 869000000 out of range (54000000..858000000)
May 17 11:45:15 browndvr kernel: [  532.944833] DVB: adapter 1 frontend 0 frequency 875000000 out of range (54000000..858000000)
May 17 11:45:15 browndvr kernel: [  532.945707] DVB: adapter 1 frontend 0 frequency 881000000 out of range (54000000..858000000)
May 17 11:45:15 browndvr kernel: [  532.946549] DVB: adapter 1 frontend 0 frequency 887000000 out of range (54000000..858000000)
May 17 11:48:35 browndvr kernel: [  732.119274] DVB: adapter 1 frontend 0 frequency 863000000 out of range (54000000..858000000)
May 17 11:48:35 browndvr kernel: [  732.120453] DVB: adapter 1 frontend 0 frequency 869000000 out of range (54000000..858000000)
May 17 11:48:35 browndvr kernel: [  732.121451] DVB: adapter 1 frontend 0 frequency 875000000 out of range (54000000..858000000)
May 17 11:48:35 browndvr kernel: [  732.122339] DVB: adapter 1 frontend 0 frequency 881000000 out of range (54000000..858000000)
May 17 11:48:35 browndvr kernel: [  732.123217] DVB: adapter 1 frontend 0 frequency 887000000 out of range (54000000..858000000)
May 17 11:50:37 browndvr lircd-0.8.6[1270]: removed client
May 17 11:50:37 browndvr kernel: [  854.764172] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:51:21 browndvr ntpd[1534]: synchronized to 91.189.94.4, stratum 2
May 17 11:52:47 browndvr kernel: [  984.705842] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:53:00 browndvr kernel: [  997.783981] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:54:24 browndvr kernel: [ 1081.813975] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:54:25 browndvr kernel: [ 1082.314865] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:54:25 browndvr kernel: [ 1082.818868] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:54:26 browndvr kernel: [ 1083.322868] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:54:26 browndvr kernel: [ 1083.826867] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:54:27 browndvr kernel: [ 1084.330864] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:54:27 browndvr kernel: [ 1084.834866] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:54:28 browndvr kernel: [ 1085.338865] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:54:28 browndvr kernel: [ 1085.842865] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 11:58:50 browndvr init: mythtv-backend main process (2705) terminated with status 255
May 17 11:58:50 browndvr lircd-0.8.6[1270]: accepted new client on /var/run/lirc/lircd
May 17 12:01:42 browndvr lircd-0.8.6[1270]: removed client
May 17 12:01:43 browndvr kernel: [ 1520.535093] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 12:06:20 browndvr kernel: [ 1797.106158] cx88[0]: irq pci [0x800] risc_wr_err*
May 17 12:09:01 browndvr CRON[3234]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 17 12:11:58 browndvr kernel: [ 2135.920884] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 12:12:04 browndvr kernel: [ 2141.915958] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 12:12:16 browndvr kernel: [ 2154.033730] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 12:13:08 browndvr kernel: [ 2205.859191] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
May 17 12:15:13 browndvr acpid: client 1182[0:0] has disconnected
May 17 12:15:13 browndvr acpid: client 1182[0:0] has disconnected
May 17 12:15:13 browndvr acpid: client connected from 1182[0:0]
May 17 12:15:14 browndvr acpid: client connected from 1182[0:0]
May 17 12:17:01 browndvr CRON[3605]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

==> /var/log/Xorg.0.log <==
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Logitech USB Receiver
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
(II) Logitech USB Receiver: initialized for relative axes.
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Logitech USB Receiver: Device reopened after 1 attempts.
(II) Logitech USB Receiver: Device reopened after 1 attempts.
(II) Sleep Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.

==> /home/jbrown/.xsession-errors <==
17/05/2010 11:36:43   If this yields undesired behavior (poor response, painting
17/05/2010 11:36:43   errors, etc) it may be disabled via: '-noscr'
17/05/2010 11:36:43   Also see the -help entry for tuning parameters.
17/05/2010 11:36:43   You can press 3 Alt_L's (Left "Alt" key) in a row to 
17/05/2010 11:36:43   repaint the screen, also see the -fixscreen option for
17/05/2010 11:36:43   periodic repaints.
17/05/2010 11:36:43 
17/05/2010 11:36:43 XKEYBOARD: number of keysyms per keycode 6 is greater
17/05/2010 11:36:43   than 4 and 288 keysyms are mapped above 4.
17/05/2010 11:36:43   Automatically switching to -xkb mode.
17/05/2010 11:36:43   If this makes the key mapping worse you can
17/05/2010 11:36:43   disable it with the "-noxkb" option.
17/05/2010 11:36:43   Also, remember "-remap DEAD" for accenting characters.
17/05/2010 11:36:43 X FBPM extension not supported.
17/05/2010 11:36:43 X display is capable of DPMS.
17/05/2010 11:36:43 --------------------------------------------------------
17/05/2010 11:36:43 
17/05/2010 11:36:43 Default visual ID: 0x21
17/05/2010 11:36:43 Read initial data from X display into framebuffer.
17/05/2010 11:36:43 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/7680
17/05/2010 11:36:43 
17/05/2010 11:36:43 X display :0.0 is 32bpp depth=24 true color
2010-05-17 11:36:43.318 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
17/05/2010 11:36:43 
17/05/2010 11:36:43 Listening for VNC connections on TCP port 5901
17/05/2010 11:36:43 fb read rate: 144 MB/sec
17/05/2010 11:36:43 screen setup finished.
17/05/2010 11:36:43 

The VNC desktop is:      browndvr:1
PORT=5901

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

more info: http://www.karlrunge.com/x11vnc/#faq-client-caching

/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 11 overrides entry on line 7

** (gnome-screensaver:1678): WARNING **: Failed to get session presence proxy: Could not get owner of name 'org.gnome.SessionManager': no such name
Failed to run gnome-keyring-daemon: Failed to execute child process "gnome-keyring-daemon" (No such file or directory)
xfdesktop[1700]: starting up
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3
2010-05-17 11:36:46.889 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
xfce4-settings-helper is already running

(polkit-gnome-authentication-agent-1:1831): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1831): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
(xfce4-mixer-plugin:1909): xfce4-mixer-plugin-DEBUG: mixer_plugin->track_label = 'Master'
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mythtv-backend stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mythtv-backend
mythtv-backend stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mythtv-backend restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart mythtv-backend
mythtv-backend start/running, process 2336
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mythtv-backend stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mythtv-backend
mythtv-backend stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mythtv-backend restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart mythtv-backend
mythtv-backend start/running, process 2705

(firefox:2844): GLib-WARNING **: g_set_prgname() called multiple times
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mythtv-backend stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mythtv-backend
mythtv-backend stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mythtv-backend restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart mythtv-backend
mythtv-backend start/running, process 3116

==> lsb_release -a <==
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              19G  2.7G   15G  16% /
udev                 1007M  384K 1007M   1% /dev
none                 1007M     0 1007M   0% /dev/shm
none                 1007M  316K 1007M   1% /var/run
none                 1007M  4.0K 1007M   1% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sda6             911G  184G  728G  21% /var/lib/mythtv

==> uname -a <==
Linux browndvr 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: VIA Technologies, Inc. PT880 Ultra/PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5372
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)
03:04.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:04.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
03:04.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
03:04.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
03:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
03:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
03:06.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

==> lsusb <==
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
==> /proc/driver/nvidia/cards <==

==> /proc/driver/nvidia/patches <==

==> /proc/driver/nvidia/registry <==
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UpdateMemoryTypes: 4294967295
UseVBios: 1
RMEdgeIntrCheck: 1
UsePageAttributeTable: 4294967295
MapRegistersEarly: 0
RegistryDwords: ""

==> /proc/driver/nvidia/version <==
NVRM version: NVIDIA UNIX x86 Kernel Module  173.14.20  Thu Jun 25 19:23:24 PDT 2009
GCC version:  gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) 

==> /proc/driver/nvidia/warnings <==
Model: 		 GeForce 7300 SE/7200 GS
IRQ:   		 24
Video BIOS: 	 05.72.22.80.29
Card Type: 	 PCI-E
DMA Size: 	 39 bits
DMA Mask: 	 0x7fffffffff
Bus Location: 	 02.00.0

==> lshw <==
computer
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2013MiB
     *-cpu
          product: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          version: 6.15.13
          serial: [REMOVED]
          size: 2300MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci:0
          description: Host bridge
          product: PT880 Ultra/PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:0-3ffffff(prefetchable)
        *-generic UNCLAIMED
             description: PIC
             product: PT894 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
        *-pci:1
             description: PCI bridge
             product: PT890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:48 memory:ddf00000-dfffffff memory:c0000000-cfffffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: G72 [GeForce 7300 SE/7200 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:24 memory:df000000-dfffffff memory:c0000000-cfffffff(prefetchable) memory:de000000-deffffff memory:ddfe0000-ddffffff(prefetchable)
        *-ide:0
             description: IDE interface
             product: VIA Technologies, Inc.
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_via latency=32
             resources: irq:21 ioport:ec00(size=8) ioport:e880(size=4) ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=16) ioport:e000(size=256)
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RAM 510L v1
                vendor: Memorex
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: MWS7
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:20 ioport:d480(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:22 ioport:d800(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d880(size=32)
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:23 ioport:dc00(size=32)
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:21 memory:ddeffc00-ddeffcff
        *-isa
             description: ISA bridge
             product: VT8237S PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: [REMOVED]
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=[REMOVED] latency=32 maxlatency=8 mingnt=3 multicast=yes
             resources: irq:23 ioport:d000(size=256) memory:ddeff800-ddeff8ff
        *-pci:2
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:f2000000-fdffffff
           *-multimedia:0
                description: Multimedia video controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder
                vendor: Conexant Systems, Inc.
                physical id: 4
                bus info: pci@0000:03:04.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=cx8800 latency=32 maxlatency=55 mingnt=20
                resources: irq:17 memory:f6000000-f6ffffff
           *-multimedia:1
                description: Multimedia controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port]
                vendor: Conexant Systems, Inc.
                physical id: 4.1
                bus info: pci@0000:03:04.1
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=cx88_audio latency=32 maxlatency=255 mingnt=4
                resources: irq:17 memory:f7000000-f7ffffff
           *-multimedia:2
                description: Multimedia controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]
                vendor: Conexant Systems, Inc.
                physical id: 4.2
                bus info: pci@0000:03:04.2
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=cx88-mpeg driver manager latency=32 maxlatency=88 mingnt=6
                resources: irq:17 memory:fc000000-fcffffff
           *-multimedia:3 UNCLAIMED
                description: Multimedia controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder [IR Port]
                vendor: Conexant Systems, Inc.
                physical id: 4.4
                bus info: pci@0000:03:04.4
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=32 maxlatency=255 mingnt=6
                resources: memory:fd000000-fdffffff
           *-multimedia:4
                description: Multimedia video controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder
                vendor: Conexant Systems, Inc.
                physical id: 6
                bus info: pci@0000:03:06.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=cx8800 latency=32 maxlatency=55 mingnt=20
                resources: irq:19 memory:f2000000-f2ffffff
           *-multimedia:5
                description: Multimedia controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port]
                vendor: Conexant Systems, Inc.
                physical id: 6.1
                bus info: pci@0000:03:06.1
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=cx88_audio latency=32 maxlatency=255 mingnt=4
                resources: irq:19 memory:f3000000-f3ffffff
           *-multimedia:6
                description: Multimedia controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]
                vendor: Conexant Systems, Inc.
                physical id: 6.2
                bus info: pci@0000:03:06.2
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=cx88-mpeg driver manager latency=32 maxlatency=88 mingnt=6
                resources: irq:19 memory:f4000000-f4ffffff
           *-multimedia:7 UNCLAIMED
                description: Multimedia controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder [IR Port]
                vendor: Conexant Systems, Inc.
                physical id: 6.4
                bus info: pci@0000:03:06.4
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=32 maxlatency=255 mingnt=6
                resources: memory:f5000000-f5ffffff
     *-pci:1
          description: Host bridge
          product: PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: PT890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: VT8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
     *-pci:7
          description: Host bridge
          product: VT8237A Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:13.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-multimedia
          description: Audio device
          product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0
          resources: irq:17 memory:febfc000-febfffff

```

---

### Post by LowSky on 2010-05-17
I found this, appartly your issues might be common in a multicard setup

[http://www.mythtv.org/wiki/PcHDTV_HD-5500#Issues](http://www.mythtv.org/wiki/PcHDTV_HD-5500#Issues)

---

### Post by Meph1st0 on 2010-05-18
I checked out that page and really the only thing I'm seeing that might apply is the part about Multiple HD-5500 cards where it has me edit the alsa-base.conf file in order to ensure that audio works properly.  Prior to upgrading to 9.10 I had no problems using both tuner cards.  So I don't think it has anything to do with a possible weak reception or due to hardware.  Like I had stated before, I get a really good reception with one of them, but very poor reception with the other.  

Today I reinstalled Mythbuntu 9.10 from scratch, thinking that maybe it'd clear up the problem, but I'm seeing the exact same behavior.  Sometimes, when it attempts to tune to a channel that it's getting no lock on it'll time out and take me back to the main menu with an error saying something along the lines of "error opening jump program file" or something about a buffer timing out.  Both message seem to appear in the log that I'd posted in the second post.

I found a post that's similar but not exactly.  Check out: [http://www.mythtvtalk.com/forum/installation-issues/12848-mythbuntu-9-10-multiple-tuner-cards.html](http://www.mythtvtalk.com/forum/installation-issues/12848-mythbuntu-9-10-multiple-tuner-cards.html)

The difference though is that this person has a problem with his pcHDTV 3000 card.  and apparently all he has to do is install the linux-firmware-nonfree package to get his 3000 working.  I've installed that package too just incase it applies to me but unfortunately I'm at work so I can't verify whether that fixed it or not.  Somehow I doubt it since I'm dealing with two 5500 cards.

My next step is to remove one card and see if the remaining card works and then swap them to see if the other works as well.  I get the feeling that as soon as they're both installed together these problems will resurface.

Any other ideas would be greatly appreciated.

---

### Post by Meph1st0 on 2010-05-18
I get the feeling that maybe my problems are related to the following threads:

[http://ubuntuforums.org/showthread.php?t=753434&page=1](http://ubuntuforums.org/showthread.php?t=753434&page=1)
[http://ubuntuforums.org/showthread.php?t=1311795&page=1](http://ubuntuforums.org/showthread.php?t=1311795&page=1)

They talk about a problem with the tuner cards swapping between /dev/dvb/adapter0 and adapter1 and they discuss the need to create udev rules to statically assign them a number.

How does one know if the cards are being swapped?  Under /dev/dvb I have adapter0 and adapter1 both of which are pcHDTV 5500 cards.  Being identical cards, how do I know if they've swapped after a reboot?

Also, if the cards are in fact being detected in mythbackend-setup, do I really need to do this at all?  Do I only need to setup udev rules if they aren't being detected or installed correctly?

---

### Post by LowSky on 2010-05-19
If both cards are identical I don't think them swapping adapter numbers would really matter. Both are capable of recording the same formats and channels, while the thread you brought up revolves around cards with different recording capabilities.

Part of me says if it isn't broke don't fix it. Can you try to install 9.04 which you say was working just fine? If the machine is only used as a media center keeping it in working order is more important than kernel upgrades.

---

### Post by Meph1st0 on 2010-05-19
lol, I've been saying that to myself for days now, "if it ain't broken, don't fix it".  However, today I've solved my problem.  I had mentioned that my next step was to remove one card and see if the remaining card works and then swap them to see if the other works as well.  Well it turns out that I found that one of the cards had actually crapped out.  When I removed the first card and tested the remaining card it worked fine.  When I swapped the cards, the one that I inserted wouldn't work any better than before.  I was thinking that my problems were specifically due to a Multi-tuner setup when in reality one of them had just gone bad.  And so I ran to best buy and bought a Hauppauge Win-tv HVR 1600 and installed it.  I then had to fix a known bug involving that card and the nvidia drivers and now I'm back to a working dual tuner setup.

---


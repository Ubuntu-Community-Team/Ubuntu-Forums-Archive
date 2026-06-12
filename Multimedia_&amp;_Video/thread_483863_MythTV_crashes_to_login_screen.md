---
title: "MythTV crashes to login screen"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by thomascj on 2007-06-25
all right, so here's the background:

installed kubuntu 
installed mythtv (got everything working just the way I wanted)
installed fglrx
installed xgl/beryl

in that order.. now the problem

when I run the mythtv front end it appears to crash and sends me back to the login screen (presumably restarting the X server).  Even running it from a console to see it's output didn't help because it takes over fullscreen then gives me the boot, so I ran it as such 'sudo mythtv > myth.log'... then logged back in after the crash and read the log which you'll find below.

If anyone can pinpoint what exactly the problem is I'd really appreciate it, the last line in the log would indicate it's something to do with the audio -- but that seems a bit hard to believe considering it all worked swimmingly until I started screwing around with graphics stuff.

I tried searching the forums and google -- but without knowing exactly what's causing the problem it's kind of hard to search for it.

```

2007-06-25 08:02:18.018 Using runtime prefix = /usr
2007-06-25 08:02:18.021 DPMS is disabled.
2007-06-25 08:02:18.035 New DB connection, total: 1
2007-06-25 08:02:18.040 Connected to database 'mythconverg' at host: localhost
2007-06-25 08:02:18.041 Total desktop dim: 1280x1024, with 1 screen[s].
2007-06-25 08:02:18.043 Using screen 0, 1280x1024 at 0,0
2007-06-25 08:02:18.058 max_width: 1280 max_height: 1024
2007-06-25 08:02:18.059 Total desktop dim: 1280x1024, with 1 screen[s].
2007-06-25 08:02:18.061 Using screen 0, 1280x1024 at 0,0
2007-06-25 08:02:18.061 Switching to square mode (G.A.N.T.)
2007-06-25 08:02:18.080 Using the Qt painter
2007-06-25 08:02:18.781 New DB connection, total: 2
2007-06-25 08:02:18.782 Connected to database 'mythconverg' at host: localhost
2007-06-25 08:02:18.783 Joystick disabled.
2007-06-25 08:02:18.897 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-06-25 08:02:18.898 Using protocol version 31
2007-06-25 08:02:18.923 TV: Attempting to change from None to WatchingLiveTV
2007-06-25 08:02:18.924 Using protocol version 31
2007-06-25 08:02:19.215 LiveTVChain(live-dreamscape-2007-06-25T08:02:18): ReloadAll(): Added new recording
2007-06-25 08:02:19.218 RingBuf(/media/hdb1/1025_20070625080219.mpg): OpenFile(/media/hdb1/1025_20070625080219.mpg, 12)
2007-06-25 08:02:20.015 RingBuf(/media/hdb1/1025_20070625080219.mpg): CalcReadAheadThresh(4000 KB)
			 -> threshhold(146 KB) min read(32 KB) blk size(64 KB)
2007-06-25 08:02:20.016 TV: StartRecorder(): took 1 ms to start recorder.
2007-06-25 08:02:20.184 AFD: Stream #0, has id 0x480 codec id MPEG2VIDEO, type Video, bitrate 6000000 at 0x0x81419c0
2007-06-25 08:02:20.188 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 480) ->Interlaced Scan
2007-06-25 08:02:20.188 AFD: Looking for decoder for MPEG2VIDEO
2007-06-25 08:02:20.188 AFD: Opened codec 0x8141a80, id(MPEG2VIDEO) type(Video)
2007-06-25 08:02:20.188 AFD: Stream #1, has id 0x448 codec id MP2, type Audio, bitrate 384000 at 0x0x8141f70
2007-06-25 08:02:20.188 AFD: Looking for decoder for MP2
2007-06-25 08:02:20.207 AFD: Opened codec 0x8142020, id(MP2) type(Audio)
2007-06-25 08:02:20.207 RingBuf(/media/hdb1/1025_20070625080219.mpg): CalcReadAheadThresh(6384 KB)
			 -> threshhold(233 KB) min read(32 KB) blk size(128 KB)
2007-06-25 08:02:20.211 Opening ALSA audio device 'default'.
2007-06-25 08:02:20.224 Dec: Trying to select track (w/lang)
2007-06-25 08:02:20.224 Dec: Selecting first track
2007-06-25 08:02:20.224 Dec: Selected track #1 in the Unknown language(0)
2007-06-25 08:02:20.224 Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(0)
2007-06-25 08:02:20.226 Position map filled from DB to: 1
2007-06-25 08:02:20.227 SyncPositionMap watchingrecording, from DB: 1 entries
2007-06-25 08:02:20.228 PosMapFromEnc: Warning, tried to fetch PositionMap from Encoder but encoder returned framesWritten == 0
2007-06-25 08:02:20.228 SyncPositionMap watchingrecording no entries from encoder, try DB
2007-06-25 08:02:20.229 Position map filled from DB to: 1
2007-06-25 08:02:20.229 SyncPositionMap watchingrecording total: 1 entries
2007-06-25 08:02:20.229 SyncPositionMap, new totframes: 15, new length: 0, posMap size: 1
2007-06-25 08:02:20.230 AFD: Partial position map found
2007-06-25 08:02:20.230 AFD: Successfully opened decoder for file: "/media/hdb1/1025_20070625080219.mpg". novideo(0)
2007-06-25 08:02:20.241 VideoOutputXv: ctor
2007-06-25 08:02:20.242 Over/underscan. V: 0, H: 0, XOff: 0, YOff: 0
2007-06-25 08:02:20.242 Display Rect  left: 0, top: 0, width: 1280, height: 1024, aspect: 1.33333
2007-06-25 08:02:20.242 Video Rect    left: 0, top: 0, width: 480, height: 480, aspect: 1.33333
2007-06-25 08:02:20.246 VideoOutputXv: Pixel dimensions: Screen 1280x1024, window 1280x1024
2007-06-25 08:02:20.246 VideoOutputXv: Estimated display dimensions: 342x283 mm  Aspect: 1.20848
2007-06-25 08:02:20.246 VideoOutputXv: Estimated window dimensions: 342x283 mm  Aspect: 1.20848
2007-06-25 08:02:20.247 VideoOutputXv: XvMCTex: Init failed
2007-06-25 08:02:20.248 VideoOutputXv: @ j=3 Looking for flag[s]: XvInputMask XvImageMask 
2007-06-25 08:02:20.248 VideoOutputXv: Adaptor#0: Xgl Generic Texture Video has flag[s]: XvInputMask XvImageMask 
2007-06-25 08:02:20.248 VideoOutputXv: Grabbed xv port 48
2007-06-25 08:02:20.248 VideoOutputXv: XVideo surface found on port 48
2007-06-25 08:02:20.249 VideoOutputXv: XVideo Adaptor Name: 'Xgl Generic Texture Video'
2007-06-25 08:02:20.249 VideoOutputXv: XVideo Format #0 is 'YUY2'
2007-06-25 08:02:20.249 VideoOutputXv: XVideo Format #1 is 'YV12'
2007-06-25 08:02:20.249 VideoOutputXv: XVideo Format #2 is '
2007-06-25 08:02:20.249 VideoOutputXv: Using XVideo Format 'YV12'
2007-06-25 08:02:20.249 VideoOutputXv: CreateShmImages(32): video_dim: 480x480
2007-06-25 08:02:20.395 WriteAudio: buffer underrun

```

---

### Post by Kent84 on 2007-08-31
I get the same problem.. also using beryl with an ATI card.

---

### Post by newman on 2007-09-21
I have the same issue.
anyone???

---


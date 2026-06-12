---
title: "ffmpeg grab frame in live stream"
date: 2011-12-08
forum: Multimedia Software
---

### Post by ironman77 on 2011-12-08
Hello,
 
I need to grab a single frame from a rtmp (flv) live stream.
 
I use ffmpeg: ffmpeg.exe -i "rtmp://server/app/stream_name live=1" -an -vframes 1 -s 700x400 output.jpg
 
ffmpeg take a lot of time, this is the output:
 
```
ffmpeg version N-35462-g61b1d85, Copyright (c) 2000-2011 the FFmpeg developers
built on Dec 5 2011 14:22:27 with gcc 4.6.2
configuration: --enable-gpl --enable-version3 --disable-w32threads --enable-runtime-cpudetect --enable-avisynth --enable-bzlib --enable-frei0r --enable-libope
ncore-amrnb --enable-libopencore-amrwb --enable-libfreetype --enable-libgsm --enable-libmp3lame --enable-libopenjpeg --enable-librtmp --enable-libschroedinger -
-enable-libspeex --enable-libtheora --enable-libvo-aacenc --enable-libvo-amrwbenc --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxavs --enable-
libxvid --enable-zlib
libavutil 51. 30. 0 / 51. 30. 0
libavcodec 53. 40. 0 / 53. 40. 0
libavformat 53. 24. 0 / 53. 24. 0
libavdevice 53. 4. 0 / 53. 4. 0
libavfilter 2. 51. 0 / 2. 51. 0
libswscale 2. 1. 0 / 2. 1. 0
libpostproc 51. 2. 0 / 51. 2. 0
Parsing...
Parsed protocol: 0
Parsed host : server
Parsed app : app
RTMP_Connect1, ... connected, handshaking
HandShake: Type Answer : 03
HandShake: Server Uptime : 87696
HandShake: FMS Version : 0.0.0.0
HandShake: Handshaking finished....
RTMP_Connect1, handshaked
Invoking connect
HandleClientBW: client BW = 64000 0
HandleCtrl, received ctrl. type: 0, len: 6
HandleCtrl, Stream Begin 0
RTMP_ClientPacket, received: invoke 225 bytes
(object begin)
Property: <Name: no-name., STRING: _result>
Property: <Name: no-name., NUMBER: 1.00>
Property: NULL
Property: <Name: no-name., OBJECT>
(object begin)
Property: <Name: level, STRING: status>
Property: <Name: code, STRING: NetConnection.Connect.Success>
Property: <Name: description, STRING: Connection succeeded.>
Property: <Name: data, OBJECT>
(object begin)
Property: <Name: type, STRING: red5>
Property: <Name: version, STRING: 4,0,0,1121>
(object end)
Property: <Name: capabilities, NUMBER: 31.00>
Property: <Name: fmsVer, STRING: RED5/1,0,0,0>
Property: <Name: mode, NUMBER: 1.00>
(object end)
(object end)
HandleInvoke, server invoking <_result>
HandleInvoke, received result for method call <connect>
sending ctrl. type: 0x0003
Invoking createStream
FCSubscribe: stream_name
Invoking FCSubscribe
RTMP_ClientPacket, received: bytes read report
RTMP_ClientPacket, received: invoke 29 bytes
(object begin)
Property: <Name: no-name., STRING: _result>
Property: <Name: no-name., NUMBER: 2.00>
Property: NULL
Property: <Name: no-name., NUMBER: 1.00>
(object end)
HandleInvoke, server invoking <_result>
HandleInvoke, received result for method call <createStream>
SendPlay, seekTime=0, stopTime=0, sending play: stream_name
Invoking play
sending ctrl. type: 0x0003
RTMP_ClientPacket, received: invoke 207 bytes
(object begin)
Property: <Name: no-name., STRING: _error>
Property: <Name: no-name., NUMBER: 3.00>
Property: NULL
Property: <Name: no-name., OBJECT>
(object begin)
Property: <Name: level, STRING: error>
Property: <Name: code, STRING: NetConnection.Call.Failed>
Property: <Name: description, STRING: Method FCSubscribe with arguments [stream_name] not found>
Property: <Name: application, STRING: org.red5.server.service.MethodNotFoundException>
(object end)
(object end)
HandleInvoke, server invoking <_error>
rtmp server sent error
HandleChangeChunkSize, received: chunk size change to 1024
HandleCtrl, received ctrl. type: 0, len: 6
HandleCtrl, Stream Begin 1
RTMP_ClientPacket, received: invoke 160 bytes
(object begin)
Property: <Name: no-name., STRING: onStatus>
Property: <Name: no-name., NUMBER: 1.00>
Property: NULL
Property: <Name: no-name., OBJECT>
(object begin)
Property: <Name: level, STRING: status>
Property: <Name: code, STRING: NetStream.Play.Reset>
Property: <Name: description, STRING: Playing and resetting stream_name.>
Property: <Name: details, STRING: stream_name>
Property: <Name: clientid, NUMBER: 1.00>
(object end)
(object end)
HandleInvoke, server invoking <onStatus>
HandleInvoke, onStatus: NetStream.Play.Reset
RTMP_ClientPacket, received: invoke 154 bytes
(object begin)
Property: <Name: no-name., STRING: onStatus>
Property: <Name: no-name., NUMBER: 1.00>
Property: NULL
Property: <Name: no-name., OBJECT>
(object begin)
Property: <Name: level, STRING: status>
Property: <Name: code, STRING: NetStream.Play.Start>
Property: <Name: description, STRING: Started playing stream_name.>
Property: <Name: details, STRING: stream_name>
Property: <Name: clientid, NUMBER: 1.00>
(object end)
(object end)
HandleInvoke, server invoking <onStatus>
HandleInvoke, onStatus: NetStream.Play.Start
RTMP_ClientPacket, received: notify 413 bytes
(object begin)
Property: <Name: no-name., STRING: onMetaData>
Property: <Name: no-name., OBJECT>
(object begin)
Property: <Name: videokeyframe_freq, NUMBER: 3.00>
Property: <Name: videodevice, STRING: Webcam>
Property: <Name: avclevel, NUMBER: 31.00>
Property: <Name: width, NUMBER: 700.00>
Property: <Name: presetname, STRING: Custom>
Property: <Name: videodatarate, NUMBER: 325.00>
Property: <Name: copyright, STRING: Company>
Property: <Name: creationdate, STRING: Thu Dec 08 05:02:27 2011
>
Property: <Name: videocodecid, STRING: avc1>
Property: <Name: author, STRING: Company>
Property: <Name: avcprofile, NUMBER: 77.00>
Property: <Name: title, STRING: Live Stream>
Property: <Name: height, NUMBER: 400.00>
Property: <Name: description, STRING: Live Stream>
Property: <Name: framerate, NUMBER: 15.00>
(object end)
(object end)
Metadata:
videokeyframe_frequency3.00
videodevice Webcam
avclevel 31.00
width 700.00
presetname Custom
videodatarate 325.00
copyright Company
creationdate Thu Dec 08 05:02:27 2011
videocodecid avc1
author Company
avcprofile 77.00
title Live Stream
height 400.00
description Live Stream
framerate 15.00
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522289204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522291204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522293205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522295204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522298204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522300204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522303204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522305204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522308205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522311204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522314205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522317204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522319204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522321204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522323204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522327205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522329205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522331205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522334205
sending ctrl. type: 0x0007
RTMP_ClientPacket, received: invoke 177 bytes
(object begin)
Property: <Name: no-name., STRING: onStatus>
Property: <Name: no-name., NUMBER: 1.00>
Property: NULL
Property: <Name: no-name., OBJECT>
(object begin)
Property: <Name: level, STRING: warning>
Property: <Name: code, STRING: NetStream.Play.InsufficientBW>
Property: <Name: description, STRING: Data is playing behind the normal speed.>
Property: <Name: details, STRING: stream_name>
Property: <Name: clientid, NUMBER: 1.00>
(object end)
(object end)
HandleInvoke, server invoking <onStatus>
HandleInvoke, onStatus: NetStream.Play.InsufficientBW
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522337204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522339204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522341205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522345204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522347204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522349205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522351205
sending ctrl. type: 0x0007
RTMP_ClientPacket, received: invoke 177 bytes
(object begin)
Property: <Name: no-name., STRING: onStatus>
Property: <Name: no-name., NUMBER: 1.00>
Property: NULL
Property: <Name: no-name., OBJECT>
(object begin)
Property: <Name: level, STRING: warning>
Property: <Name: code, STRING: NetStream.Play.InsufficientBW>
Property: <Name: description, STRING: Data is playing behind the normal speed.>
Property: <Name: details, STRING: stream_name>
Property: <Name: clientid, NUMBER: 1.00>
(object end)
(object end)
HandleInvoke, server invoking <onStatus>
HandleInvoke, onStatus: NetStream.Play.InsufficientBW
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522353204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522355204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522357205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522359205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522361204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522364205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522366204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522368205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522370205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522372204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522374205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522376204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522378205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522380204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522383205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522385204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522387204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522389204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522391205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522393204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522395204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522398205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522400205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522403204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522405204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522408204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522411204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522414204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522418204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522420204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522424204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522426204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522429204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522432204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522435205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522443204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522445204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522450204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522452204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522454204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522456204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522459204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522461204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522466204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522468204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522472205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522470004
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522478204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522484204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522488205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522490205
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522493204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522504204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522506204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522508204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522518204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522520204
sending ctrl. type: 0x0007
HandleCtrl, received ctrl. type: 6, len: 6
HandleCtrl, Ping 522524204
sending ctrl. type: 0x0007
[flv @ 020C9D20] Estimating duration from bitrate, this may be inaccurate
Seems stream 0 codec frame rate differs from container frame rate: 30.00 (30/1) -> 15.00 (30/2)
Input #0, flv, from 'rtmp://server/app/stream_name live=1':
Metadata:
videokeyframe_frequency: 3
videodevice : Webcam
avclevel : 31
presetname : Custom
copyright : Company
creationdate : Thu Dec 08 05:02:27 2011
author : Company
avcprofile : 77
title : Live Stream
description : Live Stream
Duration: N/A, start: 0.080000, bitrate: 332 kb/s
Stream #0:0: Video: h264 (Main), yuv420p, 700x400 [SAR 1:1 DAR 47:26], 332 kb/s, 15 tbr, 1k tbn, 30 tbc
Incompatible pixel format 'yuv420p' for codec 'mjpeg', auto-selecting format 'yuvj420p'
[buffer @ 022B62E0] w:700 h:400 pixfmt:yuv420p tb:1/1000000 sar:1/1 sws_param:
[buffersink @ 022BE7E0] auto-inserting filter 'auto-inserted scale 0' between the filter 'src' and the filter 'out'
[scale @ 02D8B5C0] w:700 h:400 fmt:yuv420p -> w:700 h:400 fmt:yuvj420p flags:0x4
[mjpeg @ 0228DA40] removing common factors from framerate
Output #0, image2, to 'output.jpg':
Metadata:
videokeyframe_frequency: 3
videodevice : Webcam
avclevel : 31
presetname : Custom
copyright : Company
creationdate : Thu Dec 08 05:02:27 2011
author : Company
avcprofile : 77
title : Live Stream
description : Live Stream
encoder : Lavf53.24.0
Stream #0:0: Video: mjpeg, yuvj420p, 700x400 [SAR 1:1 DAR 47:26], q=2-31, 200 kb/s, 90k tbn, 15 tbc
Stream mapping:
Stream #0:0 -> #0:0 (h264 -> mjpeg)
Press [q] to stop, [?] for help
*** 2 dup!
frame= 1 fps= 0 q=5.9 Lsize= 0kB time=00:00:00.06 bitrate= 0.0kbits/s dup=2 drop=0
video:32kB audio:0kB global headers:0kB muxing overhead -100.000000%
Invoking deleteStream
```
 
After 5-10 minutes, i have my jpg...what is not correct?
 
Thank you!

---

### Post by quandt on 2011-12-18
Did you figure out a solution?

I am also seeing this type of behavior, just on trying to stream from a live rtmp feed, ie from red5.  Namely, something like:

ffplay -i "rtmp://localhost/oflaDemo/mycamfeed live=1" 

it takes a long time but eventually things start to play.

I've been thinking maybe to play around with telling ffmpeg what the format is ie via the -f flv and similar things....

ffmpeg -f flv -s AxB -i ....

But don't think it will help.  Regardless do please let me know what you find out.

---


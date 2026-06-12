---
title: "Mediaset Canale 5 RTMPDUMP problem"
date: 2013-07-18
forum: Multimedia Software
---

### Post by gallina94 on 2013-07-18
Hi all,
i cannot understand why today on mediaset channels on liveflash.tv (from the url [http://la-tv-gratis1.blogspot.it/2013/02/canale-5-streaming-gratis.html](http://la-tv-gratis1.blogspot.it/2013/02/canale-5-streaming-gratis.html))  i'm not able to start the stream (worked every time in the past). Following the parameter i got with rtmpdumphelper


```
RTMP Proxy Server v2.4
(c) 2010 Andrej Stepanchuk, Howard Chu; license: GPL

Streaming on [rtmp://0.0.0.0:1935](rtmp://0.0.0.0:1935)
WARNING: Trying different position for client digest!
Processing connect
app: stream
flashVer: WIN 11,7,700,224
swfUrl: [http://www.liveflash.tv/resources/scripts/eplayer.swf](http://www.liveflash.tv/resources/scripts/eplayer.swf)
tcUrl: [rtmp://5.63.151.44/stream](rtmp://5.63.151.44/stream)
pageUrl: [http://www.liveflash.tv/embedplayer/csa ... /1/550/380]("http://www.liveflash.tv/embedplayer/csadasdasd55/1/550/380")
Playpath: csadasdasd55?id=98431
Saving as: csadasdasd55
INFO: Metadata:
INFO:   presetname            Custom
INFO:   creationdate          Thu Jul 18 11:15:09 2013
INFO:   videodevice           SplitCam Video Capture
INFO:   framerate             25.00
INFO:   width                 480.00
INFO:   height                360.00
INFO:   videocodecid          avc1
INFO:   videodatarate         320.00
INFO:   avclevel              31.00
INFO:   avcprofile            66.00
INFO:   videokeyframe_frequency5.00
INFO:   audiodevice           Line in (e2eSoft VAudio)
INFO:   audiosamplerate       22050.00
INFO:   audiochannels         2.00
INFO:   audioinputvolume      75.00
INFO:   audiocodecid          .mp3
INFO:   audiodatarate         48.00
WARNING: ignoring too small audio packet: size: 0






Now i put all the parameter in rtmpdump

rtmpdump  -z -r "rtmp://5.63.151.44/stream" -a "stream" -f "WIN 11,7,700,224" -W  "http://www.liveflash.tv/resources/scripts/eplayer.swf" -C "S:OK" -p  "http://www.liveflash.tv/embedplayer/csadasdasd55/1/550/380" -y  "csadasdasd55?id=98431" -v

but rtmpdump itself remain stucked on "connected" and the stream never plays. Here the log


D:\streamMaterial\rtmpdumphelper>rtmpdump  -z -r "rtmp://5.63.151.44/stream" -a "stream" -f "WIN 11,7,700,224" -W  "http://www.liveflash.tv/resources/scripts/eplayer.swf" -C "S:OK" -p  "http://www.liveflash.tv/embedplayer/csadasdasd55/1/550/380" -y  "csadasdasd55?id=98431" -v
RTMPDump v2.4
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
DEBUG: Parsing...
DEBUG: Parsed protocol: 0
DEBUG: Parsed host    : 5.63.151.44
DEBUG: Parsed app     : stream
WARNING: You haven't specified an output file (-o filename), using stdout
DEBUG: Protocol : RTMP
DEBUG: Hostname : 5.63.151.44
DEBUG: Port     : 1935
DEBUG: Playpath : csadasdasd55?id=98431
DEBUG: tcUrl    : [rtmp://5.63.151.44:1935/stream](rtmp://5.63.151.44:1935/stream)
DEBUG: swfUrl   : [http://www.liveflash.tv/resources/scripts/eplayer.swf](http://www.liveflash.tv/resources/scripts/eplayer.swf)
DEBUG: pageUrl  : [http://www.liveflash.tv/embedplayer/csa ... /1/550/380]("http://www.liveflash.tv/embedplayer/csadasdasd55/1/550/380")
DEBUG: app      : stream
DEBUG: flashVer : WIN 11,7,700,224
DEBUG: live     : yes
DEBUG: timeout  : 30 sec
DEBUG: SWFSHA256:
DEBUG: d0 b7 bb 74 61 ff ca 4e 64 df b1 43 23 4c cc 58
DEBUG: 13 3c a3 40 f9 25 c4 bc c3 94 6d ca 3e d6 d0 07
DEBUG: SWFSize  : 23967
DEBUG: Setting buffer time to: 36000000ms
Connecting ...
DEBUG: RTMP_Connect1, ... connected, handshaking
DEBUG: HandShake: Client type: 03
DEBUG: HandShake: Client digest offset: 53
DEBUG: HandShake: Initial client digest:
DEBUG: 51 da 98 21 77 3b b0 bb c4 65 71 94 f3 37 68 99
DEBUG: 04 e4 8a ae 22 74 b9 b4 51 b8 b1 f2 55 0f 56 01
DEBUG: HandShake: Type Answer   : 03
DEBUG: HandShake: Server Uptime : 96850052
DEBUG: HandShake: FMS Version   : 3.0.1.1
DEBUG: HandShake: Calculated digest key from secure key and server digest:
DEBUG: 9e ed a0 e9 fc b3 3f d8 7e 08 1f 41 80 75 a1 bb
DEBUG: a5 5c ec c1 5f 4c 3d f0 27 7f 69 ae b0 f9 45 47
DEBUG: HandShake: Client signature calculated:
DEBUG: fd 79 74 36 2a 2c e3 8e 47 6b 78 79 fd 17 fe ce
DEBUG: 3b d6 19 d8 30 cf ce a5 ab 80 01 61 a7 15 e8 28
DEBUG: HandShake: Server sent signature:
DEBUG: 12 70 40 2d b4 9a f9 cb 79 fd 33 70 89 f7 59 28
DEBUG: 6b 6a 9a 10 63 e9 e0 98 4f 33 34 80 5f 51 c5 94
DEBUG: HandShake: Digest key:
DEBUG: ca 40 f1 99 a5 2f 71 86 2e 0f 97 b6 8d 94 8f 6e
DEBUG: d0 c8 24 31 2b aa c8 5f 91 5a 98 d2 9b bd 6f 26
DEBUG: HandShake: Signature calculated:
DEBUG: 12 70 40 2d b4 9a f9 cb 79 fd 33 70 89 f7 59 28
DEBUG: 6b 6a 9a 10 63 e9 e0 98 4f 33 34 80 5f 51 c5 94
DEBUG: HandShake: Genuine Adobe Flash Media Server
DEBUG: HandShake: Handshaking finished....
DEBUG: RTMP_Connect1, handshaked
DEBUG2: RTMP_SendPacket: fd=136, size=344
DEBUG2:   0000:  03 00 00 00 00 01 58 14  00 00 00 00               ......X.....
DEBUG2:   0000:  02 00 07 63 6f 6e 6e 65  63 74 00 3f f0 00 00 00   ...connect.?....
DEBUG2:   0010:  00 00 00 03 00 03 61 70  70 02 00 06 73 74 72 65   ......app...stre
DEBUG2:   0020:  61 6d 00 08 66 6c 61 73  68 56 65 72 02 00 10 57   am..flashVer...W
DEBUG2:   0030:  49 4e 20 31 31 2c 37 2c  37 30 30 2c 32 32 34 00   IN 11,7,700,224.
DEBUG2:   0040:  06 73 77 66 55 72 6c 02  00 35 68 74 74 70 3a 2f   .swfUrl..5http:/
DEBUG2:   0050:  2f 77 77 77 2e 6c 69 76  65 66 6c 61 73 68 2e 74   /www.liveflash.t
DEBUG2:   0060:  76 2f 72 65 73 6f 75 72  63 65 73 2f 73 63 72 69   v/resources/scri
DEBUG2:   0070:  70 74 73 2f 65 70 6c 61  79 65 72 2e 73 77 66 00   pts/eplayer.swf.
DEBUG2:   0000:  c3                                                 .
DEBUG2:   0000:  05 74 63 55 72 6c 02 00  1e 72 74 6d 70 3a 2f 2f   .tcUrl...rtmp://
DEBUG2:   0010:  35 2e 36 33 2e 31 35 31  2e 34 34 3a 31 39 33 35   5.63.151.44:1935
DEBUG2:   0020:  2f 73 74 72 65 61 6d 00  04 66 70 61 64 01 00 00   /stream..fpad...
DEBUG2:   0030:  0c 63 61 70 61 62 69 6c  69 74 69 65 73 00 40 2e   .capabilities.@.
DEBUG2:   0040:  00 00 00 00 00 00 00 0b  61 75 64 69 6f 43 6f 64   ........audioCod
DEBUG2:   0050:  65 63 73 00 40 a8 ee 00  00 00 00 00 00 0b 76 69   ecs.@.........vi
DEBUG2:   0060:  64 65 6f 43 6f 64 65 63  73 00 40 6f 80 00 00 00   deoCodecs.@o....
DEBUG2:   0070:  00 00 00 0d 76 69 64 65  6f 46 75 6e 63 74 69 6f   ....videoFunctio
DEBUG2:   0000:  c3                                                 .
DEBUG2:   0000:  6e 00 3f f0 00 00 00 00  00 00 00 07 70 61 67 65   n.?.........page
DEBUG2:   0010:  55 72 6c 02 00 3a 68 74  74 70 3a 2f 2f 77 77 77   Url..:[http://www](http://www)
DEBUG2:   0020:  2e 6c 69 76 65 66 6c 61  73 68 2e 74 76 2f 65 6d   .liveflash.tv/em
DEBUG2:   0030:  62 65 64 70 6c 61 79 65  72 2f 63 73 61 64 61 73   bedplayer/csadas
DEBUG2:   0040:  64 61 73 64 35 35 2f 31  2f 35 35 30 2f 33 38 30   dasd55/1/550/380
DEBUG2:   0050:  00 00 09 02 00 02 4f 4b                            ......OK
DEBUG: Invoking connect
INFO: Connected...
DEBUG2: RTMP_ReadPacket: fd=136
DEBUG2:   0000:  02 00 00 00 00 00 04 05  00 00 00 00               ............
DEBUG2:   0000:  00 26 25 a0                                        .&%.
DEBUG: HandleServerBW: server BW = 2500000
DEBUG2: RTMP_ReadPacket: fd=136
DEBUG2:   0000:  02 00 00 00 00 00 05 06  00 00 00 00               ............
DEBUG2:   0000:  00 26 25 a0 02                                     .&%..
DEBUG: HandleClientBW: client BW = 2500000 2
DEBUG2: RTMP_ReadPacket: fd=136
DEBUG2:   0000:  02 00 00 00 00 00 06 04  00 00 00 00               ............
DEBUG2:   0000:  00 00 00 00 00 00                                  ......
DEBUG: HandleCtrl, received ctrl. type: 0, len: 6
DEBUG: HandleCtrl, Stream Begin 0
DEBUG2: RTMP_ReadPacket: fd=136
DEBUG2:   0000:  02 00 00 00 00 00 04 01  00 00 00 00               ............
DEBUG2:   0000:  00 00 10 00                                        ....
DEBUG: HandleChangeChunkSize, received: chunk size change to 4096
DEBUG2: RTMP_ReadPacket: fd=136
DEBUG2:   0000:  03 00 00 00 00 01 03 14  00 00 00 00               ............
DEBUG2:   0000:  02 00 07 5f 72 65 73 75  6c 74 00 3f f0 00 00 00   ..._result.?....
DEBUG2:   0010:  00 00 00 03 00 06 66 6d  73 56 65 72 02 00 0d 46   ......fmsVer...F
DEBUG2:   0020:  4d 53 2f 33 2c 35 2c 34  2c 32 31 30 00 0c 63 61   MS/3,5,4,210..ca
DEBUG2:   0030:  70 61 62 69 6c 69 74 69  65 73 00 40 3f 00 00 00   pabilities.@?...
DEBUG2:   0040:  00 00 00 00 04 6d 6f 64  65 00 3f f0 00 00 00 00   .....mode.?.....
DEBUG2:   0050:  00 00 00 00 09 03 00 05  6c 65 76 65 6c 02 00 06   ........level...
DEBUG2:   0060:  73 74 61 74 75 73 00 04  63 6f 64 65 02 00 1d 4e   status..code...N
DEBUG2:   0070:  65 74 43 6f 6e 6e 65 63  74 69 6f 6e 2e 43 6f 6e   etConnection.Con
DEBUG2:   0080:  6e 65 63 74 2e 53 75 63  63 65 73 73 00 0b 64 65   nect.Success..de
DEBUG2:   0090:  73 63 72 69 70 74 69 6f  6e 02 00 15 43 6f 6e 6e   scription...Conn
DEBUG2:   00a0:  65 63 74 69 6f 6e 20 73  75 63 63 65 65 64 65 64   ection succeeded
DEBUG2:   00b0:  2e 00 04 64 61 74 61 08  00 00 00 00 00 07 76 65   ...data.......ve
DEBUG2:   00c0:  72 73 69 6f 6e 02 00 09  33 2c 35 2c 34 2c 32 31   rsion...3,5,4,21
DEBUG2:   00d0:  30 00 00 09 00 08 63 6c  69 65 6e 74 69 64 00 41   0.....clientid.A
DEBUG2:   00e0:  de dd 6a 67 c0 00 00 00  0e 6f 62 6a 65 63 74 45   ..jg.....objectE
DEBUG2:   00f0:  6e 63 6f 64 69 6e 67 00  00 00 00 00 00 00 00 00   ncoding.........
DEBUG2:   0100:  00 00 09                                           ...
DEBUG: RTMP_ClientPacket, received: invoke 259 bytes
DEBUG: (object begin)
DEBUG: Property: <Name:           no-name., STRING:     _result>
DEBUG: Property: <Name:           no-name., NUMBER:     1.00>
DEBUG: Property: <Name:           no-name., OBJECT>
DEBUG: (object begin)
DEBUG: Property: <Name:             fmsVer, STRING:     FMS/3,5,4,210>
DEBUG: Property: <Name:       capabilities, NUMBER:     31.00>
DEBUG: Property: <Name:               mode, NUMBER:     1.00>
DEBUG: (object end)
DEBUG: Property: <Name:           no-name., OBJECT>
DEBUG: (object begin)
DEBUG: Property: <Name:              level, STRING:     status>
DEBUG: Property: <Name:               code, STRING:     NetConnection.Connect.Success>
DEBUG: Property: <Name:        description, STRING:     Connection succeeded.>
DEBUG: Property: <Name:               data, ECMA_ARRAY>
DEBUG: (object begin)
DEBUG: Property: <Name:            version, STRING:     3,5,4,210>
DEBUG: (object end)
DEBUG: Property: <Name:           clientid, NUMBER:     2071308703.00>
DEBUG: Property: <Name:     objectEncoding, NUMBER:     0.00>
DEBUG: (object end)
DEBUG: (object end)
DEBUG: HandleInvoke, server invoking <_result>
DEBUG: HandleInvoke, received result for method call <connect>
DEBUG2: RTMP_SendPacket: fd=136, size=4
DEBUG2:   0000:  02 00 00 00 00 00 04 05  00 00 00 00               ............
DEBUG2:   0000:  00 26 25 a0                                        .&%.
DEBUG: sending ctrl. type: 0x0003
DEBUG2: RTMP_SendPacket: fd=136, size=10
DEBUG2:   0000:  42 00 00 00 00 00 0a 04                            B.......
DEBUG2:   0000:  00 03 00 00 00 00 00 00  01 2c                     .........,
DEBUG2: RTMP_SendPacket: fd=136, size=25
DEBUG2:   0000:  43 00 00 00 00 00 19 14                            C.......
DEBUG2:   0000:  02 00 0c 63 72 65 61 74  65 53 74 72 65 61 6d 00   ...createStream.
DEBUG2:   0010:  40 00 00 00 00 00 00 00  05                        @........
DEBUG: Invoking createStream
DEBUG: FCSubscribe: csadasdasd55?id=98431
DEBUG2: RTMP_SendPacket: fd=136, size=48
DEBUG2:   0000:  43 00 00 00 00 00 30 14                            C.....0.
DEBUG2:   0000:  02 00 0b 46 43 53 75 62  73 63 72 69 62 65 00 40   ...FCSubscribe.@
DEBUG2:   0010:  08 00 00 00 00 00 00 05  02 00 15 63 73 61 64 61   ...........csada
DEBUG2:   0020:  73 64 61 73 64 35 35 3f  69 64 3d 39 38 34 33 31   sdasd55?id=98431
DEBUG: Invoking FCSubscribe
DEBUG2: RTMP_ReadPacket: fd=136
DEBUG2:   0000:  03 00 00 00 00 00 1d 14  00 00 00 00               ............
DEBUG2:   0000:  02 00 07 5f 72 65 73 75  6c 74 00 40 00 00 00 00   ..._result.@....
DEBUG2:   0010:  00 00 00 05 00 3f f0 00  00 00 00 00 00            .....?.......
DEBUG: RTMP_ClientPacket, received: invoke 29 bytes
DEBUG: (object begin)
DEBUG: Property: <Name:           no-name., STRING:     _result>
DEBUG: Property: <Name:           no-name., NUMBER:     2.00>
DEBUG: Property: NULL
DEBUG: Property: <Name:           no-name., NUMBER:     1.00>
DEBUG: (object end)
DEBUG: HandleInvoke, server invoking <_result>
DEBUG: HandleInvoke, received result for method call <createStream>
DEBUG: SendPlay, seekTime=0, stopTime=0, sending play: csadasdasd55?id=98431
DEBUG2: RTMP_SendPacket: fd=136, size=50
DEBUG2:   0000:  08 00 00 00 00 00 32 14  01 00 00 00               ......2.....
DEBUG2:   0000:  02 00 04 70 6c 61 79 00  40 10 00 00 00 00 00 00   ...play.@.......
DEBUG2:   0010:  05 02 00 15 63 73 61 64  61 73 64 61 73 64 35 35   ....csadasdasd55
DEBUG2:   0020:  3f 69 64 3d 39 38 34 33  31 00 c0 8f 40 00 00 00   ?id=98431...@...
DEBUG2:   0030:  00 00                                              ..
DEBUG: Invoking play
DEBUG: sending ctrl. type: 0x0003
DEBUG2: RTMP_SendPacket: fd=136, size=10
DEBUG2:   0000:  c2                                                 .
DEBUG2:   0000:  00 03 00 00 00 01 02 25  51 00                     .......%Q.
DEBUG2: RTMP_ReadPacket: fd=136
DEBUG2:   0000:  03 00 00 00 00 00 91 14  00 00 00 00               ............
DEBUG2:   0000:  02 00 0d 6f 6e 46 43 53  75 62 73 63 72 69 62 65   ...onFCSubscribe
DEBUG2:   0010:  00 00 00 00 00 00 00 00  00 05 03 00 05 6c 65 76   .............lev
DEBUG2:   0020:  65 6c 02 00 06 73 74 61  74 75 73 00 04 63 6f 64   el...status..cod
DEBUG2:   0030:  65 02 00 14 4e 65 74 53  74 72 65 61 6d 2e 50 6c   e...NetStream.Pl
DEBUG2:   0040:  61 79 2e 53 74 61 72 74  00 0b 64 65 73 63 72 69   ay.Start..descri
DEBUG2:   0050:  70 74 69 6f 6e 02 00 23  46 43 53 75 62 73 63 72   ption..#FCSubscr
DEBUG2:   0060:  69 62 65 20 74 6f 20 73  74 72 65 61 6d 20 63 73   ibe to stream cs
DEBUG2:   0070:  61 64 61 73 64 61 73 64  35 35 2e 00 08 63 6c 69   adasdasd55...cli
DEBUG2:   0080:  65 6e 74 69 64 00 41 de  dd 6a 67 c0 00 00 00 00   entid.A..jg.....
DEBUG2:   0090:  09                                                 .
DEBUG: RTMP_ClientPacket, received: invoke 145 bytes
DEBUG: (object begin)
DEBUG: Property: <Name:           no-name., STRING:     onFCSubscribe>
DEBUG: Property: <Name:           no-name., NUMBER:     0.00>
DEBUG: Property: NULL
DEBUG: Property: <Name:           no-name., OBJECT>
DEBUG: (object begin)
DEBUG: Property: <Name:              level, STRING:     status>
DEBUG: Property: <Name:               code, STRING:     NetStream.Play.Start>
DEBUG: Property: <Name:        description, STRING:     FCSubscribe to stream csadasdasd55.>
DEBUG: Property: <Name:           clientid, NUMBER:     2071308703.00>
DEBUG: (object end)
DEBUG: (object end)
DEBUG: HandleInvoke, server invoking <onFCSubscribe>
DEBUG2: RTMP_ReadPacket: fd=136
DEBUG2:   0000:  02 00 00 00 00 00 06 04  00 00 00 00               ............
DEBUG2:   0000:  00 06 00 00 51 3d                                  ....Q=
DEBUG: HandleCtrl, received ctrl. type: 6, len: 6
DEBUG: HandleCtrl, Ping 20797
DEBUG: sending ctrl. type: 0x0007
DEBUG2: RTMP_SendPacket: fd=136, size=6
DEBUG2:   0000:  42 00 00 00 00 00 06 04                            B.......
DEBUG2:   0000:  00 07 00 00 51 3d                                  ....Q=
DEBUG2: RTMP_ReadPacket: fd=136
```




Can someone help me?
Thanks

---


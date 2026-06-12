---
title: "Problem with rtmpdump"
date: 2013-05-07
forum: Multimedia Software
---

### Post by gallina94 on 2013-05-07
Hi all,
i'm having problem with rtmpdump. sniffed the following traffic from the URL

[http://la-tv-gratis1.blogspot.it/2013/02/rete-4-streaming-gratis.html](http://la-tv-gratis1.blogspot.it/2013/02/rete-4-streaming-gratis.html)

-----------------------------this is the Wireshark capture-------------------------------------------------------

XUqlykxq3.GBG..'..\..#t......*U....?..VqR..(p>......m..S....A.?....c.....">y........
_..j..vc..+.......z.{....9..X.....k..6@......L./.t.......w
......a........connect.?..........app...live..flashVer...MAC 11,6,602,180..swfUrl..0http://www.ucaster.eu/static/scripts/eplayer.swf..tcUrl....rtmp://109.123.126.28/live..fpad....capabilities.@m........audioCodecs.@.........videoCodecs.@o.......
videoFunction.?..........pageUrl..5http://www.ucaster.eu/embedded/gfyjfdthfgli/1/500/380..objectEncoding.@.............OK..Ka'X\.k+.(.s...>P.L.ae.3..Y....*......_." ..GY.0..=.Q ...V.......x....l.a:#I....N...4J...R..g..'8..+.m.............R...e6}../.7C.+..I.}L\h+j.4..1G&..`
.NV.Z..G_I. ..`.Vp...:I..T)..eqH.e.3$.&..............&%..............&%..................................................._result.?..........fmsVer...FMS/3,5,5,2004..capabilities.@?........mode.?.............level...status..code...NetConnection.Connect.Success..description...Connection succeeded...data.......version..
3,5,5,2004.....clientid.A...}@....objectEncoding.@...........J;..........&%.C..
..*.....vujkoMiLazarBarakovOdMokrino.@........................_result.@..........B.....
...........C...........createStream.@........................_result.@.........?.............3.........play.............gfyjfdthfgli?id=44746...@.................................................onStatus.............level...status..code...NetStream.Play.Reset..description..IPlaying and resetting rtmp://ucaster.eu:1935/live/_definst_/gfyjfdthfgli...clientid.A...}@....................onStatus.............level...status..code...NetStream.Play.Start..description..CStarted playing rtmp://ucaster.eu:1935/live/_definst_/gfyjfdthfgli...clientid.A...}@...
-----------------------------end Wireshark capture-------------------------------------------------------

and this is the command line for rtmpdump

rtmpdump -z -r rtmp://109.123.126.28/live -a "live" -f "MAC 11,6,602,180" -W "http://www.ucaster.eu/static/scripts/eplayer.swf" -p "http://www.ucaster.eu/embedded/gfyjfdthfgli/1/500/380" -y "gfyjfdthfgli?id=44746" -v 

but i get this error:

DEBUG: Parsing...
DEBUG: Parsed protocol: 0
DEBUG: Parsed host    : 109.123.126.28
DEBUG: Parsed app     : live
WARNING: You haven't specified an output file (-o filename), using stdout
DEBUG: Protocol : RTMP
DEBUG: Hostname : 109.123.126.28
DEBUG: Port     : 1935
DEBUG: Playpath : gfyjfdthfgli?id=44746
DEBUG: tcUrl    : rtmp://109.123.126.28:1935/live
DEBUG: swfUrl   : [http://www.ucaster.eu/static/scripts/eplayer.swf](http://www.ucaster.eu/static/scripts/eplayer.swf)
DEBUG: pageUrl  : [http://www.ucaster.eu/embedded/gfyjfdthfgli/1/500/380](http://www.ucaster.eu/embedded/gfyjfdthfgli/1/500/380)
DEBUG: app      : live
DEBUG: flashVer : MAC 11,6,602,180
DEBUG: live     : yes
DEBUG: timeout  : 30 sec
DEBUG: SWFSHA256:
DEBUG: 2a a0 f8 06 81 5b 8e b5 32 e6 02 66 f8 93 d9 b5
DEBUG: 05 fc 9d 1d d8 c1 1b 82 14 2a 8e d1 68 b0 73 35
DEBUG: SWFSize  : 27522
DEBUG: Setting buffer time to: 36000000ms
Connecting ...
DEBUG: RTMP_Connect1, ... connected, handshaking
DEBUG: HandShake: Client type: 03
DEBUG: HandShake: Client digest offset: 430
DEBUG: HandShake: Initial client digest:
DEBUG: 50 1f 4b e4 23 15 54 26 e5 dc ce fa f3 b6 b7 3a
DEBUG: 20 95 f9 1e 77 1d 00 d6 c5 9a 15 d3 30 c1 59 9f
DEBUG: HandShake: Type Answer   : 03
DEBUG: HandShake: Server Uptime : 96850052
DEBUG: HandShake: FMS Version   : 3.0.1.1
DEBUG: HandShake: Calculated digest key from secure key and server digest:
DEBUG: 9e ed a0 e9 fc b3 3f d8 7e 08 1f 41 80 75 a1 bb
DEBUG: a5 5c ec c1 5f 4c 3d f0 27 7f 69 ae b0 f9 45 47
DEBUG: HandShake: Client signature calculated:
DEBUG: 80 bb f6 1c d1 ae 47 08 bd 0c d2 61 e3 28 bb 51
DEBUG: b0 e6 43 fd 0e 1e 21 93 27 80 78 65 ed 8e 53 86
DEBUG: HandShake: Server sent signature:
DEBUG: 82 5e dd cd 80 e0 06 75 4f 6a 94 b9 d1 f6 5a da
DEBUG: 7f 50 1f e5 ff 2e 03 ce f1 9e 5e c6 4f 01 0a 48
DEBUG: HandShake: Digest key:
DEBUG: 92 cc b7 fd f7 7d 54 65 8e 7e 54 b0 c5 ab b0 9d
DEBUG: 71 c0 23 bf 7f 86 f0 c8 9c 62 cd c0 89 8e 6f 3f
DEBUG: HandShake: Signature calculated:
DEBUG: 82 5e dd cd 80 e0 06 75 4f 6a 94 b9 d1 f6 5a da
DEBUG: 7f 50 1f e5 ff 2e 03 ce f1 9e 5e c6 4f 01 0a 48
DEBUG: HandShake: Genuine Adobe Flash Media Server
DEBUG: HandShake: Handshaking finished....
DEBUG: RTMP_Connect1, handshaked
DEBUG2: RTMP_SendPacket: fd=4, size=328
DEBUG2:   0000:  03 00 00 00 00 01 48 14  00 00 00 00               ......H.....
DEBUG2:   0000:  02 00 07 63 6f 6e 6e 65  63 74 00 3f f0 00 00 00   ...connect.?....
DEBUG2:   0010:  00 00 00 03 00 03 61 70  70 02 00 04 6c 69 76 65   ......app...live
DEBUG2:   0020:  00 08 66 6c 61 73 68 56  65 72 02 00 10 4d 41 43   ..flashVer...MAC
DEBUG2:   0030:  20 31 31 2c 36 2c 36 30  32 2c 31 38 30 00 06 73    11,6,602,180..s
DEBUG2:   0040:  77 66 55 72 6c 02 00 30  68 74 74 70 3a 2f 2f 77   wfUrl..0http://w
DEBUG2:   0050:  77 77 2e 75 63 61 73 74  65 72 2e 65 75 2f 73 74   ww.ucaster.eu/st
DEBUG2:   0060:  61 74 69 63 2f 73 63 72  69 70 74 73 2f 65 70 6c   atic/scripts/epl
DEBUG2:   0070:  61 79 65 72 2e 73 77 66  00 05 74 63 55 72 6c 02   ayer.swf..tcUrl.
DEBUG2:   0000:  c3                                                 .
DEBUG2:   0000:  00 1f 72 74 6d 70 3a 2f  2f 31 30 39 2e 31 32 33   ..rtmp://109.123
DEBUG2:   0010:  2e 31 32 36 2e 32 38 3a  31 39 33 35 2f 6c 69 76   .126.28:1935/liv
DEBUG2:   0020:  65 00 04 66 70 61 64 01  00 00 0c 63 61 70 61 62   e..fpad....capab
DEBUG2:   0030:  69 6c 69 74 69 65 73 00  40 2e 00 00 00 00 00 00   ilities.@.......
DEBUG2:   0040:  00 0b 61 75 64 69 6f 43  6f 64 65 63 73 00 40 a8   ..audioCodecs.@.
DEBUG2:   0050:  ee 00 00 00 00 00 00 0b  76 69 64 65 6f 43 6f 64   ........videoCod
DEBUG2:   0060:  65 63 73 00 40 6f 80 00  00 00 00 00 00 0d 76 69   ecs.@o........vi
DEBUG2:   0070:  64 65 6f 46 75 6e 63 74  69 6f 6e 00 3f f0 00 00   deoFunction.?...
DEBUG2:   0000:  c3                                                 .
DEBUG2:   0000:  00 00 00 00 00 07 70 61  67 65 55 72 6c 02 00 35   ......pageUrl..5
DEBUG2:   0010:  68 74 74 70 3a 2f 2f 77  77 77 2e 75 63 61 73 74   [http://www.ucast](http://www.ucast)
DEBUG2:   0020:  65 72 2e 65 75 2f 65 6d  62 65 64 64 65 64 2f 67   er.eu/embedded/g
DEBUG2:   0030:  66 79 6a 66 64 74 68 66  67 6c 69 2f 31 2f 35 30   fyjfdthfgli/1/50
DEBUG2:   0040:  30 2f 33 38 30 00 00 09                            0/380...
DEBUG: Invoking connect
INFO: Connected...
DEBUG2: RTMP_ReadPacket: fd=4
DEBUG2:   0000:  02 00 00 00 00 00 04 05  00 00 00 00               ............
DEBUG2:   0000:  00 26 25 a0                                        .&%.
DEBUG: HandleServerBW: server BW = 2500000
DEBUG2: RTMP_ReadPacket: fd=4
DEBUG2:   0000:  02 00 00 00 00 00 05 06  00 00 00 00               ............
DEBUG2:   0000:  00 26 25 a0 02                                     .&%..
DEBUG: HandleClientBW: client BW = 2500000 2
DEBUG2: RTMP_ReadPacket: fd=4
DEBUG2:   0000:  02 00 00 00 00 00 06 04  00 00 00 00               ............
DEBUG2:   0000:  00 00 00 00 00 00                                  ......
DEBUG: HandleCtrl, received ctrl. type: 0, len: 6
DEBUG: HandleCtrl, Stream Begin 0
DEBUG2: RTMP_ReadPacket: fd=4
DEBUG2:   0000:  02 00 00 00 00 00 04 01  00 00 00 00               ............
DEBUG2:   0000:  00 00 10 00                                        ....
DEBUG: HandleChangeChunkSize, received: chunk size change to 4096
DEBUG2: RTMP_ReadPacket: fd=4
DEBUG2:   0000:  03 00 00 00 00 00 a3 14  00 00 00 00               ............
DEBUG2:   0000:  02 00 06 5f 65 72 72 6f  72 00 3f f0 00 00 00 00   ..._error.?.....
DEBUG2:   0010:  00 00 05 03 00 05 6c 65  76 65 6c 02 00 05 65 72   ......level...er
DEBUG2:   0020:  72 6f 72 00 04 63 6f 64  65 02 00 1e 4e 65 74 43   ror..code...NetC
DEBUG2:   0030:  6f 6e 6e 65 63 74 69 6f  6e 2e 43 6f 6e 6e 65 63   onnection.Connec
DEBUG2:   0040:  74 2e 52 65 6a 65 63 74  65 64 00 0b 64 65 73 63   t.Rejected..desc
DEBUG2:   0050:  72 69 70 74 69 6f 6e 02  00 33 43 6f 6e 6e 65 63   ription..3Connec
DEBUG2:   0060:  74 69 6f 6e 20 66 61 69  6c 65 64 3a 20 41 70 70   tion failed: App
DEBUG2:   0070:  6c 69 63 61 74 69 6f 6e  20 72 65 6a 65 63 74 65   lication rejecte
DEBUG2:   0080:  64 20 63 6f 6e 6e 65 63  74 69 6f 6e 2e 00 08 63   d connection...c
DEBUG2:   0090:  6c 69 65 6e 74 69 64 00  41 de 6c c3 2e 00 00 00   lientid.A.l.....
DEBUG2:   00a0:  00 00 09                                           ...
DEBUG: RTMP_ClientPacket, received: invoke 163 bytes
DEBUG: (object begin)
DEBUG: Property: <Name:           no-name., STRING:     _error>
DEBUG: Property: <Name:           no-name., NUMBER:     1.00>
DEBUG: Property: NULL
DEBUG: Property: <Name:           no-name., OBJECT>
DEBUG: (object begin)
DEBUG: Property: <Name:              level, STRING:     error>
DEBUG: Property: <Name:               code, STRING:     NetConnection.Connect.Rejected>
DEBUG: Property: <Name:        description, STRING:     Connection failed: Application rejected connection.>
DEBUG: Property: <Name:           clientid, NUMBER:     2041777336.00>
DEBUG: (object end)
DEBUG: (object end)
DEBUG: HandleInvoke, server invoking <_error>
ERROR: rtmp server sent error
DEBUG2: RTMP_ReadPacket: fd=4
DEBUG2:   0000:  03 00 00 00 00 00 12 14  00 00 00 00               ............
DEBUG2:   0000:  02 00 05 63 6c 6f 73 65  00 00 00 00 00 00 00 00   ...close........
DEBUG2:   0010:  00 05                                              ..
DEBUG: RTMP_ClientPacket, received: invoke 18 bytes
DEBUG: (object begin)
DEBUG: Property: <Name:           no-name., STRING:     close>
DEBUG: Property: <Name:           no-name., NUMBER:     0.00>
DEBUG: Property: NULL
DEBUG: (object end)
DEBUG: HandleInvoke, server invoking <close>
ERROR: rtmp server requested close
DEBUG: Closing connection.



Can someone help me????
Thank you

---


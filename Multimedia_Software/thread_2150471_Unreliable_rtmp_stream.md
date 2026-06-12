---
title: "Unreliable rtmp stream?"
date: 2013-06-01
forum: Multimedia Software
---

### Post by andrew.46 on 2013-06-01
I have been spending some time trying to get the following stream playing via rtmpdump:

```

rtmpdump --live --verbose \
         --swfVfy "http://www.abc.net.au/res/players/aacPlayer.swf" \
         --pageUrl "http://www.abc.net.au/classic/player/" \
         -r "rtmp://cp112896.live.edgefcs.net/live/classic_fm@40676" | mplayer -

```

Sometimes it plays and sometimes it errors out, a variety of error messages. Can somebody test the stream in the above manner and tell me if it works perfectly from their end or is unreliable?

---

### Post by oldos2er on 2013-06-01
No audio here, output is 
```
ann@ann-XPS-8100:~$ rtmpdump --live --verbose \
>          --swfVfy "http://www.abc.net.au/res/players/aacPlayer.swf" \
>          --pageUrl "http://www.abc.net.au/classic/player/" \
>          -r "rtmp://cp112896.live.edgefcs.net/live/classic_fm@40676" | mplayer -
RTMPDump v2.4
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
DEBUG: Parsing...
DEBUG: Parsed protocol: 0
DEBUG: Parsed host    : cp112896.live.edgefcs.net
DEBUG: Parsed app     : live
WARNING: You haven't specified an output file (-o filename), using stdout
DEBUG: Protocol : RTMP
DEBUG: Hostname : cp112896.live.edgefcs.net
DEBUG: Port     : 1935
DEBUG: Playpath : classic_fm@40676
DEBUG: tcUrl    : rtmp://cp112896.live.edgefcs.net:1935/live
DEBUG: swfUrl   : http://www.abc.net.au/res/players/aacPlayer.swf
DEBUG: pageUrl  : http://www.abc.net.au/classic/player/
DEBUG: app      : live
DEBUG: live     : yes
DEBUG: timeout  : 30 sec
DEBUG: SWFSHA256:
DEBUG: 0d 2a 36 1f 5b 09 fc 50 1d 6b 0d 5a a9 ac 53 bd
DEBUG: 11 0d 42 f0 37 ff 7a 6a c4 5b fa 0a 78 fb b4 27
DEBUG: SWFSize  : 251191
DEBUG: Setting buffer time to: 36000000ms
Connecting ...
MPlayer svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing -.
Reading from stdin...
DEBUG: RTMP_Connect1, ... connected, handshaking
DEBUG: HandShake: Client type: 03
DEBUG: HandShake: Client digest offset: 430
DEBUG: HandShake: Initial client digest: 
DEBUG: 22 d8 2e a3 ca 71 43 27 39 2d d3 b8 84 16 a1 9a
DEBUG: 6c dc d6 eb ba 97 0d b0 f0 f4 51 d8 a1 f6 8a 6f
DEBUG: HandShake: Type Answer   : 03
DEBUG: HandShake: Server Uptime : 1851425314
DEBUG: HandShake: FMS Version   : 4.5.2.1
DEBUG: HandShake: Calculated digest key from secure key and server digest: 
DEBUG: 16 8b 9f 47 13 84 13 c4 7e 59 73 54 c0 37 cc 8b
DEBUG: 36 08 d5 27 aa 3c 51 5d 55 6c 91 25 51 99 b1 59
DEBUG: HandShake: Client signature calculated:
DEBUG: a9 02 4c b3 ba 35 d3 3d b7 d8 5d 50 23 96 5c 21
DEBUG: 96 f1 76 f8 59 9e 1b 19 02 ca ef 03 76 17 76 5e
DEBUG: HandShake: Server sent signature:
DEBUG: 5e 93 1b 06 74 ae 28 b3 be 81 f2 0b 7b e8 62 3c
DEBUG: a3 ca 34 1d 2d 3d c3 0a db 09 ea fd 90 31 68 55
DEBUG: HandShake: Digest key: 
DEBUG: 46 78 0e 24 78 27 04 9f ec 62 5f 79 b1 a6 f1 98
DEBUG: 2e bc 0e e1 63 c3 72 70 67 d9 62 69 12 73 46 38
DEBUG: HandShake: Signature calculated:
DEBUG: 5e 93 1b 06 74 ae 28 b3 be 81 f2 0b 7b e8 62 3c
DEBUG: a3 ca 34 1d 2d 3d c3 0a db 09 ea fd 90 31 68 55
DEBUG: HandShake: Genuine Adobe Flash Media Server
DEBUG: HandShake: Handshaking finished....
DEBUG: RTMP_Connect1, handshaked
DEBUG: Invoking connect
INFO: Connected...
DEBUG: HandleServerBW: server BW = 1250000
DEBUG: HandleClientBW: client BW = 1250000 2
DEBUG: HandleChangeChunkSize, received: chunk size change to 4096
DEBUG: RTMP_ClientPacket, received: invoke 240 bytes
DEBUG: (object begin)
DEBUG: (object begin)
DEBUG: Property: <Name:             fmsVer, STRING:     FMS/4,5,2,524>
DEBUG: Property: <Name:       capabilities, NUMBER:     127.00>
DEBUG: Property: <Name:               mode, NUMBER:     1.00>
DEBUG: (object end)
DEBUG: (object begin)
DEBUG: Property: <Name:              level, STRING:     status>
DEBUG: Property: <Name:               code, STRING:     NetConnection.Connect.Success>
DEBUG: Property: <Name:        description, STRING:     Connection succeeded.>
DEBUG: Property: <Name:     objectEncoding, NUMBER:     0.00>
DEBUG: Property: <Name:               data, OBJECT>
DEBUG: (object begin)
DEBUG: Property: <Name:            version, STRING:     4,5,2,524>
DEBUG: (object end)
DEBUG: (object end)
DEBUG: (object end)
DEBUG: HandleInvoke, server invoking <_result>
DEBUG: HandleInvoke, received result for method call <connect>
DEBUG: sending ctrl. type: 0x0003
DEBUG: Invoking createStream
DEBUG: FCSubscribe: classic_fm@40676
DEBUG: Invoking FCSubscribe
DEBUG: RTMP_ClientPacket, received: invoke 21 bytes
DEBUG: (object begin)
DEBUG: Property: NULL
DEBUG: (object end)
DEBUG: HandleInvoke, server invoking <onBWDone>
DEBUG: Invoking _checkbw
DEBUG: RTMP_ClientPacket, received: invoke 29 bytes
DEBUG: (object begin)
DEBUG: Property: NULL
DEBUG: (object end)
DEBUG: HandleInvoke, server invoking <_result>
DEBUG: HandleInvoke, received result for method call <createStream>
DEBUG: SendPlay, seekTime=0, stopTime=0, sending play: classic_fm@40676
DEBUG: Invoking play
DEBUG: sending ctrl. type: 0x0003
DEBUG: RTMP_ClientPacket, received: invoke 10275 bytes
DEBUG: (object begin)
DEBUG: Property: NULL
DEBUG: (object end)
DEBUG: HandleInvoke, server invoking <_onbwcheck>
DEBUG: Invoking _result
DEBUG: RTMP_ClientPacket, received: invoke 21 bytes
DEBUG: (object begin)
DEBUG: Property: NULL
DEBUG: Property: NULL
DEBUG: (object end)
DEBUG: HandleInvoke, server invoking <_result>
DEBUG: HandleInvoke, received result for method call <FCSubscribe>
DEBUG: HandleChangeChunkSize, received: chunk size change to 4096
DEBUG: HandleCtrl, received ctrl. type: 0, len: 6
DEBUG: HandleCtrl, Stream Begin 1
DEBUG: RTMP_ClientPacket, received: invoke 174 bytes
DEBUG: (object begin)
DEBUG: Property: NULL
DEBUG: (object begin)
DEBUG: Property: <Name:              level, STRING:     status>
DEBUG: Property: <Name:               code, STRING:     NetStream.Play.Reset>
DEBUG: Property: <Name:        description, STRING:     Playing and resetting classic_fm@40676.>
DEBUG: Property: <Name:            details, STRING:     classic_fm@40676>
DEBUG: Property: <Name:           clientid, STRING:     qAAcgbTA>
DEBUG: (object end)
DEBUG: (object end)
DEBUG: HandleInvoke, server invoking <onStatus>
DEBUG: HandleInvoke, onStatus: NetStream.Play.Reset
DEBUG: RTMP_ClientPacket, received: invoke 168 bytes
DEBUG: (object begin)
DEBUG: Property: NULL
DEBUG: (object begin)
DEBUG: Property: <Name:              level, STRING:     status>
DEBUG: Property: <Name:               code, STRING:     NetStream.Play.Start>
DEBUG: Property: <Name:        description, STRING:     Started playing classic_fm@40676.>
DEBUG: Property: <Name:            details, STRING:     classic_fm@40676>
DEBUG: Property: <Name:           clientid, STRING:     qAAcgbTA>
DEBUG: (object end)
DEBUG: (object end)
DEBUG: HandleInvoke, server invoking <onStatus>
DEBUG: HandleInvoke, onStatus: NetStream.Play.Start
Starting Live Stream
DEBUG: RTMP_ClientPacket, received: notify 24 bytes
DEBUG: (object begin)
DEBUG: (object end)
DEBUG: RTMP_ClientPacket, received: invoke 20515 bytes
DEBUG: (object begin)
DEBUG: Property: NULL
DEBUG: (object end)
DEBUG: HandleInvoke, server invoking <_onbwcheck>
DEBUG: Invoking _result
DEBUG: RTMP_ClientPacket, received: invoke 149 bytes
DEBUG: (object begin)
DEBUG: Property: NULL
DEBUG: (object begin)
DEBUG: Property: <Name:              level, STRING:     status>
DEBUG: Property: <Name:               code, STRING:     NetStream.Play.PublishNotify>
DEBUG: Property: <Name:        description, STRING:     classic_fm@40676 is now published.>
DEBUG: Property: <Name:           clientid, STRING:     qAAcgbTA>
DEBUG: (object end)
DEBUG: (object end)
DEBUG: HandleInvoke, server invoking <onStatus>
DEBUG: HandleInvoke, onStatus: NetStream.Play.PublishNotify
DEBUG: RTMP_ClientPacket, received: invoke 111 bytes
DEBUG: (object begin)
DEBUG: Property: NULL
DEBUG: (object begin)
DEBUG: Property: <Name:               code, STRING:     NetStream.Play.Start>
DEBUG: Property: <Name:            context, STRING:     clnt3802>
DEBUG: Property: <Name:        description, STRING:     classic_fm@40676>
DEBUG: (object end)
DEBUG: (object end)
DEBUG: HandleInvoke, server invoking <onFCSubscribe>
DEBUG: RTMP_ClientPacket, received: notify 37 bytes
DEBUG: (object begin)
DEBUG: (object begin)
DEBUG: Property: <Name:          AudioOnly, NUMBER:     0.00>
DEBUG: (object end)
DEBUG: (object end)
INFO: Metadata:
INFO:   AudioOnly             0.00
DEBUG: ignoring too small audio packet: size: 0
DEBUG: RTMP_ReadPacket, m_nChannel: 5db3
DEBUG: RTMP_ReadPacket, m_nChannel: 3241
DEBUG: RTMP_ReadPacket, m_nChannel: 71de
DEBUG: RTMP_ReadPacket, m_nChannel: b090
DEBUG: RTMP_ClientPacket, unknown packet type received: 0x00
DEBUG: RTMP_ReadPacket, m_nChannel: c861
```

---

### Post by ron999 on 2013-06-01
> **andrew.46 said:**
> ```

rtmpdump --live --verbose \
         --swfVfy "http://www.abc.net.au/res/players/aacPlayer.swf" \
         --pageUrl "http://www.abc.net.au/classic/player/" \
         -r "rtmp://cp112896.live.edgefcs.net/live/classic_fm@40676" | mplayer -

```
Hi
Your command above seems to play OK/reliably for me (see verbose attachment).

Also a stripped-down version of the command:-
```
ron@ubuntu:~$ rtmpdump -v -r "rtmp://cp112896.live.edgefcs.net/live/classic_fm@40676" -o - | mplayer -
RTMPDump v2.4-git-df6c518
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
Starting Live Stream
MPlayer SVN-r36293-4.5.2 (C) 2000-2013 MPlayer Team

Playing -.
Reading from stdin...
INFO: Metadata:
INFO:   AudioOnly             0.00
2.297 kB / 0.23 seclibavformat version 55.8.102 (internal)
libavformat file format detected.
63.401 kB / 7.85 sec[flv @ 0xb75684e0]max_analyze_duration 5000000 reached at 5014000 microseconds
[lavf] stream 0: audio (aac), -aid 0
Clip info:
 AudioOnly: 0
Load subtitles in ./
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 55.12.102 (internal)
AUDIO: 44100 Hz, 2 ch, floatle, 0.0 kbit/0.00% (ratio: 0->352800)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [alsa] 44100Hz 2ch floatle (4 bytes per sample)
Video: no video
Starting playback...
```

And (off-topic) the wma stream plays too:-
```
mplayer mms://a148.l11289758147.c112897.a.lm.akamaistream.net/D/148/112897/v0001/reflector:58147
```

---

### Post by andrew.46 on 2013-06-01
> **oldos2er said:**
> No audio here [...]

Thanks for having a look for me :). For the bad connection times I experimented with adding:

```

--timeout 240

```

which seems to have helped. Not quite sure why your connection has not finalised but this is certainly what I saw last night as well...

---

### Post by andrew.46 on 2013-06-01
> **ron999 said:**
> Hi
Your command above seems to play OK/reliably for me (see verbose attachment).

Oddly enough this morning the rtmpdump command is working reliably as well, it must be some network vagary I guess, thanks for having a look.

> And (off-topic) the wma stream plays too:-
```
mplayer mms://a148.l11289758147.c112897.a.lm.akamaistream.net/D/148/112897/v0001/reflector:58147
```

As you are no doubt aware I have been updating [Slackware and "For The God Who Sings]("http://www.andrews-corner.org/ftgws.html"), due for broadcast again tonight my time :).

---


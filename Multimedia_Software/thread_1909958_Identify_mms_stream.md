---
title: "Identify mms stream"
date: 2012-01-16
forum: Multimedia Software
---

### Post by Bradburts on 2012-01-16
Hi,
 
I am struggling to identify the media stream from the Radio
mplayer [http://mediasrv.musicradio.com/2CR](http://mediasrv.musicradio.com/2CR)
 
If I wget then I have:
[Reference]
Ref1=http://mediasrv.musicradio.com/2CR?MSWMExt=.asf
Ref2=http://81.20.48.50:80/2CR?MSWMExt=.asf
 
How do I capture the result of the query so that I can grab the mms stream? 
 
 
Also  Mplayer in 11.10 seems unable to decode ASX. Keeps looping whilst trying to resolve.
mplayer -playlist "[http://bbc.co.uk/radio/listen/live/r1.asx](http://bbc.co.uk/radio/listen/live/r1.asx)"
used to work in 10.04 server.
I can manually find a usable mms: stream so I suppose that I could script this although help in how to identify which is the stream would be great!
 
Finally a more general help/resources on links & support on how to get common streams to work with mpd and/or how to reliably query the play status of MPlayer (or another player) e.g. using a network protocol. 
What I am trying to do is create an embedded interface to an internet radio. 
Mplayer seemed the favourite as (it used to anyway) it could handle most streams. 
Unfortunatly I have not found a reliable way to interrogate MPlayer or command line players. Capturing MPlayer output in 10.04 using Popen() and pipes works (for me). This is not reliable though, I found on 11.10 that PIPE capture of stdout may block, it depends on an internal buffering implementation and regardless of the PIPE buffer size you can get deadlocked.
So I am back to mpd which I struggle to get to work with various stations.
The formats I need are:
asx, ram, asf

---

### Post by andrew.46 on 2012-01-16
> **Bradburts said:**
> Also  Mplayer in 11.10 seems unable to decode ASX. Keeps looping whilst trying to resolve.
mplayer -playlist "[http://bbc.co.uk/radio/listen/live/r1.asx](http://bbc.co.uk/radio/listen/live/r1.asx)"
used to work in 10.04 server.

Perhaps you need to get a newer copy of MPlayer as this works on the most recent version:

```

andrew@skamandros~$**[COLOR="Red"] mplayer -playlist "http://bbc.co.uk/radio/listen/live/r1.asx"[/COLOR]**
Resolving bbc.co.uk for AF_INET6...

Couldn't resolve name for AF_INET6: bbc.co.uk
Resolving bbc.co.uk for AF_INET...
Connecting to server bbc.co.uk[212.58.241.131]: 80...
Resolving www.bbc.co.uk for AF_INET6...

Couldn't resolve name for AF_INET6: www.bbc.co.uk
Resolving www.bbc.co.uk for AF_INET...
Connecting to server www.bbc.co.uk[212.58.246.93]: 80...

STREAM_ASF, URL: http://bbc.co.uk/radio/listen/live/r1.asx
Resolving bbc.co.uk for AF_INET6...

Couldn't resolve name for AF_INET6: bbc.co.uk
Resolving bbc.co.uk for AF_INET...
Connecting to server bbc.co.uk[212.58.241.131]: 80...

Server returned 404:Not Found
Failed to parse header.
Failed, exiting.
Resolving bbc.co.uk for AF_INET6...

Couldn't resolve name for AF_INET6: bbc.co.uk
Resolving bbc.co.uk for AF_INET...
Connecting to server bbc.co.uk[212.58.241.131]: 80...
Resolving www.bbc.co.uk for AF_INET6...

Couldn't resolve name for AF_INET6: www.bbc.co.uk
Resolving www.bbc.co.uk for AF_INET...
Connecting to server www.bbc.co.uk[212.58.246.93]: 80...

Cache size set to 320 KBytes
MPlayer SVN-r34561-4.6.2 (C) 2000-2012 MPlayer Team

Playing mms://wmlive-nonacl.bbc.net.uk/wms/bbc_ami/radio1/radio1_bb_live_int_ep1_sl0?BBC-UID=c4df41748844c7f33c06885d71239221d9dcdbbfd02081d4e41fc9c77403fd35&amp;SSO2-UID=.
STREAM_ASF, URL: mms://wmlive-nonacl.bbc.net.uk/wms/bbc_ami/radio1/radio1_bb_live_int_ep1_sl0?BBC-UID=c4df41748844c7f33c06885d71239221d9dcdbbfd02081d4e41fc9c77403fd35&amp;SSO2-UID=
Resolving wmlive-nonacl.bbc.net.uk for AF_INET6...

Couldn't resolve name for AF_INET6: wmlive-nonacl.bbc.net.uk
Resolving wmlive-nonacl.bbc.net.uk for AF_INET...
Connecting to server wmlive-nonacl.bbc.net.uk[212.58.251.92]: 1755...

Connected
unknown object
unknown object
unknown object
file object, packet length = 2261 (2261)
unknown object
stream object, stream ID: 1
unknown object
data object
mmst packet_length = 2261
Cache size set to 320 KBytes
Cache fill: 16.11% (52782 bytes)   

ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 title: BBC Radio 1
 author: BBC Radio 1
 copyright: British Broadcasting Corporation Copyright 2012, all rights reserved.
 comments: BBCMEDR107:1:A
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 53.55.105 (internal)
AUDIO: 44100 Hz, 2 ch, s16le, 48.0 kbit/3.40% (ratio: 6003->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:451954.2 (125:32:34.1) of 0.0 (unknown)  0.4% 15%

```

There is a guide on these forums somewhere for building the most recent svn MPlayer.

---

### Post by mc4man on 2012-01-16
Sometimes myself have issues with mplayer or currently mplayer2 with streams that contain a lot of address's, this one showed 32 here. So many times just try to simplify thru a playlist file, usually .m3u

In this case - 
```
#EXTM3U
#EXTINF:0,BBC Radio 1
mms://wmlive-nonacl.bbc.net.uk/wms/bbc_ami/radio1/radio1_bb_live_int_ep1_sl0?BBC-UID=345ff15499ca449ef96ee009a1d073c7be966d9b703061c182a273b364b40515&amp;SSO2-UID=

```

---

### Post by Bradburts on 2012-01-19
I am on Version: 2:1.0~rc4.dfsg1+svn33713-1
I know that this worked on Ubuntu server 10.04.
 
I am happy to grab the mms: from the .asf and add to a playlist ***but*** how do I find the mms with something like:
 
[http://mediasrv.musicradio.com/2CR](http://mediasrv.musicradio.com/2CR)
 
 
which contains queries:
 
```
 
[Reference]
Ref1=http://mediasrv.musicradio.com/2CR?MSWMExt=.asf
Ref2=http://81.20.48.50:80/2CR?MSWMExt=.asf

```

---


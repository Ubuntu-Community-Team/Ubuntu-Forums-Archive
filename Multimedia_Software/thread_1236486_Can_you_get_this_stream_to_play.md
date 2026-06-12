---
title: "Can you get this stream to play?"
date: 2009-08-10
forum: Multimedia Software
---

### Post by Westerberg on 2009-08-10
[http://www.tfnn.com/radioplayer.php](http://www.tfnn.com/radioplayer.php)

I think it's supposed to be a Microsoft Media Server (mms) stream.  I have the Gstreamer mms plugin installed, but it won't play for me.  It just sits there.

It plays in Windows.

Any help appreciated.  Thanks.

---

### Post by memyself on 2009-08-10
Hy ...

this is the source: 
mms://82.165.161.232:8083/TFNN-Radio

i tryed with vlc, xmms and totem - didn't work :-(


maybe mplayer could do this: 
[http://www.ubuntu-forum.de/artikel/41754/kent-jemand-ein-programm-f%C3%BCr-mms-webradios.html]("http://www.ubuntu-forum.de/artikel/41754/kent-jemand-ein-programm-f%C3%BCr-mms-webradios.html")

check treat no 6 !

..... 

open terminal and paste : mplayer mms://82.165.161.232:8083/TFNN-Radio 

needs some time to start with the stream - just wait a little ...

that works fine 4 me ;-)

hope i could help u a little ...

---

### Post by Westerberg on 2009-08-10
That worked.  Thanks a lot.

---

### Post by andrew.46 on 2009-08-10
Hi memyself,

> **memyself said:**
> ```
mplayer mms://82.165.161.232:8083/TFNN-Radio 
```

You can insulate yourself a little from the vagaries of internet radio streaming by adding a few cache options to this line as well:

```

mplayer -cache 2048 -cache-min 80 mms://82.165.161.232:8083/TFNN-Radio 
```

This allows MPlayer to build up a 2meg buffer to play from and ensures that the buffer fills to 80% before initial playback: 

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -cache 2048 -cache-min 80 mms://82.165.161.232:8083/TFNN-Radio [/COLOR]**
MPlayer SVN-r29484-4.2.4 (C) 2000-2009 MPlayer Team

Playing mms://82.165.161.232:8083/TFNN-Radio.
STREAM_ASF, URL: mms://82.165.161.232:8083/TFNN-Radio
Resolving 82.165.161.232 for AF_INET6...
Couldn't resolve name for AF_INET6: 82.165.161.232
Connecting to server 82.165.161.232[82.165.161.232]: 8083...
Connected
read error:: Resource temporarily unavailable
pre-header read failed
Resolving 82.165.161.232 for AF_INET6...
Couldn't resolve name for AF_INET6: 82.165.161.232
Connecting to server 82.165.161.232[82.165.161.232]: 8083...
Resolving 82.165.161.232 for AF_INET6...
Couldn't resolve name for AF_INET6: 82.165.161.232
Connecting to server 82.165.161.232[82.165.161.232]: 8083...
[B][COLOR="Red"]Cache size set to 2048 KBytes
Cache fill: 79.69% (1671168 bytes)[/COLOR][/B]   
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 title: TFNN.com
 copyright: TFNN Corp.
 comments: Educating Investors
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 48.0 kbit/3.40% (ratio: 6003->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video

A:6069.4 ( 1:41:09.3) of 2133437440.0 (-24.-8)  0.3% 80% 

```


The stream does indeed take a fair while to get started :-).

Andrew

---

### Post by memyself on 2009-08-11
@andrew.46

thx good to know ;-)

---


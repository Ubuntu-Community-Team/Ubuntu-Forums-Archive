---
title: "mencoder: cannot save MOV stream to a local file."
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by aurelieng on 2008-03-13
Hi there,

The University of Lausanne is currently organizing several conferences about internet, in french, entitled "Internet, un ami qui vous veut du bien ?". Theses conferences are quite interesting, and are available as MOV streams on [http://www.unil.ch/courspublic/page29628.html](http://www.unil.ch/courspublic/page29628.html).

Unfortunately, I cannot figure out how to save the stream on my linux box (Kubuntu 7.10), and I can nnot even play it. I tried to do my best with mencoder, with 
```
mencoder -oac mp3lame -ovc copy -o cours_public_4.mov rtsp://unistream.unil.ch/unicom/cp_2008/cp_2008_4.mov
```
But it ends up with the following output, saving nothing:
```

MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: AMD-K6(tm) 3D processor (Family: 5, Model: 8, Stepping: 12)
CPUflags: Type: 5 MMX: 1 MMX2: 0 3DNow: 1 3DNow2: 0 SSE: 0 SSE2: 0
Compiled with runtime CPU detection.

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
Resolving unistream.unil.ch for AF_INET...
Connecting to server unistream.unil.ch[130.223.32.57]: 554...
rtsp_session: unsupported RTSP server. Server type is 'QTSS/5.5.3 (Build/489.0.4; Platform/MacOSX; Release/Update; )'.
STREAM_LIVE555, URL: rtsp://unistream.unil.ch/unicom/cp_2008/cp_2008_4.mov
success: format: 21  data: 0x0 - 0x0
Stream not seekable!
 file format detected.
Initiated "video/H264" RTP subsession on port 32796
Initiated "audio/MPEG4-GENERIC" RTP subsession on port 32798
demux_rtp: Failed to guess the video frame rate
VIDEO:  [H264]  0x0  0bpp  0.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:21  fourcc:0x34363248  size:0x0  fps: 0.00  ftime:=0.0000
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
videocodec: framecopy (0x0 0bpp fourcc=34363248)
MP3 audio selected.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:      nan kbit/s  (-2147483648 B/s)  size: 0 bytes  0.000 secs  0 frames

Audio stream:      nan kbit/s  (-2147483648 B/s)  size: 0 bytes  0.000 secs

```

Any idea ?

Thanks a lot :)

Aurélien.

---

### Post by eye208 on 2008-03-13
Use MPlayer with the -dumpstream option.

---

### Post by aurelieng on 2008-03-13
Thx, but not better :(
```

MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 2.13GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing rtsp://unistream.unil.ch/unicom/cp_2008/cp_2008_4.mov.
Resolving unistream.unil.ch for AF_INET6...
Couldn't resolve name for AF_INET6: unistream.unil.ch
Resolving unistream.unil.ch for AF_INET...
Connecting to server unistream.unil.ch[130.223.32.57]: 554...
rtsp_session: unsupported RTSP server. Server type is 'QTSS/5.5.3 (Build/489.0.4; Platform/MacOSX; Release/Update; )'.
STREAM_LIVE555, URL: rtsp://unistream.unil.ch/unicom/cp_2008/cp_2008_4.mov
Cannot dump this stream - no file descriptor available.

Exiting... (Fatal error)


```

Any other idea ?

---

### Post by eye208 on 2008-03-13
If you can't save the stream this way, you can't view it either. It seems there is a compatibility problem with the RTSP server.

---


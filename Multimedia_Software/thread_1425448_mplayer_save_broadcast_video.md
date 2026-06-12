---
title: "mplayer save broadcast video"
date: 2010-03-09
forum: Multimedia Software
---

### Post by cucuru on 2010-03-09
hello, I would like to save a broadcast video with mplayer but I want do it while they are seeing, I mean, I want see them in real time, but also recording them and see them when I want

I've actually got with audio files with:

```

mplayer http://whatever/audio -ao pcm:file=/home/user/audio.mp3

```It works perfectly, I listen to the audio file from the radio I connected and save the file.

But I can't with video, I tried:

```

mplayer http://whatever/video -vo x11 -ao pcm:file=/home/user/video.mp4

```Could you help me?

It saves the audio, but not the video

Thanks! Regards!

---

### Post by andrew.46 on 2010-03-09
Hi cucuru,

> **cucuru said:**
> I've actually got with audio files with:

```

mplayer http://whatever/audio -ao pcm:file=/home/user/audio.mp3

```

It works perfectly, I listen to the audio file from the radio I connected and save the file.


The only problem with this technique is that I suspect even though this file will be labelled audio.mp3 it will actually be a wav file...

> 
But I can't with video, I tried:

```

mplayer http://whatever/video -vo x11 -ao pcm:file=/home/user/video.mp4

```Could you help me?


You are after *-dumpstream -dumpfile <filename>* for these streams, the file suffix will really be dependent on the nature of the stream itself. Can you give a specific example? 

Andrew

---

### Post by cucuru on 2010-03-11
Hello! thanks for your help, I'm afraid I can't give you an specific example because I'm working in a private subnet with Darwin Streaming Server.

I'm trying the -dumpstream option, but, I think that the video is not played at the same time that it's recording.

Anyway, I have a problem with this:

```

rocio@rocio-desktop:~$ mplayer -dumpstream rtsp://localhost/example.sdp -dumpfile prueba.mp4
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing rtsp://localhost/example.sdp
Resolving localhost for AF_INET6...
Connecting to server localhost[0.0.0.0]: 554...
connect error: Connection refused
Resolving localhost for AF_INET...
Connecting to server localhost[127.0.0.1]: 554...
A single media stream only is supported atm.
rtsp_session: unsupported RTSP server. Server type is 'DSS/5.5.5 (Build/489.16; Platform/Linux; Release/Darwin; state/beta; )'.
STREAM_LIVE555, URL: rtsp://localhost/example.sdp
Cannot dump this stream - no file descriptor available.


```How can I solve the file descriptor problem???

Thanks! Regards

---

### Post by andrew.46 on 2010-03-11
Hi cucuru,

I am afraid that I am not sure how to diagnose this problem, but certainly this syntax will not allow you to listen and record at the same time... Does your copy of MPlayer use live555? You can test this by running:

```

andrew@skamandros~$**[COLOR="Red"] mplayer -demuxer help | grep 'live555'[/COLOR]**
   live555  21   LIVE555 RTP demuxer (requires LIVE555 Streaming Media library)

```

Andrew

---

### Post by cucuru on 2010-03-12
Yes it has:

```

user@server:~$ mplayer -demuxer help | grep 'live555'
   live555  21   LIVE555 RTP demuxer (requires LIVE555 Streaming Media library)

```

Do you know any way to reproduce and save at the same time as I can do with audio?

Thanks!

---


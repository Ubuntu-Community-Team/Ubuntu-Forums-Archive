---
title: "probs creating live screencast with ffmpeg and ffserver"
date: 2008-02-18
forum: Multimedia &amp; Video
---

### Post by alina.bolero on 2008-02-18
I'm trying to generate an MPEG-4 stream of my desktop for an upcoming live presentation using my Gutsy laptop.  I'm having trouble setting up ffmpeg and ffserver.  I recompiled with x11grab.

/etc/ffserver.conf
```

Port 8090
BindAddress 0.0.0.0
MaxClients 1000
MaxBandwidth 1000
NoDaemon

<Feed screencast.ffm>
File /tmp/screencast.ffm
FileMaxSize 10M
ACL allow 127.0.0.1
</Feed>


<Stream screencast.avi>
Feed screencast.ffm
Format avi
AudioBitRate 32
AudioChannels 1
AudioSampleRate 22050
VideoBitRate 64
VideoBufferSize 40
VideoFrameRate 3
VideoSize 1360x768
VideoGopSize 12
NoAudio
</Stream>


<Stream stat.html>
Format status
ACL allow localhost
ACL allow 192.168.0.0 192.168.255.255
</Stream>


<Redirect index.html>
URL http://www.ffmpeg.org/
</Redirect>

```


no apparent problems starting up ffserver
```

# ffserver
FFserver version SVN-r11934, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --prefix=/usr/local --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libgsm --enable-libdc1394 --disable-debug --enable-shared --enable-nonfree --enable-x11grab --enable-libmp3lame --enable-libx264 --enable-libxvid --enable-libfaac --enable-libfaad
  libavutil version: 49.6.0
  libavcodec version: 51.50.1
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Feb 14 2008 15:49:32, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

```


```

# ffmpeg \
     -f x11grab \
     -i :0.0 \
     -r 3 \
     -b 64 \
     -s 1360x768 \
     http://localhost:8090/screencast.ffm
FFmpeg version SVN-r11934, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --prefix=/usr/local --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libgsm --enable-libdc1394 --disable-debug --enable-shared --enable-nonfree --enable-x11grab --enable-libmp3lame --enable-libx264 --enable-libxvid --enable-libfaac --enable-libfaad
  libavutil version: 49.6.0
  libavcodec version: 51.50.1
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Feb 14 2008 15:49:32, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
[x11grab @ 0xb7ed07b4]device: :0.0 -> display: :0.0 x: 0 y: 0 width: 0 height: 0
[x11grab @ 0xb7ed07b4]AVParameters don't have video size and/or rate. Use -s and -r.
:0.0: I/O error occured
Usually that means that input file is truncated and/or corrupted.

```

Any suggestions would be welcome.

Thanks,
Alina

---


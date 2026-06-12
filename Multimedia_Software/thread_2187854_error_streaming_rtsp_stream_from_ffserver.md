---
title: "error streaming rtsp stream from ffserver"
date: 2013-11-14
forum: Multimedia Software
---

### Post by prkhr4u on 2013-11-14
I want to live stream from an IP camera and am using ffserver for this.
here is my ffserver.conf file:
```
Port 8090
BindAddress 0.0.0.0
MaxHTTPConnections 2000
MaxClients 1000
MaxBandwidth 1000
CustomLog -
#NoDaemon

<Feed feed1.ffm>
    File /tmp/feed1.ffm
    FileMaxSize 200K
    ACL allow 127.0.0.1
</Feed>

# if you want to use mpegts format instead of flv
# then change "live.flv" to "live.ts"
# and also change "Format flv" to "Format mpegts"
<Stream live.h264>
Format rtp
Feed feed1.ffm
VideoCodec libx264
VideoFrameRate 24
VideoBitRate 100
VideoSize 480x272
AVPresetVideo default
AVPresetVideo baseline
AVOptionVideo flags +global_header

AudioCodec libfaac
AudioBitRate 32
AudioChannels 2
AudioSampleRate 22050
AVOptionAudio flags +global_header
</Stream>

##################################################################
# Special streams
##################################################################
<Stream stat.html>
    Format status
    # Only allow local people to get the status
    ACL allow localhost
    ACL allow 192.168.0.0 192.168.255.255
</Stream>

# Redirect index.html to the appropriate site
<Redirect index.html>
    URL http://www.ffmpeg.org/
</Redirect>
##################################################################
```

when i start ffserver using :
```
ffserver -d -f /etc/ffserver.conf
```

I get the following output:
```
ffserver version 2.0 Copyright (c) 2000-2013 the FFmpeg developers
  built on Nov 13 2013 13:58:41 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --prefix=/home/hls/ffmpeg_build --extra-cflags=-I/home/hls/ffmpeg_build/include --extra-ldflags=-L/home/hls/ffmpeg_build/lib --bindir=/home/hls/bin --extra-libs=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
  libavutil      52. 52.100 / 52. 52.100
  libavcodec     55. 41.100 / 55. 41.100
  libavformat    55. 21.100 / 55. 21.100
  libavdevice    55.  5.100 / 55.  5.100
  libavfilter     3. 90.102 /  3. 90.102
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
File for preset 'default' not found
/etc/ffserver.conf:25: AVPreset error: default
File for preset 'baseline' not found
/etc/ffserver.conf:26: AVPreset error: baseline
/etc/ffserver.conf:29: Unknown AudioCodec: libfaac
Incorrect config file - exiting.
```

Don't know what is wrong .
Pl also tell how to connect my input source to ffserver.My Ipcamera address is: 169.254.75.39
and i am thinking of using something like:
```
ffmpeg -i rtsp://169.254.75.39/ -vcodec -f http://localhost:8090/feed1.ffm
```

---

### Post by FakeOutdoorsman on 2013-11-14
I've never used ffserver, but have you seen [Streaming media with ffserver](http://trac.ffmpeg.org/wiki/Streaming%20media%20with%20ffserver)?

---

### Post by prkhr4u on 2013-11-14
I am using this wiki only and most of the code is from there.

---

### Post by FakeOutdoorsman on 2013-11-15
> ```
/etc/ffserver.conf:29: Unknown AudioCodec: libfaac
```
I missed this earlier: you don't have libfaac support. Luckily you don't need it because libfdk_aac is better which you can use.

Change:
```
AudioCodec libfaac
```
To:
```
AudioCodec libfdk_aac
```

There is no "default" preset, as far as I know (again, I'm ignorant of ffserver), so you can change:
```
AVPresetVideo default
```
To:
```
AVPresetVideo medium
```
Or try omitting it altogether. I don't know what to do about baseline. Try omitting it. Looks like [ticket #1275](https://trac.ffmpeg.org/ticket/1275) is relevant here.

---

### Post by prkhr4u on 2013-11-15
I have ommitted both the presets and now i am able to run ffserver well.
I have used NoAudio in .conf file as i do not require the audio element

But when i use:
```
ffmpeg -i rtsp://169.254.75.39:554/live.sdp http://localhost:8090/feed1.ffm
```
to connect my input source,it returns me an error.The complete output is as follows:

```
ffmpeg version 2.0 Copyright (c) 2000-2013 the FFmpeg developers
  built on Nov 13 2013 13:58:41 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --prefix=/home/hls/ffmpeg_build --extra-cflags=-I/home/hls/ffmpeg_build/include --extra-ldflags=-L/home/hls/ffmpeg_build/lib --bindir=/home/hls/bin --extra-libs=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
  libavutil      52. 52.100 / 52. 52.100
  libavcodec     55. 41.100 / 55. 41.100
  libavformat    55. 21.100 / 55. 21.100
  libavdevice    55.  5.100 / 55.  5.100
  libavfilter     3. 90.102 /  3. 90.102
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
Guessed Channel Layout for  Input Stream #0.1 : mono
Input #0, rtsp, from 'rtsp://169.254.75.39:554/live.sdp':
  Metadata:
    title           : RTSP server
  Duration: N/A, start: 0.000000, bitrate: 64 kb/s
    Stream #0:0: Video: h264 (High), yuv420p, 1280x720, 29.97 fps, 25 tbr, 90k tbn, 59.94 tbc
    Stream #0:1: Audio: pcm_alaw, 8000 Hz, mono, s16, 64 kb/s
[http @ 0xae5bdc0] HTTP error 503 Server too busy
http://localhost:8090/feed1.ffm: Input/output error


```

My conf file is as follows:
```
Port 8090
BindAddress 0.0.0.0
MaxHTTPConnections 200
MaxClients 100
MaxBandwidth 10000
CustomLog -
#NoDaemon

<Feed feed1.ffm>
    File /tmp/feed1.ffm
    FileMaxSize 20000K
    ACL allow 127.0.0.1
</Feed>

# if you want to use mpegts format instead of flv
# then change "live.flv" to "live.ts"
# and also change "Format flv" to "Format mpegts"
<Stream live.h264>
Format rtp
Feed feed1.ffm
VideoCodec libx264
VideoFrameRate 30
VideoBitRate 64000
VideoSize 1280x720
#AVPresetVideo default
#AVPresetVideo baseline
AVOptionVideo flags +global_header

NoAudio
</Stream>

##################################################################
# Special streams
##################################################################
<Stream stat.html>
    Format status
    # Only allow local people to get the status
    ACL allow localhost
    ACL allow 192.168.0.0 192.168.255.255
</Stream>

# Redirect index.html to the appropriate site
<Redirect index.html>
    URL http://www.ffmpeg.org/
</Redirect>
##################################################################
```

---

### Post by FakeOutdoorsman on 2013-11-15
Maybe burek will offer some help at [http://ffmpeg.gusari.org/](http://ffmpeg.gusari.org/)

---

### Post by prkhr4u on 2013-11-15
Thanks for the link. will see what best is poosible.

---


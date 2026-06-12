---
title: "html5 not working with ffserver"
date: 2010-03-13
forum: Multimedia Software
---

### Post by bandito40 on 2010-03-13
Hi,

I am using ffserver to stream from a capture directly to a browser, FireFox and Chrome.  I have been trying to get the stream to played with html5 but it doesn't seam to work.  Html5 does work with youtube.com but only in Chrome.  

Here is my ffserver setup:

```
Port 8080
BindAddress 0.0.0.0
MaxClients 1000
MaxBandwidth 10000
# Comment the following, on production use
NoDaemon

<Feed feed1.ffm>
    File /tmp/feed1.ffm
    FileMaxSize 15000M
    Launch ffmpeg -r 7 -s 480x320 -f video4linux2 -i /dev/video0
</Feed>

# FLV output
<Stream test.flv>
    Feed feed1.ffm
    Format flv
    VideoCodec flv
    VideoFrameRate 7
    VideoBufferSize 80000
    VideoBitRate 128
    VideoQMin 1
    VideoQMax 1
    VideoSize 480x320
    PreRoll 0
    Noaudio
</Stream>

# SWF output
<Stream test.swf>
    Feed feed1.ffm
    Format swf
    VideoCodec flv
    VideoFrameRate 7
    VideoBitRate 128
    VideoQMin 5
    VideoQMin 5
    VideoSize 480x320
    PreRoll 0
    Noaudio
</Stream>

# ASF output
<Stream test.asf>
# the source feed
Feed feed1.ffm
# the output stream format - ASF
Format asf
VideoCodec msmpeg4
# this must match the ffmpeg -r argument
VideoFrameRate 7
# generally leave this is a large number
VideoBufferSize 80000
# another quality tweak
VideoBitRate 128
# quality ranges - 1-31 (1 = best, 31 = worst)
VideoQMin 1
VideoQMax 5
VideoSize 352x288
# this sets how many seconds in past to start
PreRoll 0
# wecams don't have audio
Noaudio
</Stream> 
```

and here is my html code:

```
<video src="http://192.168.1.4:8080/test.flv" controls="controls" autoplay>
your browser does not support the video tag
</video>
<video src="http://192.168.1.4:8080/test.asf" controls="controls" autoplay>
your browser does not support the video tag
</video>
<video src="http://192.168.1.4:8080/test.swf" controls="controls" autoplay>
your browser does not support the video tag
</video>
```


Any ideas?

---

### Post by cmckdub on 2010-03-14
What is shown in the browser when you browse to the local address?

---

### Post by bandito40 on 2010-03-15
I am actually doing this from two different computers.  192.168.1.4 is the ip address of the computer that is streaming.

---

### Post by bandito40 on 2010-03-15
I think I realized my mistake.  Seams that the HTML5 video element only works with h264/theora videocodec.  Have been googling how to get ffserver to work with either videocodec.  Anyone have any idea how this is done?

---

### Post by sparcdr on 2011-09-16
ffserver.conf:

```

<Feed feed.ffm>
File /tmp/feed.ffm
FileMaxSize 1024M
ACL allow 127.0.0.1
</Feed>

<Stream feed.ogg>
Feed feed.ffm
Format ogg
VideoFrameRate 24
VideoSize 576x432
VideoBitRate 512k
VideoBufferSize 1024
AudioSampleRate 44100
AudioChannels 2
AudioBitRate 64k
AudioCodec libvorbis
VideoCodec libtheora
VideoQMin 1
VideoQMax 31
VideoGopSize 12
Preroll 0
AVOptionVideo flags +global_header
AVOptionAudio flags +global_header
</Stream>

```

command:
```
ffmpeg -i file.ext http://localhost:port/feed.ffm
```

location (to contain in html5 video tag):
```
http://server:port/feed.ogg
```

---


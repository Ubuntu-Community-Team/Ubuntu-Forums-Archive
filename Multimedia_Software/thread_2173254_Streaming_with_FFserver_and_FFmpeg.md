---
title: "Streaming with FFserver and FFmpeg"
date: 2013-09-08
forum: Multimedia Software
---

### Post by marfin2 on 2013-09-08
Hi,

I am trying to use FFserver and FFmpeg to stream Webm video, where I add an logo where I stream my file to the stream (such as on television channels).

I use this ffserver.conf file :

```

Port 8090
BindAddress 0.0.0.0
MaxHTTPConnections 2000
MaxClients 1000
MaxBandwidth 100000
CustomLog -
NoDaemon

<Feed feed1.ffm>
    File /tmp/feed1.ffm
    FileMaxSize 1G
    ACL allow localhost
    ACL allow 127.0.0.1
    ACL allow 192.168.0.0 192.168.255.255
</Feed>

<Stream stream.webm>
    Feed feed1.ffm
        Format webm
    
    #Audio settings
    AudioCodec vorbis
    AudioBitRate 64

    #Video settings
    VideoCodec libvpx
    VideoSize 640x320
    VideoFrameRate 25
    AVOptionVideo flags +global_header
    AVOptionVideo cpu_used 0
    AVOptionVideo qmin 10
    AVOptionVideo qmax 42
    AVOptionVideo quality good
    AVOptionAudio flags +global_header
    PreRoll 15
    StartSendOnKey
    VideoBitRate 400
</Stream>

# Server status

<Stream stat.html>
    Format status
    ACL allow localhost
    ACL allow 192.168.0.0 192.168.255.255
</Stream>


# Redirect index.html to the appropriate site

<Redirect index.html>
    URL http://www.libav.org/
</Redirect>


```

I used a stream with name stream.webm. That's work only with Chromium (or Chrome), not with Firefox.
With Chromium, I can watch the video like a live stream : I can put the video in pause, but I can not move forward or backward.
With Firerox, I can just watch the first image of the video and the icon of loading.

I used this command to stream my webm video :
```

ffmpeg -i video.webm -threads 2 http://localhost:8090/feed1.ffm

```

And I can access stream from [http://localhost:8090/stream.webm](http://localhost:8090/stream.webm).

Do you know if I can make this stream work with Firefox ? And if I can do streaming like Youtube, with control over the video ?

I have also  a more "theoretical" question : what kind of streaming is used on Youtube or Dailymotion ? Real streaming, pseudo streaming, or other ? Because I don't understand the differences 
between these different techniques.

Thanks for your help.

---


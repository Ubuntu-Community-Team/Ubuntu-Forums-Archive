---
title: "FFMPEG to Remote FFSERVER"
date: 2013-10-14
forum: Multimedia Software
---

### Post by mofolo on 2013-10-14
Hi, 


First time poster here! ;) 


I'm trying to set up a live audio feed from my camera to a webserver.


I'm currently using a D-SRL to capture Video/Audio via Firewire then using dvgrab on Ubuntu running ffmpeg.


    My Machine (Example IP: 1.2.3.4) --------------------------------------> Web Server (Example IP:  5.6.7.8)


Here is the code that I am running from machine 1.2.3.4:


```
dvgrab - | ffmpeg -i - -vn -acodec copy -b:a 32k -ar 22050 -f ffm http://5.6.7.8:8090/feed1.ffm

```

When I run this command,  it just hangs without encoding:
```
rom1394_0 warning: read failed: 0x0000fffff0000414
error reading config rom directory for node 0
ffmpeg version 0.8.6-6:0.8.6-1ubuntu2, Copyright (c) 2000-2013 the Libav developers
  built on Mar 30 2013 22:20:06 with gcc 4.7.2
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Found AV/C device with GUID 0x0000850001d0089c
Waiting for DV...
Capture Started
[dv @ 0x1e9db80] Estimating duration from bitrate, this may be inaccurate
Input #0, dv, from 'pipe:':
  Duration: N/A, start: 0.000000, bitrate: 28800 kb/s
    Stream #0.0: Video: dvvideo, yuv420p, 720x576, 28800 kb/s, PAR 16:15 DAR 4:3, 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: pcm_s16le, 32000 Hz, 2 channels, s16, 1024 kb/s
    Stream #0.2: Audio: pcm_s16le, 32000 Hz, 2 channels, s16, 1024 kb/s

```
And when I do a Control+C, it returns
```
^C
"": buffer underrun near: timecode ??:??:??.?? date 2013.10.14 23:08:55
This error means that the frames could not be written fast enough.

```

The FFServer's status page does show an inbound connection, firewall is definitely not an issue.

```
2   |   feed1.ffm   |    1.2.3.4    |   HTTP/1.1    |  WAIT_FEED
```

It works perfectly if I run this
```
ffmpeg -i downloaded.ffm http://127.0.0.1:8090/feed1.ffm

```
Where downloaded.ffm is a pre-recorded file from my local machine.

What can I do in order for ffmpeg to stream the piped dvgrab correctly to my web-sever?

For reference, here is my ffserver config file
```


Port 8090
MaxHTTPConnections 2000

MaxClients 1000
MaxBandwidth 1000


<Feed feed1.ffm>
    File /root/feed1.ffm
    FileMaxSize 10M
</Feed>


<Stream live.webm>
Feed feed1.ffm
Format webm
NoVideo
AudioCodec vorbis
AudioChannels 1
AudioSampleRate 22050
AudioBitRate 32
Preroll 0
AVOptionAudio flags +global_header
</Stream>

<Stream live.ogg>
Feed feed1.ffm
Format ogg
NoVideo
AudioCodec vorbis
AudioChannels 1
AudioSampleRate 22050
AudioBitRate 32
Preroll 0
AVOptionAudio flags +global_header
</Stream>



<Stream status.html>
    Format status
</Stream>


# Redirect index.html to the appropriate site
<Redirect index.html>
    URL http://www.ffmpeg.org/
</Redirect>



```

Thank you.

---


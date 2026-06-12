---
title: "HOWTO video stream from webcam through internet with ffmpeg"
date: 2008-01-12
forum: Multimedia Production
---

### Post by nol1ght on 2008-01-12
Hello, this is my first how to so be talerand. And sorry for my english ).

This howto works perfect with my Logitech QuickCam Express webcam.

Well. We have installed and working webcam. And we want to share our video through the internet or local network.


1)First we have to install ffmpeg ([http://ffmpeg.mplayerhq.hu/](http://ffmpeg.mplayerhq.hu/))

```
sudo apt-get install ffmpeg
```

2)Back up ffserver config file.

```
sudo mv /etc/ffserver.conf /etc/ffserver.conf_backup
```

3)Begin new ffserver config file. (this config was taken from [http://www.webmasterworld.com/video/3514671.htm](http://www.webmasterworld.com/video/3514671.htm) and edited by me)

```
sudo gedit /etc/ffserver.conf
```

paste into file lines below.

```
Port 8090 
# bind to all IPs aliased or not 
BindAddress 0.0.0.0 
# max number of simultaneous clients 
MaxClients 1000 
# max bandwidth per-client (kb/s) 
MaxBandwidth 10000 
# Suppress that if you want to launch ffserver as a daemon. 
NoDaemon 

<Feed feed1.ffm> 
File /tmp/feed1.ffm 
FileMaxSize 5M 
</Feed> 

# FLV output - good for streaming 
<Stream test.flv> 
# the source feed 
Feed feed1.ffm 
# the output stream format - FLV = FLash Video 
Format flv 
VideoCodec flv 
# this must match the ffmpeg -r argument 
VideoFrameRate 15 
# generally leave this is a large number 
VideoBufferSize 80000 
# another quality tweak 
VideoBitRate 200 
# quality ranges - 1-31 (1 = best, 31 = worst) 
VideoQMin 1 
VideoQMax 5 
VideoSize 352x288 
# this sets how many seconds in past to start 
PreRoll 0 
# wecams don't have audio 
Noaudio 
</Stream> 

# ASF output - for windows media player 
<Stream test.asf> 
# the source feed 
Feed feed1.ffm 
# the output stream format - ASF 
Format asf 
VideoCodec msmpeg4 
# this must match the ffmpeg -r argument 
VideoFrameRate 15 
# generally leave this is a large number 
VideoBufferSize 80000 
# another quality tweak 
VideoBitRate 200 
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

4)Start ffserver. Open terminal.

```
ffserver

```

in ffserver config file you can delete line "NoDaemon" to run ffserver as daemon.

5)Start ffmpeg video stream.

```
ffmpeg -r 15 -s 352x288 -f video4linux -i /dev/video0 http://localhost:8090/feed1.ffm  
```   

If there is no any errors. its done )

Now you can watch the video.
Open your favorite player and open url [http://localhost:8090/test.flv](http://localhost:8090/test.flv) or [http://localhost:8090/test.asf](http://localhost:8090/test.asf).

If you whant to watch your stream from another computer with windows media player:
type mms://<ip adress of ffserver machine>:8090/test.asf in IE

Also you can encode video to swf, mpeg and other formats . Read ffmpeg documentation.

If your internet connection is slow, you have make VideoFrameRate lower(1-5). 

[B]For streaming to flash player (swf)
[/B]
add this lines to the end of ffserver.conf
```

<Stream test.swf>
Feed feed1.ffm
Format swf
VideoCodec flv
VideoFrameRate 2
VideoBufferSize 80000
VideoBitRate 100
VideoQMin 1
VideoQMax 5
VideoSize 352x288
PreRoll 0
Noaudio
</Stream> 

```

Now you have another stream to test.sfw file then create <any name>.html file
Add this lines to it

```
<EMBED src="http://<ip adress of ffserver machine>:8090/test.swf" width=640 height=480 type="application/x-shockwave-flash"></EMBED>
```

then open it in your browser, enjoy )

I hope this howto was usefull for you. Have fun.

---

### Post by eye208 on 2008-01-14
> **nol1ght said:**
> 2)Back up ffserver config file.
3)Begin new ffserver config file.
There's no need to modify the system ffserver config file. Just start ffserver with the -f option, followed by the name of your customized config file.

---

### Post by nol1ght on 2008-01-14
to type ffserver -f newconfig.conf is longer then ffserver )
but you are right...

---

### Post by eye208 on 2008-01-14
> **nol1ght said:**
> to type ffserver -f newconfig.conf is longer
Yes. :wink: But it does not require root privileges, and you can easily run multiple servers on different ports and from different user accounts this way.

---

### Post by theacoustician on 2008-01-15
Why would you want to do all this instead of using VLC?  Its interesting from a learning perspective, but I would think VLC would be easier.

---

### Post by nol1ght on 2008-01-15
I don't know why, but VLC doest want stream to network my web cam. So i found another solution and share with other ).

---

### Post by prauscher on 2008-04-01
Hi!

At first, thanks for your howto. Made me a big step forward.
But, when I follow your howto, ffmpeg returns a lot of "rc buffer underflow" ...
```
$ ffmpeg -r 15 -s 352x288 -f video4linux -i /dev/video0 http://localhost:8090/feed1.ffm
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, video4linux, from '/dev/video0':
  Duration: N/A, bitrate: 18247 kb/s
  Stream #0.0: Video: rawvideo, yuv420p, 352x288, 18247 kb/s, 15.00 fps(r)
Output #0, ffm, to 'http://localhost:8090/feed1.ffm':
  Stream #0.0: Video: flv, yuv420p, 352x288, q=1-5, 200 kb/s, 15.00 fps(c)
  Stream #0.1: Video: flv, yuv420p, 352x288, q=1-5, 100 kb/s,  2.00 fps(c)
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
[flv @ 0xb7ebca68]rc buffer underflow
[flv @ 0xb7ebca68]rc buffer underflow
[flv @ 0xb7ebca68]rc buffer underflow
[flv @ 0xb7ebca68]rc buffer underflow
[flv @ 0xb7ebca68]rc buffer underflow
[flv @ 0xb7ebca68]rc buffer underflow
[flv @ 0xb7ebca68]rc buffer underflow
frame=    6 q=35.7 Lq=35.7 size=      96kB time=0.4 bitrate=1966.1kbits/s    
video:79kB audio:0kB global headers:0kB muxing overhead 21.963747%
Received signal 2: terminating.

```

When I watch the stream using vlc, it looks ok, but these messages go on my nerves!

however ... the bigger problem is, that I want to stream over network, not simple to localhost. On the Server I use debian etch with ffmpeg installed, but ffmpeg on my ubuntu-client machine does not want to connect:
```
$ ffmpeg -r 15 -s 352x288 -f video4linux -i /dev/video0 http://10.10.4.20:8090/feed1.ffm
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, video4linux, from '/dev/video0':
  Duration: N/A, bitrate: 18247 kb/s
  Stream #0.0: Video: rawvideo, yuv420p, 352x288, 18247 kb/s, 15.00 fps(r)
Could not read stream parameters from 'http://10.10.4.20:8090/feed1.ffm'

```
before you start to ask, 10.10.4.20 is reachable from my ubuntu machine and the server there is running.

:confused:

prauscher

---

### Post by king vash on 2008-05-20
I've been playing around and i finally got ffmpeg to work with a swf and i can see it on vlc on that computer using network stream and 
[http://localhost:8090/test.swf](http://localhost:8090/test.swf)
but i can't get it to work on any remote computer, and i've forwarded port 8090 and it won't load on a computer in my network or at work

---


---
title: "ffmpeg : Server error: Connection failed: Application folder"
date: 2012-07-08
forum: Multimedia Software
---

### Post by popeyeg on 2012-07-08
I am newbee to Ubuntu and Online streaming of TV Channel. I am getting this weird error when I try to run live streams of TV channel. 

Note the link works fine in VLC player.  I gather that I am missing some configuration part.

I have upto date FFMPEG drivers.

When type "which ffmpeg" in terminal
it returns "[COLOR=YellowGreen]/usr/local/bin/ffmpeg[/COLOR]"

when i type "ffmpeg - i <link>" it gives me below error:
[COLOR=Orange][B]
 Server error: Connection failed: Application folder ([install-location]/applications/liveorigin Playpath=newsx1 swfUrl=http:) is missing.[/B][/COLOR]

 and note that  many of the links work fine. but for some long rtmp urls I run into above error.

I hope its known issue and easy fix ( I did google lot before approaching the forum)

appreciate your help

---

### Post by FakeOutdoorsman on 2012-07-09
Please show your actual ffmpeg command and the complete console output.

---

### Post by popeyeg on 2012-07-09
> **FakeOutdoorsman said:**
> Please show your actual ffmpeg command and the complete console output.

popeyeg@ubuntu:~$ ffmpeg -i "rtmp://cdn.m.yupptv.tv:1935/liveorigin Playpath=newsx1 swfUrl=http://cdn.freedocast.com/player-octo/yume/v5/infinite-hd-player-YUPPTV.SWF pageUrl=http://www.yupptv.com"
ffmpeg version N-34431-g039e9fe Copyright (c) 2000-2012 the FFmpeg developers
  built on Jul  4 2012 16:53:11 with gcc 4.6.3
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab
  libavutil      51. 64.100 / 51. 64.100
  libavcodec     54. 32.100 / 54. 32.100
  libavformat    54. 14.100 / 54. 14.100
  libavdevice    54.  0.100 / 54.  0.100
  libavfilter     3.  0.101 /  3.  0.101
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0. 15.100 /  0. 15.100
  libpostproc    52.  0.100 / 52.  0.100
[COLOR=Red][rtmp @ 0x30c16e0] Server error: Connection failed: Application folder ([install-location]/applications/liveorigin Playpath=newsx1 swfUrl=http : ) is missing.
rtmp://cdn.m.yupptv.tv:1935/liveorigin Playpath=newsx1 swfUrl=http://cdn.freedocast.com/player-octo/yume/v5/infinite-hd-player-YUPPTV.SWF pageUrl=http://www.yupptv.com: Operation not permitted
[/COLOR]

---

### Post by popeyeg on 2012-07-11
Anyone know the answers ?

Experts , Gurus ?

---

### Post by FakeOutdoorsman on 2012-07-11
This works for me:
```
ffmpeg -i "rtmp://cdn.m.yupptv.tv:1935/liveorigin Playpath=newsx1"
```

**Edit:** It worked for me because I am using *--enable-librtmp* in the ffmpeg configure. The package **librtmp-dev** is a dependency.

---

### Post by popeyeg on 2012-07-11
> **FakeOutdoorsman said:**
> This works for me:
```
ffmpeg -i "rtmp://cdn.m.yupptv.tv:1935/liveorigin Playpath=newsx1"
```**Edit:** It worked for me because I am using *--enable-librtmp* in the ffmpeg configure. The package **librtmp-dev** is a dependency.

**[COLOR=DarkGreen]oh Well I think I am missing something: How do I get libertmp-dev ?[/COLOR]**

@ubuntu:~$ ffmpeg -i "rtmp://76.10.221.71/live/_definst_ app=tv playpath=zeelivetvoxpro swfUrl=http://www.veemi.com/player/player-licensed.swf pageUrl=http://www.veemi.com/embed.php?v=zeelivetvoxpro&amp;vw=600&amp;vh=480&amp;domain=1tvlive.in swfVfy=true live=true timeout=15"
ffmpeg version N-34431-g039e9fe Copyright (c) 2000-2012 the FFmpeg developers
  built on Jul  4 2012 16:53:11 with gcc 4.6.3
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab
  libavutil      51. 64.100 / 51. 64.100
  libavcodec     54. 32.100 / 54. 32.100
  libavformat    54. 14.100 / 54. 14.100
  libavdevice    54.  0.100 / 54.  0.100
  libavfilter     3.  0.101 /  3.  0.101
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0. 15.100 /  0. 15.100
  libpostproc    52.  0.100 / 52.  0.100
[rtmp @ 0x1e956e0] [COLOR=DarkRed]**Server error: Connection failed: Application rejected connection.**[/COLOR]
rtmp://76.10.221.71/live/_definst_ app=tv playpath=zeelivetvoxpro swfUrl=http://www.veemi.com/player/player-licensed.swf pageUrl=http://www.veemi.com/embed.php?v=zeelivetvoxpro&amp;vw=600&amp;vh=480&amp;domain=1tvlive.in swfVfy=true live=true timeout=15: Operation not permitted

---

### Post by ron999 on 2012-07-11
Good work **Fake_O_man** :guitar:

**--enable-librtmp** does the job.


Commands like this:-
```
ffmpeg -i "rtmp://cdn.m.yupptv.tv:1935/liveorigin Playpath=newsx1" -c copy foo.mkv
```
and this:-
```
ffplay "rtmp://cdn.m.yupptv.tv:1935/liveorigin Playpath=newsx1"
```
and this:-
```
ffmpeg -i "rtmp://cdn.m.yupptv.tv:1935/liveorigin Playpath=newsx1" -c copy -f flv - | vlc -
```

---

### Post by ron999 on 2012-07-11
> **popeyeg said:**
> **[COLOR=DarkGreen] How do I get libertmp-dev ?[/COLOR]**

@ popeyeg
```
sudo apt-get install librtmp-dev
```

---

### Post by popeyeg on 2012-07-12
> **ron999 said:**
> @ popeyeg
```
sudo apt-get install librtmp-dev
```

Awesome. Got it installed. Thank you ! you are da :KS

Only thing is " **--enable-librtmp** " is not working.

I typed above command in Terminal, it didn't work

I also tried ffmpeg -i " **--enable-librtmp**" , it couldn't find the directory.

perhaps I may be missing some syntax?

---

### Post by popeyeg on 2012-07-12
> **popeyeg said:**
> Awesome. Got it installed. Thank you ! you are da :KS

Only thing is " **--enable-librtmp** " is not working.

I typed above command in Terminal, it didn't work

I also tried ffmpeg -i " **--enable-librtmp**" , it couldn't find the directory.

perhaps I may be missing some syntax?


Never mind figure it out:
cd ffmpeg
./confgure " **--enable-librtmp**"

I will let you know my findings. Thanks again

---

### Post by popeyeg on 2012-07-12
> **ron999 said:**
> Good work **Fake_O_man** :guitar:

**--enable-librtmp** does the job.


Commands like this:-
```
ffmpeg -i "rtmp://cdn.m.yupptv.tv:1935/liveorigin Playpath=newsx1" -c copy foo.mkv
```and this:-
```
ffplay "rtmp://cdn.m.yupptv.tv:1935/liveorigin Playpath=newsx1"
```and this:-
```
ffmpeg -i "rtmp://cdn.m.yupptv.tv:1935/liveorigin Playpath=newsx1" -c copy -f flv - | vlc -
```


THANK YOU ! its working for me now. 

Can you help me understand how you come up with ffplay Code ? or can you point me in right direction ?

I try to play below stream in VLC it doesn't work. but when I use it in terminal
[COLOR=DarkOrange]ffplay "rtmpe://31.204.154.61/tv playpath=lifeokhq9_desistreams swfUrl=http://www.110cast.com/player/player-licensed.swf pageUrl=http://www.110cast.com/embed.php?u=lifeokhq9_desistreams live=true timeout=15"[/COLOR]

It shows below message
[COLOR=Olive]"Trying different position for server digest!"[/COLOR]
followed by several codes, and it simply start working.

What I want to learn is how to make above stream work in VLC Player ? My ultimate goal is to make it work in Serviio too.

in ANY CASE, I still WANT TO SAY  BIG THANK YOU :p

---


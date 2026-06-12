---
title: "no player will play this stream"
date: 2010-04-07
forum: Multimedia Software
---

### Post by rav0r on 2010-04-07
Every player I tried will crash giving "segmentation fault" with this radio [http://yp.shoutcast.com/sbin/tunein-station.pls?id=5440](http://yp.shoutcast.com/sbin/tunein-station.pls?id=5440)
It also doaes this on Fedora so it's a general Linux issue. It does not even play on my phone, only on Winamp on Windows in VirtualBox. In Wine, Winamp won't play it.
ffplay can do it but with a very low quality. It gives 
```

[aac @ 0xb10df0]SBR not implemented. Update your FFmpeg version to the newest one from SVN. If the problem still occurs, it means that your file has a feature which has not been implemented.

```

---

### Post by mc4man on 2010-04-07
try 
```
http://83.170.95.105:9444
```
or edit to 

```
[playlist]
numberofentries=4
File1=http://83.170.95.105:9444
Title1=(#1 - 62/1000) LOVE TDI Radio Beograd (Belgrade,Serbia,Beograd,Srbija): Untitled
Length1=-1
File2=http://77.92.92.130:9444
Title2=(#2 - 63/1000) LOVE TDI Radio Beograd (Belgrade,Serbia,Beograd,Srbija): Untitled
Length2=-1
File3=http://83.170.105.111:9444
Title3=(#3 - 66/1000) LOVE TDI Radio Beograd (Belgrade,Serbia,Beograd,Srbija): Untitled
Length3=-1
File3=http://85.222.163.162:9444
Title4=(#4 - 2/2) LOVE TDI Radio Beograd (Belgrade,Serbia,Beograd,Srbija): Untitled
Length4=-1
Version=2
```

all in all it's a rather crappy stream, the one that doesn't play may sound a bit better though there doesn't appear to be support for it
> Bitrate: 32kbit/s
Cache size set to 320 KBytes
STREAM: [null] [http://85.222.163.246:9444](http://85.222.163.246:9444)
aac @ 0xa1477e0][COLOR="Blue"]Parametric Stereo [/COLOR]

(though can playback some other acc+ files

---


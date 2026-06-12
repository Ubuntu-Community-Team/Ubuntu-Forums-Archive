---
title: "Screencast OpenGL &amp; conversion ffmpeg"
date: 2011-03-24
forum: Multimedia Software
---

### Post by Drimux on 2011-03-24
Hello everyone

In fact, I have problems with **ffmpeg **: I try to make a screencast, with microphone & speakers, of a game which runs in Java (so, RecordMyDesktop or XVidCap are not really suitable 'cause of "lags" or rather latency), and then to send this video on Youtube. I use ffmpeg, but the video is accelerated on this site or the sound is not sync on Avidemux if I want to make changes.

Here is the procedure I used : 

**First**, sound "loop" with
```
pacat -r --latency-msec=x | pacat -p --latency-msec=x
```(latency-msec to be sync)
[I also try "vlc alsa://hw:0,0" but there is latency]

**Second**, screencast :

```
ffmpeg -f alsa -ac 2 -i pulse -aq 4 -f x11grab -r 30 -s 1680x1050 -aspect 16:10 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 in.mkv
```This video mkv is really nice, with no problem! (But will be crappy if sent on Youtube)


**Third**, conversion mp4 :

```
ffmpeg -i in.mkv -s 1280x720 -aspect 16:9 -vcodec libx264 -vpre fast -crf 18 -threads 0 -acodec libfaac -ab 320k -y out.mp4
```or 2 passes

```
ffmpeg -i in.mkv -s 1280x720 -aspect 16:9 -r 30000/1001 -b 10000k -vcodec libx264 -pass 1 -vpre fast_firstpass -an out.mp4 && ffmpeg -y -i in.mkv -s 1280x720 -aspect 16:9 -r 30000/1001 -b 10000k -vcodec libx264 -pass 2 -vpre fast -acodec libfaac -ac 2 -ar 48000 -ab 320k out.mp4
```The mp4 is fine with VLC, no sound problem but if I send this on Youtube, the video is accelerated but not the sound, so the video is shorter... erf.
If I try Avidemux, the sound is not sync... and same thing of acceleration for Youtube.


So, can you help me for this, please ?

Thank you!
Regards. 

(Sorry for my bad english)

---

### Post by FakeOutdoorsman on 2011-03-24
This is a bug, and I thought YouTube would have addressed this long ago because I encountered it at least a year ago I think. Changing from High Profile to Main Profile for some reason will fix this issue (I can't think of a reason why though). You'll need to add *-vpre main*, as in:
```
ffmpeg -i in.mkv -s 1280x720 -aspect 16:9 -vcodec libx264 -vpre fast [color=red]-vpre main[/color] -crf 18 -threads 0 -acodec libfaac -ab 320k -y out.mp4
```

---


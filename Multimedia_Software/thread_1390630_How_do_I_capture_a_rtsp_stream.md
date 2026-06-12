---
title: "How do I capture a rtsp stream?"
date: 2010-01-25
forum: Multimedia Software
---

### Post by sr_guy on 2010-01-25
I want to use a command so I can run a script to capture this thaitv station for my wife, but mplayer gives me errors. 

Here is the stream:

```
rtsp://202.43.34.236/3
```

here is the command I used:
```
mplayer -noframedrop -dumpfile test.wmv -dumpstream rtsp://202.43.34.236/3
```


I don't care what software I use in linux as long as it is command line based so I can setup a cron job to record the stream. VLC handles that type of stream well, but the command line is a bit complex. If someone with vlc experience wants to throw in their two cents. It'd be appreciated.

VLC reports that the video stream is WMV3 and the audio is WMV2

Thanks

---

### Post by andrew.46 on 2010-01-26
Hi sr_guy,

> **sr_guy said:**
> I want to use a command so I can run a script to capture this thaitv station for my wife, but mplayer gives me errors.

My own attempts with MPlayer failed miserably so I have posted to MPlayer-users:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2010-January/078966.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2010-January/078966.html)

Hopefully a definitive answer will come from this...

Andrew

---

### Post by sr_guy on 2010-01-26
what about vlc commandline option?

---

### Post by andrew.46 on 2010-01-27
Hi sr_guy,

> **sr_guy said:**
> what about vlc commandline option?

Others may have to help with capturing this stream from the vlc commandline. I could play the *audio* from the graphical vlc but Live555 had too many troubles converting with cvlc. Sorry :(.

Andrew

---

### Post by no2498 on 2010-01-27
will webcam studio
do that

---

### Post by sr_guy on 2010-01-30
I think I've made some progress. I went to WWITV and downloaded the .asx file which contains the streaming URLs for the channel. Did some sniffing and came up with these URLs

[http://wwitv.com/tv_stream/b4507.asx](http://wwitv.com/tv_stream/b4507.asx) (.asx file link)

Stream URLs:

[http://vod.lib.tsu.ac.th/live1](http://vod.lib.tsu.ac.th/live1)
[http://www.maxnettv.tv/module_tvonlines/vdo_file.php?id=1879&type=tv&speed=](http://www.maxnettv.tv/module_tvonlines/vdo_file.php?id=1879&type=tv&speed=)
rtsp://202.43.34.236/3
mms://vod.lib.tsu.ac.th/live1?MSWMExt=.asf


Using this command:
mplayer -dumpstream -dumpfile thaichan`date +%Y%d%m%T`.mpg

with:
mms://vod.lib.tsu.ac.th/live1?MSWMExt=.asf

returned a .mpg file with video, but no audio. Any other assistance to fill in the gap would be great.

---

### Post by davidgutu on 2012-12-18
Use `rtmpdump`. It works for rtsp as well.

---

### Post by overdrank on 2012-12-18
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---


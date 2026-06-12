---
title: "Audacity &amp; Mixxx together"
date: 2006-09-18
forum: Multimedia &amp; Video
---

### Post by pak33m on 2006-09-18
I first ran Mixxx & then Audacity, but get the an error message:

Error Initializing Audio
There was an error initializing the audio i/o layer.
You will not be able to play or record audio.
Error: Host error

I've received this message before when just running Audacity.  I posted here: [http://www.ubuntuforums.org/showthread.php?t=248343](http://www.ubuntuforums.org/showthread.php?t=248343) & did what was suggested.  That time I did just that & had no problems with it again until now.

I want to be able to use Mixxx to start a mix & record with Audacity & the only way I can do this is to start Audacity before Mixxx.  I did this the other day & was successful if I just let the mix be recorded.  However, I cannot stop a recording in Audacity & listen, edit, etc. still with Mixxx running.

Anybody have any ideas what I'm doing wrong here or if it's even possible to run the two together?

---

### Post by wikinator on 2006-10-20
I've found that if you do:

> killall esd

it will allow you to use Audacity.  If you're looking to record your mixes, the only way I can forsee doing this is installing the beta 1.5 version of Mixxx, installing JACK, and using a JACK-aware applicaton like Ardour to record the audio.  I haven't started recording mixes yet because I have no monitor channel, so I can't give you the play-by-play.

P.S. If you want to be a DJ, you should check out Prokyon3, which helps you sort your music.  It is supposed to interface with Mixxx, but I haven't gotten them talking to one another yet.

---


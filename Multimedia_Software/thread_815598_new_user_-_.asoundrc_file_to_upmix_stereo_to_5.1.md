---
title: "new user - .asoundrc file to upmix stereo to 5.1"
date: 2008-06-01
forum: Multimedia Software
---

### Post by drfunkm on 2008-06-01
okay, i'm logged into my default account, and i'm trying to use text editor to create a /etc/asound.conf that will contain 
```
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}
```
and nothing else and save it as /etc/asound.conf . first problem is it is saying i don't have authorization to save that file. second problem is am I even going about doing this correctly? the post that I copied that code from mentions something also called PulseAudio, everything is working super spiffy, I want to get my music coming through all of my speakers, is there a media player that will handle the upmix for me? How should I go about doing this I'm a complete newbie. :guitar: rock&roll, -drfunkm

---


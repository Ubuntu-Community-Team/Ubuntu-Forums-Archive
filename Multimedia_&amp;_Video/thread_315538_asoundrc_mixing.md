---
title: "asoundrc mixing"
date: 2006-12-09
forum: Multimedia &amp; Video
---

### Post by finalbeta on 2006-12-09
I can use any one of these scripts:
```
#Set default to 5.1 surround
#pcm.!default {
#type plug
#slave.pcm "surround51"
#slave.channels 6
#route_policy duplicate
#}

pcm.!default {
         slave.pcm surround51
         slave.channels 6
         type route
         ttable.0.0 1
         ttable.1.1 1
         ttable.0.2 1
         ttable.1.3 1
         ttable.0.4 0.5
         ttable.1.4 0.5
         ttable.0.5 0.5
         ttable.1.5 0.5
}

```

to get 5.1 sound. But when I do, I need to use ESD for GStreamer apps or else I have ticking sound (xruns).
The problem is that when I want to use my TV card I need to exit all sound apps. 
Can someone help me to get this
```
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -Dplug:default
``` and the GStreamer apps which use ESD to play together?

---


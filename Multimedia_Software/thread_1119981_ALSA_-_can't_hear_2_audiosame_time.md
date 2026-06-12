---
title: "ALSA - can't hear 2 audio/same time"
date: 2009-04-08
forum: Multimedia Software
---

### Post by masque7 on 2009-04-08
Everything on my system uses ALSA. For example, say I wanted to watch a YouTube video and Rhythmbox is playing, I can't hear the audio, viceversa. Is it possible for 2 programs/instances to use ALSA?  I have all set to ALSA because I want 5.1: **.asoundrc** ```
pcm.!default { type plug slave.pcm &quot;surround51&quot; slave.channels 6 route_policy duplicate }  pcm.analog {     type plug     slave analog_slave; }  pcm_slave.analog_slave {         pcm surround51;         format S32_LE; }
```

---


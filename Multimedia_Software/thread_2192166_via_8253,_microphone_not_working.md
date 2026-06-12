---
title: "via 8253, microphone not working"
date: 2013-12-06
forum: Multimedia Software
---

### Post by miguel_miguel on 2013-12-06
Hi
i dont know what to do, can somebody help?

thanks

---

### Post by Yellow Pasque on 2013-12-06
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by miguel_miguel on 2013-12-06
The info..
 
[http://www.alsa-project.org/db/?f=bce69f2453eb63aff0e79185cd6c64c44ab410bc](http://www.alsa-project.org/db/?f=bce69f2453eb63aff0e79185cd6c64c44ab410bc)

---

### Post by Yellow Pasque on 2013-12-08
```
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 26 [84%] [4.50dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
```

Perhaps you simply need to enable something in alsamixer? Use spacebar to toggle switches and 'm' key to mute/unmute:
```
alsamixer
```

---


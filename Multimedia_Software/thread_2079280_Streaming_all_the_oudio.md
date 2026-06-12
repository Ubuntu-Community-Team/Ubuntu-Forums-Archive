---
title: "Streaming all the oudio"
date: 2012-11-01
forum: Multimedia Software
---

### Post by mafi127 on 2012-11-01
Is there some way to stream all the sounds what is playing in my laptop to my other computer what is connected to my mediacenter and my soundsystem  in whole my house can play all the sounds what my laptop is playing just like shoutcast for winamp in windows but for whole system? 
I dont mean like stream banshee sound but all my sound what is coming out from my soundcard.

---

### Post by mafi127 on 2012-11-02
some1 ?

---

### Post by mafi127 on 2012-11-05
Problem solved whit darkice. I had to compile the source whit this command to compile correct.

```
./configure --with-alsa-prefix=/usr/lib/i386-linux-gnu --with-samplerate-prefix=/usr/lib/i386-linux-gnu --with-jack-prefix=/usr/lib/i386-linux-gnu --with-lame-prefix=/usr/lib/i386-linux-gnu --with-pulseaudio-prefix=/usr/lib/i386-linux-gnu -with-vorbis-prefix=/usr/lib/i386-linux-gnu
```

---


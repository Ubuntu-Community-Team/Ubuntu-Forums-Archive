---
title: "only one app can play sound on Alsa"
date: 2010-08-24
forum: Multimedia Software
---

### Post by roy.nico on 2010-08-24
Hello, 

I have Ubuntu Lucid. If i dont' mistake, it should be possible to hear several applications playing sound simultaneously, with ALSA. But if 1 app is already playing, then starting a second one give always "device is busy".
Any idea to debug this ? 
thanks
nico

---

### Post by roy.nico on 2010-08-25
up?

---

### Post by Linuxforall on 2010-08-25
Pulse is exactly used for this purpose, it can handle multiple streams to multiple or single card one at a time, have you removed pulse btw?

---


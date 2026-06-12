---
title: "Terratec Phase 26 - alsamixer shows no capture control"
date: 2009-09-05
forum: Multimedia Software
---

### Post by cronholio on 2009-09-05
I have a Terratec Phase 26 audio interface that I use in Ubuntu Studio. Everything works well, I can use it to record from various sources via JACK. It's just that the input level is a bit low and I want to adjust it, however, alsamixer doesn't show any mixer controls for capturing. I tried choosing different input sources with the Terratec's selection button but none of them shows up in alsamixer.

Any ideas?

---

### Post by cronholio on 2009-09-06
Apparently the interface doesn't support input level control:

> The device doesn't have a hardware mixer for input level, so alsamixer won't show anything for controling capture levels. This is not a bug anywhere in ALSA! ALSA is just reflecting how the box is built.

From [here]("http://www.qbik.ch/usb/devices/showdev.php?id=2424").

---


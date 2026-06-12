---
title: "High CPU usage with ALSA"
date: 2010-06-30
forum: Multimedia Software
---

### Post by Aurum on 2010-06-30
Okay, so I'm finally posting to ask about this - why the hell does ALSA consume so much CPU time? OSS, even though it's emulated *through* ALSA, consumes a microscopic fraction of straight ALSA's CPU usage. For example, when I'm playing something through ALSA with XMMS2, I'm getting about 25-30% CPU usage, but with OSS output, only 2%, tops. The same applies to any other application in which I can choose the output method. And, I'm on 10.04.

---

### Post by Aurum on 2010-06-30
Solved. It was ALSA's stupid dmix, upsampling my audio to 48kHz. CPU usage is sane now.

---


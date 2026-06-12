---
title: "Silly Totem doesn't play video (but sound)"
date: 2010-09-12
forum: Multimedia Software
---

### Post by DrJuano on 2010-09-12
I've been looking a lot for a solution. The thing I did that fixed it was the next:

```
apt-get purge totem totem-xine totem-gstreamer

apt-get install totem-gstreamer
```

That's all. I hope this will be useful.

---

### Post by kerry_s on 2010-09-12
install "ubuntu-restricted-extras"
remove "gstreamer0.10-pulseaudio" it crashes pulseaudio

---


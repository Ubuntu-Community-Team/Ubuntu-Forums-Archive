---
title: "[SOLVED] OpenGL games are stretched across two screens"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by ad_267 on 2008-03-01
Hi,

I just tried updating my nvidia drivers to 169.12 from the nvidia website but then ubuntu wouldn't recognise my screens and I couldn't get things to work properly so I reverted back the the drivers from the ubuntu repository. Now when I play an OpenGL game in fullscreen it tries to stretch across both my displays. How do I get the second screen to be disabled and only one monitor when playing a game?

Thanks,
Adam

---

### Post by ad_267 on 2008-03-01
I've attached my xorg.conf file, hope that helps thanks.

---

### Post by ad_267 on 2008-03-01
I've got it working now

I changed this line in my xorg.conf file:
```
Option         "metamodes" "CRT-0: 1280x1024_60 +0+0, CRT-1: 1024x768_60 +1280+256; CRT-0: 1280x1024 +0+0, CRT-1: nvidia-auto-select +1280+0; CRT-0: 1280x960 +0+0, CRT-1: nvidia-auto-select +1280+0; CRT-0: 1152x864 +0+0, CRT-1: nvidia-auto-select +1152+0; CRT-0: 1024x768 +0+0, CRT-1: nvidia-auto-select +1024+0; CRT-0: 832x624 +0+0, CRT-1: nvidia-auto-select +832+0; CRT-0: 800x600 +0+0, CRT-1: nvidia-auto-select +800+0; CRT-0: 640x480 +0+0, CRT-1: nvidia-auto-select +640+0"
```

To this:
```
Option         "metamodes" "CRT-0: 1280x1024_60 +0+0, CRT-1: 1024x768_60 +1280+256; CRT-0: 1280x1024_60 +0+0, CRT-1: NULL; CRT-0: 1024x768_60 +0+0, CRT-1: NULL; CRT-0: 800x600_60 +0+0, CRT-1: NULL"
```

---


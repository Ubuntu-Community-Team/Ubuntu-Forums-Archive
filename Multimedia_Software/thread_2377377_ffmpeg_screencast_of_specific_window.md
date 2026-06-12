---
title: "ffmpeg screencast of specific window"
date: 2017-11-12
forum: Multimedia Software
---

### Post by micahpage on 2017-11-12
I usually use a command like this to get the whole screen. But how can you screencast a single window?
```
ffmpeg -f x11grab -r 50 -s 1920x1080 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -threads 5 captured.mkv
```

---

### Post by TheFu on 2017-11-12
I use Simple Screen Recorder and it let's me/you select the window to be captured.  I don't know if it will work at all with Wayland, so be certain to test it before any major recording is planned, if that is important to your requirements.

---

### Post by vasa1 on 2017-11-12
> **TheFu said:**
> ... I don't know if it will work at all with Wayland ...
I think it's going to be very helpful if people specify whether they're on Wayland or not.

---


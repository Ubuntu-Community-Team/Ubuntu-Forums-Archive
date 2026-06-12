---
title: "ffmpeg capturing screen video but not mic audio"
date: 2011-02-02
forum: Multimedia Software
---

### Post by king0 on 2011-02-02
I'm using the script below to run ffmpeg. While ffmpeg does capture the screen it does **_not_** capture the mic audio. I've checked that the mic works via "System Preferences." Anyone have any ideas on what the problems could be and suggestions on how to resolve this issue? Thanks.

```
ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -r 30 -s $(xwininfo -root |  grep 'geometry' | awk '{print $2;}') -i :0.0 -acodec pcm_s16le -vcodec  libx264 -vpre lossless_ultrafast -threads 0 -y screen-capture.mkv
```

---


---
title: "Mic Not Working."
date: 2010-12-03
forum: Multimedia Software
---

### Post by splosh5 on 2010-12-03
Hey im using the following script to screen record my desktop

```
ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -r 30 -s $(xwininfo -root | grep 'geometry' | awk '{print $2;}') -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 -y output.mkv
```

Under sound preferences i set my default sound devise to be my logitech quick chat pro. Now i dont really know how this script works so, what do i have to change to make it not be my built in mic on my laptop.

Many thanks
Splosh5.

---


---
title: "ffmpeg command for instagram"
date: 2016-10-09
forum: Multimedia Software
---

### Post by ktat on 2016-10-09
Hi,

I just spent the best part of a couple of hours putting together this command so that I could make my own movie to upload to insatgram.

I thought it might be worth sharing, so here it is with a little explanation:
```
ffmpeg -loop 1 -i image.jpg  -i music.ogg -c:v libx264 -strict -2 -c:a aac -ar 44100 -r 30 -pix_fmt yuv420p -shortest out.mov
```

Essentially this joins a music file (mono, ogg, 57secs) with a 600x600px jpg image to make an instagram clip.  Instagram clips are a maximum of 60sec long.  **libx264** is H.264 video codec and **acc** is the audio codec.  Audio must be at **44100** Hz and the frame rate **30fps**.  Don't know if the -**pix_fmt** option is necessary, but doesn't hurt. ** -shortest** makes the clip run the length of the audio.

If anyone has a simpler solution, I would be glad to hear it :)

---


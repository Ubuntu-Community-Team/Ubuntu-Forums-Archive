---
title: "Question on Recording on Ubuntu 10.04"
date: 2012-04-03
forum: Multimedia Software
---

### Post by FishBowl Ninja on 2012-04-03
Now first off I love 10.04, and that is why I use it even if it is a little older, anyways here is my question. Now I want to screen record my Minecraft videos and it works, and it captures the sound of my microphone. But sound from Minecraft itself is not recorded which I love would love to work. Here is what I am using (FFmpeg code in terminal)

ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -r 30 -s $(xwininfo -root | grep 'geometry' | awk '{print $2;}') -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 -y output.mkv

-So how can i get audio from Minecraft too record too? Thanks you very much in advance. Even post a link if you know one. Have a good day.

---


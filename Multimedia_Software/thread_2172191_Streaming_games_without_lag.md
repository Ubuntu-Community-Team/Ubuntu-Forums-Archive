---
title: "Streaming games without lag?"
date: 2013-09-03
forum: Multimedia Software
---

### Post by sci4me on 2013-09-03
Hey guys! So, I am currently using this: 
```

xterm -e avconv -f x11grab -s 1600x900 -r 50 -i :0.0 -f alsa -ac 2 -i pulse -vcodec libx264 -preset \"fast\" -s \"1280x720\" -acodec libmp3lame -ar 44100 -threads 2 -qscale 3 -b 2000000 -bufsize 512k -f flv \"rtmp://live.justin.tv/app/******************\"

```
to livestream to twitch. It works fine for everything except games. The only game I want to stream is minecraft. It works GREAT for anything, but when I play minecraft, its LAGGY on the stream.. like.. REALLY laggy. Can someone tell me what I should add/change to that to make games NOT lag?

---

### Post by zero2xiii on 2013-09-04
Hay,

Just a prod in the dark, but have you played with increasing and decreasing the buffer size, what happens (eg higher = more lag, lower = more lag, no change etc.)
Also the bitrate? I assume for the video "-b 2000000 -bufsize 512k".

Usually it is a buffer issue. Either memory, or network, but since you say other things work fine I would go with a memory buffer (remember minecraft is a JAVA app basically)

Cheers

---

### Post by dannyboy79 on 2013-09-05
it's because games take a lot of bandwidth, what sort of upload speed does your ISP provide you? Just streaming your desktop is nothing compared the amount of bandwidth required for streaming games.

---


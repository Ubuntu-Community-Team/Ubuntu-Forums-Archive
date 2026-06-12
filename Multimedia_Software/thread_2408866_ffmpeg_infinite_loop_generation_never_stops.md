---
title: "ffmpeg infinite loop generation never stops"
date: 2018-12-24
forum: Multimedia Software
---

### Post by cybervigilante on 2018-12-24
When I set ffmpeg to convert a gif to an infinite looping mp4 with the -1 flag, it just goes on forever, making hundreds of frames until I ctrl-C out of it. This makes no sense. An infinite loop should just need a loop marker at the end and be no bigger than a no-loop file. ie:

ffmpeg -stream_loop -1 -f gif -i  xmas.gif xmas.mp4

---

### Post by mc4man on 2018-12-26
I would guess you are infinitely  looping the input file so it will keep 'adding' that to the output file till you q (quit)
I don't believe it can do what you want as a video file.. (vs. a gif

---


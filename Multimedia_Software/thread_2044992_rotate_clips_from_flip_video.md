---
title: "rotate clips from flip video"
date: 2012-08-20
forum: Multimedia Software
---

### Post by coachkopie on 2012-08-20
friends,

i held the flip video on its side to shoot some video. how do i rotate the video so it appears correctly now (to save it that way and to post it in the correct vie)?

thank you very much. eager but relative newbie.

coach allan k

---

### Post by mocha on 2012-08-25
```
ffmpeg -i INPUT.AVI -acodec copy -vcodec mjpeg -qscale 2 -vf transpose=1 OUTPUT.AVI
```

or something appropriate to the Flip video, I don't know what format output it uses..

---


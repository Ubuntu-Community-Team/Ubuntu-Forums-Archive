---
title: "x11grab and fullscreen games"
date: 2012-06-01
forum: Multimedia Software
---

### Post by swickl on 2012-06-01
Hi, I'm new here, so be patient ;)
I try to record my desktop with ffmpeg -f x11grab which works pretty well:
```
ffmpeg -f x11grab -r 25 -s 1920x1080 -i :0.0 -vcodec huffyuv -sameq test.avi
```But there is a problem with games. If a game is in window mode or in fullscreen with the same resolution as the screen it works fine but if the game is in fullscreen in another resolution it only records the desktop with a black overlay where the fullscreen is (see the attachment).
Does it happen for everyone else, too?
Can someone explain the behavior and maybe even propose a possible fix?
thanks.

PS: I'm aware of glc but I just want it to work with x11grab.

---


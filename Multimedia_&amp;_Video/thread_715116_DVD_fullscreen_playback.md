---
title: "DVD fullscreen playback"
date: 2008-03-04
forum: Multimedia &amp; Video
---

### Post by lotsofish on 2008-03-04
I have Xubuntu installed on an older laptop. It's an IBM T22, 900mhz P3 with 384MB RAM. 

DVD playback with fullscreen is not very good. If it's not fullscreen, the playback is fine, but when I switch to fullscreen it gets choppy. I have tried it in MPlayer, Totem and VLC all with the same results. In XP, WMP played DVD's fullscreen without any issues.

Any suggestions?

---

### Post by Bruce M. on 2008-03-04
I have the same problem.  However I think it is due to having no video card, it's built into the motherboard. (see my SIG)

BUT ... if I change my screen resolution from 1280x1024 @ 60Hz to 800x600 @ 75Hz it goes full screen just fine.

Just have to be careful coming back to change the 75Hz back to 60Hz.  :)

Bruce

---

### Post by lotsofish on 2008-03-05
I couldn't change my display from 1024x768 to 800x600. I might try to straighten out my Xorg.conf file so I can get that working and it may help.

I did get MPlayer to play a movie reasonably well using a large cache.

```

mplayer -vo sdl -vm -framedrop -cache 204800 dvd://

```

My computer doesn't support xv output and sdl works a little better than X11. GL/GL2 was terrible. I had to have the -framedrop in or it would act weird and at times it still was a little choppy. I guess it's just slow hardware. If I can get my video config fixed so it will work at 800x600 I will give that a try and report back here if I get any better results.

---


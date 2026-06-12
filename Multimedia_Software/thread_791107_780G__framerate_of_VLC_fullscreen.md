---
title: "780G : framerate of VLC fullscreen"
date: 2008-05-11
forum: Multimedia Software
---

### Post by mboisson on 2008-05-11
Hello,
I have a GA-MA78GM-S2H motherboard with the 780G chipset and the ATI HD3200 graphic chips. I got the proprietary drivers (fglrx) installed properly with hardy.

I am trying to play XviD videos with resolution 624x352, frame rate 23.97 in fullscreen.

The problem is, if I keep the highest available screen resolution (1920x1080), the video is choppy. I looked at CPU usage with "top", and it was close to 100%.

I lowered the resolution and tried 1776x1000, it is not better.

Only when I get to down to1440x900 is the playback smooth. Since this is not 16:9 ratio, I set the resolution to 1280x720 and it runs smooth in fullscreen.

Now, this graphic chip is supposedly pretty good and can even decode HD video. I have a hard time believing that when I can't even play XviD low resolution in fullscreen.

So, is there a way to improve the performances ? Is there a way to know if all available hardware acceleration is used ? Or must I conclude that if I even want to run HD movies, I will need a dedicated graphic card ? (contrary to what I read in many tests).

---

### Post by mboisson on 2008-05-11
oh, an by the way, I read somewhere that --overlay or --no-overlay activates or deactivates hardware acceleration with VLC, well the result seems to be the same whatever option I use.

---


---
title: "Ubuntu 8.10, weird video problem"
date: 2009-05-26
forum: Multimedia Software
---

### Post by mancimailman on 2009-05-26
I get these weird kindof like tear marks when I watch videos, I cant really explain it but here is a screenshot.......

---

### Post by lukeiamyourfather on 2009-05-26
What hardware is in the system and does this happen on any other video files? I've seen this happen on slower systems that can't decode the video codec fast enough to playback, or the system was busy doing something that was using 99% of the resources. Not sure what codec and video card are being used but the video card can help decode some codecs too. Cheers!

---

### Post by Plasma_NZ on 2009-05-26
generally its not a hardware issue.....

i've got a 3ghz duo-core 64bit on jaunty with 8500 GT running on a 22" 2rms LCD - u wouldnt expect tearing, but if the monitor is configured incorrectly, thats exactly wat u get...

I've found having incorrect xorg.conf settings for one's card is generally the issue...

like having the refresh-rate wrong, or not running the monitor @ its recommended resolution...

You'll probley notice if u don't full-screen it and just run it in a window, u don't get that tearing which if u ask me is config issue...  solved mine by fixing my refresh settings manually...

hope this helps point u in a direction that could yield some positive results

---


---
title: "Plymouth Issue on Maverick"
date: 2010-10-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by cottfcfan on 2010-10-03
Just installed FGLRX on Maverick works great.
After rebooting though the resolution is huge and ugly.
 Same thing in Lucid was solved with the workaround here:
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)
Applied it to Maverick though and it doesn't work.
Any workaround anyone???

---

### Post by exploder on 2010-10-03
Startup Manager might take care of the problem, it works for NVidea but I have not tried it with ATI graphics.

---

### Post by cottfcfan on 2010-10-03
exploder.. startupmanager did nothing.
It appears that plymouth in maverick doesn't support my screen resolution of 1680x1050. strange as Lucid did.
Anyway followed the workaround in my 1st thread and set the resolution at 1280x1024.
 looks a bit crappy but better than before.
Does anyone else have a 1680x1050 screen that they've got working right with maverick?

---

### Post by exploder on 2010-10-03
> exploder.. startupmanager did nothing.
It appears that plymouth in maverick doesn't support my screen resolution of 1680x1050. strange as Lucid did.
Anyway followed the workaround in my 1st thread and set the resolution at 1280x1024.
looks a bit crappy but better than before.
Does anyone else have a 1680x1050 screen that they've got working right with maverick?

I have similar problems on my system with on-board nvidea graphics. My system with the nvidea gt 220 works fine and startup manager fixes plymouth to some degree but it isn't perfect. I tried fixing the plymouth issue by hand on the system with the on-board graphics but it just does not work right. I tried several different resolutions, my native resolution is 1920x1080.

---

### Post by TheDesertDragon on 2010-10-03
> exploder.. startupmanager did nothing.
It appears that plymouth in maverick doesn't support my screen resolution of 1680x1050. strange as Lucid did.
Anyway followed the workaround in my 1st thread and set the resolution at 1280x1024.
looks a bit crappy but better than before.
Does anyone else have a 1680x1050 screen that they've got working right with maverick?
Mine does support 1680x1050, but not my native resolution of 1920x1080. It reverts to 320x240.
I do not approve of the size of my terminal atm. xD

---

### Post by exploder on 2010-10-03
> Mine does support 1680x1050, but not my native resolution of 1920x1080. It reverts to 320x240.

That must be what I got! The text was HUGE and blurry as could be. If I used 1024x768 plymouth looked fine but my monitor displayed "out of range" on every boot or re-boot.

---

### Post by cottfcfan on 2010-10-03
So it seems that Plymouth supports everything but your native resolution:confused:
 Lets hope they fix it soon.
I can live with mine at 1280x1024 but its not great.

---

### Post by exploder on 2010-10-03
Plymouth is slowly maturing, it will get better with time.

---

### Post by drmartens on 2010-10-03
Yeah, it seems to be a bit improved since Lucid, but still far for succeeding. 

My system seems to set a bit higher resolution at the very beginning, but then suddenly scales it down and ubuntu logo moves to the bottom right corner with a little flickering, then the login screen appears in what seem to be 640x480 (same as lucid, blurry text), however my external monitor has 1920x1200...
Going from login screen to desktop seem to be much nicer and wallpaper is no longer mangled - but maybe it's just my fast ssd and I can't see it anymore (because now it's just like 1 or 2 seconds). There is no transition effect I've seen before, but maybe that's due to my new notebook with Intel GMA4500 instead of ATI, which I used to run before.

Well, it's not a great experience, especially when you start to dock/undock your notebook while using external monitor. Lots of flickering, resizing, switching off the screen which was supposed to be on etc. But things are getting better. It should be great in a few years ;)

---


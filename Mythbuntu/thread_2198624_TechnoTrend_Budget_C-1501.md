---
title: "TechnoTrend Budget C-1501"
date: 2014-01-09
forum: Mythbuntu
---

### Post by bdalsager on 2014-01-09
Hello.

5 years ago, i bought a 'TechnoTrend Budget C-1501' - DVB-C Tv-Tuner.

At the time, i never got it working with Mythbuntu, and i finally gave up.

I was wondering if anyone has any experience with this card, and could tell me how to get it working with Mythbuntu ?

I would like to say, i am no expert in linux/ubuntu, but i know the basics.

Thanks

Brian.

---

### Post by aelfric55 on 2014-01-10
A rare card these days. The only discussion pertaining to it is this ancient thread from 2008 here: [http://ubuntuforums.org/showthread.php?t=819903&p=5487658](http://ubuntuforums.org/showthread.php?t=819903&p=5487658)

The implication is that v4l kernel drivers still had to be patched in mid-2008, but came to include full C-1501 support shortly thereafter. A German review of the card I stumbled across states the card came to be supported as of kernel 2.6.31 So the card may simply work nowadays. Depending on the current status of clear QAM from your cable co., of course.

---

### Post by Zorbitz on 2014-01-15
I bought a C-1501 back in Nov 2009. At the time I built a pc hoping it would be able to run mythtv and record from my DVB-C provider. It worked fine, and I'm still using the same hardware running Mythbuntu 12.04.3 / MythTV 0.25.

I can't recall doing any tweaking at all. The card should be recognized by the kernel and show as an available input device in mythbackend config. The optional CI also works fine for me.

---


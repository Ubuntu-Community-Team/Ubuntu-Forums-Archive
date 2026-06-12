---
title: "TV-out with Radeon Xpress 200M"
date: 2008-07-27
forum: Multimedia Software
---

### Post by djmoore85 on 2008-07-27
Hey all, I need some help here. How do I go about doing a tv-out setup, with the TV on the left, and cloned but with the correct TV res? Right now I can get it, but it changes my laptops resolution as well when all I want to do is change my TV's so the picture is correct. It is running through the S-video out, and I want to be able to start piping movies through it, and this is my last issue. Thanks in advance

---

### Post by djmoore85 on 2008-07-29
Alright, hate to bump but need some help here. I am trying to get tv-out working using the catalyst control center. Do I need to be editing my xorg.conf and then make the edited .conf load instead of my current .conf? And if so what do I need to edit my xorg.conf or change it to to allow independent resolutions i.e. my laptop monitor at 1280x768 and my tv at 1024x768?

---

### Post by zwaardmeester on 2008-07-30
I ran into the same problem as you, apparently the CCC does not offer this option. As somebody pointed out to me: don't mess with the xorg.conf, that is not controlling your tv-out. What version of driver do you use? The repository one , or the newest 8.7? 

The config tool 'aticonfig' can set resolutions, but i find this very unclear and buggy. 

I guess we have to wait some more months before Ati provides proper drivers.

---

### Post by charding on 2008-09-14
Try this thread. It worked for me:

[http://ubuntuforums.org/showthread.php?t=467304](http://ubuntuforums.org/showthread.php?t=467304)

I edited my xorg.conf file. I replaced my Driver "ati" with "flgrx" and added 

Option "EnableMonitor" "tv"

to the same Device block.

---


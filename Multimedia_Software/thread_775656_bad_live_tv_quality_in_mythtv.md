---
title: "bad live tv quality in mythtv"
date: 2008-04-30
forum: Multimedia Software
---

### Post by harrydg on 2008-04-30
hey all,

since my upgrade from 7.10 to 8.04, my system seems to have huge problems with playing live tv (and recorded tv). i don't know why that happens. there is picture, but it's very ... well... not fluent , extremely annoying to watch!

i didn't have problems with 7.10 tough... my tv card: bttv hauppauge 848
my graphics card: nvidia 8600GTS
my screen/tv: sony KDL 40V3000

if any configs are needed, i'll provide them.

please... i just upgraded 2 of my machines, and on each of them, i have 2 problems which make it... well... unusable!

tnx!

---

### Post by spongeman66 on 2008-06-17
Sounds like I am having the same problem. 
I upgraded my dedicated MythTV box from 7.04->7.10->8.04
When I play back large video ~ HD content, I am lucky to get about 1 frame per second. Sometimes, the video freezes about 5 seconds into the show, and the audio starts to stutter.

I have some multiplexed channels in my area that are ~320X240, and they seem to play back OK.
With the 1FPS video playing, I logged-in to my MythTV box remotely. When doing a 'top', I see that X11 seems to be using ~100% of one of my cores.

I have an ATI X600 Video card that outputs S-Video, so I don't need 1080P output. I 'think' I have the proprietary drivers installed now, but they didn't seem to help.

Has anyone solved this problem yet?
Thanks!
Sponge

---

### Post by spongeman66 on 2008-06-17
I wonder if the bob2 de-interlacing is my problem:
[http://www.uluga.ubuntuforums.org/showthread.php?t=723345](http://www.uluga.ubuntuforums.org/showthread.php?t=723345)

I will try this tonight...
Sponge

---

### Post by spongeman66 on 2008-06-19
Indeed, the link above did point me in the right direction...
[http://www.uluga.ubuntuforums.org/showthread.php?t=723345](http://www.uluga.ubuntuforums.org/showthread.php?t=723345)

I have an ATI video card that doesn't support XvMC, so it is VERY processor intensive to scale 720P/1080i video down to my Standard Definition TV 800x600 format...
I had to pick an option that didn't allow scaling. (Yes, I get some strange squished aspect ratios, but that is how it looked before.) Now my CPU loading is back to normal, and I can view the shows that I had before. 
I guess I need to start looking for a 1/2 height Nvidia video card so that I can turn on XvMC...

Sponge

---


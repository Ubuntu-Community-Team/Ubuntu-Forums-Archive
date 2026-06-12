---
title: "jack-rack - EQs have little effect even with big db's"
date: 2011-07-09
forum: Multimedia Software
---

### Post by lorriman on 2011-07-09
Ubunti 10.04

I usually use aqualung to play my music but I also use spotify (on wine) to find new music. 

I use an LADSPA parametric equaliser to correct headphone resonances which makes a HUGE improvement (see here : [How to equalize your headphones]("http://www.head-fi.org/forum/thread/413900/how-to-equalize-your-headphones-a-tutorial") ). Aqualung does a sterling job of this.

For Spotify I'm piping the wine output in to jack-rack to use the same LADSPA equalisers (I've tried more than one, same problem). However weirdly they seem to have hardly any effect at the same settings. Infact even if I equalise to the maximum setting available I'm not getting enough 'attenuation' (if that's the right word) to make it worthwhile.

I did at one point notice that I had got the jack connections wrong, and was piping both the output of Wine and also jack-rack in to my headphones, instead of wine->jack-rack->system. So that can now be discounted.

Wine is set to only JACK as the sound 'driver'. Wine doesn't seem to work through jack if set to ALSA or OSS. Jack is using ALSA as the driver.

Any ideas?

---


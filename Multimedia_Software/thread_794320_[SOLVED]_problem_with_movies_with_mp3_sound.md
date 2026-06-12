---
title: "[SOLVED] problem with movies with mp3 sound"
date: 2008-05-14
forum: Multimedia Software
---

### Post by r00dy on 2008-05-14
Hi all
I have xubuntu 7.04 on my old P3 laptop.

I've recently problems with playing movies which have mp3/libmad as sound codec. The same is in mplayer and in vlc. 
The effect is that the sound is like shooting from uzi and there are also some artefacts on the buttom of video. When I shitch off sound this artefacts dissapear. 
Movies with other audio codecs are working ok.
I think that recently there was no change of mplayer/codecs in xubuntu 7.04.

I've tryied to reinstall libmad, mplayer and w32codecs but without any effect.

I have now installed
mplayer 2:1.0~rc1-0ubuntu9.3 and w32codecs 20071007-0medibuntu0.7.04.1

---

### Post by r00dy on 2008-05-14
I've solved this problem.
I've found similiar problem here: [https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/85751]("https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/85751") but in my case this was not a problem with soud codec but... video output.
The problem existed with any mp3 capable audio codec used together with xv video output. 
When I set -vo x11 it works well.

---


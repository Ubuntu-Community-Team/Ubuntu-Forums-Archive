---
title: "video editing issues in gutsy"
date: 2007-12-21
forum: Multimedia Production
---

### Post by AvengingAngel718 on 2007-12-21
I'm trying to start making my own compiz fusion videos to share on youtube. I've been using gtk-recordMyDesktop, which records fine, but i have a few problems with the video. First off, it saves as ogg-theora and i need to convert it to another format. It also wasn't recorded with sound, and i want to add an mp3 file to go along with it. Finally, I want to shrink the size of the video down a bit. The current dimensions are 1024 x 768 and I'd like to make it a bit smaller so it'll upload to youtube quicker.

Does anyone know what tools i can use to convert everything to the right format and what video editing program would work best?

---

### Post by eye208 on 2007-12-22
> **AvengingAngel718 said:**
> First off, it saves as ogg-theora and i need to convert it to another format.
mencoder yourvideo.ogg -nosound -ovc x264 -o yourvideo.avi

> It also wasn't recorded with sound, and i want to add an mp3 file to go along with it.
mencoder yourvideo.ogg [COLOR="Red"]-audiofile youraudio.mp3[/COLOR] -ovc x264 [COLOR="Red"]-oac copy[/COLOR] -o yourvideo.avi

> Finally, I want to shrink the size of the video down a bit. The current dimensions are 1024 x 768 and I'd like to make it a bit smaller so it'll upload to youtube quicker.
mencoder yourvideo.ogg -audiofile youraudio.mp3 [COLOR="Red"]-vf scale=320:240[/COLOR] -ovc x264 -oac copy -o yourvideo.avi

This final command line includes all the previous steps, i.e. you need to run MEncoder only once. YouTube videos are indeed only 320x240 pixels, so you can save a lot of upload time by scaling your clip down like this.

---

### Post by AvengingAngel718 on 2007-12-24
Thanks a lot! Worked like a charm. You can see the video here: [http://www.youtube.com/watch?v=P3JfbQLHKl0](http://www.youtube.com/watch?v=P3JfbQLHKl0)

---


---
title: "Recording ingame sounds in linux"
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by asipi on 2008-03-03
Hi,

I need to make some clanmovies of Enemy Territory and/or Urban Terror. Both are Q3 engine based games. To make videos from a recorded game demo is not problem, mencoder do the trick from the series of screenshots.

My problem is that I am not able to record the ingame sounds. Is it impossible? (I guess it isn't...)
Could anybody post some ideas or a howto?

---

### Post by aeiah on 2008-03-03
audacity will enable you to do it, although it might not be the most efficient solution. you can set it to 'record what you hear', which should capture all sounds coming out of your computer. you may want to make sure audacity isnt locking the sound out though, as this may stop ET from producing sounds. you'll be able to tell if this is the case though, obviously.

there are probably other 'record what you hear' programs knocking around. perhaps even the basic sound recorder in ubuntu will do this, but you can use audacity to edit the  sound afterwards to sync it with your video (or you may find it easier to do this in a video editing app)

---

### Post by ron999 on 2008-03-03
Hi
You can record whatever's coming through the sound channel using **arecord.**

It's a bit tricky to set it up, but once it's done all you do is type:-

**arecord -f cd output.wav**

Then it records everything to the file 'output.wav' which you can convert to mp3 or whatever later.
This is where I got the info from:-[http://jordilin.wordpress.com/2006/07/28/howto-recording-audio-from-the-command-line/]("http://jordilin.wordpress.com/2006/07/28/howto-recording-audio-from-the-command-line/")

---

### Post by asipi on 2008-03-03
thank you guys, I know audacity, but I never used to record sounds :) I'll try it.

I never used arecord, but I guess that will be the solution for me because I prefer to use one simple console task to do one simple thing instead of a huge gui app.

thanks again, I will refer here how they are  worked.

---


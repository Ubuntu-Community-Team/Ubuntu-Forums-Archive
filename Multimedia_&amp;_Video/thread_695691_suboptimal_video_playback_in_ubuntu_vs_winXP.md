---
title: "suboptimal video playback in ubuntu vs winXP"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by gwpritch on 2008-02-13
I have recently been backing up my DVD collection to .avi using a script called xvidenc which utilizes memcoder to encode with XviD and mp3. This script has given me much better results than some of the other apps such as acidrip, dvdrip etc. Problem is with playback. I have tried totem, vlc, mplayer and all give suboptimal results: choppy video and audio, frame skipping and pauses especially during fast action scenes. If I play back in winXP however, the playback is as smooth as silk. 
I have all codecs installed, and have a nvidia Gforce fx5500 card with 256M with the latest restricted drivers.
Are there some options I can play with in any of the players to help this situation? 
Any help would be appreciated. I hate having to switch back to Windows.

---

### Post by aashay on 2008-02-13
try playing around with settings in gstreamer-properties for video. The one with xv is supposed to be good, but i'm not too sure

---

### Post by gwpritch on 2008-02-13
Thanks for the reply. I tried fiddling with those settings...tried xv, X11, xshm etc. Some didn't work at all and the others didn't really improve things. I also tried turning off Compiz/fusion which helped a little with the pausing but didn't help the choppy video playback at all.

---

### Post by aashay on 2008-02-14
which player are you using? If you already havent done so, try totem, vlc and mplayer. Different players might give different performances. Does anything else (like 3d games, compiz cube etc) show the choppy behavior??

---

### Post by gwpritch on 2008-02-14
I have tried all of the above players with the same results.  Everything else is nice and smooth,  and as I say, playing the files with media player classic in XP works just fine, otherwise I'd be suspecting the video card or the encoding.
Unfortunately I don't have a dvd player on this box so I can't speak to playing dvd directly from disc using these players.

---


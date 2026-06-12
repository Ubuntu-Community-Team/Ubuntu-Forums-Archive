---
title: "screen recording"
date: 2009-05-12
forum: Multimedia Software
---

### Post by t0mmy9 on 2009-05-12
Hi, ive been trying to find some decent screen recording software for a while. I have ubuntu 9.04 but its installed on a pretty old laptop with old drivers. 

I tried gtk-recordmydesktop and Istanbul. These worked but made really bad video results, with terrible quality and i couldnt make out any of the text on the screen.

I thought it might be because of my graphics card, but then i found xvidcap fixed the libavcodec-unstripped-52 error and set it up to record. This seemed to work fine until i looked at the video. The quality is really good but the colors are mixed up. red seems to turn blue and blue turn red. with light blue also turning yellow. Im using the later version of ffmpeg along with it and i can send a screenshot if you want or any hardware info. They mention color problems on their site, but i cant find a solution to any problem.

I would really like to get this working, its got a great interface and can record straight to mpg which none of the others seem to. Thanks for any help.

---

### Post by Braedon on 2009-05-12
I too, love xvidcap, however, I can't get the audio to work.

---

### Post by t0mmy9 on 2009-05-12
have you read their FAQ?

[http://xvidcap.wiki.sourceforge.net/faq](http://xvidcap.wiki.sourceforge.net/faq)

also, you could use the built in ubuntu sound recorder for a mic or audacity set to i think its "line in" or "stereo mix" to record any sound coming out of your computer speakers, just run it at the same time you run xvidcap.

Ive found this for me: [http://sourceforge.net/forum/forum.php?thread_id=2550202&forum_id=278401](http://sourceforge.net/forum/forum.php?thread_id=2550202&forum_id=278401)   but it hasnt helped. ive tried mpg avi and flv outputs.

---

### Post by t0mmy9 on 2009-05-14
Ok, turns out this might not only be a problem with xvidcap. 

[http://forum.notebookreview.com/showthread.php?t=121926](http://forum.notebookreview.com/showthread.php?t=121926)

[http://ubuntuforums.org/showthread.php?t=873464](http://ubuntuforums.org/showthread.php?t=873464)

Apparently it is adjusting the hue of the video which is causing the problem. I found that recording the screen captured video again whilst playing it in mplayer corrects the problem, but this isnt really a good fix.

Are there any video editing programs (or players) that let you change the hue of a video? I also have a windows PC so any free programs for windows would also be acceptable.

---


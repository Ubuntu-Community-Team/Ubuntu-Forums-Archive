---
title: "Split DVD into single tracks"
date: 2008-02-18
forum: Multimedia Production
---

### Post by Sebastian Stein on 2008-02-18
Hi,


I thought this one must be easy, but I'm still not sure how to do it. I have a DVD containing 20 minutes of MPEG encoded video (with AC3 stereo sound) in 16:9 PAL (720x576) format. The DVD consists of several tracks or scenes or however it is called. So there is one big file (about 1,3 GB) containing those tracks.

I want to split the DVD in a way that I have a single file for each track containing the video as well as the sound. If possible, this splitting should be done without recompression by just reusing the existing bit stream.

I have the feeling that this must be possible somehow with some command line tool, but I have no idea where to start to look, because actually it is the first digital video I ever created...

Thanks for your pointers,


Sebastian

---

### Post by erginemr on 2008-02-18
I believe you can do the splitting of a *.vob file without recompression (but manually) via **avidemux.** It is in the repositories.

---

### Post by Creative2 on 2008-02-19
:) try wiith mencoder 

play with mplayer , vlc or something your big file  then when you have time you can use this 

mencoder INPUT -ovc copy -oac copy -ss  hh:mm:ss.ms  -endpos hh:mm:ss.ms  -o OUTPUT.mpeg

---


---
title: "TS files (transport stream mpegs) won't play in mplayer but do in Xp"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by konungursvia on 2007-03-20
It usually plays a few frames then says an error message like "too many frames in the buffer (382)" and freezes. Please help. Xp plays them, but I wanna get away from Bill.

---

### Post by konungursvia on 2007-03-20
Bump. I think linux should be able to handle these hi def movies.

---

### Post by Erlander on 2007-03-21
I've just tried playing some .ts files with MPlayer, Totem, Xine and Kaffiene.  All failed to play them.  mpeg files from the ts files play well when all that I did to get the mpeg was to take that stream out of the ts under Windows using VideoReDo.

Pity they don't play with our Linux software.  I might have to keep Windoze a bit longer.

Rob

Edit:  Interesting though that Kaffiene will play back HDTV files recorded by it in .m2t format.

---

### Post by superm1 on 2007-03-21
Whenever I've had troubles playing a transport stream - i've always ran it through an mpeg2 cleaner.  This has meant for me that there was digital corruption during the reception process.  

I do my ts recordings directly from mythtv, and when I need to fix them - i run them through the mythtv "default" mpeg2-mpeg2 transcoder.

---

### Post by majoridiot on 2007-03-21
i agree that it is likely corrupted streams.  i notice that some channels are especially flaky- i can
currently view only one of 6 available HD channels with mythtv due to this problem.  looking at
the log, there are tons packet errors, etc.

cleaning tham as superm1 suggests fixes this problem 99% of the time- but you have to record
first.

---

### Post by konungursvia on 2007-03-21
Thanks for the ideas. Does anyone have the name of a package I can install to clean them up? I have been receiving my HD files on DVD discs from my girlfriend's sister, and don't have any linux mpeg software cleaners.

---

### Post by majoridiot on 2007-03-21
you can use the default mythtv transcoder as superm1 suggested, or use avidemux to do it.  
i have cleaned up corupted HD-TS with avidemux by having it convert from an mpeg TS to an mpeg 
PS. 

you can grab avidemux via synaptic or automatix.

---

### Post by Jose Catre-Vandis on 2007-03-21
> **konungursvia said:**
> Thanks for the ideas. Does anyone have the name of a package I can install to clean them up? I have been receiving my HD files on DVD discs from my girlfriend's sister, and don't have any linux mpeg software cleaners.

Or try ProjectX, which will also help to make them seekable (if not already)

look here for a deb

[http://www.ubuntuforums.org/showpost.php?p=1594641&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1594641&postcount=2)

:guitar:

---

### Post by majoridiot on 2007-03-21
> **Jose Catre-Vandis said:**
> Or try ProjectX, which will also help to make them seekable (if not already)

look here for a deb

[http://www.ubuntuforums.org/showpost.php?p=1594641&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1594641&postcount=2)

:guitar:

thanks for that link... i'll check that out too!

---

### Post by konungursvia on 2007-03-22
AVIdemux works, at least it vastly improves the mpegs, but projectx doesnt even run on my dapper. Just for the record. Thanks for the tips.

---

### Post by superm1 on 2007-03-22
> **konungursvia said:**
> AVIdemux works, at least it vastly improves the mpegs, but projectx doesnt even run on my dapper. Just for the record. Thanks for the tips.
ProjectX requires a java env to be setup last I remember.  I had it running on dapper back in the day, but stopped bothering with it once the myth file cleaner was in good shape.

---

### Post by spottyrover on 2007-05-04
I do not seem to be finding the original qu

This is how i record dvb
1) use kaffeine as it is easy to use, has a record time function, and is wife freindly
2) set it to record mpeg ps files
3) I record normal tv in sd mode because i can then easily reduce the size using avidemux down to 10% original with no reduction in quality
4) if you record in hd mode its much harder to reduce the size for archiving the best i found so far is devede  30% which is still very large 

if i have a problem with a ps file corupted in kafeine I use vlc to recode it to a ps file

I hope this helps

good luck
dave

---

### Post by disturbedite on 2007-05-04
> **konungursvia said:**
> Bump. I think linux should be able to handle these hi def movies.
i know you've figured this out already, but it IS possible.  they play fine for me in any xine based player (i.e. kaffeine) or mplayer based player  (i.e. kmplayer).  (although xine based players seem to handle the audio better, so i wonder if the problem isn't that you have corrupted audio but that xine is better able to decode *possibly* corrupted/messed up streams).

---

### Post by buMPer on 2007-05-04
> **konungursvia said:**
> ................ linux should be able to handle these hi def movies.

have you tried VLC?  kick-*** media player that can handle any video/audio/streaming format.  i also use it for my home entertainment setup using Studio64 distro which is also debian based.

---

### Post by disturbedite on 2007-05-04
from what i know, on win & lin vlc is not very good at playing hd content.  i know it wasn't on windows when i used vlc.  now on linux, i can't say from personal experience how it would work for me, cuz i use kaffeine and have absolutely zero reason to use anything else.  (kaffeine=best video player for linux imho).

---


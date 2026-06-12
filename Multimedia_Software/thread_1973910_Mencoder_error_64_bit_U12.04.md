---
title: "Mencoder error 64 bit U12.04"
date: 2012-05-05
forum: Multimedia Software
---

### Post by thomlark on 2012-05-05
I have installed both the 32 bit and 64 bit U12.04 desktops and all is well except for mencoder on the 64 bit desktop I get an error :

[mpeg4 @ 0x7f114895a300]Error, Invalid timestamp=1, last=1

This happens on 64 bit only and works great on 32 bit.

The resulting output file will not start playing, but if I skip past the first few seconds, it will play.

I would like to keep using 64 bit but if I can't find a solution to this problem, I will have to go 32 bit.

Please help if you can.

---

### Post by thomlark on 2012-05-17
I still have not solved this problem.  Surely someone else had this problem or has an idea.

The latest version of LMDE 64 bit also is problem.

Thanks for any help.

I have done more testing using divxenc and the 32 bit test and the 64 bit created the same mencoder command line but the 32 bit ran and the 64 bit failed. This clearly points to a mencoder problem on 64bit. 
 
I would also like to explain why I need to use mencoder instead of some other program.  My wife has a hearing problem so when I compress my mpeg videos with closed captioning I lose the closed captioning, so I convert the closed captioning into subtitling on the screen using mencoder.

If anyone knows of another program besides mencoder to do this, I would like to know how (including example script).

Thanks for any help and except for this problem,  Ubuntu 12.04 is great.

---

### Post by thomlark on 2012-06-07
Some people believe the problem is with divxenc so I have done more testing using divxenc and the 32 bit test and the 64 bit created the same mencoder command line but the 32 bit ran and the 64 bit failed. This clearly points to a mencoder problem on 64bit not divxenc.

I would also like to explain why I need to use mencoder instead of some other program. My wife has a hearing problem so when I compress my mpeg videos with closed captioning I lose the closed captioning, so I convert the closed captioning into subtitling on the screen using mencoder.

If anyone knows of another program besides mencoder to do this, I would like to know how (including example script).

Thanks for any help and except for this problem, Ubuntu 12.04 is great.

---

### Post by thomlark on 2013-03-06
Well here I am again in 2013 and still no answer to my problem. I just can't believe that someone else hasn't encountered the same problem with 64 bit mencoder.

Please help !   :(

---

### Post by thomlark on 2013-03-28
Well I tried upgrading to 12.10 64 bit and the same problem exists.  I guess if no one will fix the problem, I will have to stick wiith 12.04 32 bit until 13.04 comes out.

---

### Post by SeijiSensei on 2013-03-28
Mencoder is pretty much dead as a project at this point.  The [mplayer2]("http://www.mplayer2.org/") fork simply dumped it entirely.  The code was always rather rickety from what I understand, and most people have moved to ffmpeg (avconv) instead.  [DeVeDe]("http://www.rastersoft.com/programas/devede.html") switched from using mencoder to ffmpeg as the backend late in 2011.

---

### Post by andrew.46 on 2013-03-28
Can you give an example of the commandline that you use which generates this problem?

---

### Post by Goldfinger88 on 2013-04-13
thomlark:  > **thomlark said:**
> Well here I am again in 2013 and still no answer to my problem. I just can't believe that someone else hasn't encountered the same problem with 64 bit mencoder.  Please help !   :(  just stumbled on this forum question. I too have the same problem as you describe. I'm surprised that 12.04 mencoder works for you.  My situation is different: 10.04 works for me, but not 11.04 and not 12.04. Now I'm trying 13.04 beta 2 and it is still the same problem as you describe. I too am surprised. Another poster said that it is the fault of mencoder (old code/ unmaintained?) but I use latest mencoder on slackware-current and it works.  As a side note a few other problems have not been fixed since 11.04: 1. when playing a movie with VLC,  the screensaver is not disabled 2. volume control is useless until the highest 90% is reached and then user has only a narrow band with which to adjust volume. (there is a workaround for this)  BTW did you ever bug report this problem? If yes what did they say?  cheers.

---

### Post by Goldfinger88 on 2013-04-13
I wanted to mention earlier that I too have found that mencoder works on 32bit 12.04 (don't know about 11.04) but I'm maintaining the PC's of 5 family members who use 64 bit10.04 installed and I do not want to switch them to 32 bit version, especially when I busted their eardrums with how much better Ubuntu/Linux is to windows.

---


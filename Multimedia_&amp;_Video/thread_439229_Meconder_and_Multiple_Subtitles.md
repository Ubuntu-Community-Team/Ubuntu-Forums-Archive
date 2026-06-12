---
title: "Meconder and Multiple Subtitles"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by marko_4454 on 2007-05-10
Hello, I am using acidrip to rip my DVD's into my hard drive as .avi. I am really happy with the output, I just wish it could extract more than one subtitle, since I speak both Spanish and English. Does anyone know what to put in the Misc. box in order to get more than one sub file? Or maybe just modifying the command below...

this is the output it gives to terminal in terms of meconder:

> 
mencoder dvd://1 -dvd-device /dev/dvd  -aid 128 **-sid 0 -vobsubout /media/Movies/Movies/GotRoot?/TITLE_OF_MOVIE** -info srcform="DVD ripped by acidrip.sf.net" -oac mp3lame -lameopts abr:br=128  -ovc lavc -lavcopts vcodec=mpeg4:vhq:v4mv:vqmin=2:vbitrate=809 -vf pp=de,crop=0:0:0:0,scale=480:-2    -o "/media/Movies/Movies/GotRoot?/TITLE_OF_MOVIE.avi"


I put bold on the part that refers to subtitle.

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-extractsub.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-extractsub.html)
I looked at this and couldnt get it, can someone tell me what I should add to that command to extract another sid or subtitle?

---

### Post by mojoman on 2007-08-30
The thread is a bit old but I too need a solution for this, as I'm in the exact same situation.

The problem is that the .sub and .idx have the same name as the .avi so acidrip couldn't very well create two sets of .sub and .idx, unless acidrip gave one set another name. 

I have found a work-around but it's a very bad one, and that is to rip it twice. First I rip it with english subs.  Then I put the sub-files in another folder, delete the .avi-file and repeat the process with spanish subs. This gives me one .avi and two sets of subs (.idx and .sub) and the avi-file works fine with both sets of subs. However, it takes a lot of unnecessary time and energy and is plainly a very bad work-around. There has to be a better way to do this. Any ideas, anyone?

---

### Post by marko_4454 on 2007-08-30
> **mojoman said:**
> The thread is a bit old but I too need a solution for this, as I'm in the exact same situation.

The problem is that the .sub and .idx have the same name as the .avi so acidrip couldn't very well create two sets of .sub and .idx, unless acidrip gave one set another name. 

I have found a work-around but it's a very bad one, and that is to rip it twice. First I rip it with english subs.  Then I put the sub-files in another folder, delete the .avi-file and repeat the process with spanish subs. This gives me one .avi and two sets of subs (.idx and .sub) and the avi-file works fine with both sets of subs. However, it takes a lot of unnecessary time and energy and is plainly a very bad work-around. There has to be a better way to do this. Any ideas, anyone?

Yes, thats exactly what I want to avoid. I am too lazy to do it twice. I sure hope, someone can do something about that. Or if some developer of acid rip is around, could you please address this?

---


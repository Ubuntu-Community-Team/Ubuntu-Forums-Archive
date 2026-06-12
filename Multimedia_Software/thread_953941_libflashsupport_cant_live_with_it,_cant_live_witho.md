---
title: "libflashsupport: cant live with it, cant live without it?"
date: 2008-10-20
forum: Multimedia Software
---

### Post by photonic on 2008-10-20
Hi forum,

I have a problem that I cannot have sound in both firefox (youtube videos etc) and in audacious at the same time. Following advice from someone over at mozillazine.org, I installed libflashsupport using synaptec. Some quick testing showed that I could now indeed have sound from both a youtube video and some mp3 playing in audacious. A little later, I went to thedailyshow.com for my daily fix. However, when the main page is loaded almost completely, it completely crashes firefox. This happens very consistently, while the site used to work without problems before. Then I uninstalled libflashsupport again -> dailyshow works again. WTF?

Any suggestions or pointers to other posts?

Thanks,
Bas
Ubuntu 8.04 on Toshiba laptop

---

### Post by estyles on 2008-10-20
I don't have this exact problem, but similar.  Flash 10 doesn't work for me at all.  Flash 9 with libflashsupport will work fine with ALSA, but then it kills support for multiple-application sound and Flash won't start at all if another application has a hold on the sound card.  Flash 9 without libflashsupport will work with pulseaudio, which theoretically works with sound from multiple applications, however it crashes whenever another app tries to make sound.

Or something like that - I still don't have my brain wrapped around it completely.  Suffice it to say that Flash and Pulseaudio are both pretty hosed under 8.04.  I really hope that these problems are fixed under 8.10.  In fact, I'd have to say that Flash and Pulseaudio are two of the big 3 fixes which would make 8.10 worthwhile to me, and if they are not included would make 8.10 a big waste of development time in my opinion (the 3rd is wireless support).  

There's a big thread full of fixes for Pulseaudio which brought me to the point I am currently at - where Flash will work, and multiple programs using audio will work, but if Flash is one of the multiple programs, it will crash, pretty much without fail.  I appreciate the work of that thread's author, and am willing to live with it, assuming that fixing those problems are part of development, but the state of Pulseaudio in Ubuntu 8.04 is something that I would call "unacceptable" in a final product, assuming that I had any right to call anything unacceptable in something as generally awesome and free as Ubuntu... ;)

So, long story short...  I have no help for you.  But libflashsupport is a kludge and shouldn't be necessary in the first place if Flash 10 fixes some of the problems of Flash 9.

---

### Post by cor2y on 2008-10-20
Ever since i followed the [Pulse Audio how to](http://ubuntuforums.org/showpost.php?p=4849192&postcount=1) by zman0900 in this section of the forums i haven't had the need for libflash.
And i used 8.04 and when i upgraded to 8.10 used the method again and no issues with the lack of libflash.
In both cases with libflash installed i could not run the webbrowser and media player, video or audio, at the sametime, with HowTo thats no longer a problem.

---

### Post by minky311 on 2008-10-20
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
Use this guide and set up pulseaudio correctly.
I followed this guide and everything works perfect using flash player 10.

---


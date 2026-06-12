---
title: "No sound in a particular DVD"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by drycellbattery on 2006-08-13
That particular DVD is called "Nine Commentaries of the Communist Party" I didn't want to include the title in the subject to avoid confusion on whether this is a political or technical issue. My issue is that when I put this dvd in I get sound in the title menu but when I play a chapter I get no sound. Since installing Ubuntu I've been able to play dvd's like that Enron documentary (was it called "The Smartest Guys in the Room"?), Doom, and Aeon Flux. Besides my taste in movies being called into question ;) I would like to hear sound on this 9 commentaries dvd. In the "sound" menu in Totem (using the xine backend bytheway) there is an option for languages: "Auto", "English" and "Language 2" which I'm assuming is Chinese. Neither option produces sound nor does fiddling with levels in alsamixer. My conclusion is that it's using a nonstandard audio codec, but I have no idea on how to find which codec it uses.

I have ffmpeg, dix0, w32codecs, libdvdcss2 (of course), what else... liba somthing. Generally anything that should decode ac3 or other codecs. I may be missing something.

Maybe the dvd copy I got from a chinese lady on the streets is broken.

So, does anyone else have this dvd and has this problem, or doesn't? Does anyone have problems with a dvd and no sound? Could this be a regional issue? I get video during the chapters, just no audio. The title menu plays both fine. Maybe I should just get the book and have to read like a commoner ;)

---

### Post by drycellbattery on 2006-08-15
ok I solved it. I noticed I wasn't getting sound in some .mov and .avi files as well so I found that installing libxine-extracodecs helped. Then I put in the dvd and behold there is magnificant sound!

---


---
title: "Cropping mp3 Losslessly"
date: 2008-02-01
forum: Multimedia Production
---

### Post by Aikon- on 2008-02-01
I know, you clicked on this to tell me "mp3 is lossy, newb!" I'm well aware; all the music I really care about that I am able to purchase myself is all FLAC, but in this case I've got an old mp3 that I don't really have anyway to get the source for.

So here's the scoop. I've got this mp3, and at the end it sounds like there's a clip of the start of the next song. (There's a gap between when the song ends and when this short 3-second clip of noise plays). Its horrendous, and every time I listen to it it throws me completely off my game.

So, I want to crp it out. Should be simple enough, right? Well, not quite.. I don't want to transcode or re-encode the file after the cropping, as this will result in a huge loss in quality. I want to just crop those frames from the end of the audio file without modifying the rest of it.

Is there a way to do this? I installed Audacity and gave it a try, but its only letting me output as WAV PCM :(

Thanks in advance,

-Aikon

p.s. If you can't figure out a way to do it with open-source software, but you know of another app that will do what I'm asking, I would accept that as well. Obviously I'd rather use OSS, but if worst comes to worse I'd rather get it done period :P

---

### Post by logos34 on 2008-02-01
Use mp3splt or mp3directcut (wine).  

Audacity will export output as mp3 but you need lame installed (>prefs)

---

### Post by Aikon- on 2008-02-01
Awesome, mp3splt worked like a charm. Thanks!

---


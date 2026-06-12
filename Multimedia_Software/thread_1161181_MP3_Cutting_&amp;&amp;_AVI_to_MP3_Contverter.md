---
title: "MP3 Cutting &amp;&amp; AVI to MP3 Contverter"
date: 2009-05-16
forum: Multimedia Software
---

### Post by vampiremind on 2009-05-16
Hi dudes
A am looking for pragram to cut my3 files
And another programa who can save the music from avi/wmv... to mp3 file :)

---

### Post by squaregoldfish on 2009-05-16
I assume by 'cutting' mp3 file, you mean editing them, so you're after a sound editor. Audacity (in the repositories) will perform this task admirably.

For extracting the sound from video files, I use mplayer (again in the repositories). It's a command line tool, so it may not be too easy to figure out, so to help you along here's the command I use:

```
mplayer -vc null -vo null -ao pcm:fast:file="out.wav" "in.wmv"
```

This will give you a standard Windows WAV file, which you can edit and convert in Audacity as above.

Hope this helps,
Steve.

---

### Post by FakeOutdoorsman on 2009-05-16
An excellent tool for cutting mp3 files is **mp3splt**.  No quality loss because it doesn't re-encode.

---

### Post by Teutorix on 2009-05-16
will mplayer do flv - audio?

---

### Post by squaregoldfish on 2009-05-16
> **Teutorix said:**
> will mplayer do flv - audio?

Indeed it will - just tested it.

Steve.

---

### Post by alexandari on 2009-05-16
well about the extracting you might try **AcetoneISO** It`s a very handy program it`s mainly for mounting stuff but :) check it out you might like it

---

### Post by vampiremind on 2009-05-17
Okey

1st 10X to all of you :)
2nd For "MP3 Cutting program" I was mean something like "MP3 Cutter Joiner"... btw I've do what I want:

Install MP3 Cutter Joiner with Wine
Cut a song (you can cut it and save it *.wav) for a some reason when you save it in MP3 file it doesent work (I save it as MP3 and the file was 1.7kb...)
When you save it as *.wav I use "lame -v2 somename.wav othername.mp3" that is how it work for me :) Now i enjoy at the end of the last minute of the song "Trashmen - Surfin' Bird" in my cell phone :) (I've watch family guy S7EP2 and become one of my favorite songs :D ) And I just loved the last min of that song :)
10x again to everyone :)

Wish You Luck

---


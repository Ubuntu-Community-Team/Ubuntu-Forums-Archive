---
title: "Convert FLV to WMV or maybe MPEG"
date: 2008-08-28
forum: Multimedia Software
---

### Post by Spades_Neil on 2008-08-28
Searched the forums for this but had trouble finding anything to assist, at least nothing straight-forward enough for me.

Anyone know any good URLs that can convert FLV (flash videos) into perhaps Windows Media Video (.wmv) files instead?

I'm looking to convert a 20 minute YouTube one, but the converter that came with a firefox addon just fails. It's too bloody confusing on how it works.

Plain and simple, I just wanna convert a 20 minute FLV to WMV so I can edit clips from it. I also want to keep the audio, not lose it.

---

### Post by unutbu on 2008-08-28
[http://zamzar.com](http://zamzar.com) will convert flv up to 100MB into wmv. It can convert other formats too.

[http://keepvid.com/](http://keepvid.com/) can download youtube videos as mp4

You might also try [http://vixy.net/](http://vixy.net/)

[http://ubuntuforums.org/showthread.php?t=705990](http://ubuntuforums.org/showthread.php?t=705990) has instructions on how to do the conversion yourself using ffmpeg.

---

### Post by cariboo on 2008-08-29
Another thing to try is **avidemux** it is available in the repositories and you can use Add/Remove Programs, Synaptic Package Manager or the command line to install it.

Jim

---

### Post by lovinglinux on 2008-08-29
[WinFF]("http://www.winff.org/") can do it and is very easy to use.

---

### Post by Spades_Neil on 2008-08-29
> **unutbu said:**
> [http://zamzar.com](http://zamzar.com) will convert flv up to 100MB into wmv. It can convert other formats too.

[http://keepvid.com/](http://keepvid.com/) can download youtube videos as mp4

You might also try [http://vixy.net/](http://vixy.net/)

[http://ubuntuforums.org/showthread.php?t=705990](http://ubuntuforums.org/showthread.php?t=705990) has instructions on how to do the conversion yourself using ffmpeg.

Zamzar is one I'm trying right now. Let's see how well that works.

Although the videos I wish to convert are often well beyond 100 megs. Zamzar will help part of the problem, but not all of it just yet.

I'll see what the others can do in a moment.

---

### Post by randywilharm on 2008-08-30
I use KINO --it's a DV editor--
It's in synaptic, easy to learn and it will
convert FLV to almost anything.

---

### Post by benerivo on 2008-08-30
I know this works in a console...```
ffmpeg -i /home/brian/Desktop/video.flv /home/brian/Desktop/video2.wmv
```but you may need some plugins installed, that aren't included in the default installation (you'll definitely need ffmpeg installed).

---

### Post by Vivaldi Gloria on 2008-08-30
Here is a flv2avi script.

---

### Post by unutbu on 2008-08-30
Thanks for the interesting script, Vivaldi Gloria.
I've always just used ffmpeg -i -sameq file.flv file.avi -- mainly because I never understood what all the options to mencoder meant.

Can you explain what the advantage of the script is over ffmpeg -i -sameq ?

---

### Post by Vivaldi Gloria on 2008-08-30
> **unutbu said:**
> Thanks for the interesting script, Vivaldi Gloria.
I've always just used ffmpeg -i -sameq file.flv file.avi -- mainly because I never understood what all the options to mencoder meant.

Can you explain what the advantage of the script is over ffmpeg -i -sameq ?

Sorry mate, not my script:

[http://www.linux.com/feature/56642](http://www.linux.com/feature/56642)

---


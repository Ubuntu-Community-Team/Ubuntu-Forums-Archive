---
title: "Issues converting a movie file from one format to another"
date: 2009-09-26
forum: Multimedia Software
---

### Post by riminicat on 2009-09-26
A friend of mine at work has been playing with Ubuntu since his vista install crashed, he said he was trying to convert a file and keeps getting this error.  I wondered if it was an mpeg and maybe he was having issues because of this, but he doesn't know a lot about computers and couldn't provide much help.

He plays with media a lot though, maybe a media specific ubuntu would help him more?

Do any of you know what this error means? 

```
Stream #1.0: Audio: mp2, 48000 Hz, 5.1, s16, 224 kb/s
Stream mapping:
Stream #0.0 -> #0.0
Stream #0.1 -> #1.0
encoding 6 channel(s) is not allowed in mp2
Error while opening codec for output stream #1.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```

---

### Post by dr_dred5 on 2009-09-26
I've been using Handbrake from [http://handbrake.fr/](http://handbrake.fr/)

It has an easy to use Gui, lets you choose what video and audio codec to use, supports subtitle, ripping and what I like is that it will let you choose the size of your final video and set the quality automatically.

Oh yeah, it's also quite fast without loss of quality.

I believe it was originally designed for Mac, but has been re-tooled for Linux.

Cheers!

---

### Post by RedRat on 2009-09-27
Warning to Hardy users: Handbrake does not apperar to work with Hardy 8.04. I downloaded it and belatedly, after running the deb package, saw that it was for 9.04. My bad. Nevertheless, it does not even launch under Hardy.

---

### Post by FakeOutdoorsman on 2009-09-27
> **riminicat said:**
> A friend of mine at work has been playing with Ubuntu since his vista install crashed, he said he was trying to convert a file and keeps getting this error.  I wondered if it was an mpeg and maybe he was having issues because of this, but he doesn't know a lot about computers and couldn't provide much help.

He plays with media a lot though, maybe a media specific ubuntu would help him more?

Do any of you know what this error means? 

```
Stream #1.0: Audio: mp2, 48000 Hz, 5.1, s16, 224 kb/s
Stream mapping:
Stream #0.0 -> #0.0
Stream #0.1 -> #1.0
encoding 6 channel(s) is not allowed in mp2
Error while opening codec for output stream #1.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```

This is an FFmpeg message saying that mp2 does not support 6 channel audio.  It would be helpful to give some more info:
[list][*]What version of Ubuntu is your friend using?
[*]What is the full FFmpeg command and the full FFmpeg response to that command?[/list]
This will help figure out exactly what is going on.

---

### Post by arnab_das on 2009-09-27
i've been using devede. and it hyas been giving me fab results. i have tried everything and found it to be the best.

its literally the convertx for linux! :)

---


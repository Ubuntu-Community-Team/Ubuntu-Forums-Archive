---
title: "How to convert to h264 + aac using aconv"
date: 2013-06-16
forum: Multimedia Software
---

### Post by ras123 on 2013-06-16
Hi,
Please help me to convert mpeg files to video encoded in h264 and audio encoded in aac format using aconv,
```
avconv -i infut.mpeg -c:v libx264 -c:a ??? output.mkv
```

Thanking You,
Ras

---

### Post by evilsoup on 2013-06-16
See [the x264](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) and [AAC encoding guides](https://ffmpeg.org/trac/ffmpeg/wiki/AACEncodingGuide). Those are strictly speaking for ffmpeg, but AFAIK the syntax should still work with avconv.

To check which AAC encoders you have, use

```

avconv -codecs | grep aac

```

...and then consult the AAC encoding guide for how to use it.

---

### Post by ras123 on 2013-06-17
Thnaks, please let me know how to improve video (and audio) quality? I think the default is not sufficient. 
Is it possible to use similar to -tune option in ffmpeg with avconv?

---

### Post by Yellow Pasque on 2013-06-17
You're probably not going to get better quality by encoding to a different format.

---

### Post by ras123 on 2013-06-17
Yes. I know, but it is now losing quality!

---

### Post by andrew.46 on 2013-06-17
> **ras123 said:**
> Yes. I know, but it is now losing quality!

Are you using a preset? Might be better if you post your complete commandline and full terminal output...

---

### Post by evilsoup on 2013-06-18
Check out the guides I linked to in my first post, those show how to set the quality. I think the should work with avconv, but I've been using ffmpeg eclusively for about a year, so I don't know if the syntax is still 100% compatible (the only way to find out would be to give it a go).

---


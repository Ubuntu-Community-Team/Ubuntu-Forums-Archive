---
title: "Uncompressing a wav to wav?"
date: 2013-06-30
forum: Multimedia Software
---

### Post by honeybear on 2013-06-30
Hi,

I have wav which are compressed. I would be glad to transform them to uncompressed wavs 

Would you know how to perform this?

compressed wav to uncompressed wav.

Kind regareds
Mini

---

### Post by sandyd on 2013-06-30
moved to multimedia and video

---

### Post by evilsoup on 2013-06-30
```
ffmpeg -i input.wav output.wav
```

Will, by default, generate 'output.wav' containing uncompressed 16-bit PCM audio.

---


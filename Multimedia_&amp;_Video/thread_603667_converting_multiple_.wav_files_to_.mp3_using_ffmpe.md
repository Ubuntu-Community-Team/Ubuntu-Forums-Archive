---
title: "converting multiple .wav files to .mp3 using ffmpeg"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by psabhay on 2007-11-05
can any body tell me how to convert multiple .wav files into .mp3. I want to convert whole folder. i am new to linux. can any body tell how to script it? thanks...

---

### Post by kidders on 2007-11-06
Hi there,

Many tools are capable of performing conversions on multiple files in one go. If the one you're using isn't, you could always try a loop of some sort. Here are a few examples, using "echo", but you can obviously substitute in any commands you want...

```
for f in *.wav; do echo $f; done
for f in *.wav; do echo "Pretending to convert $f to `basename $f .wav`.mp3"; done
for f in *.wav; do echo "Pretending to convert $f to `basename $f .wav`.mp3" || echo FAILED; done
```Remember to be careful with spaces & characters with special meanings. Quotes (ie " and ' ) are very useful.

I hope that helps.

---


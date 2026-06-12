---
title: "command line tool to take wav data and play it through pulseaudio/alsa"
date: 2008-05-25
forum: Multimedia Software
---

### Post by CrazyGuy123 on 2008-05-25
is there a command line tool to take wav data from stdin and play it through pulseaudio/alsa?

I'm trying to do something like this:

```
cat testfile.wav | transform1 | transform2 | output
```

where transform1 and transform2 are tools I've made to add special effects to wav files, and output is the program I'm looking for to play the sound through the speakers.

---

### Post by CrazyGuy123 on 2008-05-25
solved it myself - it turns out aplay was what I was looking for.

---


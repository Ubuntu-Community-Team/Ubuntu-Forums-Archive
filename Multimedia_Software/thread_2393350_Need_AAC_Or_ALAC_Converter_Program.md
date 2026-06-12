---
title: "Need AAC Or ALAC Converter Program"
date: 2018-06-02
forum: Multimedia Software
---

### Post by besi1 on 2018-06-02
Hello I have the program SoundConverter Installed Now I can not find in the program how to Convent music in AAC or ALAC formats There are other programs that can or alternatives ?:D 
I have read in pages that also works with SoundConverter but I can not find any instructions on how to do that ??:confused:

Unfortunately, my english is not perfect:P

I thank you for every answer:P

---

### Post by speartip on 2018-06-02
We could do to know. Are you looking to convert to or from AAC/ALAC?

---

### Post by besi1 on 2018-06-02
no the files are mp3 256kbs i will convert in AAC

---

### Post by speartip on 2018-06-02
I know Soundconverter doesn't work at the moment. There is a bug report for that. Apparently the KDE version Soundkonverter does, but also drags in a lot of KDE dependencies. Plus I haven't checked it myself.
Using ffmpeg in the command line will probably work, but I've never had occasion to use it, so would rather leave that to someone more experienced.

---

### Post by SeijiSensei on 2018-06-02
[https://trac.ffmpeg.org/wiki/Encode/AAC](https://trac.ffmpeg.org/wiki/Encode/AAC)

---

### Post by kazakore on 2018-06-04
I would also go with ffmpeg but that assumes that you're happy with a CLI option....

---

### Post by Yellow Pasque on 2018-06-04
- Is winff still good for those who like GUI? (I prefer ffmpeg CLI for these simple audio conversions).

- I'd like to point out that the link that SeijiSensei gave talks about the Fraunhoufer encoder, but Ubuntu's version of ffmpeg doesn't support it (for copyright reasons). The native AAC encoder is good though. [https://trac.ffmpeg.org/wiki/Encode/AAC#NativeFFmpegAACEncoder](https://trac.ffmpeg.org/wiki/Encode/AAC#NativeFFmpegAACEncoder)

- Encoding from mp3 to AAC will degrade audio quality (like all lossy->lossy conversions). Encoding from mp3 to ALAC will just waste space (like all lossy -> lossless conversions).

---


---
title: "ffmpeg help: convert 16 bit to 24 bit"
date: 2010-06-09
forum: Multimedia Software
---

### Post by lykwydchykyn on 2010-06-09
I have a bunch of 16 bit 44.1 kHz wav files I need to convert to 24 bit 48kHz so they can be imported into a session file.  I want to script the process in case I have to do it again.

(And yes, I know it does not add any quality to the audio, this is just a compatibility issue).

I know I can use this command to fix the sampling rate:
```

ffmpeg -i somefile.wav -ar 48000 somefile-fixed.wav

```

I don't know the syntax for changing to bit depth to 24 bit.  I tried different values for the -ab switch but nothing works; the resulting file is always 16 bit.

Does anyone know if this can be done with ffmpeg, or if there is another CLI tool I can use to convert?

---

### Post by FakeOutdoorsman on 2010-06-09
Perhaps something like this?
```
ffmpeg -i input.foo -acodec pcm_s24le -ar 48000 output.wav
```
There are other -*acodec* variants you can try.  See:
```
ffmpeg -codecs | grep DEA.*PCM.*24
```
SoX looks like it can do it too:
```
sox input.wav -b 24 output.wav
```

---

### Post by lykwydchykyn on 2010-06-09
The sox command just resulted in static, but the ffmpeg command worked for me.  Thanks!

---


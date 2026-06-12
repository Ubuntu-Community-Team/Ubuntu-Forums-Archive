---
title: "mp3 to .wavs"
date: 2009-08-14
forum: Multimedia Software
---

### Post by accodata on 2009-08-14
Hi

Can someone please tell me what program I need to convert mp3 files to wav files.

with thanks

Tracey

---

### Post by SpaceBison on 2009-08-14
Try "Sound Converter"

---

### Post by accodata on 2009-08-14
thanks you

---

### Post by lostfawords on 2009-08-27
better to use lame from the command line. sound converter uses some ridiculous presets at times.

man lame

look for the "--decode" switch i think

---

### Post by andrew.46 on 2009-08-28
Hi Tracey,

> **accodata said:**
> Can someone please tell me what program I need to convert mp3 files to wav files.

MPlayer can do this from the commandline:
```

mplayer **[COLOR="Red"]myfile.mp3[/COLOR]** -vc null -vo null -ao pcm:fast:waveheader:file=output.wav
```

and this is easy enough to script if you have many such files.

Andrew

---

### Post by Matt 6:27 on 2009-12-23
Just exactly what I needed!  Thanks andrew.46!!!

---

### Post by Jose Catre-Vandis on 2009-12-23
Other command line ways:

Using ffmpeg:
```
ffmpeg -i input.mp3 output.wav
```
Using sox
```
sox -i input.mp3 output.wav
```

---

### Post by K.J. on 2009-12-23
Audacity is a good choice if you need a GUI. Not very good for batches though.

---


---
title: "convert mpeg adts to normal mp3"
date: 2008-05-16
forum: Multimedia Software
---

### Post by stahoo23 on 2008-05-16
hello
I need convert MPEG ADTS to normal mp3 because my net radio can't play ADTS, for example:

```
file plik.mp3 
plik.mp3: MPEG ADTS, layer III, v1, 128 kBits, 44.1 kHz, JntStereo
```

not play

```
file beautiful.mp3 
beautiful.mp3: Audio file with ID3 version 23.0 tag, MP3 encoding

```
play.

I tested this:


```
lame -h plik.mp3 1.mp3
```

and

```
mplayer -nojoystick -nolirc -nortc -vo null -vc dummy -af resample=44100 -ao pcm:waveheader:file=1.wav plik.mp3
lame -h 1.wav 2.mp3
```

and results are same - MPEG ADTS
sorry for my english

---

